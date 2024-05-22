---
title: "View Layer"
slug: "view-layer"
excerpt: "This section explains the concept of View Layer in Mini Program Framework."
hidden: true
metadata: 
  robots: "index"
createdAt: "Mon May 01 2023 09:05:07 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Wed May 03 2023 10:15:47 GMT+0000 (Coordinated Universal Time)"
---
You can also use the createAnimation API to create simple animation effects dynamically.If the above declaration is added to the Mini Program, the Mini Program page rotates, and the display area is resized as the screen rotates. Note: You cannot enable or disable screen rotation for a single page.The current component bound to the event.The view layer of the framework is written using WXML and WXSS and presented by components.

The data at the logic layer is rendered in a view, and the events at the view layer are sent to the logic layer.

WXML (WeiXin Markup language) is used to describe the page structure.

WXS (WeiXin Script) is a scripting language for Mini Programs. Combined with `WXML`, it can be used to construct the page structure.

WXSS (WeiXin Style Sheet) is used to describe the page style.

Components are the building blocks of a view.

# WXML

WXML (WeiXin Markup Language) is a markup language for framework design. It can be used to build the page structure when combined with base components and event system.

For more information on WXML syntax, see WXML syntax.

The following examples show what WXML can do:

## Data Binding

```Text code
<!--wxml-->
<view> {{message}} </view>
```

```Text code
// page.js
Page({
  data: {
    message: 'Hello MINA!'
  }
})
```

## List Rendering

```Text code
<!--wxml-->
<view wx:for="{{array}}"> {{item}} </view>
```

```Text code
// page.js
Page({
  data: {
    array: [1, 2, 3, 4, 5]
  }
})
```

## Condition Rendering

```Text code
<!--wxml-->
<view wx:if="{{view == 'WEBVIEW'}}"> WEBVIEW </view>
<view wx:elif="{{view == 'APP'}}"> APP </view>
<view wx:else="{{view == 'MINA'}}"> MINA </view>
```

```Text code
// page.js
Page({
  data: {
    view: 'MINA'
  }
})
```

## Template

```Text code
<!--wxml-->
<template name="staffName">
  <view>
    FirstName: {{firstName}}, LastName: {{lastName}}
  </view>
</template>

<template is="staffName" data="{{...staffA}}"></template>
<template is="staffName" data="{{...staffB}}"></template>
<template is="staffName" data="{{...staffC}}"></template>
```

```Text code
// page.js
Page({
  data: {
    staffA: {firstName: 'Hulk', lastName: 'Hu'},
    staffB: {firstName: 'Shang', lastName: 'You'},
    staffC: {firstName: 'Gideon', lastName: 'Lin'}
  }
})
```

# WXSS

WXSS (WeiXin Style Sheets) is a set of style languages that describe WXML component styles,

and is used to determine how WXML components are displayed.

WXSS has most of the features of CSS to cater for the needs of front-end developers, but incorporates some new features and modifications to adapt to the development of Weixin Mini Programs.

Compared with CSS, WXSS offers the following additional features:

- Dimension unit
- Style import

## Dimension Unit

- rpx (responsive pixel): Adaptable to the screen width. The specified screen width is 750 rpx. If the screen width on iPhone6 is 375 px (750 physical pixels), then 750 rpx = 375 px = 750 physical pixels, i.e. 1 rpx = 0.5 px = 1 physical pixel.

| Device       | rpx-to-px conversion (screen width/750) | px-to-rpx conversion (750/screen width) |
| :----------- | :-------------------------------------- | :-------------------------------------- |
| iPhone5      | 1rpx = 0.42px                           | 1px = 2.34rpx                           |
| iPhone6      | 1rpx = 0.5px                            | 1px = 2rpx                              |
| iPhone6 Plus | 1rpx = 0.552px                          | 1px = 1.81rpx                           |

> 👍 Tip
> 
> Designers can use iPhone6 as a standard in Visual Design when developing Weixin Mini Programs.

> 📘 Note
> 
> It is inevitable to have some glitches on small screens. Please try to avoid this during development.

## Style Import

