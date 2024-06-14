---
title: "Component Constructor"
slug: "component-constructor"
excerpt: ""
hidden: false
createdAt: "Wed May 03 2023 10:17:57 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Tue Nov 28 2023 10:25:25 GMT+0000 (Coordinated Universal Time)"
layout: "default"
parent: "Custom Components"
grand_parent: "Guide"
---
# Component Constructor 
*** 
The component constructor can be used to define a component, and the attributes, data, and methods of the component can be specified when the component constructor is called.

| Definition Section | Type         | Required | Description                                                                                                                                                                                                                                                                                                           |
| :----------------- | :----------- | :------- | :-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| properties         | Object Map   | No       | The externally exposed attribute of the component, which is a mapping table between the attribute name and attribute setting. The attribute setting can contain three fields: `type` (attribute type), `value` (initial attribute value), and `observer` (the response function when the attribute value is changed). |
| data               | Object       | No       | Internal data of the component, which is used together with properties for template rendering of the component.                                                                                                                                                                                                       |
| observers          | Object       | No       | Listener for component data fields, which is used to listen for changes in `properties` and `data`. For more information, see [Data Listener](doc:data-listener).                                                                                                                                                     |
| methods            | Object       | No       | Component methods, including event response functions and any custom methods. For the usage of event response functions, see [Component Event](doc:inter-component-communication-and-events).                                                                                                                         |
| behaviors          | String Array | No       | Similar to the code reuse mechanism between `mixins` and `traits`. For more information, see [Behaviors](doc:behaviors).                                                                                                                                                                                              |
| created            | Function     | No       | Component lifecycle function, which is executed when the component instance is just create d. Note that `setData` cannot be called at this time. For more information, see [Component Lifecycle](doc:component-lifecycle).                                                                                            |
| attached           | Function     | No       | Component lifecycle function, which is executed when the component instance enters the page node tree. For more information, see [Component Lifecycle](doc:component-lifecycle).                                                                                                                                      |
| ready              | Function     | No       | Component lifecycle function, which is executed after component layout is completed. For more information, see [Component Lifecycle](doc:component-lifecycle).                                                                                                                                                        |
| moved              | Function     | No       | Component lifecycle function, which is executed when the component instance is moved to another position in the node tree. For more information, see [Component Lifecycle](doc:component-lifecycle).                                                                                                                  |
| detached           | Function     | No       | Component lifecycle function, which is executed when the component instance is removed from the page node tree. For more information, see [Component Lifecycle](doc:component-lifecycle).                                                                                                                             |
| relations          | Object       | No       | Relationship definition between components. For more information, see [Relationship Between Components](doc:inter-component-relationship).                                                                                                                                                                            |
| externalClasses    | String Array | No       | External style classes that can be accepted by the component. For more information, see [Component Template and Style](doc:component-template-and-style).                                                                                                                                                             |
| options            | Object Map   | No       | Some options (specific option settings will be described when related features are introduce d in the documents).                                                                                                                                                                                                     |
| lifetimes          | Object       | No       | Lifecycle declaration object of the component. For more information, see [Component Lifecycle](doc:component-lifecycle)                                                                                                                                                                                               |
| pageLifetimes      | Object       | No       | Lifecycle declaration object of the page where the component is located, which supports `show`, `hide`, and other lifecycle functions of the page. For more information, see [Component  Lifecycle](doc:component-lifecycle)                                                                                          |
| definitionFilter   | Function     | No       | Definition section filter for custom component extensions. For more information, see [Custom Component Extension](doc:custom-component-extension).                                                                                                                                                                    |

The generated component instance can be accessed via `this` in the component's methods, lifecycle functions, and attribute `observer`. The component contains some common attributes and methods:

| Attribute  | Type   | Description                                                                            |
| :--------- | :----- | :------------------------------------------------------------------------------------- |
| is         | String | File path of the component                                                             |
| id         | String | Node ID                                                                                |
| dataset    | String | Node dataset                                                                           |
| data       | Object | Component data, **including internal data and attribute values**.                      |
| properties | Object | Component data, including internal data and attribute values (consistent with `data`). |

