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
---
# Checkbox-group 
*** 
Checkbox-group is a multiple selector that internally consists of multiple [checkboxes](doc:checkbox).

[block:parameters]
{
  "data": {
    "h-0": "Attribute",
    "h-1": "Type",
    "h-2": "Required",
    "h-3": "Description",
    "0-0": "bindchange",
    "0-1": "Event Handler",
    "0-2": "No",
    "0-3": "Triggers change event when a check box item checked state changes.  \n`event.detail = {value:[Array of values for the selected checkbox]}`"
  },
  "cols": 4,
  "rows": 1,
  "align": [
    "left",
    "left",
    "left",
    "left"
  ]
}
[/block]


### Sample code

```javascript
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
