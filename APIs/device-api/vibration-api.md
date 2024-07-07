---
title: "Vibration"
slug: "vibration-api"
excerpt: "This section lists the Vibration related APIs."
hidden: false
createdAt: "Mon Apr 24 2023 08:36:42 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Wed Nov 29 2023 18:08:02 GMT+0000 (Coordinated Universal Time)"
layout: "default"
parent: "Device"
grand_parent: "APIs"
nav_order: 15
---
# Vibration 
This section lists the Vibration related APIs.

***

- [vibrateShort](vibration-api#wxvibrateshortobject-object)
- [vibrateLong](vibration-api#wxvibratelongobject-object)

# wx.vibrateShort(Object object)

Makes the phone vibrate for a short period of time (15 ms). It takes effect only on iPhone 7/7 Plus or later and Android devices.

## Parameters

**Object object**

| Attribute | Type     | Required | Description                                                                         |
| :-------- | :------- | :------- | :---------------------------------------------------------------------------------- |
| success   | Function | No       | Callback function for successful API call.                                          |
| fail      | Function | No       | Callback function for failed API call.                                              |
| complete  | Function | No       | Callback function for API call end (executed for both successful and failed calls). |

# wx.vibrateLong(Object object)

Makes the phone vibrate for a long period of time (400 ms).

# Parameters

**Object object**

| Attribute | Type     | Required | Description                                                                        |
| :-------- | :------- | :------- | :--------------------------------------------------------------------------------- |
| success   | Function | No       | Callback function for successful API call                                          |
| fail      | Function | No       | Callback function for failed API call                                              |
| complete  | Function | No       | Callback function for API call end (executed for both successful and failed calls) |
