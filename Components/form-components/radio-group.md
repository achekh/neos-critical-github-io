---
title: "Radio-group"
slug: "radio-group"
excerpt: "Radio group is a selector that can select only one option from a given set of options."
hidden: false
metadata: 
  image: []
  robots: "index"
createdAt: "Mon Apr 10 2023 12:31:49 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Thu Jun 15 2023 11:47:10 GMT+0000 (Coordinated Universal Time)"
layout: "default"
parent: "Form components"
grand_parent: "Components"
nav_order: 12
---
# Radio-group 
Radio group is a selector that can select only one option from a given set of options.

***

Radio group is composed of multiple radio components.

| Attribute  | Type          | Required | Description                                                                                                                                                     |
| :--------- | :------------ | :------- | :-------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| bindchange | Event Handler | No       | The change `event` triggered when the status of an option in the `radio-group` component changes: `event.detail = {value:[array of values of selected radios]}` |

### Sample code

```javascript
// JavaScript
Page({
  data: {
    items: [
      {name: 'USA', value: 'United States'},
      {name: 'CHN', value: 'China', checked: 'true'},
      {name: 'BRA', value: 'Brazil'},
      {name: 'JPN', value: 'Japan'},
      {name: 'ENG', value: 'United Kingdom'},
      {name: 'TUR', value: 'France'},
    ]
  },
  radioChange(e) {
  	console.log('A change event occurred in `radio`, and the carried value is ', e.detail.value)
  }
})

```
```xml
<!--WXML-->
{% raw %}
<radio-group class="radio-group" bindchange="radioChange">
  <label class="radio" wx.for="{{items}}">
  <radio value="{{item.name}}" checked="{{item.checked}}" />
  	{{item.value}}
  </label>
</radio-group>
{% endraw %}
```

![](../../assets/images/164e159-Screenshot_2023-06-15_at_5.16.50_PM.png)
