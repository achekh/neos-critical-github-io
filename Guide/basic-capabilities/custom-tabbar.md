---
title: "Custom tabBar"
slug: "custom-tabbar-copy"
excerpt: "This section explains the concept of custom tabBar."
hidden: false
createdAt: "Mon May 08 2023 06:17:05 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Tue Nov 28 2023 10:31:55 GMT+0000 (Coordinated Universal Time)"
layout: "default"
parent: "Basic Capabilities"
grand_parent: "Guide"
nav_order: 4
---
# Custom tabBar 
This section explains the concept of custom tabBar.
*** 
Custom tabBar allows developers to set tabBar styles and achieve greater personalization with flexibility.

In custom tabBar mode:

- In order to ensure compatibility with older versions and to identify the pages that are tab pages, the relevant tabBar configuration items must be completely declared. However, these fields cannot be used to render custom tabBars.
- Developers must provide a custom component to render the tabBar, and all tabBar styles must be rendered via the custom component. To ensure a higher tabBar level, we recommend using cover-view and cover-image components which are fixed at the bottom of the page to render styles.
- APIs related to tabBar styles such as wx.setTabBarItem will be deactivated.
- The custom tabBar component instances vary with different tab pages. You can use the `getTabBar` API under a custom component to get the custom tabBar component instance of the current page.

> 📘 Note
> 
> To put a tab in the selected status on the current page, use the getTabBar API to get the component instance and call setData to update the selected status. See the code sample at the bottom for details.

## How to Use

Perform the following steps to use the custom tabBar:

## 1. Configure the information

- Specify the `custom` field of the `tabBar` item in `app.json` and set the other configurations related to `tabBar`.
- The `usingComponents` item must be declared in json of all tab pages. You can also enable this option globally in `app.json`.

### Example:

```javascript
// code
{
  "tabBar": {
    "custom": true,
    "color": "#000000",
    "selectedColor": "#000000",
    "backgroundColor": "#000000",
    "list": [{
      "pagePath": "page/component/index",
      "text": "Component"
    }, {
      "pagePath": "page/API/index",
      "text": "API"
    }]
  },
  "usingComponents": {}
}
```

## 2. Add tabBar code files

Add the entry files in the code root directory:

```Text
// code
custom-tab-bar/index.js
custom-tab-bar/index.json
custom-tab-bar/index.wxml
custom-tab-bar/index.wxss
```

## 3. Write tabBar code

You can write the code using a custom component to render tabBar. In addition, the getTabBar API is added to the custom component to get the custom tabBar component instance of the current page.
