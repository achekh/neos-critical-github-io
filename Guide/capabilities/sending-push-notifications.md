---
title: "Sending push notifications"
slug: "sending-push-notifications"
excerpt: ""
hidden: false
metadata: 
  image: []
  robots: "index"
createdAt: "Thu May 18 2023 06:27:53 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Fri Jul 14 2023 11:24:45 GMT+0000 (Coordinated Universal Time)"
layout: "default"
parent: "Backend assisted capabilities"
grand_parent: "Guide"
nav_order: 1
---
# Sending push notifications 
*** 
To send a push notification to Mini Apps' users, you can call the following API:

**URL:** <https://qa.neuxnet.com/neuopenapi/notify/sendNotify>

**Request method:** `POST`

**Content-Type:** `application/x-www-form-urlencoded`

**Request Parameter:**

| Parameter | Type | Available | Description             | Example         |
| :-------- | :--- | :-------- | :---------------------- | :-------------- |
| sign | String | Yes | Authenticated security key. | c09636a3a529a  <br>386fdaa389228  <br>e36fac |
| timestamp | Long | Yes | Unix Epoch timestamp within 5 minutes of the current calling interface, unit: milliseconds. | 1600140360000 |
| appid | String | Yes | Mini App ID. | 6364a1ec8754dd1a55d6b8de |
| notifyType | Integer | Yes | Message type;  <br>1-plain text type | 1 |
| rulesType | String | Yes | Rules:  <br>1-send to everyone  <br>2- send by phone number  <br>3-uid | 1 |
| countryCode | String | No | Country code. | +966 |
| mobileNumber | String | No | Telephone number | 123456789 |
| openIds | Attay<String> | No | Mini App user's openid | 15555555555 |
| title | String | Yes | Push notification title | "Hello World" |
| text | String | Yes | Push notification content| "This is a test push notification" |
| navigateType | String | Yes | Deep link navigation type;  <br>1- Mini App, 2- URL | 1 |
| miniAppId | String | No| mini App ID  <br>Note: When  <br>navigateType is 1 (navigation type is Mini App), this value is required.| |
| url| String | No | Note: When  <br>navigateType is  <br>2 (navigation type is URL), this value  <br>is required.| |
| link | String | No | Mini App page link | |
| language | String | No | Push notification language  <br>Note:  <br>When the  <br>navigate type is  1 (navigation type is Mini  <br>App), this  <br>value is required. | en_US;  <br>ar_SA;" |

Response Result:

```json
// Response
{
  "responseHeader": {
    "status": 200,
		"msg": "OK"
	},
  "response": true
}
```

Response Parameters:

| Parameter | Description | Type | Example |
| :-------- | :-------------------------------------- | :-------- | :--------- |
| responseHeader | Response header | Object| {  <br>status: 200,  <br>msg: \"OK\"  <br>} |
| response | Whether the sending of the  <br>message was successful; true  <br>means that the sending of the  <br>notification was successful and  <br>failed | Boolean | True |

Response header parameters:

| Parameter | Description                       | Type    | Example |
| :-------- | :-------------------------------- | :------ | :------ |
| status    | HTTP corresponding status code.   | Integer | 200     |
| msg       | Message about the request status/ | String  | "OK"    |

> 📘 Note
> 
> In order to receive the push notification, your Mini App should be published, Mini Apps that are in development mode won't recieve push notifications.
