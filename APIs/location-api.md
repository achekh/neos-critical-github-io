---
title: "Location"
slug: "location-api"
excerpt: "This section displays the list of all Location related APIs for the Mini App."
hidden: false
createdAt: "Fri Apr 21 2023 07:31:07 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Wed Nov 29 2023 13:26:47 GMT+0000 (Coordinated Universal Time)"
layout: "default"
parent: "APIs"
nav_order: 10
---
# Location 
This section displays the list of all Location related APIs for the Mini App.

***

| Name                                                                                          | Feature Description                                                                                                                                      |
| :-------------------------------------------------------------------------------------------- | :------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [startLocationUpdate](location-api#startlocationupdate-object-object)                     | Enables the Mini App to receive location information on the foreground.                                                                                  |
| [stopLocationUpdate](location-api#stoplocationupdate-object-object)                       | Unlistens for the real-time location change. Both the foreground and background will stop receiving messages                                             |
| [startLocationUpdateBackground](location-api#startlocationupdatebackground-object-object) | Enables the Mini App to receive location information on both the foreground and background, which requires user ‘authorization’.                         |
| [openLocation](location-api#openlocation-object-object)                                   | Uses WeChat's built-in map to view the location.                                                                                                         |
| [onLocationChange](location-api#onlocationchange-object-object)                           | Listens for the real-time geographic location change event, which must be used together with `startLocationUpdateBackground` and `startLocationUpdate `. |
| [offLocationChange](location-api#offlocationchange-object-object)                         | Unlistens for the real-time geographic location change event.                                                                                            |
| [onLocationChangeError](location-api#onlocationchangeerror-object-object)                 | Listens for the error returned by the continuous positioning API.                                                                                        |
| [offLocationChangeError](location-api#offlocationchangeerror-object-object)               | Unlistens for the error returned by the continuous positioning API.                                                                                      |
| [getLocation](location-api#wxgetlocationobject-object)                                    | Gets the current geographic location and speed.                                                                                                          |
| [choosePoi](location-api#choosepoi)                                                       | Opens the POI list to select a location. Fuzzy positioning (accurate to the city) and precise positioning can be selected at the same time.              |
| [chooseLocation](location-api#chooselocation)                                             | Opens the map to select a location.                                                                                                                      |
| [getFuzzyLocation](location-api#wxgetfuzzylocationobject-object)                          | Gets the current vague geographic location.                                                                                                              |

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

| Level-1  <br />Category/Entity  <br />Type | Level-2 Category | Application Scenario |
| :----------------------------------------- | :--------------- | :------------------- |
| Ecommerce platforms | / | Offline store guide and navigation services in the mini app |
| Self-operated merchants | / | Offline store guide and navigation services in the mini app |
| Transportation services | / | Chauffeur, taxi, urban public transportation, and real-time navigation services |
| Lifestyle services | Errand and shared services | Delivery services and location-based tool sharing services |
| Logistics services | Package pickup/delivery, package query, postal service, loading and un  \nloading, delivery locker, and cargo transportation | Package/Cargo pickup and delivery services |
| Catering services | Food ordering and delivery platforms | Food delivery and real-time offline store navigation services |
| Tools | Health management | Body management records based on the real-time geographic location |
| Tourism | Scenic spot and accommodation services | Scenic spot navigation, tour guide, and hotel n  \navigation services in the mini app |
| Governmental and civic services | / | Government affair services |
| Government entity account | / | Government affair services |
| Transportation services | / | Chauffeur, taxi, ur  \nban public transportation, and real-time navigation services |
| Lifestyle services | Housekeeping and delivery | Delivery services  \nand location-base  \nd door-to-door services |
| Courier and post | / | Package/Cargo pi  \nckup and delivery  \nservices |
| Catering services | Food ordering and delivery platforms | Food delivery and  \nreal-time offline st  \nore navigation ser  \nvices |
| Ecommerce platforms | / | Offline store guide  \nand navigation ser  \nvices in the mini app |
| Cross-border ecommerce | / | Offline store guide  \nand navigation ser  \nvices in the mini app |
| Local services | Clothing, shoes, bags, toys, home appliances, digital devices, mobile phones, makeups, skincare, jewelry, accessories, glasses, watches, sports, outdoor, musical instruments, flowers, gardening, handicrafts, home, furniture, textiles, office, stationery, machinery, electronic devices, wine, food, department stores, supermarkets, convenience stores, and pet food and supplies | Offline store guide  \nand navigation ser  \nvices in the mini      app |

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

| Attribute | Type | Default | Required | Description |
| :-------- | :--- | :------ | :------- | :---------- |
| type | string | tencent | | No | only supported on Studio  <br />Tencent Maps: tencent  <br />Google Maps: google |
| latitude | number |  | No | Destination latitude |
| longitude | number |  | No | Destination longitude |
| success | function |  | No | Callback function for successful API call |
| fail | function |  | No | Callback function for failed API call |
| complete | function |  | No | Callback function for API call end (executed for both successful and failed calls |

`object.success `callback function

**Parameters**

**Object res**

| Attribute | Type | Description |
| :-------- | :--- | :---------- |
| name | string | Location name |
| address | string | Detailed address |
| latitude | number | Latitude, which can be a floating point number in the range of -90 to 90 . A negative value indicates the south latitude.  \nThe GCJ-02 coordinate system is used. |
| longitude | number | Longitude, which can be a floating point number in the range of -180 to 180 . A negative value indicates the west longitude. The GCJ-02 coordinate system is used. |

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
