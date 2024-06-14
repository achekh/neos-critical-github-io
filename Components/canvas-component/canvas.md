---
title: "Canvas"
slug: "canvas"
excerpt: "This component is native. Hence, you should keep in mind relevant limits when using it."
hidden: false
metadata: 
  image: []
  robots: "index"
createdAt: "Thu Apr 13 2023 07:08:21 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Tue Jun 20 2023 05:29:30 GMT+0000 (Coordinated Universal Time)"
layout: "default"
parent: "Canvas"
grand_parent: "Components"
---
# Canvas 
*** 
| Attribute       | Type          | Default Value | Required | Description                                                                                                                       |
| :-------------- | :------------ | :------------ | :------- | :-------------------------------------------------------------------------------------------------------------------------------- |
| canvas-id       | String        |               | No       | Unique ID of the canvas component.                                                                                                |
| disable-scroll  | Boolean       | false         | No       | Disables scroll and pull-to-refresh when the cursor is moved on the canvas and the gesture event is bound.                        |
| bindtouchstart  | Event Handler |               | No       | Touch starts.                                                                                                                     |
| bindtouchmove   | Event Handler |               | No       | Moves upon touch.                                                                                                                 |
| bindtouchend    | Event Handler |               | No       | Touch ends.                                                                                                                       |
| bindtouchcancel | Event Handler |               | No       | Touch is interrupted by the incoming call or pop-up window.                                                                       |
| bindlongtap     | Event Handler |               | No       | The event triggered after the user touches the screen and holds for 500 ms, after which scroll will not be triggered by movement. |
| binderror       | Event Handler |               | No       | The error event triggered when an error occurred: `event.detail = {errMsg: 'something wrong'}`.                                   |

> 📘 Notes
> 
> - For canvas tags, the default width is 300px and height is 150px.
> - The canvas-id must be unique on the same page. If a previous canvas-id is used, its corresponding canvas will be hidden and cannot work normally.
> - Avoid setting large width and height values; otherwise, crashes will occur on Android.

### Sample code

```xml WXML
<!-- canvas.wxml -->
<canvas style="width: 300px; height: 200px;" canvas-id="firstCanvas"></canvas>
<!-- When the absolute location is used, the canvas after the normal flow has a higher priority for showing than the canvas before the normal
flow. -->
<canvas style="width: 400px; height: 500px;" canvas-id="secondCanvas"></canvas>
<!-- If the `canvas-id` of a canvas is the same as that of the previous canvas, the canvas will not be shown, and an error event will be sent
to the AppService. -->
<canvas
  style="width: 400px; height: 500px;"
  canvas-id="secondCanvas"
  binderror="canvasIdErrorCallback"
  ></canvas>

```
```javascript JavaScript
Page({
  canvasIdErrorCallback(e) {
  	console.error(e.detail.errMsg)
  },
  onReady(e) {
    // Use `wx.createContext` to get the drawing context
    const context = wx.createCanvasContext('firstCanvas')
    context.setStrokeStyle('#00ff00')
    context.setLineWidth(5)
    context.rect(0, 0, 200, 200)
    context.stroke()
    context.setStrokeStyle('#ff0000')
    context.setLineWidth(2)
    context.moveTo(160, 100)
    context.arc(100, 100, 60, 0, 2 * Math.PI, true)
    context.moveTo(140, 100)
    context.arc(100, 100, 40, 0, Math.PI, false)
    context.moveTo(85, 80)
    context.arc(80, 80, 5, 0, 2 * Math.PI, true)
    context.moveTo(125, 80)
    context.arc(120, 80, 5, 0, 2 * Math.PI, true)
    context.stroke()
    context.draw()
  }
})
```

> 📘 Bugs and tips
> 
> 1. Keep in mind the restrictions on the use of native components.
> 2. Bug: Avoid setting large width and height values; otherwise, crashes will occur on Android.
