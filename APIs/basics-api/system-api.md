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
---
# System 
*** 
- [getSystemInfo](doc:system-api#getsysteminfo-object-object) To retrieve information about the system through a callback.
- [getSystemInfoSync](doc:system-api#getsysteminfosync)- To retrieve information about the system synchronously.

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

[block:parameters]
{
  "data": {
    "h-0": "Attribute",
    "h-1": "Type",
    "h-2": "Description",
    "0-0": "brand",
    "0-1": "String",
    "0-2": "Device brand.",
    "1-0": "model",
    "1-1": "String",
    "1-2": "Device model.",
    "2-0": "pixelRatio",
    "2-1": "Number",
    "2-2": "Device pixel ratio.",
    "3-0": "screenWidth",
    "3-1": "Number",
    "3-2": "Display width in px.",
    "4-0": "screenHeight",
    "4-1": "Number",
    "4-2": "Display height in px.",
    "5-0": "windowWidth",
    "5-1": "Number",
    "5-2": "Usable window width in px.",
    "6-0": "windowHeight",
    "6-1": "Number",
    "6-2": "Usable window height in px.",
    "7-0": "statusBarHeight",
    "7-1": "Number",
    "7-2": "Status bar height in px.",
    "8-0": "language",
    "8-1": "String",
    "8-2": "Language.",
    "9-0": "version",
    "9-1": "String",
    "9-2": "Version number.",
    "10-0": "system",
    "10-1": "String",
    "10-2": "Operating system and version.",
    "11-0": "platform",
    "11-1": "String",
    "11-2": "Client platform.",
    "12-0": "SDKVersion",
    "12-1": "String",
    "12-2": "Base library version of the client.",
    "13-0": "AppPlatform",
    "13-1": "String",
    "13-2": "App platform.",
    "14-0": "safeArea",
    "14-1": "Object",
    "14-2": "Safe area in portrait mode.",
    "15-0": "theme",
    "15-1": "String",
    "15-2": "Current system theme.  \nValid values: `light` ,` dark` .  \nThis parameter can be obtained only if `\"darkmode\": true` is globally configured; otherwise, it will be` undefined`."
  },
  "cols": 3,
  "rows": 16,
  "align": [
    "left",
    "left",
    "left"
  ]
}
[/block]


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

Sync version of [wx.getSystemInfo](doc:system-api#getsysteminfo-object-object).

## Returned value

### Object response

[block:parameters]
{
  "data": {
    "h-0": "Attribute",
    "h-1": "Type",
    "h-2": "Description",
    "0-0": "brand",
    "0-1": "String",
    "0-2": "Device brand.",
    "1-0": "model",
    "1-1": "String",
    "1-2": "Device model.",
    "2-0": "pixelRatio",
    "2-1": "Number",
    "2-2": "Device pixel ratio.",
    "3-0": "screenWidth",
    "3-1": "Number",
    "3-2": "Display width in px.",
    "4-0": "screenHeight",
    "4-1": "Number",
    "4-2": "Display height in px.",
    "5-0": "windowWidth",
    "5-1": "Number",
    "5-2": "Usable window width in px.",
    "6-0": "windowHeight",
    "6-1": "Number",
    "6-2": "Usable window height in px.",
    "7-0": "statusBarHeight",
    "7-1": "Number",
    "7-2": "Status bar height in px.",
    "8-0": "language",
    "8-1": "String",
    "8-2": "Language.",
    "9-0": "version",
    "9-1": "String",
    "9-2": "Version number.",
    "10-0": "system",
    "10-1": "String",
    "10-2": "Operating system and version.",
    "11-0": "platform",
    "11-1": "String",
    "11-2": "Client platform.",
    "12-0": "SDKVersion",
    "12-1": "String",
    "12-2": "Base library version of the client.",
    "13-0": "AppPlatform",
    "13-1": "String",
    "13-2": "App platform.",
    "14-0": "safeArea",
    "14-1": "Object",
    "14-2": "Safe area in portrait mode.",
    "15-0": "theme",
    "15-1": "String",
    "15-2": "Current system theme.  \nValid values: `light` ,` dark` .  \nThis parameter can be obtained only if `\"darkmode\": true` is globally configured; otherwise, it will be` undefined`."
  },
  "cols": 3,
  "rows": 16,
  "align": [
    "left",
    "left",
    "left"
  ]
}
[/block]


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
