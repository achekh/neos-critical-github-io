---
title: "Messages"
slug: "messages-copy"
excerpt: "This section explains the concept of messages."
hidden: true
metadata: 
  image: []
  robots: "index"
createdAt: "Mon May 08 2023 09:21:09 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Mon May 29 2023 10:55:19 GMT+0000 (Coordinated Universal Time)"
layout: "default"
parent: "Open Capabilities (COPY)"
grand_parent: "Guide"
---
# Uniform Service Messages

In order to facilitate developers to send user service messages and simplify the issuing of Mini Program and Official Account message templates, the Mini Program provides a uniform service message issuing API.

## Related APIs

- [Issue uniform service messages](<>)

# Customer Service Messages

## Using Customer Service Messages on the Page

The developer needs to set the `open-type` value of the button component to contact. After tapping the button, the user will enter a customer service session. When tapping the Mini Program message in the session, the user will return to the Mini Program. The developer can get the `path` of the page on which the user taps the message and the corresponding parameter `query` via the `bindcontact` event callback.

## Code sample

```Text code
<button open-type="contact" bindcontact="handleContact"></button>
```

```Text code
Page({
    handleContact (e) {
        console.log(e.path)
        console.log(e.query)
    }
})
```

## Response parameters

| Parameter | Type   | Description                                                |
| :-------- | :----- | :--------------------------------------------------------- |
| path      | String | The path used to store Mini Program messages               |
| query     | Object | The query parameter specified for the Mini Program message |

## Integrating Messaging Service in Server

When a user sends messages to the Mini Program customer service or enter a session, messages and events are pushed from the Weixin server to the URL the developer entered in the server configurations (a cloud function is configured if Cloud Base is used), and the developer can respond according to the business logic. For information on how to integrate and use messaging service, refer to [Message Push](<>).

# Receiving Messages and Events

Use `<button open-type="contact" />` in the page to display the customer service session button.

When a user sends a message in a customer service session, or when an event is pushed due to certain operations performed by the user, the Weixin server will send the data package of the message or event to the URL configured by the developer. After receiving the request, the developer can respond to the request asynchronously via the Send Customer Service Messages API.

The followings are the structures of JSON and XML data packages via which various types of messages are pushed.

## Text Messages

The following data package is generated when the user sends text messages in a customer service session:

### In XML format

```xml
<xml>
   <ToUserName><![CDATA[toUser]]></ToUserName>
   <FromUserName><![CDATA[fromUser]]></FromUserName>
   <CreateTime>1482048670</CreateTime>
   <MsgType><![CDATA[text]]></MsgType>
   <Content><![CDATA[this is a test]]></Content>
   <MsgId>1234567890123456</MsgId>
</xml>
```

### In JSON format

```json
{
  "ToUserName": "toUser",
  "FromUserName": "fromUser",
  "CreateTime": 1482048670,
  "MsgType": "text",
  "Content": "this is a test",
  "MsgId": 1234567890123456
}
```

## Parameters

| Parameter    | Description                             |
| :----------- | :-------------------------------------- |
| ToUserName   | Mini Program's original ID              |
| FromUserName | Sender's openid                         |
| CreateTime   | Creation time of the message (integral) |
| MsgType      | text                                    |
| Content      | Text message content                    |
| MsgId        | Message ID (64-bit integer)             |

## Image Messages

The following data package is generated when the user sends image messages in a customer service session:

### In XML format

```xml
<xml>
      <ToUserName><![CDATA[toUser]]></ToUserName>
      <FromUserName><![CDATA[fromUser]]></FromUserName>
      <CreateTime>1482048670</CreateTime>
      <MsgType><![CDATA[image]]></MsgType>
      <PicUrl><![CDATA[this is a url]]></PicUrl>
      <MediaId><![CDATA[media_id]]></MediaId>
      <MsgId>1234567890123456</MsgId>
</xml>
```

### In JSON format

```json
{
  "ToUserName": "toUser",
  "FromUserName": "fromUser",
  "CreateTime": 1482048670,
  "MsgType": "image",
  "PicUrl": "this is a url",
  "MediaId": "media_id",
  "MsgId": 1234567890123456
}
```

## Parameters

| Parameter    | Description                                                                                |
| :----------- | :----------------------------------------------------------------------------------------- |
| ToUserName   | Mini Program's original ID                                                                 |
| FromUserName | Sender's openid                                                                            |
| CreateTime   | Creation time of the message (integral)                                                    |
| MsgType      | image                                                                                      |
| PicUrl       | Image link (generated by the system)                                                       |
| MediaId      | Media ID of the image message. Data can be fetched by calling the Get Temporary Media API. |
| MsgId        | Message ID (64-bit integer)                                                                |

## Mini Program Card Messages

The following data package is generated when the user sends Mini Program card messages in a customer service session:

### In XML format

```xml
<xml>
  <ToUserName><![CDATA[toUser]]></ToUserName>
  <FromUserName><![CDATA[fromUser]]></FromUserName>
  <CreateTime>1482048670</CreateTime>
  <MsgType><![CDATA[miniprogrampage]]></MsgType>
  <MsgId>1234567890123456</MsgId>
  <Title><![CDATA[Title]]></Title>
  <AppId><![CDATA[AppId]]></AppId>
  <PagePath><![CDATA[PagePath]]></PagePath>
  <ThumbUrl><![CDATA[ThumbUrl]]></ThumbUrl>
  <ThumbMediaId><![CDATA[ThumbMediaId]]></ThumbMediaId>
</xml>
```

### In JSON format

