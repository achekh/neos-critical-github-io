---
title: "Camera"
slug: "camera"
excerpt: "Native camera component."
hidden: false
metadata: 
  image: []
  robots: "index"
createdAt: "Tue Apr 11 2023 09:33:07 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Fri Jul 14 2023 11:09:31 GMT+0000 (Coordinated Universal Time)"
layout: "default"
parent: "Media components"
grand_parent: "Components"
---
# Camera 
Native camera component.
*** 
This component is native, so you should keep in mind relevant limits when using it.

The user should 'authorize' `scope.camera`.

[block:parameters]
{
  "data": {
    "h-0": "Attribute",
    "h-1": "Type",
    "h-2": "Default Value",
    "h-3": "Required",
    "h-4": "Description",
    "0-0": "mode",
    "0-1": "String",
    "0-2": "normal",
    "0-3": "No",
    "0-4": "Valid values: `normal`, `scanCode`.",
    "1-0": "device-position",
    "1-1": "String",
    "1-2": "back",
    "1-3": "No",
    "1-4": "Valid values: `front`, `back`.",
    "2-0": "flash",
    "2-1": "String",
    "2-2": "car",
    "2-3": "No",
    "2-4": "Valid values: `auto`, `on`, `off`.",
    "3-0": "bindstop",
    "3-1": "Event Handler",
    "3-2": "",
    "3-3": "No",
    "3-4": "Triggered when the camera is abnormally terminated, for example, it is switched to  \nthe background.",
    "4-0": "binderror",
    "4-1": "Event Handler",
    "4-2": "",
    "4-3": "No",
    "4-4": "Triggered if the user hasn't granted the camera access.",
    "5-0": "bindscancode",
    "5-1": "Event Handler",
    "5-2": "",
    "5-3": "No",
    "5-4": "Triggered when the scan is successful, which takes effect only when mode is `sca  \nnCode`."
  },
  "cols": 5,
  "rows": 6,
  "align": [
    "left",
    "left",
    "left",
    "left",
    "left"
  ]
}
[/block]


### Mode values:

| Value    | Description    |
| :------- | :------------- |
| normal   | Camera mode    |
| scanCode | Scan code mode |

### Device-position values:

| Value | Description  |
| :---- | :----------- |
| front | Front camera |
| back  | Back camera  |

### Flash valid values:

| Value | Description |
| :---- | :---------- |
| auto  | Automatic   |
| on    | Open        |
| off   | Stop        |

> 📘 Notes
> 
> - Only one camera component is inserted on the same page.

### Sample code

```javascript
// javascript
Page({
  takePhoto() {
    const ctx = wx.createCameraContext()
    ctx.takePhoto({
      quality: 'high',
      success: (res) => {
        this.setData({
        	src: res.tempImagePath
    		})
  		}
  	})
  },
  error(e) {
  	console.log(e.detail)
  }
})

```
```xml
<!--WXML-->
{% raw %}
<camera
  device-position="back"
  flash="off"
  binderror="error"
  style="width: 100%; height: 300px;"
  ></camera>
<button type="primary" bindtap="takePhoto">Shot</button>
<view>Preview</view>
<image mode="widthFix" src="{{src}}"></image>
{% endraw %}
```
