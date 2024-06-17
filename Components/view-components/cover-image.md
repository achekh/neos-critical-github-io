---
title: "Cover image"
slug: "cover-image"
excerpt: "An image view that renders images natively."
hidden: false
metadata: 
  image: []
  robots: "index"
createdAt: "Wed Mar 01 2023 13:52:02 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Tue Jun 13 2023 04:27:38 GMT+0000 (Coordinated Universal Time)"
layout: "default"
parent: "View components"
grand_parent: "Components"
---
# Cover image 
*** 
The image view that covers the native components, which can be nested in `cover-view`. Coverable native components are those listed for `cover- view`.

| Attribute  | Type          | Default | Description                                                                                              |
| :--------- | :------------ | :------ | :------------------------------------------------------------------------------------------------------- |
| src        | String        |         | Icon path, which can be a temporary path or network address. Base64-encoding is not supported currently. |
| bindload   | Event Handler |         | Triggered upon image loading success                                                                     |
| binderror  | Event Handler |         | Triggered upon image loading failure                                                                     |
| aria-role  | String        |         | Accessibility, which uses the role to identify the purposes of elements.                                 |
| aria-label | String        |         | Accessibility, which is the additional description of the (attribute) element.                           |

> 📘 Bugs and tips
> 
> - Tip: You can set the aria-role of `[<cover-view>](<>)` and `<cover-image>` only to `button`, which can be clicked only in screen reading mode, with the button text read out. If it is empty, it can be focused but not clicked.
> - Tip: The event model follows the bubble model but will not bubble into native components.
> - Tip: We recommend you add the `cover-view` tag for text to avoid layout errors.
> - Tip: You can only set the basic location, layout, and text style but not `single-side border`, `background-image`, `shadow`, and `overflow: visible`.
> - Tip: Child nodes should not overflow parent nodes.
> - Tip: Default styles are as follows: `white-space: nowrap;` `line-height: 1.2;` `display: block;`
> - Bug: If cover-view is nested in a custom component, the `slot` and parent node of the custom component cannot be shown or hidden through `wx:if`; otherwise, `cover-view` will not be shown.

### Sample code

```javascript JavaScript
Page({
  onReady() {
    this.videoCtx = wx.createVideoContext('myVideo')
  },
  play() {
    this.videoCtx.play()
	}, pause() {
    this.videoCtx.pause()
  }
})
```
```xml
<!--WXML-->
{% raw %}
<video
  id="myVideo"
  src="https://qzonestyle.gtimg.cn/qzone/qzact/act/external/qq-video/qq-video.mp4"
  controls="{{false}}"
  event-model="bubble"
>
  <cover-view class="controls">
    <cover-view class="play" bindtap="play">
      <cover-image class="img" src="/path/to/icon_play" />
    </cover-view>
    <cover-view class="pause" bindtap="pause">
      <cover-image class="img" src="/path/to/icon_pause" />
    </cover-view>
    <cover-view class="time">00:00</cover-view>
  </cover-view>
</video>
{% endraw %}
```
```css
/* WXSS */
.controls {
  position: relative;
  top: 50%;
  height: 50px;
  margin-top: -25px;
  display: flex;
}
.play,
.pause,
.time {
flex: 1;
  height: 100%;
}
.time {
  text-align: center;
  background-color: rgba(0, 0, 0, 0.5);
  color: white;
  line-height: 50px;
} .img {
  width: 40px;
  height: 40px;
  margin: 5px auto;
}
```
