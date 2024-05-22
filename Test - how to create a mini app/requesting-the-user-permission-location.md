---
title: "Requesting the user permission (location)"
slug: "requesting-the-user-permission-location"
excerpt: ""
hidden: true
metadata: 
  image: []
  robots: "index"
createdAt: "Wed Jan 11 2023 15:10:14 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Wed Jan 25 2023 16:38:12 GMT+0000 (Coordinated Universal Time)"
---
Let's register the user location permission message:

1. Copy the code below:

```Text app.json
  "permission": {
    "scope.userLocation": {
      "desc": "In order to use this mini app properly, we need your location permission"
    }
  },
```

2. Insert and format it as the one below:

```Text app.json
{
  "pages":[
    "pages/map/map",
    "pages/list/list",
    "pages/about/about"
  ],
  "permission": {
    "scope.userLocation": {
      "desc": "In order to use this mini app properly, we need your location permission"
    }
  },
  "window":{
    "backgroundTextStyle":"light",
    "navigationBarBackgroundColor": "#fff",
    "navigationBarTitleText": "Near me",
    "navigationBarTextStyle":"black"
  },
  "tabBar": {
    "color": "#000000",
    "selectedColor": "#5C7CFA",
    "backgroundColor": "#ffffff",
    "list": [{
      "pagePath": "pages/map/map",
      "iconPath": "assets/images/map.png",
      "selectedIconPath": "assets/images/map-selected.png",
      "text": "Map"
    }, {
      "pagePath": "pages/about/about",
      "iconPath": "assets/images/info.png",
      "selectedIconPath": "assets/images/info-selected.png",
      "text": "About"
    }]
  }
}
```