You can use the `@import` statement to import external style sheet. The `@import` statement should be followed by the relative path of the external style sheet and ends with `;.`

**Sample code:**

```Text code
/** common.wxss **/
.small-p {
  padding:5px;
}
```

```Text code
/** app.wxss **/
@import "common.wxss";
.middle-p {
  padding:15px;
}
```

## Inline Style

You can use "style" and "class" properties for framework components to control the component style.

- style: Static styles are all written to "class". "style" receives dynamic styles and parses them at runtime. It is not recommended to write static styles to "style" to avoid affecting the rendering speed.

```Text code
<view style="color:{{color}};" />
```

- class: Used to specify style rules. Its value is a collection of class selector names (style class names) in the style rules. The style class names do not contain. and are separated with spaces.

```
<view class="normal_view" />
```

## Selectors

The following selectors are supported:

| Selector         | Example        | Description                                                                  |
| :--------------- | :------------- | :--------------------------------------------------------------------------- |
| .class           | .intro         | Selects all components with class="intro"                                    |
| # id             | # firstname    | Selects the component with id="firstname"                                    |
| element          | view           | Selects all "view" components                                                |
| element, element | view, checkbox | Selects all "checkbox" components and the "view" components of all documents |
| ::after          | view::after    | Inserts content after the "view" component                                   |
| ::before         | view::before   | Inserts content before the "view" component                                  |

## Global and Local Styles

A global style is defined in app.wxss and applies to every page, while a local one is defined in the page's wxss file and only applies to the current page (overrides the same selector in app.wxss).

# WXS

WXS (WeiXin Script) is a scripting language for Mini Programs. Combined with `WXML`, it can be used to construct the page structure.

> 📘 Note
> 
> 1. WXS does not depend on the runtime base library version and can run in all versions of Mini Programs.
> 2. WXS is a different language from JavaScript. It has its own syntax, which is different from that of JavaScript.
> 3. WXS runtime environment is isolated from other JavaScript code. WXS does not support calling functions defined in other JavaScript files and APIs provided by Mini Programs.
> 4. WXS function cannot be called back as an event of a component.
> 5. In Mini Programs on iOS, WXS is 2 to 20 times faster than JavaScript code, But on Android, they run almost equally fast.

The following are simple examples of WXS. For more information on WXS syntax, see [WXS syntax](<>).

## Page Rendering

```Text code
<!--wxml-->
<wxs module="m1">
var msg = "hello world";

module.exports.message = msg;
</wxs>

<view> {{m1.message}} </view>
```

Page output:

```Text code
hello world
```

## Data Processing

```Text code
// page.js
Page({
  data: {
    array: [1, 2, 3, 4, 5, 1, 2, 3, 4]
  }
})
```

```Text code
<!--wxml-->
<!-- The following getMax function takes an array and returns the value of the largest element in the array -->
<wxs module="m1">
var getMax = function(array) {
  var max = undefined;
  for (var i = 0; i < array.length; ++i) {
    max = max === undefined ?
      array[i] :
      (max >= array[i] ? max : array[i]);
  }
  return max;
}

module.exports.getMax = getMax;
</wxs>

<!-- Calls the getMax function in WXS with the "array" in page.js as the parameter -->
<view> {{m1.getMax(array)}} </view>
```

# Event

## What Is an Event?

- An event is a channel through which the view layer communicants with the logical layer.
- An event can pass user's action on to the logical layer for processing.
- An event can be bound to a component. When the event is triggered, the corresponding event handler is executed at the logic layer.
- An event object can have additional information such as ID, dataset, touches.

## How to Use an Event

- Bind an event handler to the component.

For example, if the event is `bindtap`, the event handler can be found in the page when a user taps the component.

```Text code
<view id="tapTest" data-hi="Weixin" bindtap="tapName"> Click me! </view>
```

- Write the event handler in the Page definition with "event" as the parameter.

```Text code
Page({
  tapName: function(event) {
    console.log(event)
  }
})
```

- The log content is as follows:

