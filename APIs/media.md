---
title: "Media"
slug: "media"
excerpt: "This section consists of list of all APIs related to Media."
hidden: false
createdAt: "Wed Apr 19 2023 11:44:45 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Wed Nov 29 2023 10:45:04 GMT+0000 (Coordinated Universal Time)"
layout: "default"
parent: "APIs"
has_children: true
has_toc: false
nav_order: 9
---
# Media 
This section consists of list of all APIs related to Media.

***

### Map

| Name                                       | Feature Description                               |
| :----------------------------------------- | :------------------------------------------------ |
| [createMapContext](media/map-api#mapcontext) | Creates a MapContext object of the map component. |

### MapContext

| Name                                                                                   | Feature Description                                                                                                                            |
| :------------------------------------------------------------------------------------- | :--------------------------------------------------------------------------------------------------------------------------------------------- |
| [MapContext.addMarkers](media/map-api#mapcontextaddmarkersobject-object)                 | Adds a marker.                                                                                                                                 |
| [MapContext.fromScreenLocation](media/map-api#mapcontextfromscreenlocationobject-object) | Gets the latitude and longitude corresponding to the point on the screen. The origin is the top-left corner of the map.                        |
| [MapContext.getCenterLocation](media/map-api#mapcontextgetcenterlocationobject-object)   | Gets the latitude and longitude of the center of the current map.                                                                              |
| [MapContext.getRegion](media/map-api#mapcontextgetregionobject-object)                   | Gets the current field of view of the map.                                                                                                     |
| [MapContext.getRotate](media/map-api#mapcontextgetrotateobject-object)                   | Gets the current rotation angle of the map.                                                                                                    |
| [MapContext.getScale](media/map-api#mapcontextgetscaleobject-object)                     | Gets the current zoom level of the map.                                                                                                        |
| [MapContext.getSkew](media/map-2#mapcontextgetskewobject-object)                         | Gets the current tilt angle of the map.                                                                                                        |
| [MapContext.includePoints](media/map-api#mapcontextincludepointsobject-object)           | Zooms out to show all latitudes and longitudes.                                                                                                |
| [MapContext.moveAlong](media/map-api#mapcontextmovealongobject-object)                   | Moves the marker along the specified path, which is used for scenarios such as track playback.                                                 |
| [MapContext.moveToLocation](media/map-api#mapcontextmovetolocationobject-object)         | Moves the center of the map to the current location. At this time, you need to set the show-location parameter of the map component to `true`. |
| [MapContext.openMapApp](media/map-api#mapcontextopenmapappobject-object)                 | Opens the map app to select navigation.                                                                                                        |
| [MapContext.removeMarkers](media/map-api#mapcontextremovemarkersobject-object)           | Removes a marker.                                                                                                                              |
| [MapContext.translateMarker](media/map-api#mapcontexttranslatemarkerobject-object)       | Translates the marker (with animation).                                                                                                        |

### Image

| Name                                                                          | Feature Description                                     |
| :---------------------------------------------------------------------------- | :------------------------------------------------------ |
| [chooseImage](media/image-api#chooseimage-object-object)                        | Chooses an image from the local album or takes a photo. |
| [saveImageToPhotosAlbum](media/image-api#wxsaveimagetophotosalbumobject-object) | Saves the image to the system album.                    |
| [previewImage](media/image-api#wxpreviewimageobject-object)                     | Previews the image in full screen mode on a new page.   |
| [getImageInfo](media/image-api#wxgetimageinfoobject-object)                     | Gets the image information.                             |

### Audio

| Name                                                                             | Feature Description                                          |
| :------------------------------------------------------------------------------- | :----------------------------------------------------------- |
| [createInnerAudioContext](media/audio#inneraudiocontext-wxcreateinneraudiocontext) | Creates an InnerAudioContext object of the internal ‘audio’. |
| [setInnerAudioOption](media/audio#wxsetinneraudiooptionobject-object)              | Sets the playback options for InnerAudioContext.             |

### InnerAudioContext

| Name                                                       | Feature Description                                                |
| :--------------------------------------------------------- | :----------------------------------------------------------------- |
| [InnerAudioContext.destroy](media/audio#destroy)             | Terminates the current instance.                                   |
| [InnerAudioContext.offCanplay](media/audio#offcanplay)       | Unlistens for the event that the audio enters the playable status. |
| [InnerAudioContext.offEnded](media/audio#offended)           | Unlistens for the event that the audio plays to the end.           |
| [InnerAudioContext.offPause](media/audio#offpause)           | Unlistens for the audio pause event.                               |
| [InnerAudioContext.offError](media/audio#offerror)           | Unlistens for the audio play error event.                          |
| [InnerAudioContext.offPlay](media/audio#offplay)             | Unlistens for the audio play event.                                |
| [InnerAudioContext.offSeeked](media/audio#offseeked)         | Unlistens for the audio seek end event.                            |
| [InnerAudioContext.offSeeking](media/audio#offseeking)       | Unlistens for the audio seek event.                                |
| [InnerAudioContext.offStop](media/audio#offstop)             | Unlistens for the audio stop event.                                |
| [InnerAudioContext.offTimeUpdate](media/audio#offtimeupdate) | Unlistens for the audio playback progress update event.            |
| [InnerAudioContext.offWaiting](media/audio#offwaiting)       | Unlistens for the audio loading event.                             |
| [InnerAudioContext.onCanplay](media/audio#oncanplay)         | Listens for the event that the audio enters the playable status.   |
| [InnerAudioContext.onEnded](media/audio#onended)             | Listens for the event that the audio plays to the end.             |
| [InnerAudioContext.onError](media/audio#onerror)             | Listens for the audio play error event.                            |
| [InnerAudioContext.onPause](media/audio#onpause)             | Listens for the audio pause event.                                 |
| [InnerAudioContext.onPlay](media/audio#onplay)               | Listens for the audio play event.                                  |
| [InnerAudioContext.onSeeked](media/audio#onseeked)           | Listens for the audio seek end event.                              |
| [InnerAudioContext.onSeeking](media/audio#onseeking)         | Listens for the audio seek event.                                  |
| [InnerAudioContext.onStop](media/audio#onstop)               | Listens for the audio stop event.                                  |
| [InnerAudioContext.onTimeUpdate](media/audio#ontimeupdate)   | Listens for the audio playback progress update event.              |
| [InnerAudioContext.onWaiting](media/audio#onwaiting)         | Listens for the audio loading event.                               |
| [InnerAudioContext.pause](media/audio#pause-1)               | Pauses the audio.                                                  |
| [InnerAudioContext.play](media/audio#play)                   | Plays the audio.                                                   |
| [InnerAudioContext.seek](media/audio#seek-1)                 | Seeks to the specified position.                                   |
| [InnerAudioContext.stop](media/audio#stop)                   | Stops the audio.                                                   |

### Camera

| Name                                                                      | Feature Description                                               |
| :------------------------------------------------------------------------ | :---------------------------------------------------------------- |
| [createCameraContext](media/camera-api#cameracontext-wxcreatecameracontext) | Creates the CameraContext context object of the camera component. |

### CameraContext

| Name                                                        | Feature Description                          |
| :---------------------------------------------------------- | :------------------------------------------- |
| [CameraContext.onCameraFrame](media/camera-api#oncameraframe) | Gets the real-time frame data of the camera. |
| [CameraContext.setZoom](media/camera-api#setzoom)             | Sets the zoom level.                         |
| [CameraContext.startRecord](media/camera-api#startrecord)     | Starts recording.                            |
| [CameraContext.stopRecord](media/camera-api#stoprecord)       | Stops recording.                             |
| [CameraContext.takePhoto](media/camera-api#takephoto)         | Takes a photo.                               |

### CameraFrameListener

| Name                                                                            | Feature Description       |
| :------------------------------------------------------------------------------ | :------------------------ |
| [CameraFrameListener.start](media/camera-api#cameraframelistener)                 | Listens for frame data.   |
| [CameraFrameListener.stop](media/camera-api#cameraframelistenerstopobject-object) | Unlistens for frame data. |
