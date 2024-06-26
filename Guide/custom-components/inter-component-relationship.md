---
title: "Relationship Between Components"
slug: "inter-component-relationship"
excerpt: "This section explains the concept of inter-component relationship."
hidden: false
metadata: 
  image: []
  robots: "index"
createdAt: "Tue May 02 2023 07:50:43 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Fri Jul 14 2023 11:01:08 GMT+0000 (Coordinated Universal Time)"
layout: "default"
parent: "Custom Components"
grand_parent: "Guide"
nav_order: 6
---
# Relationship Between Components 
This section explains the concept of inter-component relationship.

***

## Defining and using a relationship between components

Sometimes, it is necessary to implement components like the following:

```xml
<!-- WXML -->
<custom-ul>
  <custom-li>item 1</custom-li>
  <custom-li>item 2</custom-li>
</custom-ul>
```

In this sample, `custom-ul` and `custom-li` are both custom components, which have a mutual relationship and often involve complicated communication. At this time, adding the `relations` definition section when the components are defined can solve this problem. Sample:

```javascript
// javascript
// path/to/custom-ul.js
Component({
  relations: {
    './custom-li': {
      type: 'child', // The associated target node should be a child node.
      linked(target) {
        // Executed every time a `custom-li` is inserted. The target is the instance object of the node, which is triggered after the node's
				`attached` lifecycle.
      },
      linkChanged(target) {
        // Executed every time a `custom-li` is moved. The target is the instance object of the node, which is triggered after the node's
				`moved` lifecycle.
      },
      unlinked(target) {
        // Executed every time a `custom-li` is removed. The target is the instance object of the node, which is triggered after the node's
				`detached` lifecycle.
			} 
    }
	}, 
  methods: {
    _getAllLi() {
      // Use `getRelationNodes` to get the `nodes` array, which contains all associated `custom-li` values in sequence.
      const nodes = this.getRelationNodes('path/to/custom-li')
    }
	}, 
  ready() {
    this._getAllLi()
  }
})
```

```javascript
// javascript
// path/to/custom-li.js
Component({
  relations: {
    './custom-ul': {
      type: 'parent', // The associated target node should be a parent node.
      linked(target) {
        // Executed every time it is inserted into `custom-ul`. The target is the instance object of the `custom-ul` node, which is triggered
				after the `attached` lifecycle.
      },
      linkChanged(target) {
        // Executed every time it is moved. The target is the instance object of the `custom-ul` node, which is triggered after the `moved`
				lifecycle.
      },
      unlinked(target) {
        // Executed every time it is removed. The target is the instance object of the `custom-ul` node, which is triggered after the
				`detached` lifecycle.
			} 
    }
	} 
})
```

**Note: The `relations` definition must be added to both components' definitions; otherwise, it will not take effect.**

## Associating a class of components

Sometimes, a class of components needs to be associated; for example:

```javascript
// javascript
<custom-form>
  <view>
input
    <custom-input></custom-input>
  </view>
  <custom-submit>submit</custom-submit>
</custom-form>
```

You want to associate the `custom-form` component with two components: `custom-input` and `custom-submit`. In this case, if both components have the same behavior:

```javascript
// javascript
// path/to/custom-form-controls.js
module.exports = Behavior({
  // ...
})
```

```javascript
// javascript
// path/to/custom-input.js
const customFormControls = require('./custom-form-controls')
Component({
  behaviors: [customFormControls],
  relations: {
    './custom-form': {
      type: 'ancestor', // The associated target node should be an ancestor node.
		} 
  }
})
```

```javascript
// javascript
// path/to/custom-submit.js
const customFormControls = require('./custom-form-controls')
Component({
  behaviors: [customFormControls],
  relations: {
    './custom-form': {
      type: 'ancestor', // The associated target node should be an ancestor node.
		} 
  }
})
```

Then, in the `relations` definition, you can use this behavior instead of the component path as the associated target node:

```javascript
// javascript
// path/to/custom-form.js
const customFormControls = require('./custom-form-controls')
Component({
  relations: {
    customFormControls: {
      type: 'descendant', // The associated target node should be a descendant node.
      target: customFormControls
    }
	} 
})
```

## `relations` definition section

The `relations` definition section contains the target component path and its corresponding options. The options that can be included are as shown below.

| Option      | Type     | Required | Description                                                                                                                                                                                    |
| :---------- | :------- | :------- | :--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| type        | String   | Yes      | The relative relationship of the target component. Valid values: `parent`, `child`, `ancestor`, `descendant`.                                                                                  |
| linked      | Function | No       | Relationship lifecycle function, which will be triggered when the relationship is established in the page node tree. Its triggering time is after the component's attached lifecycle function. |
| linkChanged | Function | No       | Relationship lifecycle function, which will be triggered when the relationship is changed in the page node tree. Its triggering time is after the component's `moved` lifecycle function.      |
| unlinked    | Function | No       | Relationship lifecycle function, which will be triggered when the relationship is removed from the page node tree. Its triggering time is after the component's `detached` lifecycle function. |
| target      | String   | No       | If this option is set, it indicates the behavior that the associated target node should have, and all component nodes with this behavior will be associated.                                   |
