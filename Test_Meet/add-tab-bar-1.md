---
title: "Add Tab Bar"
slug: "add-tab-bar-1"
excerpt: "This section explains the procedure to add a Tab bar to Mini App."
hidden: true
metadata: 
  image: []
  robots: "index"
createdAt: "Tue Feb 07 2023 10:24:00 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Wed Feb 15 2023 11:04:45 GMT+0000 (Coordinated Universal Time)"
layout: "default"
parent: "Meet the MiniApp"
---
# Add Tab Bar 
This section explains the procedure to add a Tab bar to Mini App.

***

To add Tab Bar icons, please

- Copy the code snippet below 

```Text
// app.json

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

- After pasting the above code to the existing code your `app.json` file should look like the one below.

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

- You will now be able to see the icons in the preview window as shown below and be able to tap on the tab bar icons. 

![](https://files.readme.io/b2eaded-image.png)
