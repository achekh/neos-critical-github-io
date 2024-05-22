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
---
To send a push notification to Mini Apps' users, you can call the following API:

**URL:** <https://qa.neuxnet.com/neuopenapi/notify/sendNotify>

**Request method:** `POST`

**Content-Type:** `application/x-www-form-urlencoded`

**Request Parameter:**

[block:parameters]
{
  "data": {
    "h-0": "Parameter",
    "h-1": "Type",
    "h-2": "Available",
    "h-3": "Description",
    "h-4": "Example",
    "0-0": "sign",
    "0-1": "String",
    "0-2": "Yes",
    "0-3": "Authenticated security key.",
    "0-4": "c09636a3a529a  \n386fdaa389228  \ne36fac",
    "1-0": "timestamp",
    "1-1": "Long",
    "1-2": "Yes",
    "1-3": "Unix Epoch timestamp within 5 minutes of the current calling interface, unit: milliseconds.",
    "1-4": "1600140360000",
    "2-0": "appid",
    "2-1": "String",
    "2-2": "Yes",
    "2-3": "Mini App ID.",
    "2-4": "6364a1ec8754dd1a55d6b8de",
    "3-0": "notifyType",
    "3-1": "Integer",
    "3-2": "Yes",
    "3-3": "Message type;  \n1-plain text type",
    "3-4": "1",
    "4-0": "rulesType",
    "4-1": "String",
    "4-2": "Yes",
    "4-3": "Rules:  \n1-send to everyone  \n2- send by phone number  \n3-uid",
    "4-4": "1",
    "5-0": "countryCode",
    "5-1": "String",
    "5-2": "No",
    "5-3": "Country code.",
    "5-4": "+966",
    "6-0": "mobileNumber",
    "6-1": "String",
    "6-2": "No",
    "6-3": "Telephone number",
    "6-4": "123456789",
    "7-0": "openIds",
    "7-1": "Attay<String>",
    "7-2": "No",
    "7-3": "Mini App user's openid",
    "7-4": "15555555555",
    "8-0": "title",
    "8-1": "String",
    "8-2": "Yes",
    "8-3": "Push notification title",
    "8-4": "\"Hello World\"",
    "9-0": "text",
    "9-1": "String",
    "9-2": "Yes",
    "9-3": "Push notification content",
    "9-4": "\"This is a test push notification\"",
    "10-0": "navigateType",
    "10-1": "String",
    "10-2": "Yes",
    "10-3": "Deep link navigation type;  \n1- Mini App, 2- URL",
    "10-4": "1",
    "11-0": "miniAppId",
    "11-1": "String",
    "11-2": "No",
    "11-3": "mini App ID  \nNote: When  \nnavigateType is 1 (navigation type is Mini App), this value is required.",
    "11-4": "",
    "12-0": "url",
    "12-1": "String",
    "12-2": "No",
    "12-3": "Note: When  \nnavigateType is  \n2 (navigation type is URL), this value  \nis required.",
    "12-4": "",
    "13-0": "link",
    "13-1": "String",
    "13-2": "No",
    "13-3": "Mini App page link",
    "13-4": "",
    "14-0": "language",
    "14-1": "String",
    "14-2": "No",
    "14-3": "Push notification language  \nNote:  \nWhen the  \nnavigate type is  1 (navigation type is Mini  \nApp), this  \nvalue is required.",
    "14-4": "en_US;  \nar_SA;"
  },
  "cols": 5,
  "rows": 15,
  "align": [
    "left",
    "left",
    "left",
    "left",
    "left"
  ]
}
[/block]


Response Result:

```json Response
{
  "responseHeader": {
    "status": 200,
		"msg": "OK"
	},
  "response": true
}
```

Response Parameters:

[block:parameters]
{
  "data": {
    "h-0": "Parameter",
    "h-1": "Description",
    "h-2": "Type",
    "h-3": "Example",
    "0-0": "responseHeader",
    "0-1": "Response header",
    "0-2": "Object",
    "0-3": "{  \nstatus: 200,  \nmsg: \"OK\"  \n}",
    "1-0": "response",
    "1-1": "Whether the sending of the  \nmessage was successful; true  \nmeans that the sending of the  \nnotification was successful and  \nfailed",
    "1-2": "Boolean",
    "1-3": "True"
  },
  "cols": 4,
  "rows": 2,
  "align": [
    "left",
    "left",
    "left",
    "left"
  ]
}
[/block]


Response header parameters:

| Parameter | Description                       | Type    | Example |
| :-------- | :-------------------------------- | :------ | :------ |
| status    | HTTP corresponding status code.   | Integer | 200     |
| msg       | Message about the request status/ | String  | "OK"    |

> 📘 Note
> 
> In order to receive the push notification, your Mini App should be published, Mini Apps that are in development mode won't recieve push notifications.
