---
title: "Writing tests for Mini Apps"
slug: "writing-tests-for-mini-apps"
excerpt: ""
hidden: false
metadata: 
  image: []
  robots: "index"
createdAt: "Wed May 17 2023 07:31:32 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Fri Jul 14 2023 11:25:45 GMT+0000 (Coordinated Universal Time)"
layout: "default"
parent: "Advanced topics"
grand_parent: "Guide"
---
In order to write tests for Mini apps, you can use the library `miniprogram-simulate`

### Introduction

At present, there is no elegant solution for unit testing of Mini app custom components because of the unique running environment of Mini apps, and this toolset is born to solve this pain point. The original mechanism of double-threaded separation of Mini app custom components into single-threaded simulation, using the dom environment for rendering, so as to complete the entire custom component tree construction.

This toolset relies on a js runtime environment and a dom environment, so it can use jsdom + nodejs (e.g. jest) or a real browser environment (e.g. karma). Documentation [usage profile]\(. /docs/tutorial.md) provides a brief introduction to its use.

### Installation

```shell npm
npm install --save-dev miniprogram-simulate
```

### Usage

```javascript JavaScript
const simulate = require('miniprogram-simulate')

test('test sth', () => {
    const id = simulate.load('/components/comp/index') // Loading custom component
    const comp = simulate.render(id) // Rendering custom component

    // Use custom component wrapper instance comp objects to perform various unit tests.
})
```

The above is just a simple example, in fact this toolset must be used with a testing framework such as jest or jsdom/mocha, for more details please refer to the following documentation.

### Framework Selection

It can be used with most popular frameworks, as long as it meets the js runtime environment and dom environment. Here is a brief introduction to jest and karma:

#### Jest

