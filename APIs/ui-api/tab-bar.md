---
title: "Tab Bar"
slug: "tab-bar"
excerpt: "Show, hide and set the tab bar and items in it."
hidden: false
createdAt: "Tue May 02 2023 10:47:49 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Wed Nov 29 2023 08:32:56 GMT+0000 (Coordinated Universal Time)"
---
- [showTabBar](doc:tab-bar#showtabbar-object-object)
- [hideTabBar](doc:tab-bar#hidetabbar-object-object)
- [setTabBarStyle](doc:tab-bar#settabbarstyle-object-object)
- [setTabBarItem](doc:tab-bar#settabbaritem-object-object)
- [showTabBarRedDot](doc:tab-bar#wxshowtabbarreddotobject-object)
- [hideTabBarRedDot](doc:tab-bar#wxhidetabbarreddotobject-object)
- [setTabBarBadge](doc:tab-bar#wxsettabbarbadgeobject-object)
- [removeTabBarBadge](doc:tab-bar#wxremovetabbarbadgeobject-object)

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

```javascript JavaScript
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

[block:parameters]
{
  "data": {
    "h-0": "Attribute",
    "h-1": "Type",
    "h-2": "Required",
    "h-3": "Description",
    "0-0": "index",
    "0-1": "Number",
    "0-2": "Yes",
    "0-3": "Number of the item on the tab bar; counted from the left.",
    "1-0": "text",
    "1-1": "String",
    "1-2": "No",
    "1-3": "Button text on the tab.",
    "2-0": "iconPath",
    "2-1": "String",
    "2-2": "No",
    "2-3": "Image path. The icon file size cannot exceed 40 KB. The recommended icon size is 81\\*81 px.  \nWhen `position` is `top`, this parameter won't take effect.",
    "3-0": "selectedIconPath",
    "3-1": "String",
    "3-2": "No",
    "3-3": "Image path when selected. The icon file size cannot exceed 40 KB. The recommended icon size is 81\\*81 px. When `position` is `top`, this parameter won't take effect.",
    "4-0": "success",
    "4-1": "Function",
    "4-2": "No",
    "4-3": "Callback function for a successful API call.",
    "5-0": "fail",
    "5-1": "Function",
    "5-2": "No",
    "5-3": "Callback function for a failed API call.",
    "6-0": "complete",
    "6-1": "Function",
    "6-2": "No",
    "6-3": "Callback function for an API call end (executed for both successful and failed calls)."
  },
  "cols": 4,
  "rows": 7,
  "align": [
    "left",
    "left",
    "left",
    "left"
  ]
}
[/block]


### Sample code

```javascript JavaScript
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

```javascript JavaScript
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
