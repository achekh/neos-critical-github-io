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
nav_order: 1
---
# Interaction 
APIs to display messages and actions to the user.

***

# showToast (Object object)

Displays the message prompt box.

## Parameters

**Object object**

| Attribute | Type | Valid Value | Default | Required | Description |
| :-------- | :--- | :---------- | :------ | :------- | :---------- |
| title | String |  |  | Yes | Prompt content. |
| icon | String | `success`, `error`, `none` |  |  | **success**: Displays the success icon. In this  \ncase, the title text can contain up to 14 characters.  \n**error**: Displays the failure icon. In this case, the title text can contain up to 14 characters.  \nloading: Displays the loading icon. In this case, the title text can contain up to 14 characters.  \n**none**: Doesn't display any icon. In this case, the title text can contain up to two lines of characters. |
| success | No | icon |  |  |  |
| image | String |  |  | No | Local path of the custom icon. image has a higher priority than icon. |
| duration | Number |  | 1500 | No | Delay time for the prompt |
| mask | Boolean |  | false | No | Whether to show a transparent layer to prevent touches from passing through UI canvas objects |
| success | Function |  |  | No | Callback function for successful  \nAPI call |
| fail | Function |  |  | No | Callback function for failed API call |
| complete | Function |  |  | No | Callback function for API call end  \n(executed for both successful and failed calls) |

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

| Attribute | Type | Default | Required | Description |
| :-------- | :--- | :------ | :------- | :---------- |
| itemList | Array.<string> |  | Yes | Text array of the button, which can contain up to 12 characters. |
| itemColor | String | # 000000 | No | Text color of the button. |
| success | Function |  | No | Callback function for successful API call. |
| fail | Function |  | No | Callback function for failed API call. |
| complete | Function |  | No | Callback function for API call end (executed for both successful and  \nfailed calls). |

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
