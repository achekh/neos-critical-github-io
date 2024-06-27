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
nav_order: 3
---
# Camera 
Native camera component.

***

This component is native, so you should keep in mind relevant limits when using it.

The user should 'authorize' `scope.camera`.

| Attribute | Type | Default Value | Required | Description |
| :-------- | :--- | :------------ | :------- | :---------- |
| mode | String | normal | No | Valid values: `normal`, `scanCode`. |
| device-position | String | back | No | Valid values: `front`, `back`. |
| flash | String | car | No | Valid values: `auto`, `on`, `off`. |
| bindstop | Event Handler |  | No | Triggered when the camera is abnormally terminated, for example, it is switched to  \nthe background. |
| binderror | Event Handler |  | No | Triggered if the user hasn't granted the camera access. |
| bindscancode | Event Handler |  | No | Triggered when the scan is successful, which takes effect only when mode is `sca  \nnCode`. |

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
