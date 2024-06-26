---
title: "Login"
slug: "login-api"
excerpt: "This section lists all the APIS related with Login functionality of Mini App."
hidden: false
metadata: 
  image: []
  robots: "index"
createdAt: "Fri Apr 21 2023 10:06:28 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Fri Jul 14 2023 11:18:30 GMT+0000 (Coordinated Universal Time)"
layout: "default"
parent: "Open APIs"
grand_parent: "APIs"
---
# Login 
This section lists all the APIS related with Login functionality of Mini App.

***

## wx.login(Object object)

This API is currently not supported in Super Hub Mini App Studio, and it must be debugged within the host app. The content returned on calling this API must be provided by the host app.

# Parameter

**Object object**

| Attribute | Type     | Description                                                                         |
| :-------- | :------- | :---------------------------------------------------------------------------------- |
| success   | Function | Callback function for successful API call.                                          |
| fail      | Function | Callback function for failed API call.                                              |
| complete  | Function | Callback function for API call end (executed for both successful and failed calls). |

### Sample code

```javascript
// JavaScript
wx.login({
  success(res) {
 	 console.log(res ,"info, host app return");
  }
})
```
