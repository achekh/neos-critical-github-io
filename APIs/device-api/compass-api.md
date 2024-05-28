---
title: "Compass"
slug: "compass-api"
excerpt: "This section lists the Compass related APIs."
hidden: false
createdAt: "Mon Apr 24 2023 08:34:19 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Wed Nov 29 2023 18:05:43 GMT+0000 (Coordinated Universal Time)"
layout: "default"
parent: "Device"
grand_parent: "APIs"
---
- [stopCompass](doc:compass-api#wxstopcompassobject-object)
- [startCompass](doc:compass-api#wxstartcompassobject-object)
- [onCompassChange](doc:compass-api#wxoncompasschangefunction-callback)
- [offCompassChange](doc:compass-api#wxoffcompasschangefunction-listener)

# wx.startCompass(Object object)

Listens for compass data.

# Parameters

**Object object**

| Attribute | Type     | Required | Description                                                                         |
| :-------- | :------- | :------- | :---------------------------------------------------------------------------------- |
| success   | Function | No       | Callback function for successful API call.                                          |
| fail      | Function | No       | Callback function for failed API call.                                              |
| complete  | Function | No       | Callback function for API call end (executed for both successful and failed calls). |

### Sample code

```javascript JavaScript
wx.startCompass()
```

# wx.stopCompass(Object object)

Unlistens for compass data.

## Parameters

**Object object**

| Attribute | Type     | Required | Description                                                                         |
| :-------- | :------- | :------- | :---------------------------------------------------------------------------------- |
| success   | Function | No       | Callback function for successful API call.                                          |
| fail      | Function | No       | Callback function for failed API call.                                              |
| complete  | Function | No       | Callback function for API call end (executed for both successful and failed calls). |

### Sample code

```javascript JavaScript
wx.stopCompass()
```

# wx.onCompassChange(function callback)

Listens for the compass data change event five times per second. Listening will start automatically after this API is called and can be stopped by calling `wx.stopCompass`.

## Parameters

## Function callback

Callback function for the compass data change event.

# Parameters\*\*

**Object res**

| Attribute | Type          | Description                    |
| :-------- | :------------ | :----------------------------- |
| direction | Number        | Degree in the faced direction. |
| accuracy  | Number/String | Accuracy.                      |

### Sample code

```javascript JavaScript
wx.onCompassChange(function (res) {
	console.log(res.direction)
})
```

## Accuracy differences between iOS and Android

Due to platform differences, `accuracy` has different values on iOS and Android.

- **iOS**: accuracy is a value of number type indicating the deviation from the magnetic north pole. 0 means that the device is pointing to magnetic north, 90 east, 180 south, and so on.
- **Android**:` accuracy` is an enumerated value of string type.

| Value           | Description                                                                                                                                             |
| :-------------- | :------------------------------------------------------------------------------------------------------------------------------------------------------ |
| high            | High accuracy.                                                                                                                                          |
| medium          | Medium accuracy.                                                                                                                                        |
| low             | Low accuracy.                                                                                                                                           |
| no-contact      | Untrusted as the sensor lost connection.                                                                                                                |
| unreliable      | Untrusted for unknown reasons.                                                                                                                          |
| unknow ${value} | Unknown enumerated accuracy value; that is, the accuracy value returned by the Android system at this time is not a standard enumerated accuracy value. |

# wx.offCompassChange(function listener)

Unlistens for the compass data change event.

# Parameters

## Function listener

The listener function passed in when `onCompassChange` is called. If this parameter is not passed in, all listener functions will be removed.

### Sample code

```javascript JavaScript
const listener = function (res) { console.log(res) }

wx.onCompassChange(listener)
wx.offCompassChange(listener) // You should pass in the same function object as for the listener.
```
