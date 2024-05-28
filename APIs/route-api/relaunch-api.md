---
title: "reLaunch (Object object)"
slug: "relaunch-api"
excerpt: "Closes all pages and opens a specific page in the Mini App."
hidden: false
metadata: 
  image: []
  robots: "index"
createdAt: "Mon Apr 17 2023 11:00:41 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Fri Jul 14 2023 11:13:32 GMT+0000 (Coordinated Universal Time)"
layout: "default"
parent: "Route"
grand_parent: "APIs"
---
# Parameters

**Object object**

| Attribute | Type     | Required | Description                                                                                                                                                                                                                                                                   |
| :-------- | :------- | :------- | :---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| url       | String   | Yes      | Path of the page in the app to redirect to (code package path), which can be followed by parameters. Use `?` to separate the path and parameters, use `=` to concatenate a parameter key and value, and use `&` to separate parameters, such as `path?key=value&key2=value2`. |
| success   | Function | No       | Callback function for a successful API call.                                                                                                                                                                                                                                  |
| fail      | Function | No       | Callback function for a failed API call.                                                                                                                                                                                                                                      |
| complete  | Function | No       | Callback function for an API call end (executed for both successful and failed calls).                                                                                                                                                                                        |

### Sample code

```javascript page2.js
wx.reLaunch({
	url: 'page1?id=1'
})
```
```javascript page1.js
Page({
	onLoad (option) {
		console.log(option.query)
	}
})
```
