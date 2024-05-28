---
title: "showShareMenu (Object object)"
slug: "show-share-menu-api"
excerpt: "Updates the share attribute."
hidden: false
metadata: 
  image: []
  robots: "index"
createdAt: "Tue Apr 18 2023 06:15:10 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Fri Jul 14 2023 11:15:33 GMT+0000 (Coordinated Universal Time)"
layout: "default"
parent: "Forward"
grand_parent: "APIs"
---
# Parameters

**Object object**

| Attribute       | Type     | Default | Description                                                                         |
| :-------------- | :------- | :------ | :---------------------------------------------------------------------------------- |
| withShareTicket | Boolean  | false   | Whether to forward with `shareTicket`.                                              |
| success         | Function |         | Callback function for a successful API call.                                        |
| fail            | Function |         | Callback function for a failed API call.                                            |
| complete        | Function |         | Callback function for API call end (executed for both successful and failed calls). |

### Sample code

```javascript JavaScript
wx.showShareMenu({
	withShareTicket: true
})
```