```Text code
{
  "type":"tap",
  "timeStamp":895,
  "target": {
    "id": "tapTest",
    "dataset":  {
      "hi":"Weixin"
    }
  },
  "currentTarget":  {
    "id": "tapTest",
    "dataset": {
      "hi":"Weixin"
    }
  },
  "detail": {
    "x":53,
    "y":14
  },
  "touches":[{
    "identifier":0,
    "pageX":53,
    "pageY":14,
    "clientX":53,
    "clientY":14
  }],
  "changedTouches":[{
    "identifier":0,
    "pageX":53,
    "pageY":14,
    "clientX":53,
    "clientY":14
  }]
}
```

## Respond to Events with WXS Function

> Start from base library version 2.4.4. Please remaining backward compatible.

As of base library version `2.4.4`, you can bind events using the WXS function, which accepts two parameters. One is "event", with an additional `event.instance` object. The other is `ownerInstance`, which is a `ComponentDescriptor` object, just like `event.instance`. The WXS function is used as follows:

- Bind and register the WXS function for event handling in component.

```Text code
<wxs module="wxs" src="./test.wxs"></wxs>
<view id="tapTest" data-hi="Weixin" bindtap="{{wxs.tapName}}"> Click me! </view>
**Note: The bound WXS function must be enclosed with {{}}.**
```

- Test.wxs file implements the tapName function.

```
function tapName(event, ownerInstance) {
  console.log('tap Weixin', JSON.stringify(event))
}
module.exports = {
  tapName: tapName
}
```

`ownerInstance` contains some methods to set the style and class of a component. For more information on the methods and the reason why the WXS function is used to response to events, click here.

## Events

## Event Types

Events are divided into bubbling events and non-bubbling ones.

1. Bubbling event: When an event is triggered on a component, this event is propagated to the component's parent node.
2. Non-bubbling event: When an event is triggered on a component, this event is not propagated to the component's parent node.

WXML bubbling events:

| Type               | Trigger Condition                                                                                                                                                                                | Minimum Version |
| :----------------- | :----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :-------------- |
| touchstart         | Finger touch starts                                                                                                                                                                              |                 |
| touchmove          | Finger moves after touch                                                                                                                                                                         |                 |
| touchcancel        | Finger touch is interrupted by call reminder, pop-up window, etc.                                                                                                                                |                 |
| touchend           | Finger touch ends                                                                                                                                                                                |                 |
| tap                | The finger leaves the screen after touch                                                                                                                                                         |                 |
| longpress          | The finger leaves the screen after it taps and holds on the screen for more than 350 ms. If an event callback function is specified and this event is triggered, the tap event is not triggered. |                 |
| longtap            | The finger leaves the screen after it taps and holds on the screen for more than 350 ms (it is recommended to use longpress event instead).                                                      |                 |
| transitionend      | Triggered when a WXSS transition or wx.createAnimation animation ends                                                                                                                            |                 |
| animationstart     | Triggered when a WXSS animation starts                                                                                                                                                           |                 |
| animationiteration | Triggered after an iteration of a WXSS animation ends                                                                                                                                            |                 |
| animationend       | Triggered when a WXSS animation completes                                                                                                                                                        |                 |
| touchforcechange   | Triggered when the screen is tapped again on an iPhone supporting 3D Touch.                                                                                                                      |                 |

