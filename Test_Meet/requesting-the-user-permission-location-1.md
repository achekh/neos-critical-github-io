---
title: "Requesting the user permission (location)"
slug: "requesting-the-user-permission-location-1"
excerpt: "This section explains the procedure to request the user permission in Mini App."
hidden: true
metadata: 
  image: []
  robots: "index"
createdAt: "Fri Feb 10 2023 11:45:07 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Wed Feb 15 2023 11:09:32 GMT+0000 (Coordinated Universal Time)"
layout: "default"
parent: "Meet the MiniApp"
---
# Requesting the user permission (location) 
This section explains the procedure to request the user permission in Mini App.
*** 
To register the user location permission message:

- Copy the code below:

```Text
// app.json
  "permission": {
    "scope.userLocation": {
      "desc": "In order to use this mini app properly, we need your location permission"
    }
  },
```

- After pasting the above code to the existing code, your `app.json` file should look like the one below.

```Text
// app.json
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

![](https://files.readme.io/b041113-Req_User_permission.PNG)
