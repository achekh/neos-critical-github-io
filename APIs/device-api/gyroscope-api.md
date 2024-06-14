---
title: "Gyroscope"
slug: "gyroscope-api"
excerpt: "This section list the Gyroscope related APIs."
hidden: false
createdAt: "Mon Apr 24 2023 08:36:34 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Wed Nov 29 2023 18:07:06 GMT+0000 (Coordinated Universal Time)"
layout: "default"
parent: "Device"
grand_parent: "APIs"
---
# Gyroscope 
*** 
- [stopGyroscope](doc:gyroscope-api#wxstopgyroscopeobject-object)
- [startGyroscope](doc:gyroscope-api#wxstartgyroscopeobject-object)
- [onGyroscopeChange](doc:gyroscope-api#wxongyroscopechangefunction-callback)

# wx.startGyroscope(Object object)

Listens for gyroscope data.

# Parameters

**Object object**

| Attribute | Type     | Default | Required | Description                                                                         |
| :-------- | :------- | :------ | :------- | :---------------------------------------------------------------------------------- |
| interval  | String   | normal  | No       | Execution frequency of the callback function for gyroscope data listening.          |
| success   | Function |         | No       | Callback function for successful API call.                                          |
| fail      | Function |         | No       | Callback function for failed API call.                                              |
| complete  | Function |         | No       | Callback function for API call end (executed for both successful and failed calls). |

Valid values of `object.interval`

| Value  | Description                                                              |
| :----- | :----------------------------------------------------------------------- |
| game   | Callback frequency suitable for game update, which is around 20 ms/time. |
| ui     | Callback frequency suitable for UI update, which is around 60 ms/time.   |
| normal | Normal callback frequency, which is around 200 ms/time.                  |

# wx.stopGyroscope(Object object)

Unlistens for gyroscope data.

# Parameters

**Object object**

| Attribute | Type     | Required | Description                                                                         |
| :-------- | :------- | :------- | :---------------------------------------------------------------------------------- |
| success   | Function | No       | Callback function for successful API call.                                          |
| fail      | Function | No       | Callback function for failed API call.                                              |
| complete  | Function | No       | Callback function for API call end (executed for both successful and failed calls). |

# wx.onGyroscopeChange(function callback)

Listens for the gyroscope data change event. The frequency is determined by the `interval `parameter of [wx.startGyroscope()](doc:gyroscope-api#wxstartgyroscopeobject-object). Listening can be stopped by calling [wx.stopGyroscope().](doc:gyroscope-api#wxstopgyroscopeobject-object)

## Parameters

## Function callback

Callback function for the gyroscope data change event.

# Parameters

**Object res**

| Attribute | Type   | Description |
| :-------- | :----- | :---------- |
| res       | Object |             |

Structure of `res`

| Attribute | Type   | Description                     |
| :-------- | :----- | :------------------------------ |
| x         | Number | Angular velocity of the X axis. |
| y         | Number | Angular velocity of the Y axis. |
| z         | Number | Angular velocity of the Z axis. |
