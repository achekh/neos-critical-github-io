---
title: "Register pages"
slug: "register-pages"
excerpt: ""
hidden: true
metadata: 
  image: []
  robots: "index"
createdAt: "Tue Jan 24 2023 11:39:45 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Wed Jan 25 2023 16:28:35 GMT+0000 (Coordinated Universal Time)"
layout: "default"
parent: "Test - how to create a mini app"
---
# Register pages 
*** 
Let's register pages in app.json:

1. Copy the code snippet below and Paste it into Mini App Studio and press ctrl/cmd S to save, please make sure to add the snippet inside the global JSON object inside the file

```Text
// app.json
 "pages":[
    "pages/map/map",
    "pages/list/list",
    "pages/about/about"
],
```

2. Register pages in their own <page name>.json files:

```Text
// about.json
{
  "usingComponents": {}
}
```
```Text
// list.json
{
  "usingComponents": {}
}
```
```Text
// map.json
{
  "usingComponents": {}
}
```

3. Add Global styling to app.wxss:

```Text
// app.wxss
.container {
  height: 100%;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: space-between;
  padding: 20rpx 0;
  box-sizing: border-box;
}
```
