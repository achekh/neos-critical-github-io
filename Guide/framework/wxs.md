---
title: "WXS"
slug: "wxs"
excerpt: ""
hidden: false
metadata: 
  image: []
  robots: "index"
createdAt: "Tue May 16 2023 08:53:58 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Wed Jun 07 2023 07:15:37 GMT+0000 (Coordinated Universal Time)"
---
WXS is a scripting language for Mini Apps. Combined with WXML, it can be used to construct the page structure.

> 📘 Notes
> 
> - WXS does not depend on the runtime base library version and can run in all versions of Mini Apps.
> - WXS is a different language from JavaScript. It has its own syntax, which is different from that of JavaScript.
> - WXS runtime environment is isolated from other JavaScript code. WXS does not support calling functions defined in other JavaScript files and APIs provided by Mini Apps.
> - The WXS function cannot be called back as an event of a component.
> - In Mini Apps on iOS, WXS is 2 to 20 times faster than JavaScript code, but on Android, they run almost equally fast.

The following are simple examples of WXS:

### Page rendering

```html WXML
<!--wxml-->
<wxs module="m1">
  var msg = "hello world";
  module.exports.message = msg;
</wxs>
<view>{{m1.message}}</view>
```

### Page output:

```
 hello world
```

### Data processing

```javascript
// page.js
Page({
  data: {
    array: [1, 2, 3, 4, 5, 1, 2, 3, 4],
  },
})
```

```html WXML
<!--wxml-->
<!-- The following `getMax` function takes an array and returns the value of the largest element in the array -->
<wxs module="m1">
  var getMax = function(array) {
    var max = undefined;
    for (var i = 0; i < array.length; ++i) {
       max = max === undefined ? array[i] : (max >= array[i] ? max : array[i]);
    }
return max; }
  module.exports.getMax = getMax;
</wxs>
<!-- Calls the `getMax` function in WXS with the `array` in `page.js` as the parameter -->
<view>{{m1.getMax(array)}}</view>
```

### Page output:

```
5
```

## Module

### WXS module

WXS code can be written in `<wxs>` tags in a `wxml` file or in files with the extension `.wxs`.

### Module

Each `.wxs` file or `<wxs>` tag is an independent module.

Each module has an independent scope. This means the variables and functions in a module are private by default and not visible to other modules.

A module can only externally expose its private variables and functions through `module.exports`.

### `.wxs` file

In **Super Hub Mini App Studio**, right-click to create a `.wxs` file. You can write WXS scripts directly in the file.

### Sample code:

```javascript
// /pages/comm.wxs
var foo = "'hello world' from comm.wxs"
var bar = function(d) {
return d }
module.exports = {
  foo: foo,
  bar: bar,
}
```

In the above sample, WXS code is written in the `/pages/comm.wxs` file. This `.wxs` file can be referenced by other `.wxs` files or `<wxs>` tags in WXML.

### `module` object

Each `wxs` module contains a built-in `module` object.

### Attribute

- `exports` : This attribute is used to share the module's private variables and functions externally.

### Sample code:

```javascript
// /pages/tools.wxs
var foo = "'hello world' from tools.wxs"
var bar = function(d) {
return d }
module.exports = {
  FOO: foo,
  bar: bar,
}
module.exports.msg = 'some msg'
```

```html WXML
<!-- page/index/index.wxml -->
<wxs src="./../tools.wxs" module="tools" />
<view>{{tools.msg}}</view>
<view>{{tools.bar(tools.FOO)}}</view>
```

Page output:

```
 some msg
'hello world' from tools.wxs
```

### `require` function

You can use a `require` function to reference another `wxs` file module in a `.wxs` module.

When referencing another `wxs` file module, you must note the following:

- You can only reference `.wxs` file modules and must use relative paths.
- All `wxs` modules are single instances. The first time a `wxs` module is referenced, it is automatically initialized as a single-instance object. Multiple pages, multiple regions, and multiple references all use the same `wxs` module object.
- If a `wxs` module is never referenced after it is defined, the module is not parsed or run.

### Sample code:

