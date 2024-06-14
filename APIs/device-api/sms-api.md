---
title: "SMS"
slug: "sms-api"
excerpt: "This section contains SMS related API that opens the SMS sending UI of the phone."
hidden: false
metadata: 
  image: []
  robots: "index"
createdAt: "Mon Apr 24 2023 08:36:40 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Fri Jul 14 2023 11:23:17 GMT+0000 (Coordinated Universal Time)"
layout: "default"
parent: "Device"
grand_parent: "APIs"
---
# SMS 
*** 
# wx.sendSms(Object object)

Opens the SMS sending UI of the phone.

# Parameters

**Object object**

| Attribute   | Type     | Required | Description                                                                         |
| :---------- | :------- | :------- | :---------------------------------------------------------------------------------- |
| phoneNumber | String   | No       | The mobile number populated on the SMS sending UI content string.                   |
| content     | String   | No       | The content populated on the SMS sending UI.                                        |
| success     | Function | No       | Callback function for successful API call.                                          |
| fail        | Function | No       | Callback function for failed API call.                                              |
| complete    | Function | No       | Callback function for API call end (executed for both successful and failed calls). |
