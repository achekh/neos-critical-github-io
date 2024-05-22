---
title: "Behaviors"
slug: "behaviors"
excerpt: "This section explains the concept of Behaviors."
hidden: false
metadata: 
  image: []
  robots: "index"
createdAt: "Tue May 02 2023 07:48:04 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Fri Jun 09 2023 09:46:01 GMT+0000 (Coordinated Universal Time)"
---
## Defining and using a behavior

A behavior is a feature for code sharing between components, similar to `mixins` or `traits` in some programming languages.

Each behavior can contain a set of attributes, data, lifecycle functions, and methods. When a component references it, its attributes, data, and methods will be merged into the component, and its lifecycle functions will be called at the corresponding time. Each component can reference multiple behaviors. A behavior can also reference other behaviors.

A behavior needs to be defined with the `Behavior()` constructor.

### Sample code:

```javascript
// my-behavior.js
module.exports = Behavior({
  behaviors: [],
  properties: {
    myBehaviorProperty: {
      type: String
} },
  data: {
    myBehaviorData: {}
  },
  attached() {},
  methods: {
    myBehaviorMethod() {}
  }
})
```

When referencing components, list them one by one in the `behaviors` definition section.

### Sample code:

```javascript
// my-component.js
const myBehavior = require('my-behavior')
Component({
  behaviors: [myBehavior],
  properties: {
    myProperty: {
      type: String
		} 
  },
  data: {
    myData: {}
  },
  attached() {},
  methods: {
    myMethod() {}
  }
})
```

In the above sample,  `my-behavior` is added to the `my-component` component definition and contains the   `myBehaviorProperty` attribute, `myBehaviorData` data field, `myBehaviorMethod` method, and `attached` lifecycle function. This will make `my-component` eventually contain two attributes of `myBehaviorProperty` and `myProperty`, two data fields of `myBehaviorData` and `myData`, and two methods of `myBehaviorMethod` and `myMethod`. When a component triggers the `attached` lifecycle, the `attached` lifecycle function in `my-behavior` and `my-component` will be triggered in turn.

## Field overwriting and combining rules

A component and its referenced behavior can contain fields with the same name, which are handled as follows:

- For attributes or methods with the same name, the attribute or method of the component will overwrite that in the behavior; if multiple behaviors are referenced, that in the last behavior in the definition section will overwrite previous ones.
- For data fields with the same name, if they are of object type, the objects will be merged; otherwise, they will overwrite each other.
- Lifecycle functions will not overwrite each other; instead, they will be called one by one at the corresponding triggering time. If the same behavior is referenced multiple times by a component, the lifecycle function it defines will be executed only once.

## Built-in behaviors

Custom components can get the behaviors of built-in components by referencing built-in behaviors.

```
Component({
  behaviors: ['wx://form-field']
})
```

In the above sample, `wx://form-field` represents a built-in behavior that makes this custom component behave like a form control.

The built-in behavior generally adds some attributes to the component. Unless otherwise specified, a component can overwrite these attributes to change its `type` or add an `observer`.

## wx://form-field

It makes custom components behave like a form control. The form component can recognize these custom components and returns their field names and corresponding field values in the submit event. This will add the following two attributes to it:

| Attribute | Type   | Description             |
| :-------- | :----- | :---------------------- |
| name      | String | Field name in the form  |
| value     | Any    | Field value in the form |

## wx://component-export

It enables custom components to support the `export` definition section, which can be used to specify the returned value of the component when called by `selectComponent`.

If this section is not used, `selectComponent` will return `this` of the custom component (or `null` for a plugin custom component). If it is used, the returned value of its function will be returned instead.

### Sample code:

```javascript
// Inside the custom component `my-component`
Component({
  behaviors: ['wx://component-export'],
  export() {
    return {myField: 'myValue'}
  }
})
```

```Text WXML
<!-- If the custom component is used -->
<my-component id="the-id" />
```

```javascript
 this.selectComponent('#the-id') // Equivalent to { myField: 'myValue' }
```
