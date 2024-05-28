---
title: "Response to Display Area Change"
slug: "response-to-display-area-change"
excerpt: ""
hidden: false
metadata: 
  image: []
  robots: "index"
createdAt: "Tue May 23 2023 11:19:05 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Thu Jun 08 2023 10:25:40 GMT+0000 (Coordinated Universal Time)"
layout: "default"
parent: "View Layer"
grand_parent: "Guide"
---
## Display area size

The display area refers to the area in the Mini App UI that can be freely arranged and displayed. By default, the size of the Mini App display area does not change after the page is initialized. However, this default behavior can be changed in two ways.

## Enabling screen rotation support on a phone

The Mini App supports screen rotation on phones. The method of supporting screen rotation for the Mini App page is as follows: Set `"pageOrientation": "auto"` in the `window` section of `app.json`, or set `"pageOrientation": "auto"` in the `json` file of the page.

Below is an example of enabling screen rotation in a single page's `json` file.

### Sample code:

```json
{
  "pageOrientation": "auto"
}
```

If the above statement is added to the page, when the screen rotates, the page will rotate accordingly, and the size of the display area will also change. `pageOrientation` can also be set to landscape to fix the screen in `landscape` mode.

## Enabling screen rotation support on iPad

The Mini App supports screen rotation on iPad. The method of supporting iPad screen rotation for the Mini App is as follows: Add `"resizable": true` in `app.json`.

### Sample code:

```json
{
  "resizable": true
}
```

If the above statement is added to the Mini App, when the screen rotates, the mini app will rotate accordingly, and the size of the display area will also change. Note: You cannot configure screen rotation support for individual pages on iPad.

## Media query

Sometimes, the page layout varies by display area size. In this case, a media query can be used to solve most issues.

### Sample code:

```css WXSS
.my-class {
  width: 40px;
}
@media (min-width: 480px) {
  /* Style rules that take effect only on screens of 480 px or wider */
  .my-class {
    width: 200px;
  }
}
```

## Screen rotation event

Sometimes, some fine layout changes cannot be controlled by just using media query. In this case, JS can be used.

To read the display area size of the page in JS, use selectorQuery.selectViewport.

Events that change the page size can be listened for by using the page's `onResize`. For custom components, you can use the resize lifecycle for listening. The callback function will return the size information of the display area.

### Sample code:

```javascript
Page({
  onResize(res) {
    res.size.windowWidth // New display area width
    res.size.windowHeight // New display area height
  }
})
```

```javascript
Component({
  pageLifetimes: {
    resize(res) {
      res.size.windowWidth // New display area width
      res.size.windowHeight // New display area height
		} 
  }
})
```

In addition, you can also use [`wx.onWindowResize`] for listening, which is not recommended though.
