---
title: "Progress"
slug: "progress"
excerpt: "Progress bar component."
hidden: false
metadata: 
  image: []
  robots: "index"
createdAt: "Thu Apr 06 2023 09:58:36 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Fri Jul 14 2023 11:04:38 GMT+0000 (Coordinated Universal Time)"
---
[block:parameters]
{
  "data": {
    "h-0": "Attribute",
    "h-1": "Type",
    "h-2": "Default Value",
    "h-3": "Required",
    "h-4": "Description",
    "0-0": "percent",
    "0-1": "Number",
    "0-2": "",
    "0-3": "No",
    "0-4": "Percentage between 0 and 100.",
    "1-0": "show-info",
    "1-1": "Boolean",
    "1-2": "false",
    "1-3": "No",
    "1-4": "Whether to show the percentage on the right of the progress bar.",
    "2-0": "border-radius",
    "2-1": "Number/String",
    "2-2": "0",
    "2-3": "No",
    "2-4": "Rounded corner size in px.",
    "3-0": "font-size",
    "3-1": "Number/String",
    "3-2": "16",
    "3-3": "No",
    "3-4": "Font size in px of the percentage displayed on the right.",
    "4-0": "stroke-width",
    "4-1": "Number/String",
    "4-2": "6",
    "4-3": "No",
    "4-4": "Progress bar width in px.",
    "5-0": "color",
    "5-1": "String",
    "5-2": "# 09BB07",
    "5-3": "No",
    "5-4": "Progress bar color (use active Color)",
    "6-0": "activeColor",
    "6-1": "String",
    "6-2": "# 09BB07",
    "6-3": "No",
    "6-4": "Color of the progress bar indicator.",
    "7-0": "backgroundColor",
    "7-1": "String",
    "7-2": "# EBEBEB",
    "7-3": "No",
    "7-4": "Color of the progress bar track.",
    "8-0": "active",
    "8-1": "Boolean",
    "8-2": "false",
    "8-3": "No",
    "8-4": "Progress bar animation moving from left to right.",
    "9-0": "active-mode",
    "9-1": "String",
    "9-2": "backwards",
    "9-3": "No",
    "9-4": "`backwards`: Plays the animation from the start.  \n`forwards`: Plays the animation from where it ended.",
    "10-0": "bindactiveend",
    "10-1": "Event handler",
    "10-2": "",
    "10-3": "No",
    "10-4": "Animation completion event.",
    "11-0": "aria-label",
    "11-1": "String",
    "11-2": "",
    "11-3": "No",
    "11-4": "Accessibility, which is the additional description of the element."
  },
  "cols": 5,
  "rows": 12,
  "align": [
    "left",
    "left",
    "left",
    "left",
    "left"
  ]
}
[/block]


### Sample code

```xml WXML
<view class="progress-box">
  <progress percent="20" show-info stroke-width="3"/>
</view>

<view class="progress-box">
  <progress percent="40" active stroke-width="3" />
  <icon class="progress-cancel" type="cancel"></icon>
</view>

<view class="progress-box">
  <progress percent="60" active stroke-width="3" />
</view>

<view class="progress-box">
  <progress percent="80" color="#10AEFF" active stroke-width="3" />
</view>
```

![](https://files.readme.io/78fb0ac-Screenshot_2023-06-13_at_11.41.31_AM.png)
