---
title: "Logic Layer"
slug: "logic-layer"
excerpt: "This section explains the concept of Logic layer in Mini Program framework."
hidden: true
metadata: 
  robots: "index"
createdAt: "Mon May 01 2023 09:05:04 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Wed May 03 2023 10:15:27 GMT+0000 (Coordinated Universal Time)"
layout: "default"
parent: "Mini Program Framework"
grand_parent: "Guide"
---
# Logic Layer 
*** 
In Logic layer, the code examples, variables, and functions declared in the JavaScript file are valid only in the file. Variables and functions with the same names can be declared in different files without affecting each other.

The global application instance can be obtained via the global function getApp. To obtain the global data, you can set App(). 

For example:

## Registering a Mini Program Account

For each Mini Program, a Mini Program instance needs to be registered by calling the App method via `app.js`, to link the lifecycle callback function, error listening function, page not found listening function, and others.

For specific definitions and usage of the parameters, refer to App Reference Documents.

```Text
// code
//app.js
App({
  onLaunch (options) {
    // Do something initial when launch.
  },
  onShow (options) {
    // Do something when show.
  },
  onHide () {
    // Do something when hide.
  },
  onError (msg) {
    console.log(msg)
  },
  globalData: 'I am global data'
})
```

A Mini Program has only one app instance, which is shared to all pages. Developers can obtain the globally unique app instance by using the `getApp` method, and then obtain data in the app or call a function registered with `App` by the developers.

```Text
// code
// xxx.js
const appInstance = getApp()
console.log(appInstance.globalData) // I am global data
```

## Registering a Page

For each page of a Mini Program, a page instance needs to be registered by calling the `Page` method via the `js` file corresponding to the page, to specify the initial data of the page, the lifecycle callback function, the event processing function, and the like of the page.

For specific definitions and usage of the parameters, refer to Page Reference Documents.

```Text
// code
// index.js
Page({
  data: {
    text: "This is page data."
  },
  onLoad: function(options) {
    // Do some initialize when page load.
  },
  onReady: function() {
    // Do something when page ready.
  },
  onShow: function() {
    // Do something when page show.
  },
  onHide: function() {
    // Do something when page hide.
  },
  onUnload: function() {
    // Do something when page close.
  },
  onPullDownRefresh: function() {
    // Do something when pull down.
  },
  onReachBottom: function() {
    // Do something when page reach bottom.
  },
  onShareAppMessage: function () {
    // return custom share data when user share.
  },
  onPageScroll: function() {
    // Do something when page scroll
  },
  onResize: function() {
    // Do something when page resize
  },
  onTabItemTap(item) {
    console.log(item.index)
    console.log(item.pagePath)
    console.log(item.text)
  },
  // Event handler.
  viewTap: function() {
    this.setData({
      text: 'Set some data for updating view.'
    }, function() {
      // this is setData callback
    })
  },
  customData: {
    hi: 'MINA'
  }
})
```

In addition to `Page`, as an advanced usage, `Component` can also be used to create a page in the same way as a custom component. In this case, you can use features of custom components, such as `behaviors`.

For details, see `Component` Constructor.

## Lifecycle

**You don't need to fully understand the following content right away, but it will help in the future. **

The following figure describes the lifecycle of a `Page` instance.

