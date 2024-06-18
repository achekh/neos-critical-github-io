---
title: "Mini App permissions settings"
slug: "mini-app-permissions-settings"
excerpt: ""
hidden: false
metadata: 
  image: []
  robots: "index"
createdAt: "Thu May 18 2023 11:13:37 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Fri Jul 14 2023 11:26:13 GMT+0000 (Coordinated Universal Time)"
layout: "default"
parent: "Advanced topics"
grand_parent: "Guide"
nav_order: 3
---
# Mini App permissions settings 
*** 
To direct the user to the Mini App permissions settings screen from the Mini App, use the following code:

```javascript
// javascript
var opts = {
   api_name: 'openSetting', // api name
   success: function(res) {},
   fail: function(res) {},
   complete: function(res) {},
   data: {}
 }
 wx.invokeNativePlugin(opts);
```
