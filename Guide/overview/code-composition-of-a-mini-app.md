---
title: "Code Composition of a Mini App"
slug: "code-composition-of-a-mini-app"
excerpt: "This chapter explains the code composition of a Mini Program."
hidden: true
metadata: 
  robots: "index"
createdAt: "Thu Apr 27 2023 06:34:23 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Wed May 03 2023 10:11:44 GMT+0000 (Coordinated Universal Time)"
layout: "default"
parent: "Overview"
grand_parent: "Guide"
---
# Code Composition of a Mini App 
This chapter explains the code composition of a Mini Program.

***

​In the previous chapter, we quickly created a QuickStart project via Mini App DevTools, where the following types of files are generated:

- `JSON` configuration files suffixed with` .json`
- `WXML` template files suffixed with `.wxml`
- `WXSS` style files suffixed with` .wxss`
- `JS` script logic files suffixed with` .js`

Now let us have a look at the use of these files.

# JSON Configuration

JSON is a data format, rather than a programming language. In the Mini Program, JSON is used for static configuration.

The following sections describe the use of  `app.json` and `project.config.json` in the root directory of the project and `logs.json` in the `pages/logs` directory.

## app.json for Mini Program Configuration

`app.json` is used for the global configuration of the Mini Program by setting all the page paths, interface behaviors, network timeouts, and bottom tabs. The `app.json` is configured in the QuickStart project as below:

```Text
// code
{
  "pages":[
    "pages/index/index",
    "pages/logs/logs"
  ],
  "window":{
    "backgroundTextStyle":"light",
    "navigationBarBackgroundColor": "#fff",
    "navigationBarTitleText": "Weixin",
    "navigationBarTextStyle":"black"
  }
}
```

Meaning of each configuration item:

- The `pages` field - describes all the page paths of the Mini Program, so that the Weixin app knows the directory where your Mini Program page is defined.
- The `window` field - defines the background color and text color at the top of all pages in the Mini Program.

For more information on other configuration items, see app.json for Mini Program configuration.

## project.config.json for Tool Configuration

When using a tool, you would make custom configurations to the interface color, compilation options, and others based on your preference. When you install the tool on another computer, you should repeat these steps again.

For this reason, the Mini Program DevTools creates a `project.config.json` in the root directory of each project. Any configuration made to the tool will be written to this file. Therefore, when you reinstall the tool or use it on another computer, you must load the code package of the project, and the Mini Program DevTools will automatically restore the customized settings done at the time of project development, such as the color of the editor, the option to compress the code automatically during upload, and others.

For details, see Mini App DevTools Configuration.

## page.json for Page Configuration

`page.json` is used for page-related configuration of the Mini Program, for example, the logs.json under the pages/logs directory.

If you want the entire Mini Program in blue color, you can specify the top color as blue in app.json. However, this may not be the same scenario as you may want to use different colors for different pages to indicate different function modules. Therefore, page.json is provided to allow developers to define the properties of each page separately, such as the top color, the option to enable "Pull Down to Refresh", and others.

For more information on other configuration items, see Page Configuration.

## JSON Syntax

**Note**: The following points are important regarding JSON configuration in the Mini Program.

1. JSON files are wrapped in curly brackets ({}), containing data in the form of key-value pairs.
2. JSON keys must be enclosed in double quotes.
3. Values in JSON files must be in one of the following data formats. Any other format will trigger an error, such as "undefined" in JavaScript.
   1. Numbers, including floating-point numbers and integers.
   2. Strings enclosed in double quotes.
   3. Booleans with a value of true or false.
   4. Arrays enclosed in square brackets (\[]).
   5. Objects enclosed in curly brackets ({}).
   6. Null

It is also important to note that the JSON files do not support comments. Adding comments will trigger an error.

# WXML Template

All web page programmers know that web pages are built using HTML, CSS and JavaScript, where `HTML` describes the structure of the page, `CSS` determines the appearance of the page, and `JS` defines the interaction between the page and the user.

Similar roles exist in the Mini Program, where `WXML` is the equivalent of `HTML`. By opening `pages/index/index.wxml`, the following option displays:

