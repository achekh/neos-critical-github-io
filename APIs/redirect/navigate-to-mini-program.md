---
title: "navigateToMiniProgram (Object object)"
slug: "navigate-to-mini-program"
excerpt: "Opens another Mini App."
hidden: false
metadata: 
  image: []
  robots: "index"
createdAt: "Tue Apr 18 2023 05:35:53 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Fri Jul 14 2023 11:14:32 GMT+0000 (Coordinated Universal Time)"
layout: "default"
parent: "Redirect"
grand_parent: "APIs"
---
# navigateToMiniProgram (Object object) 
Opens another Mini App.

***

# Parameters

**Object object**

| Attribute  | Type     | Default | Required | Description                                                                                                                                                                                                                               |
| :--------- | :------- | :------ | :------- | :---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| appId      | String   |         | Yes      | `appId` of the Mini App to be opened.                                                                                                                                                                                                     |
| path       | String   |         | No       | Path of the page to be opened. If this parameter is empty, the homepage will be displayed.                                                                                                                                                |
| extraData  | Object   |         | No       | The data that needs to be passed to the target Mini App. It can be obtained in `App.onLaunch` and `App.onShow`.                                                                                                                           |
| envVersion | String   | release | No       | A version of the Mini App to be opened. This parameter takes effect only when the current Mini App is a developer version or trial version. If the current Mini App is the official version, the opened Mini app is the official version. |
| success    | Function |         | No       | Callback function for a successful API call.                                                                                                                                                                                              |
| fail       | Function |         | No       | Callback function for a failed API call.                                                                                                                                                                                                  |
| complete   | Function |         | No       | Callback function for an API call end (executed for both successful and failed calls).                                                                                                                                                    |

**Valid values of `object.envVersion`**

| Value   | Description        |
| :------ | :----------------- |
| develop | Developer version. |
| trial   | Trial version.     |
| release | Official version.  |

# Use limits

## The redirect should be triggered by the user

If the user does not click anywhere on the Mini App page, the developer will not be able to call this API to automatically redirect to another Mini App.

## The redirect should be confirmed by the user

Before redirecting to another Mini App, a pop-up window will be added uniformly to ask the user whether to redirect. The redirect can be performed only after confirmation by the user. If the user clicks "Cancel", `fail cancel` will be called back.

## Each Mini app can redirect to no more than 10 Mini apps

When the developer submits a new version of the Mini App code, it is important for the developer to declare the list of Mini Apps to be redirected in the code configuration for using the feature of redirecting to another Mini App. The list cannot contain more than 10 items; otherwise, the code review will fail. 

The list can be updated only when a new version is released. For the configuration method, see Global Configuration. When this API is called, the `appId` of the Mini App that needs to be redirected must be in the configured list; otherwise, ` fail appId "${appId}" is not in navigateToMiniProgramAppIdList` will be returned.

### Sample code

```javascript
// JavaScript
wx.navigateToMiniProgram({
  appId: '',
  path: 'page/index/index?id=123',
  extraData: {
  	foo: 'bar'
  },
  envVersion: 'develop',
  success(res) {
		// Opened successfully
	}
})
```
