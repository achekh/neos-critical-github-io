---
title: "Canvas"
slug: "canvas-api"
excerpt: "This section consists of the list of APIs related with Canvas."
hidden: false
createdAt: "Wed Apr 19 2023 10:36:35 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Thu Dec 07 2023 09:23:22 GMT+0000 (Coordinated Universal Time)"
layout: "default"
parent: "APIs"
nav_order: 3
---
# Canvas 
This section consists of the list of APIs related with Canvas.

***

- createCanvasContext
- canvasToTempFilePath
- canvasPutImageData
- canvasGetImageData
- CanvasContext
- CanvasGradient

# CanvasContext wx.createCanvasContext(string canvasId, Object this)

Creates the [CanvasContext](doc:canvas-api#canvascontext) object of the canvas.

## Parameters

**string canvasId**

The `canvas-id` attribute of the `<canvas>` component for which to get the context

**Object this**

`this` of the current custom component instance, which indicates to search for the `<canvas>` with `canvas-id` in this custom component. If `this` is not specified, no search will be performed in any custom component.

### Returned value

[CanvasContext](doc:canvas-api#canvascontext)

# wx.canvasToTempFilePath(Object object, Object this)

Exports the content of the specified area on the current canvas as an image of the specified size. You need to call this method in the `draw()` callback to ensure that the image can be exported successfully.

## Parameters

**Object object**

| Attribute  | Type     | Default                      | Required | Description                                                                                                                |
| :--------- | :------- | :--------------------------- | :------- | :------------------------------------------------------------------------------------------------------------------------- |
| x          | number   | 0                            | No       | The abscissa of the top-left corner of the specified area on the canvas                                                    |
| y          | number   | 0                            | No       | The ordinate of the top-left corner of the specified area on the canvas                                                    |
| width      | number   | canvas width-x               | No       | The width of the specified area on the canvas                                                                              |
| height     | number   | canvas height-y              | No       | The height of the specified area on the canvas                                                                             |
| destWidth  | number   | width\*screen pixel density  | No       | The width of the output image                                                                                              |
| destHeight | number   | height\*screen pixel density | No       | The height of the output image                                                                                             |
| canvasId   | string   |                              | Yes      | Canvas ID. Pass in the `canvas-id` of the `<canvas>` component.                                                            |
| fileType   | string   | png                          | No       | Target file type                                                                                                           |
| quality    | number   |                              | Yes      | Image quality, which takes effect only for `jpg`. Value range: (0, 1]. If the value is out of the range, `1` will be used. |
| success    | function |                              | No       | Callback function for successful API call                                                                                  |
| fail       | function |                              | No       | Callback function for failed API call                                                                                      |
| complete   | function |                              | No       | Callback function for API call end (executed for both successful and failed calls)                                         |

### Valid values of `object.fileType`

| Value | Description |
| :---- | :---------- |
| jpg   | JPG image   |
| png   | PNG image   |

### `object.success` callback function

**Parameters**

**Object res**

| Attribute    | Type   | Description         |
| :----------- | :----- | :------------------ |
| tempFilePath | string | Temporary file path |

### Object this

`this` of the current custom component instance, which is used to manipulate the contained `<canvas>` component.

## Sample code

```javascript
// javascript
wx.canvasToTempFilePath({
  x: 100,
  y: 200,
  width: 50,
  height: 50,
  destWidth: 100,
  destHeight: 100,
  canvasId: 'myCanvas',
  success(res) {
    console.log(res.tempFilePath)
  }
})
```

# wx.canvasPutImageData(Object object, Object this)

Draws pixel data on the canvas. In a custom component, pass in the `this` of the custom component for the second parameter to manipulate the contained `canvas` component.

## Parameters

**Object object**

| Attribute | Type              | Default | Required | Description                                                                                                    |
| :-------- | :---------------- | :------ | :------- | :------------------------------------------------------------------------------------------------------------- |
| canvasId  | string            |         | Yes      | Canvas ID. Pass in the `canvas-id`  parameter of the `[<canvas>](<>)` component.                               |
| data      | Uint8ClampedArray |         | Yes      | The pixel data of the image, which is a one-dimensional array. Every four items represent the RGBA of a pixel. |
| x         | number            |         | Yes      | The location offset of the source image data on the target canvas (offset in the X axis)                       |
| y         | number            |         | Yes      | The location offset of the source image data on the target canvas (offset in the Y axis)                       |
| width     | number            |         | Yes      | The width of the rectangular area of the source image data                                                     |
| height    | number            |         | Yes      | The height of the rectangular area of the source image data                                                    |
| success   | function          |         | No       | Callback function for successful API call                                                                      |
| fail      | function          |         | No       | Callback function for failed API call                                                                          |
| complete  | function          |         | No       | Callback function for API call end (executed for both successful and failed calls)                             |

**Object this**

`this` of the current custom component instance, which is used to manipulate the contained `<canvas>` component.

### Sample code

```javascript
// javascript
const data = new Uint8ClampedArray([255, 0, 0, 1])
wx.canvasPutImageData({
  canvasId: 'myCanvas',
  x: 0,
  y: 0,
  width: 1,
	data,
  success(res) {}
})
```

# wx.canvasGetImageData(Object object, Object this)

Gets the pixel data hidden in the canvas area.

## Parameters

**Object object**

| Attribute | Type     | Default | Required | Description                                                                                   |
| :-------- | :------- | :------ | :------- | :-------------------------------------------------------------------------------------------- |
| canvasId  | string   |         | Yes      | Canvas ID. Pass in the `canvas-id` parameter of the `<canvas>` component.                     |
| x         | number   |         | Yes      | The abscissa of the top-left corner of the rectangular area of the image data to be extracted |
| y         | number   |         | Yes      | The ordinate of the top-left corner of the rectangular area of the image data to be extracted |
| width     | number   |         | Yes      | The width of the rectangular area of the image data to be extracted                           |
| height    | number   |         | Yes      | The height of the rectangular area of the image data to be extracted                          |
| success   | function |         | No       | Callback function for successful API call                                                     |
| fail      | function |         | No       | Callback function for failed API call                                                         |
| complete  | function |         | No       | Callback function for API call end (executed for both successful and failed calls)            |

**`object.success` callback function**

**Parameters**

### Object res

| Attribute | Type   | Description                                   |
| :-------- | :----- | :-------------------------------------------- |
| width     | number | The width of the rectangle of the image data  |
| height    | number | The height of the rectangle of the image data |

### Uint8ClampedArray data

The pixel data of the image, which is a one-dimensional array. Every four items represent the RGBA of a pixel.

**Object this**

`this` of the current custom component instance, which is used to manipulate the contained `<canvas>` component.

### Sample code

```javascript
// javascript
wx.canvasGetImageData({
  canvasId: 'myCanvas',
  x: 0,
  y: 0,
  width: 100,
  height: 100,
  success(res) {
    console.log(res.width) // 100
    console.log(res.height) // 100
    console.log(res.data instanceof Uint8ClampedArray) // true
    console.log(res.data.length) // 100 * 100 * 4
} })
```

- [CanvasContext](doc:canvas-api#canvascontext)
  - [setLineCap](doc:canvas-api#setlinecap)
  - [setTextAlign](doc:canvas-api#settextalign)
  - [setTextBaseline](doc:canvas-api#settextbaseline)
  - [setTransform](doc:canvas-api#settransform)
  - [stroke](doc:canvas-api#stroke)
  - [strokeRect](doc:canvas-api#strokerect)
  - [strokeText](doc:canvas-api#stroketext)
  - [transform](doc:canvas-api#transform)
  - [translate](doc:canvas-api#translate)
  - [arc](doc:canvas-api#arc)
  - [arcTo](doc:canvas-api#arcto)
  - [beginPath](doc:canvas-api#beginpath)
  - [bezierCurveTo](doc:canvas-api#beziercurveto)
  - [clearRect](doc:canvas-api#clearrect)
  - [clip](doc:canvas-api#clip)
  - [closePath](doc:canvas-api#closepath)
  - [createCircularGradient](doc:canvas-api#createcirculargradient)
  - [createLinearGradient](doc:canvas-api#createlineargradient)
  - [createPattern](doc:canvas-api#createpattern)
  - [draw](doc:canvas-api#draw)
  - [drawImage](doc:canvas-api#drawimage)
  - [fill](doc:canvas-api#fill)
  - [fillRect](doc:canvas-api#fillrect)
  - [fillText](doc:canvas-api#filltext)
  - [lineTo](doc:canvas-api#lineto)
  - [measureText](doc:canvas-api#measuretext)
  - [moveTo](doc:canvas-api#moveto)
  - [quadraticCurveTo](doc:canvas-api#quadraticcurveto)
  - [rect](doc:canvas-api#rect)
  - [restore](doc:canvas-api#restore)
  - [rotate](doc:canvas-api#rotate)
  - [save](doc:canvas-api#save)
  - [scale](doc:canvas-api#scale)

# CanvasContext

The drawing context of the canvas component.

## Attributes

### string fillStyle

Fill color, It is used in the same way as `CanvasContext.setFillStyle()`.

### string strokeStyle

Border color. It is used in the same way as `CanvasContext.setFillStyle()`.

### number shadowOffsetX

The horizontal offset of the shadow against the shape.

### number shadowOffsetY

The vertical offset of the shadow against the shape.

### number shadowColor

Shadow color.

### number shadowBlur

The blur level of the shadow.

### number lineWidth

The width of the line. It is used in the same way as `CanvasContext.setLineWidth()`.

### number lineCap

The endpoint style of the line. It is used in the same way as `CanvasContext.setLineCap()`.

### number lineJoin

The intersection style of the line. It is used in the same way as `CanvasContext.setLineJoin()`.

### number miterLimit

The maximum miter length. It is used in the same way as `CanvasContext.setMiterLimit()`.

### number lineDashOffset

The offset of the dotted line, which is `0` initially.

### string font

The attribute of the current font style. It is a DOMString in line with the [CSS font syntax](https://developer.mozilla.org/zh-CN/docs/Web/CSS/font) which requires at least the font size and font family name. Default value: `10px sans-serif`.

### number globalAlpha

Global brush transparency. Value range: 0–1. `0` indicates transparent, and `1` indicates opaque.

### string globalCompositeOperation

The type of the compositing operation when a new shape is drawn. Currently, only `fill` blocks can be composited on Android, and `stroke` lines are composited through `source-cover`.

The following operations are supported:

- Android: xor, source-over, source-atop, destination-out, lighter, overlay, darken, lighten, hard-light
- iOS: xor, source-over, source-atop, destination-over, destination-out, lighter, multiply, overlay, darken, lighten, color-dodge, color-burn, hard-light, soft-light, difference, exclusion, saturation, luminosity

## Methods

### [CanvasContext.draw(boolean reserve, function callback)](doc:canvas-api#draw)

Draws the drawing context description (path, transformation, and style) on the canvas.

### [CanvasGradient CanvasContext.createLinearGradient(number x0, number y0, number x1, number y1)](doc:canvas-api#createlineargradient)

Creates a linear gradient. The returned [`CanvasGradient`](doc:canvas-api#canvasgradient) bject requires specifying at least two gradient points through `CanvasGradient.addColorStop()`.

### [CanvasGradient CanvasContext.createCircularGradient(number x, number y, number r)](doc:canvas-api#createcirculargradient)

Creates a circular gradient. The start point is the center of the circle, and the end point is on the ring. The returned [`CanvasGradient`](<>) object requires specifying at least two gradient points through [`CanvasGradient.addColorStop()`](<>).

### [CanvasContext.createPattern(string image, string repetition)](doc:canvas-api#createpattern)

Creates a pattern for the specified image, which can repeat the source image in the specified direction.

### [Object CanvasContext.measureText(string text)](doc:canvas-api#measuretext)

Measures the text size. Currently, only the text width is returned. Sync API.

### [CanvasContext.save()](doc:canvas-api#save)

Saves the drawing context.

### [CanvasContext.restore()](doc:canvas-api#restore)

Restores a previously saved drawing context.

### [CanvasContext.beginPath()](doc:canvas-api#beginpath)

Starts creating a path. You need to call `fill` or `stroke` to use the path for filling or stroking.

- At the beginning, the effect is equivalent to calling `beginPath` once.
- If `setFillStyle`, `setStrokeStyle` & `setLineWidth` are set multiples times in the same path, the last setting shall prevail.

### [CanvasContext.moveTo(number x, number y)](doc:canvas-api#moveto)

Moves the path to the specified point on the canvas, without creating a line. Use the `stroke` method to draw lines.

### [CanvasContext.lineTo(number x, number y)](doc:canvas-api#lineto)

Adds a new point and creates a line from the last specified point to it on the canvas. Use the `stroke` method to draw lines.

### [CanvasContext.quadraticCurveTo(number cpx, number cpy, number x, number y)](doc:canvas-api#quadraticcurveto)

Creates a quadratic Bézier curve. The start point of the curve is the last point in the path.

### [CanvasContext.bezierCurveTo()](doc:canvas-api#beziercurveto)

Creates a cubic Bézier curve. The start point of the curve is the last point in the path.

### [CanvasContext.arc(number x, number y, number r, number sAngle, number eAngle, number counterclockwise)](doc:canvas-api#arc)

Creates an arc.

- To create a circle, set the start radian to `0` and end radian to `2 * Math.PI`.
- Use the `stroke` or `fill` method to draw the arc on the `canvas`.

### [CanvasContext.rect(number x, number y, number width, number height)](doc:canvas-api#rect)

Creates a rectangular path. You need to use the [`fill`](doc:canvas-api#fill) or [`stroke`](doc:canvas-api#stroke) method to actually draw the rectangle on the `canvas`.

### [CanvasContext.arcTo(number x1, number y1, number x2, number y2, number radius)](doc:canvas-api#arcto)

Draws an arc path based on the control points and radius.

### [CanvasContext.clip()](doc:canvas-api#clip)

Clips an area of any shape and size from the original canvas. Once an area is clipped, all future drawings will be restricted into the clipped area (no access to other areas on the canvas). You can save the current canvas area through the `save` method before using the `clip` method and restore it through the `restore` method at any time later.

### [CanvasContext.fillRect(number x, number y, number width, number height)](doc:canvas-api#fillrect)

Fills a rectangle. Use `setFillStyle` to set the fill color of the rectangle. If it is not specified, black will be used by default.

### [CanvasContext.strokeRect(number x, number y, number width, number height)](doc:canvas-api#strokerect)

Draws a rectangle (no fill). Use `setStrokeStyle()` to set the stroke color of the rectangle. If it is not specified, black will be used by default.

### [CanvasContext.clearRect(number x, number y, number width, number height)](doc:canvas-api#clearrect)

Clears the content of the rectangular area on the canvas.

### [CanvasContext.fill()](doc:canvas-api#fill)

Fills the content in the current path. The default fill color is black.

### [CanvasContext.stroke()](doc:canvas-api#stroke)

Draws the borders of the current path. The default color is black.

### [CanvasContext.closePath()](doc:canvas-api#closepath)

Closes a path to connect the start and end points. After the path is closed, if `stroke` or `fill` is not called and a new path is opened, the previous path will not be rendered.

### [CanvasContext.scale(number scaleWidth, number scaleHeight)](doc:canvas-api#scale)

Specifies to scale the ordinates and abscissas of subsequently created paths. Multiple calls will multiply.

### [CanvasContext.rotate(number rotate)](doc:canvas-api#rotate)

Rotates the current axis clockwise from the origin. The rotation angles of multiple calls will add up. You can modify the origin through the `translate` method.

### [CanvasContext.translate(number x, number y)](doc:canvas-api#translate)

Transforms the origin `(0, 0)` of the current coordinate system. The default origin is the top-left corner of the page.

### [CanvasContext.drawImage(string imageResource, number sx, number sy, number sWidth, number sHeight, number dx, number dy, number dWidth, number dHeight)](doc:canvas-api#drawimage)

Draws an image on the canvas.

### [CanvasContext.strokeText(string text, number x, number y, number maxWidth)](doc:canvas-api#stroketext)

Draws a text stroke at the specified position `(x, y)`.

### [CanvasContext.transform(number scaleX, number scaleY, number skewX, number skewY, number translateX, number translateY)](doc:canvas-api#transform)

Overlays the current transformation multiple times by using a matrix.

### [CanvasContext.setTransform(number scaleX, number scaleY, number skewX, number skewY, number translateX, number translateY)](doc:canvas-api#settransform)

Resets/Overwrites the current transformation by using a matrix.

### CanvasContext.setFillStyle(Color color)

Sets the fill color.

### CanvasContext.setStrokeStyle(Color color)

Sets the stroke color.

### CanvasContext.setShadow(number offsetX, number offsetY, number blur, string color)

Sets the shadow style.

### CanvasContext.setGlobalAlpha(number alpha)

Sets the global brush transparency.

### CanvasContext.setLineWidth(number lineWidth)

Sets the width of the line.

### CanvasContext.setLineJoin(string lineJoin)

Sets the intersection style of the line.

### [CanvasContext.setLineCap(string lineCap)](doc:canvas-api#setlinecap)

Sets the endpoint style of the line.

### CanvasContext.setLineDash(Array.<number> pattern, number offset)

Sets the style of the dotted line.

### CanvasContext.setMiterLimit(number miterLimit)

Sets the maximum miter length. Miter length refers to the distance between the inner and outer corners where two lines intersect. It takes effect when `CanvasContext.setLineJoin()` is `miter`. If the maximum miter length is exceeded, the join will be displayed with `lineJoin` as `bevel`.

### [CanvasContext.fillText(string text, number x, number y, number maxWidth)](doc:canvas-api#filltext)

Draws the filled text on the canvas.

### CanvasContext.setFontSize(number fontSize)

Sets the font size.

### [CanvasContext.setTextAlign(string align)](doc:canvas-api#settextalign)

Sets the text alignment.

### [CanvasContext.setTextBaseline(string textBaseline)](doc:canvas-api#settextbaseline)

Sets the vertical alignment of the text.

# setLineCap

## CanvasContext.setLineCap(string lineCap)

Sets the endpoint style of the line.

# Parameters

**string lineCap** The endpoint style of the line.

**Valid values of** `lineCap`

| Value  | Description                                         |
| :----- | :-------------------------------------------------- |
| butt   | A flat edge is added to each end of the line.       |
| round  | A rounded end cap is added to each end of the line. |
| square | A square end cap is added to each end of the line.  |

### Sample code

```javascript
// javascript
const ctx = wx.createCanvasContext('myCanvas')
ctx.beginPath()
ctx.moveTo(10, 10)
ctx.lineTo(150, 10)
ctx.stroke()

ctx.beginPath()
ctx.setLineCap('butt')
ctx.setLineWidth(10)
ctx.moveTo(10, 30)
ctx.lineTo(150, 30)
ctx.stroke()

ctx.beginPath()
ctx.setLineCap('round')
ctx.setLineWidth(10)
ctx.moveTo(10, 50)
ctx.lineTo(150, 50)
ctx.stroke()

ctx.beginPath()
ctx.setLineCap('square')
ctx.setLineWidth(10)
ctx.moveTo(10, 70)
ctx.lineTo(150, 70)
ctx.stroke()

ctx.draw()
```

![](https://files.readme.io/bf5c345-1.PNG)

# setTextAlign

## CanvasContext.setTextAlign(string align)

Sets the text alignment.

# Parameters

**string align** Text alignment.

**Valid values of** `align`

| Value  | Description    |
| :----- | :------------- |
| left   | Left-aligned.  |
| center | Centered.      |
| right  | Right-aligned. |

### Sample code

```javascript
// JavaScript
const ctx = wx.createCanvasContext('myCanvas')

ctx.setStrokeStyle('red')
ctx.moveTo(150, 20)
ctx.lineTo(150, 170)
ctx.stroke()

ctx.setFontSize(15)
ctx.setTextAlign('left')
ctx.fillText('textAlign=left', 150, 60)

ctx.setTextAlign('center')
ctx.fillText('textAlign=center', 150, 80)

ctx.setTextAlign('right')
ctx.fillText('textAlign=right', 150, 100)

ctx.draw()
```

![](https://files.readme.io/85898b8-2.PNG)

# setTextBaseline

## CanvasContext.setTextBaseline(string textBaseline)

Sets the vertical alignment of the text.

# Parameters

**string textBaseline** The vertical alignment of the text.

**Valid values of** `textBaseline`

| Value  | Description     |
| :----- | :-------------- |
| top    | Top-aligned.    |
| bottom | Bottom-aligned. |
| middle | Middle-aligned. |
| normal |                 |

### Sample code

```javascript
// JavaScript
const ctx = wx.createCanvasContext('myCanvas')

ctx.setStrokeStyle('red')
ctx.moveTo(5, 75)
ctx.lineTo(295, 75)
ctx.stroke()

ctx.setFontSize(20)

ctx.setTextBaseline('top')
ctx.fillText('top', 5, 75)

ctx.setTextBaseline('middle')
ctx.fillText('middle', 50, 75)

ctx.setTextBaseline('bottom')
ctx.fillText('bottom', 120, 75)

ctx.setTextBaseline('normal')
ctx.fillText('normal', 200, 75)

ctx.draw()
```

![](https://files.readme.io/0a9f720-3.PNG)

# setTransform

## CanvasContext.setTransform(number scaleX, number scaleY, number skewX, number skewY, number translateX, number translateY)

Resets/Overwrites the current transformation by using a matrix.

# Parameters

- **number scaleX** Vertical zoom.
- **number skewX** Horizontal skew.
- **number skewY** Vertical skew.
- **number translateX** Horizontal movement.
- **number translateY** Vertical movement.

# stroke

## CanvasContext.stroke()

Draws the borders of the current path. The default color is black.

### Sample code

```javascript
// JavaScript
const ctx = wx.createCanvasContext('myCanvas')
ctx.moveTo(10, 10)
ctx.lineTo(100, 10)
ctx.lineTo(100, 100)
ctx.stroke()
ctx.draw()
```

![](https://files.readme.io/35aa0f3-4.PNG)

The path drawn by `stroke()` begins at `beginPath()` but does not include `strokeRect() `.

```javascript
// JavaScript
const ctx = wx.createCanvasContext('myCanvas')
// begin path
ctx.rect(10, 10, 100, 30)
ctx.setStrokeStyle('yellow')
ctx.stroke()

// begin another path
ctx.beginPath()
ctx.rect(10, 40, 100, 30)

// only stoke this rect, not in current path
ctx.setStrokeStyle('blue')
ctx.strokeRect(10, 70, 100, 30)

ctx.rect(10, 100, 100, 30)

// it will stroke current path
ctx.setStrokeStyle('red')
ctx.stroke()
ctx.draw()
```

![](https://files.readme.io/1cb1a02-5.PNG)

# strokeRect

## CanvasContext.strokeRect(number x, number y, number width, number height)

Draws a rectangle (no fill). Use [`setStrokeStyle`](<>) to set the stroke color of the rectangle. If it is not specified, black will be used by default.

## Parameters

- **number x** The abscissa of the top-left corner of the rectangular path.
- **number y** The ordinate of the top-left corner of the rectangular path.
- **number width** The width of the rectangular path.
- **number height** The height of the rectangular path.

### Sample code

```javascript
// JavaScript
const ctx = wx.createCanvasContext('myCanvas')
ctx.setStrokeStyle('red')
ctx.strokeRect(10, 10, 150, 75)
ctx.draw()
```

![](https://files.readme.io/a58d0d7-6.PNG)

# strokeText

## CanvasContext.strokeText(string text, number x, number y, number maxWidth)

Draws a text stroke at the specified position (x, y).

# Parameters

- **string text** The text to be drawn.
- **number x** The X-axis coordinate of the text start point.
- **number y** The Y-axis coordinate of the text start point.
- **number maxWidth** The maximum width to be drawn, which is optional.

# transform

## CanvasContext.transform(number scaleX, number scaleY, number skewX, number skewY, number translateX, number translateY)

Overlays the current transformation multiple times by using a matrix.

# Parameters

- **number scaleX** Horizontal zoom.
- **number scaleY** Vertical zoom.
- **number skewX** Horizontal skew.
- **number skewY** Vertical skew.
- **number translateX** Horizontal movement.
- **number translateY** Vertical movement.

# translate

## CanvasContext.translate(number x, number y)

Transforms the origin (0, 0) of the current coordinate system. The default origin is the top-left corner of the page.

# Parameters

### number x

Horizontal coordinate offset.

### number y

Vertical coordinate offset.

### Sample code

```javascript
// JavaScript
const ctx = wx.createCanvasContext('myCanvas')

ctx.strokeRect(10, 10, 150, 100)
ctx.translate(20, 20)
ctx.strokeRect(10, 10, 150, 100)
ctx.translate(20, 20)
ctx.strokeRect(10, 10, 150, 100)

ctx.draw()
```

![](https://files.readme.io/f226b66-7.PNG)

# arc

## CanvasContext.arc(number x, number y, number r, number sAngle, number eAngle, number counterclockwise)

Creates an arc.

- To create a circle, set the start radian to 0 and end radian to 2 \* Math.PI.
- Use the stroke or fill method to draw the arc on the canvas .

# Parameters

### number x

The X coordinate of the center of the circle.

### number y

The Y coordinate of the center of the circle.

### number r

Circle radius.

### number sAngle

Start radian in radians (at the 3 o'clock position).

### number eAngle

End radian.

### number counterclockwise

Whether the radian is counterclockwise.

### Sample code

```javascript
// JavaScript
const ctx = wx.createCanvasContext('myCanvas')

// Draw coordinates
ctx.arc(100, 75, 50, 0, 2 * Math.PI)
ctx.setFillStyle('#EEEEEE')
ctx.fill()

ctx.beginPath()
ctx.moveTo(40, 75)
ctx.lineTo(160, 75)
ctx.moveTo(100, 15)
ctx.lineTo(100, 135)
ctx.setStrokeStyle('#AAAAAA')
ctx.stroke()

ctx.setFontSize(12)
ctx.setFillStyle('black')
ctx.fillText('0', 165, 78)
ctx.fillText('0.5*PI', 83, 145)
ctx.fillText('1*PI', 15, 78)
ctx.fillText('1.5*PI', 83, 10)

// Draw points
ctx.beginPath()
ctx.arc(100, 75, 2, 0, 2 * Math.PI)
ctx.setFillStyle('lightgreen')
ctx.fill()

ctx.beginPath()
ctx.arc(100, 25, 2, 0, 2 * Math.PI)
ctx.setFillStyle('blue')
ctx.fill()

ctx.beginPath()
ctx.arc(150, 75, 2, 0, 2 * Math.PI)
ctx.setFillStyle('red')
ctx.fill()

// Draw arc
ctx.beginPath()
ctx.arc(100, 75, 50, 0, 1.5 * Math.PI)
ctx.setStrokeStyle('#333333')
ctx.stroke()

ctx.draw()
```

![](https://files.readme.io/43b3f3e-8.PNG)

Key coordinates of `arc(100, 75, 50, 0, 1.5 * Math.PI)` are as follows:

- Green: Center (100, 75)
- Red: Start radian (0)
- Blue: End radian (1.5 \* Math.PI)

# arcTo

## CanvasContext.arcTo(number x1, number y1, number x2, number y2, number radius)

Draws an arc path based on the control points and radius.

# Parameters

### number x1

The X-axis coordinate of the first control point.

### number y1

The Y-axis coordinate of the first control point.

### number x2

The X-axis coordinate of the second control point.

### number y2

The Y-axis coordinate of the second control point.

### number radius

Arc radius.

# beginPath

## CanvasContext.beginPath()

Starts creating a path. You need to call `fill` or `stroke` to use the path for filling or stroking.

- At the beginning, the effect is equivalent to calling `beginPath` once.
- If `setFillStyle` , `setStrokeStyle` , and `setLineWidth` are set multiples times in the same path, the last setting shall prevail.

### Sample code

```javascript
// JavaScript
const ctx = wx.createCanvasContext('myCanvas')
// begin path
ctx.rect(10, 10, 100, 30)
ctx.setFillStyle('yellow')
ctx.fill()

// begin another path
ctx.beginPath()
ctx.rect(10, 40, 100, 30)

// only fill this rect, not in current path
ctx.setFillStyle('blue')
ctx.fillRect(10, 70, 100, 30)

ctx.rect(10, 100, 100, 30)

// it will fill current path
ctx.setFillStyle('red')
ctx.fill()
ctx.draw()
```

![](https://files.readme.io/da899ed-9.PNG)

# bezierCurveTo

## CanvasContext.bezierCurveTo()

Creates a cubic Bézier curve. The start point of the curve is the last point in the path.

### Sample code

```javascript
// JavaScript
const ctx = wx.createCanvasContext('myCanvas')

// Draw points
ctx.beginPath()
ctx.arc(20, 20, 2, 0, 2 * Math.PI)
ctx.setFillStyle('red')
ctx.fill()

ctx.beginPath()
ctx.arc(200, 20, 2, 0, 2 * Math.PI)
ctx.setFillStyle('lightgreen')
ctx.fill()

ctx.beginPath()
ctx.arc(20, 100, 2, 0, 2 * Math.PI)
ctx.arc(200, 100, 2, 0, 2 * Math.PI)
ctx.setFillStyle('blue')
ctx.fill()

ctx.setFillStyle('black')
ctx.setFontSize(12)

// Draw guides
ctx.beginPath()
ctx.moveTo(20, 20)
ctx.lineTo(20, 100)
ctx.lineTo(150, 75)

ctx.moveTo(200, 20)
ctx.lineTo(200, 100)
ctx.lineTo(70, 75)
ctx.setStrokeStyle('#AAAAAA')
ctx.stroke()

// Draw quadratic curve
ctx.beginPath()
ctx.moveTo(20, 20)
ctx.bezierCurveTo(20, 100, 200, 100, 200, 20)
ctx.setStrokeStyle('black')
ctx.stroke()

ctx.draw()
```

![](https://files.readme.io/00bfb76-10.PNG)

Key coordinates of `moveTo(20, 20) bezierCurveTo(20, 100, 200, 100, 200, 20)` are as follows:

- Red: Start point (20, 20)
- Blue: Two control points (20, 100) and (200, 100)
- Green: End point (200, 20)

# clearRect

## CanvasContext.clearRect(number x, number y, number width, number height)

Clears the content of the rectangular area on the canvas.

# Parameters

### number x

The abscissa of the top-left corner of the rectangular path.

### number y

The ordinate of the top-left corner of the rectangular path.

### number width

The width of the rectangular path.

### number height

The height of the rectangular path.

### Sample code

`clearRect` does not draw a white rectangle in the area. Instead, it clears the canvas object. For intuitive display, a background color is added to the canvas.

```xml
<!--WXML-->
{% raw %}
<canvas canvas-id="myCanvas" style="border: 1px solid; background: #123456;" />
{% endraw %}
```

```javascript
// JavaScript
const ctx = wx.createCanvasContext('myCanvas')
ctx.setFillStyle('red')
ctx.fillRect(0, 0, 150, 200)
ctx.setFillStyle('blue')
ctx.fillRect(150, 0, 150, 200)
ctx.clearRect(10, 10, 150, 75)
ctx.draw()
```

![](https://files.readme.io/ce276c4-11.PNG)

# clip

## CanvasContext.clip()

Clips an area of any shape and size from the original canvas. Once an area is clipped, all future drawings will be restricted into the clipped area (no  
access to other areas on the canvas). You can save the current canvas area through the save method before using the clip method and restore it through the `restore` method at any time later.

### Sample code

```javascript
// JavaScript
const ctx = wx.createCanvasContext('myCanvas')

wx.downloadFile({
  url: 'https://is5.mzstatic.com/image/thumb/Purple128/v4/75/3b/90/753b907c-b7fb-5877-215a-759bd73691a4/source/50x50bb.jpg',
  success(res) {
    ctx.save()
    ctx.beginPath()
    ctx.arc(50, 50, 25, 0, 2 * Math.PI)
    ctx.clip()
    ctx.drawImage(res.tempFilePath, 25, 25)
    ctx.restore()
    ctx.draw()
  }
})
```

![](https://files.readme.io/635f347-12.PNG)

# closePath

## CanvasContext.closePath()

Closes a path to connect the start and end points. After the path is closed, if `fill` or `stroke` is not called and a new path is opened, the previous path will not be rendered.

### Sample code

```javascript
// JavaScript
const ctx = wx.createCanvasContext('myCanvas')
ctx.moveTo(10, 10)
ctx.lineTo(100, 10)
ctx.lineTo(100, 100)
ctx.closePath()
ctx.stroke()
ctx.draw()
```

![](https://files.readme.io/def123d-13.PNG)

```javascript
// JavaScript
const ctx = wx.createCanvasContext('myCanvas')
// begin path
ctx.rect(10, 10, 100, 30)
ctx.closePath()

// begin another path
ctx.beginPath()
ctx.rect(10, 40, 100, 30)

// only fill this rect, not in current path
ctx.setFillStyle('blue')
ctx.fillRect(10, 70, 100, 30)

ctx.rect(10, 100, 100, 30)

// it will fill current path
ctx.setFillStyle('red')
ctx.fill()
ctx.draw()
```

![](https://files.readme.io/40d25ae-14.PNG)

# createCircularGradient

## CanvasGradient CanvasContext.createCircularGradient(number x, number y, number r)

Creates a circular gradient. The start point is the center of the circle, and the end point is on the ring. The returned CanvasGradient object requires specifying at least two gradient points through CanvasGradient.addColorStop().

# Parameters

### number x

The X coordinate of the center of the circle.

### number y

The Y coordinate of the center of the circle.

### number r

Circle radius.

## Returned value

[CanvasGradient](<>)

### Sample code

```javascript
// JavaScript
const ctx = wx.createCanvasContext('myCanvas')

// Create circular gradient
const grd = ctx.createCircularGradient(75, 50, 50)
grd.addColorStop(0, 'red')
grd.addColorStop(1, 'white')

// Fill with gradient
ctx.setFillStyle(grd)
ctx.fillRect(10, 10, 150, 80)
ctx.draw()
```

![](https://files.readme.io/828a0c1-15.PNG)

# createLinearGradient

## CanvasGradient CanvasContext.createLinearGradient(number x0, number y0, number x1, numbery1)

Creates a linear gradient. The returned `CanvasGradient` object requires specifying at least two gradient points through [CanvasGradient.addColorStop()](<>).

# Parameters

### number x0

The X coordinate of the start point.

### number y0

The Y coordinate of the start point.

### number x1

The X coordinate of the end point.

### number y1

The Y coordinate of the end point.

## Returned value

[CanvasGradient](<>)

### Sample code

```javascript
// JavaScript
const ctx = wx.createCanvasContext('myCanvas')

// Create linear gradient
const grd = ctx.createLinearGradient(0, 0, 200, 0)
grd.addColorStop(0, 'red')
grd.addColorStop(1, 'white')

// Fill with gradient
ctx.setFillStyle(grd)
ctx.fillRect(10, 10, 150, 80)
ctx.draw()
```

![](https://files.readme.io/b7312ac-16.PNG)

# createPattern

## CanvasContext.createPattern(string image, string repetition)

Creates a pattern for the specified image, which can repeat the source image in the specified direction.

# Parameters

### string image

The repeated image source, which can be only a package or temporary path.

### string repetition

Specifies how to repeat an image.

**Valid values of` repetition`**

| Value     | Description                        |
| :-------- | :--------------------------------- |
| repeat    | Horizontal and vertical repetition |
| repeat-x  | Horizontal repetition              |
| repeat-y  | Vertical repetition                |
| no-repeat | No repetition                      |

### Sample code

```javascript
// JavaScript
const ctx = wx.createCanvasContext('myCanvas')
const pattern = ctx.createPattern('/path/to/image', 'repeat-x')
ctx.fillStyle = pattern
ctx.fillRect(0, 0, 300, 150)
ctx.draw()
```

# draw

## CanvasContext.draw(boolean reserve, function callback)

Draws the drawing context description (path, transformation, and style) on the canvas.

# Parameters

### Boolean reserve

Whether this drawing follows the previous drawing. If the `reserve` parameter is `false` , the native layer will empty the canvas before drawing; if it is `true` , the content of the current canvas will be retained and overlaid by the content drawn by calling `drawCanvas` . Default value: `false` .

### Function callback

Callback function for drawing completion

### Sample code

If `reserve` is true in the second `draw()` , the result of the last drawing will be retained, and the `fillStyle` value of `red` set in the context will become the default `black`.

```javascript
// JavaScript
const ctx = wx.createCanvasContext('myCanvas')

ctx.setFillStyle('red')
ctx.fillRect(10, 10, 150, 100)
ctx.draw()
ctx.fillRect(50, 50, 150, 100)
ctx.draw(true)
```

![](https://files.readme.io/f2119f0-17.PNG)

### Sample code

If `reserve` is false in the second `draw()` , the result of the last drawing and the `fillStyle` value of `red` set in the context will not be retained.

```javascript
// JavaScript
const ctx = wx.createCanvasContext('myCanvas')

ctx.setFillStyle('red')
ctx.fillRect(10, 10, 150, 100)
ctx.draw()
ctx.fillRect(50, 50, 150, 100)
ctx.draw()
```

![](https://files.readme.io/abb764d-18.PNG)

# drawImage

## CanvasContext.drawImage(string imageResource, number sx, number sy, number sWidth, number sHeight, number dx, number dy, number dWidth, number dHeight)

Draws an image on the canvas.

# Parameters

### string imageResource

The image resource to be drawn.

### number sx

The X coordinate of the top-left corner of the rectangular selection box of the source image.

### number sy

The Y coordinate of the top-left corner of the rectangular selection box of the source image.

### number sWidth

The width of the rectangular selection box of the source image.

### number sHeight

The height of the rectangular selection box of the source image.

### number dx

The position of the top-left corner of the image in the X axis of the target canvas

### number dy

The position of the top-left corner of the image in the Y axis of the target canvas.

### number dWidth

The width of the image drawn on the target canvas. The drawn image can be scaled.

### number dHeight

The height of the image drawn on the target canvas. The drawn image can be scaled.

### Sample code

It can be written in three ways:

- drawImage(imageResource, dx, dy)
- drawImage(imageResource, dx, dy, dWidth, dHeight)
- drawImage(imageResource, sx, sy, sWidth, sHeight, dx, dy, dWidth, dHeight)

```javascript
// JavaScript
const ctx = wx.createCanvasContext('myCanvas')

wx.chooseImage({
  success(res) {
    ctx.drawImage(res.tempFilePaths[0], 0, 0, 150, 100)
    ctx.draw()
  }
})
```

![](https://files.readme.io/8934bd1-19.PNG)

# fill

## CanvasContext.fill()

Fills the content in the current path. The default fill color is black.

### Sample code

If the current path is not closed, the `fill()` method will connect the start and end points and fill the path.

```javascript
// JavaScript
const ctx = wx.createCanvasContext('myCanvas')
ctx.moveTo(10, 10)
ctx.lineTo(100, 10)
ctx.lineTo(100, 100)
ctx.fill()
ctx.draw()
```

The path filled by `fill()` begins at `beginPath()` but does not include `fillRect()` .

![](https://files.readme.io/898a1bf-20.PNG)

```javascript
// JavaScript
const ctx = wx.createCanvasContext('myCanvas')
// begin path
ctx.rect(10, 10, 100, 30)
ctx.setFillStyle('yellow')
ctx.fill()

// begin another path
ctx.beginPath()
ctx.rect(10, 40, 100, 30)

// only fill this rect, not in current path
ctx.setFillStyle('blue')
ctx.fillRect(10, 70, 100, 30)

ctx.rect(10, 100, 100, 30)

// it will fill current path
ctx.setFillStyle('red')
ctx.fill()
ctx.draw()
```

![](https://files.readme.io/4c98193-21.PNG)

# fillRect

## CanvasContext.fillRect(number x, number y, number width, number height)

Fills a rectangle. Use `[setFillStyle](<>)` to set the fill color of the rectangle. If it is not specified, black will be used by default.

# Parameters

### number x

The abscissa of the top-left corner of the rectangular path.

### number y

The ordinate of the top-left corner of the rectangular path.

### number width

The width of the rectangular path.

### number height

The height of the rectangular path.

### Sample code

```javascript
// JavaScript
const ctx = wx.createCanvasContext('myCanvas')
ctx.setFillStyle('red')
ctx.fillRect(10, 10, 150, 75)
ctx.draw()
```

![](https://files.readme.io/7a8a004-22.PNG)

# fillText

## CanvasContext.fillText(string text, number x, number y, number maxWidth)

Draws the filled text on the canvas.

# Parameters

### string text

The text output on the canvas.

### number x

The X coordinate of the top-left corner of the drawn text.

### number y

The Y coordinate of the top-left corner of the drawn text.

### number maxWidth

The maximum width to be drawn, which is optional

### Sample code

```javascript
// JavaScript
const ctx = wx.createCanvasContext('myCanvas')

ctx.setFontSize(20)
ctx.fillText('Hello', 20, 20)
ctx.fillText('MINA', 100, 100)

ctx.draw()
```

![](https://files.readme.io/79d6f90-23.PNG)

# lineTo

## CanvasContext.lineTo(number x, number y)

Adds a new point and creates a line from the last specified point to it on the canvas. Use the `stroke` method to draw lines.

# Parameters

### number x

The X coordinate of the target position.

### number y

The Y coordinate of the target position.

### Sample code

```javascript
// JavaScript
const ctx = wx.createCanvasContext('myCanvas')
ctx.moveTo(10, 10)
ctx.rect(10, 10, 100, 50)
ctx.lineTo(110, 60)
ctx.stroke()
ctx.draw()
```

![](https://files.readme.io/56690cf-24.PNG)

# measureText

## Object CanvasContext.measureText(string text)

Measures the text size. Currently, only the text width is returned. Sync API.

# Parameters

### string text

The text to be measured.

## Returned value

| Attribute | Type   | Description |
| :-------- | :----- | :---------- |
| width     | number | Text width  |

### Sample code

```javascript
// JavaScript
const ctx = wx.createCanvasContext('myCanvas')
ctx.font = 'italic bold 20px cursive'
const metrics = ctx.measureText('Hello World')
console.log(metrics.width)
```

# moveTo

## CanvasContext.moveTo(number x, number y)

Moves the path to the specified point on the canvas, without creating a line. Use the `stroke` method to draw lines.

# Parameters

### number x

The X coordinate of the target position.

### number y

The Y coordinate of the target position.

### Sample code

```javascript
// JavaScript
const ctx = wx.createCanvasContext('myCanvas')
ctx.moveTo(10, 10)
ctx.lineTo(100, 10)

ctx.moveTo(10, 50)
ctx.lineTo(100, 50)
ctx.stroke()
ctx.draw()
```

![](https://files.readme.io/5bbba63-25.PNG)

# quadraticCurveTo

## CanvasContext.quadraticCurveTo(number cpx, number cpy, number x, number y)

Creates a quadratic Bézier curve. The start point of the curve is the last point in the path.

# Parameters

### number cpx

The X coordinate of the Bézier control point.

### number cpy

The Y coordinate of the Bézier control point.

### number x

The X coordinate of the end point.

### number y

The Y coordinate of the end point.

### Sample code

```javascript
// JavaScript
const ctx = wx.createCanvasContext('myCanvas')

// Draw points
ctx.beginPath()
ctx.arc(20, 20, 2, 0, 2 * Math.PI)
ctx.setFillStyle('red')
ctx.fill()

ctx.beginPath()
ctx.arc(200, 20, 2, 0, 2 * Math.PI)
ctx.setFillStyle('lightgreen')
ctx.fill()

ctx.beginPath()
ctx.arc(20, 100, 2, 0, 2 * Math.PI)
ctx.setFillStyle('blue')
ctx.fill()

ctx.setFillStyle('black')
ctx.setFontSize(12)

// Draw guides
ctx.beginPath()
ctx.moveTo(20, 20)
ctx.lineTo(20, 100)
ctx.lineTo(200, 20)
ctx.setStrokeStyle('#AAAAAA')
ctx.stroke()

// Draw quadratic curve
ctx.beginPath()
ctx.moveTo(20, 20)
ctx.quadraticCurveTo(20, 100, 200, 20)
ctx.setStrokeStyle('black')
ctx.stroke()

ctx.draw()
```

![](https://files.readme.io/9ab7c2b-26.PNG)

Key coordinates of `moveTo(20, 20) quadraticCurveTo(20, 100, 200, 20) `are as follows:

- Red: Start point (20, 20)
- Blue: Control point (20, 100)
- Green: End point (200, 20)

# rect

## CanvasContext.rect(number x, number y, number width, number height)

Creates a rectangular path. You need to use the `[fill](<>)` or `[stroke](<>)` method to actually draw the rectangle on the `canvas` .

# Parameters

### number x

The abscissa of the top-left corner of the rectangular path.

### number y

The ordinate of the top-left corner of the rectangular path.

### number width

The width of the rectangular path.

### number height

The height of the rectangular path.

### Sample code

```javascript
// JavaScript
const ctx = wx.createCanvasContext('myCanvas')
ctx.rect(10, 10, 150, 75)
ctx.setFillStyle('red')
ctx.fill()
ctx.draw()
```

![](https://files.readme.io/7ccfc66-27.PNG)

# restore

## CanvasContext.restore()

Restores a previously saved drawing context.

### Sample code

```javascript
// JavaScript
const ctx = wx.createCanvasContext('myCanvas')

// save the default fill style
ctx.save()
ctx.setFillStyle('red')
ctx.fillRect(10, 10, 150, 100)

// restore to the previous saved state
ctx.restore()
ctx.fillRect(50, 50, 150, 100)

ctx.draw()
```

![](https://files.readme.io/9a2e08a-28.PNG)

# rotate

## CanvasContext.rotate(number rotate)

Rotates the current axis clockwise from the origin. The rotation angles of multiple calls will add up. You can modify the origin through the translate method.

# Parameters

### number rotate

The rotation angle calculated in the radians of `degrees * Math.PI/180` . The value range of degrees is 0–360.

### Sample code

```javascript
// JavaScript
const ctx = wx.createCanvasContext('myCanvas')

ctx.strokeRect(100, 10, 150, 100)
ctx.rotate(20 * Math.PI / 180)
ctx.strokeRect(100, 10, 150, 100)
ctx.rotate(20 * Math.PI / 180)
ctx.strokeRect(100, 10, 150, 100)

ctx.draw()
```

![](https://files.readme.io/189d632-29.PNG)

# save

## CanvasContext.save()

Saves the drawing context.

### Sample code

```javascript
// JavaScript
const ctx = wx.createCanvasContext('myCanvas')

// save the default fill style
ctx.save()
ctx.setFillStyle('red')
ctx.fillRect(10, 10, 150, 100)

// restore to the previous saved state
ctx.restore()
ctx.fillRect(50, 50, 150, 100)

ctx.draw()
```

![](https://files.readme.io/47a03da-30.PNG)

# scale

## CanvasContext.scale(number scaleWidth, number scaleHeight)

Specifies to scale the ordinates and abscissas of subsequently created paths. Multiple calls will multiply.

# Parameters

### number scaleWidth

The zoom factor of the abscissa (1 = 100%, 0.5 = 50%, 2 = 200%)

### number scaleHeight

The zoom factor of the ordinate (1 = 100%, 0.5 = 50%, 2 = 200%)

### Sample code

```javascript
// JavaScript
const ctx = wx.createCanvasContext('myCanvas')

ctx.strokeRect(10, 10, 25, 15)
ctx.scale(2, 2)
ctx.strokeRect(10, 10, 25, 15)
ctx.scale(2, 2)
ctx.strokeRect(10, 10, 25, 15)

ctx.draw()
```

![](https://files.readme.io/38e3b6d-31.PNG)

# CanvasGradient

Gradient object

## Methods

[CanvasGradient.addColorStop(number stop, Color color)](doc:canvas-api#addcolorstop)

Adds a gradient color point. For values smaller than the minimum `stop`, the color at the minimum `stop` is used for rendering; for those greater than the maximum `stop`, the color at the maximum `stop` is used for rendering.

## .addColorStop

### CanvasGradient.addColorStop(number stop, Color color)

Adds a gradient color point. For values smaller than the minimum `stop`, the color at the minimum stop is used for rendering; for those greater than the maximum `stop`, the color at the maximum `stop` is used for rendering.

# Parameters

### number stop

The position between the start and end in a gradient. Value range: 0–1.

### [Color](doc:canvas-api#color) color

The color of the gradient point.

### Sample code

```javascript
// JavaScript
const ctx = wx.createCanvasContext('myCanvas')

// Create circular gradient
const grd = ctx.createLinearGradient(30, 10, 120, 10)
grd.addColorStop(0, 'red')
grd.addColorStop(0.16, 'orange')
grd.addColorStop(0.33, 'yellow')
grd.addColorStop(0.5, 'green')
grd.addColorStop(0.66, 'cyan')
grd.addColorStop(0.83, 'blue')
grd.addColorStop(1, 'purple')

// Fill with gradient
ctx.setFillStyle(grd)
ctx.fillRect(10, 10, 150, 80)
ctx.draw()
```

# Color

Color. The color used on the canvas can be displayed as follows:

- RGB color: For example, `'rgb(255, 0, 0)'`.
- RGBA color: For example, '`rgba(255, 0, 0, 0.3)`'.
- Hex color: For example, `'#FF0000'`.
- Predefined color: For example, `'red'`.

There are 148 predefined colors. Note that the color name is case-insensitive.

| Color Name           | HEX      |
| :------------------- | :------- |
| AliceBlue            | # F0F8FF |
| AntiqueWhite         | # FAEBD7 |
| Aqua                 | # 00FFFF |
| Aquamarine           | # 7FFFD4 |
| Azure                | # F0FFFF |
| Beige                | # F5F5DC |
| Bisque               | # FFE4C4 |
| Black                | # 000000 |
| BlanchedAlmond       | # FFEBCD |
| Blue                 | # 0000FF |
| BlueViolet           | # 8A2BE2 |
| Brown                | # A52A2A |
| BurlyWood            | # DEB887 |
| CadetBlue            | # 5F9EA0 |
| Chartreuse           | # 7FFF00 |
| Chocolate            | # D2691E |
| Coral                | # FF7F50 |
| CornflowerBlue       | # 6495ED |
| Cornsilk             | # FFF8DC |
| Crimson              | # DC143C |
| Cyan                 | # 00FFFF |
| DarkBlue             | # 00008B |
| DarkCyan             | # 008B8B |
| DarkGoldenRod        | # B8860B |
| DarkGray             | # A9A9A9 |
| DarkGrey             | # A9A9A9 |
| DarkGreen            | # 006400 |
| DarkKhaki            | # BDB76B |
| DarkMagenta          | # 8B008B |
| DarkOliveGreen       | # 556B2F |
| DarkOrange           | # FF8C00 |
| DarkOrchid           | # 9932CC |
| DarkRed              | # 8B0000 |
| DarkSalmon           | # E9967A |
| DarkSeaGreen         | # 8FBC8F |
| DarkSlateBlue        | # 483D8B |
| DarkSlateGray        | # 2F4F4F |
| DarkSlateGrey        | # 2F4F4F |
| DarkTurquoise        | # 00CED1 |
| DarkViolet           | # 9400D3 |
| DeepPink             | # FF1493 |
| DeepSkyBlue          | # 00BFFF |
| DimGray              | # 696969 |
| DimGrey              | # 696969 |
| DodgerBlue           | # 1E90FF |
| FireBrick            | # B22222 |
| FloralWhite          | # FFFAF0 |
| ForestGreen          | # 228B22 |
| Fuchsia              | # FF00FF |
| Gainsboro            | # DCDCDC |
| GhostWhite           | # F8F8FF |
| Gold                 | # FFD700 |
| GoldenRod            | # DAA520 |
| Gray                 | # 808080 |
| Grey                 | # 808080 |
| Green                | # 008000 |
| GreenYellow          | # ADFF2F |
| HoneyDew             | # F0FFF0 |
| HotPink              | # FF69B4 |
| IndianRed            | # CD5C5C |
| Indigo               | # 4B0082 |
| Ivory                | # FFFFF0 |
| Khaki                | # F0E68C |
| Lavender             | # E6E6FA |
| LavenderBlush        | # FFF0F5 |
| LawnGreen            | # 7CFC00 |
| LemonChiffon         | # FFFACD |
| LightBlue            | # ADD8E6 |
| LightCoral           | # F08080 |
| LightCyan            | # E0FFFF |
| LightGoldenRodYellow | # FAFAD2 |
| LightGray            | # D3D3D3 |
| LightGrey            | # D3D3D3 |
| LightGreen           | # 90EE90 |
| LightPink            | # FFB6C1 |
| LightSalmon          | # FFA07A |
| LightSeaGreen        | # 20B2AA |
| LightSkyBlue         | # 87CEFA |
| LightSlateGray       | # 778899 |
| LightSlateGrey       | # 778899 |
| LightSteelBlue       | # B0C4DE |
| LightYellow          | # FFFFE0 |
| Lime                 | # 00FF00 |
| LimeGreen            | # 32CD32 |
| Linen                | # FAF0E6 |
| Magenta              | # FF00FF |
| Maroon               | # 800000 |
| MediumAquaMarine     | # 66CDAA |
| MediumBlue           | # 0000CD |
| MediumOrchid         | # BA55D3 |
| MediumPurple         | # 9370DB |
| MediumSeaGreen       | # 3CB371 |
| MediumSlateBlue      | # 7B68EE |
| MediumSpringGreen    | # 00FA9A |
| MediumTurquoise      | # 48D1CC |
| MediumVioletRed      | # C71585 |
| MidnightBlue         | # 191970 |
| MintCream            | # F5FFFA |
| MistyRose            | # FFE4E1 |
| Moccasin             | # FFE4B5 |
| NavajoWhite          | # FFDEAD |
| Navy                 | # 000080 |
| OldLace              | # FDF5E6 |
| Olive                | # 808000 |
| OliveDrab            | # 6B8E23 |
| Orange               | # FFA500 |
| OrangeRed            | # FF4500 |
| Orchid               | # DA70D6 |
| PaleGoldenRod        | # EEE8AA |
| PaleGreen            | # 98FB98 |
| PaleTurquoise        | # AFEEEE |
| PaleVioletRed        | # DB7093 |
| PapayaWhip           | # FFEFD5 |
| PeachPuff            | # FFDAB9 |
| Peru                 | # CD853F |
| Pink                 | # FFC0CB |
| Plum                 | # DDA0DD |
| PowderBlue           | # B0E0E6 |
| Purple               | # 800080 |
| RebeccaPurple        | # 663399 |
| Red                  | # FF0000 |
| RosyBrown            | # BC8F8F |
| RoyalBlue            | # 4169E1 |
| SaddleBrown          | # 8B4513 |
| Salmon               | # FA8072 |
| SandyBrown           | # F4A460 |
| SeaGreen             | # 2E8B57 |
| SeaShell             | # FFF5EE |
| Sienna               | # A0522D |
| Silver               | # C0C0C0 |
| SkyBlue              | # 87CEEB |
| SlateBlue            | # 6A5ACD |
| SlateGray            | # 708090 |
| SlateGrey            | # 708090 |
| Snow                 | # FFFAFA |
| SpringGreen          | # 00FF7F |
| SteelBlue            | # 4682B4 |
| Tan                  | # D2B48C |
| Teal                 | # 008080 |
| Thistle              | # D8BFD8 |
| Tomato               | # FF6347 |
| Turquoise            | # 40E0D0 |
| Violet               | # EE82EE |
| Wheat                | # F5DEB3 |
| White                | # FFFFFF |
| WhiteSmoke           | # F5F5F5 |
| Yellow               | # FFFF00 |
| YellowGreen          | # 9ACD32 |
