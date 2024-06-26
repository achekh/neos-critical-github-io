---
title: "Swiper"
slug: "swiper"
excerpt: "A slider view container."
hidden: false
metadata: 
  image: []
  robots: "index"
createdAt: "Wed Apr 05 2023 10:19:19 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Mon Jun 12 2023 05:59:32 GMT+0000 (Coordinated Universal Time)"
layout: "default"
parent: "View components"
grand_parent: "Components"
nav_order: 2
---
# Swiper 
A slider view container.

***

A swiper is a slider view container that can only host a [swiper-item](swiper-item) component.

| Attribute               | Type          | Default Value     | Required | Description                                                                                                                                                                                              |
| :---------------------- | :------------ | :---------------- | :------- | :------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| indicator-dots          | Boolean       | false             | No       | Whether to display dot indicators.                                                                                                                                                                       |
| indicator-color         | Color         | rgba(0, 0, 0, .3) | No       | Dot indicator color.                                                                                                                                                                                     |
| indicator-active-color  | Color         | # 000000          | No       | Color of the currently selected dot indicator.                                                                                                                                                           |
| autoplay                | Boolean       | false             | No       | Whether to enable automatic switching between items.                                                                                                                                                     |
| current                 | Number        | 0                 | No       | Index of the current swiper.                                                                                                                                                                             |
| current-item-id         | String        | ""                | No       | `item-id` of the current swiper, which cannot be specified together with current.                                                                                                                        |
| interval                | Number        | 5000              | No       | Automatic switching interval.                                                                                                                                                                            |
| duration                | Number        | 500               | No       | Swipe animation duration.                                                                                                                                                                                |
| circular                | Boolean       | false             | No       | Whether to enable circular swipe.                                                                                                                                                                        |
| vertical                | Boolean       | false             | No       | Whether to enable vertical swipe.                                                                                                                                                                        |
| previous-margin         | String        | "0px"             | No       | Front margin that can be used to expose a small part of the previous item. Accepts px and rpx values.                                                                                                    |
| next-margin             | String        | "0px"             | No       | Back margin that can be used to expose a small portion of the latter item. Accepts px and rpx values.                                                                                                    |
| display-multiple-items  | Number        | 1                 | No       | Number of sliders displayed simultaneously.                                                                                                                                                              |
| skip-hidden-item-layout | Boolean       | false             | No       | Whether to skip the layout of a hidden swiper. If it is set to `true`, the swiper performance in complicated situations will be optimized, but the layout information of the hidden swiper will be lost. |
| bindchange              | Event Handler |                   | No       | The change event triggered when current changes: `event.detail = {current: current, source: source}`.                                                                                                    |
| bindtransition          | Event Handler |                   | No       | swiper-item Is triggered when the location of transition Event chnages. `event.detail = {dx: dx, Two: two}`.                                                                                             |
| bindanimationfinish     | Event Handler |                   | No       | The `animationfinish `event triggered when the animation ends, with the same `event.detail` as above.                                                                                                    |

The `detail` returned by the `change` event contains a `source` field, which causes the change. Possible values:

- `autoplay`: Swiper change due to autoplay
- `touch` : Swiper change due to user touch
- Empty string: Other causes

**Note**: Only the `<swiper-item/>` component can be set; otherwise, an undefined behavior will occur.

## swiper-item

It can be placed in the [swiper](swiper) component only. The width and height are automatically set to 100%.

| Attribute | Type   | Default | Description             |
| :-------- | :----- | :------ | :---------------------- |
| item-id   | String | ""      | ID of the `swiper-item` |

### Sample code

```javascript
// JavaScript
Page({
  data: {
    imgUrls: [
      'https://img02.tooopen.com/images/20150928/tooopen_sy_143912755726.jpg',
      'https://img06.tooopen.com/images/20160818/tooopen_sy_175866434296.jpg',
      'https://img06.tooopen.com/images/20160818/tooopen_sy_175833047715.jpg'
    ],
    indicatorDots: false,
    autoplay: false,
    interval: 5000,
    duration: 1000
  },
  changeIndicatorDots(e) {
    this.setData({
      indicatorDots: !this.data.indicatorDots
		}) 
  },
  changeAutoplay(e) {
    this.setData({
      autoplay: !this.data.autoplay
    })
  },
  intervalChange(e) {
    this.setData({
      interval: e.detail.value
		}) 
  },
  durationChange(e) {
    this.setData({
      duration: e.detail.value
    })
	} 
});
```
```xml
<!--WXML-->
{% raw %}
<swiper
  indicator-dots="{{indicatorDots}}"
  autoplay="{{autoplay}}"
  interval="{{interval}}"
  duration="{{duration}}"
>
  <block wx.for="{{imgUrls}}">
    <swiper-item>
      <image src="{{item}}" class="slide-image" width="355" height="150" />
    </swiper-item>
  </block>
</swiper>
<button bindtap="changeIndicatorDots">indicator-dots</button>
<button bindtap="changeAutoplay">autoplay</button>
<slider bindchange="intervalChange" show-value min="500" max="2000" />
interval
<slider bindchange="durationChange" show-value min="1000" max="10000" />
duration
{% endraw %}
```

> 📘 Bugs and tips
> 
> - Tip: If `setData` is used in the `bindchange` event callback function to change the `current` value, `setData` may be called continuously. In general, we recommend you check the `source` field to determine whether the change is caused by user touch before changing the `current` value.