> 📘 Note
> 
> Unless otherwise specified, the custom events of components other than those listed above are non-bubbling events, such as the `submit` event of it` ev\((form),` input` event of ut` eve\((input), and `scroll` event of ll\` event of \((scroll-view). For more information, see [Components](<>)).

## Event Binding and Bubbling

Similar to component properties, an event is bound in the form of key and value.

- Key starts with bind or catch, followed by the event type, such as `bindtap` and `catchtouchstart`. As of base library version [1.5.0](<>), in non-[native-component](../../../component/native-component.md),  (../../../component/native-component.md), bind and catch can be followed by a colon with their meaning remaining unchanged.
- Value is a string, and a function with the same name needs to be defined in the Page. Otherwise, an error will occur when the event is triggered.

Binding `bind` event does not prevent a bubbling event from bubbling, but binding `catch` event does.

In the example shown below, tap "inner view" to call `handleTap3` and `handleTap2` (because the tap event is propagated to middle view, which prevents the tap event from being propagated to the parent node); tap "middle view" to trigger `handleTap2` and tap "outer view" to trigger `handleTap1`.

```Text code
<view id="outer" bindtap="handleTap1">
  outer view
  <view id="middle" catchtap="handleTap2">
    middle view
    <view id="inner" bindtap="handleTap3">
      inner view
    </view>
  </view>
</view>
```

## Event Capturing

As of base library 1.5.0, touch-related events support capturing. In event capturing, which precedes bubbling, events arrive at nodes in an order reverse of that in which they do during bubbling. To listen to events during capturing, use `capture-bind` or `capture-catch` as the keyword. The latter interrupts the capturing and cancels bubbling.

In the code below, tap "inner view" to call `handleTap2`, `handleTap4`, `handleTap3`, and `handleTap1` in turn.

```Text code
<view id="outer" bind:touchstart="handleTap1" capture-bind:touchstart="handleTap2">
  outer view
  <view id="inner" bind:touchstart="handleTap3" capture-bind:touchstart="handleTap4">
    inner view
  </view>
</view>
```

If the first capture-bind in the above code is changed to capture-catch, only handleTap2 is triggered.

```Text code
<view id="outer" bind:touchstart="handleTap1" capture-catch:touchstart="handleTap2">
  outer view
  <view id="inner" bind:touchstart="handleTap3" capture-bind:touchstart="handleTap4">
    inner view
  </view>
</view>
```

## Event Objects

Unless otherwise specified, when the component triggers an event, the handler bound to the event at logic layer receives an event object.

### BaseEvent object properties:

| Property      | Type    | Description                                                            | Base Library Version |
| :------------ | :------ | :--------------------------------------------------------------------- | :------------------- |
| type          | String  | Event Type                                                             |                      |
| timeStamp     | Integer | Timestamp when the event is generated                                  |                      |
| target        | Object  | A collection of property values​for the component triggering the event |                      |
| currentTarget | Object  | A collection of property values​for the current component              |                      |
| mark          | Object  | Event flag data                                                        | 2.7.1                |

### CustomEvent object properties (inherit from BaseEvent):

| Property | Type   | Description            |
| :------- | :----- | :--------------------- |
| detail   | Object | Additional information |

### TouchEvent object properties (inherit from BaseEvent):

| Property       | Type  | Description                                                                          |
| :------------- | :---- | :----------------------------------------------------------------------------------- |
| touches        | Array | Touch event. An array of information of touch points staying in the screen.          |
| changedTouches | Array | Touch event. An array of information of touch points involving changes in the screen |

### Special events: The touch events in canvas are non-bubbling events and thus have no currentTarget.

## type

Represents the type of an event.

## timeStamp

Number of milliseconds from the moment when the page is opened until the event is triggered.

## target

The source component triggering the event.

| Property      | Type   | Description                                                                         |
| :------------ | :----- | :---------------------------------------------------------------------------------- |
| id            | String | ID of the event source component                                                    |
| tagName       | String | Type of the current component                                                       |
| [dataset](<>) | Object | A collection of custom properties starting with data- on the event source component |

## currentTarget

The current component bound to the event.

| Property | Type   | Description                                                                    |
| :------- | :----- | :----------------------------------------------------------------------------- |
| id       | String | Current component ID                                                           |
| tagName  | String | Type of the current component                                                  |
| dataset  | Object | A collection of custom properties starting with data- on the current component |

> 📘 Note
> 
> You can refer to the above example for "target" and "currentTarget". When you tap "inner view", the event objects "target" and "currentTarget" received by `handleTap3` are both "inner", but the "target" and "currentTarget" received by `handleTap2` are "inner" and "middle", respectively.

## dataset

You can add some custom data to the component node so as to obtain the custom node data from the event for logical processing.

In WXML, these custom data begins with `data-` and multiple words are joined with hyphen `-`. In the code, a hyphenation is converted to camel case, and the uppercase characters are automatically converted to lowercase ones. For example:

- `data-element-type` is converted to `event.currentTarget.dataset.elementType;`
- `data-elementType` is converted to `event.currentTarget.dataset.elementtype`.

**Example:**

```Text code
<view data-alpha-beta="1" data-alphaBeta="2" bindtap="bindViewTap"> DataSet Test </view>
```

```Text code
Page({
  bindViewTap:function(event){
    event.currentTarget.dataset.alphaBeta === 1 // - Converts to camel case
    event.currentTarget.dataset.alphabeta === 2 // Uppercase converts to lowercase
  }
})
```

## mark

As of base library 2.7.1, you can use `mark` to identify the target node triggering the event. In addition, `mark` can also be used to carry some custom data (similar to `dataset`).

When an event is triggered, all `mark`s on the event bubbling path are merged and returned to the event callback function. (Even if the event is not a bubbling event, `mark` is called.)

**Code example:**

Preview with Developer Tool

```Text code
<view mark:myMark="last" bindtap="bindViewTap">
  <button mark:anotherMark="leaf" bindtap="bindButtonTap">Button</button>
</view>
```

In the above WXML, if a button is tapped, events `bindViewTap` and `bindButtonTap` are triggered. The `event.mark` carried by the event contains `myMark` and `anotherMark`.

```Text code
Page({
  bindViewTap: function(e) {
    e.mark.myMark === "last" // true
    e.mark.anotherMark === "leaf" // true
  }
})
```

`mark` is very similar to `dataset`, except that `mark` contains all the `mark`: property values from the event-triggering node to the root node, while `dataset` only contains the `data`- property value of one node.

> 📘 Notes
> 
> - If there are duplicate `mark`s with the same name, the `mark` at the parent node is overwritten by that at the child node.
> - When an event is received in a custom component, `mark` does not contain the `mark` of the node outside the custom component.
> - Unlike `dataset`, `mark` at the node does not involve hyphenation and case conversion.

## touches

"touches" is an array, in which each element is a Touch object ("touches" in the canvas touch event is a CanvasTouch array). Touch points staying in the screen

## Touch objects

| Property         | Type   | Description                                                                                                                                                                   |
| :--------------- | :----- | :---------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| identifier       | Number | Touch point identifier                                                                                                                                                        |
| pageX, pageY     | Number | Distance from the upper left corner of the document. The top left corner is the origin, the horizontal line is X-axis, and the vertical line is Y-axis.                       |
| clientX, clientY | Number | Distance from the upper left corner of the page display area (the area on the screen without navigation pane). The horizontal line is X-axis and the vertical line is Y-axis. |

## CanvasTouch objects

| Property   | Type   | Description                                                                                                                                              |
| :--------- | :----- | :------------------------------------------------------------------------------------------------------------------------------------------------------- |
| identifier | Number | Touch point identifier                                                                                                                                   |
| x, y       | Number | Distance from the upper left corner of Canvas. Canvas's upper left corner is the origin, the horizontal line is X-axis, and the vertical line is Y-axis. |

## changedTouches

Indicates the touch points involving changes (in the same format as "touches"), including touchstart (appearance of touch point), touchmove (movement of touch point), and touchend/touchcancel (disappearance of touch point).

## detail

The data carried by the custom event. For example, the submission event of a form component carries user's input, and the error event of media carries the error message. For more information, see the event definitions in [Components](<>).

Similar to pageX and page Y, the x and y in `detail` of the tap event represent the distance from the upper left corner of the document.

> ## Respond to Events with WXS
>
> Start from base library version 2.4.4. Please remaining backward compatible.
>
> ### Background
>
> Frequent user interactions can cause stutters of a Mini Program. For example, A and B are two elements on the page. When the user makes a touchmove gesture on A, B is required to follow A to move. movable-view is a typical example. The response process for a touchmove event is as follows.
>
> a. A touchmove event is thrown from the view layer (Webview) to the logical layer (App Service);
>
> b. The touchmove event is handled at the logic layer (App Service), and then the position of B is changed through setData.
>
> A response to touchmove involves two rounds of communication between the logic layer and rendering layer, as well as a rendering. The time-consumed communication and setData rendering that blocks the execution of other scripts cause delays of the interactive animations.
>
> ### Implementation of Solution
>
> The solution is about reducing the number of communication rounds to respond to the event at the view layer (Webview). The framework of a Mini Program is divided into view layer (Webview) and logic layer (App Service) for better control. Developer's code can only run at the logic layer (Webview), but the solution requires that the code run at the view layer (App Service) instead, as shown below:
>
> ![](https://files.readme.io/bbe7f49-11.png)
>
> WXS function can only be used to respond to the events of built-in components of a Mini Program and does not support custom component events. In addition to purely logic operations, WXS function can also access and set the class and style of a component through the encapsulated ComponentDescriptor instance. Setting style and class is sufficient for interactive animations. The following is an example of WXS function:
>
> > ```Text code
> > var wxsFunction = function(event, ownerInstance) {
> >     var instance = ownerInstance.selectComponent('.classSelector') // Returns the instance of the component
> >     instance.setStyle({
> >         "font-size": "14px" // rpx is supported
> >     })
> >     instance.getDataset()
> >     instance.setClass(className)
> >     // ...
> >     return false // The event does not bubble (is not propagated to the parent node), which means both stopPropagation and preventDefault are called.
> > }
> > ```
>
> For the input parameter event, the `event.instance` parameter is added to the event objects of Mini Program to indicate the `ComponentDescriptor` instance of the component triggering the event. ownerInstance represents the `ComponentDescriptor` instance of the component where the component triggering the event resides. If the component triggering the event is inside the page, `ownerInstance` indicates a page instance.
>
> The definition of `ComponentDescriptor` is as follows:
>
> | Method                         | Parameter                      | Description                                                                                                                                                                   |
> | :----------------------------- | :----------------------------- | :---------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
> | selectComponent                | "selector" object              | Returns `ComponentDescriptor `instance of the component                                                                                                                       |
> | selectAllComponents            | "selector" object array        | Returns the array of `ComponentDescriptor `instances of the component                                                                                                         |
> | setStyle                       | Object/string                  | Sets the component style (`rpx` is supported). The style set has priority over that defined in the component wxml. It does not support setting the style of the topmost page. |
> | addClass/removeClass/ hasClass | string                         | Sets the component class. The class set has priority over that defined in the component wxml. It does not support setting the class of the topmost page.                      |
> | getDataset                     | None                           | Returns the dataset object of the current component/page                                                                                                                      |
> | callMethod                     | (funcName:string, args:object) | Calls the function defined by the current component/page at the logic layer (App Service). funcName indicates the function name and args the function's parameters.           |
> | requestAnimationFrame          | Function                       | Sets animation, same as the native `requestAnimationFrame`.                                                                                                                   |
> | getState                       | None                           | Returns an object. It is used when a local variable needs to be stored for subsequent use.                                                                                    |
> | triggerEvent                   | (eventName, detail)            | Same as triggerEvent of component                                                                                                                                             |
>
> WXS runs at the view layer (Webview), where fewer events can be handled. Therefore, a mechanism is needed to communicate with the developer's code at the logic layer (App Service). The callMethod is a method in WXS that calls the developer's code at logic layer (App Service), and WxsPropObserver is the mechanism by which the developer's code at logic layer (App Service) calls the WXS logic.
>
> ## Usage
>
> ```Text code
> <wxs module="test" src="./test.wxs"></wxs>
> <view change:prop="{{test.propObserver}}" prop="{{propValue}}" bindtouchmove="{{test.touchmove}}" class="movable"></view>
> ```
>
> The `change:prop` above (a property prefixed by change:) triggers the WXS function when the prop value is set, and its value must be enclosed with` {{}}`. Similar to the "observer" in Component-defined properties, setData({propValue: newValue}) will trigger the WXS function once being called.
>
> > 📘 Note
> > 
> > The WXS function must be enclosed with {{}} and is triggered once the prop value is set, rather than just when the value is changed. Therefore, the WxsPropObserver function is called when the page is initialized.
> > 
> > - The event handler and the functions triggered when properties are changed are defined in and exported from the WXS file` test.wxs:`
>
> ```Text code
> module.exports = {
>     touchmove: function(event, instance) {
>         console.log('log event', JSON.stringify(event))
>     },
>     propObserver: function(newValue, oldValue, ownerInstance, instance) {
>         console.log('prop observer', newValue, oldValue)
>     }
> }
> ```
>
> For more examples, see [Preview with Developer Tool](<>).
>
> > 👍 Tips
> > 
> > - Events of native components and the bindinput event of input and textarea components are not supported.
> > - Weixin DevTools 1.02.1901170 or above supports interactive animations. The minimum version of base library is 2.4.4.
> > - Only console.log is supported for log location in the WXS function. Note that consecutive duplicate logs will be filtered out.

# Basic Components

The framework provides developers with a set of basic components that can be combined to achieve quick development. For more information, see [Component Documentation](<>).

What is component?

- A component is the basic building block of a view layer.
- A component comes with some features and Weixin styles.
- A component includes a `start tag`, `end tag`, `property` (modifies the component), and `content` (between the two tags).

```Text code
<tagname property="value">
Content goes here ...
</tagname>
```

> 📘 Note
> 
> All components and properties are in lowercase and joined with a hyphen `-`.

## Property Types

[block:parameters]
{
  "data": {
    "h-0": "Type",
    "h-1": "Description",
    "h-2": "Comment",
    "0-0": "Boolean",
    "0-1": "Boolean value",
    "0-2": "If a component has this property, the property value is always considered `true` regardless of what the actual value is. The property value is `false` only when the component has no this property.  \nIf the property value is a variable, the variable is converted to a Boolean value.",
    "1-0": "Number",
    "1-1": "Number",
    "1-2": "`1`, `2.5`",
    "2-0": "String",
    "2-1": "String",
    "2-2": "`\"string\"`",
    "3-0": "Array",
    "3-1": "Array",
    "3-2": "`[ 1, \"string\" ]`",
    "4-0": "Object",
    "4-1": "Object",
    "4-2": "`{ key: value }`",
    "5-0": "EventHandler",
    "5-1": "Event handler",
    "5-2": "`\"handlerName\" `is the event handler name defined in Page",
    "6-0": "Any",
    "6-1": "Any property",
    "6-2": ""
  },
  "cols": 3,
  "rows": 7,
  "align": [
    "left",
    "left",
    "left"
  ]
}
[/block]


