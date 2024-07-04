---
title: "Audio"
slug: "audio"
excerpt: "This section consists of the list of Audio related APIs for Mini App."
hidden: false
createdAt: "Thu Apr 20 2023 10:19:31 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Wed Nov 29 2023 13:10:51 GMT+0000 (Coordinated Universal Time)"
layout: "default"
parent: "Media"
grand_parent: "APIs"
nav_order: 3
---
# Audio 
This section consists of the list of Audio related APIs for Mini App.

***

- [createInnerAudioContext](audio#inneraudiocontext-wxcreateinneraudiocontext)
- [InnerAudioContext](audio#inneraudiocontext)

## [InnerAudioContext](audio#inneraudiocontext) wx.createInnerAudioContext()

Creates an [`InnerAudioContext`](audio#inneraudiocontext) object of the internal `audio `.

## Returned value

[InnerAudioContext](audio)

## .pause

## AudioContext.pause()

Pauses the audio.

## .seek

## AudioContext.seek(number position)

Seeks to the specified position.

# Parameters

**number position**

Seek position in s

## .setSrc

## AudioContext.setSrc(string src)

Sets the audio address.

# Parameters

**string src**

Audio address

## wx.setInnerAudioOption(Object object)

Sets the playback options for [InnerAudioContext](audio#inneraudiocontext). The settings take effect globally for the current mini app.

# Parameters

**Object object**

| Attribute | Type | Default | Required | Description |
| :-------- | :--- | :------ | :------- | :---------- |
| mixWithOther | Boolean | true | No | Whether to allow the audio to play together with other audios. If this parameter is set to `true`,  \nthe audio of another app won't be stopped. |
| obeyMute  \nSwitch | Boolean | true | No | (For iOS only) Whether to follow the mute switch. If this parameter is set to `false` , the audio can be played back even in muted mode. |
| success | Function |  | No | Callback function for successful API call |
| fail | Function |  | No | Callback function for failed API call |
| complete | Function |  | No | Callback function for API call end (executed for both successful and failed calls) |


- InnerAudioContext
  - destroy
  - offCanplay
  - offEnded
  - offError
  - offPause
  - offPlay
  - offSeeked
  - offSeeking
  - offStop
  - offTimeUpdate
  - offWaiting
  - onCanplay
  - onEnded
  - onError
  - onPause
  - onPlay
  - onSeeked
  - onSeeking
  - onStop
  - onTimeUpdate
  - onWaiting
  - pause
  - play
  - seek
  - stop

# InnerAudioContext

[`InnerAudioContext` instance, which can be obtained through the wx.createInnerAudioContext](audio#inneraudiocontext) API.

## Attributes

### string src

Address of the audio resource, which is used for direct playback. Cloud file IDs are supported.

### number startTime

Start position in s. Default value: `0` .

### boolean autoplay

Whether to start playback automatically. Default value: `false `.

### boolean loop

Whether to loop. Default value:` false` .

### number volume

Volume. Value range: 0–1. Default value: `1` .

### number duration

Length of the current audio in s, which is returned only if there currently is a valid `src` (read-only).

### number currentTime

Playback position of the current audio in s, which is returned only if there currently is a valid `src` and is rounded to six decimal places (read-only).

### boolean paused

Whether the audio is currently paused or stopped (read-only)

### number buffered

Time point for audio buffering (read-only). The system only guarantees that the content from the current playback time point to this time point has been buffered.

## Methods

- [InnerAudioContext.play()](audio#play)  
  Plays the audio.
- [InnerAudioContext.pause()](audio#pause-1)  
  Pauses the audio. The audio will start playing from where paused when it is resumed.
- [InnerAudioContext.stop()](audio#stop)  
  Stops the audio. The audio will start playing from the beginning when it is played back again.
- [InnerAudioContext.seek(number position)](audio#inneraudiocontextseeknumber-position)  
  Seeks to the specified position.
- [InnerAudioContext.destroy()](audio#destroy)  
  Terminates the current instance.
- [InnerAudioContext.onCanplay(function callback)](audio#inneraudiocontextoncanplayfunction-callback)  
  Listens for the event that the audio enters the playable status. However, this doesn't guarantee that the audio can play smoothly.
- [InnerAudioContext.offCanplay(function callback)](audio#inneraudiocontextoffcanplayfunction-callback)  
  Unlistens for the event that the audio enters the playable status.
- [InnerAudioContext.onPlay(function callback)](audio#inneraudiocontextonplayfunction-callback)  
  Listens for the audio play event.
- [InnerAudioContext.offPlay(function callback)](audio#inneraudiocontextoffplayfunction-callback)  
  Unlistens for the audio play event.
- [InnerAudioContext.onPause(function callback)](audio#inneraudiocontextonpausefunction-callback)  
  Listens for the audio pause event.
- [InnerAudioContext.offPause(function callback)](audio#inneraudiocontextoffpausefunction-callback)  
  Unlistens for the audio pause event.
- [InnerAudioContext.onStop(function callback)](audio#inneraudiocontextonstopfunction-callback)  
  Listens for the audio stop event.
- [InnerAudioContext.offStop(function callback)](audio#inneraudiocontextoffstopfunction-callback)  
  Unlistens for the audio stop event.
- [InnerAudioContext.onEnded(function callback)](audio#inneraudiocontextonendedfunction-callback)  
  Listens for the event that the audio plays to the end.
- [InnerAudioContext.offEnded(function callback)](audio#inneraudiocontextoffendedfunction-callback)  
  Unlistens for the event that the audio plays to the end.
- [InnerAudioContext.onTimeUpdate(function callback)](audio#inneraudiocontextontimeupdatefunction-callback)  
  Listens for the audio playback progress update event.
- [InnerAudioContext.offTimeUpdate(function callback)](audio#inneraudiocontextofftimeupdatefunction-callback)  
  Unlistens for the audio playback progress update event.
- [InnerAudioContext.onError(function callback)](audio#inneraudiocontextonerrorfunction-callback)  
  Listens for the audio play error event.
- [InnerAudioContext.offError(function callback)](audio#inneraudiocontextofferrorfunction-callback)  
  Unlistens for the audio play error event.
- [InnerAudioContext.onWaiting(function callback)](audio#inneraudiocontextonwaitingfunction-callback)  
  Listens for the audio loading event. This API is triggered when the audio needs to be loaded due to insufficient buffer data.
- [InnerAudioContext.offWaiting(function callback)](audio#offwaiting)  
  Unlistens for the audio loading event.
- [InnerAudioContext.onSeeking(function callback)](audio#onseeking)  
  Listens for the audio seek event.
- [InnerAudioContext.offSeeking(function callback)](audio#offseeking)  
  Unlistens for the audio seek event.
- [InnerAudioContext.onSeeked(function callback)](audio#onseeked)  
  Listens for the audio seek end event.
- [InnerAudioContext.offSeeked(function callback)](audio#offseeked)  
  Unlistens for the audio seek end event.

## Supported formats

| Format | iOS | Android |
| :----- | :-- | :------ |
| flac   | x   | √       |
| m4a    | √   | √       |
| ogg    | x   | √       |
| ape    | x   | √       |
| amr    | x   | √       |
| wma    | x   | √       |
| wav    | √   | √       |
| mp3    | √   | √       |
| mp4    | x   | √       |
| aac    | √   | √       |
| aiff   | √   | x       |
| caf    | √   | x       |

### Sample code

```javascript
// JavaScript
const innerAudioContext = wx.createInnerAudioContext()
innerAudioContext.autoplay = true
innerAudioContext.src = 'https://ws.stream.qqmusic.qq.com/M500001VfvsJ21xFqb.mp3?
guid=ffffffff82def4af4b12b3cd9337d5e7&uin=346897220&vkey=6292F51E1E384E061FF02C31F716658E5C81F5594D561F2E88B854E81CAAB7806D5E4F103E55D33C16F3F
AC506D1AB172DE8600B37E43FAD&fromtag=46'
innerAudioContext.onPlay(() => {
	console.log('Start playback')
})
innerAudioContext.onError((res) => {
  console.log(res.errMsg)
  console.log(res.errCode)
})
```

## .destroy

## InnerAudioContext.destroy()

Terminates the current instance.

## .offCanplay

## InnerAudioContext.offCanplay(function callback)

Unlistens for the event that the audio enters the playable status.

# Parameters

## Function callback

Callback function for the event that the audio enters the playable status

## .offEnded

## InnerAudioContext.offEnded(function callback)

Unlistens for the event that the audio plays to the end.

# Parameters

## Function callback

Callback function for the event that the audio plays to the end

## .offError

## InnerAudioContext.offError(function callback)

Unlistens for the audio play error event.

# Parameters

## Function callback

Callback function for the audio play error event

## .offPause

## InnerAudioContext.offPause(function callback)

Unlistens for the audio pause event.

# Parameters

## Function callback

Callback function for the audio pause event.

## .offPlay

## InnerAudioContext.offPlay(function callback)

Unlistens for the audio play event.

# Parameters

## Function callback

Callback function for the audio play event

## .offSeeked

## InnerAudioContext.offSeeked(function callback)

Unlistens for the audio seek end event.

# Parameters

## Function callback

Callback function for the audio seek end event

## .offSeeking

## InnerAudioContext.offSeeking(function callback)

Unlistens for the audio seek event.

# Parameters

## Function callback

Callback function for the audio seek event.

## .offStop

## InnerAudioContext.offStop(function callback)

Unlistens for the audio stop event.

# Parameters

## Function callback

Callback function for the audio stop event

## .offTimeUpdate

## InnerAudioContext.offTimeUpdate(function callback)

Unlistens for the audio playback progress update event.

# Parameters

## Function callback

Callback function for the audio playback progress update event

## .offWaiting

InnerAudioContext.offWaiting(function callback)

Unlistens for the audio loading event.

# Parameters

## Function callback

Callback function for the audio loading event.

## .onCanplay

## InnerAudioContext.onCanplay(function callback)

Listens for the event that the audio enters the playable status. However, this doesn't guarantee that the audio can play smoothly.

# Parameters

## Function callback

Callback function for the event that the audio enters the playable status.

## .onEnded

## InnerAudioContext.onEnded(function callback)

Listens for the event that the audio plays to the end.

# Parameters

## Function callback

Callback function for the event that the audio plays to the end.

## .onError

## InnerAudioContext.onError(function callback)

Listens for the audio play error event.

## Parameters

## Function callback

Callback function for the audio play error event.

# Parameters

**Object res**

| Attribute | Type   | Description |
| :-------- | :----- | :---------- |
| errCode   | Number |             |

**Valid values of `errCode`**

| Value | Description   |
| :---- | :------------ |
| 10001 | System error  |
| 10002 | Network error |
| 10003 | File error    |
| 10004 | Format error  |
| -1    | Unknown error |

## .onPause

## InnerAudioContext.onPause(function callback)

Listens for the audio pause event.

# Parameters

## Function callback

Callback function for the audio pause event.

## .onPlay

## InnerAudioContext.onPlay(function callback)

Listens for the audio play event.

# Parameters

## Function callback

Callback function for the audio play event.

## .onSeeked

## InnerAudioContext.onSeeked(function callback)

Listens for the audio seek end event.

# Parameters

## Function callback

Callback function for the audio seek end event.

## .onSeeking

## InnerAudioContext.onSeeking(function callback)

Listens for the audio seek event.

## Parameters

### function callback

Callback function for the audio seek event

## .onStop

## InnerAudioContext.onStop(function callback)

Listens for the audio stop event.

## Parameters

### function callback

Callback function for the audio stop event.

## .onTimeUpdate

## InnerAudioContext.onTimeUpdate(function callback)

Listens for the audio playback progress update event.

# Parameters

## Function callback

Callback function for the audio playback progress update event.

## .onWaiting

## InnerAudioContext.onWaiting(function callback)

Listens for the audio loading event. This API is triggered when the audio needs to be loaded due to insufficient buffer data.

# Parameters

# Function callback

Callback function for the audio loading event.

## .pause

## InnerAudioContext.pause()

Pauses the audio. The audio will start playing from where paused when it is resumed.

## .play

## InnerAudioContext.play()

Plays the audio.

## .seek

## InnerAudioContext.seek(number position)

Seeks to the specified position.

# Parameters

## Number position

Seek time in s, which is accurate to three decimal places; that is, ms-level accuracy is supported.

## .stop

## InnerAudioContext.stop()

Stops the audio. The audio will start playing from the beginning when it is played back again.
