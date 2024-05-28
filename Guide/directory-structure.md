---
title: "Directory Structure"
slug: "directory-structure"
excerpt: "This section explains the concept of Directory Structure."
hidden: true
metadata: 
  robots: "index"
createdAt: "Thu Apr 27 2023 07:25:27 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Wed May 03 2023 10:12:54 GMT+0000 (Coordinated Universal Time)"
layout: "default"
parent: "Guide"
---
The Mini Program comes with an `app` directory that describes the overall program and consists of multiple `page` directories to describe the respective pages.

The main part of a Mini Program is composed of below three files that must be placed in the project’s root directory:

| File     | Required | Description                             |
| :------- | :------- | :-------------------------------------- |
| app.js   | Yes      | Mini Program logic.                     |
| app.json | Yes      | Common configurations for Mini Program. |
| app.wxss | No       | Common style sheet for Mini Program.    |

A Mini Program page is composed of four files:

| File Type | Required | Description        |
| :-------- | :------- | :----------------- |
| js        | Yes      | Page logic         |
| wxml      | Yes      | Page structure     |
| json      | No       | Page configuration |
| wxss      | No       | Page style sheet   |

> 📘 Note
> 
> To reduce the number of configuration items dealt by the developers, the four files that describe a page must have identical paths and file names.

## Files allowed for upload

In the project directory, the following files are compiled and thus cannot be accessed directly after they are uploaded: _\*.js, app.json, \_\_.wxml, and _.wxss (wxml and wxss are only for pages configured in app.json). In addition to these file types, only files with suffixes in the following whitelist can be uploaded:

1. wxs
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
