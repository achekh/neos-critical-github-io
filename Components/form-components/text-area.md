---
title: "Textarea"
slug: "text-area"
excerpt: "Multi-line plain text input box used to collect user input."
hidden: false
metadata: 
  image: []
  robots: "index"
createdAt: "Mon Apr 10 2023 12:58:27 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Fri Jul 14 2023 11:08:27 GMT+0000 (Coordinated Universal Time)"
layout: "default"
parent: "Form components"
grand_parent: "Components"
---
This component is a native component; hence it is important to know the limitations when using it.

| Attribute         | Type          | Default Value        | Description                                                                                                                                                                                                                                                                                              |
| :---------------- | :------------ | :------------------- | :------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| value             | String        |                      | Content in the input box.                                                                                                                                                                                                                                                                                |
| placeholder       | String        |                      | Placeholder when the input box is empty.                                                                                                                                                                                                                                                                 |
| placeholder-style | String        |                      | Placeholder style. Valid values: `color`, `font-size` and `font-weight`.                                                                                                                                                                                                                                 |
| placeholder-class | String        | textarea-placeholder | Placeholder style class.                                                                                                                                                                                                                                                                                 |
| disabled          | Boolean       | false                | Whether it is disabled.                                                                                                                                                                                                                                                                                  |
| maxlength         | Number        | 140                  | Maximum length of the input text. If it is set to `-1` , the length is not restricted.                                                                                                                                                                                                                   |
| auto-focus        | Boolean       | false                | Whether to enable auto-focus to pull the keyboard automatically.                                                                                                                                                                                                                                         |
| focus             | Boolean       | false                | Whether to get the focus.                                                                                                                                                                                                                                                                                |
| auto-height       | Boolean       | false                | Whether to enable automatic height adjustment for the input box. If `auto-height` is set, `style`.  `height` will not take effect.                                                                                                                                                                       |
| fixed             | Boolean       | false                | If `textarea` is in a region with `position:fixed` , `fixed` should be set to `true`.                                                                                                                                                                                                                    |
| cursor-spacing    | Number        | 0                    | Distance between the cursor and keyboard in px. The actual distance is the distance between the textarea component and the bottom or the value specified by `cursor-spacing`, whichever is smaller.                                                                                                      |
| cursor            | Number        | -1                   | Cursor position when the input box is focused on.                                                                                                                                                                                                                                                        |
| show-confirm-bar  | Boolean       | true                 | Whether to show the bar with the "Done" button above the keyboard.                                                                                                                                                                                                                                       |
| selection-start   | Number        | -1                   | Cursor start position, which will take effect if `auto-focus` is enabled and must be used together with `selection-end`.                                                                                                                                                                                 |
| selection-end     | Number        | -1                   | Cursor end position, which will take effect if `auto-focus` is enabled and must be used together with `selection-start`.                                                                                                                                                                                 |
| adjust-position   | Boolean       | true                 | Whether to automatically push up the page when the keyboard pops up.                                                                                                                                                                                                                                     |
| bindfocus         | Event Handler |                      | The event triggered when the input box is focused: `event.detail = {value, height}` (here, `height` is the keyboard height).                                                                                                                                                                             |
| bindblur          | Event Handler |                      | The event triggered when the input box is not focused: `event.detail = {value, cursor}`.                                                                                                                                                                                                                 |
| bindlinechange    | Event Handler |                      | The event called when the number of lines in the input box changes: `event.detail = {height: 0, heightRpx: 0, lineCount: 0}`.                                                                                                                                                                            |
| bindinput         | Event Handler |                      | The `input` event triggered when text is input through the keyboard: `event.detail = {value, cursor, keyCode}` (here, `keyCode` is the key value). Currently, the `keyCode` parameter cannot be returned. The returned value of the `bindinput` processing function will not be reflected in `textarea`. |
| bindconfirm       | Event Handler |                      | The event triggered when the user clicks the confirmation button: `event.detail = {value: value}`.                                                                                                                                                                                                       |
| aria-label        | String        |                      | Accessibility, which is the additional description of the element.                                                                                                                                                                                                                                       |

> 📘 Notes
> 
> - The `blur` event of textarea will be called after the tap event on the page. If you need to get `textarea` from the button click event, use `bindsubmit` of form.
> - Do not modify user input in multi-line text, as the `bindinput` processing function of `textarea` will not reflect the returned value in `textarea`.

### Sample code

```javascript JavaScript
Page({
  data: {
    height: 20,
    focus: false
  },
  bindButtonTap: function() {
    this.setData({
      focus: true
    })
  },
  bindTextAreaBlur: function(e) {
    console.log(e.detail.value)
  },
  bindFormSubmit: function(e) {
    console.log(e.detail.value.textarea)
  }
})
```
```xml WXML
<view class="section">
  <textarea bindblur="bindTextAreaBlur" auto-height Placeholder = "auto high" />
</view>
<view class="section">
  <textarea Placeholder = "Placeholder color is red" placeholder-style="color:red"  />
</view>
<view class="section">
  <textarea Placeholder = "This is an autofocus textarea" auto-focus />
</view>
<view class="section">
  <textarea Placeholder = "This only focuses when the on is clicked" focus="{{focus}}" />
  <view class="btn-area">
    <button bindtap="bindButtonTap">Make the input field focus</button>
  </view>
</view>
<view class="section">
  <form bindsubmit="bindFormSubmit">
    <textarea placeholder="form to hit the target textarea" name="textarea"/>
    <button form-type="submit"> submit </button>
  </form>
</view>
```
