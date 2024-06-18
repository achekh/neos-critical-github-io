---
title: "Forwarding"
slug: "forwarding-copy"
excerpt: "This section explains the concept of forwarding in Mini App."
hidden: true
metadata: 
  image: []
  robots: "index"
createdAt: "Mon May 08 2023 09:21:04 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Mon May 29 2023 10:53:50 GMT+0000 (Coordinated Universal Time)"
layout: "default"
parent: "Open Capabilities (COPY)"
grand_parent: "Guide"
---
# Forwarding 
*** 
After a dynamic message is sent, the message content can be modified through updatableMessage.setUpdatableMsg.

## Obtaining More Forwarded Information

The Forwarded Mini Program is typically opened twice in the hopes that some information, such as the group's identity, can be gleaned. Now, after the user forwards the applet to any group chat, this forwarded card can be obtained in App.onLaunch or App.onShow when the forwarded card is opened by other users in the group chat by calling wx.showShareMenu and setting withShareTicket to true. You can obtain the forwarding details by calling the wx.getShareInfo interface and providing this shareTicket.

## Initiating Forwarding in the Page

> The basic library 1.2.0 is supported, and the lower version needs to be compatible.

By setting the property open-type="share" to the button component, the Page.onShareAppMessage event can be triggered after the user clicks the button. The related component is button.

## User Guide

The forward button is designed to help users share content and services with friends more easily. They can forward anything independently at any time. Developers may create a better user experience by following the guidelines below.

1. **Concise meaning**: Button images should be clear and recognizable, which reduces the time the user requires to understand its usage. Such button media can be found in our resource download center for direct use, or you can create your own button samples that convey meaning clearly according to the style of your business design. Of course, you can also directly use the ready-made button Forward to friends, which is also concise enough.
2. **Easy to tap**: The tap area of the button should not be too small or too big. Besides, the forward button is just like other buttons, their tap areas should not be too close together to prevent incorrect operation.
3. **Shown as needed**: The forward button is not suitable for every page. This feature is not recommended for non-public content that involves user privacy, or scenarios where the user's ongoing operation may be interrupted. As we will use the user's screen images as the sample images in the forwarding process, the user's personal information must be hided.
4. **Respecting what the user wants**: Not every user would like to share your Mini Program with friends. Therefore, this should not be an induced or compulsory action, e.g. only allowing certain features to be unlocked after forwarding. Note that such practices are not recommended and may be in violation of our Operating Regulations. We strongly suggest that you read this content before using.

What listed above are some of the key points. See the complete Design Guidelines for more information.

> 📘 Note
> 
> 1. If the forwarded image is not defined, the current page will be taken by default, starting from the top with a height 80% of the width of the screen.
> 2. For debugging, see General forwarding and Forwarding with shareTicket.
> 3. The `shareTickets` return value can only be obtained by forwarding the Mini Program to group chats.
> 4. The `shareTicket` remains effective only within the current Mini Program's lifecycle
> 5. Due to policy changes, capabilities of the Mini Program group are being adjusted. Developers can use the group ID of the wx.getShareInfo API for development.

# Dynamic Messages

Support for forwarding dynamic messages starts with base library 2.4.0. Compared with common messages, dynamic messages have the following features:

1. After a message is sent, the developer can modify part of the message content through the backend API.
2. Messages have corresponding reminder button. Users can tap the reminder button to subscribe to the reminders. Developers can modify the message state through the backend and push a reminder message to the users who have subscribed to the reminders.

## Message Attributes

Dynamic messages have state, text content, and text color.

## State

A message has two states, each with its corresponding text content and color, where state 0 can be converted to states 0 and 1, and state 1 can no longer be converted.

| State | Text Content                                                         | Color    | Allowed Conversion of State |
| :---- | :------------------------------------------------------------------- | :------- | :-------------------------- |
| 0     | “Members are joining, currently {member_count}/{room_limit} persons” | # FA9D39 | 0, 1                        |
| 1     | “Has started”                                                        | # CCCCCC | None                        |

## State parameters

Each state can carry parameters when it is converted. Specific parameters are described as follows.

| Parameter    | Type   | Description                                                                                                                                                                                                        |
| :----------- | :----- | :----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| member_count | string | Valid for state 0, the value of member_count in the text content template                                                                                                                                          |
| room_limit   | string | Valid for state 0, the value of room_limit in the text content template                                                                                                                                            |
| path         | string | Valid for state 1, the path used when taping [Enter] to enable the Mini Program. For Mini Games, there is no concept of a page that can be used to transmit a queried character string (query), such as "?foo=bar" |
| version_type | string | Valid for state 1, the version used when taping [Enter] to enable the Mini Program. Valid parameters are: develop (developer version), trial (test version), release (official version)                            |

## Usage

## 1. Create activity_id

Each dynamic message can be understood as an activity. Before launching an activity, `activity_id` needs to be created through the updatableMessage.createActivityId API. Subsequent forwarding and updating of dynamic messages require passing in this `activity_id.`

The default validity period for an activity is 24 hours. At the end of the activity, the message content will become a unified style:

- Text content: “Ended”
- Text color: #00ff00

## 2. Declare the message as a dynamic message before forwarding

Pass in the` isUpdatableMessage: true,` `templateInfo`, and `activityId` parameters by calling the wx.updateShareMenu API, where `activityId` is obtained from step 1.

```Text
// code
wx.updateShareMenu({
  withShareTicket: true,
  isUpdatableMessage: true,
  activityId: '', // Event ID
  templateInfo: {
    parameterList: [{
      name: 'member_count',
      value: '1'
    }, {
      name: 'room_limit',
      value: '3'
    }]
  }
})
```

## 3. Modify dynamic message content

After a dynamic message is sent, the message content can be modified through [updatableMessage.setUpdatableMsg](<>).

## Compatibility with Lower Versions

For the client versions that do not support dynamic messages, the received dynamic messages will be displayed as common messages.
