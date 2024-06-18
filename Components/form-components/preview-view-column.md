---
title: "Preview-view-column"
slug: "preview-view-column"
excerpt: "Preview-view-column can be placed only in the picker-view component."
hidden: false
metadata: 
  image: []
  robots: "index"
createdAt: "Mon Apr 10 2023 11:26:39 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Fri Jul 14 2023 11:34:53 GMT+0000 (Coordinated Universal Time)"
layout: "default"
parent: "Form components"
grand_parent: "Components"
---
# Preview-view-column 
*** 
It can be placed only in [picker-view](doc:picker-view). The height of its child nodes will be automatically set to the same value as that of the selection box of [picker-view](doc:picker-view).

### Sample code

```javascript
// JavaScript
const date = new Date()
const years = []
const months = []
const days = []
for (let i = 1990; i <= date.getFullYear(); i++) {
	years.push(i)
}
for (let i = 1; i <= 12; i++) {
	months.push(i)
}
for (let i = 1; i <= 31; i++) {
	days.push(i)
}
Page({
  data: {
    years,
    year: date.getFullYear(),
    months,
    month: 2,
    days,
    day: 2,
    value: [9999, 1, 1],
  },
  bindChange(e) {
    const val = e.detail.value
    this.setData({
      year: this.data.years[val[0]],
      month: this.data.months[val[1]],
      day: this.data.days[val[2]]
    })
  }
})

```
```xml
<!--WXML-->
{% raw %}
<view>
  <view>{{year}}Year{{month}}Month{{day}}Day</view>
  <picker-view
    indicator-style="height: 50px;"
    style="width: 100%; height: 300px;"
    value="{{value}}"
    bindchange="bindChange">
    <picker-view-column>
    	<view wx.for="{{years}}" style="line-height: 50px">{{item}}Year</view>
    </picker-view-column>
    <picker-view-column>
    	<view wx.for="{{months}}" style="line-height: 50px">{{item}}Month</view>
    </picker-view-column>
    <picker-view-column>
    	<view wx.for="{{days}}" style="line-height: 50px">{{item}}Day</view>
    </picker-view-column>
  </picker-view>
</view>
{% endraw %}
```

> 📘 Notes
> 
> - Scrolling the picker will generate the vibration feedback on iOS, which can be disabled from "Settings" > "Sounds & Haptics" > "System Haptics".
