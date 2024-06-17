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
| sign | String | Yes | Authenticated security key. | c09636a3a529a  \n386fdaa389228  \ne36fac |
| timestamp | Long | Yes | Unix Epoch timestamp within 5 minutes of the current calling interface, unit: milliseconds. | 1600140360000 |
| appid | String | Yes | Mini App ID. | 6364a1ec8754dd1a55d6b8de |
| notifyType | Integer | Yes | Message type;  \n1-plain text type | 1 |
| rulesType | String | Yes | Rules:  \n1-send to everyone  \n2- send by phone number  \n3-uid | 1 |
| countryCode | String | No | Country code. | +966 |
| mobileNumber | String | No | Telephone number | 123456789 |
| openIds | Attay<String> | No | Mini App user's openid | 15555555555 |
| title | String | Yes | Push notification title | "Hello World" |
| text | String | Yes | Push notification content| "This is a test push notification" |
| navigateType | String | Yes | Deep link navigation type;  \n1- Mini App, 2- URL | 1 |
| miniAppId | String | No| mini App ID  \nNote: When  \nnavigateType is 1 (navigation type is Mini App), this value is required.| |
| url| String | No | Note: When  \nnavigateType is  \n2 (navigation type is URL), this value  \nis required.| |
| link | String | No | Mini App page link | |
| language | String | No | Push notification language  \nNote:  \nWhen the  \nnavigate type is  1 (navigation type is Mini  \nApp), this  \nvalue is required. | en_US;  \nar_SA;" |

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
| responseHeader | Response header | Object| {  \nstatus: 200,  \nmsg: \"OK\"  \n} |
| response | Whether the sending of the  \nmessage was successful; true  \nmeans that the sending of the  \nnotification was successful and  \nfailed | Boolean | True |

Response header parameters:

| Parameter | Description                       | Type    | Example |
| :-------- | :-------------------------------- | :------ | :------ |
| status    | HTTP corresponding status code.   | Integer | 200     |
| msg       | Message about the request status/ | String  | "OK"    |

> 📘 Note
> 
> In order to receive the push notification, your Mini App should be published, Mini Apps that are in development mode won't recieve push notifications.
