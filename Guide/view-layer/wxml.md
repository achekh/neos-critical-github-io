---
title: "WXML"
slug: "wxml"
excerpt: ""
hidden: false
createdAt: "Tue May 23 2023 11:09:31 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Tue Nov 28 2023 09:56:59 GMT+0000 (Coordinated Universal Time)"
layout: "default"
parent: "View Layer"
grand_parent: "Guide"
nav_order: 1
---
# WXML 
*** 
WXML is a markup language for framework design. It can be used to build the page structure when combined with [base components](../../Components/view-components) and event system.

> 📘 Notes
> 
> WXML data binding cannot use the \[keywords and reserved words defined in the ECMAScript specification; otherwise, the error message `Unexpected token `or `Unexpected token: "tokenName"`, `may be reserved words`. will be reported.

The samples below demonstrate what WXML is capable of.:

- **Data binding**
  ```html
  <!--WXML-->
  {% raw %}
  <view>{{message}}</view>
  {% endraw %}
  ```
  ```javascript
  // page.js
  Page({
    data: {
      message: 'Hello MINA!',
    },
  })
  ```
- **List rendering**
  ```html
  <!--WXML-->
  {% raw %}
  <view wx:for="{{array}}">{{item}}</view>
  {% endraw %}
  ```
  ```javascript
  // page.js
  Page({
    data: {
      array: [1, 2, 3, 4, 5],
    },
  })
  ```
- **Conditional rendering**
  ```html
  <!--WXML-->
  {% raw %}
  <view wx:if="{{view == 'WEBVIEW'}}">WEBVIEW</view>
  <view wx:elif="{{view == 'APP'}}">APP</view>
  <view wx:else="{{view == 'MINA'}}">MINA</view>
  {% endraw %}
  ```
  ```javascript
  // page.js
  Page({
    data: {
      view: 'MINA',
    },
  })
  ```
- **Template**
  ```html
  <!--WXML-->
  {% raw %}
  <template name="staffName">
    <view>
      FirstName: {{firstName}}, LastName: {{lastName}}
    </view>
  </template>
  <template is="staffName" data="{{...staffA}}"></template>
  <template is="staffName" data="{{...staffB}}"></template>
  <template is="staffName" data="{{...staffC}}"></template>
  {% endraw %}
  ```
  ```javascript
  // page.js
  Page({
    data: {
      staffA: { firstName: 'Hulk', lastName: 'Hu' },
      staffB: { firstName: 'Shang', lastName: 'You' },
      staffC: { firstName: 'Gideon', lastName: 'Lin' },
  	}, 
  });
  ```
- **Event**
  ```html
  <!--WXML-->
  {% raw %}
   <view bindtap="add">{{count}}</view>
   {% endraw %}
  ```
  ```javascript
  Page({
    data: {
  	count: 1, 
    },
    add(e) {
      this.setData({
        count: this.data.count + 1,
      })
  	}, 
  });
  ```

# WXML features

## Data binding

The dynamic data in WXML comes from the data of the corresponding `Page`.

### Simple binding

Data binding uses the Mustache syntax (double curly brackets) to wrap the variables. It can be used for the following:

#### Content

```html
<!--WXML-->
{% raw %}
 <view>{{ message }}</view>
 {% endraw %}
```
```javascript
Page({
  data: {
    message: 'Hello MINA!',
  },
})
```

### Component attribute (must be enclosed in double quotes)

```html
<!--WXML-->
{% raw %}
 <view id="item-{{id}}"></view>
 {% endraw %}
```
```javascript
Page({
  data: {
		id: 0, 
  },
});
```

### Control attribute (must be enclosed in double quotes)

```html
<!--WXML-->
{% raw %}
 <view wx:if="{{condition}}"></view>
 {% endraw %}
```
```javascript
Page({
  data: {
    condition: true,
  },
})
```

### Keyword (must be enclosed in double quotes)

`true` : Boolean-type true.

`false` : Boolean-type false.

```html
<!--WXML-->
{% raw %}
 <checkbox checked="{{false}}"></checkbox>
{% endraw %}
```

> 📘 Note
> 
> Do not directly write checked="false" . Its computing result is a string which represents a true value when converted to a Boolean value.

### Operation

You can implement simple operations in {{}} . This syntax supports the following methods:

#### Ternary operation

```html
<!--WXML-->
{% raw %}
 <view hidden="{{flag ? true : false}}">Hidden</view>
 {% endraw %}
```

#### Arithmetic operation

```html
<!--WXML-->
{% raw %}
 <view>{{a + b}} + {{c}} + d</view>
 {% endraw %}
```
```javascript
Page({
  data: {
    a: 1,
    b: 2,
    c: 3,
	}, 
})
```

The content in view is `3 + 3 + d`.

### Logical judgment

```html
<!--WXML-->
{% raw %}
 <view wx:if="{{length > 5}}"></view>
 {% endraw %}
```

### String operation

```html
<!--WXML-->
{% raw %}
 <view>{{"hello" + name}}</view>
{% endraw %}
```
```javascript
Page({
  data: {
    name: 'MINA',
  },
})
```

### Data path operation

```html
<!--WXML-->
{% raw %}
 <view>{{object.key}} {{array[0]}}</view>
{% endraw %}
```
```javascript
Page({
  data: {
    object: {
      key: 'Hello ',
		},
    array: ['MINA'],
  },
})
```

### Combination

You can also directly implement combinations in Mustache syntax to build new objects and arrays.

### Array

```html
<!--WXML-->
{% raw %}
 <view wx:for="{{[zero, 1, 2, 3, 4]}}">{{item}}</view>
{% endraw %}
```
```javascript
Page({
  data: {
		zero: 0, 
  },
})
```

The final result is the array `[0, 1, 2, 3, 4]`.

### Object

```html
<!--WXML-->
{% raw %}
 <template is="objectCombine" data="{{for: a, bar: b}}"></template>
{% endraw %}
```
```javascript
Page({
  data: {
		a: 1,
		b: 2, 
  },
})
```

The final result is the object `{for: 1, bar: 2}`.

You can also use the extended operator `...` to extend the object.

```html
<!--WXML-->
{% raw %}
 <template is="objectCombine" data="{{...obj1, ...obj2, e: 5}}"></template>
{% endraw %}
```
```javascript
Page({
  data: {
    obj1: {
      a: 1,
      b: 2,
		}, 
    obj2: {
			c: 3,
			d: 4, 
    },
	}, 
})
```

The final result is the object `{a: 1, b: 2, c: 3, d: 4, e: 5}`.

If the object's `key` and `value` are identical, this can be indirectly expressed.

```html
<!--WXML-->
{% raw %}
 <template is="objectCombine" data="{{foo, bar}}"></template>
{% endraw %}
```
```javascript
Page({
  data: {
    foo: 'my-foo',
    bar: 'my-bar',
  },
})
```

The final result is the object `{foo: 'my-foo', bar:'my-bar'}`.

> 📘 Notes
> 
> Any combination of the above methods is allowed, but if there are cases where identical variable names occur, the latter will overwrite the former, such as:
> 
>```xml
><!--WXML-->
>{% raw %}
>  <template is="objectCombine" data="{{...obj1, ...obj2, a, c: 6}}"></template>
>{% endraw %}
>```
> ```javascript JavaScript
> Page({
>   data: {
>     obj1: {
>       a: 1,
>       b: 2,
> 		}, 
>     obj2: {
> 			b: 3,
> 			c: 4, 
>     },
> 		a: 5, 
>   },
> })
> ```
> 
> The final result is the object `{a: 5, b: 3, c: 6}`.

> 📘 Notes
> 
> If there are spaces between curly brackets and quotes, the content is ultimately parsed into a string:
> 
> ```html
><!--WXML-->
>{% raw %}
> <view wx:for="{{[1,2,3]}} ">
>   {{item}}
> </view>
>{% endraw %}
>```
> 
> equivalent to
> 
> ```html
><!--WXML-->
>{% raw %}
> <view wx:for="{{[1,2,3] + ' '}}">
>   {{item}}
> </view>
>{% endraw %}
>```

## List rendering

### wx:for

In a component, by binding an array using the `wx:for` control attribute, you can use the data of the array items to re-render this component.

The subscript variable name of the current item of the default array defaults to `index`, and the variable name of the current item of the array defaults to `item`.

```html
<!--WXML-->
{% raw %}
<view wx:for="{{array}}">
  {{index}}: {{item.message}}
</view>
{% endraw %}
```
```javascript
Page({
  data: {
		array: [ 
      {
        message: 'foo',
      },
      {
        message: 'bar',
      }, 
    ],
	}, 
})
```

You can use `wx:for-item` to specify the variable name of the array's current element.

You can use `wx:for-index` to specify the variable name of the array's current subscript:

```html
<!--WXML-->
{% raw %}
<view wx:for="{{array}}" wx:for-index="idx" wx:for-item="itemName">
  {{idx}}: {{itemName.message}}
</view>
{% endraw %}
```

`wx:for` can also be embedded. Below is the multiplication table:

```html
<!--WXML-->
{% raw %}
<view wx:for="{{[1, 2, 3, 4, 5, 6, 7, 8, 9]}}" wx:for-item="i">
  <view wx:for="{{[1, 2, 3, 4, 5, 6, 7, 8, 9]}}" wx:for-item="j">
    <view wx:if="{{i <= j}}">
      {{i}} * {{j}} = {{i * j}}
    </view>
  </view>
</view>
{% endraw %}
```

### block wx:for

Similar to block `wx:if`, you can use `wx:for` on a `<block/>` tag to render a structural block containing multiple nodes. For example:

```html
<!--WXML-->
{% raw %}
<block wx:for="{{[1, 2, 3]}}">
  <view>{{index}}:</view>
  <view>{{item}}</view>
</block>
{% endraw %}
```

### wx:key

If the positions of list items dynamically change or new items are added to the list and you want the items in the list to retain their features and statuses (such as the content input in `<input />` and the selection status of `<switch>`, you must use `wx:key` to specify the unique identifiers of the items in the list.

The `wx:key` value is provided in either of the following formats:

1. String: represents an attribute of an item in the for loop array. The value of this attribute must be a unique string or number in the list and cannot dynamically change.
2. Reserved keyword `*this`: Represents the item itself in the for loop. This indicates that the item itself is a unique string or number. For example:

When a data change triggers re-rendering at the rendering layer, the components that have keys are corrected. The framework ensures that they are reordered, rather than recreated. This ensures the components retain their statuses and improves the efficiency of list rendering.

**If `wx:key` is not provided, a warning is reported. If you know that this list is static or the order is not important, you can ignore the warning. **

#### Sample code:

```html
<!--WXML-->
{% raw %}
<switch wx:for="{{objectArray}}" wx:key="unique" style="display: block;">
  {{item.id}}
</switch>
<button bindtap="switch">Switch</button>
<button bindtap="addToFront">Add to the front</button>
<switch wx:for="{{numberArray}}" wx:key="*this" style="display: block;">
  {{item}}
</switch>
<button bindtap="addNumberToFront">Add to the front</button>
{% endraw %}
```
```javascript
Page({
  data: {
    objectArray: [
      { id: 5, unique: "unique_5" },
      { id: 4, unique: "unique_4" },
      { id: 3, unique: "unique_3" },
      { id: 2, unique: "unique_2" },
      { id: 1, unique: "unique_1" },
      { id: 0, unique: "unique_0" },
    ],
    numberArray: [1, 2, 3, 4],
  },
  switch(e) {
    const length = this.data.objectArray.length;
    for (let i = 0; i < length; ++i) {
      const x = Math.floor(Math.random() * length);
      const y = Math.floor(Math.random() * length);
      const temp = this.data.objectArray[x];
      this.data.objectArray[x] = this.data.objectArray[y];
      this.data.objectArray[y] = temp;
    }
    this.setData({
      objectArray: this.data.objectArray,
    });
  },
  addToFront(e) {
    const length = this.data.objectArray.length;
    this.data.objectArray = [{ id: length, unique: "unique_" + length }].concat(
      this.data.objectArray
    );
    this.setData({
      objectArray: this.data.objectArray,
    });
  },
  addNumberToFront(e) {
    this.data.numberArray = [this.data.numberArray.length + 1].concat(
      this.data.numberArray
    );
    this.setData({
      numberArray: this.data.numberArray,
    });
  },
});

```

#### Note:

When the `wx:for` value is a string, the string is parsed into a string array

```html
<!--WXML-->
{% raw %}
<view wx:for="array">
  {{item}}
</view>
{% endraw %}
```

equivalent to

```html
<!--WXML-->
{% raw %}
<view wx:for="{{['a','r','r','a','y']}}">
  {{item}}
</view>
{% endraw %}
```

**Note:** If there are spaces between curly brackets and quotes, the content is ultimately parsed into a string

```html
<!--WXML-->
{% raw %}
<view wx:for="{{[1,2,3]}} ">
  {{item}}
</view>
{% endraw %}
```

equivalent to

```html
<!--WXML-->
{% raw %}
<view wx:for="{{[1,2,3] + ' '}}">
  {{item}}
</view>
{% endraw %}
```

## Conditional rendering

### wx:if

In the framework, use `wx:if="{{condition}}"` to determine whether or not to render this code block:

```html
<!--WXML-->
{% raw %}
<view wx:if="{{condition}}">True</view>
{% endraw %}
```

You can also use `wx:elif` and `wx:else` to add an "else" block:

```html
<!--WXML-->
{% raw %}
<view wx:if="{{length > 5}}">1</view>
<view wx:elif="{{length > 2}}">2</view>
<view wx:else>3</view>
{% endraw %}
```

### block wx:if

Because `wx:if` is a control attribute, you must add it to a tag. To judge multiple component tags at once, you can use a `<block/>` tag to package multiple components together and use the `wx:if` control attribute above.

```html
<!--WXML-->
{% raw %}
<block wx:if="{{true}}">
  <view>view1</view>
  <view>view2</view>
</block>
{% endraw %}
```

`Note:` <block/> is not a component, but merely a package element. It does not perform any rendering on the page and only accepts control attributes.

### `wx:if` vs `hidden`

Because the template in `wx:if` can also contain data bindings, when the `wx:if` condition value changes, the framework has a local rendering process that will ensure the conditional block is destroyed or re-rendered when the value changes.

In addition, `wx:if` is inert. If the condition is `false` during initial rendering, the framework does not render it. When the condition changes to true for the first time, local rendering starts.

In contrast, `hidden` is much simpler. The component is always rendered, and this attribute simply controls whether the content is shown or hidden.

Generally, `wx:if` has higher change overheads, while hidden has higher initial rendering overheads. Therefore, in situations where frequent changes are required, it is better to use `hidden`. If conditions are unlikely to change at runtime, `wx:if` is a better choice.

## Template

WXML provides templates, where you can define code snippets and then call them in different places.

### Defining a template

Use the `name` attribute to specify the name of the template. Then, define a code snippet in `<template/>`. For example:

```html
<!--WXML-->
{% raw %}
<!--
  index: int
  msg: string
  time: string
-->
<template name="msgItem">
  <view>
    <text>{{index}}: {{msg}}</text>
    <text>Time: {{time}}</text>
  </view>
</template>
{% endraw %}
```

### Using a template

Use the `is` attribute to declare the template to be used. Then, pass the data needed by the template. For example:

```html
<!--WXML-->
{% raw %}
 <template is="msgItem" data="{{...item}}" />
{% endraw %}
```
```javascript
Page({
  data: {
    item: {
      index: 0,
      msg: 'this is a template',
      time: '2016-09-15',
		}, 
  },
})
```

The `is` attribute can use Mustache syntax to dynamically determine the template to be rendered:

```html
<!--WXML-->
{% raw %}
<template name="odd">
  <view>odd</view>
</template>
<template name="even">
  <view>even</view>
</template>
<block wx:for="{{[1, 2, 3, 4, 5]}}">
  <template is="{{item % 2 == 0 ? 'even' : 'odd'}}" />
</block>
{% endraw %}
```

### Template scope

Templates have their own scopes. They can only use the `data` passed in by data and the `<wxs />` module defined in the file defined by the template.

## Event

### What is an event

- An event is a channel through which the view layer communicants with the logic layer.
- An event can pass a user action on to the logic layer for processing.
- An event can be bound to a component. When the event is triggered, the corresponding event handler is executed at the logic layer.
- An event object can have additional information such as ID, dataset, and touches.

### How to use an event

- Bind an event handler to the component.

For example, if the event is `bindtap`, the event handler can be found in the Page when a user clicks the component.

```html
<!--WXML-->
{% raw %}
 <view id="tapTest" data-hi="WeChat" bindtap="tapName">Click me!</view>
{% endraw %}
```

- Write the event handler in the Page definition with event as the parameter.

```javascript
Page({
  tapName(event) {
    console.log(event)
  },
})
```

- The log content is as follows:

```javascript
{
  "type": "tap",
    "timeStamp": 895,
      "target": {
    "id": "tapTest",
      "dataset": {
      "hi": "WeChat"
    }
  },
  "currentTarget": {
    "id": "tapTest",
      "dataset": {
      "hi": "WeChat"
    }
  },
  "detail": {
    "x": 53,
      "y": 14
  },
  "touches": [
    {
      "identifier": 0,
      "pageX": 53,
      "pageY": 14,
      "clientX": 53,
      "clientY": 14
    }
  ],
  "changedTouches": [
    {
      "identifier": 0,
      "pageX": 53,
      "pageY": 14,
      "clientX": 53,
      "clientY": 14
    }
  ]
}
```

### Responding to an event with the WXS function

The WXS function accepts two parameters. One is `event`, with an additional `event.instance object`. The other is `ownerInstance`, which is a `ComponentDescriptor` object, just like `event.instance`. The WXS function is used as follows:

- Bind and register the WXS function for event handling in the component.

```html
<!--WXML-->
{% raw %}
<wxs module="wxs" src="./test.wxs"></wxs>
<view id="tapTest" data-hi="TMF" bindtap="{{wxs.tapName}}">Click me!</view>
**Note: The bound WXS function must be enclosed with {{}}.**
{% endraw %}
```

- The `test.wxs` file implements the `tapName` function.

```javascript
function tapName(event, ownerInstance) {
  console.log('tap wechat', JSON.stringify(event))
}
module.exports = {
	tapName, 
}
```

`ownerInstance` contains some methods for setting the style and class of a component. 

### Event description

#### Event types

Events are divided into bubbling events and non-bubbling ones:

1. Bubbling event: When an event is triggered on a component, this event is propagated to the component's parent node.
2. Non-bubbling event: When an event is triggered on a component, this event is not propagated to the component's parent node.

WXML bubbling events:

| Type               | Trigger Condition                                                                                                                                                                                    |
| :----------------- | :--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| touchstart         | Finger touch starts                                                                                                                                                                                  |
| touchmove          | Finger moves after touch                                                                                                                                                                             |
| touchcancel        | Finger touch is interrupted by an incoming call notification or pop-up window                                                                                                                        |
| touchend           | Finger touch ends                                                                                                                                                                                    |
| tap                | The finger leaves the screen after touch                                                                                                                                                             |
| longpress          | The finger leaves the screen after it clicks and holds on the screen for more than 350 ms. If an event callback function is specified and this event is triggered, the `tap` event is not triggered. |
| longtap            | The finger leaves the screen after it clicks and holds on the screen for more than 350 ms (it is recommended to use t he `longpress` event instead).                                                 |
| transitionend      | Triggered when a WXSS transition or `wx.createAnimation` animation ends                                                                                                                              |
| animationstart     | Triggered when a WXSS animation starts                                                                                                                                                               |
| animationiteration | Triggered after an iteration of a WXSS animation ends                                                                                                                                                |
| animationend       | Triggered when a WXSS animation completes                                                                                                                                                            |
| touchforcechange   | Triggered when the screen is clicked again on an iPhone supporting 3D Touch                                                                                                                          |

> 📘 Notes
> 
> Unless otherwise specified, the custom events of components other than those listed above are non-bubbling events, such as the submit event of [`<form/>`](doc:form), input event of [`<input/>`](doc:input), and scroll event of [`<scroll-view/>`](doc:scroll-view).

### Event binding and bubbling

Similar to component attributes, an event is bound in the form of `key` and `value`.

- `key` starts with `bind` or `catch`, followed by the event type, such as `bindtap` and `catchtouchstart`. In non-[native-component](doc:native-components), `bind` and `catch` can be followed by a colon with their meaning remaining unchanged, such as `bind:tap` and `catch:touchstart`.
- `value` is a string, and a function with the same name needs to be defined in the `Page`; otherwise, an error will be reported when the event is triggered.

`bind` event binding does not prevent a bubbling event from bubbling, but `catch` event binding does.

In the sample shown below, click "inner view" to call `handleTap3` and `handleTap2` (because the `tap` event is propagated to middle view, which prevents the `tap` event from being propagated to the parent node); click "middle view" to trigger `handleTap2` and click "outer view" to trigger `handleTap1`.

```html
<!--WXML-->
{% raw %}
<view id="outer" bindtap="handleTap1">
  outer view
  <view id="middle" catchtap="handleTap2">
    middle view
    <view id="inner" bindtap="handleTap3">
      inner view
    </view>
  </view>
</view>
{% endraw %}
```

### Event capturing

Touch-related events support capturing. During event capturing, which precedes bubbling, events arrive at nodes in an order reverse of that in which they do during bubbling. To listen for events during capturing, use `capture-bind` or `capture-catch` as the keyword. The latter interrupts the capturing and cancels the bubbling.

```html
<!--WXML-->
{% raw %}
<view
  id="outer"
  bind:touchstart="handleTap1"
  capture-bind:touchstart="handleTap2"
>
  outer view
  <view
    id="inner"
    bind:touchstart="handleTap3"
    capture-bind:touchstart="handleTap4"
  >
    inner view
  </view>
</view>
{% endraw %}
```

If the first `capture-bind` in the above code is changed to `capture-catch`, only `handleTap2` is triggered.

```html
<!--WXML-->
{% raw %}
<view
  id="outer"
  bind:touchstart="handleTap1"
  capture-catch:touchstart="handleTap2"
>
  outer view
  <view
    id="inner"
    bind:touchstart="handleTap3"
    capture-bind:touchstart="handleTap4"
  >
    inner view
  </view>
</view>
{% endraw %}
```

### Event object

Unless otherwise specified, when the component triggers an event, the handler bound to the event at the logic layer receives an event object.

**`BaseEvent` object attributes:**

| Attribute     | Type    | Description                                                             |
| :------------ | :------ | :---------------------------------------------------------------------- |
| type          | String  | Event type                                                              |
| timeStamp     | Integer | Timestamp when the event is generated                                   |
| target        | Object  | A collection of attribute values for the component triggering the event |
| currentTarget | Object  | A collection of attribute values for the current component              |

**`CustomEvent` object attributes (inherited from BaseEvent ):**

| Attribute | Type   | Description            |
| :-------- | :----- | :--------------------- |
| detail    | Object | Additional information |

**`TouchEvent` object attributes (inherited from BaseEvent ):**

| Attribute      | Type  | Description                                                                          |
| :------------- | :---- | :----------------------------------------------------------------------------------- |
| touches        | Array | Touch event. An array of information of touch points staying on the screen           |
| changedTouches | Array | Touch event. An array of information of touch points involving changes on the screen |

**Special events: The touch events on `<canvas>` are non-bubbling events and thus have no currentTarget.**

### type

Represents the type of an event.

### timeStamp

Number of milliseconds from the moment when the page is opened until the event is triggered.

### target

The source component triggering the event.

| Attribute | Type   | Description                                                                           |
| :-------- | :----- | :------------------------------------------------------------------------------------ |
| id        | String | ID of the event source component                                                      |
| tagName   | String | Type of the current component                                                         |
| dataset   | Object | A collection of custom attributes starting with `data-` on the event source component |

### currentTarget

The current component bound to the event.

| Attribute | Type   | Description                                                                      |
| :-------- | :----- | :------------------------------------------------------------------------------- |
| id        | String | Current component ID                                                             |
| tagName   | String | Type of the current component                                                    |
| dataset   | Object | A collection of custom attributes starting with `data-` on the current component |

> 📘 Notes
> 
> You can refer to the above example for `target` and `currentTarget`. When you click "inner view", the event objects `target` and `currentTarget` received by `handleTap3` are both `inner`, but the event objects `target` and `currentTarget` received by `handleTap2` are `inner` and `middle`, respectively.

### dataset

You can customize data in the component, which will be passed to the service through an event. Format: The custom data begins with `data-` and multiple words are concatenated with hyphen `-`. Uppercase characters are not allowed and are automatically converted to lowercase, such as `data-element-type`. Eventually, hyphenation is converted to camel case `elementType` in `event.currentTarget.dataset`.

**Sample:**

```html
<!--WXML-->
{% raw %}
<view data-alpha-beta="1" data-alphaBeta="2" bindtap="bindViewTap">
  DataSet Test
</view>
{% endraw %}
```
```javascript
Page({
  bindViewTap(event) {
    event.currentTarget.dataset.alphaBeta === 1 // `-` converts to camel case.
    event.currentTarget.dataset.alphabeta === 2 // Uppercase converts to lowercase.
  },
})
```

### touches

`touches` is an array, in which each element is a `Touch` object ( `touches` in the canvas touch event is a `CanvasTouch` array). It indicates the touch points staying on the screen.

### `Touch` object

| Attribute        | Type   | Description                                                                                                                                                                       |
| :--------------- | :----- | :-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| identifier       | Number | Touch point identifier                                                                                                                                                            |
| pageX, pageY     | Number | Distance from the top-left corner of the document. The top-left corner is the origin, the horizontal line is X-axis, and the vertical line is Y-axis.                             |
| clientX, clientY | Number | Distance from the top-left corner of the page display area (the area on the screen excluding the navigation pane). The horizontal line is X-axis and the vertical line is Y-axis. |

### `CanvasTouch` object

| Attribute  | Type   | Description                                                                                                                                                       |
| :--------- | :----- | :---------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| identifier | Number | Touch point identifier                                                                                                                                            |
| x, y       | Number | Distance from the top-left corner of the canvas. The top-left corner of the canvas is the origin, the horizontal line is X-axis, and the vertical line is Y-axis. |

### changedTouches

Indicates the touch points involving changes (in the same format as `touches`), including `touchstart` (appearance of touch point), `touchmove` (movement of touch point), and  `touchend`/`touchcancel`  (disappearance of touch point).

### detail

The data carried by the custom event. For example, the submission event of a form component carries user input, and the error event of media carries the error message.

Similar to `pageX` and `pageY`, the `x` and `y` in `detail` of the `tap` event represent the distance from the top-left corner of the document.

### Responding to an event with WXS

#### Background

Frequent user interactions can cause stutters of a Mini App. For example, A and B are two elements on the page. When the user makes a `touchmove` gesture on A, B is required to follow A. <movable-view> is a typical example. The response process for a `touchmove` event is as follows:

a. A `touchmove` event is thrown from the view layer (Webview) to the logic layer (App Service).

b. The `touchmove` event is handled at the logic layer (App Service), and then the position of B is changed through `setData`.

A response to `touchmove` involves two rounds of communication between the logic layer and rendering layer, as well as a rendering. The time- consuming communication and `setData` rendering that blocks the execution of other scripts cause delays of the interactive animations.

#### Implementation solution

The solution is about reducing the number of rounds of communication to respond to the event at the view layer (Webview). The framework of a Mini App is divided into the view layer (Webview) and logic layer (App Service) for better control. Developer's code can only run at the logic layer (App Service), but the solution requires that the code run at the view layer (Webview) instead.

The [WXS]\(Need to add link) function can only be used to respond to the events of built-in components of a Mini App and does not support custom component events. In addition to purely logic operations, the WXS function can also access and set the class and style of a component through the encapsulated `ComponentDescriptor` instance. Setting the style and class is sufficient for interactive animations. The following is an example of the WXS function:

```javascript
const wxsFunction = function(event, ownerInstance) {
  const instance = ownerInstance.selectComponent('.classSelector') // Return the instance of the component
  instance.setStyle({
    'font-size': '14px', // `rpx` is supported
  })
  instance.getDataset()
  instance.setClass(className)
  // ...
  return false // The event does not bubble, which means both `stopPropagation` and `preventDefault` are called.
}
```

For the input parameter `event`, the `event.instance` parameter is added to the [event objects]\(Need to add link) of Mini Apps to indicate the `ComponentDescriptor` instance of the component triggering the event. `ownerInstance` represents the `ComponentDescriptor` instance of the component where the component triggering the event resides. If the component triggering the event is inside the page, `ownerInstance` indicates a page instance.

The definition of `ComponentDescriptor` is as follows:

| Method                         | Parameter                      | Description                                                                                                                                                                     |
| :----------------------------- | :----------------------------- | :------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| selectComponent                | `selector` object              | Returns the `ComponentDescriptor` instance of the component                                                                                                                     |
| selectAllComponents            | `selector` object array        | Returns the array of `ComponentDescriptor` instances of the component                                                                                                           |
| setStyle                       | Object/string                  | Sets the component style ( `rpx` is supported). The set style has priority over that defined in the comp onent WXML. It does not support setting the style of the topmost page. |
| addClass/removeClass/ hasClass | string                         | Sets the component class. The set class has priority over that defined in the component WXML. It does not support setting the class of the topmost page.                        |
| getDataset                     | None                           | Returns the `dataset` object of the current component/page                                                                                                                      |
| callMethod                     | (funcName:string, args:object) | Calls the function defined by the current component/page at the logic layer (App Service).`funcName` indicates the function name and args the function's parameters.            |
| requestAnimationFrame          | Function                       | Sets animation, same as the native `requestAnimationFrame`.                                                                                                                     |
| getState                       | None                           | Returns an object. It is used when a local variable needs to be stored for subsequent use.                                                                                      |
| triggerEvent                   | (eventName, detail)            | Same as [triggerEvent]\(Need to add link) of the component                                                                                                                      |

WXS runs at the view layer (Webview), where fewer events can be handled. Therefore, a mechanism is needed to communicate with the developer's code at the logic layer (App Service). The `callMethod` is a method in WXS that calls the developer's code at the logic layer (App Service), and `WxsPropObserver` is the mechanism by which the developer's code at the logic layer (App Service) calls the WXS logic.

#### Usage

- Define events using WXML:

```
<wxs module="test" src="./test.wxs"></wxs>
<view
  change:prop="{{test.propObserver}}"
  prop="{{propValue}}"
  bindtouchmove="{{test.touchmove}}"
  class="movable"
></view>
```

The `change:prop` above (an attribute prefixed by `change:`) triggers the WXS function when the `prop` attribute is set, and its value must be enclosed with `{{}}`. Similar to the observer attribute in Component-defined `properties`, `setData({propValue: newValue})` will trigger the WXS function once called.

> 📘 Notes
> 
> The WXS function must be enclosed with `{{}}` and is triggered once the `prop` value is set, rather than just when the value is changed. Therefore, the `WxsPropObserver` function is called when the page is initialized.

The event handler and the functions triggered when attributes are changed are defined in and exported from the WXS file `test.wxs`:

```javascript
module.exports = {
  touchmove(event, instance) {
    console.log('log event', JSON.stringify(event))
  },
  propObserver(newValue, oldValue, ownerInstance, instance) {
    console.log('prop observer', newValue, oldValue)
	}, 
}
```

> 📘 Notes
> 
> 1. Events of [native components]\(Need to add link) and the `bindinput` event of [`<input>`]\(Need to add link) and [`<textarea>` ]\(Need to add link)components are not supported.
> 2. Only `console.log` is supported for log location in the WXS function. Note that consecutive duplicate logs will be filtered out.
