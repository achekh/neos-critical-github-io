---
title: "Switch"
slug: "switch"
excerpt: "Used for switching between two states; on and off."
hidden: false
metadata: 
  image: []
  robots: "index"
createdAt: "Mon Apr 10 2023 12:51:14 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Fri Jul 14 2023 11:07:56 GMT+0000 (Coordinated Universal Time)"
layout: "default"
parent: "Form components"
grand_parent: "Components"
nav_order: 14
---
# Switch 
Used for switching between two states; on and off.

***

A switch component functions similar to a checkbox component but explicitly representing boolean on and off states.

| Attribute  | Type         | Default Value | Required | Description                                                                                                           |
| :--------- | :----------- | :------------ | :------- | :-------------------------------------------------------------------------------------------------------------------- |
| checked    | Boolean      | false         | No       | Whether it is selected.                                                                                               |
| disabled   | Boolean      | false         | No       | Whether it is disabled.                                                                                               |
| type       | String       | switch        | No       | Style. Valid values: `switch`, `checkbox`.                                                                            |
| color      | String       | # 04BE02      | No       | Switch color, which uses the same color specifications of CSS.                                                        |
| bindchange | Eventhandler |               | No       | This event is triggered when the value of checked changes: Events, `event.detail ={value}`.                           |
| aria-label | String       |               | No       | The `change` event triggered when the component is clicked and the value of `checked` changes: `event.detail={value}` |

### Sample code

```javascript
// JavaScript
Page({
  switch1Change(e) {
  	console.log('A change event occurred in `switch1`, and the carried value is ', e.detail.value)
  },
  switch2Change(e) {
  	console.log('A change event occurred in `switch2`, and the carried value is ', e.detail.value)
  }
})
```
```xml
<!--WXML-->
{% raw %}
<view class="body-view">
  <switch checked bindchange="switch1Change" />
  <switch bindchange="switch2Change" />
</view>
{% endraw %}
```

> 📘 Notes
> 
> - Changing the switch type will generate the vibration feedback on iOS, which can be disabled from "Settings" > "Sounds & Haptics" > "System Haptics".

![](../../assets/images/9b8b98a-Screenshot_2023-06-15_at_5.19.18_PM.png)
