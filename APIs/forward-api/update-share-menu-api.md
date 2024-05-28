---
title: "updateShareMenu (Object object)"
slug: "update-share-menu-api"
excerpt: "Updates the share attribute."
hidden: false
metadata: 
  image: []
  robots: "index"
createdAt: "Tue May 02 2023 10:44:45 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Fri Jul 14 2023 11:15:21 GMT+0000 (Coordinated Universal Time)"
layout: "default"
parent: "Forward"
---
# Parameters

**Object object**

| Attribute       | Type     | Default | Required | Description                                                                            |
| :-------------- | :------- | :------ | :------- | :------------------------------------------------------------------------------------- |
| withShareTicket | Foolean  | false   | No       | Whether to forward with `shareTicket`.                                                 |
| success         | Function |         | No       | Callback function for a successful API call.                                           |
| fail            | Function |         | No       | Callback function for a failed API call.                                               |
| complete        | Function |         | No       | Callback function for an API call end (executed for both successful and failed calls). |

### Sample code

```javascript JavaScript
wx.updateShareMenu({
	withShareTicket: true
})
```
