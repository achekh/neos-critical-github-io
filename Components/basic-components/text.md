---
title: "Text"
slug: "text"
excerpt: "Text field to render text."
hidden: false
metadata: 
  image: []
  robots: "index"
createdAt: "Thu Apr 06 2023 12:29:58 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Fri Jul 14 2023 11:04:50 GMT+0000 (Coordinated Universal Time)"
layout: "default"
parent: "Basic components"
grand_parent: "Components"
---
# Text 
*** 
| Attribute  | Type    | Default Value | Description                         |
| :--------- | :------ | :------------ | :---------------------------------- |
| selectable | Boolean | false         | Whether the text is selectable.     |
| space      | String  |               | Whether to show consecutive spaces. |
| decode     | Boolean | false         | Whether to decode the text.         |

## Space valid value

| Value | Description                            |
| :---- | :------------------------------------- |
| ensp  | Size of one space character            |
| emsp  | Size of two space characters           |
| nbsp  | Space size specified based on the font |

> 📘 Tips
> 
> - Decode can be parsed with   `&nbsp` `&lt` `&gt` `&amp` `&apos` `&ensp` and `&emsp`.
> - The standards for spaces vary by operating system.
> - In the `<text>` component, only `<text>` can be nested.
> - Only text nodes can be pressed and held.

### Sample Code

```javascript
const initData = 'this is first line\nthis is second line'
const extraLine = []
Page({
  data: {
  	text: initData
  },
  add(e) {
    extraLine.push('other line')
    this.setData({
    	text: initData + '\n' + extraLine.join('\n')
  	})
  },
  remove(e) {
  if (extraLine.length > 0) {
    extraLine.pop()
    this.setData({
    	text: initData + '\n' + extraLine.join('\n')
    })
    }
  }
})
```
```xml
<!--WXML-->
{% raw %}
<view class="btn-area">
  <view class="body-view">
    <text>{{text}}</text>
    <button bindtap="add">add line</button>
    <button bindtap="remove">remove line</button>
  </view>
</view>
{% endraw %}
```

![](https://files.readme.io/6484796-Screenshot_2023-06-13_at_11.44.42_AM.png)
