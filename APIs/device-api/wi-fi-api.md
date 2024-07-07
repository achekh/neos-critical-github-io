---
title: "Wi-Fi"
slug: "wi-fi-api"
excerpt: "This section consists of list of Wi-Fi related APIs."
hidden: false
createdAt: "Mon Apr 24 2023 07:08:15 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Wed Nov 29 2023 17:59:29 GMT+0000 (Coordinated Universal Time)"
layout: "default"
parent: "Device"
grand_parent: "APIs"
nav_order: 3
---
# Wi-Fi 
This section consists of list of Wi-Fi related APIs.

***

- [onWifiConnected](wi-fi-api#wxonwificonnectedfunction-listener)
- [offWifiConnected](wi-fi-api#wxoffwificonnectedfunction-listener)
- [WifiInfo](wi-fi-api#wifiinfo)

# wx.onWifiConnected(function listener)

Listens for the Wi-Fi connection event.

# Parameters

## Function listener

Listener function for the Wi-Fi connection event.

# Parameters

**Object res**

| Attribute | Type     | Description       |
| :-------- | :------- | :---------------- |
| wifi      | WifiInfo | Wi-Fi information |

# wx.offWifiConnected(function listener)

Unlistens for the Wi-Fi connection event.

# Parameters

## Function listener

The listener function passed in when `onWifiConnected` is called. If this parameter is not passed in, all listener functions will be removed.

### Sample code

```javascript
// JavaScript
const listener = function (res) { console.log(res) }

wx.onWifiConnected(listener)
wx.offWifiConnected(listener) // You should pass in the same function object as for the listener.
```

# WifiInfo

Wi-Fi information

## Attributes

### string SSID

Wi-Fi SSID

### string BSSID

Wi-Fi BSSID

### boolean secure

Wi-Fi security

### number signalStrength

Wi-Fi signal strength. Value range: 0–100 for Android or 0–1 for iOS. The larger the value, the stronger the signal.

### number frequency

Wi-Fi frequency band in MHz

> 📘 Notes
> 
> - On Android, if `partialInfo:true` is set for `wx.connectWifi / wx.getConnectedWifi` , or the `wx.onWifiConnectedWithPartialInfo` event is called, a`WifiInfo` object containing only the SSID attribute will be returned.
> - On iOS, if `partialInfo:true` is set for `wx.getConnectedWifi`, a `WifiInfo` object containing only SSID and BSSID attributes will be returned, and the result can be properly returned only if the user grants the app location permission.
> - In some cases, even if the Wi-Fi connection is successful, an error may still be reported because no complete WifiInfo object can be obtained.  
>   The specific error message is `errCode: 12010`, `errMsg: can't gain current wifi` or `no wifi is connected`. If the developer does not need the complete `WifiInfo` object, the error can be solved by adopting the above strategy.
