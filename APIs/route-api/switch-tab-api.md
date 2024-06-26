---
title: "switchTab (Object object)"
slug: "switch-tab-api"
excerpt: "Redirects to the tab bar page and closes all other non-tab bar pages."
hidden: false
metadata: 
  image: []
  robots: "index"
createdAt: "Mon Apr 17 2023 10:55:51 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Fri Jul 14 2023 11:13:19 GMT+0000 (Coordinated Universal Time)"
layout: "default"
parent: "Route"
grand_parent: "APIs"
---
# switchTab (Object object) 
Redirects to the tab bar page and closes all other non-tab bar pages.
*** 
# Parameters

**Object object**

| Attribute | Type     | Required | Description                                                                                                                                                                               |
| :-------- | :------- | :------- | :---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| url       | String   | Yes      | Path of the tabbar page to be redirected to (code package path, i.e., the page that needs to be defined in the tabBar field of `app.json`). There can't be any parameters after the path. |
| success   | Function | No       | Callback function for a successful API call.                                                                                                                                              |
| fail      | Function | No       | Callback function for a failed API call.                                                                                                                                                  |
| complete  | Function | No       | Callback function for an API call end (executed for both successful and failed calls).                                                                                                    |

### Sample code

```Text
// app.json
// app.json
{
	"tabBar": {
		"list": [
      {
        "pagePath": "index",
        "text": "Homepage"
     },
     {
       "pagePath": "other",
       "text": "Other"
     }
   ]
	}
}
```
```javascript
// page.js
wx.switchTab({
  url: '/index'
})
```
