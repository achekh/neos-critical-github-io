---
title: "Picker-view"
slug: "picker-view"
excerpt: "The wheel picker embedded in the page to display one or more set of values."
hidden: false
metadata: 
  image: []
  robots: "index"
createdAt: "Mon Apr 10 2023 09:42:38 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Mon May 22 2023 12:10:22 GMT+0000 (Coordinated Universal Time)"
layout: "default"
parent: "Form components"
grand_parent: "Components"
nav_order: 9
---
# Picker-view 
The wheel picker embedded in the page to display one or more set of values.
*** 
The picker view component can be embedded in the page. User can manipulate picker-view wheeler to select items. The picker-view-column can be place only in picker-view and other components do not display. 

| Attribute       | Type          | Description                                                                                                                                                                                                                                                      |
| :-------------- | :------------ | :--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| value           | Number array  | The numbers in the array are represented sequentially by the `picker-view-column` in `picker-view`. If the number is greater than length of the `picker-view-column`, the last item is selected.                                                                 |
| indicator-style | String        | Sets the style of the checkbox in the middle of the picker.                                                                                                                                                                                                      |
| indicator-class | String        | Sets the class name of the selection box in the middle of the picker.                                                                                                                                                                                            |
| mask-style      | String        | Layer style.                                                                                                                                                                                                                                                     |
| mask-class      | String        | Layer class.                                                                                                                                                                                                                                                     |
| bindchange      | Event Handler | Triggers the change event when scrolling the selection, the value of the wheel picker changes: event. `event.detail = {value}`. Here, `value` is an array representing the number of items selected by `picker-view-column` in `picker-view`. It starts from 0). |
| bindpickstart   | Event Handler | Trigger event when scroll selection starts.                                                                                                                                                                                                                      |
| bindpickend     | Event Handler | Trigger event when scroll selection ends.                                                                                                                                                                                                                        |
| aria-label      | String        | Accessibility, which is the additional description of the element.                                                                                                                                                                                               |

> 📘 Notes
> 
> - Only the <picker-view-column> component can be nested inside <picker-view>, other components will not be displayed.
