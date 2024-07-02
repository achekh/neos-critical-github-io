---
title: "redirectTo(Object object)"
slug: "redirect-to-api"
excerpt: "Closes the current page and jumps to another page within the Mini App. However, jumping to the tabbar page is not allowed."
hidden: false
metadata: 
  image: []
  robots: "index"
createdAt: "Mon Apr 17 2023 11:02:32 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Fri Jul 14 2023 11:13:44 GMT+0000 (Coordinated Universal Time)"
layout: "default"
parent: "Route"
grand_parent: "APIs"
nav_order: 3
---
# redirectTo(Object object) 
Closes the current page and jumps to another page within the Mini App. However, jumping to the tabbar page is not allowed.

***

# Parameters

**Object object**

| Attribute | Type | Required | Description |
| :-------- | :--- | :------- | :---------- |
| url | String | Yes | Path of the non-tab bar page in the app to redirect to (code package path), which can be followed by parameters.  \nUse `?` to separate the path and parameters, use `=` to concatenate a parameter key and value, and use `&` to separate parameters, such as `path?key=value&key2=value2`. |
| success | Function | No | Callback function for a successful API call. |
| fail | Function | No | Callback function for a failed API call. |
| complete | Function | No | Callback function for API call end (executed for both successful and failed calls). |

### Sample code

```javascript
// page2.js
wx.redirectTo({
	url: 'page1?id=1'
})
```
