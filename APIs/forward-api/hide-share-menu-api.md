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
---
# hideShareMenu (Object object) 
*** 
Hide the "Share with Friends" and "Share to Qzone" buttons when the menu in the top-right corner is clicked.

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
    "0-0": "hideShareItems",
    "0-1": "Array.<string>",
    "0-2": "['qq', 'qzone',  \n]",
    "0-3": "No",
    "0-4": "'qq', and 'qzone' control whether to hide \"Forward\", and \"Share to Qzone\", \" respectively. If the `hideShareItems` parameter is not carried, all the options will be hidden.",
    "1-0": "success",
    "1-1": "Function",
    "1-2": "",
    "1-3": "No",
    "1-4": "Callback function for successful API call.",
    "2-0": "fail",
    "2-1": "Function",
    "2-2": "",
    "2-3": "No",
    "2-4": "Callback function for failed API call.",
    "3-0": "complete",
    "3-1": "Function",
    "3-2": "",
    "3-3": "No",
    "3-4": "Callback function for API call end (executed for both successful and failed calls)."
  },
  "cols": 5,
  "rows": 4,
  "align": [
    "left",
    "left",
    "left",
    "left",
    "left"
  ]
}
[/block]


### Sample code

```javascript
// JavaScript
wx.hideShareMenu({
	hideShareItems: ['qq', 'qzone', 'wechatFriends', 'wechatMoment']
})
```
