---
title: "Camera"
slug: "camera-api"
excerpt: "This section consists of Camera related APIs for Mini App."
hidden: false
createdAt: "Fri Apr 21 2023 07:28:52 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Wed Nov 29 2023 13:17:33 GMT+0000 (Coordinated Universal Time)"
layout: "default"
parent: "Media"
grand_parent: "APIs"
---
# Camera 
This section consists of Camera related APIs for Mini App.
*** 
- [createCameraContext](doc:camera-api#cameracontext-wxcreatecameracontext)
- [CameraContext](doc:camera-api#cameracontext)
- [CameraFrameListener](doc:camera-api#cameraframelistener-cameracontextoncameraframeoncameraframecallback-callback)

## [CameraContext](doc:camera-api#cameracontext) wx.createCameraContext()

Creates the`[ CameraContext](<>)` object of `camera `.

## Returned value

[CameraContext](<>)

# CameraContext

`CameraContext` instance, which can be obtained through [wx.createCameraContext](doc:camera-api#cameracontext-wxcreatecameracontext).  
`cameraContext` is bound to the only `<camera>` component on the page to manipulate it.

## Methods

[CameraFrameListener CameraContext.onCameraFrame(onCameraFrameCallback callback)](doc:camera-api#cameraframelistener-cameracontextoncameraframeoncameraframecallback-callback)  
Gets the real-time frame data of the camera.

[CameraContext.setZoom(Object object)](doc:camera-api#cameracontextsetzoomobject-object)  
Sets the zoom level.

[CameraContext.takePhoto(Object object)](doc:camera-api#cameracontexttakephotoobject-object)  
Takes a photo.

[CameraContext.startRecord(Object object)](doc:camera-api#cameracontextstartrecordobject-object)  
Starts recording.

[CameraContext.stopRecord()](doc:camera-api#cameracontextstoprecordobject-object)  
Stops recording.

## Sample code

## onCameraFrame

## CameraFrameListener CameraContext.onCameraFrame(onCameraFrameCallback callback

Gets the real-time frame data of the camera.

# Parameters

## Function callback

Callback function

# Parameters

**Object res**

| Attribute | Type        | Description                                                                                                    |
| :-------- | :---------- | :------------------------------------------------------------------------------------------------------------- |
| width     | Number      | The width of the rectangle of the image data.                                                                  |
| height    | Number      | The height of the rectangle of the image data.                                                                 |
| data      | ArrayBuffer | The pixel data of the image, which is a one-dimensional array. Every four items represent the RGBA of a pixel. |

## Returned value

[CameraFrameListener](doc:camera-api#cameraframelistener-cameracontextoncameraframeoncameraframecallback-callback)

> > 📘 Note
> > 
> > To use the API, you need to specify `frame-size` in the [camera](doc:camera) component.

### Sample code

```javascript
// JavaScript
const context = wx.createCameraContext()
const listener = context.onCameraFrame((frame) => {
	console.log(frame.data instanceof ArrayBuffer, frame.width, frame.height)
})
listener.start()
```

## CameraContext.setZoom(Object object)

Sets the zoom level.

## Parameters

**Object object**

| Attribute | Type     | Required | Description                                                                                   |
| :-------- | :------- | :------- | :-------------------------------------------------------------------------------------------- |
| zoom      | Number   | Yes      | Zoom level. Value range: [1, maxZoom]. `zoom` can be a decimal accurate to one decimal place. |
| success   | Function | No       | Callback function for successful API call.                                                    |
| fail      | Function | No       | Callback function for failed API call.                                                        |
| complete  | Function | No       | Callback function for API call end (executed for both successful and failed calls).           |

**`object.success` callback function**

# Parameters

**Object res**

| Attribute | Type   | Description                                                                                                                                           |
| :-------- | :----- | :---------------------------------------------------------------------------------------------------------------------------------------------------- |
| zoom      | Number | Actual zoom level. Due to system restrictions, certain device models may not support the specified value, which will be changed to the closest value. |

## CameraContext.startRecord(Object object)

Starts recording.

## Parameters

**Object object**

| Attribute       | Type     | Description                                                                         |
| :-------------- | :------- | :---------------------------------------------------------------------------------- |
| timeoutCallback | Function | Recording ends when the value exceeds 30 seconds or the page is `onHide` .          |
| success         | Function | Callback function for successful API call.                                          |
| fail            | Function | Callback function for failed API call.                                              |
| complete        | Function | Callback function for API call end (executed for both successful and failed calls). |

`object.timeoutCallback` callback function

# Parameters

**Object res**

| Attribute     | Type   | Description                                     |
| :------------ | :----- | :---------------------------------------------- |
| tempThumbPath | String | The temporary path of the thumbnail image file. |
| tempVideoPath | String | The temporary path of the video file.           |

## CameraContext.stopRecord(Object object)

**Stops recording.**

# Parameters

**Object object**

| Attribute | Type     | Description                                                                        |
| :-------- | :------- | :--------------------------------------------------------------------------------- |
| success   | Function | Callback function for successful API call                                          |
| fail      | Function | Callback function for failed API call                                              |
| complete  | Function | Callback function for API call end (executed for both successful and failed calls) |

`object.success` callback function

# Parameters

**Object res**

| Attribute     | Type   | Description                                    |
| :------------ | :----- | :--------------------------------------------- |
| tempThumbPath | String | The temporary path of the thumbnail image file |
| tempVideoPath | String | The temporary path of the video file           |

## CameraContext.takePhoto(Object object)

Takes a photo.

# Parameters

**Object object**

| Attribute | Type     | Default | Description                                                                         |
| :-------- | :------- | :------ | :---------------------------------------------------------------------------------- |
| quality   | String   | normal  | Image quality.                                                                      |
| success   | Function |         | Callback function for successful API call.                                          |
| fail      | Function |         | Callback function for failed API call                                               |
| complete  | Function |         | Callback function for API call end (executed for both successful and failed calls). |

**Valid values of** `object.quality`

| Value  | Description    |
| :----- | :------------- |
| high   | High quality   |
| normal | Medium quality |
| low    | Low quality    |

`object.success` callback function

# Parameters

**Object res**

| Attribute     | Type   | Description                           |
| :------------ | :----- | :------------------------------------ |
| tempImagePath | String | The temporary path of the photo file. |

# CameraFrameListener

> Documentation: [Camera](doc:camera).

The listener returned by `CameraContext.onCameraFrame()` .

## Methods

[CameraFrameListener.start(Object object)](doc:camera-api#cameraframelistenerstartobject-object)

Listens for frame data.

[CameraFrameListener.stop()](doc:camera-api#cameraframelistenerstopobject-object)

Unlistens for frame data.

## CameraFrameListener.start(Object object)

Listens for frame data.

# Parameters

**Object object**

| Attribute | Type     | Description                                                                         |
| :-------- | :------- | :---------------------------------------------------------------------------------- |
| success   | Function | Callback function for successful API call.                                          |
| fail      | Function | Callback function for failed API call.                                              |
| complete  | Function | Callback function for API call end (executed for both successful and failed calls). |

## CameraFrameListener.stop(Object object)

Unlistens for frame data.

# Parameters

**Object object**

| Attribute | Type     | Description                                                                         |
| :-------- | :------- | :---------------------------------------------------------------------------------- |
| success   | Function | Callback function for successful API call.                                          |
| fail      | Function | Callback function for failed API call.                                              |
| complete  | Function | Callback function for API call end (executed for both successful and failed calls). |
