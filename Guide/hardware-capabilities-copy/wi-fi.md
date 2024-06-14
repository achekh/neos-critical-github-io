---
title: "Wi-Fi"
slug: "wi-fi"
excerpt: "This section explains the concept of Wi-Fi in Mini App."
hidden: true
metadata: 
  robots: "index"
createdAt: "Mon May 08 2023 07:59:40 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Mon May 29 2023 07:17:32 GMT+0000 (Coordinated Universal Time)"
layout: "default"
parent: "Hardware Capabilities"
grand_parent: "Guide"
---
# Wi-Fi 
*** 
In the Mini Program, it supports searching for peripheral Wi-Fi devices, and you can initiate a connection for the specified device and pass in the password.

This series of interfaces is system native capability. If you want to seeWeChat with Wi-FiAbility and configuration jump Mini Program, please refer to document。

## Connect to the specified Wi-Fi Device

If you know the Wi-Fi device name and password and confirm that the device is nearby, you can connect to the specified Wi-Fi directly in the applet.

The interface call sequence is:

1. startWifi: Initializes the Wi-Fi module.
2. connectWifi: Connect to Wi-Fi (iOS 11 and above).
3. onWifiConnected: An event for connecting to Wi-Fi.

## Connect to the peripheral Wi-Fi devices

The applet allows users to choose a Wi-Fi device to connect to by scanning nearby Wi-Fi devices.

Due to system limitations, the timing of interface calls varies on different platforms:

### For Android

1. startWifi: Initializes the Wi-Fi module.
2. getWifiList: Requests a list of surrounding Wi-Fi.
3. onGetWifiList: Get Wi-Fi list data events.
4. connectWifi: Connect to Wi-Fi.
5. onWifiConnected: Event callback for connecting to Wi-Fi.

### For iOS（iOS 11.0 and 11.1 versions are temporarily not supported for system reasons)\*\*

1. startWifi: Initializes the Wi-Fi module.
2. getWifiList: Requests a list of surrounding Wi-Fi. This interface will jump to the WeChat setting page in the system settings, and the user needs to be guided to the "Wireless LAN" setting page to manually connect the device. (iOS 11.0 and 11.1 versions fail due to system issues).
3. onGetWifiList: Get Wi-Fi list data events.
4. setWifiList: Sets information about the AP in the Wi-Fi list to assist users in connecting.
5. onWifiConnected: Event callback for connecting to Wi-Fi.

> 📘 Note
> 
> - Android system version 6.0 or above, when the positioning switch is not turned on, the device will not be able to obtain the surrounding Wi-Fi information normally.
> - Wi-Fi related interfaces are not available for use with the wx.canIUse interface.
