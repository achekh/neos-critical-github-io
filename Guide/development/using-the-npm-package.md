---
title: "Using a package from npm"
slug: "using-the-npm-package"
excerpt: ""
hidden: false
metadata: 
  image: []
  robots: "index"
createdAt: "Fri May 12 2023 04:24:32 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Wed Jun 07 2023 01:30:07 GMT+0000 (Coordinated Universal Time)"
layout: "default"
parent: "Using npm"
grand_parent: "Guide"
---
## Initializing npm

Run the command `npm init` inside your project's home folder in order to initialize npm for your Mini App project.

## Adding the package to package.json

Add your dependency to the `dependencies` section in the `package.json` file.

## Installing the npm package

Run the following command in the directory where the Mini App's `package.json` is located to install the npm package:

`npm install`

## Building npm

Click on the menu bar in the DevTools: Tools > Build npm

![](https://files.readme.io/94da698-small-Screenshot_2023-05-12_at_10.40.22_AM.png)

**After building is completed, the npm package can be used.**

Import the npm package into JS:

```javascript
const myPackage = require('packageName');
const packageOther = require('packageName/other');
```

Use custom components in the npm package:

```json
{  
  "usingComponents": {  
    "myPackage": "packageName",  
    "package-other": "packageName/other"  
  }  
}
```

## Usage restrictions on the npm package

The npm package cannot have any browser APIs and can only provide a pure JavaScript interpretation and execution environment (for more information, refer to the Mini App dual-process model).  
Therefore, the Mini App environment is special, and some global variables (such as the window object) and constructors (such as the function constructor) cannot be used.  
Taking the commonly used `lodash` library as an example, directly importing it into the Mini App environment will cause some compatibility issues, resulting in the following error:

`Uncaught TypeError: Cannot read property 'prototype' of undefined`

You can do a simple polyfill to fix some global variables used when `lodash` is loaded for the first time.  
Under normal circumstances, as long as you redefine the global object, you can use the features of lodash properly. Note that the **redefined code must be imported before** `lodash` is referenced. The sample code is as follows:

```javascript
// fix-lodash.js

global.Object = Object;
global.Array = Array;
global.DataView = DataView;
global.Date = Date;
global.Error = Error;
global.Float32Array = Float32Array;
global.Float64Array = Float64Array;
global.Function = Function;
global.Int8Array = Int8Array;
global.Int16Array = Int16Array;
global.Int32Array = Int32Array;
global.Map = Map;
global.Math = Math;
global.Promise = Promise;
global.RegExp = RegExp;
global.Set = Set;
global.String = String;
global.Symbol = Symbol;
global.TypeError = TypeError;
global.Uint8Array = Uint8Array;
global.Uint8ClampedArray = Uint8ClampedArray;
global.Uint16Array = Uint16Array;
global.Uint32Array = Uint32Array;
global.WeakMap = WeakMap;
global.clearTimeout = clearTimeout;
global.isFinite = isFinite;
global.parseInt = parseInt;
global.setTimeout = setTimeout;
```

As long as you reference the file reassigning a value to global above before importing `lodash` in the page file, you can use the features of `lodash` normally. The sample code is as follows:

```javascript
import "./fix-lodash.js";
import _ from "../miniprogram_npm/lodash/index";

Page({
  // Click **Submit**
  submit: _.debounce(
    async function () {
      // A series of form operations
		},
    1000
  );
});
```
