---
title: "Basic Component"
slug: "basic-component"
excerpt: ""
hidden: false
metadata: 
  image: []
  robots: "index"
createdAt: "Tue May 23 2023 11:17:13 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Thu Jun 08 2023 10:20:45 GMT+0000 (Coordinated Universal Time)"
layout: "default"
parent: "View Layer"
grand_parent: "Guide"
---
# Basic Component 
*** 
The framework provides a series of basic components, which can be used in combination for quick development.

What is a component?

- A component is the basic unit of the view layer.
- A component comes with some styles which serve the same purpose as Super Hub styles.
- A component typically includes the start tag and end tag and is described by attributes between the two tags.

```html
<!--WXML-->
{% raw %}
<tagname property="value">
  Content goes here ...
</tagname>
{% endraw %}
```

> 📘 Notes
> 
> All components and attributes are in lowercase and separated by hyphen `-`.

## Attribute type

| Type          | Description                 | Remarks                                                                                                                                                                                                                                                                                         |
| :------------ | :-------------------------- | :---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Boolean       | Boolean value               | When the component has this attribute, no matter what value it is, it will be regarded as `true`. Only when there is no such attribute in the component will the attribute value be `false`. If the attribute value is a variable, the value of the variable will be converted to Boolean type. |
| Number        | Number                      | `1`,`2.5`                                                                                                                                                                                                                                                                                       |
| String        | String                      | `"string"`                                                                                                                                                                                                                                                                                      |
| Array         | Array                       | [ `1`, `"string"` ]                                                                                                                                                                                                                                                                             |
| Object        | Object                      | `{ key: value }`                                                                                                                                                                                                                                                                                |
| Event Handler | Event handler function name | `"handlerName"` is the event handler function name defined in the JavaScript page.                                                                                                                                                                                                              |
| Any           | Any attribute               |                                                                                                                                                                                                                                                                                                 |

## Common attributes

All components have the following attributes:

| Attribute    | Type          | Description                   | Remarks                                                                                     |
| :----------- | :------------ | :---------------------------- | :------------------------------------------------------------------------------------------ |
| id           | String        | Unique ID of the component    | Keeps the whole page unique                                                                 |
| class        | String        | Style class of the component  | The style class defined in the corresponding WXSS                                           |
| style        | String        | Inline style of the component | The inline style that can be set dynamically                                                |
| hidden       | Boolean       | Whether to show the component | All components are shown by default.                                                        |
| data-\*      | Any           | Custom attribute              | When an event is triggered on the component, it will be sent to the event handler function. |
| bind / catch | Event Handler | Event of the component        |                                                                                             |

## Special attributes

Almost all components have their own custom attributes, which can modify the features or styles of the components.
