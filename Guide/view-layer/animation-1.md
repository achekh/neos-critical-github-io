---
title: "Animation"
slug: "animation-1"
excerpt: ""
hidden: false
metadata: 
  image: []
  robots: "index"
createdAt: "Tue May 23 2023 11:19:58 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Fri Jul 14 2023 11:24:19 GMT+0000 (Coordinated Universal Time)"
layout: "default"
parent: "View Layer"
grand_parent: "Guide"
---
# Animation 
*** 
## Common ways of UI animations

In a Mini App, you can usually use [CSS gradients](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Transitions/Using_CSS_transitions) and CSS [animations](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Animations/Using_CSS_animations) to create simple UI animations.

You can also use the wx.createAnimation API to dynamically create simple animation effects.

During animation, you can use `bindtransitionend`, `bindanimationstart`, `bindanimationiteration`, and `bindanimationend` to listen for animation events.

### Event description

- transitionend

CSS gradient ends or a `wx.createAnimation` stage ends

- animationstart

CSS animation starts

- animationiteration

A CSS animation stage ends

- animationend

CSS animation ends

> 📘 Note
> 
> None of these events are bubbling events, and they need to be bound to the node where the animation actually occurs to take effect.

## Advanced animation methods

In some complex scenarios, the above animation methods may not be applicable.

WXS response events can dynamically adjust the `style` attribute of a node by responding to events via WXS. Animation effects can be achieved by continuously changing the value of the `style` attribute. Additionally, this method can also dynamically generate animations based on the user's touch events.

Animation effects can also be achieved by continuously using `setData` to change the UI. In this way, the UI can be changed arbitrarily, but it usually causes a severe delay or lag and even mini app crash. In this case, you can improve the performance by changing the page's `setData` to `setData` in a custom component. The following sample uses `setData` to implement the stopwatch animation.
