---
title: "Location"
slug: "location-api"
excerpt: "This section displays the list of all Location related APIs for the Mini App."
hidden: false
createdAt: "Fri Apr 21 2023 07:31:07 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Wed Nov 29 2023 13:26:47 GMT+0000 (Coordinated Universal Time)"
layout: "default"
parent: "APIs"
---
# Location 
This section displays the list of all Location related APIs for the Mini App.
*** 
| Name                                                                                          | Feature Description                                                                                                                                      |
| :-------------------------------------------------------------------------------------------- | :------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [startLocationUpdate](doc:location-api#startlocationupdate-object-object)                     | Enables the Mini App to receive location information on the foreground.                                                                                  |
| [stopLocationUpdate](doc:location-api#stoplocationupdate-object-object)                       | Unlistens for the real-time location change. Both the foreground and background will stop receiving messages                                             |
| [startLocationUpdateBackground](doc:location-api#startlocationupdatebackground-object-object) | Enables the Mini App to receive location information on both the foreground and background, which requires user ‘authorization’.                         |
| [openLocation](doc:location-api#openlocation-object-object)                                   | Uses WeChat's built-in map to view the location.                                                                                                         |
| [onLocationChange](doc:location-api#onlocationchange-object-object)                           | Listens for the real-time geographic location change event, which must be used together with `startLocationUpdateBackground` and `startLocationUpdate `. |
| [offLocationChange](doc:location-api#offlocationchange-object-object)                         | Unlistens for the real-time geographic location change event.                                                                                            |
| [onLocationChangeError](doc:location-api#onlocationchangeerror-object-object)                 | Listens for the error returned by the continuous positioning API.                                                                                        |
| [offLocationChangeError](doc:location-api#offlocationchangeerror-object-object)               | Unlistens for the error returned by the continuous positioning API.                                                                                      |
| [getLocation](doc:location-api#wxgetlocationobject-object)                                    | Gets the current geographic location and speed.                                                                                                          |
| [choosePoi](doc:location-api#choosepoi)                                                       | Opens the POI list to select a location. Fuzzy positioning (accurate to the city) and precise positioning can be selected at the same time.              |
| [chooseLocation](doc:location-api#chooselocation)                                             | Opens the map to select a location.                                                                                                                      |
| [getFuzzyLocation](doc:location-api#wxgetfuzzylocationobject-object)                          | Gets the current vague geographic location.                                                                                                              |

# startLocationUpdate (Object object)

Enables the Mini App to receive location information in the foreground.

# Parameters

**Object object**

| Attribute | Type     | Default | Required | Description                                                                                                 |
| :-------- | :------- | :------ | :------- | :---------------------------------------------------------------------------------------------------------- |
| type      | String   |         | No       | GPS coordinates are returned for WGS84, and coordinates used for `wx.openLocation` are returned for GCJ-02. |
| success   | Function |         | No       | Callback function for successful API call                                                                   |
| fail      | Function |         | No       | Callback function for failed API call                                                                       |
| complete  | Function |         | No       | Callback function for API call end (executed for both successful and failed calls)                          |

# stopLocationUpdate (Object object)

Unlistens for the real-time location change. Both the foreground and background will stop receiving messages.

# Parameters

**Object object**

| Attribute | Type     | Default | Required | Description                                                                         |
| :-------- | :------- | :------ | :------- | :---------------------------------------------------------------------------------- |
| success   | Function |         | No       | Callback function for successful API call.                                          |
| fail      | Function |         | No       | Callback function for failed API call.                                              |
| complete  | Function |         | No       | Callback function for API call end (executed for both successful and failed calls). |

# startLocationUpdateBackground (Object object)

Enables the Mini App to receive location information on both the foreground and background, which requires user 'authorization'. After the authorization, the mini app can receive location change messages when running on the foreground or background.

**Categories opened for Chinese mini apps**

[block:parameters]
{
  "data": {
    "h-0": "Level-1  \nCategory/Entity  \nType",
    "h-1": "Level-2 Category",
    "h-2": "Application Scenario",
    "0-0": "Ecommerce platforms",
    "0-1": "/",
    "0-2": "Offline store guide and navigation services in the mini app",
    "1-0": "Self-operated merchants",
    "1-1": "/",
    "1-2": "Offline store guide and navigation services in the mini app",
    "2-0": "Transportation services",
    "2-1": "/",
    "2-2": "Chauffeur, taxi, urban public transportation, and real-time navigation services",
    "3-0": "Lifestyle services",
    "3-1": "Errand and shared services",
    "3-2": "Delivery services and location-based tool sharing services",
    "4-0": "Logistics services",
    "4-1": "Package pickup/delivery, package query, postal service, loading and un  \nloading, delivery locker, and cargo transportation",
    "4-2": "Package/Cargo pickup and delivery services",
    "5-0": "Catering services",
    "5-1": "Food ordering and delivery platforms",
    "5-2": "Food delivery and real-time offline store navigation services",
    "6-0": "Tools",
    "6-1": "Health management",
    "6-2": "Body management records based on the real-time geographic location",
    "7-0": "Tourism",
    "7-1": "Scenic spot and accommodation services",
    "7-2": "Scenic spot navigation, tour guide, and hotel n  \navigation services in the mini app",
    "8-0": "Governmental and civic services",
    "8-1": "/",
    "8-2": "Government affair services",
    "9-0": "Government entity account",
    "9-1": "/",
    "9-2": "Government affair services",
    "10-0": "Transportation services",
    "10-1": "/",
    "10-2": "Chauffeur, taxi, ur  \nban public transportation, and real-time navigation services",
    "11-0": "Lifestyle services",
    "11-1": "Housekeeping and delivery",
    "11-2": "Delivery services  \nand location-base  \nd door-to-door services",
    "12-0": "Courier and post",
    "12-1": "/",
    "12-2": "Package/Cargo pi  \nckup and delivery  \nservices",
    "13-0": "Catering services",
    "13-1": "Food ordering and delivery platforms",
    "13-2": "Food delivery and  \nreal-time offline st  \nore navigation ser  \nvices",
    "14-0": "Ecommerce platforms",
    "14-1": "/",
    "14-2": "Offline store guide  \nand navigation ser  \nvices in the mini app",
    "15-0": "Cross-border ecommerce",
    "15-1": "/",
    "15-2": "Offline store guide  \nand navigation ser  \nvices in the mini app",
    "16-0": "Local services",
    "16-1": "Clothing, shoes, bags, toys, home appliances, digital devices, mobile phones, makeups, skincare, jewelry, accessories, glasses, watches, sports, outdoor, musical instruments, flowers, gardening, handicrafts, home, furniture, textiles, office, stationery, machinery, electronic devices, wine, food, department stores, supermarkets, convenience stores, and pet food and supplies",
    "16-2": "Offline store guide  \nand navigation ser  \nvices in the mini      app"
  },
  "cols": 3,
  "rows": 17,
  "align": [
    "left",
    "left",
    "left"
  ]
}
[/block]


# Parameters

**Object object**

| Attribute | Type     | Default | Required | Description                                                                                                 |
| :-------- | :------- | :------ | :------- | :---------------------------------------------------------------------------------------------------------- |
| type      | String   | gcj02   | No       | GPS coordinates are returned for WGS84, and coordinates used for` wx.openLocation` are returned for GCJ-02. |
| success   | Function |         | No       | Callback function for successful API call                                                                   |
| fail      | Function |         | No       | Callback function for failed API call                                                                       |
| complete  | Function |         | No       | Callback function for API call end (executed for both successful and failed calls)                          |

# openLocation (Object object)

Uses the built-in map to view the location.

# Parameters

**Object object**

| Attribute | Type     | Default | Required | Description                                                                                                                    |
| :-------- | :------- | :------ | :------- | :----------------------------------------------------------------------------------------------------------------------------- |
| latitude  | Number   |         | Yes      | Latitude in the range of `-90 to 90`. A negative value indicates the south latitude. The GCJ-02 coordinate system is used.     |
| longitude | Number   |         | Yes      | Longitude in the range of `-180 to 180 `. A negative value indicates the west longitude. The GCJ-02 coordinate system is used. |
| scale     | Number   | 18      | No       | Zoom ratio. Value range: `5–18`.                                                                                               |
| name      | String   |         | No       | Location name.                                                                                                                 |
| address   | String   |         | No       | Detailed address.                                                                                                              |
| success   | Function |         | No       | Callback function for successful API call.                                                                                     |
| fail      | Function |         | No       | Callback function for failed API call.                                                                                         |
| complete  | Function |         | No       | Callback function for API call end (executed for both successful and failed calls).                                            |

### Sample code

```javascript
// JavaScript
wx.getLocation({
  type: 'gcj02', // Return a latitude and longitude value that can be used for `wx.openLocation`
  success (res) {
    const latitude = res.latitude
    const longitude = res.longitude
    wx.openLocation({
      latitude,
      longitude,
      scale: 18
    })
  }
})
```

# onLocationChange (Object object)

Listens for the real-time geographical location change event, which must be used together with [wx.startLocationUpdateBackground](<>) and [wx.startLocationUpdate](<>).

# Parameters

## Function callback

Callback function for the real-time geographic location change event.

# Parameters

**Object res**

| Attribute          | Type   | Description                                                                                                                    |
| :----------------- | :----- | :----------------------------------------------------------------------------------------------------------------------------- |
| latitude           | Number | Latitude in the range of `-90 to 90` . A negative value indicates the south latitude. The GCJ-02 coordinate system is used.    |
| longitude          | Number | Longitude in the range of `-180 to 180 `. A negative value indicates the west longitude. The GCJ-02 coordinate system is used. |
| speed              | Number | Speed in milliseconds.                                                                                                         |
| accuracy           | Number | Location accuracy.                                                                                                             |
| altitude           | Number | Altitude in meters.                                                                                                            |
| verticalAccuracy   | Number | Vertical accuracy in meters (which cannot be obtained on Android and will be returned as 0).                                   |
| horizontalAccuracy | Number | Horizontal accuracy in meters.                                                                                                 |

### Sample code

```javascript
// JavaScript
const locationChangeFn = function(res) {
	console.log('location change', res)
}
wx.onLocationChange(locationChangeFn)
wx.offLocationChange(locationChangeFn)
```

# onLocationChangeError (Object object)

Listens for the error returned by the continuous positioning API.

# Parameters

## Function callback

# Parameters

**Object res**

| Attribute | Type   | Description |
| :-------- | :----- | :---------- |
| errCode   | number | Error code  |

# offLocationChange (Object object)

Unlistens for the real-time geographic location change event.

# Parameters

## Function callback

Callback function for the real-time geographic location change event

# offLocationChangeError (Object object)

Unlistens for the error returned by the continuous positioning API.

# Parameters

## Function callback

# wx.getLocation(Object object)

> The user should 'authorize' `scope.userLocation` before this API can be called.

Gets the current geographic location and speed. This API cannot be called after the user exits the mini app.

# Parameters

**Object object**

| Attribute | Type     | Default | Required | Description                                                                                                                                                  |
| :-------- | :------- | :------ | :------- | :----------------------------------------------------------------------------------------------------------------------------------------------------------- |
| type      | String   | wgs84   | No       | GPS coordinates are returned for WGS84, and coordinates used for `wx.openLocation` are returned for GCJ-02.                                                  |
| altitude  | String   | false   | No       | Altitude information is returned if `true` is passed in. The API will take a longer time to respond since a higher accuracy is required to get the altitude. |
| success   | Function |         | No       | Callback function for successful API call                                                                                                                    |
| fail      | Function |         | No       | Callback function for failed API call                                                                                                                        |
| complete  | Function |         | No       | Callback function for API call end (executed for both successful and failed calls)                                                                           |

`object.success` callback function

# Parameters

**Object res**

| Attribute          | Type   | Description                                                                                  |
| :----------------- | :----- | :------------------------------------------------------------------------------------------- |
| latitude           | Number | Latitude in the range of `-90 to 90` . A negative value indicates the south latitude.        |
| longitude          | Number | Longitude in the range of `-180 to 180 `. A negative value indicates the west longitude.     |
| speed              | Number | Speed in milliseconds.                                                                       |
| accuracy           | Number | Location accuracy                                                                            |
| altitude           | Number | Altitude in meters.                                                                          |
| verticalAccuracy   | Number | Vertical accuracy in meters. (which cannot be obtained on Android and will be returned as 0) |
| horizontalAccuracy | Number | Horizontal accuracy in meters.                                                               |

### Sample code

```javascript
// JavaScript
wx.getLocation({
  type: 'gcj02',
  success(res) {
    const latitude = res.latitude
    const longitude = res.longitude
    const speed = res.speed
    const accuracy = res.accuracy
  }
})
```

> 📘 Notes
> 
> The tool uses IP-based positioning, and there may be some deviations. The tool currently only supports GCJ-02 coordinates.
> 
> - When using a third-party service for reverse geocoding, check its default coordinate system to perform coordinate conversion correctly.

# choosePoi

Opens the POI list to select a location. Fuzzy positioning (accurate to the city) and precise positioning can be selected at the same time.

# Parameters

**Object object**

| Attribute | Type     | Required | Description                                                                        |
| :-------- | :------- | :------- | :--------------------------------------------------------------------------------- |
| success   | Function | No       | Callback function for successful API call                                          |
| fail      | Function | No       | Callback function for failed API call                                              |
| complete  | Function | No       | Callback function for API call end (executed for both successful and failed calls) |

`object.success` callback function

# Parameters

**Object res**

| Attribute | Type   | Description                                                                                                                                                                                 |
| :-------- | :----- | :------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| type      | Number | `1 `: City; `2` : Precise location.                                                                                                                                                         |
| city      | Number | City name                                                                                                                                                                                   |
| name      | String | Location name                                                                                                                                                                               |
| address   | String | Detailed address                                                                                                                                                                            |
| latitude  | Number | Latitude, which can be a floating point number in the range of `-90` to `90 `. A negative value indicates the south latitude. The GCJ-02 coordinate system is used (to be disused soon).    |
| longitude | Number | Longitude, which can be a floating point number in the range of `-180` to `180` . A negative value indicates the west longitude. The GCJ-02 coordinate system is used (to be disused soon). |

### Sample

# chooseLocation

Opens the map to select a location.

## Parameters

**Object object**

[block:parameters]
{
  "data": {
    "h-0": "Attribute",
    "h-1": "Type",
    "h-2": "Default",
    "h-3": "Required",
    "h-4": "Description",
    "0-0": "type",
    "0-1": "string",
    "0-2": "tencent",
    "0-3": "No",
    "0-4": "only supported on Studio  \nTencent Maps: tencent  \nGoogle Maps: google",
    "1-0": "latitude",
    "1-1": "number",
    "1-2": "",
    "1-3": "No",
    "1-4": "Destination latitude",
    "2-0": "longitude",
    "2-1": "number",
    "2-2": "",
    "2-3": "No",
    "2-4": "Destination longitude",
    "3-0": "success",
    "3-1": "function",
    "3-2": "",
    "3-3": "No",
    "3-4": "Callback function for successful API call",
    "4-0": "fail",
    "4-1": "function",
    "4-2": "",
    "4-3": "No",
    "4-4": "Callback function for failed API call",
    "5-0": "complete",
    "5-1": "function",
    "5-2": "",
    "5-3": "No",
    "5-4": "Callback function for API call end (executed for both successful and failed calls"
  },
  "cols": 5,
  "rows": 6,
  "align": [
    "left",
    "left",
    "left",
    "left",
    "left"
  ]
}
[/block]


`object.success `callback function

**Parameters**

**Object res**

[block:parameters]
{
  "data": {
    "h-0": "Attribute",
    "h-1": "Type",
    "h-2": "Description",
    "0-0": "name",
    "0-1": "string",
    "0-2": "Location name",
    "1-0": "address",
    "1-1": "string",
    "1-2": "Detailed address",
    "2-0": "latitude",
    "2-1": "number",
    "2-2": "Latitude, which can be a floating point number in the range of -90 to 90 . A negative value indicates the south latitude.  \nThe GCJ-02 coordinate system is used.",
    "3-0": "longitude",
    "3-1": "number",
    "3-2": "Longitude, which can be a floating point number in the range of -180 to 180 . A negative value indicates the west longitude. The GCJ-02 coordinate system is used."
  },
  "cols": 3,
  "rows": 4,
  "align": [
    "left",
    "left",
    "left"
  ]
}
[/block]


# wx.getFuzzyLocation(Object object)

Gets the current vague geographic location.

# Parameters

**Object object**

| Attribute | Type     | Default | Required | Description                                                                                                 |
| :-------- | :------- | :------ | :------- | :---------------------------------------------------------------------------------------------------------- |
| type      | String   | wgs84   | No       | GPS coordinates are returned for WGS84, and coordinates used for `wx.openLocation` are returned for GCJ-02. |
| success   | Function |         | No       | Callback function for successful API call                                                                   |
| fail      | Function |         | No       | Callback function for failed API call                                                                       |
| complete  | Function |         | No       | Callback function for API call end (executed for both successful and failed calls)                          |

`object.success` **callback function**

# Parameters

**Object res**

| Attribute | Type   | Description                                                                              |
| :-------- | :----- | :--------------------------------------------------------------------------------------- |
| latitude  | Number | Latitude in the range of `-90 to 90` . A negative value indicates the south latitude.    |
| longitude | Number | Longitude in the range of `-180 to 180` . A negative value indicates the west longitude. |

### Sample code

```javascript
// JavaScript
wx.getFuzzyLocation({
  type: 'wgs84',
  success (res) {
    const latitude = res.latitude
    const longitude = res.longitude
  }
})
```
