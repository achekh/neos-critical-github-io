---
title: "Custom Components"
slug: "custom-components"
excerpt: "This section explains the concept of Custom Components."
hidden: false
metadata: 
  image: []
  robots: "index"
createdAt: "Tue May 02 2023 07:31:16 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Thu Jun 08 2023 10:45:26 GMT+0000 (Coordinated Universal Time)"
layout: "default"
parent: "Guide"
has_children: true
---
# Custom Components 
*** 
Mini Programs support concise componential programming.

Developers can abstract feature modules in a page into custom components to reuse them in different pages, or split a page into multiple low-coupling modules for easy code maintenance. Custom components are used in almost the same way as base components.

## Creating Custom Component

Similar to a page, a custom component consists of `json`, `wxml`,` wxss`, and `js` files. To write a custom component, you first need to make a custom component declaration in the json file (set the files as custom components by setting the `component` field to `true`):

```Text code
{
  "component": true
}
```

In the meanwhile, write a component template in the `wxml` file and a component style in the `wxss` file in a same way that you write a page. For details and considerations, see Component Template and Style.

### Code example:

```Text code
<!-- This is the internal WXML structure of the custom component -->
<view class="inner">
  {{innerText}}
</view>
<slot></slot>
```

```Text code
/*  This style only applies to this custom component  */
.inner {
  color: red;
}
```

> 📘 Note
> 
> ID selectors, attribute selectors, and tag name selectors should not be used in the component's wxss.

In the custom component's `js` file, you need to register the component using `Component()` and provide the component's property definitions, internal data, and custom methods.

The property values and internal data of the component are used to render the component's `wxml`. The property values are passed in from outside the component. For details, see Component Constructor.

### Code example:

```Text code
Component({
  properties: {
    // The innerText property is defined here, and the property value can be specified when the component is used.
    innerText: {
      type: String,
      value: 'default value',
    }
  },
  data: {
    // Here are some component internal data
    someData: {}
  },
  methods: {
    // Here is a custom method
    customMethod: function(){}
  }
})
Using 
```

## Using Custom Component

Before using a registered custom component, make a reference declaration in the json file of the page. You need to provide the tag name of each custom component and the file path of the corresponding custom component:

```Text code
{
  "usingComponents": {
    "component-tag-name": "path/to/the/custom/component"
  }
}
```

As such, you can use custom components like you would with base components in the `wxml` of the page. The node name is the tag name of the custom component, and the node property is the property value passed to the component.

### Code example:

```Text code
<view>
  <!-- The following is a reference to a custom component -->
  <component-tag-name inner-text="Some text"></component-tag-name>
</view>
```

The custom component's `wxml` node structure, after being combined with the data, will be inserted into the reference location.

> 📘 Notes
> 
> - Since the tag name of a WXML node can only be a combination of lowercase letters, hyphens (-), and underscores (\_), the tag name of a custom component can contain these characters only.
> - Custom components can also reference other custom components in a similar way to referencing custom components by pages (the `usingComponents` field is used).
> - The name of the project's root directory where the custom components and pages are located cannot be prefixed with "wx-". Otherwise, an error will occur.

> 📘 Notes
> 
> Using `usingComponents` in the page file will make the prototype of the page's this object slightly different, including:
> 
> - The prototype that uses the usingComponents page differs from the prototype that does not use usingComponents, i.e. the result of Object.getPrototypeOf(this) is different.
> - More methods, such selectComponent, are available when usingComponents is used.
> - For performance reasons, when usingComponents is used, the content of setData is not deep copied directly, that is, this.data.field === obj after this.setData({ field: obj }) is called. (Deep copy occurs when this value is passed between components.)

For complicated pages, retest is required if the `usingComponents` definition field is added or removed.
