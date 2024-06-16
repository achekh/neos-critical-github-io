---
title: "Global configuration"
slug: "global-configuration"
excerpt: ""
hidden: false
createdAt: "Fri May 12 2023 11:38:28 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Tue Nov 28 2023 10:14:21 GMT+0000 (Coordinated Universal Time)"
layout: "default"
parent: "Mini App configuration"
grand_parent: "Guide"
nav_order: 1
---
# Global configuration 
*** 
The `app.json` file in the root directory of a Mini App is used to configure Super Hub Mini App, determine the page file path and window display, and set the network timeout period and customize the tab bar.

## Sample configuration

The following is an `app.json` contains some common configuration options:

```json
{
  "pages": ["pages/index/index", "pages/logs/index"],
  "window": {
    "navigationBarTitleText": "Demo"
  },
  "tabBar": {
    "list": [
      {
        "pagePath": "pages/index/index",
        "text": "Homepage"
			},{
        "pagePath": "pages/logs/logs",
        "text": "Log"
      }
	]},
  "networkTimeout": {
    "request": 10000
  },
  "debug": true,
  "navigateToMiniProgramAppIdList": ["tmfq0nbl3hxxlv2w7u"],
  "groupIdList":["123456","34356576","457658769"]
}
```

### `app.json` configuration items

