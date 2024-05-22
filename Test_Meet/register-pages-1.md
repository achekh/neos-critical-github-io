---
title: "Register pages"
slug: "register-pages-1"
excerpt: "This section walks you through the process of registering pages in various files."
hidden: true
metadata: 
  image: []
  robots: "index"
createdAt: "Tue Feb 07 2023 07:10:41 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Fri Feb 10 2023 14:44:03 GMT+0000 (Coordinated Universal Time)"
---
> 📝 Note
> 
> Copy the code snippets below and paste it into Mini App Studio and press **ctrl/cmd + S** to save.

### Register pages in `app.json`:

 Please make sure to add the snippet inside the global JSON object inside the file.

```Text app.json
 "pages":[
    "pages/map/map",
    "pages/list/list",
    "pages/about/about"
],
```

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/f074e43-Register_Page_1.PNG",
        null,
        "app.json"
      ],
      "align": "center",
      "sizing": "70% ",
      "border": true,
      "caption": "app.json"
    }
  ]
}
[/block]


### Register pages in their own `<page name>.json files`

```Text about.json
{
  "usingComponents": {}
}
```
```Text list.json
{
  "usingComponents": {}
}
```
```Text map.json
{
  "usingComponents": {}
}
```

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/716f31a-Register_Page_2.PNG",
        null,
        "about.json"
      ],
      "align": "center",
      "border": true,
      "caption": "about.json"
    }
  ]
}
[/block]


***

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/e726661-Register_Page_3.PNG",
        null,
        "list.json"
      ],
      "align": "center",
      "border": true,
      "caption": "list.json"
    }
  ]
}
[/block]


***

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/1271d79-Register_Page_4.PNG",
        null,
        "map.json"
      ],
      "align": "center",
      "border": true,
      "caption": "map.json"
    }
  ]
}
[/block]


### Add Global styling to `app.wxss`.

```Text app.wxss
.container {
  height: 100%;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: space-between;
  padding: 20rpx 0;
  box-sizing: border-box;
}
```

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/14d03be-Register_Page_5.PNG",
        null,
        "app.wxss"
      ],
      "align": "center",
      "border": true,
      "caption": "app.wxss"
    }
  ]
}
[/block]
