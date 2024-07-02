---
title: "hideShareMenu (Object object)"
slug: "hide-share-menu-api"
excerpt: "Hides the share button on the current page."
hidden: false
metadata: 
  image: []
  robots: "index"
createdAt: "Tue Apr 18 2023 06:19:03 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Fri Jul 14 2023 11:15:42 GMT+0000 (Coordinated Universal Time)"
layout: "default"
parent: "Forward"
grand_parent: "APIs"
nav_order: 3
---
# hideShareMenu (Object object) 
Hides the share button on the current page.

***

Hide the "Share with Friends" and "Share to Qzone" buttons when the menu in the top-right corner is clicked.

# Parameters

**Object object**

| Attribute | Type | Default | Required | Description |
| :-------- | :--- | :------ | :------- | :---------- |
| hideShareItems | Array.<string> | ['qq', 'qzone', ] | No | 'qq', and 'qzone' control whether to hide \"Forward\", and \"Share to Qzone\", \" respectively. If the `hideShareItems` parameter is not carried, all the options will be hidden. |
| success | Function |  | No | Callback function for successful API call. |
| fail | Function |  | No | Callback function for failed API call. |
| complete | Function |  | No | Callback function for API call end (executed for both successful and failed calls). |

### Sample code

```javascript
// JavaScript
wx.hideShareMenu({
	hideShareItems: ['qq', 'qzone', 'wechatFriends', 'wechatMoment']
})
```
