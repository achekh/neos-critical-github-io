---
title: "Accelerometer"
slug: "accelerometer-api"
excerpt: "This section lists the Accelerometer related APIs."
hidden: false
createdAt: "Mon Apr 24 2023 08:28:22 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Wed Nov 29 2023 18:04:33 GMT+0000 (Coordinated Universal Time)"
layout: "default"
parent: "Device"
grand_parent: "APIs"
---
- [stopAccelerometer](doc:accelerometer-api#wxstopaccelerometerobject-object)
- [startAccelerometer](doc:accelerometer-api#wxstartaccelerometerobject-object)
- [onAccelerometerChange](doc:accelerometer-api#wxonaccelerometerchangefunction-callback)
- [offAccelerometerChange](doc:accelerometer-api#wxoffaccelerometerchangefunction-listener)

# wx.startAccelerometer(Object object)

Listens for accelerometer data.

# Parameters

**Object object**

| Attribute | Type     | Default | Required | Description                                                                        |
| :-------- | :------- | :------ | :------- | :--------------------------------------------------------------------------------- |
| interval  | String   | normal  | No       | Execution frequency of the callback function for accelerometer data listening      |
| success   | Function |         | No       | Callback function for successful API call                                          |
| fail      | Function |         | No       | Callback function for failed API call                                              |
| complete  | Function |         | No       | Callback function for API call end (executed for both successful and failed calls) |

Valid values of `object.interval`

| Value  | Description                                                              |
| :----- | :----------------------------------------------------------------------- |
| game   | Callback frequency suitable for game update, which is around 20 ms/time. |
| ui     | Callback frequency suitable for UI update, which is around 60 ms/time.   |
| normal | Normal callback frequency, which is around 200 ms/time.                  |

## Sample code

```javascript JavaScript
wx.startAccelerometer({
	interval: 'game'
})
```

> 📘 Notes
> 
> The value of `interva` may slightly differ from the actual execution frequency of the `[wx.onAccelerometerChange](<>)` callback function due to factors of device model performance and current CPU and memory utilizations.

# wx.stopAccelerometer(Object object)

Unlistens for accelerometer data.

## Parameters

**Object object**

| Attribute | Type     | Required | Description                                                                        |
| :-------- | :------- | :------- | :--------------------------------------------------------------------------------- |
| success   | Function | No       | Callback function for successful API call                                          |
| fail      | Function | No       | Callback function for failed API call                                              |
| complete  | Function | No       | Callback function for API call end (executed for both successful and failed calls) |

### Sample code

```javascript JavaScript
wx.stopAccelerometer()
```

# wx.onAccelerometerChange(function callback)

Listens for the accelerometer data event. The frequency is determined by the `interval` parameter of [wx.startAccelerometer()](<>). Listening can be stopped by calling [wx.stopAccelerometer().](<>)

# Parameters

## Function callback

Callback function for the accelerometer data event

# Parameters

**Object res**

| Attribute | Type   | Description |
| :-------- | :----- | :---------- |
| x         | Number | X axis.     |
| y         | Number | Y axis.     |
| z         | Number | Z axis.     |

# Sample code

```javascript JavaScript
wx.onAccelerometerChange(function (res) {
  console.log(res.x)
  console.log(res.y)
  console.log(res.z)
})
```

# wx.offAccelerometerChange(function listener)

Unlistens for the accelerometer data event.

# Parameters

## Function listener

The listener function passed in when `onAccelerometerChange` is called. If this parameter is not passed in, all listener functions will be removed.

### Sample code

```javascript JavaScript
const listener = function (res) { console.log(res) }

wx.onAccelerometerChange(listener)
wx.offAccelerometerChange(listener) // You should pass in the same function object as for the listener.
```
