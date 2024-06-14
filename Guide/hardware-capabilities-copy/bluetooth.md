---
title: "Bluetooth"
slug: "bluetooth"
excerpt: "This section explains the concept of use of Bluetooth in Mini App."
hidden: true
metadata: 
  robots: "index"
createdAt: "Mon May 08 2023 07:59:35 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Mon May 29 2023 06:21:04 GMT+0000 (Coordinated Universal Time)"
layout: "default"
parent: "Hardware Capabilities"
grand_parent: "Guide"
---
# Bluetooth 
*** 
To use the Bluetooth functionality in the applet, you must first call wx.openBluetoothAdapter to initialize the Bluetooth adapter module. This must be done before calling wx.closeBluetoothAdapter or the applet will be destroyed. 

The developer can use the Bluetooth-related Mini Program API normally and receive event callbacks related to the Bluetooth module only while the Bluetooth adapter module of the Mini Program is active (binding listeners are exempt from this restriction).

> 🚧 Be careful
> 
> - Each Bluetooth peripheral is identified by a unique `deviceId`. Due to the limitations of some system implementations, the `deviceId`obtained by scanning different central devices may vary for the same Bluetooth peripheral. Therefore, the deviceId cannot be hard-coded into the code.
> - The deviceId obtained by scanning on the Android device is the MAC address of the peripheral device, which is relatively fixed.
> - The iOS device's `deviceId`, which is discovered through scanning, is a UUID that the system creates using the peripheral device's MAC address and the moment it was found. The UUID for connected devices stays constant for a while. The UUID can also change under specific circumstances (such as the system Bluetooth module restarting, the paired device being disregarded, etc.), and it differs depending on the device from which it is obtained.

## Debugging

Bluetooth implementations also vary widely across platforms. On the basis of providing a unified interface, the Mini Program will provide complete system Bluetooth capabilities as much as possible, weakening the implementation differences of different platforms.

However, due to the limitations of the operating system itself, some capabilities cannot be guaranteed to be completely consistent, please pay attention to the precautions in the document, and debug the real machine on each end. Only part of the Bluetooth interface capability can be simulated on the developer tool, and the full function should be debugged by the real machine.
