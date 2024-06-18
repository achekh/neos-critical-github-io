---
title: "Map"
slug: "map"
excerpt: "Component used to render maps."
hidden: false
metadata: 
  image: []
  robots: "index"
createdAt: "Wed Apr 12 2023 11:22:25 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Mon Jun 19 2023 07:01:47 GMT+0000 (Coordinated Universal Time)"
layout: "default"
parent: "Map"
grand_parent: "Components"
---
# Map 
*** 
Map component is native, so you should keep in mind relevant limits when using it.

## Supported maps

- Apple maps: only supported on iOS.
- Google Maps: supported on Android and Super Hub Mini App Studio.
- Huawei Maps: only supported on Android Huawei devices.

### Map base attribute

| Attribute        | Type            | Default Value | Required | iOS | Android | Description                                                                                                                           |
| :--------------- | :-------------- | :------------ | :------- | :-- | :------ | :------------------------------------------------------------------------------------------------------------------------------------ |
| longitude        | Number          |               | Yes      | Yes | Yes     | Longitude of the map center.                                                                                                          |
| latitude         | Number          |               | Yes      | Yes | Yes     | Latitude of the map center.                                                                                                           |
| scale            | Number          | 16            | No       | Yes | Yes     | Zoom level. Value range: 3–20.                                                                                                        |
| min-scale        | Number          | 3             | No       | No  | Yes     | Minimum zoom level.                                                                                                                   |
| max-scale        | Number          | 20            | No       | No  | Yes     | Maximum zoom level.                                                                                                                   |
| markers          | Array<marker>   |               | No       | Yes | Yes     | List of markers to be rendered on the map.                                                                                            |
| polyline         | Array<polyline> |               | No       | Yes | Yes     | Route                                                                                                                                 |
| circles          | Array<circle>   |               | No       | Yes | Yes     | Circle                                                                                                                                |
| include-points   | Array<Point>    |               | No       | No  | Yes     | Zooms out to include all specified coordinate points.                                                                                 |
| show-location    | Boolean         | false         | No       | Yes | Yes     | Show current location with a direction.                                                                                               |
| polygons         | Array<polygon>  |               | No       | Yes | Yes     | Polygon                                                                                                                               |
| rotate           | Number          | 0             | No       | No  | Yes     | Rotation angle. Value range: 0–360. It is the angle between the north direction in the map and the Y coordinate of the device.        |
| show-compass     | Boolean         | false         | No       | Yes | Yes     | Whether to show the compass.                                                                                                          |
| enable-zoom      | Boolean         | true          | No       | Yes | Yes     | Whether to support zoom                                                                                                               |
| enable-scroll    | Boolean         | true          | No       | Yes | Yes     | Whether to support scroll.                                                                                                            |
| enable-rotate    | Boolean         | false         | No       | No  | Yes     | Whether to support rotation.                                                                                                          |
| enable-satellite | Boolean         | false         | No       | Yes | Yes     | Whether to enable the satellite map.                                                                                                  |
| bindtap          | Event Handler   |               | No       | Yes | Yes     | The event triggered when the user clicks the map, which returns the latitude and longitude information.                               |
| bindmarkertap    | Event Handler   |               | No       | Yes | Yes     | The event triggered when the user clicks the marker: `event.detail = {markerId}`.                                                     |
| bindlabeltap     | Event Handler   |               | No       | Yes | No      | The event triggered when the user clicks the label: `event.detail = {markerId}`.                                                      |
| bindupdated      | Event Handler   |               | No       | No  | Yes     | The event triggered when the map rendering and update are completed.                                                                  |
| bindregionchange | Event Handler   |               | No       | Yes | Yes     | The event triggered when the view changes. It will be triggered twice and return the `type` values of `begin` and `end` respectively. |
| bindpoitap       | Event Handler   |               | No       | No  | Yes     | The event triggered when the user clicks the map POI: `event.detail = {name, longitude, latitude}`                                    |

