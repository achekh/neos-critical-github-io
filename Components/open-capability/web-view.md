---
title: "Web-view"
slug: "web-view"
excerpt: "A container that displays webpages."
hidden: false
metadata: 
  image: []
  robots: "index"
createdAt: "Thu Apr 13 2023 07:33:31 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Tue Jun 20 2023 05:34:04 GMT+0000 (Coordinated Universal Time)"
layout: "default"
parent: "Open capability"
grand_parent: "Components"
---
# Web-view 
*** 
The `web-view` component is a container that displays webpages. It will automatically cover the entire Mini App UI.

| Attribute   | Type          | Description                                                                                                                                                                                                                                                                |
| :---------- | :------------ | :------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| src         | String        | The webview link redirecting to a webpage. You need to configure the corresponding business domain name in the Super Hub Mini App Platform.                                                                                                                                |
| bindmessage | Event Handler | The message triggered and received at a certain time point (returning to a mini app page; terminating or sharing a component) when the webpage sends `postMessage` to the mini app: `event.detail = { data }` (here, `data` is an array of multiple `postMessage` values.) |
| bindload    | Event Handler | The event triggered when the webpage is loaded successfully: `event.detail = {src}`                                                                                                                                                                                        |
| binderror   | Event Handler | This event is triggered when a page load fails to be loaded. `event.detail = {src}`.                                                                                                                                                                                       |

### Sample code

```Text WXML
<!-- wxml -->
<web-view src="https://fmp.tmf.stage.neuxnet.com:30001/#/login"></web-view>
```

### Relevant APIs (1)

On a `<web-view>` webpage, you can use APIs provided by JSSDK to return to a mini app page. The following APIs are supported:

| Interface name              | Description                                                                                                                                                  |
| :-------------------------- | :----------------------------------------------------------------------------------------------------------------------------------------------------------- |
| wx.miniProgram.navigateTo   | Parameters are consistent with the Mini Program interface.                                                                                                   |
| wx.miniProgram.navigateBack | Parameters are consistent with the Mini Program interface.                                                                                                   |
| wx.miniProgram.switchTab    | Parameters are consistent with the Mini Program interface.                                                                                                   |
| wx.miniProgram.reLaunch     | Parameters are consistent with the Mini Program interface.                                                                                                   |
| wx.miniProgram.redirectTo   | Parameters are consistent with the Mini Program interface.                                                                                                   |
| wx.miniProgram.postMessage  | Sends a message to the Mini Programs that triggers the component's message event at a specific time (Mini Programs retreat, component destruction, sharing). |
| wx.miniProgram.getEnv       | Get the current environment.                                                                                                                                 |

### Sample Code

```javascript
// javascript
// <script type="text/javascript" src="https://res.wx.tonomus.com/open/js/jssdk-1.3.2.js"></script>

// javascript
wx.miniProgram.navigateTo({url: '/path/to/page'})
wx.miniProgram.postMessage({ data: 'foo' })
wx.miniProgram.postMessage({ data: {foo: 'bar'} })
wx.miniProgram.getEnv(function(res) { console.log(res.miniprogram) })
```

### Relevant APIs (2)

When sharing a webpage, the user can get the URL of the current `<web-view>`, i.e., the webViewUrl parameter is returned in the `onShareAppMessage` callback.

### Sample Code

```javascript JavaScript
Page({
  onShareAppMessage(options) {
    console.log(options.webViewUrl)
  }
})
```

### Relevant APIs (3)

On the webpage, you can determine whether a mini app environment exists through `window.__wxjs_environment`. We recommend you use it in WeixinJSBridgeReady . You can also use the `getEnv` API provided by the JSSDK.

### Sample code

```javascript JavaScript
function ready() {
	console.log(window.__wxjs_environment === 'miniprogram') // true
}
if (!window.WeixinJSBridge || !WeixinJSBridge.invoke) {
	document.addEventListener('WeixinJSBridgeReady', ready, false)
} else {
	ready()
}
// Or
wx.miniProgram.getEnv(function(res) {
	console.log(res.miniprogram) // true
})
```

> 📘 Notes
> 
> - `web-view` doesn't support media APIs.
> - You can determine whether `web-view` is in the mini app environment through the `miniProgram` field in `userAgent` header.
> - For webpages embedded through `iframe`, you need to add the domain names to the domain name allowlist.
> - On Super Hub Mini App Studio, you can open `<web-view>` debugging by right-clicking and selecting Debugging.
> - Each page can have only one `<web-view>`, which automatically covers the full page and other components.
> - `<web-view>` can communicate with the mini app only through APIs provided by the JSSDK.
