---
title: "Movable area"
slug: "movable-area"
excerpt: "A host view for the moveable view."
hidden: false
metadata: 
  image: []
  robots: "index"
createdAt: "Wed Apr 05 2023 07:40:17 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Tue Jun 13 2023 04:29:55 GMT+0000 (Coordinated Universal Time)"
layout: "default"
parent: "View components"
grand_parent: "Components"
nav_order: 5
---
# Movable area 
A host view for the moveable view.

***

A component that hosts the [moveable-view](movable-view).

| Attribute  | Type    | Default Value | Description                                                                                                                                                          |
| :--------- | :------ | :------------ | :------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| scale-area | Boolean | False         | If two-finger pinch-to-zoom is supported in `movable-view`, the area for which the zoom gesture takes effect can be changed to `movable-area` by setting this value. |

> 📘 Notes
> 
> - You need to set the `width` and `height` attributes for movable-area; otherwise, the default value of 10 px is used. 
> - When the [movable-view](movable-view) is smaller than the movable-area, the movable-view moves within the movable-area.
> - When [movable-view](movable-view) is larger than movable-area, the moveable-view must move within a moveable-area (x and y directions are considered separately).

### Sample code

```javascript
// javascript
Page({
  data: {
    x: 0,
    y: 0
  },
  tap(e) {
    this.setData({
      x: 30,
      y: 30
    })
  },
  onChange(e) {
  	console.log(e.detail)
  },
  onScale(e) {
  	console.log(e.detail)
  }
})
```
```xml
// WXML
{% raw %}
<view class="section">
  <view class="section__title">`movable-view` smaller than `movable-area`</view>
  <movable-area style="height: 200px; width: 200px; background: red;">
    <movable-view
      style="height: 50px; width: 50px; background: blue;"
      x="{{x}}"
      y="{{y}}"
      direction="all">
    </movable-view>
  </movable-area>
  <view class="btn-area">
  	<button size="mini" bindtap="tap">click me to move to (30px, 30px)</button>
  </view>
  <view class="section__title">`movable-view` larger than `movable-area`</view>
  <movable-area style="height: 100px; width: 100px; background: red;">
    <movable-view
      style="height: 200px; width: 200px; background: blue;"
      direction="all">
    </movable-view>
  </movable-area>
  <view class="section__title">Zoom support</view>
  <movable-area
    style="height: 200px; width: 200px; background: red;"
    scale-area>
    <movable-view
      style="height: 50px; width: 50px; background: blue;"
      direction="all"
      bindchange="onChange"
      bindscale="onScale"
      scale
      scale-min="0.5"
      scale-max="4"
      scale-value="2">
    </movable-view>
  </movable-area>
</view>
{% endraw %}
```
