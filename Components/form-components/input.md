---
title: "Input"
slug: "input"
excerpt: "The input component allows users to enter data."
hidden: false
metadata: 
  image: []
  robots: "index"
createdAt: "Mon Apr 10 2023 06:11:24 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Thu Jun 15 2023 11:21:32 GMT+0000 (Coordinated Universal Time)"
layout: "default"
parent: "Form components"
grand_parent: "Components"
---
# Input 
*** 
Input component is a native component, so you should keep in mind relevant limits when using it.

| Attribute                | Type          | Default Value     | Required | Description                                                                                                                                                                                                                            |
| :----------------------- | :------------ | :---------------- | :------- | :------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| value                    | String        |                   | Yes      | Initial content in the input box.                                                                                                                                                                                                      |
| type                     | String        | text              | No       | Input Type.                                                                                                                                                                                                                            |
| password                 | Boolean       | false             | No       | Whether the input is a password.                                                                                                                                                                                                       |
| placeholder              | String        |                   | Yes      | Placeholder when input box is empty.                                                                                                                                                                                                   |
| placeholder-style        | String        |                   | Yes      | Placeholder style.                                                                                                                                                                                                                     |
| placeholder-class        | String        | input-placeholder | No       | Placeholder style class.                                                                                                                                                                                                               |
| disabled                 | Boolean       | false             | No       | Whether it is disabled.                                                                                                                                                                                                                |
| maxlength                | Number        | 140               | No       | Maximum length of the input text. If it is set to -1 , the length is not restricted.                                                                                                                                                   |
| cursor-spacing           | Number        | 0                 | No       | Distance between the cursor and keyboard in px. The actual distance is the distance between the input component and the bottom or the value specified by `cursor-spacing`, whichever is smaller.                                       |
| auto-focus               | Boolean       | false             | No       | Whether to enable auto-focus to pull the keyboard automatically (it better to use `focus` directly.).                                                                                                                                  |
| focus                    | Boolean       | false             | No       | Whether to get the focus.                                                                                                                                                                                                              |
| confirm-type             | String        | done              | No       | Text on the button in the bottom-right corner of the keyboard, which will take effect only if `type` is text.                                                                                                                          |
| confirm-hold             | Boolean       | false             | No       | Whether to still display the keyboard after the button in the bottom-right corner of the keyboard is clicked.                                                                                                                          |
| cursor                   | Number        |                   | Yes      | Cursor position when the input box is focused on.                                                                                                                                                                                      |
| selection-start          | Number        | -1                | No       | Cursor start position, which will take effect if `auto-focus` is enabled and must be used together with `selection-end`.                                                                                                               |
| selection-end            | Number        | -1                | No       | Cursor end position, which will take effect if `auto-focus` is enabled and must be used together with `selection-start`.                                                                                                               |
| adjust-position          | Boolean       | true              | No       | Whether to automatically push up the page when the keyboard pops up.                                                                                                                                                                   |
| bindinput                | Event Handler |                   | Yes      | The event triggered when text is input through the keyboard: `event.detail = {value, cursor, keyCode} `(here, keyCode is the key value). The processing function can directly return a string to replace the content in the input box. |
| bindfocus                | Event Handler |                   | Yes      | The event triggered when the input box is focused: `event.detail = {value, height} `(here, height is the keyboard height).                                                                                                             |
| bindblur                 | Event Handler |                   | Yes      | The event triggered when the input box is not focused: `event.detail = {value: value}`.                                                                                                                                                |
| bindconfirm              | Event Handler |                   | Yes      | The event triggered when the user clicks the confirmation button: `event.detail = {value: value}`.                                                                                                                                     |
| bindkeyboardheightchange | Event Handler |                   | Yes      | The event triggered when the keyboard height changes: `event.detail = {height: height, duration: duration}`.                                                                                                                           |
| aria-label               | String        |                   | No       | Accessibility, which is the additional description of the element.                                                                                                                                                                     |

### Type valid value

| Value  | Description                        |
| :----- | :--------------------------------- |
| text   | Text input keyboard.               |
| number | Digital input keyboard.            |
| idcard | ID number input keyboard.          |
| digit  | Numeric keypad with decimal point. |

### Confirm-type valid value

| Value  | Description                                        |
| :----- | :------------------------------------------------- |
| send   | The button in the bottom-right corner is "Send".   |
| search | The button in the bottom-right corner is "Search". |
| next   | The button in the bottom-right corner is "Next".   |
| go     | The button in the bottom-right corner is "Go".     |
| done   | The button in the bottom-right corner is "Done".   |

> 📘 Notes
> 
> - The final presentation of `confirm-type` is related to the implementation of the input method of the mobile phone, which may not be supported or fully supported by the input method of some Android operating systems or third-party input methods.
> - input is a native component and the font is system font, so you cannot set `font-family`.
> - If input is focused, do not use CSS animations.
> - If input is encapsulated in the custom component but form is outside, form cannot get the input value in the custom component. In this case, you need to use built-in behaviors of the custom component wx://form-field.

### Sample code

```javascript
Page({
  data: {
    focus: false,
    inputValue: ''
  },
  bindButtonTap() {
    this.setData({
    	focus: true
  	})
  },
  bindKeyInput(e) {
    this.setData({
   		inputValue: e.detail.value
    })
  },
  bindReplaceInput(e) {
    const value = e.detail.value
    let pos = e.detail.cursor
    if (pos != -1) {
      // Cursor in the middle
      const left = e.detail.value.slice(0, pos)
      // Calculate the cursor position
      pos = left.replace(/11/g, '2').length
  	}
  // Directly return the object. You can filter the input and control the cursor position.
  return {
  	value: value.replace(/11/g, '2'),
  	cursor: pos
  }
  // Or directly return the string, with the cursor at the rear
  // return value.replace(/11/g,'2'),
  }
})

```
```xml WXML
<view class="section">
	<input placeholder="This is an input that can be automatically focused on" auto-focus />
</view>
<view class="section">
	<input placeholder="This is focused on only when the user clicks the button" focus="{{focus}}" />
<view class="btn-area">
	<button bindtap="bindButtonTap">Allows the input box to get the focus</button>
</view>
</view>
<view class="section">
	<input maxlength="10" placeholder="Maximum length: 10" />
</view>
<view class="section">
	<view class="section__title">You input: {{inputValue}}</view>
	<input bindinput="bindKeyInput" placeholder="Input synced to the view" />
</view>
<view class="section">
	<input bindinput="bindReplaceInput" placeholder="Two `1`s in a row become `2`" />
</view>
<view class="section">
	<input password type="number" />
</view>
<view class="section">
	<input password type="text" />
</view>
<view class="section">
	<input type="digit" placeholder="Numeric keypad with a decimal point" />
</view>
<view class="section">
	<input type="idcard" placeholder="ID number input keyboard" />
</view>
<view class="section">
	<input placeholder-style="color:red" placeholder="The placeholder style is red" />
</view>

```

![](https://files.readme.io/96a23d1-Screenshot_2023-06-15_at_4.51.15_PM.png)
