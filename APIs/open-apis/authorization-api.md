---
title: "Authorization"
slug: "authorization-api"
excerpt: "This section list all APIs related with Authorization functionality of the Mini App."
hidden: false
metadata: 
  image: []
  robots: "index"
createdAt: "Fri Apr 21 2023 10:36:36 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Fri Jul 14 2023 11:18:43 GMT+0000 (Coordinated Universal Time)"
layout: "default"
parent: "Open APIs"
grand_parent: "APIs"
---
# Authorization 
*** 
## wx.authorize(Object object)

Sends an authorization request to the user in advance. Immediately after the call, a window will pop up to ask the user whether to allow the mini app to use a certain feature or to access certain user data. However, the corresponding APIs is not called actually. If the user has already granted the permission, no pop-up window displays, and a success returns directly.

# Parameters

**Object object**

| Attribute | Type     | Required | Description                                                                        |
| :-------- | :------- | :------- | :--------------------------------------------------------------------------------- |
| scope     | String   | Yes      | Scope of the permissions to be obtained                                            |
| success   | Function | No       | Callback function for successful API call                                          |
| fail      | Function | No       | Callback function for failed API call                                              |
| complete  | Function | No       | Callback function for API call end (executed for both successful and failed calls) |

### Sample code

```javascript
// JavaScript
// You can first check whether the user has authorized the "scope.record" scope through `wx.getSetting`.
  wx.getSetting({
    success(res) {
      if (!res.authSetting['scope.location']) {
      wx.authorize({
        scope: 'scope.location',
        success() {
          // The user has already allowed the mini app to use the recording feature. Subsequent calls to the `wx.startRecord` API will not pop up a window to ask for permission.
          wx.startRecord()
        }
      })
    }
  }
})
```
