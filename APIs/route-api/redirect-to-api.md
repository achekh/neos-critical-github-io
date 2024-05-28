---
title: "redirectTo(Object object)"
slug: "redirect-to-api"
excerpt: "Closes the current page and jumps to another page within the Mini App. However, jumping to the tabbar page is not allowed."
hidden: false
metadata: 
  image: []
  robots: "index"
createdAt: "Mon Apr 17 2023 11:02:32 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Fri Jul 14 2023 11:13:44 GMT+0000 (Coordinated Universal Time)"
layout: "default"
parent: "Route"
---
# Parameters

**Object object**

[block:parameters]
{
  "data": {
    "h-0": "Attribute",
    "h-1": "Type",
    "h-2": "Required",
    "h-3": "Description",
    "0-0": "url",
    "0-1": "String",
    "0-2": "Yes",
    "0-3": "Path of the non-tab bar page in the app to redirect to (code package path), which can be followed by parameters.  \nUse `?` to separate the path and parameters, use `=` to concatenate a parameter key and value, and use `&` to separate parameters, such as `path?key=value&key2=value\n2`.",
    "1-0": "success",
    "1-1": "Function",
    "1-2": "No",
    "1-3": "Callback function for a successful API call.",
    "2-0": "fail",
    "2-1": "Function",
    "2-2": "No",
    "2-3": "Callback function for a failed API call.",
    "3-0": "complete",
    "3-1": "Function",
    "3-2": "No",
    "3-3": "Callback function for API call end (executed for both successful and failed calls)."
  },
  "cols": 4,
  "rows": 4,
  "align": [
    "left",
    "left",
    "left",
    "left"
  ]
}
[/block]


### Sample code

```javascript page2.js
wx.redirectTo({
	url: 'page1?id=1'
})
```
