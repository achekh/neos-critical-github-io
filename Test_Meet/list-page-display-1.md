---
title: "\"List\" page display"
slug: "list-page-display-1"
excerpt: "This section explains the procedure to display List page in Mini App."
hidden: true
metadata: 
  image: []
  robots: "index"
createdAt: "Fri Feb 10 2023 11:46:15 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Tue Mar 14 2023 14:24:41 GMT+0000 (Coordinated Universal Time)"
layout: "default"
parent: "Meet the MiniApp"
---
# \"List\" page display 
*** 
To display the List page:

1. Copy the code from each of 3 tabs below and paste it into the corresponding file in Mini App Studio

> 🚧 Need Ben's help on design for wxss

```Text
// list.wxml
<view class="container">
  <view wx:for="{{markers}}" wk:key="{{item.label.content}}">
    <text>{{index+1}}: {{item.label.content}}</text>
  </view>
</view>
```
```Text
// list.wxss
ben help!
```
```Text
// list.js
const app = getApp()

Page({
  data: {
    markers: null
  },
  onLoad: function () {
    this.setData({markers: app.globalData.markers})
  },
})
```

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/6321b69-List_page1.PNG",
        null,
        "list.wxml"
      ],
      "align": "center",
      "caption": "list.wxml"
    }
  ]
}
[/block]


***

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/6526f06-List_page2.PNG",
        null,
        "list.js"
      ],
      "align": "center",
      "caption": "list.js"
    }
  ]
}
[/block]


2. Copy the code from each of 3 tabs below.

```Text
// maps.wxml
<view bindtap="listClicked" class="list-button">
  <cover-image src="../../assets/images/list.png" />
  <text>List</text>
</view>
```
```Text
// maps.wxss
.list-button {
  position: absolute;
  bottom: 50rpx;
  left: 50rpx;
  background-color: grey;
  padding: 10rpx;
}
.list-image {
  height: 30rpx;
  width: 30rpx;
}
```
```Text
// maps.js
listClicked: function () {
    wx.navigateTo({url: "../../list/list"})
  }
```

3. Insert and format them to see the one below.

```Text
// maps.wxml
<view class="container">
  <map id="map" show-location latitude="{{userLocation.latitude}}" longitude="{{userLocation.longitude}}" markers="{{markers}}" />
  <view bindtap="listClicked" class="list-button">
    <cover-image src="../../assets/images/list.png" />
    <text>List</text>
  </view>
</view>
```
```Text
// maps.wxss
#map {
  height: 100vh;
  width: 100vw;
}
.list-button {
  position: absolute;
  bottom: 50rpx;
  left: 50rpx;
  background-color: grey;
  padding: 10rpx;
}
.list-image {
  height: 30rpx;
  width: 30rpx;
}
```
```Text
// maps.js
const util = require('../../utils/util.js')

const app = getApp()

Page({
  data: {
    userLocation: {
      latitude: 24.92284475581099,
      longitude: 46.63479878033597
    },
  },
  onLoad: function () {
    wx.getLocation({
      type: 'wgs84',
      success: (res) => {
        const latitude = res.latitude
        const longitude = res.longitude
        // this.setData({
        //   userLocation: {
        //     latitude: latitude,
        //     longitude: longitude
        //   }
        // })
        wx.showLoading({title: "Fetching nearby restaurants"})
        wx.request({
      url: `https://maps.googleapis.com/maps/api/place/nearbysearch/json?location=${this.data.userLocation.latitude},${this.data.userLocation.longitude}&radius=15000&type=restaurant&key=<google-api-key>`,
      success: (res) => {
        wx.hideLoading({})
        const markers = util.processPlacesResponse(res)
        if (markers.length === 0) {
          wx.showToast({title: "Sorry, there is no restaurants around you", duration: 5000})
        }
        this.setData({markers: markers})
        app.globalData.markers = markers
      }
    })
      }
    })
  },
  listClicked: function () {
    wx.navigateTo({url: "../../list/list"})
  }
})
```

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/ab013f5-List_page3.PNG",
        null,
        "map.wxml"
      ],
      "align": "center",
      "caption": "maps.wxml"
    }
  ]
}
[/block]


***

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/f5bd1bd-List_page4.PNG",
        null,
        "map.wxss"
      ],
      "align": "center",
      "caption": "maps.wxss"
    }
  ]
}
[/block]


***

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/a9740f4-List_page5.PNG",
        null,
        "maps.js"
      ],
      "align": "center",
      "caption": "maps.js"
    }
  ]
}
[/block]


4. Your page in the preview window should now have a  **List** option as shown in the screenshot below.

![](https://files.readme.io/7e3b6c6-image.png)

....

> 👍 Congratulations! You have created your first mini app for Super Hub
