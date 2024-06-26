---
title: "Checkbox"
slug: "checkbox"
excerpt: "Checkbox element is used as a component to select multiple items."
hidden: false
metadata: 
  image: []
  robots: "index"
createdAt: "Fri Apr 07 2023 10:31:16 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Thu Jun 15 2023 11:10:48 GMT+0000 (Coordinated Universal Time)"
layout: "default"
parent: "Form components"
grand_parent: "Components"
nav_order: 2
---
# Checkbox 
Checkbox element is used as a component to select multiple items.

***


| Attribute  | Type    | Default Value | Required | Description                                                                                                                                                             |
| :--------- | :------ | :------------ | :------- | :---------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| value      | String  |               | No       | It represents the checkbox ID. When the checkbox is selected, a change event will occur in [checkbox-group](checkbox-group), which will hold the value of checkbox. |
| disabled   | Boolean | False         | No       | Whether it is disabled.                                                                                                                                                 |
| checked    | Boolean | False         | No       | Whether the checkbox is selected. It can be used to set the checkbox to be selected by default.                                                                         |
| color      | String  | # 09BB07      | No       | It represents the checkbox color, which uses the same color specifications of CSS.                                                                                      |
| aria-label | String  |               | No       | Accessibility, which is the additional description of the element.                                                                                                      |

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
