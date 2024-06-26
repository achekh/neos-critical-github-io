---
title: "Cover view"
slug: "cover-view"
excerpt: "A view holder for native views that renders natively."
hidden: false
metadata: 
  image: []
  robots: "index"
createdAt: "Wed Apr 05 2023 06:30:20 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Fri Jul 14 2023 11:04:15 GMT+0000 (Coordinated Universal Time)"
layout: "default"
parent: "View components"
grand_parent: "Components"
nav_order: 8
---
# Cover view 
A view holder for native views that renders natively.

***

A native component that supports same-layer rendering, and it is recommended to use the [view](view) instead where applicable. Coverable native components include [map](../map-capability/map), [video](../media-components/video), [canvas](../canvas-component/canvas) and [camera](../media-components/camera).

| Attribute  | Type          | Description                                                                                            |
| :--------- | :------------ | :----------------------------------------------------------------------------------------------------- |
| scroll-top | Number/String | Set the top scroll offset only when the `overflow-y: scroll ` as the view becomes a scrolling element. |
| aria-role  | String        | Accessibility, which uses the role to identify the purposes of element.                                |
| aria-label | String        | Accessibility, which is the additional description of the (attribute) element.                         |

> 📘 Notes
> 
> - `<cover-view>` `aria-role` can only be set to `button`.
> - The event model follows the bubbling model but does not bubble to native components.
> - Only basic positioning, layout, and text styles are supported. Does not support `settings`, `unilateral border`, `background-image`, `shadow` and `overflow: visibleWait`.
> - Make sure child nodes not to overflow parent nodes.
> - Supports the use of z-index level adjustment.
> - The default styles are: `white-space: nowrap line-height: 1.2  display: block`.

### Sample code

```javascript
// javascript
Page({
  onShareAppMessage() {
    return {
      title: 'cover-view',
      path: 'page/component/pages/cover-view/cover-view'
    }
  },
  data: {
    latitude: 23.099994,
    longitude: 113.324520,
  }
})
```
```xml
<!--WXML-->
{% raw %}
<view class="container">
  <view class="page-body">
    <view class="page-section page-section-gap">
      <map
        style="width: 100%; height: 300px;"
        latitude="{{latitude}}"
        longitude="{{longitude}}"
      >
        <cover-view class="cover-view">
          <cover-view class="container">
            <cover-view class="flex-wrp" style="flex-direction:row;">
              <cover-view class="flex-item demo-text-1"></cover-view>
              <cover-view class="flex-item demo-text-2"></cover-view>
              <cover-view class="flex-item demo-text-3"></cover-view>
            </cover-view>
          </cover-view>
        </cover-view>
      </map>
    </view>
  </view>
</view>
{% endraw %}
```
```css
/* WXSS */
.cover-view {
  position: absolute;
  top: calc(50% - 150rpx);
  left: calc(50% - 300rpx);
}

.flex-wrp{
  display:flex;
}

.flex-item{
  width: 200rpx;
  height: 300rpx;
  font-size: 26rpx;
}

.demo-text-1 {
  background: rgba(26, 173, 25, 0.7);
}

.demo-text-2 {
  background: rgba(39, 130, 215, 0.7);
}

.demo-text-3 {
  background: rgba(255, 255, 255, 0.7);
}
```
