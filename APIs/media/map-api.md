---
title: "Map"
slug: "map-api"
excerpt: "This section consits of the list of APIs related with Map feature of the Mini App."
hidden: false
createdAt: "Wed Apr 19 2023 11:45:01 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Wed Nov 29 2023 12:57:55 GMT+0000 (Coordinated Universal Time)"
layout: "default"
parent: "Media"
---
Following are the two important Map related APIs:

- [Return value](doc:map-api#returned-value)
- [MapContext](doc:map-api)

## Returned value

[MapContext](doc:map-api#mapcontext)

# MapContext

`MapContext` instance, which can be obtained through `wx.createMapContext`.

`MapContext` is bound to a [`<map>`](doc:map) component through id to manipulate it.

## Methods

### [MapContext.addMarkers](doc:map-api#mapcontextaddmarkers)

Adds a marker.

### [MapContext.fromScreenLocation](doc:map-api#mapcontextfromscreenlocation)

Gets the latitude and longitude corresponding to the point on the screen. The origin is the top-left corner of the map.

### [MapContext.getCenterLocation](doc:map-api#mapcontextgetcenterlocation)

Gets the latitude and longitude of the center of the current map. GCJ-02 coordinates are returned, which can be used for [wx.openLocation()](<>).

### [MapContext.getRotate](doc:map-api#mapcontextgetrotate)

Gets the current rotation angle of the map.

Support: Android only

### [MapContext.getRegion()](doc:map-api#mapcontextgetregion)

Gets the current field of view of the map.

### [MapContext.getScale()](doc:map-api#mapcontextgetscale)

Gets the current zoom level of the map.

### [MapContext.moveAlong](doc:map-api#mapcontextmovealong)

Moves the marker along the specified path, which is used for scenarios such as track playback. A callback event is triggered when the animation is completed. If the animation in the previous call is in progress, calling the `moveAlong` method on the same marker again will interrupt the animation.

Support: iOS only

[MapContext.moveToLocation](doc:map-api#mapcontextmovetolocationobject-object)

Moves the center of the map to the current location. At this time, you need to set the `show-location` parameter of the map component to true .

[MapContext.openMapApp](doc:map-api#mapcontextopenmapappobject-object)

Opens the map app to select navigation.

[MapContext.removeMarkers](doc:map-api#mapcontextremovemarkersobject-object)

Removes a marker.

[MapContext.translateMarker](doc:map-api#mapcontexttranslatemarkerobject-object)

Translates the marker (with animation).

### Sample code

```xml WXML
<!-- map.wxml -->
<map id="myMap" show-location />
<button type="primary" bindtap="getCenterLocation">Get the location</button>
<button type="primary" bindtap="moveToLocation">Move the location</button>
<button type="primary" bindtap="translateMarker">Move the marker</button>
<button type="primary" bindtap="includePoints">Zoom out to show all latitudes and longitudes</button>
```

```javascript JavaScript
// map.js
Page({
  onReady: function (e) {
    // Use `wx.createMapContext` to get the map context
    this.mapCtx = wx.createMapContext('myMap')
  },
  getCenterLocation: function () {
    this.mapCtx.getCenterLocation({
      success: function(res){
        console.log(res.longitude)
        console.log(res.latitude)
    	}
    })
  },
  moveToLocation: function () {
  	this.mapCtx.moveToLocation()
  },
  translateMarker: function() {
    this.mapCtx.translateMarker({
      markerId: 0,
      autoRotate: true,
      duration: 1000,
      destination: {
        latitude:23.10229,
        longitude:113.3345211,
      },
      animationEnd() {
        console.log('animation end')
      }
  	})
  },
  includePoints: function() {
    this.mapCtx.includePoints({
      padding: [10],
      points: [{
        latitude:23.10229,
        longitude:113.3345211,
      }, {
        latitude:23.00229,
        longitude:113.3345211,
      }]
    })
  }
})
```

# MapContext.addMarkers(Object object)

> Support:  
> System map (only supported on iOS): Yes  
> Google Maps (supported on Android and Studio): Yes  
> Huawei Maps (only supported on Android): Yes  
> Tencent Maps (supported on Android and Studio): Yes

## Feature description

Adds a marker.

# Parameters

**Object object**

| Attribute | Type     | Default | Required | Description                                                                        |
| :-------- | :------- | :------ | :------- | :--------------------------------------------------------------------------------- |
| markers   | Array    |         | Yes      | Same as the marker attribute passed into the map component.                        |
| clear     | Boolean  | false   | No       | Whether to clear all markers on the map first                                      |
| success   | Function |         | No       | Callback function for successful API call                                          |
| fail      | Function |         | No       | Callback function for failed API call                                              |
| complete  | Function |         | No       | Callback function for API call end (executed for both successful and failed calls) |

# MapContext.fromScreenLocation(Object object)

> Support:  
> System map (only supported on iOS): Yes  
> Google Maps (supported on Android and Studio): Yes  
> Huawei Maps (only supported on Android): Yes  
> Tencent Maps (supported on Android and Studio): Yes

## Feature description

Gets the latitude and longitude corresponding to the point on the screen. The origin is the top-left corner of the map.

# Parameters

**Object object**

| Attribute | Type     | Default | Required | Description                                                                        |
| :-------- | :------- | :------ | :------- | :--------------------------------------------------------------------------------- |
| x         | Number   |         | Yes      | X coordinate                                                                       |
| y         | Number   |         | Yes      | Y coordinate                                                                       |
| success   | Function |         | No       | Callback function for successful API call                                          |
| fail      | Function |         | No       | Callback function for failed API call                                              |
| complete  | Function |         | No       | Callback function for API call end (executed for both successful and failed calls) |

`object.success` callback function

# Parameters

Object res

| Attribute | Type   | Description |
| :-------- | :----- | :---------- |
| latitude  | number | Latitude    |
| longitude | number | Longitude   |

# MapContext.getCenterLocation(Object object)

> Support:  
> System map (only supported on iOS): Yes  
> Google Maps (supported on Android and Studio): Yes  
> Huawei Maps (only supported on Android): Yes  
> Tencent Maps (supported on Android and Studio): Yes

## Feature description

Gets the latitude and longitude of the center of the current map. GCJ-02 coordinates are returned, which can be used for[ wx.openLocation()](<>).

# Parameters

**Object object**

| Attribute | Type     | Default | Required | Description                                                                        |
| :-------- | :------- | :------ | :------- | :--------------------------------------------------------------------------------- |
| iconPath  | String   |         | No       | Icon path, which can be a network, local, or code package path.                    |
| success   | Function |         | No       | Callback function for successful API call                                          |
| fail      | Function |         | No       | Callback function for failed API call                                              |
| complete  | Function |         | No       | Callback function for API call end (executed for both successful and failed calls) |

**`object.success` callback function**

**Parameters**

Object res

| Attribute | Type   | Description |
| :-------- | :----- | :---------- |
| longitude | number | Longitude   |
| latitude  | number | Latitude    |

# MapContext.getRegion(Object object)

> Support:  
> System map (only supported on iOS): Yes  
> Google Maps (supported on Android and Studio): Yes  
> Huawei Maps (only supported on Android): Yes  
> Tencent Maps (supported on Android and Studio): Yes

## Feature description

Gets the current field of view of the map.

# Parameters

**Object object**

| Attribute | Type     | Default | Required | Description                                                                        |
| :-------- | :------- | :------ | :------- | :--------------------------------------------------------------------------------- |
| success   | Function |         | No       | Callback function for successful API call                                          |
| fail      | Function |         | No       | Callback function for failed API call                                              |
| complete  | Function |         | No       | Callback function for API call end (executed for both successful and failed calls) |

**`object.success` callback function**

# Parameters

**Object res**

| Attribute | Type   | Description                                    |
| :-------- | :----- | :--------------------------------------------- |
| southwest | Object | Latitude and longitude of the southwest corner |
| northeast | Object | Latitude and longitude of the northeast corner |

- southwest

| Structure Attribute | Type   | Description |
| :------------------ | :----- | :---------- |
| longitude           | Number | Longitude   |
| latitude            | Number | Latitude    |

- northeast

| Structure Attribute | Type   | Description |
| :------------------ | :----- | :---------- |
| longitude           | Number | Longitude   |
| latitude            | Number | Latitude    |

# MapContext.getRotate(Object object)

> Support:  
> System map (only supported on iOS): No  
> Google Maps (supported on Android and Studio): Yes  
> Huawei Maps (only supported on Android): Yes  
> Tencent Maps (supported on Android and Studio): Yes

## Feature description

Gets the current rotation angle of the map.

# Parameters

**Object object**

| Attribute | Type     | Default | Required | Description                                                                        |
| :-------- | :------- | :------ | :------- | :--------------------------------------------------------------------------------- |
| success   | Function |         | No       | Callback function for successful API call                                          |
| fail      | Function |         | No       | Callback function for failed API call                                              |
| complete  | Function |         | No       | Callback function for API call end (executed for both successful and failed calls) |

**`object.success` callback function**

# Parameters

**Object res**

| Attribute | Type   | Description    |
| :-------- | :----- | :------------- |
| rotate    | Number | Rotation angle |

# MapContext.getScale(Object object)

> Support:  
> System map (only supported on iOS): Yes  
> Google Maps (supported on Android and Studio): Yes  
> Huawei Maps (only supported on Android): Yes  
> Tencent Maps (supported on Android and Studio): Yes

## Feature description

Gets the current zoom level of the map.

# Parameters

**Object object**

| Attribute | Type     | Default | Required | Description                                                                        |
| :-------- | :------- | :------ | :------- | :--------------------------------------------------------------------------------- |
| success   | Function |         | No       | Callback function for successful API call                                          |
| fail      | Function |         | No       | Callback function for failed API call                                              |
| complete  | Function |         | No       | Callback function for API call end (executed for both successful and failed calls) |

**`object.success` callback function**

# Parameters

Object res

| Attribute | Type   | Description |
| :-------- | :----- | :---------- |
| scale     | Number | Zoom level  |

# MapContext.getSkew(Object object)

> Support:  
> System map (only supported on iOS): No  
> Google Maps (supported on Android and Studio): Yes  
> Huawei Maps (only supported on Android): Yes  
> Tencent Maps (supported on Android and Studio): Yes

## Feature description

Gets the current tilt angle of the map.

# Parameters

**Object object**

| Attribute | Type     | Default | Required | Description                                                                         |
| :-------- | :------- | :------ | :------- | :---------------------------------------------------------------------------------- |
| success   | Function |         | No       | Callback function for successful API call.                                          |
| fail      | Function |         | No       | Callback function for failed API call.                                              |
| complete  | Function |         | No       | Callback function for API call end (executed for both successful and failed calls). |

`object.success` **callback function**

# Parameters

Object res

| Attribute | Type   | Description |
| :-------- | :----- | :---------- |
| skew      | Number | Tilt angle  |

# MapContext.includePoints(Object object)

> Support:  
> System map (only supported on iOS): No  
> Google Maps (supported on Android and Studio): Yes  
> Huawei Maps (only supported on Android): Yes  
> Tencent Maps (supported on Android and Studio): Yes

## Feature description

Zooms out to show all latitudes and longitudes.

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
    "0-0": "points",
    "0-1": "Array.",
    "0-2": "",
    "0-3": "Yes",
    "0-4": "List of coordinate points to be shown in the visible area",
    "1-0": "padding",
    "1-1": "Array.",
    "1-2": "",
    "1-3": "No",
    "1-4": "The distance in pixels from the edge of the rectangle formed by coordinate points to the edge of the map, which is in the format of [top, right, bottom, left]. Only the first item in the array can be recognized on Android. The top, bottom, left, and right paddings are  \nthe same. DevTools does not support the padding parameter currently.",
    "2-0": "success",
    "2-1": "Function",
    "2-2": "",
    "2-3": "No",
    "2-4": "Callback function for successful API call",
    "3-0": "fail",
    "3-1": "Function",
    "3-2": "",
    "3-3": "No",
    "3-4": "Callback function for failed API call",
    "4-0": "complete",
    "4-1": "Function",
    "4-2": "",
    "4-3": "No",
    "4-4": "Callback function for API call end (executed for both successful and failed calls)"
  },
  "cols": 5,
  "rows": 5,
  "align": [
    "left",
    "left",
    "left",
    "left",
    "left"
  ]
}
[/block]


**points**

| Structure Attribute | Type   | Default | Required | Description |
| :------------------ | :----- | :------ | :------- | :---------- |
| longitude           | Number |         | Yes      | Longitude   |
| latitude            | Number |         | Yes      | Latitude    |

# MapContext.moveAlong(Object object)

> Support:  
> System map (only supported on iOS): Yes  
> Google Maps (supported on Android and Studio): No  
> Huawei Maps (only supported on Android): No  
> Tencent Maps (supported on Android and Studio): No

## Feature description

Moves the marker along the specified path, which is used for scenarios such as track playback. A callback event is triggered when the animation is completed. If the animation in the previous call is in progress, calling the moveAlong method on the same marker again will interrupt the animation.

# Parameters

**Object object**

| Attribute  | Type     | Default | Required | Description                                                                                       |
| :--------- | :------- | :------ | :------- | :------------------------------------------------------------------------------------------------ |
| markerId   | Number   |         | Yes      | The specified marker                                                                              |
| path       | Array    |         | Yes      | Coordinate string of the movement path, with coordinates in the format of `{longitude, latitude}` |
| autoRotate | Boolean  | true    | No       | Whether to automatically rotate the marker according to the path direction                        |
| duration   | Number   |         | Yes      | Movement duration                                                                                 |
| success    | Function |         | No       | Callback function for successful API call                                                         |
| fail       | Function |         | No       | Callback function for failed API call                                                             |
| complete   | Function |         | No       | Callback function for API call end (executed for both successful and failed calls)                |

# MapContext.moveToLocation(Object object)

> Support:  
> System map (only supported on iOS): Yes  
> Google Maps (supported on Android and Studio): Yes  
> Huawei Maps (only supported on Android): Yes  
> Tencent Maps (supported on Android and Studio): Yes

## Feature description

Moves the center of the map to the current location. At this time, you need to set the `show-location` parameter of the map component to true .

# Parameters

**Object object**

| Attribute | Type     | Default | Required | Description                                                                        |
| :-------- | :------- | :------ | :------- | :--------------------------------------------------------------------------------- |
| longitude | Number   |         | No       | Longitude                                                                          |
| latitude  | Number   |         | No       | Latitude                                                                           |
| success   | Function |         | No       | Callback function for successful API call                                          |
| fail      | Function |         | No       | Callback function for failed API call                                              |
| complete  | Function |         | No       | Callback function for API call end (executed for both successful and failed calls) |

# MapContext.openMapApp(Object object)

> Support:  
> System map (only supported on iOS): Yes  
> Google Maps
>
> - supported on Android: Yes
> - supported on Studio: No  
>   Huawei Maps (only supported on Android): Yes  
>   Tencent Maps
> - supported on Android: Yes
> - supported on Studio: No

## Feature description

Opens the map app to select navigation.

# Parameters

**Object object**

| Attribute   | Type     | Default | Required | Description                                                                        |
| :---------- | :------- | :------ | :------- | :--------------------------------------------------------------------------------- |
| longitude   | Number   |         | Yes      | Destination longitude                                                              |
| latitude    | Number   |         | Yes      | Destination latitude                                                               |
| destination | String   |         | Yes      | Destination name                                                                   |
| success     | Function |         | No       | Callback function for successful API call                                          |
| fail        | Function |         | No       | Callback function for failed API call                                              |
| complete    | Function |         | No       | Callback function for API call end (executed for both successful and failed calls) |

# MapContext.removeMarkers(Object object)

> Support:  
> System map (only supported on iOS): Yes  
> Google Maps (supported on Android and Studio): Yes  
> Huawei Maps (only supported on Android): Yes  
> Tencent Maps (supported on Android and Studio): Yes

## Feature description

Removes a marker.

# Parameters

**Object object**

| Attribute | Type     | Default | Required | Description                                                                        |
| :-------- | :------- | :------ | :------- | :--------------------------------------------------------------------------------- |
| markerIds | Array    |         | Yes      | The set of marker IDs                                                              |
| success   | Function |         | No       | Callback function for successful API call                                          |
| fail      | Function |         | No       | Callback function for failed API call                                              |
| complete  | Function |         | No       | Callback function for API call end (executed for both successful and failed calls) |

# MapContext.translateMarker(Object object)

> Support:  
> System map (only supported on iOS): Yes  
> Google Maps (supported on Android and Studio): Yes  
> Huawei Maps (only supported on Android): Yes  
> Tencent Maps (supported on Android and Studio): Yes

## Feature description

Translates the marker. The animation effects are only supported in iOS and Studio, but not supported in Android currently.

# Parameters

**Object object**

| Attribute    | Type     | Default | Required | Description                                                                        |
| :----------- | :------- | :------ | :------- | :--------------------------------------------------------------------------------- |
| markerId     | Number   |         | Yes      | The specified marker                                                               |
| destination  | Object   |         | Yes      | The specified destination point to move the marker to                              |
| animationEnd | Function |         | No       | Callback function for animation end                                                |
| success      | Function |         | No       | Callback function for successful API call                                          |
| fail         | Function |         | No       | Callback function for failed API call                                              |
| complete     | Function |         | No       | Callback function for API call end (executed for both successful and failed calls) |

**destination**

| Structure Attribute | Type   | Default | Required | Description |
| :------------------ | :----- | :------ | :------- | :---------- |
| longitude           | Number |         | Yes      | Longitude   |
| latitude            | Number |         | Yes      | Latitude    |