## Common Properties

All components have the following properties:

| Property      | Type         | Description                        | Comment                                                                      |
| :------------ | :----------- | :--------------------------------- | :--------------------------------------------------------------------------- |
| id            | String       | A unique identifier of a component | Remains unique across the entire page.                                       |
| class         | String       | Component style class              | The style class defined in the WXSS                                          |
| style         | String       | Component inline style             | This is an inline style that can be dynamically set                          |
| hidden        | Boolean      | Whether to display the component   | All components are displayed by default                                      |
| data-\*       | Any          | Custom property                    | When an event is triggered on the component, it is sent to the event handler |
| bind_/ catch_ | EventHandler | Component event                    | See Event                                                                    |

## Special Properties

Almost all components have their own custom properties. You can modify the features or style of the component. See the definition of each component.

# Get Node Information on Interface

## WXML Node Information

The API for querying node information is used to get information of a node such as its properties, style, and position in the interface.

This API is mostly used to query the current position and scroll position of a node in the interface.

**Sample code:**

```Text code
const query = wx.createSelectorQuery()
query.select('#the-id').boundingClientRect(function(res){
  res.top // The upper boundary coordinates of the #the-id node (relative to the display area)
})
query.selectViewport().scrollOffset(function(res){
  res.scrollTop // The vertical scroll position of the display area
})
query.exec()
```