```javascript
// /pages/tools.wxs
var foo = "'hello world' from tools.wxs"
var bar = function(d) {
return d }
module.exports = {
  FOO: foo,
  bar: bar,
}
module.exports.msg = 'some msg'
```

```javascript
// /pages/logic.wxs
var tools = require('./tools.wxs')
console.log(tools.FOO)
console.log(tools.bar('logic.wxs'))
console.log(tools.msg)
```

```html WXML
<!-- /page/index/index.wxml -->
<wxs src="./../logic.wxs" module="logic" />
```

### Console output:

```
'hello world' from tools.wxs
logic.wxs
some msg
```

### `<wxs>` tag

| Attribute | Type   | Default Value                                                                                                                         | Description |
| :-------- | :----- | :------------------------------------------------------------------------------------------------------------------------------------ | :---------- |
| module    | String | The module name of the current `<wxs>` tag. This is a required field.                                                                 |             |
| src       | String | The relative path of the referenced `.wxs` file, only valid when this tag is a **single closed tag** or the **tag content is empty**. |             |

### `module` attribute

The `module` attribute is the module name of the current `<wxs>` tag. In a single `wxml` file, we recommend that this value be unique. In the case of duplicate module names, the value is overwritten based on the order (the latter overwrites the former). The names of WXS modules are not overwritten across different files.

The name specified by the `module` attribute value must comply with the following rules:

- The first character must be an English letter (a–z, A–Z) or underscore (\_).
- The remaining characters can be English letters (a–z, A–Z), underscores (\_), or digits (0–9).

### Sample code:

```html WXML
<!--wxml-->
<wxs module="foo">
  var some_msg = "hello world";
  module.exports = { msg : some_msg, }
</wxs>
<view>{{foo.msg}}</view>
```

Page output:

```
 hello world
```

The above sample declares a module named `foo` and exposes the `some_msg` variable to be used on the current page.

### `src` attribute

The `src` attribute is used to reference another `wxs` file module.

When referencing another `wxs` file module, you must note the following:

- You can only reference `.wxs` file modules and must use relative paths.
- All `wxs` modules are single instances. The first time a `wxs` module is referenced, it is automatically initialized as a single-instance object. Multiple pages, multiple regions, and multiple references all use the same `wxs` module object.
- If a `wxs` module is never referenced after it is defined, the module is not parsed or run.

### Sample code:

```javascript
// /pages/index/index.js
Page({
  data: {
    msg: "'hello wrold' from js",
  },
})
```

```html WXML
<!-- /pages/index/index.wxml -->
<wxs src="./../comm.wxs" module="some_comms"></wxs>
<!-- You can also directly use a single closed tag.
<wxs src="./../comm.wxs" module="some_comms" />
-->
<!-- Calls the `bar` function in the `some_comms` module, and the parameter is `foo` in the `some_comms` module. -->
<view>{{some_comms.bar(some_comms.foo)}}</view>
<!-- Calls the `bar` function in the `some_comms` module, and the parameter is `msg` in `page/index/index.js`. -->
<view>{{some_comms.bar(msg)}}</view>
```

### Page output:

```
'hello world' from comm.wxs
'hello wrold' from js
```

In the above sample, the `<wxs>` tag is used to reference the `/page/comm.wxs` module in the `/page/index/index.wxml` file.

> 📘 Notes
> 
> - A `<wxs>` module can only be accessed in the WXML file that defines the module. If you use `<include>` or `<import>`, `<wxs>` modules are not introduced into the corresponding WXML files.
> - In a `<template>` tag, you can only use the `<wxs>` module defined in the WXML file that defines the `<template>`.

## Variable

### Concept

- In WXS, all variables reference values.
- Undeclared variables that use directly assigned values are defined as global variables.
- If you declare a variable but do not assign a value, its default value is `undefined`.
- The `var` performance is consistent with JavaScript and variable hoisting is performed.

```javascript
var foo = 1
var bar = 'hello world'
var i // i === undefined
```

The above code declares three variables: `foo`, `bar`, and `i`. Then, foo is assigned the value of `1` and `bar` is assigned the string value `"hello world"`.

### Variable name

Variable names must comply with the following rules:

