---
title: "Performance Analysis Tools"
slug: "performance-analysis-tools"
excerpt: "This section explains the concept of performance analysis tools."
hidden: true
metadata: 
  robots: "index"
createdAt: "Tue May 09 2023 06:17:53 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Tue May 30 2023 05:27:41 GMT+0000 (Coordinated Universal Time)"
layout: "default"
parent: "Performance and Experience"
grand_parent: "Guide"
---
## performance Trace tool

The Trace export tool is provided to developers that they can use in the developer tool Trace Panel.

## Use method

1. You need to install the adb tool on the PC first, you can refer to some mainstream tutorials to install, and you can use brew to install it directly on the Mac.
2. After making sure that the adb tool has been successfully installed, open the Trace Panel on the developer tools, connect the Android phone to the PC via USB, click "Choose Devices", at this time the connection authorization box may pop up on the phone, click "Allow".
3. After selecting the device, open the development version Mini Program you need to debug on the mobile phone, and open the performance monitoring panel through the upper-right menu to restart the Mini Program.
4. After restarting, perform operations on the Mini Program, and after completing the operation, export the Trace data through the menu in the upper right corner.
5. At this time, the Trace file will be automatically pulled on the Trace Panel of the developer tool, select the Trace file you want to analyze.

> You can use the adb devices command to determine if a device is connected to a PC

![](https://files.readme.io/bc4a495-small-134cfb9-37.translated.jpg)

## Performance Panel

From WeChat 6.5.8 To begin with, we provide a performance panel that lets developers understand how Mini Programs perform. Developers can open the performance panel under the development version Mini Program. How to open it: Enter the development edition Mini Program, enter the top right corner more ons, clickDisplay Performance Window.

![](https://files.readme.io/6eb06a8-small-3064489-38.translated.jpg)

## Performance Panel Metrics Dxplaination

| index                          | Explanation                                                                                                                           |
| :----------------------------- | :------------------------------------------------------------------------------------------------------------------------------------ |
| CPU                            | Mini Program process CPU Occupancy, only Android Under offers                                                                         |
| Memory                         | Memory footprint of the Mini Program process (Total Pss), only Android Under offers                                                   |
| Time to start                  | Total time spent on Mini Program startup                                                                                              |
| Downloading is time-consuming  | Mini Programs are time-consuming to download and will be downloaded when they are first opened or when a resource pack needs updating |
| Page switching time-consuming  | Time Consuming for Mini Program Page Switching                                                                                        |
| frame rate/FPS                 |                                                                                                                                       |
| First rendering time consuming | Time consuming for page first rendering                                                                                               |
| Rendering again time-consuming | Time consuming for the page to render again (usually by the developer's setData Operation trigger)                                    |
| Data cache                     | Mini Program passes Storage Cache size stored by interface                                                                            |
