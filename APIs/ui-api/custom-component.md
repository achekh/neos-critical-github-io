---
title: "Custom Component"
slug: "custom-component"
excerpt: "This API delays a part of the operation until the next time slice."
hidden: false
metadata: 
  image: []
  robots: "index"
createdAt: "Wed Apr 19 2023 07:10:04 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Wed May 17 2023 07:12:57 GMT+0000 (Coordinated Universal Time)"
layout: "default"
parent: "UI"
grand_parent: "APIs"
---
# Custom Component 
*** 
# nextTick

Delays a part of the operation until the next time slice. (This API is similar to `setTimeout`).

# Parameters

**function callback**

## Description

APIs such as `setData` and `triggerEvent` in custom components are sync operations. When they are called continuously, they are all executed in a sync process. Therefore, improper logic may lead to errors.

For example, when the `setData` API of the parent component triggers the `triggerEvent `API of the child component, this will cause the parent component to perform `setData` again. During this period of time, if the child component is unloaded through the `wx:if` statement, strange errors may occur. Therefore, for logics that don't need to be completed in a sync process, this API can be called to delay the execution until the next time slice.

### Sample code

```javascript
// JavaScript
Component({
  doSth() {
    this.setData({ number: 1 }) // Execute directly in the current sync process
   
    wx.nextTick(() => {
    	this.setData({ number: 3 }) // Execute in the next time slice after the current sync process ends
    })
    
    this.setData({ number: 2 }) // Execute directly in the current sync process
  }
})
```