![](https://files.readme.io/1218b0b-10.png)

## Page Routing

The framework manages all the routes to pages of a Mini Program.

### Page Stack

The framework maintains all the existing pages via stacks. When a route is switched, the page stack reacts as follows:

| Routing            | Reaction on the Page Stack                                                                     |
| :----------------- | :--------------------------------------------------------------------------------------------- |
| Initialization     | The new page is pushed onto the stack.                                                         |
| Opening a new page | The new page is pushed onto the stack.                                                         |
| Page redirection   | The current page is popped out of the stack, and the new page is pushed onto the stack.        |
| Page return        | Pages are successively popped out of the stack until the destination return page is displayed. |
| Tab switching      | All the pages are popped out of the stack, and only the new tab page is retained.              |
| Reloading          | All the pages are popped out of the stack, and only the new page is retained.                  |

Developers can obtain the current page stack by using the `getCurrentPages()` function.

### Routing

The following shows how page routing is triggered and the lifecycle functions for pages.

[block:parameters]
{
  "data": {
    "h-0": "Routing",
    "h-1": "Trigger Condition",
    "h-2": "Source Page",
    "h-3": "Routed-To Page",
    "0-0": "Initialization",
    "0-1": "A page of the Mini Program is opened for the first time.",
    "0-2": "",
    "0-3": "onLoad, onShow",
    "1-0": "Opening a new page",
    "1-1": "The API wx.navigateTo is called.  \nThe component `<navigator open-type=\"navigateTo\"/>` is used.",
    "1-2": "onHide",
    "1-3": "onLoad, onShow",
    "2-0": "Page redirection",
    "2-1": "The API wx.redirectTo is called.  \nThe component `<navigator open-type=\"redirectTo\"/>` is used.",
    "2-2": "onUnload",
    "2-3": "onLoad, onShow",
    "3-0": "Page return",
    "3-1": "The API wx.navigateBack is called.  \nThe component `<navigator open-type=\"navigateBack\">` is used.  \nThe user taps the return button on the top left.",
    "3-2": "onUnload",
    "3-3": "onShow",
    "4-0": "Tab switching",
    "4-1": "The API wx.switchTab is called.  \nThe component `<navigator open-type=\"switchTab\"/>` is used.  \nThe user switches between tabs.",
    "4-2": "",
    "4-3": "For details, refer to the following table.",
    "5-0": "Restart",
    "5-1": "The API wx.reLaunch is called.  \nThe component `<navigator open-type=\"reLaunch\"/>` is used.",
    "5-2": "onUnload",
    "5-3": "onLoad, onShow"
  },
  "cols": 4,
  "rows": 6,
  "align": [
    "left",
    "left",
    "left",
    "left"
  ]
}
[/block]


Lifecycle functions corresponding to tab switching (in the following example, pages A and B are Tabbar pages, page C is obtained after page A is opened, and page D is obtained after page C is opened):

| Current Page                   | Routed-To Page   | Triggered Lifecycle Function (In Order)            |
| :----------------------------- | :--------------- | :------------------------------------------------- |
| A                              | A                | Nothing happend                                    |
| A                              | B                | A.onHide(), B.onLoad(), B.onShow()                 |
| A                              | B (Opened again) | A.onHide(), B.onShow()                             |
| C                              | A                | C.onUnload(), A.onShow()                           |
| C                              | B                | C.onUnload(), B.onLoad(), B.onShow()               |
| D                              | B                | D.onUnload(), C.onUnload(), B.onLoad(), B.onShow() |
| D (Entered due to redirection) | A                | D.onUnload(), A.onLoad(), A.onShow()               |
| D (Entered due to redirection) | B                | D.onUnload(), B.onLoad(), B.onShow()               |

> 👍 Tips
> 
> - `navigateTo` and `redirectTo` can be used to open non-tabBar pages only.
> - `switchTab` can be used to open tabBar pages only.
> - `reLaunch` can be used to open any pages.
> - The tabBar on the bottom of a page is determined by the page. In other words, tabBar is displayed on the bottom of all pages defined as tabBar.
> - Parameters used to call page routing can be obtained via `onLoad` in the destination page.

## Modularization

Some common codes can be extracted to create an independent js file as a module. APIs for the module can be exposed only via `module.exports` or `exports.`

> 📘 Note
> 
> - `exports` is a reference to `module.exports`. Therefore, a random modification to the point of exports in the module may cause an unknown error. Developers are advised to expose module APIs via `module.exports` if they do not know the relationship between them.
> - Currently, `node_modules` cannot be directly passed into Mini Programs. To use `node_modules`, developers are advised to copy relevant code to the directory of the Mini Program or use the npm feature supported by Mini Programs.

```Text
// code
// common.js
function sayHello(name) {
  console.log(`Hello ${name} !`)
}
function sayGoodbye(name) {
  console.log(`Goodbye ${name} !`)
}

module.exports.sayHello = sayHello
exports.sayGoodbye = sayGoodbye
```

To pass common code into files that need to access these modules, use `require`.

```Text
// code
var common = require('common.js')
Page({
  helloMINA: function() {
    common.sayHello('MINA')
  },
  goodbyeMINA: function() {
    common.sayGoodbye('MINA')
  }
})
```

### File Scope

Variables and functions declared in the JavaScript file are valid only in the file. Variables and functions with the same names can be declared in different files without affecting each other.

The global application instance can be obtained via the global function getApp. To obtain the global data, you can set App(). 

For example:

```Text
// code
//app.js
App({
  globalData: 1
})
```

```Text
// code
// a.js
// The localValue can only be used in file a.js.
var localValue = 'a'
// Get the app instance.
var app = getApp()
// Get the global data and change it.
app.globalData++
```

```Text
// code
// b.js
// You can redefine localValue in file b.js, without interference with the localValue in a.js.
var localValue = 'b'
// If a.js is run before b.js, now the globalData should be 2.
console.log(getApp().globalData)
```

## API

Mini Program development framework to provide rich micro-channel native API, you can easily tune up WeChat provides capabilities, such as access to user information, local storage, payment functions. Please refer to API file.

Usually, in Mini Programs API There are several types:

### Event monitor API

We made a pact to `on` Initial API Used to listen if an event is triggered, such as:wx.onSocketOpen，wx.onCompassChange Wait.

this kind API Accepts a callback function as a parameter that is called when an event is triggered and passes in the relevant data as parameters.

**Code examples**

```Text
// code
wx.onCompassChange(function (res) {
  console.log(res.direction)
})
```

### synchronization API

We made a pact to `Sync` Ending API It's all in sync. API， Such as [wx.setStorageSync](<>) ，[wx.getSystemInfoSync](<>) Wait. In addition, there are some other synchronization API, such as [wx.createWorker](<>) ，，[wx.getBackgroundAudioManager](<>) For details, see API Instructions in the documentation.

synchronization API Can be obtained directly from the return value of the function, and an exception can be thrown if the execution goes wrong.

Code examples:

```Text
// code
try {
  wx.setStorageSync('key', 'value')
} catch (e) {
  console.error(e)
}
```

### asynchronous API

Majority pf the APIs are asynchronous such as request .login Wait, etc. This kind API Interfaces usually accept a `Object` type, which supports by specifying the following fields on demand to receive interface call results.

### Object Parameter specification

| Parameter name | type     | Required | Introductions                                                                                           |
| :------------- | :------- | :------- | :------------------------------------------------------------------------------------------------------ |
| success        | function | no       | Interface calls the successful callback function.                                                       |
| fail           | function | no       | Interface calls failed callback functions.                                                              |
| complete       | function | no       | Callback function at the end of an interface call (both successful and unsuccessful calls are executed) |
| Other          | Any      |          | Additional parameters defined by the interface.                                                         |

### Parameters to the callback function

`success`，`fail`，`complete` When the function is called, it passes in a `Object` type parameter with the following fields:

| attribute | type   | Introductions                                                                                                      |
| :-------- | :----- | :----------------------------------------------------------------------------------------------------------------- |
| errMsg    | string | Error message if the call returns successfully ${apiName}:ok                                                       |
| errCode   | number | Error code, partial only API Support, please refer to the corresponding meaning API Documentation, if successful 0 |
| Other     | Any    | Interface to return additional data.                                                                               |

In asynchronous API, the need for the adoption of Object gets the corresponding callback function passed in an argument of type.  
In Partially asynchronous APIs, there are also return values that can be used to implement richer functionality, such as [wx.request](<>)，[wx.connectSocket](<>) wait.

**Code examples**

```Text
// code
wx.login({
  success(res) {
    console.log(res.code)
  }
})
```

## asynchronous API return Promise

> 📘 Note
> 
> - In partial interfaces such as `downloadFile`, `request`, `uploadFile`, `connectSocket`, `createCamera`, the game itself has a return value, that requires developer self-encapsulation.
> - When there are no callback parameters, the asynchronous interface returns promise. If the function call fails to enter fail Logic, developers can use an error prompt `Uncaught (in promise)`, to capture.
> - wx.onUnhandledRejection can listen to unprocessed Promise Reject event.

**Code examples**

```Text
// code
// callback Formal invocation
wx.chooseImage({
  success(res) {
    console.log('nothing:', nothing)
  }
})

// promise Formal invocation
wx.chooseImage().then(nothing => console.log('nothing: ', nothing))
```

## Cloud Development API

While accessing and using Mini AppCloud Development, you can use the cloud development API in the Mini Program directly to all the server-side[Cloud function]\.([https://developers.WeChat.qq.with/miniprogram/dev/wxcloud/guide/functions.html#Cloudfunction](https://developers.WeChat.qq.with/miniprogram/dev/wxcloud/guide/functions.html#Cloud)

**Code examples**

```Text
// code
wx.cloud.callFunction({
  // Cloud function name
  name: 'cloudFunc',
  // Parameters to the cloud function
  data: {
    a: 1,
    b: 2,
  },
  success: function(res) {
    console.log(res.result) // Example
  },
  fail: console.error
})

// In addition, cloud functions also support promise calls
```
