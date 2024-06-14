---
title: "Add Google places API"
slug: "google-places-api"
excerpt: ""
hidden: true
metadata: 
  image: []
  robots: "index"
createdAt: "Mon Jan 23 2023 11:26:44 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Thu Jan 26 2023 12:00:55 GMT+0000 (Coordinated Universal Time)"
layout: "default"
parent: "Test - how to create a mini app"
---
# Add Google places API 
*** 
Let's add Google places API:

1. Copy the code below

```Text map.js
wx.showLoading({title: "Fetching nearby restaurants"})
wx.request({
  url: `https://maps.googleapis.com/maps/api/place/nearbysearch/json?location=${this.data.userLocation.latitude},${this.data.userLocation.longitude}&radius=15000&type=restaurant&key=YOUR_API_KEY`,
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
```

2. Insert and format it like the one below:

```Text map.js
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
        this.setData({
          userLocation: {
            latitude: latitude,
            longitude: longitude
          }
        })
        wx.showLoading({title: "Fetching nearby restaurants"})
        wx.request({
          url: `https://maps.googleapis.com/maps/api/place/nearbysearch/json?location=${this.data.userLocation.latitude},${this.data.userLocation.longitude}&radius=15000&type=restaurant&key=YOUR_API_KEY`,
          success: (res) => {
            wx.hideLoading({})     
        	}
    		})
      }
    })
  },
})
```

3. Instead of YOUR_API_KEY (see URL link in line 22 above) insert your API key
