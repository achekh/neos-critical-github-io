---
title: "Component Lifecycle"
slug: "component-lifecycle"
excerpt: "This section explains the concept of component lifecycle."
hidden: false
metadata: 
  image: []
  robots: "index"
createdAt: "Tue May 02 2023 07:44:44 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Fri Jun 09 2023 09:18:56 GMT+0000 (Coordinated Universal Time)"
layout: "default"
parent: "Custom Components"
grand_parent: "Guide"
---
## Main lifecycle functions of a component

The lifecycle of a component refers to some functions of the component itself, which are automatically triggered at special time points or when some special framework events occur.

Among them, the most important ones are `created`, `attached`, and `detached`, which contain the key time points in the entire lifecycle of a component instance.

- The `created` lifecycle function is triggered when the component instance has just been created. At this point, the component data `this.data` is the data defined in the component constructor. **`setData` cannot be called yet**. Normally, this function should only be used to add some custom attributes fields to `this` of the component.
- The `attached` lifecycle function is triggered after the component is fully initialized and enters the page node tree. At this point, `this.data` has been initialized to the current value of the component. This function is very useful, and most of the initialization work can be done at this time.
- The `detached` lifecycle function is triggered after the component leaves the page node tree. When a page is exited, detached is also be triggered if the component is still in the page node tree.

## Defining a lifecycle method

Lifecycle methods can be defined directly in the first-level parameters of the component constructor.

Component lifecycle can also be declared in the `lifetimes` field (this is the recommended way and has the highest priority).

### Sample code:

```javascript
Component({
  lifetimes: {
		attached() {
      // Executed when the component instance enters the page node tree
  	},
  	detached() {
      // Executed when the component instance is removed from the page node tree
		}, 
  },
  // The following is the legacy definition method:
	attached() {
    // Executed when the component instance enters the page node tree
  },
  detached() {
    // Executed when the component instance is removed from the page node tree
	},
// ...
})
```

Lifecycle methods can also be written in behaviors without overwriting those with the same name in other behaviors. However, note that if a component directly or indirectly references the same behavior multiple times, then the lifecycle function in the behavior will be executed only once at one execution time.

All available lifecycle functions are as shown below:

| Lifecycle | Parameter      | Description                                                                        |
| :-------- | :------------- | :--------------------------------------------------------------------------------- |
| created   | None           | Executed when the component instance has just been created                         |
| attached  | None           | Executed when the component instance enters the page node tree                     |
| ready     | None           | Executed after the component layout is completed in the view layer                 |
| moved     | None           | Executed when the component instance is moved to another location in the node tree |
| detached  | None           | Executed when the component instance is removed from the page node tree            |
| error     | `Object Error` | Executed whenever a component method throws an error                               |

## Lifecycle of the page where a component is located

There are also some special lifecycle functions. They are not strongly associated with components, but need to be informed to components sometimes, so that they can be handled internally. Such a function is called "a lifecycle function of the page where a component is located" and is defined in the pageLifetimes definition section. Available lifecycle functions are as follows:

| Lifecycle | Parameter     | Description                                                                  |
| :-------- | :------------ | :--------------------------------------------------------------------------- |
| show      | None          | Executed when the page where the component is located is shown               |
| hide      | None          | Executed when the page where the component is located is hidden              |
| resize    | `Object Size` | Executed when the size of the page where the component is located is changed |

### Sample code:

```javascript
Component({
  pageLifetimes: {
		show() {
      // The page is shown
		}, 
  	hide() {
      // The page is hidden
  	},
  	resize(size) {
      // The page size is changed
		} 
  }
})
```
