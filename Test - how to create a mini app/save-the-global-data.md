---
title: "Save the global data"
slug: "save-the-global-data"
excerpt: ""
hidden: true
metadata: 
  image: []
  robots: "index"
createdAt: "Tue Jan 24 2023 08:08:46 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Wed Jan 25 2023 10:02:51 GMT+0000 (Coordinated Universal Time)"
layout: "default"
parent: "Test - how to create a mini app"
---
# Save the global data 
*** 
Prepare the app's global data for the data it will receive from pages

```Text app.js
App({
  onLaunch: function () {
  },
  globalData: {
    userLocation: null,
    markers: null
  }
})
```