- The first character must be an English letter (a–z, A–Z) or underscore (\_).
- The remaining characters can be English letters (a–z, A–Z), underscores (\_), or digits (0–9).

### Reserved identifier

The following identifiers cannot be used as variable names:

```
delete
void
typeof
null
undefined
NaN
Infinity
var
if
else
true
false
require
this
function
arguments
return
for
while
do
break
continue
switch
case
default
```

## Annotation

WXS uses three main annotation methods.

### Sample code:

```html WXML
<!--wxml -->
<wxs module="sample">
  // Method 1: Single-line annotations
  /* Method 2: Multi-line annotations */
  /* Method 3: End annotations. This annotates all the WXS code starting from `/*`. var a = 1; var b = 2; var c = "fake";
</wxs>
```

In the above sample, all WXS code is annotated.

> The only difference between method 3 and method 2 is the lack of the `*/` terminator.

## Operator

### Basic operators

#### Sample code:

```javascript
var a = 10, b = 20
// Addition
console.log(30 === a + b)
// Subtraction
console.log(-10 === a - b)
// Multiplication
console.log(200 === a * b)
// Division
console.log(0.5 === a / b)
// Complementation
console.log(10 === a % b)
```

- The addition operation (`+`) can also be used to concatenate strings.

```javascript
var a = '.q', b = 's'
// String concatenation
console.log('.wxs' === a + b)
```

### Unary operator

#### Sample code:

```javascript
var a = 10, b = 20
// Auto increment
console.log(10 === a++)
console.log(12 === ++a)
// Auto decrement
console.log(12 === a--)
console.log(10 === --a)
// Positive value
console.log(10 === +a)
// Negative value
console.log(0 - 10 === -a)
// Not
console.log(-11 === ~a)
// Negate
console.log(false === !a)
// delete
console.log(true === delete a.fake)
// void
console.log(undefined === void a)
// typeof
console.log('number' === typeof a)
```

### Bit operator

#### Sample code:

```javascript
var a = 10, b = 20
// Left shift
console.log(80 === a << 3)
// Unsigned right shift
console.log(2 === a >> 2)
// Signed right shift
console.log(2 === a >>> 2)
// AND
console.log(2 === (a & 3))
// XOR
console.log(9 === (a ^ 3))
// OR
console.log(11 === (a | 3))
```

### Relational operator

#### Sample code:

```javascript
var a = 10, b = 20
// Less than
console.log(true === a < b)
// Greater than
console.log(false === a > b)
// Less than or equal to
console.log(true === a <= b)
// Greater than or equal to
console.log(false === a >= b)
```

### Equivalence operator

#### Sample code:

```javascript
var a = 10, b = 20
// Equal sign
console.log(false === (a == b))
// Not equal sign
console.log(true === (a != b))
// Equivalent sign
console.log(false === (a === b))
// Not equivalent sign
console.log(true === (a !== b))
```

### Assignment operator

#### Sample code:

```javascript
var a = 10
a = 10
a *= 10
console.log(100 === a)
a = 10
a /= 5
console.log(2 === a)
a = 10
a %= 7
console.log(3 === a)
a = 10
a += 5
console.log(15 === a)
a = 10
a -= 11
console.log(-1 === a)
a = 10
a <<= 10
console.log(10240 === a)
a = 10
a >>= 2
console.log(2 === a)
a = 10
a >>>= 2
console.log(2 === a)
a = 10
a &= 3
console.log(2 === a)
a = 10
a ^= 3
console.log(9 === a)
a = 10
a |= 3
console.log(11 === a)
```

### Binary logical operator

#### Sample code:

```javascript
var a = 10, b = 20
// Logical AND
console.log(20 === (a && b))
// Logical OR
console.log(10 === (a || b))
```

### Other operators

#### Sample code:

```javascript
var a = 10, b = 20
//Conditional operator
console.log(20 === (a >= 10 ? a + 10 : b + 10))
//Comma operator
console.log(20 === (a, b))
```

### Operator priority

| Priority | Operator         | Description              | Associativity |               |
| :------- | :--------------- | :----------------------- | :------------ | :------------ |
| 20       | `(` ...  `)`     | Brackets                 | n/a           |               |
| 19       | ... . ...        | Member access            | Left to right |               |
|          | ... `[` ... `]`  | Member access            | Left to right |               |
|          | ... `(` ... `)`  | Function call            | Left to right |               |
| 17       | ... `++`         | Postfix increment        | n/a           |               |
|          | ... `--`         | Postfix decrement        | n/a           |               |
| 16       | `!` ...          | Logical NOT              | Right to left |               |
|          | `~` ...          | Bitwise NOT              | Right to left |               |
|          | `+` ...          | Unary addition           | Right to left |               |
|          | `-` ...          | Unary subtraction        | Right to left |               |
|          | `++` ...         | Prefix increment         | Right to left |               |
|          | `--` ...         | Prefix decrement         | Right to left |               |
|          | `typeof` ...     | typeof                   | Right to left |               |
|          | `void` ...       | void                     | Right to left |               |
|          | `delete` ...     | delete                   | Right to left |               |
| 14       | ... `*` ...      | Multiplication           | Left to right |               |
|          | ... `/` ...      | Division                 | Left to right |               |
|          | ... `%` ...      | Modulo                   | Left to right |               |
| 13       | ... `+` ...      | Addition                 | Left to right |               |
|          | ... `-` ...      | Subtraction              | Left to right |               |
| 12       | ... `<<` ...     | Bitwise left shift       | Left to right |               |
|          | ... `>>` ...     | Bitwise right shift      | Left to right |               |
|          | ... `>>>` ...    | Unsigned right shift     | Left to right |               |
| 11       | ... `<` ...      | Less than                | Left to right |               |
|          | ... `<=` ...     | Less than or equal to    | Left to right |               |
|          | ... `>` ...      | Greater than             | Left to right |               |
|          | ... `>=` ...     | Greater than or equal to | Left to right |               |
| 10       | ... `==` ...     | Equal sign               | Left to right |               |
|          | ... `!=` ...     | Not equal sign           | Left to right |               |
|          | ... `===`...     | Equivalent sign          | Left to right |               |
|          | ... `!==` ...    | Not equivalent sign      | Left to right |               |
| 9        | ... `&` ...      | Bitwise AND              | Left to right |               |
| 8        | ... `^` ...      | Bitwise XOR              | Left to right |               |
| 7        | ... \`           | \` ...                   | Bitwise OR    | Left to right |
| 6        | ... `&&` ...     | Logical AND              | Left to right |               |
| 5        | ... `｜｜`...      | Logical OR               | Left to right |               |
| 4        | ... `?`...`:`... | Conditional operator     | Right to left |               |
| 3        | ... `=` ...      | Value assignment         | Right to left |               |
|          | ... `+=` ...     | Value assignment         | Right to left |               |
|          | ... `-=` ...     | Value assignment         | Right to left |               |
|          | ... `*=` ...     | Value assignment         | Right to left |               |
|          | ... `/=` ...     | Value assignment         | Right to left |               |
|          | ... `%=` ...     | Value assignment         | Right to left |               |
|          | ... `<<=` ...    | Value assignment         | Right to left |               |
|          | ... `>>=` ...    | Value assignment         | Right to left |               |
|          | ... `>>>=` ...   | Value assignment         | Right to left |               |
|          | ...` &=` ...     | Value assignment         | Right to left |               |
|          | ... `^=` ...     | Value assignment         | Right to left |               |
|          | ... `｜=` ...     | Value assignment         | Right to left |               |
| 0        | ... `,` ...      | Comma                    | Left to right |               |

## Statement

### `if` statement

In WXS, you can use `if` statements in the following formats:

- `if (expression) statement`: Execute statement when expression is `truthy`.
- `if (expression) statement1 else statement2`: Execute `statement1` when `expression` is `truthy`; otherwise, execute `statement2`.
- `if ... else if ... else statementN`: Using this statement, you can choose one from `statement1` to `statementN` for execution.

### Sample syntax:

```javascript
// if ...
if (expression) statement
if (expression) statement
if (expression) {
  code block
}
// if ... else
if (expression) statement
else statement
if (expression) statement
else statement
if (expression) {
  code block
} else {
  code block
}
// if ... else if ... else ...
if (expression) {
  code block
} else if (expression) {
  code block
} else if (expression) {
  code block
} else {
  code block
}
```

### `switch` statement

Sample syntax:

```javascript
switch (expression) {
  case variable:
    statement;
  case number:
    statement;
    break;
  case string:
    statement;
  default:
    statement;
}
```

- `default` branches can be omitted.
- After the `case` keyword, you can only use a variable, number, or string.

### Sample code:

```javascript
var exp = 10;
switch (exp) {
  case "10":
    console.log("string 10");
    break;
  case 10:
    console.log("number 10");
    break;
  case exp:
    console.log("var exp");
    break;
  default:
    console.log("default");
}
```

### Output:

```
number 10
```

### `for` statement

Sample syntax:

```javascript
for (statement; statement; statement) statement
for (statement; statement; statement) {
  code block
}
```

- Supports the use of `break` and `continue` keywords.

### Sample code:

```javascript
for (var i = 0; i < 3; ++i) {
  console.log(i)
  if (i >= 1) break
}
```

### Output:

```
0 
1
```

### `while` statement

Sample syntax:

```javascript
while (expression) statement
while (expression) {
  code block
}
do {
  code block
} while (expression)
```

- When `expression` is true, loop execute `statement` or `code block`.
- Supports the use of `break` and `continue` keywords.

## Data types

The WXS language currently supports the following data types:

- `number` : `number`
- `string` : `string`
- `boolean` : `boolean`
- `object` : `object`
- `function` : `function`
- `array` : `array`
- `date` : `date`
- `regexp` : `regexp`(regular expression)

### number

**Syntax**

There are two types of numbers: integers and decimals.

```javascript
var a = 10
var PI = 3.141592653589793
```

#### Attribute

- `constructor` : Returns the string `"Number"`

#### Method

- `toString`
- `toLocaleString`
- `valueOf`
- `toFixed`
- `toExponential`
- `toPrecision`

> For information on how to use the above methods, refer to the ES5 standard.

### string

**Syntax**

There are two ways to write a string:

```javascript
'hello world'
"hello world"
```

#### Attribute

- `constructor` : Returns the string `"String"`.
- `length`

> For descriptions of attributes other than constructor , refer to the ES5 standard.

#### Method

- `toString`
- `valueOf`
- `charAt`
- `charCodeAt`
- `concat`
- `indexOf`
- `lastIndexOf`
- `localeCompare`
- `match`
- `replace`
- `search`
- `slice`
- `split`
- `substring`
- `toLowerCase`
- `toLocaleLowerCase`
- `toUpperCase`
- `toLocaleUpperCase`
- `trim`

> For information on how to use the above methods, refer to the ES5 standard.

### boolean

**Syntax**

Boolean values can take either of the two values: `true` and `false`.

#### Attribute

- `constructor` : Returns the string `"Boolean"`.

#### Method

- `toString`
- `valueOf`

> For information on how to use the above methods, refer to the ES5 standard.

### object

**Syntax**

An object is a type of unordered key-value pair, which can be used in the following ways:

```javascript
var o = {} // Generate a new empty object
// Generate a new non-empty object
o= {
string: 1, //The object's key can be a string.
const_var: 2, //The object's key can also be an identifier that conforms to the variable definition rules. func: {}, //The object's value can be of any type.
}
//Object attribute read operation
console.log(1 === o['string'])
console.log(2 === o.const_var)
//Object attribute write operation
o['string']++
o['string'] += 10
o.const_var++
o.const_var += 10
//Object attribute read operation
console.log(12 === o['string'])
console.log(13 === o.const_var)
```

#### Attribute

- `constructor` : Returns the string `"Object"`.

```javascript
console.log('Object' === { k: '1', v: '2' }.constructor)
```

#### Method

- `toString` : Returns the string `"[object Object]"`.

### function

**Syntax**

`function` supports the following definition methods:

```javascript
//Method 1
function a(x) {
return x 
}

