---
title: "Animation"
slug: "animation"
excerpt: "This section consists of the APIs related to animation."
hidden: false
createdAt: "Tue Apr 18 2023 13:14:43 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Wed Nov 29 2023 08:38:31 GMT+0000 (Coordinated Universal Time)"
layout: "default"
parent: "UI"
grand_parent: "APIs"
---
# Animation.left(number|string value)Length value.

If a number is passed in, px will be used as the unit by default. A length value in another custom unit can also be passed in. Sets the height. Sets the bottom value.string valueAnimationLength value. If a number is passed in, px will be used as the unit by default. A length value in another custom unit can also be passed in. Sets the width.Translates the Y axis.Animationnumber tzcreateAnimation

# wx.createAnimation

## Animation wx.createAnimation(Object object)

This API creates an animation instance and calls the instance's method to describe the animation.  Finally, the animation data is exported through the export method of the animation instance and passed to the component's animation property.

**Object object**

| Attribute       | Type   | Default     | Required | Description               |
| :-------------- | :----- | :---------- | :------- | :------------------------ |
| duration        | Number | 400         | No       | Animation duration in ms. |
| timingFunction  | String | 'linear'    | No       | Animation effect.         |
| delay           | Number | 0           | No       | Animation delay in ms.    |
| transformOrigin | String | '50% 50% 0' | No       |                           |

## Valid values of `timingFunction`

| Value         | Description                                                                                |
| :------------ | :----------------------------------------------------------------------------------------- |
| 'linear'      | The speed of the animation remains the same from start to end.                             |
| 'ease'        | The animation starts at a slow speed, accelerates, and slows down before the end.          |
| 'ease-in'     | The animation starts at a slow speed.                                                      |
| 'ease-in-out' | The animation starts and ends at a slow speed.                                             |
| 'ease-out'    | The animation ends at a slow speed.                                                        |
| 'step-start'  | The animation stays in the stopped status from the first frame till the end.               |
| 'step-end'    | The animation stays in the started status and enters the stopped status at the last frame. |

## Returned value

