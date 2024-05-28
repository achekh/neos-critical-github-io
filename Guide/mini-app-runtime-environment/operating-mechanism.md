---
title: "Operating Mechanism"
slug: "operating-mechanism"
excerpt: "This section explains the concept of operating mechanism."
hidden: true
metadata: 
  robots: "index"
createdAt: "Tue May 02 2023 09:38:13 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Wed May 03 2023 10:17:20 GMT+0000 (Coordinated Universal Time)"
layout: "default"
parent: "Mini Program Runtime"
grand_parent: "Guide"
---
# Operating Mechanism of Mini Programs

## Startup of Mini Programs

Both "cold startup" and "hot startup" are available for Mini Programs.

- **Hot startup**: This refers to the process of switching a Mini Program running in the background to foreground when a user wants to re-open the opened Mini Program after a certain period of time;
- **Cold startup**: This occurs when a user opens a Mini Program for the first time or re-opens it after its termination by Weixin.

The concept re-startup is not applicable to Mini Programs.

## Foreground/Background Status

When a user taps the Mini Program control button in the top right corner to close a Mini Program or presses the home button on the mobile to leave the app, the Mini Program is not terminated but runs in the **background**.

When he/she re-opens Weixin or the Mini Program, the Mini Program will run from the background to the **foreground**.

## Termination of Mini Programs

> 📘 Note
> 
> A Mini Program is terminated only after it runs in the background for a certain period of time, or it occupies too much system resource.

- When a Mini Program is in the background, it will be running for 5 minutes. After that, the app will terminate it.
- When a Mini Program occupies too much system resource, it may be terminated by the system or Mini app.
  - On iOS, a Mini Program is terminated when Mini app receives the memory consumption alert for two or more times consecutively within 5 seconds, and a prompt of "This Mini Program is terminated because it slows down Mini app" will appear.
  - It is recommended that Mini Programs listen memory alert events via [wx.onMemoryWarning](<>) when necessary to free up memory promptly.
    > Base library version higher than 1.1.0 (inclusive) and lower than 1.4.0: When the user enters the Mini Program from entries like Scan QR code, Forward etc. (with scene values of 1007, 1008, 1011 and 1025) and exits the Mini Program when it is not sticky on top, the Mini Program will be terminated.

## Re-open Logic

> Start from base library version 1.4.0. Please remaining [backward compatible.](<>)

Users may open a Mini Program in the following two scenarios:

A. Open homepage: Available [scene values](<>) include:

| Scene Value ID | Description                                                       |
| :------------- | :---------------------------------------------------------------- |
| 1001           | The main entry of Mini Programs in Discover "Recently Used" list. |
| 1019           | Weixin Wallet                                                     |
| 1022           | The entry of a Mini Program sticky on top at the top of a chat.   |
| 1023           | Android desktop icon                                              |
| 1038           | Returned from another Mini Program                                |
| 1056           | Music player menu                                                 |

B. Open a page specified by the Mini Program: the scene value can be any other value than A.

The logic of re-open a Mini Program is as follows:

| Previous Scene | Current Scene | Effect                                                                                                                     |
| :------------- | :------------ | :------------------------------------------------------------------------------------------------------------------------- |
| A              | A             | Remain as it is                                                                                                            |
| B              | A             | Clear the previous page stack and open the homepage (execute wx.reLaunch to go to the homepage)                            |
| A or B         | B             | Clear the previous page stack and open a specified page (execute [wx.reLaunch]\((wx.reLaunch) to go to the specified page) |
