---
title: "Rich text"
slug: "rich-text"
excerpt: "A component that displays formatted rich text."
hidden: false
metadata: 
  image: []
  robots: "index"
createdAt: "Thu Apr 06 2023 11:41:08 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Fri Jul 14 2023 11:04:58 GMT+0000 (Coordinated Universal Time)"
layout: "default"
parent: "Basic components"
grand_parent: "Components"
nav_order: 4
---
# Rich text 
A component that displays formatted rich text.

***

The `rich-text` allows entering or editing formatted rich text.

| Attribute | Type          | Default | Description                |
| :-------- | :------------ | :------ | :------------------------- |
| nodes     | Array/ String | \[]     | Node list/HTML string.     |
| space     | String        |         | Display continuous spaces. |

## Valid values of `space`:

| Value | Introductions                     |
| :---- | :-------------------------------- |
| ensp  | Size of one space character       |
| emsp  | Size of two space characters      |
| nbsp  | Space size specified by the font. |

Supported default events include: `tap`, `touchstart`, `touchmove`, `touchcancel`, `touchend`, and `longtap`.

**We recommend you use the `Array` type for `nodes`. If you use the `String` type, as the component will convert `String` to `Array`; this will affect the performance.**

### nodes

Two types of nodes are supported and differentiated by `type`: element node (default) and text node. Element nodes are displayed as HTML nodes in the rich text area.

**Element node:** **`type = node`**

| Attribute | Description     | Type   | Required | Remarks                                                                |
| :-------- | :-------------- | :----- | :------- | :--------------------------------------------------------------------- |
| name      | Tag name        | String | Yes      | Supports partially trusted HTML node.                                  |
| attrs     | attribute       | Object | No       | Supports partially trusted properties, Pascal case is used for naming. |
| children  | Child node list | Array  | No       | It has the same structure as `nodes`.                                  |

**text node:** **`type = text`**

| Attribute | Description          | Type   | Required | Remarks                 |
| :-------- | :------------------- | :----- | :------- | :---------------------- |
| text      | text to be displayed | String | Yes      | Entities are supported. |

### Trusted HTML nodes and properties

The class and style attributes are supported globally, but the `id` **attribute** is not.

| Node       | Attribute                    |
| :--------- | :--------------------------- |
| a          |                              |
| abbr       |                              |
| b          |                              |
| blockquote |                              |
| br         |                              |
| code       |                              |
| col        | span, width                  |
| colgroup   | span, width                  |
| dd         |                              |
| div        |                              |
| dl         |                              |
| dt         |                              |
| em         |                              |
| fieldset   |                              |
| h1         |                              |
| h2         |                              |
| h3         |                              |
| h4         |                              |
| h5         |                              |
| h6         |                              |
| hr         |                              |
| i          |                              |
| img        | alt，src，height，width         |
| ins        |                              |
| label      |                              |
| legend     |                              |
| li         |                              |
| ol         | start，type                   |
| p          |                              |
| q          |                              |
| span       |                              |
| strong     |                              |
| sub        |                              |
| sup        |                              |
| table      | width                        |
| tbody      |                              |
| td         | colspan，height，rowspan，width |
| tfoot      |                              |
| th         | colspan，height，rowspan，width |
| thead      |                              |
| tr         |                              |
| ul         |                              |

> 📘 Bugs and tips
> 
> - Tip: We recommend you not use the `String` type for `nodes` as it will decrease the performance.
> - Tip: We recommend you block all node events in the `rich-text` component.
> - Tip: The `attrs` attribute is supported for `class` but not `id`.
> - Tip: The `name` attribute is case-insensitive.
> - Tip: If an untrusted HTML node is used, the node and all its child nodes will be removed.
> - Tip: The `img` tag is supported for online images only.
> - Tip: If the `rich-text` component is used in a custom component, only the `wxss` style of the custom component will take effect for the class in `rich-text`.

### Sample code

```javascript
// javascript
Page({
  data: {
    nodes: [{
      name: 'div',
      attrs: {
        class: 'div_class',
        style: 'line-height: 60px; color: red;'
      },
      children: [{
        type: 'text',
        text: 'Hello&nbsp;World!'
      }]
    }]
  },
  tap() {
  	console.log('tap')
  }
})
```
```xml
<!--WXML-->
{% raw %}
<rich-text nodes="{{nodes}}" bindtap="tap"></rich-text>
{% endraw %}
```
