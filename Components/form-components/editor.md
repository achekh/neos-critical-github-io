---
title: "Editor"
slug: "editor"
excerpt: "Rich text editor.."
hidden: false
metadata: 
  image: []
  robots: "index"
createdAt: "Fri Apr 07 2023 11:25:41 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Thu Jun 15 2023 11:16:07 GMT+0000 (Coordinated Universal Time)"
layout: "default"
parent: "Form components"
grand_parent: "Components"
nav_order: 4
---
# Editor 
Rich text editor..
*** 
Rich text editor can edit images and text.

The editor can export `html` and `text` content with tags and uses the `delta` format for storage.

When the `setContents` API is used to set the content, an error may occur when the inserted `html` is parsed due to some invalid tags. We recommend you insert it through `delta` in the mini app.

The image control can be set only during initialization.

## Attribute description

| Attribute         | Type          | Default Value | Required | Description                                                                                                            |
| :---------------- | :------------ | :------------ | :------- | :--------------------------------------------------------------------------------------------------------------------- |
| read-only         | Boolean       | false         | No       | Whether to set the editor as read-only.                                                                                |
| placeholder       | String        |               | No       | Prompt message.                                                                                                        |
| show-img-size     | Boolean       | false         | No       | Whether to show the image size when the user clicks an image.                                                          |
| show-img-toolbar  | Boolean       | false         | No       | Whether to show the toolbar when the user clicks an image.                                                             |
| show-img-resize   | Boolean       | false         | No       | Whether to show the image resize control when the user clicks an image.                                                |
| bindready         | Event Handler |               | No       | The event triggered when the editor is initialized.                                                                    |
| bindfocus         | Event Handler |               | No       | The event triggered when the editor is focused: `event.detail = {html, text, delta}`                                   |
| bindblur          | Event Handler |               | No       | The event triggered when the editor is not focused: `event.detail = {html, text, delta}`                               |
| bindinput         | Event Handler |               | No       | The event triggered when the editor content changes: `event.detail = {html, text, delta}`                              |
| bindstatuschanger | Event Handler |               | No       | The event triggered when the editor style is changed through the Context method, which will return the selected style. |

The editor supports some HTML tags and inline styles but not `class` and `id`.

### Supported hashtags

Tags not meeting the conditions will be ignored, and `<div>` tags will be converted to `<p>` tags.

| Type                | Node                                                                      |
| :------------------ | :------------------------------------------------------------------------ |
| Inline element      | `<span> <strong> <b> <ins> <em> <i> <u> <a> <del> <s> <sub> <sup> <img> ` |
| Block-level element | `<p> <h1> <h2> <h3> <h4> <h5> <h6> <hr> <ol> <ul> <li>`                   |

### Supported inline styles

| Type | Style |
| :--- | :---- |
| Block-level style | `text-align, direction, margin, margin-top, margin-left, margin-right, margin-bottom `  <br />`padding, padding-top, padding-left, padding-right, padding-bottom, line-height, text-indent` |
| Inline style | `font, font-size, font-style, font-variant, font-weight, font-family, letter-spacing, text-decoration, color, background-color ` |

> 📘 Bugs and tips
> 
> - Tip: If `catchtouchend` is used to bind an event, the editor will be focused.
> - Tip: Event bindings will be removed from the inserted HTML.
> - Tip: The `color` attributes in `formats` will be returned in `hex` format.
> - Tip: Only text content will be pasted into the editor.
> - Tip: When the HTML content is inserted into the editor, the editor will delete some unnecessary tags to ensure content consistency; for example, it will rewrite `<p><span>xxx</span></p>` to `<p>xxx</p>`.
> - Tip: When the editor is focused, the page will be pushed up, which is the system behavior performed to ensure that the editor area is visible.
