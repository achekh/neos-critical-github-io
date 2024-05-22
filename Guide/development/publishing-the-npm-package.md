---
title: "Publishing the npm package"
slug: "publishing-the-npm-package"
excerpt: ""
hidden: false
metadata: 
  image: []
  robots: "index"
createdAt: "Fri May 12 2023 05:24:11 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Fri Jul 14 2023 11:30:03 GMT+0000 (Coordinated Universal Time)"
---
## Constraints on publishing the Mini App npm package

The npm package to be published here refers to the npm package customized for the Mini App (hereinafter referred to as the Mini App npm package). Because of the special nature of the custom components of Mini Apps, the original npm package work flow needs to be adjusted. Therefore, some constraints should be made on the Mini App npm package:

1. The Mini App npm package requires a build files generation directory under the root directory (which is `miniprogram_dist` by default). You can specify this directory by adding the `miniprogram` field in the `package.json` file, for example:

```json
{
  "name": "miniprogram-custom-component",
  "version": "1.0.0",
  "description": "",
  "miniprogram": "dist", // Specify the build files generation directory
  "devDependencies": {},
  "dependencies": {}
}
```

1. Only the build file generation directory in the Mini App npm package will be counted in the space used by the Mini App package, and only the code in this directory will be uploaded when the Mini App code is uploaded. If the Mini App npm package has code files related to test and build, put them outside the build file generation directory. You can also use the `.npmignore` file to avoid publishing non-business code files to npm.
2. Put the dependencies related to test and build into the devDependencies field to avoid packaging them together into the Mini App package.

## Constraints on publishing other npm packages

If some already published npm packages cannot be transformed into the structure of the Mini App npm package for some reasons, they can also be used after fine-tuning, but note the following points:

1. Only **pure JS packages** are supported, while custom components are not.
2. There must be an entry file; that is, you need to make sure that the `main` field in `package.json` points to a correct entry. If there is no `main` field in `package.json` , `index.js` in the root directory of the npm package will be used as the entry file.
3. Put the dependencies related to test and build into the devDependencies field to avoid packaging them together into the Mini App package.
4. Dependency on C++ addons and Node.js built-in libraries is **not supported**.

> 📘 Note
> 
> Some Node.js built-in libraries implemented in pure JS (such as the path module) can be supported by additionally installing npm packages implemented by other developers.

```javascript
const addon = require('./addon.node'); // Not supported
const http = require('http'); // Not supported
```

1. The following methods are also not allowed when the require dependency is used:

```javascript
// It is not allowed to assign `require` to other variables before using it. For example, the following code will not parse the dependencies:
let r;
r = require;
r('testa');
let r2 = require;
r2('testa');
// It is not allowed to require a variable. For example, the following code depends on the runtime and cannot parse the dependencies:
let m = 'testa';
require(m);
```

> 📘 Note
> 
> The Mini App environment is quite special, so some global variables (such as the window object) and constructors (such as the function constructor) cannot be used.

## Publishing process

The process of publishing the npm package is as described below:

1. If you don't have a npm account yet, go to the [npm website](https://www.npmjs.com/) to register one.
2. Log in to the npm account and run the following command locally:  
    `npm adduser`  
   Or  
    `npm login`
3. Run the following command in the root directory of the written npm package:  
   `npm publish`

At this point, the npm package successfully publishes to the npm platform.

> 📘 Notes
> 
> If you modify the npm source during development, when logging in or publishing, be sure to switch the source back to the npm source.

## How it works

To help you better understand the various requirements for npm package publishing mentioned above, the following describes how the process works:

1. The `node_modules` directory will not participate in compiling, uploading, and packaging, so the Mini App must go through the process of **"npm build"** if it wants to use the npm package. In each `miniprogramRoot` , a `miniprogram_npm` directory will be generated at the same directory level as the outer `node_modules` of the declared `package.json`. It will store the built and packaged npm package, i.e., the npm package actually used by the Mini App.
2. There are two types of building and packaging: The Mini App npm package will directly copy all the files in the build file generation directory to `miniprogram_npm` , while other npm packages will go through the dependency analysis and packaging process starting from the entry JS file  
   (Similar to webpack).
3. The process of finding a npm package is similar to the implementation of npm. The system searches outward level by level starting from the directory where the files that depend on the npm package are located until it finds an available npm package or the root directory of the Mini App. The following briefly describes the directory structure before and after building and packaging.

   Structure before building:

   ![](https://files.readme.io/75fd6e5-small-Screenshot_2023-05-12_at_11.09.45_AM.png)  

   Structure after building:

   ![](https://files.readme.io/950b882-small-Screenshot_2023-05-12_at_11.11.22_AM.png)

   > Note: The code generated by packaging will generate a source map file at the same directory level for the purpose of reverse debugging.

### The default way to build npm

By default, after `package.json` is correctly configured in `miniprogramRoot` and `npm install` is executed, the result of npm building is to build a `miniprogram_npm` for each `node_modules` corresponding to `package.json` and place it in a subdirectory in the directory of the corresponding `package.json`.

#### Before npm building:

![](https://files.readme.io/5fadd36-small-Screenshot_2023-05-12_at_11.18.58_AM.png)

#### After npm building:

![](https://files.readme.io/0a034c7-small-Screenshot_2023-05-12_at_11.19.52_AM.png)