| Method                     | Parameter                                        | Description                                                                                                                                                                                                                                     |
| :------------------------- | :----------------------------------------------- | :---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| setData                    | Object `newData`                                 | Sets `data` and performs view layer rendering                                                                                                                                                                                                   |
| hasBehavior                | Object`behavior`                                 | Checks whether the component has a behavior (recursively checks all behaviors imported directly or indirectly)                                                                                                                                  |
| triggerEvent               | String `name`, Object `detail`, Object `options` | Triggers an event. For more information, see [Component Event](doc:inter-component-communication-and-events).                                                                                                                                   |
| createSelectorQuery        |                                                  | Creates a [SelectorQuery](doc:wxml-api#selectorquery-wxcreateselectorquery) object. The selection range of the selector is within this component instance.                                                                                      |
| createIntersectionObserver |                                                  | Creates an [IntersectionObserver](doc:wxml-api#intersectionobserver-wxcreateintersectionobserverobject-thisobject-options) object. The selection range of the selector is within this component instance.                                       |
| selectComponent            | String `selector`                                | Uses a selector to select a component instance node and returns the first matched component instance object (which will be affected by `wx://component-export`).                                                                                |
| selectAllComponents        | String `selector`                                | Uses a selector to select component instance nodes and returns an array of all matched component instance objects                                                                                                                               |
| getRelationNodes           | String `relationKey`                             | Gets all associated nodes corresponding to this relationship. For more information, see [Relationship Between Components](doc:inter-component-relationship).                                                                                    |
| groupSetData               | Function `callback`                              | Immediately executes `callback`, where multiple `setData` values will not trigger UI drawing (this is required only in some special scenarios, such as UI drawing sync when `setData` is configured for different components at the same time). |

**Sample code:**

```javascript
Component({
  behaviors: [],
  properties: {
    myProperty: { // Attribute name
      type: String, // Type (required). Currently accepted types include: String, Number, Boolean, Object, Array, null (for any type)
      value: '', // Initial attribute value (optional). If it is not specified, a value will be selected according to the type.
      observer(newVal, oldVal, changedPath) {
        // The function executed when the attribute is changed (optional). It can also be written as a method name string defined in the
`methods` section, such as `_propertyChange`.
        // Usually, `newVal` is the newly set data, while `oldVal` is the old value.
} },
    myProperty2: String // Simplified definition
  },
  data: {}, // Private data, which can be used for template rendering.
lifetimes: {
    // Lifecycle function, which can be a function or a method name defined in the `methods` section.
    attached() { },
    moved() { },
    detached() { },
},
  // Lifecycle function, which can be a function or a method name defined in the `methods` section.
  attached() { }, // The declaration of `attached` here will be overwritten by the declaration in the `lifetimes` field.
  ready() { },
  pageLifetimes: {
    // The lifecycle function of the page where the component is located.
    show() { },
    hide() { },
    resize() { },
},
  methods: {
    onMyButtonTap() {
      this.setData({
        // The method of updating attributes and data is similar to that of updating page data.
}) },
    // We recommend you make internal methods begin with an underscore.
    _myPrivateMethod() {
      // Set `data.A[0].B` to `myPrivateData` here
      this.setData({
        'A[0].B': 'myPrivateData'
}) },
    _propertyChange(newVal, oldVal) {
} }
})
```

Note: In the `properties` definition section, the attribute name is written in camel case (`propertyName`); in `wxml`, the specified attribute value is written with hyphen (`component-tag-name property-name="attr value"`) or in camel case (`attr="{{propertyName}}"`) when used in data binding.

## Using the component constructor to construct a page

In fact, the pages of a mini app can also be regarded as custom components. Therefore, pages can also be constructed with the component constructor, with the same definition sections and instance methods as general components. However, the corresponding `json` file must contain the `usingComponents` definition section in this case.

At this time, the attributes of the component can be used to receive page parameters; for example, when the page `/pages/index/index?paramA=123&paramB=xyz` is accessed, if the declaration has the attribute `paramA` or `paramB`, it will be assigned as `123` or `xyz`.

The lifecycle methods of the page (i.e. methods beginning with `on`) should be written in the `methods` definition section.

### Sample code:

```Text code
{
  "usingComponents": {}
}
```

```Text code
Component({

  properties: {
    paramA: Number,
    paramB: String,
  },

  methods: {
    onLoad: function() {
      this.data.paramA // Value of page parameter paramA
      this.data.paramB // Value of page parameter paramB
    }
  }

})
```

## Bugs and tips

- Use `this.data` to get internal data and attribute values, but do not modify them directly; instead, use `setData` to modify them.
- Lifecycle functions cannot be accessed via `this` in component methods.
- Attribute names should not begin with `data`, such as `dataXyz`, because `data-xyz=""` will be treated as a node dataset rather than a component attribute in WXML.
- When a component is defined and used, its attribute names and data fields cannot conflict with each other (even if they are located in different definition sections).
- Attributes and data fields of object type can contain subfields of function type; that is, functions can be passed through the attribute fields of object type.
- Bug: For an attribute of object or array type, if a subfield of the attribute value is modified via this.setData of the component itself, the attribute `observer` will still be triggered, and the `newVal` received by the `observer` will be the value of the changed subfield, `oldVal` will be empty, and `changedPath` will contain information about the subfield name.
- Bug: A custom component located in a slot does not trigger the page lifecycle declared in `pageLifetimes`.