1. Install jest and configuration reference [jest official website](https://jestjs.io/docs/getting-started)
2. Configure jest:

```json
{
   // jest is tested directly in the nodejs environment, and jsdom is used to simulate the dom environment. When using it, you need to configure jest's `testEnvironment` to `jsdom`.
   // jest has built-in jsdom, so no additional import is required.
   "testEnvironment": "jsdom",
   // Configure jest-snapshot-plugin to obtain a more human-readable structure when using jest's snapshot function
   "snapshotSerializers": ["miniprogram-simulate/jest-snapshot-plugin"]
}
```

For specific jest configuration, please refer to configuration the following configurations:

```json jest.config.js
module.exports = {
    bail: 1,
    verbose: true,
    testEnvironment: 'jsdom',
    testURL: 'https://jest.test',
    moduleFileExtensions: ['js', 'ts'],
    testMatch: ['<rootDir>/src/**/__test__/**/*.test.{js,ts}'],
    collectCoverageFrom: [
        '<rootDir>/src/**/*.{js,ts}',
        '!<rootDir>/src/weui-wxss/**',
        '!**/__test__/**'
    ],
    snapshotSerializers: ['miniprogram-simulate/jest-snapshot-plugin']
}
```

#### Karma

Karma can use the real environment of the browser to run test cases, but because the files of the applet custom components are split, and the browser environment does not have file system support, so some special processing is required.

Install preprocessors:

```shell npm
npm install --save-dev karma-dirname-preprocessor karma-filemap-preprocessor karma-webpack
```

Configure the basePath, files, preprocessors, webpack fields in karma.conf.js:

```json karma.conf.js
module. exports = function(config) {
     config.set({
         // Other configuration  …
         basePath: path.resolve(__dirname, './test'), // The root directory of the tested component, because of the limitation of the compiler, all tested components must be in this directory
         files: [
             'node_modules/miniprogram-simulate/build.js', // inject miniprogram-simulate, the simulate object will be mounted under window
             'test/spec/*.spec.js', // test case
             'src/component/*', // component file, try not to include ../ or ./ in the path, otherwise the wcc compiler may not recognize it
         ],
         preprocessors: {
             'src/component/*': ['filemap'], // Component files use filemap to inject the content of each file into the browser, try not to include ../ or ./ in the path, otherwise the wcc compiler may not recognize it
             'test/spec/*.spec.js': ['webpack', 'dirname'], // Use webpack for packaging, use dirname to process the __dirname variable in the test case
         },
         webpack: {
             optimization: {
                 minimize: false, // no compression, easy to debug
             },
             node: {
                 __dirname: false, // do not inject __dirname, handled by preprocessor
             },
         },
         // Other configuration  …
     })
}
```

Then the test case is written as follows (using mocha + chai as an example):

```javascript
const path = require('path')
const expect = require('chai').expect

describe('component', () => {
     it ('should run successfully', () => {
         // Use simulate or window.simulate directly here, no need to do require

         const id = simulate.load(path.resolve(__dirname, '../src/component/index'))
         const comp = simulate. render(id, {prop: 'index. test. properties'})

         comp.attach(document.body) // mount under body

         expect(simulate.match(comp.dom, '<wx-view class="main--index">index.test.properties</wx-view>')).to.equal(true)
     })
})
```

> 📘 Note
> 
> When using karma to test, only official compilers are supported to compile wxml files, and js simulated compilers are not supported, so even if compiler: 'simulate' is configured in the simulate.load method, it will not take effect.

### User guide (Jest)

Import test tools:

```javascript JavaScript
const simulate = require('miniprogram-simulate')
```

Example:

```javascript
test('comp', () => {
     const id = simulate.load(path.join(__dirname, './comp')) // load custom component, return component id
     const comp = simulate.render(id) // use id to render the custom component, and return the package instance of the component

     const parent = document.createElement('parent-wrapper') // create container node
     comp.attach(parent) // inserting the component into the container node will trigger the attached lifecycle

     expect(comp.dom.innerHTML).toBe('<div>123</div>') // Judge the rendering result of the component
     // Execute some other test logic

     comp.detach() // Remove the component from the container node, which will trigger the detached life cycle
})
```

Pass in initial rendering props:

```javascript
test('comp', () => {
     const comp = simulate.render(id, {
         propName: 'propValue',
     })
})
```

Retrieve data:

```javascript JavaScript
test('comp', () => {
     // Determine component data
     expect(comp.data).toEqual({
         a: 111,
     })
})
```

Update data:

```javascript
test('comp', () => {
     // update component data
     comp.setData({
         a: 123,
     })
})
```

Get child components:

```javascript
test('comp', () => {
     const childComp = comp. querySelector('#child-id')
     expect(childComp.dom.innerHTML).toBe('<div>child</div>')
})
```

Get the list of child components:

```javascript
test('comp', () => {
     const childrenComp = comp.querySelectorAll('.child-item')
     expect(childrenComp. length).toBe(3)
})
```

Trigger event:

```javascript
test('comp', () => {
     comp.dispatchEvent('touchstart') // Trigger the touchstart event of the component
     childComp.dispatchEvent('tap') // Trigger the tap event of the child component
})
```

Trigger life cycle event:

```javascript
test('comp', () => {
     comp.triggerLifeTime('ready') // Trigger the ready life cycle of the component
     childComp.triggerLifeTime('moved') // trigger the moved life cycle of the child component
})
```

Get component instance (this)

```javascript
test('comp', () => {
     const that = comp.instance // Note that comp is not returned here, comp is an object encapsulated on the component instance, and what is returned here is the component instance, that is, this in the component method definition

     that.data // Get the data object of the component, which is the same as the object obtained by comp.data
     that.xxx() // Call the methods defined in the component methods definition section
})
```

### API

#### behavior(definition):

Register and return the object of behavior.

**Definition:** behavior defines the object, the support field and the Mini app Behavior constructor parameters are consistent.

```javascript JavaScript
const behavior = simulate.behavior({
    /* Mini app behavior support definition section */
});
```

#### load(componentPath, tagName, options) / load(definition):

Load the custom component and return componentId. There are two ways to load the custom component, one is to pass the path of the custom component, and the other is to pass the definition object of the custom component.

**componentPath:** Custom component resides absolute path.

```javascript
const id = simulate.load('/path/to/component')
```

**tagName:** optional field, the dom node's tag name that should be used when the custom component is instantiated. If this field is not passed, it defaults to main.

```javascript
const id = simulate.load('/path/to/component', 'custom-comp')
const comp = simulate.render(id)
console.log(comp.dom.tagName)
```

**options:** optional field, some of the configuration parameters passed when loading a custom component are supported:

| Property name   | Type    | Default value                                | Description                                                                                                                                                                                                                                                      |
| :-------------- | :------ | :------------------------------------------- | :--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| compiler        | String  | official                                     | WXML compiler type, passing in official means using the official compiler, passing in simulate means using the simulated compiler implemented by JavaScript.                                                                                                     |
| compilerOptions | Object  |                                              | Compilation configuration, effective when compiler = official.                                                                                                                                                                                                   |
| rootPath        | String  | The directory where the component is located | The root path of the project, which is used to compile the template related to the component. It is required that all components depend on this directory. If it is not passed, the directory where the current component is located will be taken as its value. |
| less            | Boolean | false                                        | Whether the WXSS of the custom component needs to be compiled by less.                                                                                                                                                                                           |
| usingComponents | Object  | undefined                                    | The used custom component mapping table will overwrite the usingComponents declared by the incoming component.                                                                                                                                                   |

> 📘 Note
> 
> When using karma to test, only official compilers are supported to compile WXML files, and JavaScript simulated compilers are not supported, so even if compiler: `simulate` is configured in the simulate.load method, it will not take effect.

```javascript
// Don't pass tagName
const id1 = simulate.load('/path/to/component', {
    rootPath: 'path/to/component/dir'
})
// Pass tagName
const id2 = simulate.load('/path/to/component', 'custom-comp', {
    rootPath: 'path/to/component/dir'
})
```

**compilerOptions:** The compilation configuration passed in when using the official compiler

| Property name | Type          | Default value | Description                                                                                                    |
| :------------ | :------------ | :------------ | :------------------------------------------------------------------------------------------------------------- |
| maxBuffer     | Number        | 1024 \* 1024  | Output buffer size when compiling.                                                                             |
| wxmlList      | Array<String> |               | WXML files that need to be compiled under `rootPath`, all WXML files under `rootPath` are selected by default. |
| wxsList       | Array<String> |               | WXS files that need to be compiled under `rootPath`, all WXS files under `rootPath` are selected by default    |

**definition:** the definition object of the custom component, in addition to the fields supported by the Mini app itself, the additional supported fields are as follows:

| Property name       | Type   | Description                                                                                                                                                                                                                                                    |
| :------------------ | :----- | :------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| id                  | String | Optional field, if this field is passed, it indicates that it is registered as a global component, and other components can be used directly in the template without introducing it in `usingComponents`.                                                      |
| tagName             | String | Optional field, specify the `tagName` of the DOM node corresponding to the component, and take the definition in `usingComponents` or the id of the component itself by default.                                                                               |
| template            | String | Component template, that is, the WXML content corresponding to the component.                                                                                                                                                                                  |
| usingComponents     | Object | The used custom component mapping table, when descendant components are processed `usingComponents`, they will look for components with the same name from this table for overlay processing, and it is supported to pass in the overlay path or component id. |
| behaviors           | Array  | Usage of behavior is similar to Mini App.                                                                                                                                                                                                                      |
| options             | Object | Configuration object, supporting custom components of Mini Apps All fields supported by options definition section.                                                                                                                                            |
| options.classPrefix | String | The private prefix of the component style, the default is an empty string, that is, there is no prefix.                                                                                                                                                        |

```javascript
simulate.load({
    id: 'view',
    tagName: 'wx-view',
    template: '<div><slot/></div>'
}); 

let childId = simulate.load({
    tagName: 'xxx',
    template: '<view><slot/></view>', // Use global components directly
});

let id = simulate.load({
    template: '<child>123</child>',
    usingComponents: {
        'child': childId, // Declare the component to use, pass in the component id
    },
    behaviors: [behavior],
    options: {
        classPrefix: 'xxx',

        /* Options supported by other Mini Program custom components, such as addGlobalClass, etc. */
    },

    /* Definition sections supported by other Mini Program custom components, such as methods definition section, etc. */
});
```

#### render(componentId, properties)

Render the custom component, return RootComponent.

**componentId:** The ID returned by calling load.

**properties:** Optional field, when creating component instances, the initial Properties object received by the component.

```javascript
const rootComp = simulate.render(id)
```

#### match(dom, html)

Check whether the content of the dom node conforms to the given html structure, usually used to compare whether the rendering result is as expected.

```javascript
const isMatch = simulate.match(dom, '<view>123</view>')
```

#### async sleep(timeout)

Delaying the execution of subsequent codes for a certain period of time is mainly used to deal with situations where it is necessary to wait for a certain period of time before performing subsequent operations. This method returns a promise object.

```javascript
await simulate.sleep(300)
```

#### scroll(component, destOffset, times, propName)

Simulate element scrolling. `destOffset` is the scroll target value; times is the number of times the scroll event is triggered, the default is 20 times; `propName` is the scrolling field, and the default is scrollTop.

> 📘 Note
> 
> Times are invalid in the real browser environment, and the number of times the specific scroll event is triggered depends on the browser's implementation.

```javascript
simulate.scroll(component, 100, 15)
```

#### Class: Component

**Properties:**

| Property name | Type   | Description                                                                                          |
| :------------ | :----- | :--------------------------------------------------------------------------------------------------- |
| dom           | Object | The DOM node corresponding to the component instance.                                                |
| data          | Object | The data object corresponding to the component instance.                                             |
| instance      | Object | Through this field you can access the definition segments such as methods of the component instance. |

**Methods:**

**querySelector(selector)**

Get the first node matching the given matching string, return Component instance.

> 📘 Note
> 
> Supports selector and selectComponent interface of Mini App custom components.

```javascript
const childComp = comp.querySelector('#a')
```

**querySelectorAll(selector)**

Get all nodes that match the given matching string, and return a list of Component instances.

> 📘 Note
> 
> Supports selector and selectAllComponents interface of Mini app custom components

```javascript
const childComps = comp.querySelectorAll('.a')
```

**setData(data, callback)**

Call the setData method of the component instance.

```javascript
comp.setData({ text: 'a' }, () => {})
```

**dispatchEvent(eventName, options)**

Used to simulate triggering events on the component instance node.

```javascript
// Trigger events on nodes in the component tree
comp.dispatchEvent('touchstart', {
  touches: [{ x: 0, y: 0 }],
  changedTouches: [{ x: 0, y: 0 }],
})

// Trigger custom events for nodes in the component tree
comp.dispatchEvent('customevent', {
  touches: [{ x: 0, y: 0 }],
  changedTouches: [{ x: 0, y: 0 }],
  /* options supported by other CustomEvent constructors */
})
```

**addEventListener(eventName, handler, useCapture)**

Events triggered by external listening components.

```javascript
comp.addEventListener('customevent', evt => {
    console.log(evt)
})
```

**removeEventListener(eventName, handler, useCapture)**

Used to externally unlisten for events triggered by components.

```javascript
const handler = evt => {
    console.log(evt)
    comp.removeEventListener('customevent', handler)
}
comp.addEventListener('customevent', handler)
```

**triggerLifeTime(lifeTime, args)**

Triggers a lifecycle hook for a component instance.

```javascript
comp.triggerLifeTime('moved', {test: 'xxx'})
```

**triggerPageLifeTime(lifeTime, args)**

Triggers a lifecycle hook for the page configured in the component instance.

```javascript
comp.triggerPageLifeTime('show', {test: 'xxx'})
```

**toJSON()**

Generate a JSON tree from the node tree under the node component.

```javascript
comp.toJSON()
```

#### Class: RootComponent

Root component, inherited from Component. That is to say, all attributes/interfaces supported by Component are supported by RootComponent.

**Methods:**

**attach**

Mount the root component instance on the passed dom node.

```javascript
const parent = document.createElement('div')
rootComp.attach(parent)
```

**detach**

Remove the root component instance from the parent dom node.

```javascript
rootComp.detach()
```

### Extras

#### Class prefixing

In order to achieve an effect similar to web components in the Mini App, the class in the custom component will be prefixed to achieve style isolation. To support this effect, pass in the `tagName` parameter when calling the load interface, so that `tagName` will be used as the class prefix when rendering the custom component. The default `tagName` is main, that is, the prefix is main.

Suppose the template of the custom component comp is:

```xml
<view class="abc">123</view>
```

```javascript
simulate.load('/comp') // The rendered result is <comp><wx-view class="main--abc">123</wx-view></comp>
simulate.load('/comp', 'custom-comp') // The rendered result is <comp><wx-view class="custom-comp--abc">123</wx-view></comp 
```

It should be noted that when other custom components are referenced in usingComponents in a custom component, tagName will be declared by default, so in this case, class prefixing will be performed:

```json
{
     "component": true,
     "usingComponents": {
         "other-comp": "./other"
     }
}
```

The other component here will use other-comp as the `tagName` by default when it is rendered, and the class in the other component will be prefixed and prefixed with other-comp.

#### dom interface simulation

Because building and rendering a custom component tree needs to call the DOM interface, it is necessary to simulate the DOM interface on the node side. If you are using mocha or some other test framework that does not provide DOM simulation function, a better solution is to use [jsdom ](https://www.npmjs.com/package/jsdom)library for mocking. If you are using a testing framework such as jest that has a built-in DOM simulation function, you can use it directly.

> 📘 Note
> 
> It is recommended to use jest to use with this toolset. jest has integrated `jsdom` internally. By configuring the value of the `testEnvironment` field as `jsdom`, test cases can be executed in a browser-like environment.

#### Custom component path

Because there is no concept of the Mini app root path in this test environment, the rootPath parameter in the load method is used as the root path for calculation, such as the usingComponents field in the following example:

```json
{
     "component": true,
     "usingComponents": {
         "other-comp": "/components/other"
     }
}
```

With this absolute path writing method, it will start looking for the corresponding component from the root path we provide; but with relative path writing method, no processing is required:

```json
{
     "component": true,
     "usingComponents": {
         "other-comp": "./other"
     }
}
```

#### wx object

A wx object will be injected into the Mini app running environment, which provides various interfaces for development and use. However, this test environment runs on nodejs, and there is no underlying implementation of these interfaces, so developers simulate the interfaces they will use when writing test cases, for example:

```javascript
const simulate = require('miniprogram-simulate');

test('test some', () => {
     wx.xxx = function() {
         // do something
     }

     // various test codes
})
```

The data that needs to be returned by the interface can also be drawn up by the developer to facilitate testing of various situations.

#### Built-in components

Officially provided view, image, etc. are all built-in components. Currently, the built-in components provided in this test environment are only used for ordinary rendering and have not implemented any functions. If these built-in components do not meet your needs, you can rewrite the built-in components yourself. Override built-in components provided in this test environment, for example:

```javascript
simulate.load({
     id: 'view',
     tagName: 'wx-view',
     template: '<div class-"wx-view"><slot/></div>',
})
```

This overrides the view built-in provided in this test environment.
