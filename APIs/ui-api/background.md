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
---
# Background 
*** 
- [setBackgroundColor](doc:background#setbackgroundcolor-object-object)
- [setBackgroundTextStyle](doc:background#wxsetbackgroundtextstyle-object-object)

# setBackgroundColor (Object object)

Dynamically sets the background color of the window.

# Parameters

**Object object**

[block:parameters]
{
  "data": {
    "h-0": "Attribute",
    "h-1": "Type",
    "h-2": "Required",
    "h-3": "Description",
    "0-0": "backgroundColor",
    "0-1": "String",
    "0-2": "No",
    "0-3": "Background color of the window, which must be a hex color value.",
    "1-0": "backgroundColorTop",
    "1-1": "String",
    "1-2": "No",
    "1-3": "Background color of the top of the window, which must be a hex color value and is supported on iOS only.",
    "2-0": "backgroundColorB  \nottom",
    "2-1": "String",
    "2-2": "No",
    "2-3": "Background color of the bottom of the window, which must be a hex color value and is supported on iOS only.",
    "3-0": "success",
    "3-1": "Function",
    "3-2": "No",
    "3-3": "Callback function for a successful API call.",
    "4-0": "fail",
    "4-1": "Function",
    "4-2": "No",
    "4-3": "Callback function for a failed API call.",
    "5-0": "complete",
    "5-1": "Function",
    "5-2": "No",
    "5-3": "Callback function for an API call end (executed for both successful and failed calls)."
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


### Sample code

```javascript JavaScript
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

```javascript JavaScript
wx.setBackgroundTextStyle({
	textStyle: 'dark' // The style of the background font and loading image is `dark`.
})
```
