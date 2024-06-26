---
title: "About Mini Programs"
slug: "about-mini-apps"
excerpt: "Mini Programs enables connection between the users and services."
hidden: true
metadata: 
  image: []
  robots: "index"
createdAt: "Tue Apr 25 2023 10:51:50 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Wed May 03 2023 13:05:26 GMT+0000 (Coordinated Universal Time)"
layout: "default"
parent: "Overview"
grand_parent: "Guide"
---
# About Mini Programs 
Mini Programs enables connection between the users and services.

***

Mini Programs enables connection between the users and services. They are easy to access and share on Super Hub Mini App to deliver excellent user experience.

# Technical Development of a Mini Program

The development of Mini Apps is not a new concept. ​As WebView became increasingly important as an entry to mobile web pages, the Super Hub Mini App developed the JS APIs for this purpose.

Below is an example of Code 1-1 that implements a JS API that calls the native compoenents to view images:

```Text
// Code 1-1
WeixinJSBridge.invoke('imagePreview', {
    current: 'http://inews.gtimg.com/newsapp_bt/0/1693121381/641',
    urls: [ // List of URLs of all images (in an array format)
        'https://img1.gtimg.com/10/1048/104857/10485731_980x1200_0.jpg',
        'https://img1.gtimg.com/10/1048/104857/10485726_980x1200_0.jpg',
        'https://img1.gtimg.com/10/1048/104857/10485729_980x1200_0.jpg'
    ]
}, function(res) {
    console.log(res.err_msg)
})
```

Code 1-1 implements a JS API that calls the Weixin native components to view images. This method is simpler and efficient than additionally introducing a JS image preview component library.

In fact, Weixin never officially exposed such APIs, which were only provided internally for some Tencent services. With the APIs discovered and used by many external developers, they are widely applied in the web pages in Weixin as a standard. At the beginning of 2015, Weixin released a Web development kit called JS-SDK, in which dozens of APIs for such scenarios as taking photos, recording, speech recognition, QR code, map, payment, sharing, and coupons are open to Web developers, allowing them to do what they could not to do before.

Code 1-2 also shows how to view images by calling a native component.

Code 1-2 Call image preview component using JS-SDK

```Text
// code 1-2
wx.previewImage({
  current: 'https://img1.gtimg.com/10/1048/104857/10485726_980x1200_0.jpg',
  urls: [ // List of URLs of all images (in an array format)
    'https://img1.gtimg.com/10/1048/104857/10485731_980x1200_0.jpg',
    'https://img1.gtimg.com/10/1048/104857/10485726_980x1200_0.jpg',
    'https://img1.gtimg.com/10/1048/104857/10485729_980x1200_0.jpg'
  ],
  success: function(res) {
    console.log(res)
  }
})
```

Built on WeixinJSBridge and incorporating some new features, JS-SDK was open to all developers, instead of being only available to internal developers, and became popular among developers quickly. According to the data monitoring result, most mobile web pages shared in Weixin used the APIs supplied with JS-SDK.

JS-SDK gave web developers more capabilities by exposing Weixin APIs. However, users still had an unsatisfactory experience when using mobile web pages. When a user visited a web page, a white screen occurred before the page was displayed on browser. On a mobile device, this problem was more severe due to lower device performance and network speed. To help web developers solve this problem, our team designed an enhanced version of JS-SDK, which had an important feature called "Weixin Web Resource Offline Storage".

The following text comes from an internal document (not made public):

> Weixin Web Resource Offline Storage was a Weixin-based Web acceleration solution for web developers.
>
> With Weixin Web Resource Offline Storage, Web developers could directly load Web resources from Weixin without having to fetch them from servers, thus accelerating the web page loading and optimizing web browsing experience for Weixin users. Under each Official Account, up to 5 MB resources could be cached for all Web Apps.

This design was somewhat similar to HTML5 Application Cache, but eliminated HTML5's some limitations.

In internal trials, Weixin Web Resource Offline Storage could solve some problems, but white screen still occurred in some complicated cases, for example, when a page was loaded with a large number of CSS or JavaScript files. In addition to the white screen, insufficiency of clear action feedback affected the Web user experience. This was mainly reflected in tap delay, and page switching without smooth transitions.

The Weixin Team needed to design a new system that provides a better experience than JS-SDK for all developers on Weixin and allows them to achieve:

- _Fast loading_
- _More powerful capabilities_
- _Native experience_
- _Easy and secure Weixin data exposure_
- _Efficient and simple development_

This is how Mini Program concept came into being.

# Differences Between Mini Program Development and Web Development

Mini Programs are developed in JavaScript mostly. The process is quite similar to Web development, so the transition from Web development to Mini Program development involves a low cost for front-end developers. However, there are some differences between them.

In Web development, rendering threads and scripting threads are mutually exclusive, so long-time script running may make a page unresponsive. In a Mini Program, rendering threads and scripting threads run separately. Web developers can use the DOM APIs exposed by various browsers to perform DOM selection and operation. As mentioned above, the logic layer and rendering layer of a Mini Program are separated from each other. The former runs in JSCore without a full browser object, thus lacking the relevant DOM and BOM APIs. This difference makes it impossible for some libraries familiar to front-end developers, such as jQuery and Zepto, to run in Mini Programs. Meanwhile, JSCore environment is different from NodeJS environment, which means that some NPM packages cannot run in Mini Programs.

Web developers work with IE/Chrome/QQ browsers on PC, and Safari/Chrome browsers as well as various WebViews on iOS or Android systems on mobile devices, while Mini Program developers work with Weixin on iOS, Android, and Weixin DevTools. The differences between the three operating environments are as follows:

Operating Environments of Mini Programs

| Runtime Environment | Logic Layer    | Rendering Layer        |
| :------------------ | :------------- | :--------------------- |
| iOS                 | JavaScriptCore | WKWebView              |
| Android             | V8             | Chromium custom kernel |
| Weixin DevTools     | NWJS           | Chrome WebView         |

When developing web pages, Web developers only need to use browsers with some auxiliary tools or editors. The development of Mini Programs involves applying for Mini Program accounts, installing Weixin DevTools, configuring projects, and so on.

# Using a Mini Program

You can trial your Mini Program by scanning the Mini Program code below with Weixin 6.7.2 or above.
