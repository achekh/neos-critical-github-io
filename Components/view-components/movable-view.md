---
title: "Movable view"
slug: "movable-view"
excerpt: "A movable view container that can be dragged and slid across the page."
hidden: false
metadata: 
  image: []
  robots: "index"
createdAt: "Wed Apr 05 2023 07:45:16 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Fri Jul 14 2023 11:03:55 GMT+0000 (Coordinated Universal Time)"
layout: "default"
parent: "View components"
grand_parent: "Components"
---
The movable view container, which can be dragged and scrolled on the page.

| Attribute     | Type          | Default Value | Required | Description                                                                                                                                                                                                                                                                                                                           |
| :------------ | :------------ | :------------ | :------- | :------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| direction     | String        | none          | No       | `movable-view` direction. Valid values: `all`, `vertical`, `horizontal`, and `none`.                                                                                                                                                                                                                                                  |
| inertia       | Boolean       | false         | No       | Whether `movable-view `has inertia                                                                                                                                                                                                                                                                                                    |
| out-of-bounds | Boolean       | false         | No       | Whether `movable-view` can move beyond the movable area                                                                                                                                                                                                                                                                               |
| x             | Number/String |               | No       | Defines the offset in the X axis. If this value is not within the movable area, the component will move into the movable area automatically. Changing this value will trigger the animation.                                                                                                                                          |
| y             | Number/String |               | No       | Defines the offset in the Y axis. If this value is not within the movable area, the component will move into the movable area automatically. Changing this value will trigger the animation.                                                                                                                                          |
| damping       | Number        | 20            | No       | The damping coefficient, which controls the animation when the `x` or `y` value changes and the bounce-back animation. The larger this value, the faster the movement.                                                                                                                                                                |
| friction      | Number        | 2             | No       | The friction coefficient, which controls the animation for scrolling with inertia. The larger this value, the greater the friction, and the sooner the scrolling stops. The value must be greater than `0`; otherwise, the default value will be used.                                                                                |
| disabled      | Boolean       | false         | No       | Whether it is disabled or not.                                                                                                                                                                                                                                                                                                        |
| scale         | Boolean       | false         | No       | Whether two-finger pinch-to-zoom is supported. By default, the gesture takes effect in `movable- view`.                                                                                                                                                                                                                               |
| scale-min     | Number        | 0.5           | No       | Defines minimum scaling factor.                                                                                                                                                                                                                                                                                                       |
| scale-max     | Number        | 10            | No       | Defines the maximum scaling factor.                                                                                                                                                                                                                                                                                                   |
| scale-value   | Number        | 1             | No       | The zoom factor. Value range: 0.5–10.                                                                                                                                                                                                                                                                                                 |
| animation     | Boolean       | true          | No       | Whether to use animation or not.                                                                                                                                                                                                                                                                                                      |
| bindchange    | Event Handler |               | No       | The event triggered during a drag operation: event.detail = {x: x, y: y, source: source}, where `source` indicates the movement cause. Valid values: `touch` (drag); `touch-out-of-bounds` (drag   out of the movable area); `out-of-bounds `(bounce-back after drag out of the movable area); `friction` (inertia); empty (setData). |
| bindscale     | Event Handler |               | No       | The event triggered during a zoom operation: event.detail = {x: x, y: y, scale: scale}.                                                                                                                                                                                                                                               |

Besides basic events, `movable-view` provides two special events.

| Type       | Trigger Condition                                                                                         |
| :--------- | :-------------------------------------------------------------------------------------------------------- |
| htouchmove | Horizontal movement after the first touch. If this event is caught, the `touchmove` event is also caught. |
| vtouchmove | Vertical movement after the first touch. If this event is caught, the `touchmove` event is also caught.   |

> You need to set the `width` and `height` attributes for `movable-view`; otherwise, the default value of 10 px is used.
>
> By default, `movable-view` uses the absolute location, with the `top` and `left` attributes being 0 px.

> 📘 Note
> 
> `movable-view` must be in the `<movable-area/>` component as a direct child node; otherwise, it cannot move.
