---
title: "Add title"
slug: "add-title-1"
excerpt: "This section explains the procedure to add a title to the pages in Mini App."
hidden: true
metadata: 
  image: []
  robots: "index"
createdAt: "Tue Feb 07 2023 09:27:53 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Wed Feb 22 2023 11:09:39 GMT+0000 (Coordinated Universal Time)"
layout: "default"
parent: "Meet the MiniApp"
---
# Add title 
This section explains the procedure to add a title to the pages in Mini App.

***

To add **"Near me"** title for all pages, please:

- Copy the code snippet below to the global JSON object inside `app.json`

```Text
// app.json
"window":{
    "backgroundTextStyle":"light",
    "navigationBarBackgroundColor": "#fff",
    "navigationBarTitleText": "Near me",
    "navigationBarTextStyle":"black"
},
```

- After adding the above code to the existing code (code for register pages) your `app.json` file should look like the one below.

```Text
// app.json
{
  "pages":[
    "pages/map/map",
    "pages/list/list",
    "pages/about/about"
  ],
  "window":{
    "backgroundTextStyle":"light",
    "navigationBarBackgroundColor": "#fff",
    "navigationBarTitleText": "Near me",
    "navigationBarTextStyle":"black"
  }
}
```

3. Your page in the preview window should now have a title **Near me** as shown in the screenshot below.

![](https://files.readme.io/6ac9fe6-image.png)

> 👍 Can you see the same? Well done!

> 👨‍💻 **Need help?**
> 
> If you are looking for help, try [Developer Support](<>) or our [Developer Forum](<>).

> 📄 Feedback: How can we improve the documentation?
> 
> Please use the Reader Comments form at the end of this page to communicate your feedback to us or to suggest changes that will support improvements to our documentation. Try to be specific and detailed as possible.
