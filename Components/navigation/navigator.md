---
title: "Navigator"
slug: "navigator"
excerpt: "Navigator component is used to navigate to other Mini Apps."
hidden: false
metadata: 
  image: []
  robots: "index"
createdAt: "Tue Apr 11 2023 07:05:30 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Mon May 22 2023 12:21:55 GMT+0000 (Coordinated Universal Time)"
layout: "default"
parent: "Navigation"
grand_parent: "Components"
---
# Navigator 
Navigator component is used to navigate to other Mini Apps.
*** 
Page link to another Mini App.

| Attribute              | Type          | Default Value   | Required | Description                                                                                                                                                                  |
| :--------------------- | :------------ | :-------------- | :------- | :--------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| target                 | String        | self            | No       | Target to redirect from, which is the current Mini App by default. Valid values: `self`, `miniProgram`.                                                                      |
| url                    | String        |                 | No       | Link for redirect in the current Mini App.                                                                                                                                   |
| open-type              | String        | navigate        | No       | Redirect mode.                                                                                                                                                               |
| path                   | String        |                 | No       | Opened page path. It will take effect when `target` is `miniProgram` . If it is empty, the homepage is opened.                                                               |
| extra-data             | Object        |                 | No       | Data to be passed to the target Mini App. It will take effect when `target` is `miniProgram`. The target Mini App can get the data from `App.onLaunch()` and `App.onShow()`. |
| hover-class            | String        | navigator-hover | No       | Style class when the user clicks the component. If hover-`class="none"` is set, there will be no click state effect.                                                         |
| hover-stop-propagation | Boolean       | false           | No       | Whether to prevent the ancestor node of this node from getting into the click state.                                                                                         |
| hover-start-time       | Number        | 50              | No       | How long in milliseconds the click state is triggered after the screen is pressed.                                                                                           |
| hover-stay-time        | Number        | 600             | No       | Click state retention period in milliseconds after the user lifts the finger.                                                                                                |
| bindsuccess            | Event Handler |                 | No       | Successful redirect. It will take effect when `target` is `miniProgram`.                                                                                                     |
| bindfail               | Event Handler |                 | No       | Failed redirect. It will take effect when `target` is `miniProgram`.                                                                                                         |
| bindcomplete           | Event Handler |                 | No       | Redirect completion. It will take effect when `target` is `miniProgram`.                                                                                                     |
| aria-label             | String        |                 | No       | Accessibility, which is the additional description of the element.                                                                                                           |

### Target values:

| Value       | Description       |
| :---------- | :---------------- |
| self        | Current Mini App. |
| miniProgram | Other Mini App.   |

### Open-type values:

| Value        | Description                                                              |
| :----------- | :----------------------------------------------------------------------- |
| navigate     | Corresponds to the feature of wx.navigateTo or wx.navigateToMiniProgram. |
| redirect     | Corresponds to the feature of wx.redirectTo.                             |
| switchTab    | Corresponds to the feature of wx.switchTab.                              |
| reLaunch     | Corresponds to the feature of wx.reLaunch.                               |
| navigateBack | Corresponds to the feature of wx.navigateBack.                           |

### Requiring user confirmation for redirect

Before the redirect to another Mini App, a pop-up window is added to ask for confirmation. The redirect is performed only after the confirmation. If the user click "Cancel", `fail cancel` will be returned.

> 📘 Notes
> 
> - By default, navigator-hover is `{background-color: rgba(0, 0, 0, 0.1); opacity: 0.7;}` , and the background color of the `<navigator>`subnode is opaque.

### Sample code

```javascript
// JavaScript
// redirect.js navigator.js
Page({
  onLoad(options) {
    this.setData({
    	title: options.title
    })
  }
})
```
```xml
// redirect.wxml
<view style="text-align:center">{{title}}</view>
<view>Click "Back" in the top-left corner to go back to the page at a higher level</view>
```
```xml
// navigator.wxml
<view style="text-align:center">{{title}}</view>
<view>Click "Back" in the top-left corner to go back to the previous page</view>
```
```xml
// sample.wxml
<view class="btn-area">
  <navigator
    url="/page/navigate/navigate?title=navigate"
    hover-class="navigator-hover">
  	Redirect to a new page
  </navigator>
  <navigator
    url="../../redirect/redirect/redirect?title=redirect"
    open-type="redirect"
    hover-class="other-navigator-hover">
  	Open on the current page
  </navigator>
  <navigator
    url="/page/index/index"
    open-type="switchTab"
    hover-class="other-navigator-hover">
  	Switch the tab
  </navigator>
</view>

```
```css
// WXSS
/** wxss **/
/** Modify the default click state of `navigator` **/
.navigator-hover {
	color: blue;
}
/** Add a custom style class of the click state **/
.other-navigator-hover {
	color: red;
}
```