//Method 2
var b = function(x) {
  return x
}
```

`function` also supports the following syntax (anonymous functions, closures, etc.):

```
var a = function(x) {
  return function() {
		return x 
  }
}

var b = a(100)
console.log(100 === b())
```

#### arguments

In `function` , you can use the `arguments` keyword. This keyword only has the following attributes at present:

- `length` : The number of arguments passed to the function.
- `[index]` : Each argument passed to the function can be traversed by the `index` subscript.

#### Sample code:

```javascript
var a = function() {
  console.log(3 === arguments.length)
  console.log(100 === arguments[0])
  console.log(200 === arguments[1])
  console.log(300 === arguments[2])
}

a(100, 200, 300)
```

#### Attribute

- `constructor` : Returns the string `"Function"`.
- `length` : Returns the number of formal parameters of the function.

#### Method

- toString : Returns the string "[function Function]"

#### Sample code:

```javascript
var func = function(a, b, c) {}
console.log('Function' === func.constructor)
console.log(3 === func.length)

console.log('[function Function]' === func.toString())
```

### array

**Syntax**

`array` supports the following definition methods:

```javascript
var a = [] //Generate a new empty array

a = [1, '2', {}, function() {}] //Generate a new non-empty array, with array elements of any type
```

#### Attribute

- `constructor` : Returns the string `"Array"`.
- `length`

> For descriptions of attributes other than constructor , refer to the ES5 standard.

#### Method

- `toString`
- `concat`
- `join`
- `pop`
- `push`
- `reverse`
- `shift`
- `slice`
- `sort`
- `splice`
- `unshift`
- `indexOf`
- `lastIndexOf`
- `every`
- `some`
- `forEach`
- `map`
- `filter`
- `reduce`
- `reduceRight`

> For information on how to use the above methods, refer to the ES5 standard.

### date

**Syntax**

Generates the `getDate` function required by the `date` object and returns a current time object.

```javascript
getDate()
getDate(milliseconds)
getDate(datestring)

