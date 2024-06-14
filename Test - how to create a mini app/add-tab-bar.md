---
title: "Add Tab bar"
slug: "add-tab-bar"
excerpt: ""
hidden: true
metadata: 
  image: []
  robots: "index"
createdAt: "Wed Jan 25 2023 15:23:02 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Thu Jan 26 2023 11:57:41 GMT+0000 (Coordinated Universal Time)"
layout: "default"
parent: "Test - how to create a mini app"
---
# Add Tab bar 
*** 
To add Tabbar icons, please

1. Copy the code snippet below 

```Text app.json

"tabBar": {
    "color": "#000000",
    "selectedColor": "#5C7CFA",
    "backgroundColor": "#FFFFFF",
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
```

2. Insert and format the code to see the below:

```
{
  "pages":[
    "pages/map/map",
    "pages/list/list",
    "pages/about/about"
  ],
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

3. You will see the following and be able to tap on the tab bar icons 

![](https://files.readme.io/b2eaded-image.png)
