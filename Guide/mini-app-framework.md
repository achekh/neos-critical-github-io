---
title: "Mini Program Framework"
slug: "mini-app-framework"
excerpt: "This section explains the concept of Mini Program framework."
hidden: true
metadata: 
  robots: "index"
createdAt: "Mon May 01 2023 09:04:59 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Wed May 03 2023 10:15:03 GMT+0000 (Coordinated Universal Time)"
layout: "default"
parent: "Guide"
has_children: true
nav_exclude: true
---
# Mini Program Framework 
*** 
# Framework

The Mini Program development framework is designed to allow developers to develop services with a native app experience in Mini App in the simplest and efficient way.

The Mini Program framework system includes [Logic Layer](<>) (App Service) and [View Layer](<>) (View). The Mini Program provides its own view layer description languages in WXML and WXSS, and a logic layer framework based on JavaScript. It also defines data transfer and event system between the view layer and the logic layer, allowing developers to focus on data and logic.

## Reactive Data Binding

The reactive data binding system is the core of the framework. It provides an extremely simple way to ensure the synchronization of data and views. To modify data, you simply need to modify the data on the logic layer and it will be updated in the view layer.

Here is a simple example:

[Preview with Developer Tool](<>)

```xml
{% raw %}
<!-- This is our View -->
<view> Hello {{name}}! </view>
<button bindtap="changeName"> Click me! </button>
{% endraw %}
```

```javascript
// code
// This is our App Service.
// This is our data.
var helloData = {
  name: 'Weixin'
}

// Register a Page.
Page({
  data: helloData,
  changeName: function(e) {
    // sent data change to view
    this.setData({
      name: 'MINA'
    })
  }
})
```

- The developer uses the framework to bind `name` in the logic layer data to `name` in the view layer, so `Hello Weixin!` displays once the page opens.
- When you click the button, the view layer sends `changeName `events to the logic layer, which finds and executes the corresponding event handler.
- After the callback function is triggered, the logic layer executes `setData` to change the `name` in `data` from` Mini App` to` MINA`. Since the data is bound to the view layer, Hello MINA! is automatically applied to the view layer.

## Page Management

The framework manages the page routing of the entire Mini Program, which enables seamless switching between pages and gives the pages a complete lifecycle. The developer only needs to register the data, methods, and lifecycle functions of the page to the framework. All other complex operations are handled by the framework.

## Basic Components

The framework provides a set of basic components that come with Mini App styles and special logic. Developers can create powerful **Mini App Mini Programs** by combined use of these components.

## Wide Range of APIs

The framework features a wide range of Mini App native APIs that can easily call the capabilities provided by Mini App, such as access to user information, local storage, and payment.
