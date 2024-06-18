---
title: "Request user location"
slug: "request-user-location"
excerpt: ""
hidden: true
metadata: 
  image: []
  robots: "index"
createdAt: "Tue Jan 24 2023 07:49:02 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Wed Mar 08 2023 12:03:40 GMT+0000 (Coordinated Universal Time)"
layout: "default"
parent: "Test - how to create a mini app"
---
# Request user location 
*** 
Let's request the user's location:

1. copy the code snippet below

```Text
// map.js
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
  }
})
```

2. insert and format the code like the one below

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
      }
    })
  },
})
```

3. You will see:

![](https://files.readme.io/34f577b-image.png)

4. Press <Allow> and try to zoom out the map from your location:

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/80b4d49-image.png",
        null,
        ""
      ],
      "align": "center",
      "sizing": "400px"
    }
  ]
}
[/block]


> ❗️ remove Chinese language
