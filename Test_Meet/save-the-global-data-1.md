---
title: "Save the global data"
slug: "save-the-global-data-1"
excerpt: ""
hidden: true
metadata: 
  image: []
  robots: "index"
createdAt: "Fri Feb 10 2023 11:43:40 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Wed Feb 15 2023 11:08:18 GMT+0000 (Coordinated Universal Time)"
layout: "default"
parent: "Meet the MiniApp"
---
# Save the global data 
*** 
Prepare the app's global data for the data it will receive from pages. To do so, 

- Copy the code below.

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
