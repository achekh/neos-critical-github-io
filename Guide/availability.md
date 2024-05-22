---
title: "Availability"
slug: "availability"
excerpt: ""
hidden: true
metadata: 
  image: []
  robots: "index"
createdAt: "Wed May 24 2023 04:03:06 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Fri May 26 2023 09:20:04 GMT+0000 (Coordinated Universal Time)"
---
- Debugging
- Runtime Environment 
- Operation Mechanism

# vConsole

On a real device, if you want to view the log content and additional debugging information output by the `console` API, you need to click the button in the top-right corner to open the menu and select **Enable Debugging**. Then, the Mini App will exit, and after it is reopened, a **vConsole** button will appear in the bottom-right corner. Click **vConsole** to open the log panel.

The vConsole display of the Mini App is as follows:

![](https://files.readme.io/f3aaf6f-WhatsApp_Image_2023-05-24_at_9.54.41_AM.jpeg)

## vConsole instructions

Due to the limitations of the implementation mechanism, the log content printed by calling the `console` API is converted into a `JSON` string and then transferred to the vConsole. Therefore, there are some restrictions on the content displayed in the vConsole:

- Except for `Number`, `String`, `Boolean`, and `null`, other types will be processed and displayed as `Object`, and the object and the `Enumerable` attribute in the prototype chain will be printed.
- `Infinity` and `NaN` will be displayed as `null`.
- Data of `undefined`, `ArrayBuffer`, and `Function` types cannot be displayed.
- Objects with circular references cannot be printed.

```javascript
const a = {}
a.b = a
console.log(a)
```

#### In response to the above problems, the mini app's use of vConsole has been fine-tuned:

```javascript
const circular = {x: {}, c: {}}
circular.x = [{promise: Promise.resolve()}]
circular.a = circular
circular.c.x0 = circular.x[0]
console.log(circular)
// "{a: '<Circular: @>', c: {x0: '<Circular: @.x[0]>'}, x: [{promise: '<Promise>'}]}"
```

#### Note: Avoid printing too complicated or lengthy logs in non-debugging scenarios; otherwise, additional time overheads may be incurred.

# Mini App Runtime Environment

A Mini App can run on three terminals: iOS (iPhone/iPad), Android, and DevTools (for debugging).

The script execution environments of the three terminals and the environments used for rendering non-native components are different:

- On iOS, the logic layer JavaScript code of the Mini App runs in JavaScriptCore, the view layer is rendered by WKWebView, and the environments include iOS 8, 9, and 10.
- On Android, the logic layer JavaScript code of the Mini App runs in X5 JSCore, and the view layer is rendered by [X5](https://x5.tencent.com/tbs/) based on the Mobile Chrome 57 kernel.
- On DevTools, the logic layer JavaScript code of the Mini App runs in [NW.js](https://nwjs.io/), and the view layer is rendered by Chromium 60 WebView.

## Execution limits

For security considerations, dynamic execution of JS code is not supported in Mini Apps; that is:

- Executing JS code with `eval` is not supported.
- Using `new Function` to create functions is not supported.

## Platform differences

Although the environments of the three terminals are very similar, there are still some differences:

- JavaScript syntax and API support are inconsistent: In terms of syntax, you can avoid this by enabling the feature of converting ES6 to ES5 ; in addition, the Mini App base library has built-in necessary polyfills to make up for API differences.
- `WXSS` rendering behaviours are inconsistent: Although most issues can be avoided by enabling style completion, we recommend you check the actual performance of the mini app on iOS and Android respectively.

**DevTools is for debugging only, and the final display is subject to the client.**

## ES6 support

### Client ES6 API support

The Mini App already supports most ES6 APIs as listed below:

1. Tip: `Array.values` is not supported.
2. Tip: `Proxy` is not supported.

| String               | iOS 8         | iOS 9         | iOS 10 | Android |
| :------------------- | :------------ | :------------ | :----- | :------ |
| codePointAt          |               |               |        |         |
| normalize            | Not Supported | Not Supported |        |         |
| includes             |               |               |        |         |
| startsWith           |               |               |        |         |
| endsWith             |               |               |        |         |
| repeat               |               |               |        |         |
| String.fromCodePoint |               |               |        |         |

| Array      | iOS 8         | iOS 9 | iOS 10 | Android       |
| :--------- | :------------ | :---- | :----- | :------------ |
| copyWithin |               |       |        |               |
| find       |               |       |        |               |
| findIndex  |               |       |        |               |
| fill       |               |       |        |               |
| entries    |               |       |        |               |
| keys       |               |       |        |               |
| values     | Not Supported |       |        | Not Supported |
| includes   | Not Supported |       |        |               |
| Array.from |               |       |        |               |
| Array.of   |               |       |        |               |

| Number        | iOS 8 | iOS 9 | iOS 10 | Android |
| :------------ | :---- | :---- | :----- | :------ |
| isFinite      |       |       |        |         |
| isNaN         |       |       |        |         |
| parseInt      |       |       |        |         |
| parseFloat    |       |       |        |         |
| isInteger     |       |       |        |         |
| EPSILON       |       |       |        |         |
| isSafeInteger |       |       |        |         |

| Math   | iOS 8 | iOS 9 | iOS 10 | Android |
| :----- | :---- | :---- | :----- | :------ |
| trunc  |       |       |        |         |
| sign   |       |       |        |         |
| cbrt   |       |       |        |         |
| clz32  |       |       |        |         |
| imul   |       |       |        |         |
| fround |       |       |        |         |
| hypot  |       |       |        |         |
| expm1  |       |       |        |         |
| log1p  |       |       |        |         |
| log10  |       |       |        |         |
| log2   |       |       |        |         |
| sinh   |       |       |        |         |
| cosh   |       |       |        |         |
| tanh   |       |       |        |         |
| asinh  |       |       |        |         |
| acosh  |       |       |        |         |
| atanh  |       |       |        |         |

| Object                   | iOS 8 | iOS 9 | iOS 10 | Android |
| :----------------------- | :---- | :---- | :----- | :------ |
| is                       |       |       |        |         |
| assign                   |       |       |        |         |
| getOwnPropertyDescriptor |       |       |        |         |
| keys                     |       |       |        |         |
| getOwnPropertyNames      |       |       |        |         |
| getOwnPropertySymbols    |       |       |        |         |

| Other   | iOS 8         | iOS 9         | iOS 10 | Android       |
| :------ | :------------ | :------------ | :----- | :------------ |
| Symbol  |               |               |        |               |
| Set     |               |               |        |               |
| Map     |               |               |        |               |
| Proxy   | Not Supported | Not Supported |        | Not Supported |
| Reflect |               |               |        |               |
| Promise |               |               |        |               |

# Operation Mechanism

There are two types of Mini App start: cold start and hot start. If the user has already opened a Mini App and then opens it again within a certain period of time, there is no need to restart the Mini App; instead, the system simply switches the Mini App from the background to the foreground, which is called hot start. If the user opens the Mini App for the first time or opens it again after the Mini App is actively terminated by the host app, the Mini App needs to be reloaded for start, which is called cold start.

## Update mechanism

If a new version is found during a cold start of the Mini App, the code package of the new version will be downloaded asynchronously, and the local package on the client will be used to start the Mini App at the same time. In other words, the new version of the Mini App will not be applied until the next cold start. If you need to apply the latest version immediately, call the `wx.getUpdateManager` API for processing.

## Operating mechanism

- There is no concept of restart for Mini Apps.
- When a Mini App enters the background, the client will maintain its running status for a period of time, which will be actively terminated by the container after a certain period of time (5 minutes currently).
- On iOS, when the client receives two or more system memory alarms within a certain period of time (5 seconds currently), it will actively terminate the Mini App and prompt the user that "This Mini App may have caused the host to respond slowly and thus is terminated". We recommend you make the Mini App use `wx.onMemoryWarning` to listen for memory alarm events and perform memory cleanup when necessary.