getDate(year, month[, date[, hours[, minutes[, seconds[, milliseconds]]]]])
```

- ##### Parameters
  - `milliseconds` : The number of milliseconds from 00:00:00 UTC January 1, 1970.
  - `datestring` : The date string in the format of "month day, year hours:minutes:seconds".

#### Sample code:

```javascript
var date = getDate() //Return the current time object

date = getDate(1500000000000)
// Fri Jul 14 2017 10:40:00 GMT+0800 (China Standard Time)

date = getDate('2017-7-14')
// Fri Jul 14 2017 00:00:00 GMT+0800 (China Standard Time)

date = getDate(2017, 6, 14, 10, 40, 0, 0)
// Fri Jul 14 2017 10:40:00 GMT+0800 (China Standard Time)
```

#### Attribute

- `constructor` : Returns the string `"Date"`.

#### Method

- `toString`
- `toDateString`
- `toTimeString`
- `toLocaleString`
- `toLocaleDateString`
- `toLocaleTimeString`
- `valueOf`
- `getTime`
- `getFullYear`
- `getUTCFullYear`
- `getMonth`
- `getUTCMonth`
- `getDate`
- `getUTCDate`
- `getDay`
- `getUTCDay`
- `getHours`
- `getUTCHours`
- `getMinutes`
- `getUTCMinutes`
- `getSeconds`
- `getUTCSeconds`
- `getMilliseconds`
- `getUTCMilliseconds`
- `getTimezoneOffset`
- `setTime`
- `setMilliseconds`
- `setUTCMilliseconds`
- `setSeconds`
- `setUTCSeconds`
- `setMinutes`
- `setUTCMinutes`
- `setHours`
- `setUTCHours`
- `setDate`
- `setUTCDate`
- `setMonth`
- `setUTCMonth`
- `setFullYear`
- `setUTCFullYear`
- `toUTCString`
- `toISOString`
- `toJSON`

> For information on how to use the above methods, refer to the ES5 standard.

### regexp

**Syntax**

Generates the `getRegExp` function to be used by the `regexp` object.

```javascript
getRegExp(pattern[, flags])
```

- Parameters:
  - `pattern` : The content of the regular expression.
  - `flags` : The modifiers. This field can only contain the following characters:
    - `g` : global
    - `i` : ignoreCase
    - `m` : multiline

#### Sample code:

```javascript
var a = getRegExp('x', 'img')
console.log('x' === a.source)
console.log(true === a.global)
console.log(true === a.ignoreCase)
console.log(true === a.multiline)
```

#### Attribute

- `constructor` : Returns the string `"RegExp"`.
- `source`
- `global`
- `ignoreCase`
- `multiline`
- `lastIndex`

> For descriptions of attributes other than constructor , refer to the ES5 standard.

#### Method

- `exec`
- `test`
- `toString`

> For information on how to use the above methods, refer to the ES5 standard.

## Data type determination

### `constructor` attribute

You can use the `constructor` attribute to determine the data type.

#### Sample code:

```javascript
var number = 10
console.log('Number' === number.constructor)
var string = 'str'
console.log('String' === string.constructor)
var boolean = true
console.log('Boolean' === boolean.constructor)
var object = {}
console.log('Object' === object.constructor)
var func = function() {}
console.log('Function' === func.constructor)
var array = []
console.log('Array' === array.constructor)
var date = getDate()
console.log('Date' === date.constructor)
var regexp = getRegExp()
console.log('RegExp' === regexp.constructor)
```

### typeof

You can also use `typeof` to distinguish certain data types.

#### Sample code:

```
var number = 10
var boolean = true
var object = {}
var func = function() {}
var array = []
var date = getDate()
var regexp = getRegExp()
console.log('number' === typeof number)
console.log('boolean' === typeof boolean)
console.log('object' === typeof object)
console.log('function' === typeof func)
console.log('object' === typeof array)
console.log('object' === typeof date)
console.log('object' === typeof regexp)
console.log('undefined' === typeof undefined)
console.log('object' === typeof null)
```

## Base class library

### console

The `console.log` method is used to output messages in the console window. This method can accept multiple parameters and concatenate their results for output.

### Math

#### Attribute

- `E`
- `LN10`
- `LN2`
- `LOG2E`
- `LOG10E`
- `PI`
- `SQRT1_2`
- `SQRT2`

> For information on how to use the above attributes, refer to the ES5 standard.

#### Method

- `abs`
- `acos`
- `asin`
- `atan`
- `atan2`
- `ceil`
- `cos`
- `exp`
- `floor`
- `log`
- `max`
- `min`
- `pow`
- `random`
- `round`
- `sin`
- `sqrt`
- `tan`

> For information on how to use the above methods, refer to the ES5 standard.

### JSON

#### Method

- `stringify(object)` : Converts the `object` object into a JSON string and returns the string.
- `parse(string)` : Converts the JSON string into an object and returns the object.

#### Sample code:

```
console.log(undefined === JSON.stringify())
console.log(undefined === JSON.stringify(undefined))
console.log('null' === JSON.stringify(null))

