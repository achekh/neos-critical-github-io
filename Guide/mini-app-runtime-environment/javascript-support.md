---
title: "JavaScript Support"
slug: "javascript-support"
excerpt: "This section explains the concept of JavaScript Support."
hidden: true
metadata: 
  robots: "index"
createdAt: "Mon May 01 2023 11:14:52 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Wed May 03 2023 10:17:09 GMT+0000 (Coordinated Universal Time)"
layout: "default"
parent: "Mini Program Runtime"
grand_parent: "Guide"
---
# Supports for JavaScript

## Operation Limits

For security reasons, JS code cannot be dynamically executed in Mini Programs. In other words:

- JS code cannot be executed via `eval`.
- No functions can be created with `new Function`.

## Supports for Client ES6 API

Mini Programs support most ES6 APIs as listed below (some APIs are subject to OS versions):

| String               | iOS10 | Android |
| :------------------- | :---- | :------ |
| codePointAt          |       |         |
| normalize            |       |         |
| includes             |       |         |
| startsWith           |       |         |
| endsWith             |       |         |
| repeat               |       |         |
| String.fromCodePoint |       |         |

| Array      | iOS10 | Android |
| :--------- | :---- | :------ |
| copyWithin |       |         |
| find       |       |         |
| findIndex  |       |         |
| fill       |       |         |
| entries    |       |         |
| keys       |       |         |
| values     |       | ✘       |
| includes   |       |         |
| Array.from |       |         |
| Array.of   |       |         |

| Number        | iOS10 | Android |
| :------------ | :---- | :------ |
| isFinite      |       |         |
| isNaN         |       |         |
| parseInt      |       |         |
| parseFloat    |       |         |
| isInteger     |       |         |
| EPSILON       |       |         |
| isSafeInteger |       |         |

| Math   | iOS10 | Android |
| :----- | :---- | :------ |
| trunc  |       |         |
| sign   |       |         |
| cbrt   |       |         |
| clz32  |       |         |
| imul   |       |         |
| fround |       |         |
| hypot  |       |         |
| expm1  |       |         |
| log1p  |       |         |
| log10  |       |         |
| log2   |       |         |
| sinh   |       |         |
| cosh   |       |         |
| tanh   |       |         |
| asinh  |       |         |
| acosh  |       |         |
| atanh  |       |         |

| Object                   | iOS10 | Android |
| :----------------------- | :---- | :------ |
| is                       |       |         |
| assign                   |       |         |
| getOwnPropertyDescriptor |       |         |
| keys                     |       |         |
| getOwnPropertyNames      |       |         |
| getOwnPropertySymbols    |       |         |

| Object  | iOS10 | Android |
| :------ | :---- | :------ |
| Symbol  |       |         |
| Set     |       |         |
| Map     |       |         |
| Proxy   |       | ✘       |
| Reflect |       |         |
| Promise |       |         |
