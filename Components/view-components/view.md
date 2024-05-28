---
title: "View"
slug: "view"
excerpt: "View container."
hidden: false
metadata: 
  image: []
  robots: "index"
createdAt: "Thu Apr 06 2023 06:33:35 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Fri Jul 14 2023 11:03:40 GMT+0000 (Coordinated Universal Time)"
layout: "default"
parent: "View components"
grand_parent: "Components"
---
A view container represents container that can host one or more views.

| Attribute              | Type    | Default Value | Required | Description                                                                                                       |
| :--------------------- | :------ | :------------ | :------- | :---------------------------------------------------------------------------------------------------------------- |
| hover-class            | String  | none          | No       | Style class when the user clicks the button. If `hover-class="none"` is set, there will be no click state effect. |
| hover-stop-propagation | Boolean | false         | No       | Whether to prevent the ancestor node of view from getting the click event.                                        |
| hover-start-time       | Number  | 50            | No       | How long in milliseconds the click state is triggered after the screen is pressed.                                |
| hover-stay-time        | Number  | 400           | No       | Click state retention period in milliseconds after the user lifts the finger.                                     |
| aria-role              | String  |               | No       | Accessibility, which uses the role to identify the purposes of element.                                           |
| aria-label             | String  |               | No       | Accessibility, which is the additional description of the element.                                                |

> 📘 Notes
> 
> - If you have large content and scrolling is needed, use the [scroll-view](doc:scroll-view) component.

### Sample code

```xml WXML
<view class="section">
  <view class="section__title">flex-direction: row</view>
  <view class="flex-wrp" style="flex-direction:row;">
    <view class="flex-item bc_cyanblue">A</view>
    <view class="flex-item bc_blue">B</view>
    <view class="flex-item bc_grey">C</view>
  </view>
</view>
<view class="section">
  <view class="section__title">flex-direction: column</view>
  <view class="flex-wrp" style="height: 300px;flex-direction:column;">
    <view class="flex-item bc_cyanblue">A</view>
    <view class="flex-item bc_blue">B</view>
    <view class="flex-item bc_grey">C</view>
  </view>
</view>
```
```Text WXSS
.flex-item {
    width: 33%;
    height: 150rpx;
}

.bc_cyanblue {
    background-color: #00FFFF;
}

.bc_blue {
    background-color: #0000FF;
}

.bc_grey {
    background-color: #808080;
}
```

![](https://files.readme.io/c998e8e-Screenshot_2023-06-12_at_12.08.05_PM.png)

> 🚧 Bugs and tips
> 
> - Tip: To use scroll view, use [scroll-view](doc:scroll-view).