console.log('111' === JSON.stringify(111))
console.log('"111"' === JSON.stringify('111'))
console.log('true' === JSON.stringify(true))
console.log(undefined === JSON.stringify(function() {}))

console.log(undefined === JSON.parse(JSON.stringify()))
console.log(undefined === JSON.parse(JSON.stringify(undefined)))
console.log(null === JSON.parse(JSON.stringify(null)))

console.log(111 === JSON.parse(JSON.stringify(111)))
console.log('111' === JSON.parse(JSON.stringify('111')))
console.log(true === JSON.parse(JSON.stringify(true)))

console.log(undefined === JSON.parse(JSON.stringify(function() {})))
```

### Number

#### Attribute

- `MAX_VALUE`
- `MIN_VALUE`
- `NEGATIVE_INFINITY`
- `POSITIVE_INFINITY`

> For information on how to use the above attributes, refer to the ES5 standard.

### Date

#### Attribute

- `parse` 
- `UTC` 
- `now`

> For information on how to use the above attributes, refer to the ES5 standard.

### Global

#### Attribute

- `NaN`
- `Infinity`
- `undefined`

> For information on how to use the above attributes, refer to the ES5 standard.

#### Method

- `parseInt`
- `parseFloat`
- `isNaN`
- `isFinite`
- `decodeURI`
- `decodeURIComponent`
- `encodeURI`
- `encodeURIComponent`

> For information on how to use the above methods, refer to the ES5 standard.
