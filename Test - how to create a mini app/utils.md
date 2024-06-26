---
title: "Utils and Markers"
slug: "utils"
excerpt: ""
hidden: true
metadata: 
  image: []
  robots: "index"
createdAt: "Wed Jan 11 2023 15:56:30 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Tue Feb 14 2023 08:39:50 GMT+0000 (Coordinated Universal Time)"
layout: "default"
parent: "Test - how to create a mini app"
---
# Utils and Markers 
*** 
Let's process the data from Google API to convert them to markers later

1. Copy and insert the code below to utils.js:

```Text
// util.js
const processPlacesResponse = response => {
  const markers = [];
  for (result of response.data.results) {
    markers.push({
      iconPath: "../../assets/images/marker.png",
      latitude: result.geometry.location.lat,
      longitude: result.geometry.location.lng,
      label: {
        content: result.name,
      },
    })
  }
  return markers
}

module.exports = {
  processPlacesResponse: processPlacesResponse
}
```

2. Copy the code below to maps.js:

```Text
// map.js
const util = require('../../utils/util.js')
const app = getApp()
```

3. Copy the code below to maps.js:

```Text
// map.js
const markers = util.processPlacesResponse(res)
if (markers.length === 0) {
    wx.showToast({title: "Sorry, there is no restaurants around you", duration: 5000})
}
this.setData({markers: markers})
app.globalData.markers = markers
```

4. Insert and format them to see the one below:

```Text
// map.js
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
  
})
```

5. You will see:

![](https://files.readme.io/63b56f6-image.png)