In the above example, `#the-id` is a node selector, which is slightly different from the CSS selector. For more information, see SelectorQuery.select.

In custom components or pages that contain custom components, it is recommended to use this.createSelectorQuery, instead of [wx.createSelectorQuery](<>), to ensure nodes are selected within the correct area.

# Resize Response Display Area

## Display Area Size

The display area refers to the area in Mini Program interface where you can arrange elements freely. By default, the size of the display area remains unchanged after the page initialization. But you can change the default size by either of the following two ways.

## Enable Screen Rotation on a Phone

Mini Programs support screen rotation as of base library version 2.4.0. To allow the Mini Program pages to support screen rotation, set `"pageOrientation": "auto"` in the window segment of `app.json`,or configure `"pageOrientation": "auto"` in the page json file.

The following example shows how to enable screen rotation in a single page json file.

### Code example:

```Text code
{
  "pageOrientation": "auto"
}
```

If the above declaration is added to the page, the page rotates and the display area is resized as the screen rotates.

As of library version 2.5.0, pageOrientation can be set to landscape, which locks the screen orientation to "Landscape".

## Enable Screen Rotation on an iPad

Mini Programs running on iPad support screen rotation as of base library 2.3.0. To allow the Mini Program to support screen rotation, add `"resizable": true` to `app.json`.

