---
title: "Native component"
slug: "native-component"
excerpt: "Some of the components in the Mini Program are native components created by the client."
hidden: false
metadata: 
  image: []
  robots: "index"
createdAt: "Thu Apr 13 2023 11:44:10 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Fri Jul 14 2023 11:11:14 GMT+0000 (Coordinated Universal Time)"
---
### Native Component

Some of the components are native components created by the client. These components are:

- [camera](doc:camera)
- [canvas](doc:canvas)
- [input](doc:input) - (which behaves as a native component only when in focus)
- [map](doc:map)
- [textarea](doc:text-area)
- [video](doc:video)

### Usage Restrictions of Native Components

As native components are out of the WebView rendering process, there are some restrictions when using them as follows:

- The level of a native component is highest, so other components on the page cannot overlay the native component no matter how `z-index` is set.
  - A native component inserted later can overwrite previous ones.
- Native components cannot be used in `<picker-view>`.
- Some CSS styles cannot be applied to native components, such as:
  - CSS animations cannot be set for native components.
  - Native components cannot be defined as `position: fixed`.
  - Native components cannot be used on parent nodes `overflow: hidden` To crop the display area of the native component.
- Event listeners of native components can be written only as `bindeventname` but not `bind:eventname`. Native components don't support the event binding methods of `catch` and `capture`.
- Native components will block the debug panel popped up by vConsole

> 📘 Note
> 
> In terms of tools, native components are simulated by web components, so in many cases, the performance of real devices cannot be well reproduced. We recommend you try to debug on real devices when using native components.
