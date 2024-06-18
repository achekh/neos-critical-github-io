---
title: "navigateTo"
slug: "navigate-to-api"
excerpt: "Keeps the current page and redirects to a page in the Mini App (which cannot be a tab bar page)."
hidden: false
metadata: 
  image: []
  robots: "index"
createdAt: "Mon Apr 17 2023 11:05:07 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Fri Jul 14 2023 11:13:58 GMT+0000 (Coordinated Universal Time)"
layout: "default"
parent: "Route"
grand_parent: "APIs"
---
# navigateTo 
*** 
# wx.navigateTo (Object object)

Keeps the current page and redirects to a page in the Mini App (which cannot be a tabbar page). `wx.navigateBack` can be called to return to the original page. The page stack in the Mini App can have up to 10 pages.

# Parameters

**Object object**

| Attribute | Type     | Default | Required | Description                                                                                                                                                                                                                                                                                            |
| :-------- | :------- | :------ | :------- | :----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| url       | String   |         | Yes      | The path (code package path) to the non-tabBar page in the app that needs to be jumped, which can be followed by parameters. Use `?` to separate the path and parameters, use `=` to concatenate a parameter key and value, and use `&` to separate parameters, such as `path?key=value&key2=value 2`. |
| success   | Function |         | No       | Callback function for a successful API call.                                                                                                                                                                                                                                                           |
| fail      | Function |         | No       | Callback function for a failed API call.                                                                                                                                                                                                                                                               |
| complete  | Function |         | No       | Callback function for an API call end (executed for both successful and failed calls).                                                                                                                                                                                                                 |

### Sample code

```javascript
// page2.js
wx.navigateTo({
	url: 'page1?id=1',
})   
```
```javascript
// page1.js
Page({
	onLoad: (option){
			console.log(option.query)
	}
}) 
```
