---
title: "Media"
slug: "media"
excerpt: "This section consists of list of all APIs related to Media."
hidden: false
createdAt: "Wed Apr 19 2023 11:44:45 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Wed Nov 29 2023 10:45:04 GMT+0000 (Coordinated Universal Time)"
layout: "default"
parent: "Home"
has_chidlren: true
---
### Map

| Name                                       | Feature Description                               |
| :----------------------------------------- | :------------------------------------------------ |
| [createMapContext](doc:map-api#mapcontext) | Creates a MapContext object of the map component. |

### MapContext

| Name                                                                                   | Feature Description                                                                                                                            |
| :------------------------------------------------------------------------------------- | :--------------------------------------------------------------------------------------------------------------------------------------------- |
| [MapContext.addMarkers](doc:map-api#mapcontextaddmarkersobject-object)                 | Adds a marker.                                                                                                                                 |
| [MapContext.fromScreenLocation](doc:map-api#mapcontextfromscreenlocationobject-object) | Gets the latitude and longitude corresponding to the point on the screen. The origin is the top-left corner of the map.                        |
| [MapContext.getCenterLocation](doc:map-api#mapcontextgetcenterlocationobject-object)   | Gets the latitude and longitude of the center of the current map.                                                                              |
| [MapContext.getRegion](doc:map-api#mapcontextgetregionobject-object)                   | Gets the current field of view of the map.                                                                                                     |
| [MapContext.getRotate](doc:map-api#mapcontextgetrotateobject-object)                   | Gets the current rotation angle of the map.                                                                                                    |
| [MapContext.getScale](doc:map-api#mapcontextgetscaleobject-object)                     | Gets the current zoom level of the map.                                                                                                        |
| [MapContext.getSkew](doc:map-2#mapcontextgetskewobject-object)                         | Gets the current tilt angle of the map.                                                                                                        |
| [MapContext.includePoints](doc:map-api#mapcontextincludepointsobject-object)           | Zooms out to show all latitudes and longitudes.                                                                                                |
| [MapContext.moveAlong](doc:map-api#mapcontextmovealongobject-object)                   | Moves the marker along the specified path, which is used for scenarios such as track playback.                                                 |
| [MapContext.moveToLocation](doc:map-api#mapcontextmovetolocationobject-object)         | Moves the center of the map to the current location. At this time, you need to set the show-location parameter of the map component to `true`. |
| [MapContext.openMapApp](doc:map-api#mapcontextopenmapappobject-object)                 | Opens the map app to select navigation.                                                                                                        |
| [MapContext.removeMarkers](doc:map-api#mapcontextremovemarkersobject-object)           | Removes a marker.                                                                                                                              |
| [MapContext.translateMarker](doc:map-api#mapcontexttranslatemarkerobject-object)       | Translates the marker (with animation).                                                                                                        |

### Image

| Name                                                                          | Feature Description                                     |
| :---------------------------------------------------------------------------- | :------------------------------------------------------ |
| [chooseImage](doc:image-api#chooseimage-object-object)                        | Chooses an image from the local album or takes a photo. |
| [saveImageToPhotosAlbum](doc:image-api#wxsaveimagetophotosalbumobject-object) | Saves the image to the system album.                    |
| [previewImage](doc:image-api#wxpreviewimageobject-object)                     | Previews the image in full screen mode on a new page.   |
| [getImageInfo](doc:image-api#wxgetimageinfoobject-object)                     | Gets the image information.                             |

### Audio

| Name                                                                             | Feature Description                                          |
| :------------------------------------------------------------------------------- | :----------------------------------------------------------- |
| [createInnerAudioContext](doc:audio#inneraudiocontext-wxcreateinneraudiocontext) | Creates an InnerAudioContext object of the internal ‘audio’. |
| [setInnerAudioOption](doc:audio#wxsetinneraudiooptionobject-object)              | Sets the playback options for InnerAudioContext.             |

### InnerAudioContext

| Name                                                       | Feature Description                                                |
| :--------------------------------------------------------- | :----------------------------------------------------------------- |
| [InnerAudioContext.destroy](doc:audio#destroy)             | Terminates the current instance.                                   |
| [InnerAudioContext.offCanplay](doc:audio#offcanplay)       | Unlistens for the event that the audio enters the playable status. |
| [InnerAudioContext.offEnded](doc:audio#offended)           | Unlistens for the event that the audio plays to the end.           |
| [InnerAudioContext.offPause](doc:audio#offpause)           | Unlistens for the audio pause event.                               |
| [InnerAudioContext.offError](doc:audio#offerror)           | Unlistens for the audio play error event.                          |
| [InnerAudioContext.offPlay](doc:audio#offplay)             | Unlistens for the audio play event.                                |
| [InnerAudioContext.offSeeked](doc:audio#offseeked)         | Unlistens for the audio seek end event.                            |
| [InnerAudioContext.offSeeking](doc:audio#offseeking)       | Unlistens for the audio seek event.                                |
| [InnerAudioContext.offStop](doc:audio#offstop)             | Unlistens for the audio stop event.                                |
| [InnerAudioContext.offTimeUpdate](doc:audio#offtimeupdate) | Unlistens for the audio playback progress update event.            |
| [InnerAudioContext.offWaiting](doc:audio#offwaiting)       | Unlistens for the audio loading event.                             |
| [InnerAudioContext.onCanplay](doc:audio#oncanplay)         | Listens for the event that the audio enters the playable status.   |
| [InnerAudioContext.onEnded](doc:audio#onended)             | Listens for the event that the audio plays to the end.             |
| [InnerAudioContext.onError](doc:audio#onerror)             | Listens for the audio play error event.                            |
| [InnerAudioContext.onPause](doc:audio#onpause)             | Listens for the audio pause event.                                 |
| [InnerAudioContext.onPlay](doc:audio#onplay)               | Listens for the audio play event.                                  |
| [InnerAudioContext.onSeeked](doc:audio#onseeked)           | Listens for the audio seek end event.                              |
| [InnerAudioContext.onSeeking](doc:audio#onseeking)         | Listens for the audio seek event.                                  |
| [InnerAudioContext.onStop](doc:audio#onstop)               | Listens for the audio stop event.                                  |
| [InnerAudioContext.onTimeUpdate](doc:audio#ontimeupdate)   | Listens for the audio playback progress update event.              |
| [InnerAudioContext.onWaiting](doc:audio#onwaiting)         | Listens for the audio loading event.                               |
| [InnerAudioContext.pause](doc:audio#pause-1)               | Pauses the audio.                                                  |
| [InnerAudioContext.play](doc:audio#play)                   | Plays the audio.                                                   |
| [InnerAudioContext.seek](doc:audio#seek-1)                 | Seeks to the specified position.                                   |
| [InnerAudioContext.stop](doc:audio#stop)                   | Stops the audio.                                                   |

### Camera

| Name                                                                      | Feature Description                                               |
| :------------------------------------------------------------------------ | :---------------------------------------------------------------- |
| [createCameraContext](doc:camera-api#cameracontext-wxcreatecameracontext) | Creates the CameraContext context object of the camera component. |

### CameraContext

| Name                                                        | Feature Description                          |
| :---------------------------------------------------------- | :------------------------------------------- |
| [CameraContext.onCameraFrame](doc:camera-api#oncameraframe) | Gets the real-time frame data of the camera. |
| [CameraContext.setZoom](doc:camera-api#setzoom)             | Sets the zoom level.                         |
| [CameraContext.startRecord](doc:camera-api#startrecord)     | Starts recording.                            |
| [CameraContext.stopRecord](doc:camera-api#stoprecord)       | Stops recording.                             |
| [CameraContext.takePhoto](doc:camera-api#takephoto)         | Takes a photo.                               |

### CameraFrameListener

| Name                                                                            | Feature Description       |
| :------------------------------------------------------------------------------ | :------------------------ |
| [CameraFrameListener.start](doc:camera-api#cameraframelistener)                 | Listens for frame data.   |
| [CameraFrameListener.stop](doc:camera-api#cameraframelistenerstopobject-object) | Unlistens for frame data. |
