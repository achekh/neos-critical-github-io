---
title: "Video"
slug: "video"
excerpt: "Component used to render videos."
hidden: false
metadata: 
  image: []
  robots: "index"
createdAt: "Wed Apr 12 2023 07:01:21 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Fri Jul 14 2023 11:09:16 GMT+0000 (Coordinated Universal Time)"
layout: "default"
parent: "Media components"
grand_parent: "Components"
nav_order: 2
---
# Video 
Component used to render videos.

***

This component is native, so you should keep in mind relevant limits when using it.

| Attribute | Type | Default Value | Required | Description |
| :-------- | :--- | :------------ | :------- | :---------- |
| src | String |  | Yes | Address of the video resource to be played back. |
| duration | Number |  | No | Specifies the length of video. |
| controls | Boolean | true | No | Whether to display the default playback controls (play/pause buttons, playback progress, and time). |
| danmu-list | Array.<object> |  | No | On-screen comment lists. |
| danmu-btn | Boolean | false | No | Whether to display the on-screen comment button, which is only valid during initialization and cannot be changed dynamically. |
| enable-danmu | Boolean | false | No | Whether to display on-screen comments, which is only valid during initialization and cannot be changed dynamically. |
| autoplay | Boolean | false | No | Whether to play automatically. |
| loop | Boolean | false | No | Whether to loop the video. |
| muted | Boolean | false | No | Whether to mute the video. |
| initial-time | Number | 0 | No | Initial playback position of the video. |
| page-gesture | Boolean | false | No | Whether to enable gestures for brightness and volume adjustment in non-full screen mode. |
| direction | Number |  | No | Sets the video direction in full screen mode. If this parameter is not specified, it will be determin  <br />ed automatically based on the aspect ratio. Valid values: 0 (vertical direction); 90 (rotate the screen 90 degrees anticlockwise); -90 (rotate the screen 90 degrees clockwise). |
| show-progress | Boolean | true | No | If this parameter is not set, it will be shown only if the width is greater than 240. |
| show-fullscreen-btn | Boolean | true | No | Whether to show the full screen mode button. |
| show-play-btn | Boolean | true | No | Whether to show the play button in the control bar at the bottom of the video. |
| show-center-play-btn | Boolean | true | No | Whether to show the play button in the middle of the video. |
| enable-progress-gesture | Boolean | true | No | Whether to enable the progress control gesture. |
| object-fit | String | contain | No | The presentation style of the video when the video dimensions do not match the dimensions of the video container. Valid values: `contain` (contain); `fill` (fill); `cover` (cover). |
| poster | String |  | No | Web resource address of the thumbnail image. If the controls attribute value is false, poster will not take effect. |
| show-mute-btn | Boolean | false | No | Whether to show the mute button. |
| title | String |  | No | Video title, which will be displayed on top when in full screen mode. |
| play-btn-position | String | bottom | No | Position of the play button. Valid values: `bottom` (on the controls bar); `center` (in the middle of the video). |
| enable-play-gesture | Boolean | false | No | Whether to enable playback gesture, i.e., double-click for play/pause. |
| auto-pause-if-navigate | Boolean | true | No | Whether to automatically pause the video on the current page when another mini app page is redirected to. |
| bindplay | Event Handler |  | No | The `play` event triggered when playback is started/resumed. |
| bindpause | Event Handler |  | No | The `pause` event triggered when playback is paused. |
| bindended | Event Handler |  | No | The `ended` event triggered when playback reaches the end.  |
| bindtimeupdate | Event Handler |  | No | Event triggered when the playback progress changes: `event.detail = {currentTime, duration}`; trigger frequency: once every 250 ms. |
| bindfullscreenchange | Event Handler |  | No | Event triggered when the video enters/exits the full screen mode: `event.detail = {fullScreen, direction}`. Valid values: `vertical`, `horizontal`. |
| bindwaiting | Event Handler |  | No | The event triggered when the video buffers. |
| binderror | Event Handler |  | No | The event triggered when an error occurs during video playback. |
| bindprogress | Event Handler |  | No | The event triggered when the loading progress changes. Only one-stage loading is supported.  <br />`event.detail = {buffered}`; this parameter is a percentage value. |

### Direction values

| Value | Description                                |
| :---- | :----------------------------------------- |
| 0     | Normal vertical.                           |
| 90    | The screen is 90 degrees counterclockwise. |
| -90   | Screen 90 degrees clockwise                |

### Object-fit values

| Value   | Description |
| :------ | :---------- |
| contain | Contain     |
| fill    | Fill        |
| cover   | cover       |

### Play-btn-position values:

| Value  | Description     |
| :----- | :-------------- |
| bottom | Controls Bar up |
| center | Video Middle    |

> 📘 Notes
> 
> - The default width of the video is 300px and the altitude is 225px. You can set the width and height through WXSS.
