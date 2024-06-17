---
title: "Logic layer"
slug: "framework"
excerpt: ""
hidden: false
metadata: 
  image: []
  robots: "index"
createdAt: "Fri May 12 2023 06:57:36 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Wed Jun 07 2023 03:02:45 GMT+0000 (Coordinated Universal Time)"
layout: "default"
parent: "Guide"
has_children: true
nav_order: 6
---
# Logic layer 
*** 
The Mini App framework allows you to develop native-grade services in host apps in a way that is as simple and efficient as possible.  
The framework provides its own view layer description languages `WXML` and `WXSS` , a logic layer framework based on `JavaScript` , as well as data transfer and event systems between the view layer and logic layer. This helps you focus more on data and logic.

## Response data binding

At the core of the framework is the response data binding system.

The whole Mini App framework system is divided into two parts: View layer (View) and logic layer (App Service).

Below is a simple example:

```html
<!-- WXML -->
<!-- This is our View -->
{% raw %}
<view>Hello {{name}}!</view>
<button bindtap="changeName">Click me!</button>
{% endraw %}
```

```javascript
// This is our App Service.
// This is our data.
const helloData = {
	name: 'World'
}
// Register a Page.
Page({
  data: helloData,
  changeName(e) {
    // sent data change to view
    this.setData({
      name: 'NEOM'
		})
  }
})
```

- You bind the `name` in the logic layer data and the `name` in the view layer through the framework, so `Hello World!` will be displayed when the page is opened.
- When the button is clicked, the view layer will send the `changeName` event to the logic layer, and the logic layer will find and execute the corresponding event handler.
- After the callback function is triggered, the logic layer will execute the operation of `setData` to change name in data from `World` to `NEOM` since the data and the view layer have been bound. Therefore, the view layer will automatically change to `Hello NEOM`.

## Page management

The framework manages the page routing of the entire **Mini App** to achieve a seamless switch between pages and give pages a complete lifecycle. All you need to do is to register the data, methods, and lifecycle functions of pages into the framework, and all other complex operations will be handled by the framework.

## Basic components

The framework provides a set of basic components, which come with Super Hub styles and special logic. You can create a powerful **Super Hub Mini App** by combining such components. For more information, check the [components](../components) guide.

## Rich APIs

The framework provides a diversity of native host app APIs for easily calling host app capabilities, such as user information acquisition, local storage, and payment features. For More information, check the [APIs](../APIs/basics-api) guide.
