---
title: "Interaction"
slug: "interaction"
excerpt: "APIs to display messages and actions to the user."
hidden: false
metadata: 
  robots: "index"
createdAt: "Tue Apr 18 2023 09:24:38 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Fri May 19 2023 10:41:52 GMT+0000 (Coordinated Universal Time)"
layout: "default"
parent: "UI"
grand_parent: "APIs"
---
# Interaction 
*** 
# showToast (Object object)

Displays the message prompt box.

## Parameters

**Object object**

[block:parameters]
{
  "data": {
    "h-0": "Attribute",
    "h-1": "Type",
    "h-2": "Valid Value",
    "h-3": "Default",
    "h-4": "Required",
    "h-5": "Description",
    "0-0": "title",
    "0-1": "String",
    "0-2": "",
    "0-3": "",
    "0-4": "Yes",
    "0-5": "Prompt content.",
    "1-0": "icon",
    "1-1": "String",
    "1-2": "`success`, `error`, `none`",
    "1-3": "",
    "1-4": "",
    "1-5": "**success**: Displays the success icon. In this  \ncase, the title text can contain up to 14 characters.  \n**error**: Displays the failure icon. In this case, the title text can contain up to 14 characters.  \nloading: Displays the loading icon. In this case, the title text can contain up to 14 characters.  \n**none**: Doesn't display any icon. In this case, the title text can contain up to two lines of characters.",
    "2-0": "success",
    "2-1": "No",
    "2-2": "icon",
    "2-3": "",
    "2-4": "",
    "2-5": "",
    "3-0": "image",
    "3-1": "String",
    "3-2": "",
    "3-3": "",
    "3-4": "No",
    "3-5": "Local path of the custom icon. image has a higher priority than icon.",
    "4-0": "duration",
    "4-1": "Number",
    "4-2": "",
    "4-3": "1500",
    "4-4": "No",
    "4-5": "Delay time for the prompt",
    "5-0": "mask",
    "5-1": "Boolean",
    "5-2": "",
    "5-3": "false",
    "5-4": "No",
    "5-5": "Whether to show a transparent layer to prevent touches from passing through UI canvas objects",
    "6-0": "success",
    "6-1": "Function",
    "6-2": "",
    "6-3": "",
    "6-4": "No",
    "6-5": "Callback function for successful  \nAPI call",
    "7-0": "fail",
    "7-1": "Function",
    "7-2": "",
    "7-3": "",
    "7-4": "No",
    "7-5": "Callback function for failed API call",
    "8-0": "complete",
    "8-1": "Function",
    "8-2": "",
    "8-3": "",
    "8-4": "No",
    "8-5": "Callback function for API call end  \n(executed for both successful and failed calls)"
  },
  "cols": 6,
  "rows": 9,
  "align": [
    "left",
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
wx.showToast({
  title: 'Success',
  icon: 'success',
  duration: 2000
})
```

# hideToast (Object object)

Hides the message prompt box.

# Parameters

**Object object**

| Attribute | Type     | Default | Required | Description                                                                         |
| :-------- | :------- | :------ | :------- | :---------------------------------------------------------------------------------- |
| success   | Function |         | No       | Callback function for successful API call.                                          |
| fail      | Function |         | No       | Callback function for failed API call.                                              |
| complete  | Function |         | No       | Callback function for API call end (executed for both successful and failed calls). |

> 📘 Note
> 
> - Either wx.showLoading or wx.showToast can be displayed at any time.
> - wx.showToast should be used together with wx.hideToast.

# showModal (Object object)

Shows the modal dialog box.

## Parameters

**Object object**

| Attribute    | Type     | Default  | Required | Description                                                                         |
| :----------- | :------- | :------- | :------- | :---------------------------------------------------------------------------------- |
| title        | sSring   |          | Yes      | Prompt title.                                                                       |
| content      | String   |          | No       | Prompt content.                                                                     |
| showCancel   | Boolean  | true     | No       | Whether to show the "Cancel" button.                                                |
| cancelText   | String   | Cancel   | No       | Text of the "Cancel" button, which can contain up to 8 characters.                  |
| cancelColor  | String   | # 000000 | No       | Text color of the "Cancel" button, which must be a color string in hex format.      |
| confirmText  | String   | Confirm  | No       | Text of the "Confirm" button, which can contain up to 8 characters.                 |
| confirmColor | String   | # 576B95 | No       | Text color of the "Confirm" button, which must be a color string in hex format.     |
| success      | Function |          | No       | Callback function for successful API call.                                          |
| fail         | Function |          | No       | Callback function for failed API call.                                              |
| complete     | Function |          | No       | Callback function for API call end (executed for both successful and failed calls). |

`object.success` callback function

## Parameters

**Object res**

| Attribute | Type    | Description                                                                                                                                                |
| :-------- | :------ | :--------------------------------------------------------------------------------------------------------------------------------------------------------- |
| confirm   | Boolean | `true` indicates that the user clicked "Confirm".                                                                                                          |
| cancel    | Boolean | `true` indicates that the user clicked "Cancel" (this is used on Android to distinguish between tapping outside the modal and clicking "Cancel" to close). |

```javascript
// JavaScript
wx.showModal({
  title: 'Prompt',
  content: 'This is a modal pop-up',
  success (res) {
    if (res.confirm) {
      console.log('The user clicked "Confirm"')
    } else if (res.cancel) {
      console.log('The user clicked "Cancel"')
 	 	}
	}
}
```

# showLoading (Object object)

Shows the loading prompt box. To close the prompt box, the developer need to actively call `wx.hideLoading`.

## Parameters

**Object object**

| Attribute | Type     | Default | Required | Description                                                                                    |
| :-------- | :------- | :------ | :------- | :--------------------------------------------------------------------------------------------- |
| title     | String   |         | Yes      | Prompt content.                                                                                |
| mask      | Boolean  | false   | No       | Whether to show a transparent layer to prevent touches from passing through UI canvas objects. |
| success   | Function |         | No       | Callback function for successful API call.                                                     |
| fail      | Function |         | No       | Callback function for failed API call.                                                         |
| complete  | Function |         | No       | Callback function for API call end (executed for both successful and failed calls).            |

```javascript
// JavaScript
wx.showLoading({
	title: 'Loading',
})

setTimeout(function () {
	wx.hideLoading()
}, 2000
```

# hideLoading (Object object)

Hides the loading prompt box.

## Parameters

**Object object**

| Attribute | Type     | Required | Description                                                                         |
| :-------- | :------- | :------- | :---------------------------------------------------------------------------------- |
| success   | Function | No       | Callback function for successful API call.                                          |
| fail      | Function | No       | Callback function for failed API call.                                              |
| complete  | Function | No       | Callback function for API call end (executed for both successful and failed calls). |

> 📘 Note
> 
> - Either wx.showLoading or wx.showToast can be displayed at any time.
> - wx.showLoading should be used together with wx.hideLoading.

# showActionSheet (Object object)

Shows a menu modal.

## Parameters

**Object object**

[block:parameters]
{
  "data": {
    "h-0": "Attribute",
    "h-1": "Type",
    "h-2": "Default",
    "h-3": "Required",
    "h-4": "Description",
    "0-0": "itemList",
    "0-1": "Array.<string>",
    "0-2": "",
    "0-3": "Yes",
    "0-4": "Text array of the button, which can contain up to 12 characters.",
    "1-0": "itemColor",
    "1-1": "String",
    "1-2": "# 000000",
    "1-3": "No",
    "1-4": "Text color of the button.",
    "2-0": "success",
    "2-1": "Function",
    "2-2": "",
    "2-3": "No",
    "2-4": "Callback function for successful API call.",
    "3-0": "fail",
    "3-1": "Function",
    "3-2": "",
    "3-3": "No",
    "3-4": "Callback function for failed API call.",
    "4-0": "complete",
    "4-1": "Function",
    "4-2": "",
    "4-3": "No",
    "4-4": "Callback function for API call end (executed for both successful and  \nfailed calls)."
  },
  "cols": 5,
  "rows": 5,
  "align": [
    "left",
    "left",
    "left",
    "left",
    "left"
  ]
}
[/block]


`object.success` callback function

## Parameters

**Object res**

| Attribute | Type   | Description                                                                              |
| :-------- | :----- | :--------------------------------------------------------------------------------------- |
| tapIndex  | Number | Serial number of the button clicked by the user, which starts from 0 from top to bottom. |

### Sample code

```javascript
// JavaScript
wx.showActionSheet({
  itemList: ['A', 'B', 'C'],
  success (res) {
		console.log(res.tapIndex)
	},
	fail (res) {
		console.log(res.errMsg)
	}
})
```
