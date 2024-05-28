---
title: "Slider"
slug: "slider"
excerpt: "Slider allows users to specify a numeric value within a range of minimum and maximum."
hidden: false
metadata: 
  image: []
  robots: "index"
createdAt: "Mon Apr 10 2023 12:36:50 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Fri Jul 14 2023 11:07:36 GMT+0000 (Coordinated Universal Time)"
layout: "default"
parent: "Form components"
grand_parent: "Components"
---
The slider component lets users perform selection by moving the slider within a range.

| Attribute       | Type          | Default Value | Required | Description                                                                        |
| :-------------- | :------------ | :------------ | :------- | :--------------------------------------------------------------------------------- |
| min             | Number        | 0             | No       | Minimum value.                                                                     |
| max             | Number        | 100           | No       | Maximum value.                                                                     |
| step            | Number        | 1             | No       | Step size, which must be greater than 0 and be an aliquot part of (`max` - `min`). |
| disabled        | boolean       | false         | No       | Whether it is disabled.                                                            |
| value           | Number        | 0             | No       | Current value.                                                                     |
| color           | Color         | # e9e9e9      | No       | Inactive track color (use "backgroundColor").                                      |
| selected-color  | Color         | # 1aad19      | No       | Active track color (use "activeColor").                                            |
| activeColor     | Color         | # 1aad19      | No       | Active track color.                                                                |
| backgroundColor | Color         | # e9e9e9      | No       | Inactive track color.                                                              |
| block-size      | Number        | 28            | No       | Slider size. Value range: 12–28.                                                   |
| block-color     | Color         | # ffffff      | No       | Slider color.                                                                      |
| show-value      | Boolean       | false         | No       | Whether to show the current value.                                                 |
| bindchange      | Event Handler |               | No       | The event triggered after a drag operation: `event.detail = {value: value}`.       |
| bindchanging    | Event Handler |               | No       | The event triggered during a drag operation: `event.detail = {value: value}`.      |
| aria-label      | String        |               | No       | Accessibility, which is the additional description of the element.                 |

### Sample code

```javascript
const pageData = {}
for (let i = 1; i < 5; i++) {
  (function (index) {
    pageData['slider' + index + 'change'] = function (e) {
    	console.log('slider' + 'index' + '`A change event occurred, and the carried value is ', e.detail.value)
    }
  }(i))
}
Page(pageData)
```
```xml WXML
<view class="section section_gap">
  <text class="section__title">Set the step</text>
  <view class="body-view">
  	<slider bindchange="slider2change" step="5" />
  </view>
</view>
<view class="section section_gap">
  <text class="section__title">Display the current value</text>
  <view class="body-view">
  	<slider bindchange="slider3change" show-value />
  </view>
</view>
<view class="section section_gap">
  <text class="section__title">Set the minimum/maximum value</text>
  <view class="body-view">
  	<slider bindchange="slider4change" min="50" max="200" show-value />
  </view>
</view>

```

![](https://files.readme.io/9eb48f4-Screenshot_2023-06-15_at_5.18.20_PM.png)
