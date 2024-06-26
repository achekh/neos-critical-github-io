---
title: "Data Listener"
slug: "data-listener"
excerpt: "This section explains the concept of Data Listener."
hidden: false
createdAt: "Tue May 02 2023 07:51:44 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Tue Nov 28 2023 10:13:10 GMT+0000 (Coordinated Universal Time)"
layout: "default"
parent: "Custom Components"
grand_parent: "Guide"
nav_order: 9
---
# Data Listener 
This section explains the concept of Data Listener.
*** 
## Defining and using a data listener

A data listener (or observer) can be used to listen for and respond to changes in any attribute or data field. Sometimes, certain operations need to be performed when certain data fields are set by `setData`. For example, `this.data.sum` is always the sum of `this.data.numberA` and `this.data.numberB`. In this case, you can use a data listener for the following implementation:

```javascript
// javascript
Component({
    attached: function() {
      this.setData({
        numberA: 1,
        numberB: 2,
			}) 
    },
    observers: {
      'numberA, numberB': function(numberA, numberB) {
        // Execute this function when `numberA` or `numberB` is set
        this.setData({
          sum: numberA + numberB
				}) 
      }
	} 
})
```

## Listener field syntax

A data listener can listen for changes in multiple attributes or internal data items. A `setData` operation triggers a listener at most once. In addition, a listener can listen for child data fields as shown in the following example:

```javascript
// javascript
Component({
    observers: {
      'some.subfield': function(subfield) {
        // Triggered when `this.data.some.subfield` is set with `setData`.
        // (In addition, this will also be triggered when `this.data.some` is set with `setData`.)
        subfield === this.data.some.subfield
      },
      'arr[12]': function(arr12) {
        // Triggered when `this.data.arr[12]` is set with `setData`.
        // (In addition, this will also be triggered when `this.data.arr` is set with `setData`.)
        arr12 === this.data.arr[12]
			}, 
    }
})
```

If you want to listen for changes in all child data fields, you can use the wildcard \*\*.

```javascript
// javascript
Component({
    observers: {
      'some.field.**': function(field) {
        // Triggered when `this.data.some.field` itself or its any child data field is set with `setData`.
        // (In addition, this will also be triggered when `this.data.some` is set with `setData`.)
        field === this.data.some.field
			}, 
    },
    attached: function() {
      // This will trigger the above listener.
      this.setData({
        'some.field': { /* ... */ }
      })
      // This will also trigger the above listener.
      this.setData({
        'some.field.xxx': { /* ... */ }
			})
      // This will still trigger the above listener.
      this.setData({
        'some': { /* ... */ }
			}) 
    }
})
```

In particular, all `setData` operations can be listened for by using only the wildcard \*\*.

```javascript
// javascript
Component({
    observers: {
      '**': function() {
        // Triggered every time `setData` is performed
			}, 
    },
}
```

## Bugs and tips

- The data listener listens for the data fields involved in `setData`. Even if the values of these fields don't change, the listener will still be triggered.
- If you use `setData` in the data listener function to set the data fields listened for, it may cause an infinite loop; therefore, you should exercise caution.
- Data listeners are more powerful and generally have better performance than attribute listeners.
