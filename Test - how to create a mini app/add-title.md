---
title: "Add title"
slug: "add-title"
excerpt: ""
hidden: true
metadata: 
  image: []
  robots: "index"
createdAt: "Wed Jan 25 2023 15:11:31 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Wed Mar 08 2023 12:04:07 GMT+0000 (Coordinated Universal Time)"
layout: "default"
parent: "Test - how to create a mini app"
---
# Add title 
*** 
To add "Near me" title for all pages, please 

1. copy the code snippet below to the global JSON object inside app.json

```Text app.json
"window":{
    "backgroundTextStyle":"light",
    "navigationBarBackgroundColor": "#fff",
    "navigationBarTitleText": "Near me",
    "navigationBarTextStyle":"black"
},
```

2. insert and format the code like the one below

```Text app.json
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
  }
}
```

3. You will see:

![](https://files.readme.io/6ac9fe6-image.png)

> 👍 Can you see the same? Well done!
