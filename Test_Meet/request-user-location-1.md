---
title: "Request user location"
slug: "request-user-location-1"
excerpt: "This section explains the procedure to request the user location in Mini App."
hidden: true
metadata: 
  image: []
  robots: "index"
createdAt: "Fri Feb 10 2023 11:45:24 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Wed Feb 15 2023 11:11:54 GMT+0000 (Coordinated Universal Time)"
layout: "default"
parent: "Meet the MiniApp"
---
# Request user location 
*** 
To request the user's location:

- Copy the code snippet below.

```Text map.js
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

- After pasting the above code to the existing code your `map.js` file should look like the one below.

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
      }
    })
  },
})
```

- You will see a prompt seeking permission to access your location as shown below.

![](https://files.readme.io/34f577b-image.png)

- Tap **Allow** and try to zoom out the map from your location:

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
