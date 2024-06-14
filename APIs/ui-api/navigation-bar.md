---
title: "Navigation Bar"
slug: "navigation-bar"
excerpt: "APIs to manipulate the navigation bar."
hidden: false
createdAt: "Tue Apr 18 2023 13:11:13 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Wed Nov 29 2023 08:25:51 GMT+0000 (Coordinated Universal Time)"
layout: "default"
parent: "UI"
grand_parent: "APIs"
---
# Navigation Bar 
*** 
- [setNavigationBarTitle](doc:navigation-bar#setnavigationbartitle-object-object)
- [setNavigationBarColor](doc:navigation-bar#setnavigationbarcolor-object-object)
- [hideHomeButton](doc:navigation-bar#hidehomebuttonobject-object)

# setNavigationBarTitle (Object object)

Dynamically sets the title of the current page.

# Parameters

**Object object**

| Attribute | Type     | Required | Description                                                                            |
| :-------- | :------- | :------- | :------------------------------------------------------------------------------------- |
| title     | String   | Yes      | Page title.                                                                            |
| success   | Fnction  | No       | Callback function for a successful API call.                                           |
| fail      | Function | No       | Callback function for a failed API call.                                               |
| complete  | Function | No       | Callback function for an API call end (executed for both successful and failed calls). |

```javascript JavaScript
wx.setNavigationBarTitle({
	title: 'Current page'
}
```

# setNavigationBarColor (Object object)

Sets the color of the page navigation bar.

# Parameters

**Object object**

| Attribute       | Type     | Required | Description                                                                                                             |
| :-------------- | :------- | :------- | :---------------------------------------------------------------------------------------------------------------------- |
| frontColor      | String   | Yes      | Foreground color value, including the button, title, and status bar colors. Only `#ffffff `and` #000000` are supported. |
| backgroundColor | String   | Yes      | Background color, which can be a hex color value.                                                                       |
| animation       | Object   | No       | Animation effect.                                                                                                       |
| success         | Function | No       | Callback function for a successful API call.                                                                            |
| fail            | Function | No       | Callback function for a failed API call.                                                                                |
| complete        | Function | No       | Callback function for an API call end (executed for both successful and failed calls).                                  |

## **Structure of** `object.animation`

| Attribute  | Type   | Default | Required | Description                         |
| :--------- | :----- | :------ | :------- | :---------------------------------- |
| duration   | Number | 0       | No       | Animation duration in milliseconds. |
| timingFunc | String | linear  | No       | Animation change mode.              |

## **Valid values of** `object.animation.timingFunc`

| Value     | Description                                                    |
| :-------- | :------------------------------------------------------------- |
| linear    | The speed of the animation remains the same from start to end. |
| easeIn    | The animation starts at slow speed.                            |
| easeOut   | The animation ends at a slow speed.                            |
| easeInOut | The animation starts and ends at a slow speed.                 |

### Sample code

```javascript JavaScript
wx.setNavigationBarColor({
  frontColor: '#ffffff',
  backgroundColor: '#ff0000',
  animation: {
    duration: 400,
    timingFunc: 'easeIn'
	}
})
```

# hideHomeButton(Object object)

## Feature description

Hides the "Back to Home" button on the share panel. If the bottom-level page of the Mini App opened by the user is not the homepage, the "Back to Home" button will be shown on the share panel by default. The developer can call `hideHomeButton` to hide it.

## Parameters

**Object object**

| Attribute | Type     | Required | Description                                                                            |
| :-------- | :------- | :------- | :------------------------------------------------------------------------------------- |
| success   | Function | No       | Callback function for a successful API call.                                           |
| fail      | Function | No       | Callback function for a failed API call.                                               |
| complete  | Function | No       | Callback function for an API call end (executed for both successful and failed calls). |