```json
{
  "ToUserName": "toUser",
  "FromUserName": "fromUser",
  "CreateTime": 1482048670,
  "MsgType": "miniprogrampage",
  "MsgId": 1234567890123456,
  "Title":"title",
  "AppId":"appid",
  "PagePath":"path",
  "ThumbUrl":"",
  "ThumbMediaId":""
}
```

## Parameters

| Parameter    | Description                             |
| :----------- | :-------------------------------------- |
| ToUserName   | Mini Program's original ID              |
| FromUserName | Sender's openid                         |
| CreateTime   | Creation time of the message (integral) |
| MsgType      | miniprogrampage                         |
| MsgId        | Message ID (64-bit integer)             |
| Title        | Title                                   |
| AppId        | Mini Program's appid                    |
| PagePath     | Mini Program's page path                |
| ThumbUrl     | Temporary CDN link of the cover image   |
| ThumbMediaId | Temporary media ID of the cover image   |

## Event of Entering Session

The following data package is generated when the user enters a customer service session by tapping the "customer service session button" in the Mini Program:

### In XML format

```xml
<xml>
    <ToUserName><![CDATA[toUser]]></ToUserName>
    <FromUserName><![CDATA[fromUser]]></FromUserName>
    <CreateTime>1482048670</CreateTime>
    <MsgType><![CDATA[event]]></MsgType>
    <Event><![CDATA[user_enter_tempsession]]></Event>
    <SessionFrom><![CDATA[sessionFrom]]></SessionFrom>
</xml>
```

### In JSON format

```json
{
  "ToUserName": "toUser",
  "FromUserName": "fromUser",
  "CreateTime": 1482048670,
  "MsgType": "event",
  "Event": "user_enter_tempsession",
  "SessionFrom": "sessionFrom"
}
```

## Parameters

| Parameter    | Description                                                                            |
| :----------- | :------------------------------------------------------------------------------------- |
| ToUserName   | Mini Program's original ID                                                             |
| FromUserName | Sender's openid                                                                        |
| CreateTime   | Creation time of the event (integral)                                                  |
| MsgType      | event                                                                                  |
| Event        | Event type, user_enter_tempsession                                                     |
| SessionFrom  | The session-from property set by the developer in the customer service session button. |

# Sending Customer Service Messages

When an interaction of special action (see the following table for specific action) is generated between the user and the Mini Program customer service, Weixin sends the message data to the developer, and then the developer sends messages to the user by calling the Send Customer Service Messages API within a period of time (48 hours). This API is mainly used for customer service and other features with manual message processing, so that the developer can provide better services for users.

The allowed action is listed below. The time limit and max number of messages sent via the customer service API vary depending on different actions triggered.

| User Action              | Max Number of Messages Sent | Time Limit |
| :----------------------- | :-------------------------- | :--------- |
| The user sends a message | 5                           | 48 hrs     |

# Forwarding Messages

# Forwarding Customer Service Messages

If the push notification is configured for a Mini Program, when a Weixin user sends messages to the Mini Program's customer service, the Weixin server will first POST the messages to the URL configured by the developer. If the messages are intended to be forwarded to online version of the customer service tool, the developer must return messages with MsgType as transfer_customer_service in the response package. After receiving the response, the Weixin server forwards the messages sent in that session to the customer service system.

When the user is connected to the customer service, before the customer service closes the session, messages sent by the user in the session are directly forwarded to the customer service system. When the session is not closed by the customer service after 30 minutes, the Weixin server will automatically stop forwarding messages to the customer service, and the messages will be sent to the URL configured by the developer.

When the user is waiting in queue, the messages sent by the user will still be pushed to the URL configured by the developer.

Note that, only messages sent by Weixin users will be forwarded, other events (e.g. the user starts a customer service session from the Mini Program) should not be forwarded; otherwise, the customer service will see meaningless messages on the customer service system.

## Forwarding Messages to the Online Version of Customer Service Tool

The developer only returns messages with MsgType as transfer_customer_service in the response package. The Weixin server forwards the messages sent in that session to the customer service system after receiving the response.

```xml
<xml>
    <ToUserName><![CDATA[touser]]></ToUserName>
    <FromUserName><![CDATA[fromuser]]></FromUserName>
    <CreateTime>1399197672</CreateTime>
    <MsgType><![CDATA[transfer_customer_service]]></MsgType>
</xml>
```

**Parameters**

| Parameter    | Required | Description                             |
| :----------- | :------- | :-------------------------------------- |
| ToUserName   | Yes      | Recipent's ID (OpenID received)         |
| FromUserName | Yes      | Developer's Weixin ID                   |
| CreateTime   | Yes      | Creation time of the message (integral) |
| MsgType      | Yes      | transfer_customer_service               |

# Customer Service Typing Status

By calling the Customer Service Typing Status API, the developer can return the current typing status of customer service to the user.

1. This API requires access to the customer service message API.
2. If trigger conditions of sending customer service messages are not met, typing status cannot be sent.
3. To send typing status, there should be message interactions between the user and the customer service within the last 30 seconds.
4. When the customer service is typing (lasting for 15s), the developer cannot send typing status repeatedly.
5. When the customer service is typing, if messages are forwarded to the user, the typing status is canceled at the same time.

# Temporary Media

# Using Temporary Media in Customer Service Messages

Developers can get or upload temporary media when receiving and sending customer service messages.

## Getting Temporary Media

After receiving a user message, the developer can get the temporary media in the message via the [Get Temporary Media API.](<>)

## Uploading Temporary Media

Temporary media can be uploaded via the [Upload Temporary Media API](<>), and used in the Send [Customer Service Media API](<>).
