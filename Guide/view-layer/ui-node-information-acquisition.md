---
title: "UI Node Information Acquisition"
slug: "ui-node-information-acquisition"
excerpt: ""
hidden: false
metadata: 
  image: []
  robots: "index"
createdAt: "Tue May 23 2023 11:18:00 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Thu Jun 08 2023 10:21:49 GMT+0000 (Coordinated Universal Time)"
layout: "default"
parent: "View Layer"
grand_parent: "Guide"
---
# UI Node Information Acquisition 
*** 
## WXML node information

The node information query API can be used to get information such as node attributes, styles, and positions on the UI.

Most commonly, it is used to query the current position of a node and the scrolling position of the UI.

### Sample code:

```javascript
const query = wx.createSelectorQuery()
query.select('#the-id').boundingClientRect(function (res) {
  res.top // Top boundary coordinate of the `#the-id` node (relative to the display area)
})
query.selectViewport().scrollOffset(function (res) {
  res.scrollTop // Vertical scroll position of the display area
})
query.exec()
```

In the above sample, `#the-id` is a node selector, which is similar to a CSS selector but slightly different.

In custom components or on pages containing custom components, we recommend you use `this.createSelectorQuery` instead of `wx.createSelectorQuery`, which ensures that nodes are selected in the correct range.

## WXML node layout intersection status

The node layout intersection status query API can be used to listen for the intersection status of two or more component nodes at layout positions. This API is used to infer whether certain nodes and what proportion of them can be seen by the user.

The main concepts involved in this API are as follows:

- Reference node: The listened reference node, whose layout area is taken as the reference area. If there are multiple reference nodes, the **intersection** of their layout areas will be taken as the reference area. The page display area can also be used as one of the reference areas.
- Target node: The listened target, which can only be one node by default. If the `selectAll` option is used, multiple nodes can be listened at the same time.
- Intersection area: The intersection area of the target node's layout area and the reference area.
- Intersection ratio: The ratio of the intersection area to the reference area.
- Threshold: If the intersection ratio reaches the threshold, the callback function of the listener will be triggered. There can be multiple thresholds.

In the following sample code, the callback function is triggered every time the target node (specified with the `.target-class` selector) enters or leaves the page display area.

### Sample code:

```javascript
Page({
  onLoad() {
    wx.createIntersectionObserver().relativeToViewport().observe('.target-class', (res) => {
      res.id // Target node ID
      res.dataset // Target node dataset
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

In the following sample code, the target node (specified with the `.target-class` selector) and the reference node (specified with the `.relative-class selector`) can be intersected or separated within the display area of the page, and when the ratio of intersection or separation reaches 20% or 50% of the target node's layout area, callback functions will be triggered.

```javascript
Page({
  onLoad() {
    wx.createIntersectionObserver(this, {
      thresholds: [0.2, 0.5]
    }).relativeTo('.relative-class').relativeToViewport().observe('.target-class', (res) => {
      res.intersectionRatio // The ratio of the intersection area to the layout area of the target node
      res.intersectionRect // Intersection area
      res.intersectionRect.left // Left boundary coordinate of the intersection area
      res.intersectionRect.top // Top boundary coordinate of the intersection area
      res.intersectionRect.width // Intersection area width
      res.intersectionRect.height // Intersection area height
    })
} })
```

> 📘 Notes
> 
> The intersection area in the page display area does not accurately represent the area visible to the user, because the area involved in the calculation is the "layout area", which may be cropped and hidden by other nodes during drawing (for example, the overflow style of the ancestor node is `hidden`) or covered (for example, the node position is fixed).

In custom components or on pages containing custom components, we recommend you use `this.createIntersectionObserver` instead of `wx.createIntersectionObserver`, which ensures that nodes are selected in the correct range.
