---
title: "Bluetooth"
slug: "bluetooth-api"
excerpt: "`This section displays list of Bluetooth related APIs for the Mini App."
hidden: false
createdAt: "Fri Apr 21 2023 10:44:55 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Wed Nov 29 2023 13:48:32 GMT+0000 (Coordinated Universal Time)"
layout: "default"
parent: "Device"
grand_parent: "APIs"
---
- [openBluetoothAdapter](doc:bluetooth-api#wxopenbluetoothadapterobject-object)
- [getConnectedBluetoothDevices](doc:bluetooth-api#wxgetconnectedbluetoothdevicesobject-object)
- [getBluetoothDevices](doc:bluetooth-api#wxgetbluetoothdevicesobject-object)
- [getBluetoothAdapterState](doc:bluetooth-api#wxgetbluetoothadapterstateobject-object)
- [closeBluetoothAdapter](doc:bluetooth-api#wxclosebluetoothadapterobject-object)

# wx.openBluetoothAdapter(Object object)

Initializes the Bluetooth module. This API is called only once when the central device/peripheral mode is enabled on iOS respectively, and the corresponding `mode` needs to be specified.

# Parameters

**Object object**

[block:parameters]
{
  "data": {
    "h-0": "Attribute",
    "h-1": "Type",
    "h-2": "Valid Value",
    "h-3": "Default",
    "h-4": "Required",
    "h-5": "Description",
    "0-0": "mode",
    "0-1": "String",
    "0-2": "`central`  \n`peripheral`",
    "0-3": "central",
    "0-4": "No",
    "0-5": "Bluetooth mode, which can be central or peripheral mode and is required for iOS only.",
    "1-0": "success",
    "1-1": "Function",
    "1-2": "",
    "1-3": "",
    "1-4": "No",
    "1-5": "Callback function for successful API call.",
    "2-0": "fail",
    "2-1": "Function",
    "2-2": "",
    "2-3": "",
    "2-4": "No",
    "2-5": "Callback function for failed API call.",
    "3-0": "complete",
    "3-1": "Function",
    "3-2": "",
    "3-3": "",
    "3-4": "No",
    "3-5": "Callback function for API call end (executed for both successful and failed calls)."
  },
  "cols": 6,
  "rows": 4,
  "align": [
    "left",
    "left",
    "left",
    "left",
    "left",
    "left"
  ]
}
[/block]


## Error codes

| Error Code | Error Message        | Description                                                                               |
| :--------- | :------------------- | :---------------------------------------------------------------------------------------- |
| 0          | ok                   | Normal                                                                                    |
| -1         | already connect      | Connected                                                                                 |
| 10000      | not init             | The Bluetooth adapter is not initialized.                                                 |
| 10001      | not available        | Currently, the Bluetooth adapter is unavailable.                                          |
| 10002      | no device            | The specified device was not found.                                                       |
| 10003      | connection fail      | Connection failed.                                                                        |
| 10004      | no service           | The specified service was not found.                                                      |
| 10005      | no characteristic    | The specified characteristic was not found.                                               |
| 10006      | no connection        | The connection is closed.                                                                 |
| 10007      | property not support | The operation is not supported for the current characteristic.                            |
| 10008      | system error         | Other exceptions reported by the system                                                   |
| 10009      | system not support   | The system version is earlier than 4.3 and does not support Bluetooth (for Android only). |
| 10012      | operate time out     | Connection timed out.                                                                     |
| 10013      | invalid_data         | The connection `deviceId` is empty or in an incorrect format.                             |

## `state` parameter returned by the `object.fail` callback function (for iOS only).

| Status Code | Description  |
| :---------- | :----------- |
| 0           | Unknown      |
| 1           | Resetting    |
| 2           | Unsupported  |
| 3           | Unauthorized |
| 4           | Disabled     |

> 📘 Notes
> 
> - Other Bluetooth APIs can be used only after [wx.openBluetoothAdapter()] is called. Otherwise, they will return an error ( errCode=10000 ).
> - If the user turns off Bluetooth or the phone does not support Bluetooth, an error ( errCode=10001 ) will be returned when [wx.openBluetoothAdapter](doc:bluetooth-api#wxopenbluetoothadapterobject-object) is called, indicating that the Bluetooth feature is unavailable on the phone. At this point, the Mini App Bluetooth module is intialized.

### Sample code

```javascript JavaScript
wx.openBluetoothAdapter({
  success (res) {
  	console.log(res)
  }
})
```

# wx.getConnectedBluetoothDevices(Object object)

Gets the connected Bluetooth device based on the UUID of the primary service.

# Parameters

**Object object**

| Attribute | Type          | Required | Description                                                                                                           |
| :-------- | :------------ | :------- | :-------------------------------------------------------------------------------------------------------------------- |
| services  | Array<string> | Yes      | List of UUIDs of primary services connected to the Bluetooth device (16-bit, 32-bit and 128-bit UUIDs are supported). |
| success   | Function      | No       | Callback function for successful API call.                                                                            |
| fail      | Function      | No       | Callback function for failed API call.                                                                                |
| complete  | Function      | No       | Callback function for API call end (executed for both successful and failed calls).                                   |

`object.success` callback function

# Parameters

Object res

| Object res | Type          | Description           |
| :--------- | :------------ | :-------------------- |
| devices    | Array<Object> | List of found devices |

| Structure Attribute | Type   | Description                                                          |
| :------------------ | :----- | :------------------------------------------------------------------- |
| name                | String | Bluetooth device name, which may not be present for certain devices. |
| deviceId            | String | Device ID                                                            |

## Error codes

| Error Code | Error Message        | Description                                                                         |
| :--------- | :------------------- | :---------------------------------------------------------------------------------- |
| 0          | ok                   | Normal                                                                              |
| -1         | already connect      | Connected                                                                           |
| 10000      | not init             | The Bluetooth adapter is not initialized.                                           |
| 10001      | not available        | Currently, the Bluetooth adapter is unavailable.                                    |
| 10002      | no device            | The specified device was not found.                                                 |
| 10003      | connection fail      | Connection failed.                                                                  |
| 10004      | no service           | The specified service was not found.                                                |
| 10005      | no characteristic    | The specified characteristic was not found.                                         |
| 10006      | no connection        | The connection is closed.                                                           |
| 10007      | property not support | The operation is not supported for the current characteristic.                      |
| 10008      | system error         | Other exceptions reported by the system.                                            |
| 10009      | system not support   | The system version is earlier than 4.3 and does not support BLE (for Android only). |
| 10012      | operate time out     | Connection timed out.                                                               |
| 10013      | invalid_data         | The connection `deviceId` is empty or in an incorrect format.                       |

### Sample code

```javascript JavaScript
wx.getConnectedBluetoothDevices({
  services: ['FEE7'],
  success (res) {
 	 console.log(res)
  }
})
```

# wx.getBluetoothDevices(Object object)

Gets all the Bluetooth devices found when the Bluetooth module is in effect, including those already connected to the local device.

# Parameters

**Object object**

| Attribute | Type     | Required | Description                                                                        |
| :-------- | :------- | :------- | :--------------------------------------------------------------------------------- |
| success   | Function | No       | Callback function for successful API call                                          |
| fail      | Function | No       | Callback function for failed API call                                              |
| complete  | Function | No       | Callback function for API call end (executed for both successful and failed calls) |

`object.success` callback function

# Parameters

**Object res**

| Attribute | Type           | Description                        |
| :-------- | :------------- | :--------------------------------- |
| devices   | Array.<Object> | List of UUIDs of connected devices |

[block:parameters]
{
  "data": {
    "h-0": "Structure Attribute",
    "h-1": "Type",
    "h-2": "Description",
    "0-0": "name",
    "0-1": "String",
    "0-2": "Bluetooth device name, which may not be present for certain devices.",
    "1-0": "deviceId",
    "1-1": "String",
    "1-2": "Bluetooth device ID.",
    "2-0": "RSSI",
    "2-1": "Number",
    "2-2": "Signal strength of the current Bluetooth device in dBm.",
    "3-0": "advertisData",
    "3-1": "ArrayBuffer",
    "3-2": "The `ManufacturerData` data segment in the broadcast data segment of the current Bluetooth device.",
    "4-0": "advertisServiceU  \nUIDs",
    "4-1": "Array.<string>",
    "4-2": "The `ServiceUUIDs` data segment in the broadcast data segment of the current Bluetooth device.",
    "5-0": "localName",
    "5-1": "String",
    "5-2": "The `LocalName` data segment in the broadcast data segment of the current Bluetooth device.",
    "6-0": "serviceData",
    "6-1": "Object",
    "6-2": "The `ServiceData` data segment in the broadcast data segment of the current Bluetooth device.",
    "7-0": "connectable",
    "7-1": "Boolean",
    "7-2": "Whether the current Bluetooth device can be connected (this value cannot be returned for Android versions earlier than 8.0)."
  },
  "cols": 3,
  "rows": 8,
  "align": [
    "left",
    "left",
    "left"
  ]
}
[/block]


## Error codes

| Error Code | Error Message        | Description                                                                         |
| :--------- | :------------------- | :---------------------------------------------------------------------------------- |
| 0          | ok                   | Normal                                                                              |
| -1         | already connect      | Connected                                                                           |
| 10000      | not init             | The Bluetooth adapter is not initialized.                                           |
| 10001      | not available        | Currently, the Bluetooth adapter is unavailable.                                    |
| 10002      | no device            | The specified device was not found.                                                 |
| 10003      | connection fail      | Connection failed.                                                                  |
| 10004      | no service           | The specified service was not found.                                                |
| 10005      | no characteristic    | The specified characteristic was not found.                                         |
| 10006      | no connection        | The connection is closed.                                                           |
| 10007      | property not support | The operation is not supported for the current characteristic.                      |
| 10008      | system error         | Other exceptions reported by the system                                             |
| 10009      | system not support   | The system version is earlier than 4.3 and does not support BLE (for Android only). |
| 10012      | operate time out     | Connection timed out.                                                               |
| 10013      | invalid_data         | The connection `deviceId` is empty or in an incorrect format.                       |

### Sample code

```javascript JavaScript
// Example of converting ArrayBuffer to a hex string
function ab2hex(buffer) {
  var hexArr = Array.prototype.map.call(
    new Uint8Array(buffer),
    function(bit) {
   		 return ('00' + bit.toString(16)).slice(-2)
    }
  )
  return hexArr.join('');
}
wx.getBluetoothDevices({
  success: function (res) {
    console.log(res)
    if (res.devices[0]) {
    	console.log(ab2hex(res.devices[0].advertisData))
    }
  }
})
```

> 📘 Note
> 
> - This API gets the list of all the Bluetooth devices found when the Bluetooth module is in effect. If `wx.closeBluetoothAdapter()` is not called promptly to release resources after the Bluetooth module is used, Bluetooth devices previously found may be returned when this API is called, which, however, are not nearby and cannot be connected.

# wx.getBluetoothAdapterState(Object object)

Gets the status of the local Bluetooth adapter.

# Parameters

**Object object**

| Attribute | Type     | Required | Description                                                                         |
| :-------- | :------- | :------- | :---------------------------------------------------------------------------------- |
| success   | Function | No       | Callback function for successful API call.                                          |
| fail      | Function | No       | Callback function for failed API call.                                              |
| complete  | Function | No       | Callback function for API call end (executed for both successful and failed calls). |

`object.success` callback function

# Parameters

**Object res**

| Attribute   | Type    | Description                                  |
| :---------- | :------ | :------------------------------------------- |
| discovering | Boolean | Whether the system is searching for devices. |
| available   | Boolean | Whether the Bluetooth adapter is available.  |

## Error codes

| Error Code | Error Message        | Description                                                                         |
| :--------- | :------------------- | :---------------------------------------------------------------------------------- |
| 0          | ok                   | Normal                                                                              |
| -1         | already connect      | Connected                                                                           |
| 10000      | not init             | The Bluetooth adapter is not initialized.                                           |
| 10001      | not available        | Currently, the Bluetooth adapter is unavailable.                                    |
| 10002      | no device            | The specified device was not found.                                                 |
| 10003      | connection fail      | Connection failed.                                                                  |
| 10004      | no service           | The specified service was not found.                                                |
| 10005      | no characteristic    | The specified characteristic was not found.                                         |
| 10006      | no connection        | The connection is closed.                                                           |
| 10007      | property not support | The operation is not supported for the current characteristic.                      |
| 10008      | system error         | Other exceptions reported by the system                                             |
| 10009      | system not support   | The system version is earlier than 4.3 and does not support BLE (for Android only). |
| 10012      | operate time out     | Connection timed out.                                                               |
| 10013      | invalid_data         | The connection `deviceId` is empty or in an incorrect format.                       |

### Sample code

```javascript JavaScript
wx.getBluetoothAdapterState({
  success (res) {
  	console.log(res)
  }
})
```

# wx.closeBluetoothAdapter(Object object)

Disables the Bluetooth module. Calling this method will close all the established connections and release system resources. We recommend you call it together with [wx.openBluetoothAdapter](doc:bluetooth-api#wxopenbluetoothadapterobject-object) after using the Bluetooth module.

# Parameters

**Object object**

| Attribute | Type     | Required | Description                                                                         |
| :-------- | :------- | :------- | :---------------------------------------------------------------------------------- |
| success   | Function | No       | Callback function for successful API call.                                          |
| fail      | Function | No       | Callback function for failed API call.                                              |
| complete  | Function | No       | Callback function for API call end (executed for both successful and failed calls). |

## Error codes

| Error Code | Error Message        | Description                                                                         |
| :--------- | :------------------- | :---------------------------------------------------------------------------------- |
| 0          | ok                   | Normal                                                                              |
| -1         | already connect      | Connected                                                                           |
| 10000      | not init             | The Bluetooth adapter is not initialized.                                           |
| 10001      | not available        | Currently, the Bluetooth adapter is unavailable.                                    |
| 10002      | no device            | The specified device was not found.                                                 |
| 10003      | connection fail      | Connection failed.                                                                  |
| 10004      | no service           | The specified service was not found.                                                |
| 10005      | no characteristic    | The specified characteristic was not found.                                         |
| 10006      | no connection        | The connection is closed.                                                           |
| 10007      | property not support | The operation is not supported for the current characteristic.                      |
| 10008      | system error         | Other exceptions reported by the system                                             |
| 10009      | system not support   | The system version is earlier than 4.3 and does not support BLE (for Android only). |
| 10012      | operate time out     | Connection timed out.                                                               |
| 10013      | invalid_data         | The connection `deviceId` is empty or in an incorrect format.                       |

### Sample code

```javascript JavaScript
wx.closeBluetoothAdapter({
  success (res) {
    console.log(res)
  }
})
```
