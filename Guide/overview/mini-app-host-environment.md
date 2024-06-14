---
title: "Mini Program Host Environment"
slug: "mini-app-host-environment"
excerpt: "This chapter explains the concept of Mini Program host environment."
hidden: true
metadata: 
  robots: "index"
createdAt: "Thu Apr 27 2023 07:35:09 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Wed May 03 2023 10:12:02 GMT+0000 (Coordinated Universal Time)"
layout: "default"
parent: "Overview"
grand_parent: "Guide"
---
# Mini Program Host Environment 
*** 
The environment provided by the Mini app for the Mini Program is called host environment. With the capabilities provided by the host environment, the Mini Program can deliver many features that are not available in other web pages.

In the previous chapter, we explained the different types of files in the Mini Program. Now, let's see how these files work together in the example of QuickStart.

## Rendering Layer and Logic Layer

Firstly, let's have a brief understanding of the runtime environment of the Mini Program, which is divided into a render layer and a logic layer. WXML templates and WXSS styles are used in the render layer and JS scripts in the logic layer.

These two layers are managed via two threads: the render layer renders its interfaces using WebView threads, while the logic layer runs the JS scripts with JsCore threads. As more than one interface exists in the Mini Program, there are multiple WebView threads in the render layer. The communication between the WebView threads and JsCore threads as well as the network requests sent from the logic layer are transferred via the Mini app (hereinafter also referred to as Native). The communication model of the Mini Program is shown below.

![](https://files.readme.io/8402e02-small-wxapp-navigate-1.translated.jpg)

For details, see [Mini Program Framework.](<>)

## Programs and Pages

The Mini app downloads the code package of the Mini Program to the local device before opening it. This allows you to get all the page paths of the Mini Program from the `pages` field of `app.json:`

```Text code
{
  "pages":[
    "pages/index/index",
    "pages/logs/logs"
  ]
}
```

The configuration defines two pages in the QuickStart project, which are located respectively in the `pages/index/index` and `pages/logs/logs` directories. The first page specified in the `pages` field is the homepage of the Mini Program (i.e., the first page you see when you open the Mini Program).

The Mini app loads the code of the homepage and render it via the underlying mechanism of the Mini Program.

When the Mini Program is launched, the `onLaunch` callback of the `App` instance defined in `app.js `is executed:

```Text code
App({
  onLaunch: function () {
    //Triggered when the Mini Program is launched
  }
})
```

There is only one App instance in the Mini Program, which is shared across all pages. For more event callbacks, see Registering Mini Program.

Now let's take a look at how the page of the Mini Program is written.

Four types of files can be found in the `pages/logs/logs` directory. The Mini app first generates an interface based on the `logs.json` configuration file in which the top color and text can be defined. The app then loads the `WXML` structure and `WXSS `style of the page, and finally the logs.js file. The content of the `logs.js `file looks like this:

```Text code
Page({
  data: { // Data used for page rendering
    logs: []
  },
  onLoad: function () {
    // Executed when the page is rendered
  }
})
```

`Page `is a page constructor that generates a page. When the page is generated, the Mini Program framework renders the final structure using `data `and`index.wxml,`so that the Mini Program appears as it is now.

After the interface is rendered, the page instance receives an `onLoad `callback, where you can process your logic.

For more information on the `Page `constructor, see [Registering Page.](<>)

## Components

With the wide range of basic components provided by the Mini Program, developers can build their own Mini Programs by combining various components.

Like` div`,` p` and other tags in `HTML`, in the Mini Program, you just need to provide the tag name of a component in `WXML` to display the component on the interface. For example, if you want to display the map on the interface, then write like this:

```Text code
<map></map>
```

When using the component, you can also pass values to it via properties to display the component differently. For example, if you want the center latitude and longitude of the map to be those of Guangzhou at the very beginning, you need to declare the map's longitude (center longitude) and latitude (center latitude) properties:

```Text code
<map longitude="Longitude of Guangzhou" latitude="Latitude of Guangzhou"></map>
```

The internal behavior of the component can also be perceived by developers as an event. For example, if a user taps a marker on the map, you can write a `markertap` function in the `js`:

```Text code
<map bindmarkertap="markertap" longitude="Longitude of Guangzhou" latitude="Latitude of Guangzhou"></map>
```

You can also control the external style of the component via `style` or `class `to fit the width, height and other properties of your interface.

See [Mini Program Components](<>) for details.

## API

To make it easy for developers to call the capabilities provided by Mini app, such as access to user information, local storage and WeChat Pay, the Mini Program provides a wide range of APIs.

To obtain user's geographical location, then write like this:

```Text code
wx.getLocation({
  type: 'wgs84',
  success: (res) => {
    var latitude = res.latitude // Latitude
    var longitude = res.longitude // Longitude
  }
})
```

To use the "Scan" feature, then write like this:

```Text code
wx.scanCode({
  success: (res) => {
    console.log(res)
  }
})
```

Most API callbacks are asynchronous, so you need to take care of the asynchronization of your code logic.

See [Mini Program APIs](<>) for details.

In this chapter, you have got some basic understanding of how the Mini Program works. After developing a Mini Program, you need to release it. 

In the next chapter, you will learn the preparations before release.
