---
title: "Image"
slug: "image"
excerpt: "It is used to render an image."
hidden: false
createdAt: "Tue Apr 11 2023 10:21:14 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Wed Nov 29 2023 06:03:30 GMT+0000 (Coordinated Universal Time)"
layout: "default"
parent: "Media components"
---
The[ image ](doc:image)component supports formats such as JPG, PNG, SVG, WEBP, and GIF.

| Attribute  | Type          | Default Value | Required | Description                                                                                                                                        |
| :--------- | :------------ | :------------ | :------- | :------------------------------------------------------------------------------------------------------------------------------------------------- |
| src        | String        |               | No       | Address of the image resource.                                                                                                                     |
| mode       | String        | scaleToFill   | No       | Image scaling or cropping mode.                                                                                                                    |
| lazy-load  | Boolean       | false         | No       | Image lazy loading, which takes effect only for images of `page` and `scroll-view`.                                                                |
| binderror  | Event Handler |               | No       | The event published to `AppService` when an error occurred: `event.detail = {errMsg: 'something wrong'}`                                           |
| bindload   | Event Handler |               | No       | The event published to `AppService` when the image is completely loaded: `event.detail = {height:'Image height in px', width:'Image width in px'}` |
| aria-label | String        |               | No       | Accessibility, which is the additional description of the element.                                                                                 |

### Mode values:

mode has 13 modes: 4 zooming modes and 9 cropping modes.

| Mode | Value        | Description                                                                                                                                                                                                            |
| :--- | :----------- | :--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Zoom | scaleToFill  | The image is zoomed to fill the size of the image element by changing the aspect ratio of the image if necessary.                                                                                                      |
| Zoom | aspectFit    | The image is zoomed to completely display the long side of the image at the original aspect ratio. In other words, the entire image will be displayed.                                                                 |
| Zoom | aspectFill   | The image is zoomed to completely display the short side of the image at the original aspect ratio. In other words, the image is complete either horizontally or vertically and may be cropped in the other direction. |
| Zoom | widthFix     | The width remains unchanged and the height changes automatically at the original aspect ratio.                                                                                                                         |
| Crop | top          | The image is not zoomed and only its top area is displayed.                                                                                                                                                            |
| Crop | bottom       | The image is not zoomed and only its bottom area is displayed.                                                                                                                                                         |
| Crop | center       | The image is not zoomed and only its middle area is displayed.                                                                                                                                                         |
| Crop | left         | The image is not zoomed and only its left area is displayed.                                                                                                                                                           |
| Crop | right        | The image is not zoomed and only its right area is displayed.                                                                                                                                                          |
| Crop | top left     | The image is not zoomed and only its top-left area is displayed.                                                                                                                                                       |
| Crop | top right    | The image is not zoomed and only its top-right area is displayed.                                                                                                                                                      |
| Crop | bottom left  | The image is not zoomed and only its bottom-left area is displayed.                                                                                                                                                    |
| Crop | bottom right | The image is not zoomed and only its bottom-right area is displayed.                                                                                                                                                   |

> 📘 Notes
> 
> - The default width and height of the image component are 300 px and 225 px respectively.
> - The QR code/mini app code image in the image component cannot be recognized by pressing and holding it. The operation is supported only in `wx.previewImage`.

### Sample Code

```javascript
Page({
  data: {
    array: [{
        mode: 'scaleToFill',
        text: 'scaleToFill: The image is zoomed to fully fill the size by changing the aspect ratio of the image if necessary.'
      }, {
        mode: 'aspectFit',
        text: 'aspectFit: The image is zoomed to completely display the long side of the image at the original aspect ratio.'
      }, {
        mode: 'aspectFill',
        text: 'aspectFill: The image is zoomed to completely display the short side of the image at the original aspect ratio.'
      }, {
        mode: 'top',
        text: 'top: The image is not zoomed and only its top area is displayed.'
      }, {
        mode: 'bottom',
        text: 'bottom: The image is not zoomed and only its bottom area is displayed.'
      }, {
        mode: 'center',
        text: 'center: The image is not zoomed and only its middle area is displayed.'
      }, {
        mode: 'left',
        text: 'left: The image is not zoomed and only its left area is displayed.'
      }, {
        mode: 'right',
        text: 'right: The image is not zoomed and only its right area is displayed.'
      }, {
        mode: 'top left',
        text: 'top left: The image is not zoomed and only its top-left area is displayed.'
      }, {
        mode: 'top right',
        text: 'top right: The image is not zoomed and only its top-right area is displayed.'
      }, {
        mode: 'bottom left',
        text: 'bottom left: The image is not zoomed and only its bottom-left area is displayed.'
      }, {
        mode: 'bottom right',
        text: 'bottom right: The image is not zoomed and only its bottom-right area is displayed.'
    }],
    src: '../resources/cat.jpg'
  },
  imageError(e) {
  	console.log('An error event occurred in `image3`, and the carried value is ', e.detail.errMsg)
  }
})

```
```xml WXML
<view class="page">
  <view class="page__hd">
    <text class="page__title">image</text>
    <text class="page__desc">Image</text>
  </view>
  <view class="page__bd">
    <view class="section section_gap" wx:for="{{array}}" wx:for-item="item">
      <view class="section__title">{{item.text}}</view>
      <view class="section__ctn">
      <image
      style="width: 200px; height: 200px; background-color: #eeeeee;"
      mode="{{item.mode}}"
      src="{{src}}"
      ></image>
      </view>
    </view>
  </view>
</view>

```
