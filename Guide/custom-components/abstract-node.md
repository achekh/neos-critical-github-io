---
title: "Abstract Node"
slug: "abstract-node"
excerpt: "This section explains the concept of Abstract Node."
hidden: false
metadata: 
  image: []
  robots: "index"
createdAt: "Tue May 02 2023 08:57:39 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Fri Jun 09 2023 10:09:07 GMT+0000 (Coordinated Universal Time)"
layout: "default"
parent: "Custom Components"
grand_parent: "Guide"
---
# Abstract Node 
*** 
## Using an abstract node in a component

Sometimes, for some nodes in a custom component template, the corresponding custom component is not determined by the custom component itself but by the caller of the custom component. In this case, this node can be declared as an "abstract node".

For example, you want to implement a "selectable-group" component, where radio buttons (custom-radio) or checkboxes (custom-checkbox) can be placed. The `wxml` of this component can be written as follows:

```Text WXML
<!-- selectable-group.wxml -->
<view qq:for="{{labels}}">
  <label>
    <selectable disabled="{{false}}"></selectable>
{{item}}
  </label>
</view>
```

Among them, `selectable` is not any component declared in the `usingComponents` field of the `json` file but an abstract node. It needs to be declared in the `componentGenerics` field:

```json
{
  "componentGenerics": {
    "selectable": true
  }
}
```

## Using a component containing an abstract node

When using the `selectable-group` component, you must specify which component is `selectable`:

```Text WXML
 <selectable-group generic:selectable="custom-radio" />
```

In this way, when generating an instance of this `selectable-group` component, the `selectable` node will generate an instance of the `custom-radio` component. Similarly, if the following is used:

```Text WXML
 <selectable-group generic:selectable="custom-checkbox" />
```

The `selectable` node will generate an instance of the `custom-checkbox` component.

Note: The above `custom-radio` and `custom-checkbox` need to be included in the `usingComponents` definition section of the corresponding `json` file of the `wxml`.

```json
{
  "usingComponents": {
    "custom-radio": "path/to/custom/radio",
    "custom-checkbox": "path/to/custom/checkbox"
  }
}
```

## Default component of an abstract node

You can specify the default component for an abstract node. If you don't do this, an instance of the default component will be created. The default component can be specified in the `componentGenerics` field:

```json
{
  "componentGenerics": {
    "selectable": {
      "default": "path/to/default/component"
		} 
  }
}
```

### Tips:

- In the node's generic reference `generic:xxx="yyy"`, `yyy` can only be a static value but cannot contain data binding. Therefore, abstract nodes are not suitable for scenarios where node names are dynamically determined.