[Animation](doc:animation#methods)

# Animation

Animation object

## Methods

- **Array.\\ Animation.export() ** - Exports the animation queue. Previous animation operations will be cleared after each call of the `export` method.
- **Animation Animation.step(Object object) ** - End of the set of animations. You can call any number of animation methods in a set of animations, all animations in the set will start at the same time, and the next set of animations will not start until the current set ends.
- **Animation Animation.matrix()- **Same as transform-function matrix
- **Animation Animation.matrix3d() ** Same as transform-function matrix3d
- **Animation Animation.rotate(number angle) ** - Rotates clockwise from the origin by an angle.
- **Animation Animation.rotate3d(number x, number y, number z, number angle)** - Rotates clockwise from the X-axis by an angle.
- **Animation Animation.rotateX(number angle)** - Rotates clockwise from the X-axis by an angle.
- **Animation Animation.rotateY(number angle)** - Rotates clockwise from the Y-axis by an angle.
- **Animation Animation.rotateZ(number angle)** -Rotates clockwise from the Z-axis by an angle.
- **Animation Animation.scale(number sx, number sy)** - Performs zooming.
- **Animation Animation.scale3d(number sx, number sy, number sz)** - Performs zooming.
- **Animation Animation.scaleX(number scale)** - Zooms the X-axis.
- **Animation Animation.scaleY(number scale)** - Zooms the Y-axis.
- **Animation Animation.scaleZ(number scale)** - Zooms the Z-axis.
- **Animation Animation.skew(number ax, number ay)** - Tilts X/Y-axis coordinates.
- **Animation Animation.skewX(number angle)** - Tilts the X-axis coordinate.
- **Animation Animation.skewY(number angle)** - Tilts the Y-axis coordinate.
- **Animation Animation.translate(number tx, number ty)** - nPerforms translation.
- **Animation Animation.translate3d(number tx, number ty, number tz)** - Translates X, Y, and Z-axes.
- **Animation Animation.translateX(number translation)** - Translates the X-axis.
- **Animation Animation.translateY(number translation)** - Translates the Y-axis.
- **Animation Animation.translateZ(number translation)** - Translates the Z-axis.
- **Animation Animation.opacity(number value)** - Sets the opacity.
- **Animation Animation.backgroundColor(string value)** - Sets the background color.
- **Animation Animation.width(number|string value)** - Sets the width.
- **Animation Animation.height(number|string value)** - Sets the height.
- **Animation Animation.left(number|string value)** - Sets the `left` value.
- **Animation Animation.right(number|string value)** - Sets the `right` value.
- **Animation Animation.top(number|string value)** - Sets the `top` value.
- **Animation Animation.bottom(number|string value)** - Sets the `bottom` value.

### Sample code

```Text code
<view
  animation="{{animationData}}"
  style="background:red;height:100rpx;width:100rpx"
></view>
```

```Text code
Page({
	data: {
		animationData: {}
	},
	onShow() {
		const animation = wx.createAnimation({
			duration: 1000,
			timingFunction: 'ease',
    })

     this.animation = animation

     animation.scale(2, 2).rotate(45).step()

     this.setData({
      animationData: animation.export()
    })

    setTimeout(function () {
      animation.translate(30).step()
      this.setData({
        animationData: animation.export()
      })
    }.bind(this), 1000)
  },
  rotateAndScale() {
    // Rotate and zoom in simultaneously
    this.animation.rotate(45).scale(2, 2).step()
    this.setData({
      animationData: this.animation.export()
    })
  },
  rotateThenScale() {
    // Rotate first and then zoom in
    this.animation.rotate(45).step()
    this.animation.scale(2, 2).step()
    this.setData({
      animationData: this.animation.export()
    })
  },
  rotateAndScaleThenTranslate() {
    // Rotate, zoom in, and then translate
    this.animation.rotate(45).scale(2, 2).step()
    this.animation.translate(100, 100).step({duration: 1000})
    this.setData({
      animationData: this.animation.export()
    })
  }
})
```

# Animation.backgroundColor(string value)

Sets the background color.

# Parameters

**string value**

Color value

## Returned value

**Animation**

# Animation.bottom(number|string value)

Sets the `bottom` value.

# Parameters

**number|string value**

Length value. If a number is passed in, `px` will be used as the unit by default. A length value in another custom unit can also be passed in.

## Returned value

[Animation](doc:animation#methods)

# Array.\\ Animation.export()

Exports the animation queue. Previous animation operations will be cleared after each call of the `export` method.

## Returned value

\*\*Array.\*\*

animationData

# Animation.height(number|string value)

Sets the height.

# Parameters

**number|string value**

Length value. If a number is passed in,` px` will be used as the unit by default. A length value in another custom unit can also be passed in.

## Returned value

[Animation](<>)

# Animation.left(number|string value)

Sets the `left` value.

# Parameters

**number|string value**

Length value. If a number is passed in, `px` will be used as the unit by default. A length value in another custom unit can also be passed in.

# Returned value

[Animation](doc:animation#methods)

# Animation.matrix()

Same as transform-function matrix

## Returned value

[Animation](doc:animation#methods)

## .matrix3d

# Animation.matrix3d()

Same as transform-function matrix3d

## Returned value

[Animation](doc:animation#methods)

## .opacity

# Animation.opacity(number value)

Sets the opacity.

# Parameters

**number value**

Opacity. Valid range: 0–1.

# Returned value

[Animation](doc:animation#methods)

## .right

# Animation.right(number|string value)

Sets the `right` value.

# Parameters

number|string value

Length value. If a number is passed in, `px` will be used as the unit by default. A length value in another custom unit can also be passed in.

## Returned value

[Animation](doc:animation#methods)

## .rotate

# Animation.rotate(number angle)

Rotates clockwise from the origin by an angle.

# Parameters

**number angle**

Rotation angle. Value range: [-180, 180].

## Returned value

[Animation](doc:animation#methods)

## .rotate3d

# Animation.rotate3d(number x, number y, number z, number angle)

Rotates clockwise from the X axis by an angle.

# Parameters

- **number x** X coordinate of the rotation axis
- **number y** Y coordinate of the rotation axis
- **number z** Z coordinate of the rotation axis
- **number angle** Rotation angle. Value range: [-180, 180].

## Returned value

[Animation](doc:animation#methods)

## .rotateX

# Animation.rotateX(number angle)

Rotates clockwise from the X axis by an angle.

# Parameters

**number angle**

Rotation angle. Value range: [-180, 180].

## Returned value

[Animation](doc:animation#methods)

## .rotateY

# Animation.rotateY(number angle)

Rotates clockwise from the Y axis by an angle.

# Parameters

**number angle**

Rotation angle. Value range: [-180, 180].

## Returned value

[Animation](doc:animation#methods)

## .rotateZ

# Animation.rotateZ(number angle)

Rotates clockwise from the Z axis by an angle.

# Parameters

**number angle**

Rotation angle. Value range: [-180, 180].

## Returned value

[Animation](doc:animation#methods)

## .scale

# Animation.scale(number sx, number sy)

Performs zooming.

# Parameters

- **number sx** If there is only the `sx` parameter, it means that both the X and Y-axes are zoomed `sx` times.
- **number sy** Zoom the Y-axis `sy` times

## Returned value

[Animation](doc:animation#methods)

## .scale3d

# Animation.scale3d(number sx, number sy, number sz)

Performs zooming.

# Parameters

- **number sx** Zoom factor of the X-axis
- **number sy** Zoom factor of the Y-axis
- **number sz** Zoom factor of the Z-axis

## Returned value

[Animation](doc:animation#methods)

## .scaleX

# Animation.scaleX(number scale)

Zooms the X-axis.

# Parameters

**number scale** Zoom factor of the X axis

## Returned value

[Animation](doc:animation#methods)

## .scaleY

# Animation.scaleY(number scale)

Zooms the Y-axis.

# Parameters

**number scale**Zoom factor of the Y-axis

## Returned value

[Animation](doc:animation#methods)

## .scaleZ

# Animation.scaleZ(number scale)

Zooms the Z-axis.

# Parameters

**number scale** Zoom factor of the Z axis

## Returned value

[Animation](doc:animation#methods)

## .skew

# Animation.skew(number ax, number ay)

Tilts X/Y-axis coordinates.

# Parameters

- **number ax** Tilt angle of the X-axis coordinate. Value range: [-180, 180].
- **number ay** Tilt angle of the Y-axis coordinate. Value range: [-180, 180].

## Returned value

[Animation](doc:animation#methods)

## .skewX

# Animation.skewX(number angle)

Tilts the X-axis coordinate.

# Parameters

**number angle** Tilt angle. Value range: [-180, 180].

## Returned value

[Animation](doc:animation#methods)

## .skewY

# Animation.skewY(number angle)

Tilts the Y-axis coordinate.

# Parameters

**number angle** Tilt angle. Value range: [-180, 180].

## Returned value

[Animation](doc:animation#methods)

## .step

## Animation.step(Object object)

End of the set of animations. You can call any number of animation methods in a set of animations, all animations in the set will start at the same time. The next set of animations will not start until the current set ends.

# Parameters

**Object object**

| Attribute       | Type   | Default     | Required | Description               |
| :-------------- | :----- | :---------- | :------- | :------------------------ |
| duration        | Number | 400         | No       | Animation duration in ms. |
| timingFunction  | String | 'linear'    | No       | Animation effect.         |
| delay           | Number | 0           | No       | Animation delay in ms.    |
| transformOrigin | String | '50% 50% 0' | No       |                           |

**Valid values of `timingFunction`**

| Value         | Description                                                                                |
| :------------ | :----------------------------------------------------------------------------------------- |
| 'linear'      | The speed of the animation remains the same from start to end.                             |
| 'ease'        | The animation starts at a slow speed, accelerates, and slows down before the end.          |
| 'ease-in'     | The animation starts at a slow speed.                                                      |
| 'ease-in-out' | The animation starts and ends at a slow speed.                                             |
| 'ease-out'    | The animation ends at a slow speed.                                                        |
| 'step-start'  | The animation stays in the stopped status from the first frame till the end.               |
| 'step-end'    | The animation stays in the started status and enters the stopped status at the last frame. |

## Returned value

[Animation](<>)

animation

## .top

# Animation.top(number|string value)

Sets the `top` value.

# Parameters

**number|string value** Length value. If a number is passed in, `px` will be used as the unit by default. A length value in another custom unit can also be passed in.

## Returned value

[Animation](doc:animation#methods)

## .translate

# Animation.translate(number tx, number ty)

Performs translation.

# Parameters

- **number tx** - If only this parameter is present, it means to translate by `tx` in px on the X axis.
- **number ty** - The distance to translate on the Y axis in px

## Returned value

[Animation](doc:animation#methods)

## .translate3d

# Animation.translate3d(number tx, number ty, number tz)

Translates X, Y, and Z-axes.

## Parameters

- **number tx** - The distance to translate on the X axis in px
- **number ty** - The distance to translate on the Y axis in px
- **number tz** - The distance to translate on the Z axis in px

## Returned value

[Animation](doc:animation#methods)

## .translateX

# Animation.translateX(number translation)

Translates the X-axis.

# Parameters

**number translation** The distance to translate on the X-axis in px

## Returned value

[Animation](doc:animation#methods)

## .translateY

# Animation.translateY(number translation)

Translates the Y axis.

# Parameters

**number translation** The distance to translate on the Y axis in px

## Returned value

[Animation](doc:animation#methods)

## .translateZ

# Animation.translateZ(number translation)

Translates the Z-axis.

# Parameters

**number translation** The distance to translate on the Z axis in px

## Returned value

[Animation](doc:animation#methods)

## .width

# Animation.width(number|string value)

Sets the width.

# Parameters

**number|string value** Length value. If a number is passed in, `px` will be used as the unit by default. A length value in another custom unit can also be passed in.

## Returned value

[Animation](doc:animation#methods)

## .backgroundColor

# Animation.backgroundColor(string value)

Sets the background color.

# Parameters

**string value** Color value

## Returned value

[Animation](doc:animation#methods)

## .bottom

# Animation.bottom(number|string value)

Sets the `bottom` value.

# Parameters

**number|string value** Length value. If a number is passed in, `px` will be used as the unit by default. A length value in another custom unit can also be passed in.

## Returned value

[Animation](doc:animation#methods)

## .export

# Array.\\ Animation.export()

Exports the animation queue. Previous animation operations will be cleared after each call of the `export` method.

## Returned value

\*\*Array.\*\*

animationData

## .height

# Animation.height(number|string value)

Sets the height.

# Parameters

**number|string value** Length value. If a number is passed in, `px` will be used as the unit by default. A length value in another custom unit can also be passed in.

## Returned value

[Animation](doc:animation#methods)

## .left

# Animation.left(number|string value)

Sets the `left` value.

# Parameters

**number|string value** Length value. If a number is passed in, `px` will be used as the unit by default. A length value in another custom unit can also be passed in.

## Returned value

[Animation](doc:animation#methods)

## .matrix

# Animation.matrix()

Same as [transform-function matrix](doc:animation#methods)

## Returned value

[Animation](doc:animation#methods)
