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
---
# Video 
*** 
This component is native, so you should keep in mind relevant limits when using it.

[block:parameters]
{
  "data": {
    "h-0": "Attribute",
    "h-1": "Type",
    "h-2": "Default Value",
    "h-3": "Required",
    "h-4": "Description",
    "0-0": "src",
    "0-1": "String",
    "0-2": "",
    "0-3": "Yes",
    "0-4": "Address of the video resource to be played back.",
    "1-0": "duration",
    "1-1": "Number",
    "1-2": "",
    "1-3": "No",
    "1-4": "Specifies the length of video.",
    "2-0": "controls",
    "2-1": "Boolean",
    "2-2": "true",
    "2-3": "No",
    "2-4": "Whether to display the default playback controls (play/pause buttons, playback progress, and time).",
    "3-0": "danmu-list",
    "3-1": "Array.<object>",
    "3-2": "",
    "3-3": "No",
    "3-4": "On-screen comment lists.",
    "4-0": "danmu-btn",
    "4-1": "Boolean",
    "4-2": "false",
    "4-3": "No",
    "4-4": "Whether to display the on-screen comment button, which is only valid during initialization and cannot be changed dynamically.",
    "5-0": "enable-danmu",
    "5-1": "Boolean",
    "5-2": "false",
    "5-3": "No",
    "5-4": "Whether to display on-screen comments, which is only valid during initialization and cannot be changed dynamically.",
    "6-0": "autoplay",
    "6-1": "Boolean",
    "6-2": "false",
    "6-3": "No",
    "6-4": "Whether to play automatically.",
    "7-0": "loop",
    "7-1": "Boolean",
    "7-2": "false",
    "7-3": "No",
    "7-4": "Whether to loop the video.",
    "8-0": "muted",
    "8-1": "Boolean",
    "8-2": "false",
    "8-3": "No",
    "8-4": "Whether to mute the video.",
    "9-0": "initial-time",
    "9-1": "Number",
    "9-2": "0",
    "9-3": "No",
    "9-4": "Initial playback position of the video.",
    "10-0": "page-gesture",
    "10-1": "Boolean",
    "10-2": "false",
    "10-3": "No",
    "10-4": "Whether to enable gestures for brightness and volume adjustment in non-full screen mode.",
    "11-0": "direction",
    "11-1": "Number",
    "11-2": "",
    "11-3": "No",
    "11-4": "Sets the video direction in full screen mode. If this parameter is not specified, it will be determin  \ned automatically based on the aspect ratio. Valid values: 0 (vertical direction); 90 (rotate the screen 90 degrees anticlockwise); -90 (rotate the screen 90 degrees clockwise).",
    "12-0": "show-progress",
    "12-1": "Boolean",
    "12-2": "true",
    "12-3": "No",
    "12-4": "If this parameter is not set, it will be shown only if the width is greater than 240.",
    "13-0": "show-fullscreen-btn",
    "13-1": "Boolean",
    "13-2": "true",
    "13-3": "No",
    "13-4": "Whether to show the full screen mode button.",
    "14-0": "show-play-btn",
    "14-1": "Boolean",
    "14-2": "true",
    "14-3": "No",
    "14-4": "Whether to show the play button in the control bar at the bottom of the video.",
    "15-0": "show-center-play-btn",
    "15-1": "Boolean",
    "15-2": "true",
    "15-3": "No",
    "15-4": "Whether to show the play button in the middle of the video.",
    "16-0": "enable-progress-gesture",
    "16-1": "Boolean",
    "16-2": "true",
    "16-3": "No",
    "16-4": "Whether to enable the progress control gesture.",
    "17-0": "object-fit",
    "17-1": "String",
    "17-2": "contain",
    "17-3": "No",
    "17-4": "The presentation style of the video when the video dimensions do not match the dimensions of the video container. Valid values: `contain` (contain); `fill` (fill); `cover` (cover).",
    "18-0": "poster",
    "18-1": "String",
    "18-2": "",
    "18-3": "No",
    "18-4": "Web resource address of the thumbnail image. If the controls attribute value is false, poster will not take effect.",
    "19-0": "show-mute-btn",
    "19-1": "Boolean",
    "19-2": "false",
    "19-3": "No",
    "19-4": "Whether to show the mute button.",
    "20-0": "title",
    "20-1": "String",
    "20-2": "",
    "20-3": "No",
    "20-4": "Video title, which will be displayed on top when in full screen mode.",
    "21-0": "play-btn-position",
    "21-1": "String",
    "21-2": "bottom",
    "21-3": "No",
    "21-4": "Position of the play button. Valid values: `bottom` (on the controls bar); `center` (in the middle of the video).",
    "22-0": "enable-play-gesture",
    "22-1": "Boolean",
    "22-2": "false",
    "22-3": "No",
    "22-4": "Whether to enable playback gesture, i.e., double-click for play/pause.",
    "23-0": "auto-pause-if-navigate",
    "23-1": "Boolean",
    "23-2": "true",
    "23-3": "No",
    "23-4": "Whether to automatically pause the video on the current page when another mini app page is redirected to.",
    "24-0": "bindplay",
    "24-1": "Event Handler",
    "24-2": "",
    "24-3": "No",
    "24-4": "The `play` event triggered when playback is started/resumed.",
    "25-0": "bindpause",
    "25-1": "Event Handler",
    "25-2": "",
    "25-3": "No",
    "25-4": "The `pause` event triggered when playback is paused.",
    "26-0": "bindended",
    "26-1": "Event Handler",
    "26-2": "",
    "26-3": "No",
    "26-4": "The `ended` event triggered when playback reaches the end. ",
    "27-0": "bindtimeupdate",
    "27-1": "Event Handler",
    "27-2": "",
    "27-3": "No",
    "27-4": "Event triggered when the playback progress changes: `event.detail = {currentTime, duration}`; trigger frequency: once every 250 ms.",
    "28-0": "bindfullscreenchange",
    "28-1": "Event Handler",
    "28-2": "",
    "28-3": "No",
    "28-4": "Event triggered when the video enters/exits the full screen mode: `event.detail = {fullScreen, direction}`. Valid values: `vertical`, `horizontal`.",
    "29-0": "bindwaiting",
    "29-1": "Event Handler",
    "29-2": "",
    "29-3": "No",
    "29-4": "The event triggered when the video buffers.",
    "30-0": "binderror",
    "30-1": "Event Handler",
    "30-2": "",
    "30-3": "No",
    "30-4": "The event triggered when an error occurs during video playback.",
    "31-0": "bindprogress",
    "31-1": "Event Handler",
    "31-2": "",
    "31-3": "No",
    "31-4": "The event triggered when the loading progress changes. Only one-stage loading is supported.  \n`event.detail = {buffered}`; this parameter is a percentage value."
  },
  "cols": 5,
  "rows": 32,
  "align": [
    "left",
    "left",
    "left",
    "left",
    "left"
  ]
}
[/block]


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
