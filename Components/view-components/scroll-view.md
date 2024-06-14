---
title: "Scroll view"
slug: "scroll-view"
excerpt: "Scrollable view container."
hidden: false
metadata: 
  image: []
  robots: "index"
createdAt: "Wed Apr 05 2023 08:19:52 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Mon Jun 12 2023 05:52:33 GMT+0000 (Coordinated Universal Time)"
layout: "default"
parent: "View components"
grand_parent: "Components"
---
# Scroll view 
*** 
To scroll vertically, you need to set a fixed height for `<scroll-view>` through WXSS.

| Attribute             | Type          | Default Value | Required | Description                                                                                                                                     |
| :-------------------- | :------------ | :------------ | :------- | :---------------------------------------------------------------------------------------------------------------------------------------------- |
| scroll-x              | Boolean       | false         | No       | Allow horizontal scrolling.                                                                                                                     |
| scroll-y              | Boolean       | false         | No       | Allow vertical scrolling.                                                                                                                       |
| upper-threshold       | Number/String | 50            | No       | Distance in px from the top/left border to trigger the `scrolltoupper` event.                                                                   |
| lower-threshold       | Number/String | 50            | No       | Distance in px from the bottom/right border to trigger the `scrolltolower` event.                                                               |
| scroll-top            | Number/string |               | No       | Set vertical scroll bar position.                                                                                                               |
| scroll-left           | Number/String |               | No       | Set horizontal scroll bar position.                                                                                                             |
| scroll-into-view      | String        |               | No       | Child element ID, which cannot start with a digit. The child element will be reached in the configured `scrollable` direction.                  |
| scroll-with-animation | Boolean       | false         | No       | Use animation transitions when setting the scroll bar position.                                                                                 |
| enable-back-to-top    | Boolean       | false         | No       | Whether to vertically move the scroll box back to the top when the user clicks the status bar on iOS or double-clicks the title bar on Android. |
| enhanced              | boolean       | false         | No       | After you enable enhanced, scroll-view can be operated through `ScrollViewContext`.                                                             |
| bounces               | Boolean       | true          | No       | Scroll-view boundary elastic control under iOS (effective after enabling the enhanced attribute at the same time).                              |
| show-scrollbar        | Boolean       | true          | No       | Scroll bar visible and hidden control (effective after enabling the enhanced attribute at the same time).                                       |
| paging-enabled        | Boolean       | false         | No       | Page sliding effect (effective after enabling the enhanced attribute at the same time)                                                          |
| fast-deceleration     | Boolean       | false         | No       | Sliding deceleration rate control, only effective under iOS (effective after enabling the enhanced attribute at the same time).                 |
| bindscrolltoupper     | Event Handler |               | No       | Event triggered when the UI is scrolled to the top/left.                                                                                        |
| bindscrolltolower     | Event Handler |               | No       | Event triggered when the UI is scrolled to the bottom/right.                                                                                    |
| bindscroll            | Event Handler |               | No       | The event triggered when the UI is scrolled: `event.detail = {scrollLeft, scrollTop, scrollHeight, scrollWidth, deltaX, deltaY}`.               |
| aria-label            | String        |               | No       | Accessibility, which is the additional description of the element.                                                                              |

> 📘 Notes
> 
> - `scroll-into-view` has a higher priority than `scroll-top`.
> - Do not use the `textarea`, `map`, `canvas`, or `video` component in `scroll-view`.
> - When the content in `scroll-view` is scrolled, page bounce will be prevented. Therefore, when the UI is scrolled in `scroll-view`,  
>   `onPullDownRefresh` cannot be triggered.
> - To use `pull-to-refresh`, use page scroll rather than `scroll-view`. This allows clicking the top status bar to go back to the top.

To scroll vertically, you need to set a fixed height for `<scroll-view>` through wxss.

### Sample code

```javascript
const order = ['red', 'yellow', 'blue', 'green', 'red']
Page({
  data: {
    toView: 'red',
    scrollTop: 100
	}, 
  upper(e) {
    console.log(e)
  },
  lower(e) {
    console.log(e)
  },
  scroll(e) {
    console.log(e)
  },
  tap(e) {
    for (let i = 0; i < order.length; ++i) {
      if (order[i] === this.data.toView) {
        this.setData({
          toView: order[i + 1]
        })
			break;
			} 
    }
  },
  tapMove(e) {
    this.setData({
      scrollTop: this.data.scrollTop + 10
		}) 
  }
});
```
```xml WXML
<view class="section">
  <view class="section__title">vertical scroll</view>
  <view class="section__title">Vertical scroll</view>
  <scroll-view
    scroll-y
    style="height: 200px;"
    bindscrolltoupper="upper"
    bindscrolltolower="lower"
    bindscroll="scroll"
    scroll-into-view="{{toView}}"
    scroll-top="{{scrollTop}}"
  >
    <view id="green" class="scroll-view-item bc_cyanblue">A</view>
    <view id="red" class="scroll-view-item bc_blue">B</view>
  </scroll-view>
</view>
<view class="section section_gap">
  <view class="section__title">horizontal scroll</view>
  <view class="section__title">Horizontal scroll</view>
  <scroll-view class="scroll-view_H" scroll-x style="width: 100%">
    <view id="green" class="scroll-view-item_H bc_cyanblue"></view>
    <view id="red" class="scroll-view-item_H bc_blue"></view>
  </scroll-view>
</view>
```

### Bugs and tips

1. Tip: Do not use the `textarea`, `map`, `canvas`, or video component in `scroll-view`.
2. Tip: `scroll-into-view` has a higher priority than `scroll-top`.
3. Tip: When the content in `scroll-view` is scrolled, page bounce will be prevented. Therefore, when the UI is scrolled in `scroll-view`, `onPullDownRefresh` cannot be triggered.
4. Tip: To use pull-to-refresh, use page scroll rather than `scroll-view`. This allows clicking the top status bar to go back to the top.