### Code example:

```Text code
{
  "resizable": true
}
```

If the above declaration is added to the Mini Program, the Mini Program page rotates and the display area is resized as the screen rotates. Note: You cannot enable or disable screen rotation for a single page.

## Media Query

Sometimes, the page layout varies with the size of the display area. You can use "media query" to solve most of the problems.

### Code example:

```Text code
.my-class {
  width: 40px;
}

@media (min-width: 480px) {
  /* Style rule that only takes effect on  480px  or wider screens */
  .my-class {
    width: 200px;
  }
}
```

## Screen Rotation Event

Sometimes, subtle layout changes cannot be controlled by using "media query" alone. In this case, js can be used.

You can use selectorQuery.selectViewport to read the size of the display area of the page in js.

The `onResize` of the page can be used to listen to the page resizing event. For custom components, you can use the "resize lifecycle" function to listen to the event. The callback function returns the size of the display area. (This is supported as of base library version 2.4.0.)

### Code example:

```Text code
Page({
  onResize(res) {
    res.size.windowWidth // New width of display area
    res.size.windowHeight // New height of display area
  }
})
```

```Text code
Component({
  pageLifetimes: {
    resize(res) {
      res.size.windowWidth // New width of display area
      res.size.windowHeight // New height of display area
    }
  }
})
```

