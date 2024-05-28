---
title: "File structure"
slug: "file-structure"
excerpt: ""
hidden: true
metadata: 
  image: []
  robots: "index"
createdAt: "Wed Jan 11 2023 13:35:31 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Mon Feb 06 2023 14:38:11 GMT+0000 (Coordinated Universal Time)"
layout: "default"
parent: "Test - how to create a mini app"
---
The default File structure has the following elements

[block:parameters]
{
  "data": {
    "h-0": "Files",
    "h-1": "Description",
    "0-0": "**Pages**",
    "0-1": "Files, related to specific pages",
    "1-0": "page_name.js",
    "1-1": "Business logic is written in JavaScript (.js), you can use all the features in ES6 to program the Mini app.  \n  \n**_Note:_** JavaScript eval() is not supported, as you can’t run dynamic code inside the mini app",
    "2-0": "page_name.json",
    "2-1": "JSON holds the global configurations for the Mini app, such as registering pages, app name, and navigation bar styles",
    "3-0": "page_name.wxml",
    "3-1": "**WXML** - The language used to develop the structure of app pages  \n  \n- It's similar to HTML (you can use most HTML tags) and comes with extra tags like view and block.  \n- You can specify the data that will be rendered inside the file by wrapping it with 2 curly braces: `{{ data_to_render }}`.  \n- You can apply basic business logic using “if” and “for” statements inside the WXML file.",
    "4-0": "page_name.wxss",
    "4-1": "**WXSS** - The language used to style pages and views.  \n  \n- It's like CSS and you can use most CSS features.  \n- You can also import other WXSS files inside a WXSS file.  \n- WXSS depends on a new dimensions unit called RPX (responsive pixel), which renders the dimension based on the device’s resolution.  \n- WXSS only supports certain CSS selectors.",
    "5-0": "**App**",
    "5-1": "Files related to all pages",
    "6-0": "app.js",
    "6-1": "Global data ",
    "7-0": "app.json",
    "7-1": "Global configuration",
    "8-0": "app.wxss",
    "8-1": "Global styling ",
    "9-0": "project.config.json",
    "9-1": "Project compilation and upload options",
    "10-0": "README.md",
    "10-1": "Project readme file"
  },
  "cols": 2,
  "rows": 11,
  "align": [
    "left",
    "left"
  ]
}
[/block]


- [ ] Please download the files and copy them to your project folder: 

> @Yevgen to add zip file

You will see the following file structure in Mini App Studio:

![](https://files.readme.io/83dcf74-Xnip2023-01-24_17-01-09.png)
