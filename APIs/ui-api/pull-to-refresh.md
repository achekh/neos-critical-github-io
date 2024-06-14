---
title: "Pull-to-Refresh"
slug: "pull-to-refresh"
excerpt: "Start and stop pull down refresh."
hidden: false
metadata: 
  image: []
  robots: "index"
createdAt: "Tue May 02 2023 10:47:57 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Wed May 17 2023 07:03:09 GMT+0000 (Coordinated Universal Time)"
layout: "default"
parent: "UI"
grand_parent: "APIs"
---
# Pull-to-Refresh 
*** 
# startPullDownRefresh

Starts pull-to-refresh. After the call, the pull-to-refresh animation is triggered, and the effect is the same as a manual pull-to-refresh.

# Parameters

**Object object**

| Attribute | Type     | Description                                                                            |
| :-------- | :------- | :------------------------------------------------------------------------------------- |
| success   | Function | Callback function for a successful API call.                                           |
| fail      | Function | Callback function for a failed API call.                                               |
| complete  | Function | Callback function for an API call end (executed for both successful and failed calls). |

### Sample code

```javascript JavaScript
wx.startPullDownRefresh()
```

# stopPullDownRefresh(Object object)

Stops pull-to-refresh on the current page.

# Parameters

**Object object**

| Attribute | Type     | Description                                                                            |
| :-------- | :------- | :------------------------------------------------------------------------------------- |
| success   | Function | Callback function for a successful API call.                                           |
| fail      | Function | Callback function for a failed API call.                                               |
| complete  | Function | Callback function for an API call end (executed for both successful and failed calls). |

### Sample code

```javascript JavaScript
Page({
  onPullDownRefresh () {
  	wx.stopPullDownRefresh()
  }
})
```
