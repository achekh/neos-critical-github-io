---
title: "Page Routing"
slug: "page-routing"
excerpt: ""
hidden: false
metadata: 
  image: []
  robots: "index"
createdAt: "Tue May 16 2023 06:54:52 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Wed Jun 07 2023 03:51:57 GMT+0000 (Coordinated Universal Time)"
layout: "default"
parent: "Logic layer"
grand_parent: "Guide"
nav_order: 2
---
# Page Routing 
*** 
The routing of all pages in a Mini App is managed by the framework.

## Page stack

The framework keeps a stack of all currently available pages. The page stack will act in the following ways when there is a routing switch:

| Routing Method   | Page Stack Behavior                            |
| :--------------- | :--------------------------------------------- |
| Initialization   | Pushes the new page.                           |
| New page opening | Pushes the new page.                           |
| Page redirection | Pops the current page and pushes the new page. |
| Page return      | Pops pages continuously till the target page.  |
| Tab switch       | Pops all pages and retains only the new tab.   |
| Reload           | Pops all pages and retains only the new page.  |

## getCurrentPages()

The `getCurrentPages()` function is used to get the instance of the current page stack, which is given in the order of the stack in the form of array. The first element in the array is the homepage, and the last one is the current page.

> 📘 Notes
> 
> - Do not try modifying the page stack; otherwise, routing and page status errors will occur.
> - Do not call `getCurrentPages()` during `App.onLaunch`, as `page` is not generated yet then.

## Routing method

The trigger method of routing and the page lifecycle functions are as follows:

| Routing Method   | Trigger Time                                                                                                                                                                  | Page Before Routing | Page After Routing  |
| :--------------- | :---------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :------------------ | :------------------ |
| Initialization   | The first page is opened by the Mini App.                                                                                                                                     |                     | onLoad, onShow      |
| New page opening | The [wx.navigateTo](../../APIs/route-api/navigate-to-api) API or the <navigator open-type="navigateTo"/> component is used.                                                                    | onHide              | onLoad, onShow      |
| Page redirection | The [wx.redirectTo](../../APIs/route-api/redirect-to-api) API is called or the <navigator open-type="redirectTo"/> component is used.                                                          | onUnload            | onLoad, onShow      |
| Page return      | The [wx.navigateBack](../../APIs/route-api/navigate-back-api) API is called, the <navigator open-type="navigateBack"> component is used, or the back button in the top-left corner is clicked. | onUnload            | onShow              |
| Tab switch       | The [wx.switchTab](../../APIs/route-api/switch-tab-api) API is called, the <navigator open-type="switchTab"/> component is used, or the tab is switched.                                       |                     | See the table below |
| Relaunch         | The [wx.reLaunch](../../APIs/route-api/relaunch-api) API is called, or the <navigator open-type="reLaunch"/> component is used.                                                                | onUnload            | onLoad, onShow      |

The lifecycle corresponding to tab switch (in the following example, pages A and B are tabBar pages, page C is opened from page A, and page D is opened from page C):

| Current Page                | Page After Routing | Triggered Lifecycle Functions (Sequentially)       |
| :-------------------------- | :----------------- | :------------------------------------------------- |
| A                           | A                  | Nothing happened                                   |
| A                           | B                  | A.onHide(), B.onLoad(), B.onShow()                 |
| A                           | B (opened again)   | A.onHide(), B.onShow()                             |
| C                           | A                  | C.onUnload(), A.onShow()                           |
| C                           | B                  | C.onUnload(), B.onLoad(), B.onShow()               |
| D                           | B                  | D.onUnload(), C.onUnload(), B.onLoad(), B.onShow() |
| D (entered from forwarding) | A                  | D.onUnload(), A.onLoad(), A.onShow()               |
| D (entered from forwarding) | B                  | D.onUnload(), B.onLoad(), B.onShow()               |

> 📘 Notes
> 
> - `navigateTo` and `redirectTo` can open only non-tabbar pages.
> - `switchTab` can open only tabbar pages.
> - `reLaunch` can open any page.
> - The tabBar at the bottom of a page is determined by the page; that is, as long as a page is defined as a tabbar page, it will have a tabbar at the bottom.
> - The parameters carried when page routing is called can be obtained from the `onLoad` of the target page.

## File scope

Variables and functions declared in a JavaScript file are only valid in the file. Variables and functions with the same name can be declared in different files without affecting each other.

The global application instance can be obtained through the global function `getApp()`. If you need global data, you can set it in `App()`.

For example:

```javascript
// javascript
// app.js
App({
  globalData: 1
})
```

```javascript
// javascript
// a.js
// The localValue can only be used in file a.js.
const localValue = 'a'
// Get the app instance.
const app = getApp()
// Get the global data and change it.
app.globalData++
```

```javascript
// javascript
// b.js
// You can redefine localValue in file b.js, without interference with the localValue in a.js.
const localValue = 'b'
// If a.js it run before b.js, now the globalData shoule be 2.
console.log(getApp().globalData)
```

## Module

Some common code can be extracted into a separate JS file as a module. Modules can only expose APIs through `module.exports` or `exports`.

> 📘 Notes
> 
> - As exports is a reference to `module.exports`, arbitrarily changing the pointer of `exports` in the module will cause unknown errors. Therefore, we recommend you use `module.exports` to expose module APIs, unless you already know the relationship between the two.
> - Mini Apps currently don't support directly importing `node_modules` . When you need to use it, we recommend you copy the relevant code to the directory of the Mini App or use the npm feature supported by the Mini App.
> 
> ```javascript
> // common.js
> function sayHello(name) {
>   console.log(`Hello ${name} !`)
> }
> function sayGoodbye(name) {
>   console.log(`Goodbye ${name} !`)
> }
> module.exports.sayHello = sayHello
> exports.sayGoodbye = sayGoodbye
> ```

In the files that need to use these modules, use require(path) to import the common code:

```javascript
// javascript
const common = require('common.js')
Page({
  helloMINA() {
    common.sayHello('MINA')
  },
  goodbyeMINA() {
    common.sayGoodbye('MINA')
  }
})
```

> 📘 Notes
> 
> - `require` currently doesn't support absolute paths.
