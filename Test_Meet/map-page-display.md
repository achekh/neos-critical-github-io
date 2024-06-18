---
title: "\"Map\" page display"
slug: "map-page-display"
excerpt: "This section explains the procedure to display Map page in Mini App."
hidden: true
metadata: 
  image: []
  robots: "index"
createdAt: "Fri Feb 10 2023 11:43:14 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Wed Feb 15 2023 11:05:54 GMT+0000 (Coordinated Universal Time)"
layout: "default"
parent: "Meet the MiniApp"
---
# \"Map\" page display 
*** 
To display the Map page:

- Copy the code from each of 3 tabs below and paste it into the corresponding file in Mini App Studio.

> 📝 Note
> 
> For demo purposes the user location is predefined.

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

- You will see the grey background and image as shown below:

![](https://files.readme.io/526371a-image.png)

> ❗️ Neuxnet to remove Chinese language

![](https://files.readme.io/7508f7e-image.png)

> 👍 Does it work? Let's go to the next section!
