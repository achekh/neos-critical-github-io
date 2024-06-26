---
title: "Custom Component Extension"
slug: "custom-component-extension"
excerpt: "This section explains the concept of custom component extension."
hidden: false
metadata: 
  image: []
  robots: "index"
createdAt: "Tue May 02 2023 09:03:53 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Fri Jul 14 2023 11:02:16 GMT+0000 (Coordinated Universal Time)"
layout: "default"
parent: "Custom Components"
grand_parent: "Guide"
nav_order: 8
---
# Custom Component Extension 
*** 
In order to better customize the features of a custom component, you can use the custom component extension mechanism.

## Extended effect

```javascript
// javascript
// behavior.js
module.exports = Behavior({
  definitionFilter(defFields) {
    defFields.data.from = 'behavior'
  },
})
// component.js
Component({
  data: {
    from: 'component'
  },
  behaviors: [require('behavior.js')],
  ready() {
    console.log(this.data.from) // Here, you will find that `behavior` rather than `component` is output.
  }
})
```

As can be seen from the above sample, the custom component extension essentially provides the capability to modify the definition section of the custom component. In the sample, the content in the `data` definition section of the custom component is modified.

## Using an extension

The `Behavior()` constructor provides the new definition section `definitionFilter` to support custom component extensions. `definitionFilter` is a function that injects two parameters when called. The first is the definition object of the component/behavior that uses the behavior, and the second is the `definitionFilter` function list of the behaviors used by the behavior.

### Below is a sample:

```javascript
// javascript
// behavior3.js
module.exports = Behavior({
  definitionFilter(defFields, definitionFilterArr) {},
})
// behavior2.js
module.exports = Behavior({
  behaviors: [require('behavior3.js')],
  definitionFilter(defFields, definitionFilterArr) {
    // definitionFilterArr[0](defFields)
	}, 
})
// behavior1.js
module.exports = Behavior({
  behaviors: [require('behavior2.js')],
  definitionFilter(defFields, definitionFilterArr) {},
})
// component.js
Component({
  behaviors: [require('behavior1.js')],
})
```

One custom component and three behaviors are declared in the above code, and each behavior uses the `definitionFilter` definition section. Then, the following things will happen in the order of declaration:

1. When behavior 2 is declared, the `definitionFilter` function of behavior 3 will be called, where the `defFields` parameter is the definition section of behavior 2, and the `definitionFilterArr` parameter is an empty array as behavior 3 does not use other behaviors.
2. When behavior 1 is declared, the `definitionFilter` function of behavior 2 will be called, where the `defFields` parameter is the definition section of behavior 1, the `definitionFilterArr` parameter is an array with a length of 1 , and `definitionFilterArr[0]` is the definitionFilter function of behavior 3 as behavior 2 uses behavior 3. Here, you can decide whether to call the `definitionFilter` function of behavior 3 when declaring behavior 1. If necessary, add the code `definitionFilterArr[0](defFields)` here, and the `definitionFilterArr` parameter will be passed in by the SuperHub Platfrom.
3. Similarly, the `definitionFilter` function of behavior 1 will be called when the component is declared.

In summary, the definitionFilter function can be understood as when A uses B, the declaration of A will call the `definitionFilter` function of B and pass in the definition object of A for B to filter. At this time, if B also uses C and D, then B can decide whether to call the definitionFilter functions of C and D to filter the definition object of A.

### Sample

The following uses an extension to simply implement the feature of calculating attributes of a custom component:

```javascript
// javascript
// behavior.js
module.exports = Behavior({
  lifetimes: {
    created() {
      this._originalSetData = this.setData // Original `setData`
      this.setData = this._setData // Encapsulated `setData`
		} 
  },
  definitionFilter(defFields) {
    const computed = defFields.computed || {}
    const computedKeys = Object.keys(computed)
    const computedCache = {}
    // Calculate `computed`
    const calcComputed = (scope, insertToData) => {
      const needUpdate = {}
      const data = defFields.data = defFields.data || {}
      for (const key of computedKeys) {
        const value = computed[key].call(scope) // Calculate the new value
        if (computedCache[key] !== value) needUpdate[key] = computedCache[key] = value
        if (insertToData) data[key] = needUpdate[key] // Insert this directly into `data`. This operation is only required during initialization.
		}
      return needUpdate
    }
    // Rewrite the `setData` method
    defFields.methods = defFields.methods || {}
    defFields.methods._setData = function (data, callback) {
      const originalSetData = this._originalSetData // Original `setData`
      originalSetData.call(this, data, callback) // Perform `setData` for `data`
      const needUpdate = calcComputed(this) // Calculate `computed`
      originalSetData.call(this, needUpdate) // Perform `setData` for `computed`
		}
    // Initialize `computed`
    calcComputed(defFields, true) // Calculate `computed`
  }
})
```

Use the following in the component:

```javascript
// javascript
const beh = require('./behavior.js')
Component({
  behaviors: [beh],
  data: {
		a: 0, 
  },
  computed: {
    b() {
      return this.data.a + 100
    },
	}, 
  methods: {
    onTap() {
      this.setData({
        a: ++this.data.a,
      })
		} 
  }
})
```

```xml
// WXML
{% raw %}
<view>data: {{a}}</view>
<view>computed: {{b}}</view>
<button bindtap="onTap">click</button>
{% endraw %}
```

The implementation principle is very simple. The existing `setData` is encapsulated again, and the value of each field in `computed` is calculated everytime `setData` is performed and then set to data to achieve the effect of attribute calculation.

> This implementation is only a simple sample. Do not use it directly in a production environment.
