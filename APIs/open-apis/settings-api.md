---
title: "Settings"
slug: "settings-api"
excerpt: "This section consists of Settings related APIs of Mini App."
hidden: false
createdAt: "Fri Apr 21 2023 10:39:51 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Wed Nov 29 2023 13:28:11 GMT+0000 (Coordinated Universal Time)"
layout: "default"
parent: "Open APIs"
grand_parent: "APIs"
---
# Settings 
*** 
## wx.openSetting(Object object)

Calls the Mini App settings page and returns the operation result of the user. The user can be redirected to the settings page to manage authorizations after a click.

# Parameters

**Object object**

| Attribute | Type     | Description                                                                         |
| :-------- | :------- | :---------------------------------------------------------------------------------- |
| success   | Function | Callback function for successful API call.                                          |
| fail      | Function | Callback function for failed API call.                                              |
| complete  | Function | Callback function for API call end (executed for both successful and failed calls). |

`object.success` callback function

**Parameters**

**Object res**

| Attribute   | Type              | Description                |
| :---------- | :---------------- | :------------------------- |
| authSetting | [AuthSetting](<>) | User authorization result. |

### Sample code

```javascript JavaScript
wx.openSetting({
  success(res) {
    console.log(res.authSetting)
  }
})
```

## wx.getSetting(Object object)

Gets the current settings of the user.

# Parameters

**Object object**

[block:parameters]
{
  "data": {
    "h-0": "Attribute",
    "h-1": "Type",
    "h-2": "Default",
    "h-3": "Required",
    "h-4": "Description",
    "0-0": "withSubscriptions",
    "0-1": "Boolean",
    "0-2": "false",
    "0-3": "No",
    "0-4": "Whether to get the user's message subscription status at the same time. The default value is:` false` .  \n**Note**: `withSubscriptions` only returns subscribed messages for which the user has selected \"Keep the above selection and do not ask again\" in the subscription panel.",
    "1-0": "success",
    "1-1": "Function",
    "1-2": "",
    "1-3": "No",
    "1-4": "Callback function for successful API call.",
    "2-0": "fail",
    "2-1": "Function",
    "2-2": "",
    "2-3": "No",
    "2-4": "Callback function for failed API call.",
    "3-0": "complete",
    "3-1": "Function",
    "3-2": "",
    "3-3": "No",
    "3-4": "Callback function for API call end (executed for both successful and failed calls)."
  },
  "cols": 5,
  "rows": 4,
  "align": [
    "left",
    "left",
    "left",
    "left",
    "left"
  ]
}
[/block]


`object.success` callback function

# Parameters

**Object res**

| Attribute   | Type              | Description                |
| :---------- | :---------------- | :------------------------- |
| authSetting | [AuthSetting](<>) | User authorization result. |

### Sample code

```javascript JavaScript
wx.getSetting({
  success(res) {
    console.log(res.authSetting)
    // res.authSetting = {
    // "scope.userInfo": true,
    // "scope.userLocation": true
    // }
  }
})
```

```javascript JavaScript
wx.getSetting({
  withSubscriptions: true,
  success (res) {
    console.log(res.authSetting)
    // res.authSetting = {
    //  "scope.userInfo": true,
    //  "scope.userLocation": true
    //  "setting.appMsgSubscribed": true, // Long-term subscription switch. Valid values: `true` (on); `false` (off).
    // }
    console.log(res.subscriptionsSetting)
    // res.subscriptionsSetting = {
    //  itemSettings: { // Subscribed message
    //    SYS_MSG_TYPE_INTERACTIVE: 'accept', // Subscribed mini app system message: Contact interaction reminder
    // 		SYS_MSG_TYPE_RANK: 'accept', // Subscribed mini app system message: Leaderboard ranking reminder
    // 		118d4118a4609537873d18fdsfe932332: 'reject', // Subscribed general one-time message
    // 		53231118a4609537873d18fdsfe932332: 'ban', // Subscribed general one-time message
    // 	}
    // }
  }
})
```

# AuthSetting

User authorization information.

## Attributes

- **boolean scope.userLocation**  
  Whether to grant the permission to use the geographic location, corresponding to the [wx.getLocation](doc:location-api#wxgetlocationobject-object) API.  
  Whether to grant the permission to use the geographic location, corresponding to the [wx.chooseLocation](doc:location-api#chooselocation) API.
- **boolean scope.writePhotosAlbum**  
  Whether to grant the permission to save images to the album, corresponding to the [wx.saveImageToPhotosAlbum](doc:image-api#wxsaveimagetophotosalbumobject-object) API.
- **boolean scope.camera**  
  Whether to grant the permission to use the camera, corresponding to the [<camera />](doc:camera) component.
