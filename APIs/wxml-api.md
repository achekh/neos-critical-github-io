---
title: "WXML"
slug: "wxml-api"
excerpt: "This section lists the WXML APIs."
hidden: false
createdAt: "Mon Apr 24 2023 08:43:22 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Wed Nov 29 2023 18:28:29 GMT+0000 (Coordinated Universal Time)"
layout: "default"
parent: "APIs"
nav_order: 13
---
# WXML 
This section lists the WXML APIs.

***

| Name                                                                                                                  | Feature Description                                            |
| :-------------------------------------------------------------------------------------------------------------------- | :------------------------------------------------------------- |
| [createSelectorQuery](wxml-api#selectorquery-wxcreateselectorquery)                                               | Returns a `SelectorQuery` object instance.                     |
| [createIntersectionObserver](wxml-api#intersectionobserver-wxcreateintersectionobserverobject-thisobject-options) | Creates and returns an `IntersectionObserver` object instance. |

### IntersectionObserver

| Name                                                                                                            | Feature Description                                                                |
| :-------------------------------------------------------------------------------------------------------------- | :--------------------------------------------------------------------------------- |
| [IntersectionObserver.disconnect](wxml-api#intersectionobserverdisconnect)                                  | Unlistens.                                                                         |
| [IntersectionObserver.observe](wxml-api#intersectionobserverobservestring-targetselector-function-callback) | Specifies the target node and starts listening for the intersection status change. |
| [IntersectionObserver.relativeTo](wxml-api#intersectionobserverrelativetostring-selector-object-margins)    | Uses the selector to specify a node as one of the reference areas.                 |
| [IntersectionObserver.relativeToViewport](wxml-api#intersectionobserverrelativetoviewportobject-margins)    | Specifies the page display area as one of the reference areas.                     |

### NodesRef

| Name                                                                                                  | Feature Description                                       |
| :---------------------------------------------------------------------------------------------------- | :-------------------------------------------------------- |
| [NodesRef.boundingClientRect](wxml-api#selectorquery-nodesrefboundingclientrectfunction-callback) | Adds a query request for the layout position of the node. |
| [NodesRef.context](wxml-api#selectorquery-nodesrefcontextfunction-callback)                       | Adds a query request for the context object of the node.  |
| [NodesRef.fields](wxml-api#nodesreffieldsobject-fields)                                           | Gets the node information.                                |
| [NodesRef.node](wxml-api#node)                                                                    | Gets the node instance.                                   |
| [NodesRef.scrollOffset](wxml-api#selectorquery-nodesrefscrolloffsetfunction-callback)             | Adds a query request for the scroll position of the node. |

### SelectorQuery

| Name                                                                                   | Feature Description                                                            |
| :------------------------------------------------------------------------------------- | :----------------------------------------------------------------------------- |
| [SelectorQuery.exec](wxml-api#nodesref-selectorqueryexecfunction-callback)         | Executes all requests.                                                         |
| [SelectorQuery.in](wxml-api#selectorquery-selectorqueryincomponent-component)      | Changes the selection scope of the selector to be within the custom component. |
| [SelectorQuery.select](wxml-api#nodesref-selectorqueryselectstring-selector)       | Selects the first node matching the selector on the current page.              |
| [SelectorQuery.selectAll](wxml-api#nodesref-selectorqueryselectallstring-selector) | Selects all the nodes matching the selector on the current page.               |
| [SelectorQuery.selectViewport](wxml-api#nodesref-selectorqueryselectviewport)      | Selects the display area.                                                      |

# SelectorQuery wx.createSelectorQuery()

Returns a `SelectorQuery` object instance. In custom components or on pages containing custom components, `this.createSelectorQuery()` should be used instead.

## Returned value

[SelectorQuery](<>)

### Sample code

```javascript
// JavaScript
const query = wx.createSelectorQuery()
query.select('#the-id').boundingClientRect()
query.selectViewport().scrollOffset()
query.exec(function (res) {
  res[0].top // Top boundary coordinate of the `#the-id` node
  res[1].scrollTop // Vertical scroll position of the display area
})
```

# IntersectionObserver wx.createIntersectionObserver(Object this,Object options)

Creates and returns an `IntersectionObserver` object instance. In custom components or on pages containing custom components, `this.createIntersectionObserver([options]) ` should be used instead.

# Parameters

**Object this**

Custom component instance.

**Object options**

| Attribute | Type | Default | Required | Description |
| :-------- | :--- | :------ | :------- | :---------- |
| thresholds | Array.\<number> | \\[bl | No | The value array containing all thresholds. |
| initialRatio | Number | 0 | No | Initial intersection ratio. If the intersection ratio detected during the call is not equal to this value and the threshold is reached, the callback function of the listener will be triggered once. |
| observeAll | Boolean | false | No | Whether to observe multiple target nodes at the same time. If this parameter is set to true, the targetSelector of observe will select multiple nodes. (Note: Selecting too many nodes at the same time will affect the rendering performance.) |

## Returned value

[IntersectionObserver](wxml-api#intersectionobserver-1)

# IntersectionObserver

`IntersectionObserver` object, which is used to infer whether certain nodes and what proportion of of nodes are visaible to the user.

## Methods

- [IntersectionObserver.relativeTo(string selector, Object margins)](wxml-api#intersectionobserverrelativetostring-selector-object-margins)  
  Uses the selector to specify a node as one of the reference areas.
- [IntersectionObserver.relativeToViewport(Object margins)](wxml-api#intersectionobserverrelativetoviewportobject-margins)  
  Specifies the page display area as one of the reference areas.
- [IntersectionObserver.observe(string targetSelector, IntersectionObserver.observeCallback callback)](wxml-api#intersectionobserverobservestring-targetselector-function-callback)  
  Specifies the target node and listens for the intersection status change.
- [IntersectionObserver.disconnect()](wxml-api#intersectionobserverdisconnect)  
  Unlistens.The callback function will no longer be triggered.

# disconnect

## IntersectionObserver.disconnect()

Unlistens. The callback function will no longer be triggered.

# observe

## IntersectionObserver.observe(string targetSelector, function callback)

Specifies the target node and listens for the intersection status change.

# Parameters

### string targetSelector

Selector

## Function callback

Callback function for the intersection status changes.

# Parameters

**Object res**

| Attribute          | Type   | Description                          |
| :----------------- | :----- | :----------------------------------- |
| intersectionRatio  | Number | Intersection ratio.                  |
| intersectionRect   | Object | Boundary of the intersection area.   |
| boundingClientRect | Object | Destination boundary.                |
| relativeRect       | Object | Boundary of the reference area.      |
| time               | Number | Timestamp of intersection detection. |

Structure of `res.intersectionRect`

| Attribute | Type   | Description     |
| :-------- | :----- | :-------------- |
| left      | Number | Left boundary   |
| right     | Number | Right boundary  |
| top       | Number | Top boundary    |
| bottom    | Number | Bottom boundary |

Structure of `res.boundingClientRect`

| Attribute | Type   | Description     |
| :-------- | :----- | :-------------- |
| left      | Number | Left boundary   |
| right     | Number | Right boundary  |
| top       | Number | Top boundary    |
| bottom    | Number | Bottom boundary |

Structure of `res.relativeRect`

| Attribute | Type   | Description     |
| :-------- | :----- | :-------------- |
| left      | Number | Left boundary   |
| right     | Number | Right boundary  |
| top       | Number | Top boundary    |
| bottom    | Number | Bottom boundary |

# relativeTo

## IntersectionObserver.relativeTo(string selector, Object margins)

Uses the selector to specify a node as one of the reference areas.

# Parameters

### string selector

Selector

### Object margins

The boundaries used to expand (or shrink) the reference node layout area.

| Attribute | Type   | Default | Required | Description                              |
| :-------- | :----- | :------ | :------- | :--------------------------------------- |
| left      | Number |         | No       | Left boundary of the node layout area.   |
| right     | Number |         | No       | Right boundary of the node layout area.  |
| top       | Number |         | No       | Top boundary of the node layout area.    |
| bottom    | Number |         | No       | Bottom boundary of the node layout area. |

# relativeToViewport

## IntersectionObserver.relativeToViewport(Object margins)

Specifies the page display area as one of the reference areas.

# Parameters

**Object margins**

The boundaries used to expand (or shrink) the reference node layout area

| Attribute | Type   | Default | Required | Description                             |
| :-------- | :----- | :------ | :------- | :-------------------------------------- |
| left      | Number |         | No       | Left boundary of the node layout area   |
| right     | Number |         | No       | Right boundary of the node layout area  |
| top       | Number |         | No       | Top boundary of the node layout area    |
| bottom    | Number |         | No       | Bottom boundary of the node layout area |

### Sample code

In the sample code below, if the target node (specified with the `.target-class` selector) enters 100 px below the display area, the callback function will be triggered.

```javascript
// JavaScript
Page({
  onLoad() {
    wx.createIntersectionObserver().relativeToViewport({bottom: 100}).observe('.target-class', (res) => {
      res.intersectionRatio // The ratio of the intersection area to the layout area of the target node
      res.intersectionRect // Intersection area
      res.intersectionRect.left // Left boundary coordinate of the intersection area
      res.intersectionRect.top // Top boundary coordinate of the intersection area
      res.intersectionRect.width // Intersection area width
      res.intersectionRect.height // Intersection area height
    })
  }
})
```

# NodesRef

Gets the WXML node information.

## Methods

- [NodesRef.fields(Object fields)](dco:wxml-api#nodesreffieldsobject-fields)  
  Gets the node information. The fields to be obtained are specified in fields . The returned value is the selectorQuery corresponding to nodesRef .
- [SelectorQuery NodesRef.boundingClientRect(NodesRef.boundingClientRectCallback callback)](wxml-api#selectorquery-nodesrefboundingclientrectfunction-callback)  
  Adds a query request for the layout position of the node, which is relative to the display area and in px. Its feature is similar to getBoundingClientRect  
  of DOM. The returned value is the SelectorQuery corresponding to NodesRef .
- [SelectorQuery NodesRef.scrollOffset(NodesRef.scrollOffsetCallback callback)](wxml-api#selectorquery-nodesrefscrolloffsetfunction-callback)  
  Adds a query request for the scroll position of the node in px. The node must be scroll-view or viewport , and the returned value is the SelectorQuery corresponding to NodesRef .
- [SelectorQuery NodesRef.context(NodesRef.contextCallback callback)](wxml-api#selectorquery-nodesrefcontextfunction-callback)  
  Adds a query request for the context object of the node. Currently, MapContext can be obtained.
- [SelectorQuery NodesRef.node(NodesRef.nodeCallback callback)](wxml-api#node)  
  Gets the node instance. Currently, ScrollViewContext can be obtained.  
  Currently, Canvas can be obtained.

# boundingClientRect

## SelectorQuery NodesRef.boundingClientRect(function callback)

Adds a query request for the layout position of the node, which is relative to the display area and in px. Its feature is similar to getBoundingClientRect of DOM. The returned value is the `SelectorQuery` corresponding to `NodesRef`.

# Parameters

## Function callback

Callback function. After the `[SelectorQuery.exec](<>)` method is executed, the node information will be returned in `callback `.

# Parameters

**Object res**

| Attribute | Type   | Description                             |
| :-------- | :----- | :-------------------------------------- |
| id        | String | Node ID.                                |
| dataset   | Object | Node dataset.                           |
| left      | Number | Left boundary coordinate of the node.   |
| right     | Number | Right boundary coordinate of the node.  |
| top       | Number | Top boundary coordinate of the node.    |
| bottom    | Number | Bottom boundary coordinate of the node. |
| width     | Number | Node width.                             |
| height    | Number | Node height.                            |

## Returned value

`SelectorQuery`

### Sample code

```javascript
// JavaScript
Page({
  getRect() {
    wx.createSelectorQuery().select('#the-id').boundingClientRect(function (rect) {
      rect.id // Node ID
      rect.dataset // Node dataset
      rect.left // Left boundary coordinate of the node
      rect.right // Right boundary coordinate of the node
      rect.top // Top boundary coordinate of the node
      rect.bottom // Bottom boundary coordinate of the node
      rect.width // Node width
      rect.height // Node height
     }).exec()
   },
   getAllRects() {
    wx.createSelectorQuery().selectAll('.a-class').boundingClientRect(function (rects) {
    rects.forEach(function (rect) {
      rect.id // Node ID
      rect.dataset // Node dataset
      rect.left // Left boundary coordinate of the node
      rect.right // Right boundary coordinate of the node
      rect.top // Top boundary coordinate of the node
      rect.bottom // Bottom boundary coordinate of the node
      rect.width // Node width
      rect.height // Node height
      })
    }).exec()
  }
})
```

# context

## SelectorQuery NodesRef.context(function callback)

Adds a query request for the context object of the node. Currently, [`MapContext `](media/map-api#mapcontext)can be obtained.

# Parameters

## Function callback

Callback function, which will return the node information after the `[SelectorQuery.exec](<>)` method is executed.

# Parameters

**Object res**

| Attribute | Type   | Description                 |
| :-------- | :----- | :-------------------------- |
| context   | Object | Context object of the node. |

## Returned value

`SelectorQuery`

### Sample code

```javascript
// JavaScript
Page({
  getContext() {
    wx.createSelectorQuery().select('.the-video-class').context(function (res) {
   	 console.log(res.context) // Context object of the node For example, if the selected node is the <video> component, then the
  `VideoContext` object will be returned here.
    }).exec()
  }
})
```

# fields

## NodesRef.fields(Object fields)

Gets the node information. The fields to be obtained are specified in` fields` . The returned value is the `selectorQuery` corresponding to `nodesRef` .

# Parameters

**Object fields**

| Attribute | Type | Default | Required | Description |
| :-------- | :--- | :------ | :------- | :---------- |
| id | Boolean | false | No | Whether to return the node ID. |
| dataset | Boolean | false | No | Whether to return the node dataset. |
| rect | Boolean | false | No | Whether to return the layout position of the node `( left , right , top , bottom )`. |
| size | Boolean | false | No | Whether to return the node size ( width , height ). |
| scrollOffset | Boolean | false | No | Whether to return the `scrollLeft` and `scrollTop `of a `scroll-view` or `viewport `node. |
| context | Boolean | false | No | Whether to return the context object of the node. |

> 📘 Notes
> 
> `computedStyle` has a higher priority than `size`. If` width` and `height` are specified in `computedStyle` and `size: true` is passed in, then the `width`  
> and `height` obtained by `computedStyle` will be returned first.

### Sample code

```javascript
// JavaScript
Page({
  getFields() {
    wx.createSelectorQuery().select('#the-id').fields({
      dataset: true,
      size: true,
      scrollOffset: true,
      properties: ['scrollX', 'scrollY'],
      computedStyle: ['margin', 'backgroundColor'],
      context: true,
    }, function (res) {
      res.dataset // Node dataset
      res.width // Node width
      res.height // Node height
      res.scrollLeft // Horizontal scroll position of the node
      res.scrollTop // Vertical scroll position of the node
      res.scrollX // The current value of the `scroll-x` attribute of the node
      res.scrollY // The current value of the `scroll-y` attribute of the node
      // The style name specified to be returned will be returned here.
      res.margin
      res.backgroundColor
      res.context // Context object of the node
   }).exec()
  }
})
```

# Node

`SelectorQuery` NodesRef.Node(function callback)

Gets the node instance. Currently, [ScrollViewContext](ui-api/scroll#scrollviewcontext) can be obtained.  
Currently, [Canvas](../Guide/basic-capabilities/canvas) can be obtained.

# Parameters

## Function callback

Callback function, which will return the node information after the `SelectorQuery.exec` method is executed.

**Parameters**  
**Object res**

| Attribute | Type   | Description   |
| :-------- | :----- | :------------ |
| node      | Object | Node instance |

## Returned value

`SelectorQuery`

### Sample code

```javascript
// JavaScript
Page({
  getNode() {
    wx.createSelectorQuery().select('.canvas').node(function(res){
   		 console.log(res.node) // Canvas instance of the node
    }).exec()
  }
})
```

# scrollOffset

## SelectorQuery NodesRef.scrollOffset(function callback)

Adds a query request for the scroll position of the node in px. The node must be scroll-view or viewport , and the returned value is the `SelectorQuery` corresponding to `NodesRef `.

# Parameters

## Function callback

Callback function. After the [`SelectorQuery.exec`](wxml-api#nodesref-selectorqueryexecfunction-callback) method is executed, the node information will be returned in `callback `.

**Parameters**  
**Object res**

| Attribute  | Type   | Description                             |
| :--------- | :----- | :-------------------------------------- |
| id         | String | Node ID.                                |
| dataset    | Object | Node dataset.                           |
| scrollLeft | Number | Horizontal scroll position of the node. |
| scrollTop  | Number | Vertical scroll position of the node.   |

## Returned value

`SelectorQuery`

### Sample code

```javascript
// JavaScript
Page({
  getScrollOffset() {
    wx.createSelectorQuery().selectViewport().scrollOffset(function (res) {
      res.id // Node ID
      res.dataset // Node dataset
      res.scrollLeft // Horizontal scroll position of the node
      res.scrollTop // Vertical scroll position of the node
    }).exec()
  }
})
```

# SelectorQuery

Queries the node information.

## Methods

[SelectorQuery SelectorQuery.in(Component component)](wxml-api#selectorquery-selectorqueryincomponent-component)  
Changes the selection scope of the selector to be within the custom component. (Initially, the selector only selects nodes on the page but not in any custom components).

[NodesRef SelectorQuery.select(string selector)](wxml-api#nodesref-selectorqueryselectstring-selector)  
Selects the first node matching the selector on the current page. A `[NodesRef](<>)` object instance will be returned, which can be used to get node information.

[NodesRef SelectorQuery.selectAll(string selector)](wxml-api#nodesref-selectorqueryselectallstring-selector)  
Selects all the nodes matching the selector on the current page.

[NodesRef SelectorQuery.selectViewport()](wxml-api#nodesref-selectorqueryselectviewport)  
Selects the display area. It can be used to obtain information such as the size of the display area and scroll position.

[NodesRef SelectorQuery.exec(function callback)](wxml-api#nodesref-selectorqueryexecfunction-callback)  
Executes all requests. The request results form an array in sequence, which is returned in the first parameter of `callback`.

# exec

## NodesRef SelectorQuery.exec(function callback)

Executes all requests. The request results form an array in sequence, which is returned in the first parameter of `callback`.

# Parameters

## Function callback

Callback function

## Returned value

`NodesRef`

# in

## SelectorQuery SelectorQuery.in(Component component)

Changes the selection scope of the selector to be within the custom component. (Initially, the selector only selects nodes on the page but not in any custom components).

# Parameters

### Component component

Custom component instance

### Returned value

`SelectorQuery`

### Sample code

```javascript
// JavaScript
Component({
  queryMultipleNodes() {
    const query = wx.createSelectorQuery().in(this)
    query.select('#the-id').boundingClientRect(function (res) {
   		 res.top // Top boundary coordinate of the #the-id node in the component
    }).exec()
  }
})
```

# select

## NodesRef SelectorQuery.select(string selector)

Selects the first node matching the selector on the current page. A `[NodesRef](<>)` object instance will be returned, which can be used to get node information.

# Parameters

### string selector

Selector

## Returned value

`NodesRef`

## Selector syntax

A selector is similar to a CSS selector but only supports the following syntax.

- ID selector: #the-id.
- Class selector (multiple items can be specified consecutively): .a-class.another-class.
- Subelement selector: .the-parent > .the-child.
- Descendant selector: .the-ancestor .the-descendant.
- Descendant selector across custom components: .the-ancestor >>> .the-descendant.
- Union of multiple selectors: #a-node, .some-other-nodes.

# selectAll

## NodesRef SelectorQuery.selectAll(string selector)

Selects all the nodes matching the selector on the current page.

# Parameters

### string selector

Selector

## Returned value

`NodesRef`

## Selector syntax

A selector is similar to a CSS selector but only supports the following syntax.

- ID selector: #the-id.
- Class selector (multiple items can be specified consecutively): .a-class.another-class.
- Subelement selector: .the-parent > .the-child.
- Descendant selector: .the-ancestor .the-descendant.
- Descendant selector across custom components: .the-ancestor >>> .the-descendant.
- Union of multiple selectors: #a-node, .some-other-nodes.

# selectViewport

## NodesRef SelectorQuery.selectViewport()

Selects the display area. It can be used to obtain information such as the size of the display area and scroll position.

## Returned value

`NodesRef`
