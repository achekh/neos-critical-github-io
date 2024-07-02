---
title: "System"
slug: "system-api"
excerpt: "This API is used to get the system information."
hidden: false
metadata: 
  image: []
  robots: "index"
createdAt: "Fri Apr 14 2023 09:54:43 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Thu Jun 22 2023 02:09:16 GMT+0000 (Coordinated Universal Time)"
layout: "default"
parent: "Basic"
grand_parent: "APIs"
nav_order: 2
---
# System 
This API is used to get the system information.

***

- [getSystemInfo](system-api#getsysteminfo-object-object) To retrieve information about the system through a callback.
- [getSystemInfoSync](system-api#getsysteminfosync)- To retrieve information about the system synchronously.

# getSystemInfo (Object object)

To retrieve information about the system through a callback.

# Parameters

**Object object**

| Attribute | Type     | Required | Description                                                                            |
| :-------- | :------- | :------- | :------------------------------------------------------------------------------------- |
| success   | Function | No       | Callback function for a successful API call.                                           |
| fail      | Function | No       | Callback function for a failed API call.                                               |
| complete  | Function | No       | Callback function for an API call end (executed for both successful and failed calls). |

# `object.success` callback function

## Object response

| Attribute | Type | Description |
| :-------- | :--- | :---------- |
| brand | String | Device brand. |
| model | String | Device model. |
| pixelRatio | Number | Device pixel ratio. |
| screenWidth | Number | Display width in px. |
| screenHeight | Number | Display height in px. |
| windowWidth | Number | Usable window width in px. |
| windowHeight | Number | Usable window height in px. |
| statusBarHeight | Number | Status bar height in px. |
| language | String | Language. |
| version | String | Version number. |
| system | String | Operating system and version. |
| platform | String | Client platform. |
| SDKVersion | String | Base library version of the client. |
| AppPlatform | String | App platform. |
| safeArea | Object | Safe area in portrait mode. |
| theme | String | Current system theme.  <br />Valid values: `light` ,` dark` .  <br />This parameter can be obtained only if `\"darkmode\": true` is globally configured; otherwise, it will be` undefined`. |

### Sample code

```javascript
// JavaScript
wx.getSystemInfo({
	success(res) {
    console.log(res.model)
    console.log(res.pixelRatio)
    console.log(res.windowWidth)
    console.log(res.windowHeight)
    console.log(res.language)
    console.log(res.version)
    console.log(res.platform)
  }
})
```

# getSystemInfoSync()

Sync version of [wx.getSystemInfo](system-api#getsysteminfo-object-object).

## Returned value

### Object response

| Attribute | Type | Description |
| :-------- | :--- | :---------- |
| brand | String | Device brand. |
| model | String | Device model. |
| pixelRatio | Number | Device pixel ratio. |
| screenWidth | Number | Display width in px. |
| screenHeight | Number | Display height in px. |
| windowWidth | Number | Usable window width in px. |
| windowHeight | Number | Usable window height in px. |
| statusBarHeight | Number | Status bar height in px. |
| language | String | Language. |
| version | String | Version number. |
| system | String | Operating system and version. |
| platform | String | Client platform. |
| SDKVersion | String | Base library version of the client. |
| AppPlatform | String | App platform. |
| safeArea | Object | Safe area in portrait mode. |
| theme | String | Current system theme.  <br />Valid values: `light` ,` dark` .  <br />This parameter can be obtained only if `\"darkmode\": true` is globally configured; otherwise, it will be` undefined`. |

### Sample code

```javascript
// JavaScript
try {
 const res = wx.getSystemInfoSync()
 console.log(res.model)
 console.log(res.pixelRatio)
 console.log(res.windowWidth)
 console.log(res.windowHeight)
 console.log(res.language)
 console.log(res.version)
 console.log(res.platform)
} catch (e) {
 // Do something when catch error
}
```

## Structure of `res.safeArea`

| Attribute | Type   | Description                                                                                   |
| :-------- | :----- | :-------------------------------------------------------------------------------------------- |
| left      | number | The value of a coordinate on the horizontal axis of the top-left corner of the safe area.     |
| right     | number | The value of a coordinate on the horizontal axis of the bottom-right corner of the safe area. |
| top       | number | The value of a coordinate on the vertical access of the top-left corner of the safe area.     |
| bottom    | number | The value of a coordinate on the vertical access of the bottom-right corner of the safe area. |
| width     | number | Safe area width in pixels.                                                                    |
| height    | number | Safe area height in pixels.                                                                   |
