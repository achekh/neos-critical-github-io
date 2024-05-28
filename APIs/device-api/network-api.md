---
title: "Network"
slug: "network-api"
excerpt: "This section lists the Network related APIs."
hidden: false
createdAt: "Mon Apr 24 2023 08:10:43 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Wed Nov 29 2023 18:01:54 GMT+0000 (Coordinated Universal Time)"
layout: "default"
parent: "Device"
grand_parent: "APIs"
---
- [onNetworkStatusChange](doc:network-api#wxonnetworkstatuschangefunction-callback)
- [getNetworkType](doc:network-api#wxgetnetworktypeobject-object)

# wx.onNetworkStatusChange(function callback)

Listens for the network status change event.

# Parameters

## Function callback

Callback function for the network status change event

# Parameters

**Object res**

| Attribute   | Type    | Description                                      |
| :---------- | :------ | :----------------------------------------------- |
| isConnected | Boolean | Whether there is a network connection currently. |
| networkType | String  | Network type.                                    |

Valid values of `networkType`

| Value   | Description                       |
| :------ | :-------------------------------- |
| wifi    | Wi-Fi network.                    |
| 2g      | 2G network.                       |
| 3g      | 3G network.                       |
| 4g      | 4G network.                       |
| unknown | Uncommon network type on Android. |
| none    | No network.                       |

### sample code

```javascript JavaScript
wx.onNetworkStatusChange(function (res) {
  console.log(res.isConnected)
  console.log(res.networkType)
})
```

# wx.getNetworkType(Object object)

Gets the network type.

# Parameters

**Object object**

| Attribute | Type     | Required | Description                                                                         |
| :-------- | :------- | :------- | :---------------------------------------------------------------------------------- |
| success   | Function | No       | Callback function for successful API call.                                          |
| fail      | Function | No       | Callback function for failed API call.                                              |
| complete  | Function | No       | Callback function for API call end (executed for both successful and failed calls). |

`object.success` callback function

# Parameters

Object res

| Attribute   | Type   | Description   |
| :---------- | :----- | :------------ |
| networkType | String | Network type. |

Valid values of `res.networkType`

| Value   | Description                       |
| :------ | :-------------------------------- |
| wifi    | Wi-Fi network.                    |
| 2g      | 2G network.                       |
| 3g      | 3G network.                       |
| 4g      | 4G network.                       |
| unknown | Uncommon network type on Android. |
| none    | No network.                       |

### Sample code

```javascript JavaScript
wx.getNetworkType({
  success(res) {
 	 const networkType = res.networkType
  }
})
```
