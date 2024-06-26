---
title: "Add Google places API"
slug: "add-google-places-api"
excerpt: "This section describes the procedure to add Google Places API."
hidden: true
metadata: 
  image: []
  robots: "index"
createdAt: "Fri Feb 10 2023 11:45:49 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Wed Feb 15 2023 11:24:41 GMT+0000 (Coordinated Universal Time)"
layout: "default"
parent: "Meet the MiniApp"
---
# Add Google places API 
This section describes the procedure to add Google Places API.

***

To add Google Places API:

- Copy the code below.

```Text
// map.js
wx.showLoading({title: "Fetching nearby restaurants"})
wx.request({
  url: `https://maps.googleapis.com/maps/api/place/nearbysearch/json?location=${this.data.userLocation.latitude},${this.data.userLocation.longitude}&radius=15000&type=restaurant&key=YOUR_API_KEY`,
  success: (res) => {
    wx.hideLoading({})
  }
})
```

- After pasting the above code to the existing code, your `map.js` file should look like the one below.

```Text
// map.js
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

- Instead of `YOUR_API_KEY` (see URL link in line 22 above) insert your API key.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/fb6ed8c-Google_places_API_1.PNG",
        null,
        ""
      ],
      "align": "center"
    }
  ]
}
[/block]


- Refer the GIF below which illustrates replacing `YOUR_API_KEY` with API key.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/f22897a-chrome-capture-2023-1-14.gif",
        null,
        "Replacing `YOUR_API_KEY` with API key"
      ],
      "align": "center",
      "caption": "Replacing `YOUR_API_KEY` with API key"
    }
  ]
}
[/block]