### Returned values of `regionchange`

When the view changes, `regionchange` will be triggered twice and return the type values of `begin` and `end` respectively.

`causedBy` is returned during the `begin` stage. Valid values: `gesture` (triggered by gesture); `update` (triggered by API).

`causedBy` is returned during the `end` stage. Valid values: `drag` (triggered by drag); `scale` (triggered by zoom); `update` (triggered by update API call).

`event = {causedBy, type, detail: {rotate, skew, scale, centerLocation, region}}`

### setting

The `setting` object provides map configuration.

```javascript
// javascript
// Default value
const setting = {
  rotate: 0,
  showLocation: false,
  subKey: '',
  layerStyle: 1,
  enableZoom: true,
  enableScroll: true,
  enableRotate: false,
  showCompass: false,
  enableSatellite: false,
}
this.setData({
  // Only the set attribute takes effect, while others will not be affected.
  setting: {
    enableZoom: false,
    enableScroll: false,
  }
})
```

### Marker

A marker displays the marked position in a map.

| Attribute   | Description                                                                     | Type          | Required | iOS | Android | Remarks                                                                                                                                                             |
| :---------- | :------------------------------------------------------------------------------ | :------------ | :------- | :-- | :------ | :------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| id          | Marker point id                                                                 | Number        | No       | Yes | Yes     | The marker click event callback returns this ID. It is recommended to set the number type ID for each marker to ensure better performance when updating the marker. |
| joinCluster | Participate in point aggregation                                                | Boolean       | No       | No  | Yes     | By default, itdoes not participate in point aggregation.                                                                                                            |
| latitude    | latitude                                                                        | Number        | Yes      | Yes | Yes     | Floating-point number. The value range is-90 90                                                                                                                     |
| longitude   | longitude                                                                       | Number        | Yes      | Yes | Yes     | Floating point number, range -180 180                                                                                                                               |
| title       | Calling-out                                                                     | String        | No       | Yes | Yes     | Displays when clicked, and ignored when callout exists.                                                                                                             |
| zIndex      | Display level                                                                   | Number        | No       | No  | Yes     |                                                                                                                                                                     |
| iconPath    | Display icons                                                                   | String        | Yes      | Yes | Yes     | Project directory under the picture path. It support network path, local path, code package path (2.3.0.                                                            |
| rotate      | Rotation angle                                                                  | Number        | No       | No  | Yes     | The angle of a clockwise rotation from 0 to 360. By default, it is 0.                                                                                               |
| alpha       | Annotated transparency                                                          | Number        | No       | No  | Yes     | By default, it is 1, no transparency, and scope is 0 1.                                                                                                             |
| width       | Label icon width                                                                | Number/String | No       | No  | Yes     | The default is the actual width of the image.                                                                                                                       |
| height      | Mark icon height                                                                | Number/String | No       | No  | Yes     | The default is the actual height of the image.                                                                                                                      |
| callout     | Bubble window above the marker point                                            | Object        | No       | Yes | Yes     | The supported properties are shown in the following table and are recognized as newlines.                                                                           |
| anchor      | Latitude and longitude at anchor point of callout icon, default bottom midpoint | Object        | No       | No  | Yes     | {x, y},`x` Represent horizontal(0-1)，`y` Vertical(0-1)。{x: .5, and: 1} Represents the midpoint of the bottom                                                        |

**Note: We recommend you set an ID of the `number` type for each marker for a higher performance when the marker is updated.**

### Callout above the marker

| Attribute    | Description                                      | Type   | iOS | Android |
| :----------- | :----------------------------------------------- | :----- | :-- | :------ |
| content      | Text                                             | String | Yes | Yes     |
| color        | Text color                                       | String | No  | Yes     |
| fontSize     | Text size                                        | Number | No  | Yes     |
| borderRadius | Border fillet                                    | Number | No  | Yes     |
| borderWidth  | Border width                                     | Number | No  | Yes     |
| borderColor  | Border color                                     | String | No  | Yes     |
| bgColor      | Background color                                 | String | No  | Yes     |
| padding      | Text margin                                      | Number | No  | Yes     |
| textAlign    | Text alignment. Valid value: left, right, center | String | No  | Yes     |
| anchorX      | Lateral offset, positive to the right            | Number | No  | Yes     |
| anchorY      | Vertical offset, positive downward               | Number | No  | Yes     |

### Custom callout above the marker

If `customCallout` exists, `callout` and `title` attributes will be ignored. The custom callout is customized based on `cover-view` and more flexible.

| Attribute | Description                                                        | Type   | iOS | Android | SuperHub Studio |
| :-------- | :----------------------------------------------------------------- | :----- | :-- | :------ | :-------------- |
| display   | 'BYCLICK':(click to display); `ALWAYS` (always display).           | string | No  | No      | No              |
| anchorX   | Horizontal offset. A positive value indicates to extend rightward. | number | No  | No      | No              |
| anchorY   |                                                                    | number | No  | No      | No              |

It can be used in the following way: Add a `slot` node named `callout` to the `map` component and bind its `cover-view` to marker through the `marker-id` attribute. When `marker` is created, the content shown in `cover-view` will be the `callout` above the marker.

```Text
// WXML
<map>
  <cover-view slot="callout">
    <cover-view marker-id="1"></cover-view>
    <cover-view marker-id="2"></cover-view>
  </cover-view>
</map>
```

### Callout label above the marker

| Attribute    | Description                                                                  | Type   | iOS | Android | Studio |
| :----------- | :--------------------------------------------------------------------------- | :----- | :-- | :------ | :----- |
| content      | Text                                                                         | string | No  | No      | Yes    |
| color        | Text color                                                                   | string | No  | No      | Yes    |
| fontSize     | Font size                                                                    | number | No  | No      | Yes    |
| x            | Label coordinate (disused)                                                   | number | No  | No      | No     |
| y            | Label coordinate (disused)                                                   | number | No  | No      | No     |
| anchorX      | Label coordinate, with the origin being the latitude/longitude of the marker | number | No  | No      | Yes    |
| anchorY      | Label coordinate, with the origin being the latitude/longitude of the marker | number | No  | No      | Yes    |
| borderWidth  | Border width                                                                 | number | No  | No      | Yes    |
| borderColor  | Border color                                                                 | string | No  | No      | Yes    |
| borderRadius | Border radius                                                                | number | No  | No      | Yes    |
| bgColor      | Background color                                                             | string | No  | No      | Yes    |
| padding      | Text padding                                                                 | number | No  | No      | Yes    |
| textAlign    | Text alignment mode. Valid values: `left`, `right`, `center`.                | string | No  | No      | Yes    |

### Point aggregation

When too many markers need to be shown on the map, they may overlap, which compromises the overall performance. The point aggregation feature can solve this problem.

It can be used as follows:

1. Specify the markers to be aggregated through `MapContext.addMarkers`.

<!---->

1. Remove the aggregated markers through `MapContext.removeMarkers`.

> 📘 Note
> 
> 1. On the map, the marker is divided into ordinary marker and for aggregated markers, specify properties when the value of aggregation joinCluster for is set to true. 
> 2. When you customize the cluster style, you also use the MapContext.addMarkers to draw by specifying the clusterID.

### Polyline

It specifies a series of coordinate points to connect the first to the last items in the array. When drawing a polyline, you need to specify the colors of different lines. If points contain five points, you should pass in four color values in `colorList` . If the length of `colorList` is smaller than `points.length - 1`, the colors of the remaining lines are the same as that of the last item.

| Attribute     | Description                  | Type    | Required | iOS | Android | Remarks                                                                             |
| :------------ | :--------------------------- | :------ | :------- | :-- | :------ | :---------------------------------------------------------------------------------- |
| points        | Longitude and latitude array | Array   | Yes      | Yes | Yes     | [{latitude: 0, longitude: 0}]                                                       |
| color         | The color of the line        | String  | No       | Yes | Yes     | Hexadecimal                                                                         |
| width         | Width of line                | Number  | No       | Yes | Yes     |                                                                                     |
| dottedLine    | Whether dashed lines         | Boolean | No       | Yes | Yes     | Default value: false.                                                               |
| arrowLine     | Lines with arrows            | Boolean | No       | No  | Yes     | Default value: false. This attribute is not supported by Super Hub Mini App Studio. |
| arrowIconPath | Replace Arrow Icon           | String  | No       | No  | Yes     | It takes effect if arrowLine is true .                                              |

### Polygon

It specifies a series of coordinate points to generate a closed polygon based on the `points` data.

| Attribute   | Description                  | Type   | Required | iOS | Android | Remarks                       |
| :---------- | :--------------------------- | :----- | :------- | :-- | :------ | :---------------------------- |
| points      | Longitude and latitude array | Array  | Yes      | Yes | Yes     | [{latitude: 0, longitude: 0}] |
| strokeWidth | Width of stroke              | Number | No       | Yes | Yes     | Hexadecimal                   |
| strokeColor | Stroke color                 | String | No       | Yes | Yes     | Hexadecimal                   |
| FillColor   | Fill color                   | String | No       | Yes | Yes     | Hexadecimal                   |
| zIndex      | Set polygon z-axis value     | Number |          | No  | Yes     |                               |

### Circle

Displays a circle in the map.

| Attribute   | Description     | Type   | Required | iOS | Android | Remarks                               |
| :---------- | :-------------- | :----- | :------- | :-- | :------ | :------------------------------------ |
| latitude    | latitude        | Number | Yes      | Yes | Yes     | Floating-point number, range -90 90   |
| longitude   | longitude       | Number | Yes      | Yes | Yes     | Floating-point number, range -180 180 |
| color       | Stroke color    | String | No       | Yes | Yes     | Hexadecimal                           |
| FillColor   | Fill color      | String | No       | Yes | Yes     | Hexadecimal                           |
| radius      | Radius          | Number | Yes      | Yes | Yes     |                                       |
| strokeWidth | Width of stroke | Number | No       | Yes | Yes     |                                       |

### Bindregionchange Return value

| Attribute | Description                                   | Type   | Remarks                                                                                         |
| :-------- | :-------------------------------------------- | :----- | :---------------------------------------------------------------------------------------------- |
| type      | Triggered when the view change starts or ends | String | Valid values: `begin`, `end`.                                                                   |
| causedBy  | Reason of the view change                     | String | Valid values: `drag` (caused by drag); `scale` (caused by zoom); `update` (caused by API call). |

### Scale

| Scale      | 3      | 4     | 5     | 6     | 7    | 8    | 9    | 10   | 11  |
| :--------- | :----- | :---- | :---- | :---- | :--- | :--- | :--- | :--- | :-- |
| Proportion | 1000km | 500km | 200km | 100km | 50km | 50km | 20km | 10km | 5km |
| Scale      | 12     | 13    | 14    | 15    | 16   | 17   | 18   | 19   | 20  |
| Proportion | 2km    | 1km   | 500m  | 200m  | 100m | 50m  | 50m  | 20m  | 10m |

> 📘 Notes
> 
> - Map color values (`color`, `borderColor`, and `bgColor`) should be represented by 6 or 8 hex characters. In the latter case, the last two characters indicate the alpha value, such as #000000AA.
> - The latitude and longitude of the map control are required. If they are not specified, the default value will be used, which is the latitude and longitude of Riyadh.
> - The map component uses latitude and longitude in the GCJ-02 coordinate system. Calling the `wx.getLocation` API requires specifying type as gcj02.
> - If the `enablePassiveEvent` configuration item is enabled on the page of the current component or globally, the built-in component may have unexpected behaviors. For more information, see [Global configuration](docs:global-configurations).
