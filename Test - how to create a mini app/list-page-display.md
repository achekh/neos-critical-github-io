---
title: "\"List\" page display"
slug: "list-page-display"
excerpt: ""
hidden: true
metadata: 
  image: []
  robots: "index"
createdAt: "Wed Jan 11 2023 14:50:37 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Thu Jan 26 2023 12:02:49 GMT+0000 (Coordinated Universal Time)"
layout: "default"
parent: "Test - how to create a mini app"
---
Let's display the List page:

1. Copy the code from each of 3 tabs below and paste it into the corresponding file in Mini App Studio

> 🚧 Need Ben's help on design for wxss

```Text list.wxml
<view class="container">
  <view wx:for="{{markers}}" wk:key="{{item.label.content}}">
    <text>{{index+1}}: {{item.label.content}}</text>
  </view>
</view>
```
```Text list.wxss
ben help!
```
```Text list.js
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

2. Copy the code from each of 3 tabs below:

```Text maps.wxml
<view bindtap="listClicked" class="list-button">
  <cover-image src="../../assets/images/list.png" />
  <text>List</text>
</view>
```
```Text maps.wxss
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
```Text maps.js
listClicked: function () {
    wx.navigateTo({url: "../../list/list"})
  }
```

3. Insert and format them to see the one below

```Text maps.wxml
<view class="container">
  <map id="map" show-location latitude="{{userLocation.latitude}}" longitude="{{userLocation.longitude}}" markers="{{markers}}" />
  <view bindtap="listClicked" class="list-button">
    <cover-image src="../../assets/images/list.png" />
    <text>List</text>
  </view>
</view>
```
```Text maps.wxss
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
```Text maps.js
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
      url: `https://maps.googleapis.com/maps/api/place/nearbysearch/json?location=${this.data.userLocation.latitude},${this.data.userLocation.longitude}&radius=15000&type=restaurant&key=AIzaSyAfoSnjsqf7AwaR4FD2DfbnE1bqIlvrTNI`,
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

4. You will see:

![](https://files.readme.io/7e3b6c6-image.png)

....

> 👍 Congratulations! You have created your first mini app for Super Hub
