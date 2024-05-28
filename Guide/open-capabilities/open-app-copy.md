---
title: "Open App"
slug: "open-app-copy"
excerpt: "This section explains the concept of Open App."
hidden: true
metadata: 
  image: []
  robots: "index"
createdAt: "Mon May 08 2023 09:21:07 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Mon May 29 2023 10:54:39 GMT+0000 (Coordinated Universal Time)"
layout: "default"
parent: "Open Capabilities (COPY)"
grand_parent: "Guide"
---
"Open App" allows the Mini Program's linked app to be opened from within the Mini Program. Since "Open App" can only be triggered by the user, this feature is not called by an API, but is triggered by clicking the button component with the value of `open-type` as `launchApp`.

When a Mini Program is opened from a message card shared from an app (scene value 1036; see the documentation on sharing a Mini Program from an app for iOS/Android), or opened from an app (scene value 1069), the Mini Program will have the ability to open the app. In this case, the user can tap the button to open the app that shares the Mini Program card/starts the Mini Program. That is to say, the Mini Program cannot open any app, but can only return to the app.

Within the lifecycle of a Mini Program, it has the ability to open its linked app only under specific conditions.

In the base library before 2.5.1, this ability has the following rules:

- When a Mini Program is opened from scene 1069, an app can be opened.
- When a Mini Program is opened from a non-1069 scene, a status is managed within the Mini Program framework. The app can be opened when the status is true; otherwise, false. This status is maintained as follows:
  - When the Mini Program is opened from a message card shared from an app (scene value 1036), the status is set to true.
  - When the Mini Program is opened from the following scenes, the status of the ability to open the app remains the same as that set when the Mini Program was opened last time:
    - When the Mini Program is returned from another Mini Program (scene value 1038) (supported from base library 2.2.4 and later)
    - When the Mini Program is opened from Recently Used in the scene on the top of chats (scene value 1089)
    - When the Mini Program is opened from the list of recently used Mini Programs opened by holding the upper right corner menu (scene value 1090)
- When the Mini Program is opened from the scenes other than the above ones, it does not have the ability to open the app. The status is set to false.

![](https://files.readme.io/80800bd-27.png)

In the base library of 2.5.1 and later, this ability has the following rules:

- When a Mini Program is opened from any scene, a status is managed within the Mini Program framework. The app can be opened when the status is true; otherwise, false. This status is maintained as follows:
- When the Mini Program is opened from a message card shared from an app (scene value 1036) or opened from an app (scene value 1069), the status is set to true.
- When the Mini Program is opened from the following scenes, the status of the ability to open the app remains the same as that set when the Mini Program was opened last time:
  - When the Mini Program is returned from another Mini Program (scene value 1038) (supported from base library 2.2.4 and later)
  - When the Mini Program is opened from Recently Used in the scene on the top of chats (scene value 1089)
  - When the Mini Program is opened from the list of recently used Mini Programs opened by holding the upper right corner menu (scene value 1090)

When the Mini Program is opened from the scenes other than the above ones, it does not have the ability to open the app. The status is set to false.

![](https://files.readme.io/51c4ef1-28.png)

## Usage

## Mini Program

You need to set the `open-type` value of the button component to `launchApp`. To pass a parameter to the app when you open it, you can set `app-parameter` as the parameter to pass. The error events of opening the app can be listened via `binderror`.

## App

The app needs access to OpenSDK. See document for iOS / Android.

For third-party apps for Android, the Weixin callback of `ShowMessageFromWX.req` should be processed, while for iOS, the appId should be added to the URL types field in the plist file of the third party app project. For details on how to get `app-parameter`, see the onResp method in WXEntryActivity of Android SDKSample and the onResp method in WXApiDelegate of iOS SDKSample.

### Code Sample

```Text code
<button open-type="launchApp" app-parameter="wechat" binderror="launchAppError">Open APP</button>
```

```Text code
Page({
  launchAppError (e) {
    console.log(e.detail.errMsg)
  }
})
```

## Parameter Description of error Event

| Value         | Description                                                                                          |
| :------------ | :--------------------------------------------------------------------------------------------------- |
| invalid scene | Incorrect call scenario, indicating that the Mini Program does not have the ability to open the App. |