In addition, you can also use wx.onWindowResize to listen to the event (not recommended).

### Bug & tips:

- Bug: In Weixin 6.7.3 for Android, an error occurs with the screen orientation when the screen is rotated for the `live-pusher` component.

# Animation

## Common User Interface Animations

In Mini Programs, you can use CSS transitions and CSS animations to create simple UI animations.

[Preview with Developer Tool](<>)

You can also use the [wx.createAnimation](<>) API to create simple animation effects dynamically.

During the animation creation, you can use` bindtransitionend`, `bindanimationstart`, `bindanimationiteration`, and `bindanimationend` to listen to animation events.

| Event              | Description                                                |
| :----------------- | :--------------------------------------------------------- |
| transitionend      | A CSS transition ends or a step of wx.createAnimation ends |
| animationstart     | CSS animation starts                                       |
| animationiteration | A step of CSS animation ends                               |
| animationend       | A CSS animation ends                                       |

> 📘 Note
> 
> These events are not bubbling events and need to be bound to the node that is being animated to take effect.

## Advanced Animations

The above animations may not be applicable to complicated scenarios.

You can dynamically adjust the "style" property of a node by [responding to events with WXS](<>). Changing the value of "style" continuously can produce animation effects. And this method can be used to dynamically generate animations based on users' touch events.

Animation effects can also be achieved by using setData to change the user interface continuously. This can change the interface arbitrarily, but usually produces a large delay or stutter, and even causes the Mini Program to freeze. In this case, you can improve performance by changing the setData of the page to the setData in [custom components](<>). The following example shows how to generate a stopwatch animation using setData.

[Preview with Developer Tool](<>)
