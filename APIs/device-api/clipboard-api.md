---
title: "Clipboard"
slug: "clipboard-api"
excerpt: "This section lists the Clipboard related APIs."
hidden: false
createdAt: "Mon Apr 24 2023 08:08:58 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Wed Nov 29 2023 18:01:09 GMT+0000 (Coordinated Universal Time)"
layout: "default"
parent: "Device"
---
- [setClipboardData](doc:clipboard-api#wxsetclipboarddataobject-object)
- [getClipboardData](doc:clipboard-api#wxgetclipboarddataobject-object)

# wx.setClipboardData(Object object)

Sets the content in the system clipboard. This API should be called for no more than once per second for a single user.

# Parameters

**Object object**

| Attribute | Type     | Required | Description                                                                         |
| :-------- | :------- | :------- | :---------------------------------------------------------------------------------- |
| data      | String   | Yes      | Content to be added to the clipboard.                                               |
| success   | Function | No       | Callback function for successful API call.                                          |
| fail      | Function | No       | Callback function for failed API call.                                              |
| complete  | Function | No       | Callback function for API call end (executed for both successful and failed calls). |

### Sample code

```javascript JavaScript
wx.setClipboardData({
  data: 'data',
  success(res) {
    wx.getClipboardData({
      success(res) {
     		console.log(res.data) // data
      }
    })
  }
})
```

# wx.getClipboardData(Object object)

Gets the content in the system clipboard. This API should be called for no more than once per second for a single user.

# Parameters

**Object object**

| Attribute | Type     | Required | Description                                                                         |
| :-------- | :------- | :------- | :---------------------------------------------------------------------------------- |
| success   | Function | No       | Callback function for successful API call.                                          |
| fail      | Function | No       | Callback function for failed API call.                                              |
| complete  | Function | No       | Callback function for API call end (executed for both successful and failed calls). |

`object.success` callback function

# Parameters

**Object object**

| Attribute | Type   | Description               |
| :-------- | :----- | :------------------------ |
| data      | String | Content in the clipboard. |

### Sample code

```javascript JavaScript
wx.getClipboardData({
  success(res) {
  	console.log(res.data)
  }
})
```
