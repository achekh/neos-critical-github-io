---
title: "API"
slug: "api"
excerpt: ""
hidden: false
createdAt: "Tue May 16 2023 08:21:42 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Tue Nov 28 2023 09:54:01 GMT+0000 (Coordinated Universal Time)"
layout: "default"
parent: "Logic layer"
grand_parent: "Guide"
---
# API 
*** 
The Mini App development framework provides a diversity of native APIs for easily calling host app capabilities, such as user information acquisition, local storage, and payment features. For more information, see the [API documentation](doc:basics-api).

Generally, there are the following types of Mini App APIs:

## Event listener APIs

It is agreed that APIs starting with `on` are used to listen whether an event is triggered, such as [wx.onCompassChange](doc:compass-api#wxoncompasschangefunction-callback)

## Sample code

```javascript
wx.onCompassChange(function (res) {
  console.log(res.direction)
})
```

## Sync APIs

It is generally accepted that APIs with the prefix "Sync"—for example, `[wx.setStorageSync]`and `['wx.getSystemInfoSync']` are in sync. There are also some more sync APIs. See the description in the API documentation for further details.

The execution result of a sync API is directly obtained through the returned value of the function, and an exception will be thrown if the execution fails.

### Sample code

```javascript
try {
  wx.setStorageSync('key', 'value')
} catch (e) {
  console.error(e)
}
```

## Async APIs

Most APIs are `async`, such as `wx.request` and `wx.login`. This type of APIs usually accepts a parameter of `Object` type, which supports specifying the following fields as needed to receive the API call result:

### `Object` parameter description

| Parameter | Type     | Description                                                                        |
| :-------- | :------- | :--------------------------------------------------------------------------------- |
| success   | function | Callback function for successful API call                                          |
| fail      | function | Callback function for failed API call                                              |
| complete  | function | Callback function for API call end (executed for both successful and failed calls) |
| Other     | Any      | Other parameters defined by the API                                                |

### Parameters of the callback function

A parameter of `Object` type will be passed in when the `success` , `fail` , or `complete` function is called, which contains the following fields:

| Attribute | Type   | Description                                                                                                                                                   |
| :-------- | :----- | :------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| errMsg    | string | Error message. If the call succeeds, `${apiName}:ok` will be returned.                                                                                        |
| errCode   | number | Error code, which is supported only for certain APIs. For specific descriptions, see the API documentation. If the call succeeds, this parameter will be `0`. |
| Other     | Any    | Other data returned by the API                                                                                                                                |

The execution result of an async API needs to be obtained through the corresponding callback function passed in via the parameter of Object type. Some async APIs also have returned values, which can be used to implement richer features, such as [`[wx.request]`](doc:request).

### Sample code

```javascript
wx.login({
  success(res) {
    console.log(res.code)
  }
})
```
