---
title: "Background"
slug: "background"
excerpt: "APIs to manipulate background color and text style."
hidden: false
createdAt: "Tue May 02 2023 10:47:42 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Wed Nov 29 2023 08:28:56 GMT+0000 (Coordinated Universal Time)"
layout: "default"
parent: "UI"
grand_parent: "APIs"
nav_order: 3
---
# Background 
APIs to manipulate background color and text style.

***

- [setBackgroundColor](background#setbackgroundcolor-object-object)
- [setBackgroundTextStyle](background#wxsetbackgroundtextstyle-object-object)

# setBackgroundColor (Object object)

Dynamically sets the background color of the window.

# Parameters

**Object object**

| Attribute | Type | Required | Description |
| :-------- | :--- | :------- | :---------- |
| backgroundColor | String | No | Background color of the window, which must be a hex color value. |
| backgroundColorTop | String | No | Background color of the top of the window, which must be a hex color value and is supported on iOS only. |
| backgroundColorB  \nottom | String | No | Background color of the bottom of the window, which must be a hex color value and is supported on iOS only. |
| success | Function | No | Callback function for a successful API call. |
| fail | Function | No | Callback function for a failed API call. |
| complete | Function | No | Callback function for an API call end (executed for both successful and failed calls). |

### Sample code

```javascript
// JavaScript
wx.setBackgroundColor({
	backgroundColor: '#ffffff', // The background color of the window is white.
})
wx.setBackgroundColor({
  backgroundColorTop: '#ffffff', // The background color of the top of the window is white.
  backgroundColorBottom: '#ffffff', // The background color of the bottom of the window is white.
})
```

# wx.setBackgroundTextStyle (Object object)

Dynamically sets the style of the background font and loading image.

# Parameters

**Object object**

| Attribute | Type     | Required | Description                                                                            |
| :-------- | :------- | :------- | :------------------------------------------------------------------------------------- |
| textStyle | String   | Yes      | Style of the background font and loading image.                                        |
| success   | Function | No       | Callback function for a successful API call.                                           |
| fail      | Function | No       | Callback function for a failed API call.                                               |
| complete  | Function | No       | Callback function for an API call end (executed for both successful and failed calls). |

## Valid values of `object.textStyle`

| Value | Description  |
| :---- | :----------- |
| dark  | Dark style.  |
| light | Light style. |

### Sample code

```javascript
// JavaScript
wx.setBackgroundTextStyle({
	textStyle: 'dark' // The style of the background font and loading image is `dark`.
})
```
