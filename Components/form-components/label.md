---
title: "Label"
slug: "label"
excerpt: "Used to improve the usability of form components."
hidden: false
metadata: 
  image: []
  robots: "index"
createdAt: "Mon Apr 10 2023 08:36:54 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Thu Jun 15 2023 11:24:44 GMT+0000 (Coordinated Universal Time)"
layout: "default"
parent: "Form components"
grand_parent: "Components"
---
You can use the `for` attribute to match the corresponding ID or place the target control under the label. In this case, when the user clicks the label, the target control will be triggered. for has a higher priority than internal controls. If there are multiple internal controls, the first one will be triggered by default. Currently, the following controls can be bound: [button](doc:button), [checkbox](doc:checkbox), [radio](doc:radio), [switch](doc:switch), and [input](doc:input).

| Attribute | Type   | Required | Description              |
| :-------- | :----- | :------- | :----------------------- |
| for       | String | No       | ID of the bound control. |

### Sample code

```javascript
Page({
  data: {
    checkboxItems: [
      {name: 'USA', value: 'United States'},
      {name: 'CHN', value: 'China', checked: 'true'},
      {name: 'BRA', value: 'Brazil'},
      {name: 'JPN', value: 'Japan', checked: 'true'},
      {name: 'ENG', value: 'United Kingdom'},
      {name: 'TUR', value: 'Turkey'},
    ],
    radioItems: [
      {name: 'USA', value: 'United States'},
      {name: 'CHN', value: 'China', checked: 'true'},
      {name: 'BRA', value: 'Brazil'},
      {name: 'JPN', value: 'Japan'},
      {name: 'ENG', value: 'United Kingdom'},
      {name: 'TUR', value: 'Turkey'},
    ],
    hidden: false
  },
  checkboxChange(e) {
    const checked = e.detail.value
    const changed = {}
    for (let i = 0; i < this.data.checkboxItems.length; i++) {
      if (checked.indexOf(this.data.checkboxItems[i].name) !== -1) {
      	changed['checkboxItems[' + i + '].checked'] = true
      } else {
      	changed['checkboxItems[' + i + '].checked'] = false
      }
    }
  this.setData(changed)
  },
  radioChange(e) {
    const checked = e.detail.value
    const changed = {}
    for (let i = 0; i < this.data.radioItems.length; i++) {
      if (checked.indexOf(this.data.radioItems[i].name) !== -1) {
      	changed['radioItems[' + i + '].checked'] = true
      } else {
      	changed['radioItems[' + i + '].checked'] = false
      }
    }
    this.setData(changed)
  }
})

```
```xml WXML
<view class="section section_gap">
  <view class="section__title">The form component is in the label</view>
  <checkbox-group class="group" bindchange="checkboxChange">
  	<view class="label-1" wx.for="{{checkboxItems}}">
      <label>
        <checkbox
        hidden
        value="{{item.name}}"
        checked="{{item.checked}}"
        ></checkbox>
        <view class="label-1__icon">
          <view
          class="label-1__icon-checked"
          style="opacity:{{item.checked ? 1: 0}}"
          ></view>
        </view>
        <text class="label-1__text">{{item.value}}</text>
      </label>
  	</view>
  </checkbox-group>
  </view>
  <view class="section section_gap">
  	<view class="section__title">The label uses `for` to identify the form component</view>
  	<radio-group class="group" bindchange="radioChange">
      <view class="label-2" wx.for="{{radioItems}}">
        <radio
        id="{{item.name}}"
        hidden
        value="{{item.name}}"
        checked="{{item.checked}}"
        ></radio>
      <view class="label-2__icon">
      <view
      class="label-2__icon-checked"
      style="opacity:{{item.checked ? 1: 0}}"
      ></view>
  		</view>
    <label class="label-2__text" for="{{item.name}}">
    <text>{{item.name}}</text>
    </label>
  	</view>
  </radio-group>
</view>

```
```css WXSS
.label-1,
.label-2 {
	margin-bottom: 15px;
}
.label-1__text,
.label-2__text {
  display: inline-block;
  vertical-align: middle;
}
.label-1__icon {
  position: relative;
  margin-right: 10px;
  display: inline-block;
  vertical-align: middle;
  width: 18px;
  height: 18px;
  background: #fcfff4;
}
.label-1__icon-checked {
  position: absolute;
  top: 3px;
  left: 3px;
  width: 12px;
  height: 12px;
  background: #1aad19;
}
.label-2__icon {
  position: relative;
  display: inline-block;
  vertical-align: middle;
  margin-right: 10px;
  width: 18px;
  height: 18px;
  background: #fcfff4;
  border-radius: 50px;
}
.label-2__icon-checked {
  position: absolute;
  left: 3px;
  top: 3px;
  width: 12px;
  height: 12px;
  background: #1aad19;
  border-radius: 50%;
}
.label-4_text {
  text-align: center;
  margin-top: 15px;
}
```
