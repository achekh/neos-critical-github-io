---
title: "Mini Program Runtime"
slug: "mini-app-runtime-environment"
excerpt: "This section explains the concept of Mini Program Runtime."
hidden: true
metadata: 
  robots: "index"
createdAt: "Mon May 01 2023 10:25:55 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Wed May 03 2023 10:16:35 GMT+0000 (Coordinated Universal Time)"
layout: "default"
parent: "Guide"
has_children: true
---
# Runtime Environment of Mini Programs

The Mini Program runs on 3 platforms: iOS (iPhone/iPad), Android, and the Mini App DevTools used for debugging.

The script runtime environments and environments for rendering non-native components of the three platforms are different:

- On iOS, the javascript code of the Mini Program logic layer runs in JavaScriptCore, and its view layer is rendered by WKWebView. The runtime environments are iOS8, iOS9 and iOS10.
- On Android,
  - for an older version, the javascript code of the Mini Program logic layer is running in the X5 JSCore, and its view layer is rendered by X5 based on the Mobile Chrome 57 kernel.
  - for a newer version, the javascript code of the Mini Program logic layer is running in the V8, and its view layer is rendered by self-developed XWeb engine based on the Mobile Chrome 67 kernel.
- On the development tool, the javascript code of the Mini Program logic layer is running in NW.js, and its view layer is rendered by the Chromium 60 Webview.

## Platform Differences

Even though the environments on the 3 platforms are very similar, there is a slight difference as well, which is given below:

- JavaScript syntax is different from what API supports: For syntax, developers can enable `ES6` to `ES5 `conversion to avoid this issue (Details); in addition, the Mini Program base library has a necessary Polyfill built in to compensate for API differences (Details).
- WXSS(<https://developers.weixin.qq.com/miniprogram/dev/devtools/codecompile.html#样式补全>). It is still recommended that developers check the actual performance of the Mini Program separately on iOS and Android.

**The Mini App DevTools is for debugging only, and the final performance is subject to clients.clients. **
