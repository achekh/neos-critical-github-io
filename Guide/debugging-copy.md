---
title: "Debugging"
slug: "debugging-copy"
excerpt: "This section explains the concept of debugging."
hidden: true
metadata: 
  image: []
  robots: "index"
createdAt: "Tue May 09 2023 05:20:20 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Mon May 29 2023 11:44:39 GMT+0000 (Coordinated Universal Time)"
---
## vConsole

On a real device, if you want to view the log content and additional debugging information output by the console API, you need to click the button in the upper right corner of the screen to open the menu and select "Turn on Debugging". At this point, the Mini Program/Mini Game will exit, and a vConsole button will appear in the lower right corner after reopening. Click the vConsole button to open the log panel.

There will be some differences between the vConsole display content of Mini Programs and Mini Games, and the left side of the figure below is the Mini Program vConsole, and the right side is the Mini Game vConsole.

## How to use vConsole

Due to the limitations of the implementation mechanism, the log content printed by the developer calling the console API is converted into a JSON string and transmitted to vConsole, resulting in some restrictions on the content displayed in the vConsole:

- With the exception of Number, String, Boolean, and null, all other types are displayed as Objects, printing objects and Enumerable properties in the prototype chain.
- Infinity and NaN appear as null.
- undefined, ArrayBuffer, Function types cannot be displayed.
- Unable to print objects with circular references.

```Text code
let a = {}
a.b = a
console.log(a) // For base libraries below 2.3.2, `An object width circular reference can't be logged` is output.
```

## Mini Programs/Mini Games incorporate the solutions to the above problems.

- Version 2.3.2 and later, support printing circular reference objects. The object properties of the circular reference show the reference path, @Represents the object itself.

```Text code
const circular = { x: {}, c: {} }
circular.x = [{ promise: Promise.resolve() }]
circular.a = circular
circular.c.x0 = circular.x[0]

console.log(circular)
// "{a: '<Circular: @>', c: {x0: '<Circular: @.x[0]>'}, x: [{promise: '<Promise>'}]}"
```

- Base library 2.3 1 or above supports displaying all types.The base library converts the log content, and each converted string is enclosed by `<>`.  
  For example:
  - `<Function: func>`
  - `<Undefined>`
  - `<Infinity>`
  - `<Map: size=0>`
  - `<ArrayBuffer: byteLength=10>`
  - ...
- In base libraries 2.2.3-2.3.0, `ArrayBuffer` and `Function` types are displayed and `undefined `is output as the string '`undefined`'.

> 📘 Note
> 
> Try to avoid printing log content (such as sprites or material objects in the game engine, etc.) that is too complex or too long in non-debugging scenarios, which may cause additional time-consuming. In order to prevent exceptions from occurring, the log content will be replaced if it exceeds a certain length\<LOG_EXCEED_MAX_LENGTH>, and the developer needs to trim the log content.

## Source Map

> This is only supported on iOS 6.7.2 or above.

All the js code is packaged into a file during the Mini Program/Mini Game packaging. Mini Programs/Mini Games come with Source Map to make it easier for developers to pinpoint errors on phones.

When ES6-to-ES5 conversion and code compression are enabled in Weixin DevTools, the `.map` file for Source Map is generated. For Mini Programs of **developer version**, the base library uses the `.map` file in the code package to remap the error message stack shown in the vConsole (only for developer code files).

![](https://files.readme.io/4817bce-35.jpg)

If you process the source file using an external makefile, simply place the generated Source Map file in the same directory as the source file.

For example:

> pages/index.js
>
> pages/index.js.map
>
> app.js
>
> app.js.map

The Weixin DevTools will read, parse and upload the Source Map file.

Then you can use the uploaded Source Map file for error analysis in the operation center at the Mini Program backend.

1. **The size of Source Map file is not counted in the code package size.**
2. **The code package of developer version contains the .map file, so the actual code package is larger than the test and official versions.**

## Physical Device Debugging

Remote debugging allows you to directly debug a Mini Program on the mobile phone via network connection using Weixin DevTools, making it easy for you to pinpoint errors on the phone. For more information, see Weixin DevTools documentation [Physical Device Debugging](<>).
