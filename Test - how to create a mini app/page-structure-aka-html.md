---
title: "\"Map\" page display"
slug: "page-structure-aka-html"
excerpt: ""
hidden: true
metadata: 
  image: []
  robots: "index"
createdAt: "Wed Jan 11 2023 14:06:24 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Wed Jan 25 2023 16:36:27 GMT+0000 (Coordinated Universal Time)"
layout: "default"
parent: "Test - how to create a mini app"
---
# \"Map\" page display 
*** 
Let's display the Map page:

1. Copy the code from each of 3 tabs below and paste it into the corresponding file in Mini App Studio. Please note, that for demo purposes the user location is predefined

```Text
// map.wxml
<view class="container">
  <map id="map" show-location latitude="{{userLocation.latitude}}" longitude="{{userLocation.longitude}}" markers="{{markers}}" />
</view>
```
```Text
// map.wxss
#map {
  height: 100vh;
  width: 100vw;
}
```
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
  },
})
```

2. You will see the grey background and image below:

![](https://files.readme.io/526371a-image.png)

> ❗️ Neuxnet to remove Chinese language

![](https://files.readme.io/7508f7e-image.png)

> 👍 Does it work? Let's go to the next section!
