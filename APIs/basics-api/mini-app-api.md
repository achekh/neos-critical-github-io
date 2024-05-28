---
title: "Mini App"
slug: "mini-app-api"
excerpt: "Global Mini App APIs."
hidden: false
metadata: 
  image: []
  robots: "index"
createdAt: "Mon Apr 17 2023 05:28:04 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Fri Jul 14 2023 11:12:30 GMT+0000 (Coordinated Universal Time)"
layout: "default"
parent: "Basic"
grand_parent: "APIs"
---
- [Lifecycle](doc:mini-app-api#lifecycle)
  - [getLaunchOptionsSync](doc:mini-app-api#getLaunchOptionsSync)
- [App-level event](doc:mini-app-api#app-level-event)
  - [onError](doc:mini-app-api#wxonerror)
  - [offError](doc:mini-app-api#wxofferror)
  - [onThemeChange](doc:mini-app-api#wxonthemechangefunction-listener)
  - [offThemeChange](doc:mini-app-api#wxoffthemechangefunction-listener)

# Lifecycle

# getLaunchOptionsSync (Object object)

This app retrieves the parameter sent to the Mini App when the Mini App is started. The return value is consistent with the callback parameter, App.onLaunch.

## Returned value

**Object object**

# Startup Parameter

| Attribute    | Type   | Description                                                                                                                                                                                     |
| :----------- | :----- | :---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| path         | String | Path to start the Mini App.                                                                                                                                                                     |
| scene        | Number | Scene value to start the Mini App.                                                                                                                                                              |
| query        | Object | Query parameter to start the Mini App.                                                                                                                                                          |
| referrerInfo | Object | Source information If the current mini app is entered from another Mini App, official account, or app, this parameter will be returned; otherwise, `{}` will be returned (see the notes below). |

## Structure of `referrerInfo`

| Attribute | Type   | Description                                                                           |
| :-------- | :----- | :------------------------------------------------------------------------------------ |
| appId     | String | `appId` of the source Mini App, official account, or app.                             |
| extraData | Object | The data from the source Mini App, which is supported if `scene` is `1037` or` 1038`. |

## Structure of `forwardMaterials`

| Attribute | Type   | Description                 |
| :-------- | :----- | :-------------------------- |
| type      | String | `mimetype` of the file.     |
| name      | Object | Filename                    |
| path      | String | File path (or WebView URL). |
| size      | Number | File size                   |

## Scenes with valid `referrerInfo` returned

| Scene Value | Scene                                                    | `appId` Description                |
| :---------- | :------------------------------------------------------- | :--------------------------------- |
| 1020        | Mini app list on the profile page of an official account | The source is an official account. |
| 1035        | Custom menu of an official account                       | The source is an official account. |
| 1036        | App message sharing card                                 | The source is an app.              |
| 1037        | Another mini app                                         | The source is a Mini App.          |
| 1038        | Return from another mini app                             | The source is a Mini App.          |
| 1043        | Template message of an official account                  | The source is an official account. |

> 📘 Note
> 
> On certain versions, if there is no `referrerInfo` , `undefined` will be returned. We recommend you use `options.referrerInfo && options.referrerInfo.appId`.

# App-level event

The following are the different types of App-level event:

- [onError](doc:mini-app#wxonerror)
- [offError](doc:mini-app#wxofferror)
- [onThemeChange](doc:mini-app#wxonthemechangefunction-listener)
- [offThemeChange](doc:mini-app#wxoffthemechangefunction-listener)

# wx.onError

## wx.onError(function callback)

Listen for Mini App error events. For example, script errors or API call errors. The event coincides with the callback timing and parameters of App.OnError.

# Parameters

## Function callback

A Callback function for the Mini App error event.

### Parameters

**String error:** Error message, including the error stack.

# wx.offError

## wx.offError(function callback)

Remove listeners for Mini App error events.

# Parameters

## Function callback

Callback function for the Mini App error event. 

### Sample code

```javascript JavaScript
const listener = function (res) { console.log(res) }

wx.onError(listener)
wx.offError(listener) // You should enable the same function object as for the listener.
```

# wx.onThemeChange(function listener)

Listens for the system theme change event.

# Parameters

## Function listener

Callback function for the Mini App theme change event.

## Parameters

## Object response

[block:parameters]
{
  "data": {
    "h-0": "Attribute",
    "h-1": "Valid Value",
    "h-2": "Type",
    "h-3": "Description",
    "0-0": "theme",
    "0-1": "dark: Dark theme  \nlight: Light theme",
    "0-2": "string",
    "0-3": "The current system theme.  \nValid values: `light`, `dark`."
  },
  "cols": 4,
  "rows": 1,
  "align": [
    "left",
    "left",
    "left",
    "left"
  ]
}
[/block]


> 📘 Note
> 
> This event is triggered only if `"darkmode": true` is globally configured.

# wx.offThemeChange(function listener)

Removes listeners for system theme change events.

## Parameters

### Function description

The listener function passed in when `onThemeChange` is called. If this parameter is not passed in, all listener functions will be removed.

### Sample code

```javascript JavaScript
const listener = function (res) { console.log(res) }

wx.onThemeChange(listener)
wx.offThemeChange(listener) // You should enable the same function object as for the listener.
```
