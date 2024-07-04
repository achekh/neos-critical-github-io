---
title: "Tab Bar"
slug: "tab-bar"
excerpt: "Show, hide and set the tab bar and items in it."
hidden: false
createdAt: "Tue May 02 2023 10:47:49 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Wed Nov 29 2023 08:32:56 GMT+0000 (Coordinated Universal Time)"
layout: "default"
parent: "UI"
grand_parent: "APIs"
nav_order: 4
---
# Tab Bar 
Show, hide and set the tab bar and items in it.

***

- [showTabBar](tab-bar#showtabbar-object-object)
- [hideTabBar](tab-bar#hidetabbar-object-object)
- [setTabBarStyle](tab-bar#settabbarstyle-object-object)
- [setTabBarItem](tab-bar#settabbaritem-object-object)
- [showTabBarRedDot](tab-bar#wxshowtabbarreddotobject-object)
- [hideTabBarRedDot](tab-bar#wxhidetabbarreddotobject-object)
- [setTabBarBadge](tab-bar#wxsettabbarbadgeobject-object)
- [removeTabBarBadge](tab-bar#wxremovetabbarbadgeobject-object)

# showTabBar (Object object)

Shows the tab bar.

# Parameters

**Object object**

| Attribute | Type     | Default | Required | Description                                                                            |
| :-------- | :------- | :------ | :------- | :------------------------------------------------------------------------------------- |
| animation | Boolean  | false   | No       | Whether an animation effect is needed.                                                 |
| success   | Function |         | No       | Callback function for a successful API call.                                           |
| fail      | Function |         | No       | Callback function for a failed API call.                                               |
| complete  | Function |         | No       | Callback function for an API call end (executed for both successful and failed calls). |

# hideTabBar (Object object)

Hides the tab bar.

# Parameters

**Object object**

| Attribute | Type     | Default | Required | Description                                                                            |
| :-------- | :------- | :------ | :------- | :------------------------------------------------------------------------------------- |
| animation | Boolean  | false   | No       | Whether an animation effect is needed.                                                 |
| success   | Function |         | No       | Callback function for a successful API call                                            |
| fail      | Function |         | No       | Callback function for a failed API call                                                |
| complete  | Function |         | No       | Callback function for an API call end (executed for both successful and failed calls). |

# setTabBarStyle (Object object)

Dynamically sets the overall style of the tab bar.

# Parameters

**Object object**

| Attribute       | Type     | Required | Description                                                                            |
| :-------------- | :------- | :------- | :------------------------------------------------------------------------------------- |
| color           | String   | No       | Default color of the text on the tab, which must be a hex color.                       |
| selectedColor   | String   | No       | Color of the selected text on the tab, which must be a hex color.                      |
| backgroundColor | String   | No       | Background color of the tab, which must be a hex color.                                |
| borderStyle     | String   | No       | Color of the top border on the tab bar, which can only be black or white.              |
| success         | Function | No       | Callback function for a successful API call.                                           |
| fail            | Function | No       | Callback function for a failed API call.                                               |
| complete        | Function | No       | Callback function for an API call end (executed for both successful and failed calls). |

### Sample code

```javascript
// JavaScript
wx.setTabBarStyle({
  color: '#FF0000',
  selectedColor: '#00FF00',
  backgroundColor: '#0000FF',
  borderStyle: 'white'
})
```

# setTabBarItem (Object object)

Dynamically sets the content of a tab bar item.

# Parameters

**Object object**

| Attribute | Type | Required | Description |
| :-------- | :--- | :------- | :---------- |
| index | Number | Yes | Number of the item on the tab bar; counted from the left. |
| text | String | No | Button text on the tab. |
| iconPath | String | No | Image path. The icon file size cannot exceed 40 KB. The recommended icon size is 81\\*81 px.  \nWhen `position` is `top`, this parameter won't take effect. |
| selectedIconPath | String | No | Image path when selected. The icon file size cannot exceed 40 KB. The recommended icon size is 81\\*81 px. When `position` is `top`, this parameter won't take effect. |
| success | Function | No | Callback function for a successful API call. |
| fail | Function | No | Callback function for a failed API call. |
| complete | Function | No | Callback function for an API call end (executed for both successful and failed calls). |

### Sample code

```javascript
// JavaScript
wx.setTabBarItem({
  index: 0,
  text: 'text',
  iconPath: '/path/to/iconPath',
  selectedIconPath: '/path/to/selectedIconPath'
})
```

## wx.showTabBarRedDot(Object object)

Shows the red dot in the top-right corner of an item on the tab bar.

# Parameters

**Object object**

| Attribute | Type     | Required | Description                                                                            |
| :-------- | :------- | :------- | :------------------------------------------------------------------------------------- |
| index     | Number   | Yes      | Number of the item on the tab bar; counted from the left.                              |
| success   | Function | No       | Callback function for a successful API call.                                           |
| fail      | Function | No       | Callback function for a failed API call.                                               |
| complete  | Function | No       | Callback function for an API call end (executed for both successful and failed calls). |

## wx.setTabBarBadge(Object object)

Adds text in the top-right corner of an item on the tab bar.

# Parameters

**Object object**

| Attribute | Type     | Required | Description                                                                            |
| :-------- | :------- | :------- | :------------------------------------------------------------------------------------- |
| index     | Number   | Yes      | Number of the item on the tab bar; counted from the left.                              |
| text      | String   | Yes      | The shown text, which will be displayed as ... if it contains more than 8 characters.  |
| success   | Function | No       | Callback function for a successful API call.                                           |
| fail      | Function | No       | Callback function for a failed API call.                                               |
| complete  | Function | No       | Callback function for an API call end (executed for both successful and failed calls). |

### Sample code

```javascript
// JavaScript
wx.setTabBarBadge({
  index: 0,
  text: '1'
})
```

## wx.removeTabBarBadge(Object object)

Removes the text in the top-right corner of an item on the tab bar.

# Parameters

**Object object**

| Attribute | Type     | Required | Description                                                                            |
| :-------- | :------- | :------- | :------------------------------------------------------------------------------------- |
| index     | Number   | Yes      | Number of the item on the tab bar; counted from the left.                              |
| success   | Function | No       | Callback function for a successful API call.                                           |
| fail      | Function | No       | Callback function for a failed API call.                                               |
| complete  | Function | No       | Callback function for an API call end (executed for both successful and failed calls). |

## wx.hideTabBarRedDot(Object object)

Hides the red dot in the top-right corner of an item on the tab bar.

# Parameters

**Object object**

| Attribute | Type     | Required | Description                                                                            |
| :-------- | :------- | :------- | :------------------------------------------------------------------------------------- |
| index     | Number   | Yes      | Number of the item on the tab bar; counted from the left.                              |
| success   | Function | No       | Callback function for a successful API call.                                           |
| fail      | Function | No       | Callback function for a failed API call.                                               |
| complete  | Function | No       | Callback function for an API call end (executed for both successful and failed calls). |
