---
title: "Component Event"
slug: "inter-component-communication-and-events"
excerpt: "This section explains the concept of inter-component communication and events."
hidden: false
metadata: 
  image: []
  robots: "index"
createdAt: "Tue May 02 2023 07:40:03 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Fri Jun 09 2023 09:02:28 GMT+0000 (Coordinated Universal Time)"
---
## Inter-component communication

The basic communication methods between components are as follows:

- WXML data binding: It is used by the parent component to set only JSON-compatible data for the specified attribute of the child component (functions can also be included in the data). For more information, see [Component Template and Style](doc:component-template-and-style#component-template).
- Event: It is used for the child component to pass any data to the parent component.
- If the above two methods cannot meet your needs, you can also make the parent component get the child component's instance object through the `this.selectComponent` method, so that it can directly access any data and methods of the child component.

## Listening for an event

The event system is one of the major means of communication between components. Custom components can trigger arbitrary events, and pages that reference such components can listen for these events. For the basic concepts and usage of events, see [Event](doc:wxml#event).

The method of listening for custom component events is exactly the same as that of listening for basic component events:

### Sample code:

```Text WXML
<!-- When the custom component triggers the `myevent` event, call the `onMyEvent` method. -->
<component-tag-name bindmyevent="onMyEvent" />
<!-- Or, it can be written as: -->
<component-tag-name bind:myevent="onMyEvent" />
```

```javascript
Page({
  onMyEvent(e) {
    e.detail // The `detail` object provided when the custom component triggers an event
  }
})
```

## Triggering an event

When a custom component triggers an event, you need to use the `triggerEvent` method to specify the event name, `detail` object, and event options:

```Text WXML
<!-- In the custom component -->
<button bindtap="onTap">Clicking this button will trigger the `myevent` event.</button>
```

```javascript
Component({
  properties: {},
  methods: {
    onTap() {
      const myEventDetail = {} // `detail` object, which is provided to the event listener.
      const myEventOption = {} // Options of the triggered event
      this.triggerEvent('myevent', myEventDetail, myEventOption)
} }
})
```

Options for triggered events include:

| Option       | Type    | Required | Default | Description                                                                                                                                                                                                   |
| :----------- | :------ | :------- | :------ | :------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| bubbles      | Boolean | No       | false   | Whether the event bubbles                                                                                                                                                                                     |
| composed     | Boolean | No       | false   | Whether the event can cross the boundary of the component. If this parameter is false , the event can only be triggered on the node tree of the referenced component and will not enter any other components. |
| capturePhase | Boolean | No       | false   | Whether the event has a capture phase                                                                                                                                                                         |

For the concepts of bubbling and capture phase, see [Event](doc:wxml#event).

```Text WXML
// `page.wxml` of the page
<another-component bindcustomevent="pageEventListener1">
  <my-component bindcustomevent="pageEventListener2"></my-component>
</another-component>
```

```Text WXML
// `another-component.wxml` of the component
<view bindcustomevent="anotherEventListener">
  <slot />
</view>
```

```Text WXML
// `my-component.wxml` of the component
<view bindcustomevent="myEventListener">
  <slot />
</view>
```

```javascript
// `my-component.js` of the component
Component({
  methods: {
    onTap() {
      this.triggerEvent('customevent', {}) // Only `pageEventListener2` will be triggered.
      this.triggerEvent('customevent', {}, {bubbles: true}) // `pageEventListener2` and `pageEventListener1` will be triggered in turn.
      this.triggerEvent('customevent', {}, {bubbles: true, composed: true}) // `pageEventListener2`, `anotherEventListener`, and
`pageEventListener1` will be triggered in turn.
} }
})
```
