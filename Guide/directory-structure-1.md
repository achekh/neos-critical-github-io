---
title: "Directory Structure"
slug: "directory-structure-1"
excerpt: ""
hidden: false
metadata: 
  image: []
  robots: "index"
createdAt: "Fri May 12 2023 11:11:06 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Fri Jul 14 2023 11:28:01 GMT+0000 (Coordinated Universal Time)"
layout: "default"
parent: "Guide"
---
# Directory Structure 
*** 
A Mini App consist of an `app` describing the entire app and multiple `pages` describing respective pages.

The main part of a Mini App consists of three files which must be placed in the root directory of the project: These three files are listed below:

| File                                       | Required | Purpose                               |
| :----------------------------------------- | :------- | :------------------------------------ |
| [app.js](doc:logic-layer-section#mini-app) | Yes      | Mini App logic.                       |
| [app.json](doc:global-configuration)       | Yes      | Common configuration of the Mini App. |
| [app.wxss](doc:wxss)                       | No       | Common style sheet of the Mini App.   |

A mini app page consists of four files:

| File                               | Required | Purpose             |
| :--------------------------------- | :------- | :------------------ |
| [js](doc:logic-layer-section#page) | Yes      | Page logic.         |
| [wxml](doc:wxml)                   | Yes      | Page structure.     |
| [json](doc:page-configuration)     | Yes      | Page configuration. |
| [wxss](doc:wxss)                   | No       | Page style sheet.   |

> 📘 Note:
> 
> The four page's files must have the same path and name as described above.

## Files allowed for upload

In the project directory, the following files are compiled and thus cannot be accessed directly after upload: \*.js, app.json, \*.wxml, and \*.wxss ( `wxml` and `wxss` are only for pages configured in `app.json`). In addition, only files with extensions in the allowlist uploads. The specific allowlist is as follows:

1. qs
2. png
3. jpg
4. jpeg
5. gif
6. svg
7. json
8. cer
9. mp3
10. aac
11. m4a
12. mp4
13. wav
14. ogg
15. silk
