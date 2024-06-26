---
title: "Checkbox-group"
slug: "checkbox-group"
excerpt: "Checkbox-group is a container that consists of multiple checkbox components."
hidden: false
metadata: 
  image: []
  robots: "index"
createdAt: "Fri Apr 07 2023 07:29:17 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Fri Jul 14 2023 11:05:48 GMT+0000 (Coordinated Universal Time)"
layout: "default"
parent: "Form components"
grand_parent: "Components"
nav_order: 3
---
# Checkbox-group 
Checkbox-group is a container that consists of multiple checkbox components.
*** 
Checkbox-group is a multiple selector that internally consists of multiple [checkboxes](doc:checkbox).

| Attribute | Type | Required | Description |
| :-------- | :--- | :------- | :---------- |
| bindchange | Event Handler | No | Triggers change event when a check box item checked state changes.  <br />`event.detail = {value:[Array of values for the selected checkbox]}`" |

### Sample code

```javascript
// javascript
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
  checkboxChange(e) {
  	console.log('A change event occurred in `checkbox`, and the carried value is ', e.detail.value)
  }
})
```
```xml
<!--WXML-->
{% raw %}
<checkbox-group bindchange="checkboxChange">
  <label class="checkbox" wx.for="{{items}}">
  	<checkbox value="{{item.name}}" checked="{{item.checked}}" />
  	{{item.value}}
  </label>
</checkbox-group>
{% endraw %}
```
