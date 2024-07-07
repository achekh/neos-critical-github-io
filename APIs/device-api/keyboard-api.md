---
title: "Keyboard"
slug: "keyboard-api"
excerpt: "This section lists the list of Keyboard related APIs."
hidden: false
createdAt: "Mon Apr 24 2023 08:17:34 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Wed Nov 29 2023 18:03:13 GMT+0000 (Coordinated Universal Time)"
layout: "default"
parent: "Device"
grand_parent: "APIs"
nav_order: 8
---
# Keyboard 
This section lists the list of Keyboard related APIs.

***

- [onKeyboardHeightChange](keyboard-api#onkeyboardheightchangefunction-listener)
- [hideKeyboard](keyboard-api#hidekeyboardobject-object)
- [offKeyboardHeightChange](keyboard-api#wxoffkeyboardheightchangefunction-listener)
- [getSelectedTextRange](keyboard-api#wxgetselectedtextrangeobject-object)

# onKeyboardHeightChange(function listener)

Listens for the keyboard height change event.

# Parameters

## Function listener

Listener function for the keyboard height change event

# Parameters

**Object res**

| Attribute | Type   | Description      |
| :-------- | :----- | :--------------- |
| height    | Number | Keyboard height. |

```javascript
// JavaScript
wx.onKeyboardHeightChange(res => {
	console.log(res.height)
})
```

# hideKeyboard(Object object)

Hides the keyboard manually after it appears because of the focus in the input or text area.

# Parameters

**Object object**

| Attribute | Type     | Required | Description                                                                         |
| :-------- | :------- | :------- | :---------------------------------------------------------------------------------- |
| success   | Function | No       | Callback function for successful API call.                                          |
| fail      | Function | No       | Callback function for failed API call.                                              |
| complete  | Function | No       | Callback function for API call end (executed for both successful and failed calls). |

### Sample code

```javascript
// JavaScript
wx.hideKeyboard({
  complete: res => {
  	console.log('hideKeyboard res', res)
  }
})
```

# wx.offKeyboardHeightChange(function listener)

Unlistens for the keyboard height change event.

# Parameters

## Function listener

The listener function passed in when `onKeyboardHeightChange` is called. If this parameter is not passed in, all listener functions will be removed.

### Sample code

```javascript
// JavaScript
const listener = function (res) { console.log(res) }

wx.onKeyboardHeightChange(listener)
wx.offKeyboardHeightChange(listener) // You should pass in the same function object as for the listener.
```

# wx.getSelectedTextRange(Object object)

Gets the cursor position of the input box after `input `and `textarea` are focused. Note: This API takes effect only when the component is focused.

# Parameters

**Object object**

| Attribute | Type     | Required | Description                                                                         |
| :-------- | :------- | :------- | :---------------------------------------------------------------------------------- |
| success   | Function | No       | Callback function for successful API call.                                          |
| fail      | Function | No       | Callback function for failed API call.                                              |
| complete  | Function | No       | Callback function for API call end (executed for both successful and failed calls). |

`object.success` callback function

# Parameters

**Object res**

| Attribute | Type   | Description                                    |
| :-------- | :----- | :--------------------------------------------- |
| start     | Number | Start position of the cursor in the input box. |
| end       | Number | End position of the cursor in the input box.   |

### Sample code

```javascript
// JavaScript
wx.getSelectedTextRange({
  complete: res => {
  	console.log('getSelectedTextRange res', res.start, res.end)
  }
})
```
