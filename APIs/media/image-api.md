---
title: "Image"
slug: "image-api"
excerpt: "This section consists of the list of Image related APIs in Mini App."
hidden: false
createdAt: "Thu Apr 20 2023 06:45:54 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Wed Nov 29 2023 12:59:17 GMT+0000 (Coordinated Universal Time)"
layout: "default"
parent: "Media"
grand_parent: "APIs"
---
# Image 
*** 
- [saveImageToPhotosAlbum](doc:image-api#wxsaveimagetophotosalbumobject-object)
- [previewImage](doc:image-api#wxpreviewimageobject-object)
- [getImageInfo](doc:image-api#wxgetimageinfoobject-object)
- [chooseImage](doc:image-api#chooseimage-object-object)

# chooseImage (Object object)

Chooses an image from the local album or takes a photo.

# Parameters

### Object object

[block:parameters]
{
  "data": {
    "h-0": "Attribute",
    "h-1": "Type",
    "h-2": "Valid Value",
    "h-3": "Default",
    "h-4": "Description",
    "0-0": "count",
    "0-1": "Number",
    "0-2": "",
    "0-3": "9",
    "0-4": "Maximum number of images that can be selected.",
    "1-0": "sizeType",
    "1-1": "Array",
    "1-2": "original: Original image  \ncompressed: Compressed image",
    "1-3": "['original', 'comp  \nressed']",
    "1-4": "Size of the selected image.",
    "2-0": "sourceType",
    "2-1": "Array",
    "2-2": "album: Chooses an image from the album camera: Uses the camera",
    "2-3": "['album', 'camer  \na']",
    "2-4": "Chooses the source of the image.",
    "3-0": "success",
    "3-1": "Function",
    "3-2": "",
    "3-3": "",
    "3-4": "Callback function for successful API call.",
    "4-0": "fail",
    "4-1": "Function",
    "4-2": "",
    "4-3": "",
    "4-4": "Callback function for failed API call.",
    "5-0": "complete",
    "5-1": "Function",
    "5-2": "",
    "5-3": "",
    "5-4": "Callback function for API call end (executed for both  \nsuccessful and failed calls)."
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


**`object.success` callback function**

# Parameters

**Object res**

| Attribute     | Type  | Description                                                |
| :------------ | :---- | :--------------------------------------------------------- |
| tempFilePaths | Array | List of local temporary file paths of images (local path). |
| tempFiles     | Array | List of local temporary files of images.                   |

**Structure of` res.tempFiles`**

| Attribute | Type   | Description                     |
| :-------- | :----- | :------------------------------ |
| path      | String | Temporary local file path.      |
| size      | Number | Temporary local file size in B. |

### Sample code

```javascript JavaScript
wx.chooseImage({
  count: 1,
  sizeType: ['original', 'compressed'],
  sourceType: ['album', 'camera'],
  success (res) {
    // `tempFilePath` can be used as the `src` attribute of the `img` tag to display the image.
    const tempFilePaths = res.tempFilePaths
  }
})
```

## wx.saveImageToPhotosAlbum(Object object)

> The user should 'authorize' `scope.writePhotosAlbum` before calling this API.

Saves the image to the system album.

# Parameters

### Object object

| Attribute | Type     | Required | Description                                                                                    |
| :-------- | :------- | :------- | :--------------------------------------------------------------------------------------------- |
| filePath  | String   | Yes      | Image file path, which can be a temporary or permanent file path but not an online image path. |
| success   | Function | No       | Callback function for successful API call.                                                     |
| fail      | Function | No       | Callback function for failed API call.                                                         |
| complete  | Function | No       | Callback function for API call end (executed for both successful and failed calls).            |

### Sample code

```javascript JavaScript
wx.saveImageToPhotosAlbum({
	success(res) {},
})
```

## wx.previewImage(Object object)

Previews the image in full screen mode on a new page. During the preview, the user can save or share the image.

## Parameters

### Object object

| Attribute | Type     | Default                  | Required | Description                                                                         |
| :-------- | :------- | :----------------------- | :------- | :---------------------------------------------------------------------------------- |
| urls      | Array    |                          | Yes      | List of URLs of the images to be previewed. Cloud file IDs are supported.           |
| current   | String   | The first item in `urls` | No       | URL of the currently displayed image.                                               |
| success   | Function |                          | No       | Callback function for successful API call.                                          |
| fail      | Function |                          | No       | Callback function for failed API call.                                              |
| complete  | Function |                          | No       | Callback function for API call end (executed for both successful and failed calls). |

### Sample code

```javascript JavaScript
wx.previewImage({
  current: '', // HTTP URL of the currently displayed image
  urls: [], // List of HTTP URLs of the images to be previewed
})
```

## wx.getImageInfo(Object object)

Gets the image information. For online images, you need to configure the download domain name first for this API to take effect.

# Parameters

### Object object

| Attribute | Type     | Required | Description                                                                             |
| :-------- | :------- | :------- | :-------------------------------------------------------------------------------------- |
| src       | String   | Yes      | Image path, which can be a relative, temporary file, stored file, or online image path. |
| success   | Function | No       | Callback function for successful API call.                                              |
| fail      | Function | No       | Callback function for failed API call.                                                  |
| complete  | Function | No       | Callback function for API call end (executed for both successful and failed calls).     |

`object.success` callback function

# Parameters

**Object res**

| Attribute   | Type   | Description                                                     |
| :---------- | :----- | :-------------------------------------------------------------- |
| width       | Number | Original width of the image in px. Rotation is not considered.  |
| height      | Number | Original height of the image in px. Rotation is not considered. |
| path        | String | Local path of the image.                                        |
| orientation | String | The device orientation when the photo was taken.                |
| type        | String | Image format                                                    |

Valid values of `res.orientation`

| Value          | Description                                                                                                                                         |
| :------------- | :-------------------------------------------------------------------------------------------------------------------------------------------------- |
| up             | The default orientation (holding the phone horizontally to take photos), which corresponds to `1` in Exif. Or, there is no orientation information. |
| up-mirrored    | Same as up but mirrored, which corresponds to 2 in Exif.                                                                                            |
| down           | Rotation by 180°, which corresponds to` 3` in Exif.                                                                                                 |
| down-mirrored  | Same as down but mirrored, which corresponds to `4` in Exif.                                                                                        |
| left-mirrored  | Same as left but mirrored, which corresponds to` 5` in Exif.                                                                                        |
| right          | Rotation by 90° clockwise, which corresponds to `6` in Exif.                                                                                        |
| right-mirrored | Same as right but mirrored, which corresponds to `7` in Exif.                                                                                       |
| left           | Rotation by 90° counterclockwise, which corresponds to` 8` in Exif.                                                                                 |

### Sample code

```javascript JavaScript
wx.getImageInfo({
  src: 'images/a.jpg',
  success(res) {
    console.log(res.width)
    console.log(res.height)
  },
})
wx.chooseImage({
  success(res) {
    wx.getImageInfo({
      src: res.tempFilePaths[0],
      success(res) {
        console.log(res.width)
        console.log(res.height)
      },
    })
  },
})
```
