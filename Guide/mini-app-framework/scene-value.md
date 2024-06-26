---
title: "Scene Value"
slug: "scene-value"
excerpt: "This section explains the concept of scene value in Mini Program framework."
hidden: true
metadata: 
  robots: "index"
createdAt: "Mon May 01 2023 09:05:02 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Wed May 03 2023 10:15:14 GMT+0000 (Coordinated Universal Time)"
layout: "default"
parent: "Mini Program Framework"
grand_parent: "Guide"
---
# Scene Value 
This section explains the concept of scene value in Mini Program framework.

***

The scene value describes a path in which a user enters a Mini Program. For the definition of the scene value, refer to the [Scene Value List](<>).

Due to restriction of the Android system, currently the value for the scene when the user taps the home button to exit the Mini Program and returns to the home page and then enters the Mini Program from the home page cannot be obtained. In this case, the previous scene value is retained.

## Obtaining the scene value

Developers can obtain the scene value in the following ways:

- For Mini Programs, you can obtain the scene value via onLaunch and onShow in App or via getLaunchOptionsSync.
- For Mini Games, you can obtain the scene value via getLaunchOptionsSync and onShow.

## Scenes where source information is returned

In some scenes, the returned scene values come with the appId of the source app, Official Account, or Mini Program. For details, refer to the reference documents of the corresponding API.

| Scene Value | Scene                                                                | Meaning of appId        |
| :---------- | :------------------------------------------------------------------- | :---------------------- |
| 1020        | Related Mini Program list in the profile page of an Official Account | Source Official Account |
| 1035        | Custom menu of an Official Account                                   | Source Official Account |
| 1036        | Message card shared from an app                                      | Source app              |
| 1037        | Mini Program opened from a Mini Program                              | Source Mini Program     |
| 1038        | Returned from another Mini Program                                   | Source Mini Program     |
| 1043        | Template message of an Official Account                              | Source Official Account |