```Text
// code
<view class="container">
  <view class="userinfo">
    <button wx:if="{{!hasUserInfo && canIUse}}"> Get profile photo and alias </button>
    <block wx:else>
      <image src="{{userInfo.avatarUrl}}" background-size="cover"></image>
      <text class="userinfo-nickname">{{userInfo.nickName}}</text>
    </block>
  </view>
  <view class="usermotto">
    <text class="user-motto">{{motto}}</text>
  </view>
</view>
```

Similar to `HTML`, `WXML` consists of tags and properties. However, there are also some differences, shown as below:

1. Tag names are different.  
   div, p and span are three most commonly used tags when writing HTML, which can be combined in different ways to create different components, such as calendars and pop-ups. Since these common components are required in almost all scenarios, we can put them into packages to improve development efficiency.  
   In the above example, the WXML of the Mini Program uses view, button and text tags. In addition to these native basic capabilities, we also provide packaged component capabilities like map, video and audio.  
   For more information on components, see the next chapter Mini Program Capabilities.
2. Properties like `wx:if` and expressions like are added  
   When developing web pages, we generally manipulate DOM (the tree generated from the description of `HTML`) with `JS` to allow the interface to respond to users' behaviors. For example, when a user clicks a button, `JS` records the states in `JS `variables and manipulates DOM properties or behaviors via the DOM API to trigger changes in the interface. However, as the project gets more and more complex, your code will be full of interface interaction logic and program state variables, which is not conducive to development. Therefore, the MVVM developer mode (e.g., React, Vue) is created to separate rendering from logic. To put it simply, instead of manipulating DOM directly, JS only needs to manage the states, and describes the relationship between states and interface structure via another template syntax.  
   This also applies to the framework of the Mini Program. If you want to display the Hello World string in the interface:  
   Write the WXML as follows:

   ```Text code
   <text>{{msg}}</text>
   ```

   Use JS to manage the state only: 

   ```Text code
   this.setData({ msg: "Hello World" })
   ```

   The process that binds a variable to the interface via the  syntax is called data binding. Data binding is not enough to describe the relationship between states and interface. Control capabilities such as `if/else` and` for` are required, which are expressed with properties that start with `wx:` in the Mini Program.

Refer to [WXML](<>) for more details.

# WXSS Style

`WXSS` has most of the features of CSS but incorporates some new features and modifications for the Mini Program.

1. New size unit is added. When writing the `CSS` style, developers need to convert the pixel units to adapt to different mobile device screens with different widths and pixel ratios. `WXSS` supports the new `rpx` unit at its underlying layer, allowing the Mini Program to take over the job from developers and convert the units at the underlying layer. Since the units are converted using floating-point operations, the result may deviate slightly from the expected one.
2. Global and local styles are provided. Similar to the above `app.json` and page.json, app.wxss can be written as the global style, which applies to all the pages of the Mini Program. The local page style page.wxss only applies to the current page.
3. `WXSS` only supports certain `CSS` selectors

Refer to [WXSS](<>) for more details.

# JS Logic Interaction

It's not enough for a service to just display the interface. Interaction with users is required, such as responding to user's clicks and obtaining user's location. In the Mini Program, we process user's operations by writing JS scripts.

```Text
// code
<view>{{ msg }}</view>
<button bindtap="clickMe">Click me</button>
```

When a `button` is clicked, we want to display `msg` as `"Hello World"` on the interface. To do this, we declare the `bindtap` property on the `button` and the clickMe method in the JS file to respond to this click:

```Text
// code
Page({
  clickMe: function() {
    this.setData({ msg: "Hello World" })
  }
})
```

It's just so easy to respond to user's operations. For more information on events, see WXML - Events.

You can also use a wide range of APIs provided by the Mini Program in JS, allowing you to easily call the capabilities provided by Weixin, such as access to user information, local storage and WeChat Pay. In the previous QuickStart example, [wx.getUserInfo]\((wx.getUserInfo) is called at `pages/index/index.js` to obtain the profile photo and alias of Weixin user. The obtained information is then displayed on the interface via `setData`. For more APIs, see Mini Program APIs.

In this chapter, you've learned the different types of files and their roles in the Mini Program. In the next chapter, we will integrate all these files via the framework of the Mini Program to make them work.