| Attribute                                                                                 | Type           | Required | Description                                                                                                               |
| :---------------------------------------------------------------------------------------- | :------------- | :------- | :------------------------------------------------------------------------------------------------------------------------ |
| [pages](global-configuration#pages)                                                   | String <Array> | Yes      | List of page paths                                                                                                        |
| [window](global-configuration#window)                                                 | Object         | No       | Global default window display                                                                                             |
| [tabBar](global-configuration#tabbar)                                                 | Object         | No       | Bottom tabbar display                                                                                                     |
| [networkTimeout](global-configuration#networktimeout)                                 | Object         | No       | Network timeout period                                                                                                    |
| [debug](global-configuration#debug)                                                   | Boolean        | No       | Whether to enable the debug mode (disabled by default)                                                                    |
| [requiredBackgroundModes](global-configuration#requiredbackgroundmodes)               | String <Array> | No       | Capabilities required to be used in the background, such as "music playback".                                             |
| [navigateToMiniProgramAppIdList](global-configuration#navigatetominiprogramappidlist) | String <Array> | No       | List of mini apps to redirect to. For more information, see [navigateToMiniProgram](/APIs/redirect/navigate-to-mini-program).        |
| [permission](global-configuration#permission)                                         | Object         | No       | API permission configuration of the mini app                                                                              |
| darkmode                                                                                  | Boolean        | No       | When this parameter is `true` , it is allowed to get whether Mobile is currently in dark mode through `wx.getSystemInfo`. |

## pages

It is used to register the Mini App pages, each of which corresponds to the path + filename information of a page. The filename does not need to have the extension, as the framework will automatically find the four files of `.json` , `.js` , `.wxml `, and `.wxss` for processing.

**The first item in the array represents the initial page (homepage) of the Mini App. To add/remove pages in the Mini App requires modifying the `pages` array.**

For example, if the directory is as follows:

![](/assets/images/af55877-small-Screenshot_2023-05-12_at_4.54.52_PM.png)

Then you need to write the following in `app.json` :

```json
{
  "pages": ["pages/index/index", "pages/logs/logs"]
}
```

## window

It is used to set the status bar, navigation bar, title, and window background color of the Mini App.

| Attribute                    | Type     | Default  | Description                                                                                                                                                            |
| :--------------------------- | :------- | :------- | :--------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| navigationBarBackgroundColor | HexColor | # 000000 | Background color of the navigation bar, such as `#000000`.                                                                                                             |
| navigationBarTextStyle       | String   | white    | Title color of the navigation bar. Valid values: `black , white`.                                                                                                      |
| navigationBarTitleText       | String   |          | Title text of the navigation bar                                                                                                                                       |
| navigationStyle              | String   | default  | Style of the navigation bar. Valid values: `default` (default style), `custom` (custom navigation bar, which only retains the capsule button in the top-right corner). |
| backgroundColor              | HexColor | # ffffff | Background color of the window                                                                                                                                         |
| backgroundTextStyle          | String   | dark     | Loading style during pull-to-refresh. Valid values: `dark , light`.                                                                                                    |
| backgroundColorTop           | String   | # ffffff | Background color of the top of the window, which is supported only on iOS.                                                                                             |
| backgroundColorBottom        | String   | # ffffff | Background color of the bottom of the window, which is supported only on iOS.                                                                                          |
| enablePullDownRefresh        | Boolean  | false    | Whether to enable pull-to-refresh globally.                                                                                                                            |
| pageOrientation              | String   | portrait | Screen rotation settings. Valid values: `auto , portrait , landscape`.                                                                                                 |

- HexColor refer to a hex color value, such as "#ff00ff".

Sample code:

```json
{
	"window": {
    "navigationBarBackgroundColor": "#ffffff",
    "navigationBarTextStyle": "black",
    "navigationBarTitleText": "Super Hub API demo",
    "backgroundColor": "#eeeeee",
    "backgroundTextStyle": "light"
	} 
}
```

## tabBar

If the Mini App is a multi-tab app (there is a tab bar at the bottom or top of the client window to switch between pages), you can use the `tabBar` configuration item to specify the tab bar display and the corresponding page displayed when the tab is switched.

| Attribute       | Type     | Required | Default | Description                                                                                           |
| :-------------- | :------- | :------- | :------ | :---------------------------------------------------------------------------------------------------- |
| color           | HexColor | Yes      |         | Default color of the text on the tab, which must be a hex color.                                      |
| selectedColor   | HexColor | Yes      |         | Color of the selected text on the tab, which must be a hex color.                                     |
| backgroundColor | HexColor | Yes      |         | Background color of the tab, which must be a hex color.                                               |
| borderStyle     | String   | No       | black   | Color of the border on the tabbar. Valid values: `black` , `white`.                                   |
| list            | Array    | Yes      |         | List of tabs, which can contain 2–5 tabs. For more information, see the `list` attribute description. |
| position        | String   | No       | bottom  | Tabbar position. Valid values: `bottom`, `top`.                                                       |
| custom          | Boolean  | No       | false   | Custom tabbar. For more information, see [custom tab bar.](../basic-capabilities/custom-tabbar)                    |

`list` can only be an array of 2–5 tabs. The tabs are sorted in the order of the array, and each of them is an object with the following attributes:

| Attribute | Type   | Required | Description                                                                                                                 |
| :-------- | :----- | :------- | :-------------------------------------------------------------------------------------------------------------------------- |
| pagePath  | String | Yes      | Page path, which must be defined in `pages` first.                                                                          |
| text      | String | Yes      | Button text on the tab                                                                                                      |
| iconPath  | String | Yes      | Image path. The icon file size cannot exceed 40 KB. The recommended icon size is 81x81 px. Online images are not supported. |

> 📘 Notes
> 
> - When `position` is `top` , icons are not shown.
> - For selectedIconPath, the icon file size cannot exceed 40 KB. The recommended icon size is 81x81 px. Online images are not supported.

## networkTimeout

It is the timeout period of various network requests in milliseconds.

| Attribute  | Type   | Required | Default | Description                                                 |
| :--------- | :----- | :------- | :------ | :---------------------------------------------------------- |
| request    | Number | No       | 60000   | Timeout period of [request](/APIs/network/request) in milliseconds.   |
| uploadFile | Number | No       | 60000   | Timeout period of [uploadFile](/APIs/network/upload) in milliseconds. |

## debug

You can enable the `debug` mode in Super Hub Mini App Studio. In the IDE console, the debugging information is presented in the form of `info` , including page registration, page routing, data update, and event triggering. It helps you quickly locate common problems.

## requiredBackgroundModes

It declares the array of capabilities that need to run in the background. The following items are currently supported:

- `audio` : Background music playback

Example:

```json
{
  "pages": ["pages/index/index"],
  "requiredBackgroundModes": ["audio"]
}
```

> 📘 Notes
> 
> APIs running in the background are declared here, which can directly take effect on the developer and trial versions but need to be approved first for the official version.

## navigateToMiniProgramAppIdList

When the Mini App needs to use the [navigateToMiniProgram](doc:navigate-to-mini-program) API to redirect to other Mini Apps, it is necessary to declare the list of (up to 10) appId values of target Mini Apps in the configuration file.

## permission

It is the API permission settings of the mini app. The field is of Object type in the following structure:

| Attribute          | Type             | Required | Description                     |
| :----------------- | :--------------- | :------- | :------------------------------ |
| scope.userLocation | PermissionObject | No       | Location permission declaration |

### Structure of PermissionObject

| Attribute | Type   | Required | Description                                                                                                            |
| :-------- | :----- | :------- | :--------------------------------------------------------------------------------------------------------------------- |
| desc      | string | Yes      | Purpose description of the API displayed when the Mini App obtains the permission. It can contain up to 30 characters. |

Example:

```json
{
  "pages": ["pages/index/index"],
  "permission": {
    "scope.userLocation": {
      "desc": "Your location information will be used to display the effect of the location APIs of the mini app."
    }
  }
}

```
