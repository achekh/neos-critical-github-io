---
title: "Menu"
slug: "menu"
excerpt: "Gets the layout position information of the menu button."
hidden: false
createdAt: "Wed Apr 19 2023 07:58:10 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Wed Nov 29 2023 08:39:01 GMT+0000 (Coordinated Universal Time)"
layout: "default"
parent: "UI"
grand_parent: "APIs"
---
# Menu 
*** 
- [getMenuButtonBoundingClientRect](doc:menu#object-wxgetmenubuttonboundingclientrect)

## Object wx.getMenuButtonBoundingClientRect()

Gets the layout position information of the menu button (capsule button in the top-right corner). The origin is the top-left corner of the screen.

## Returned value

**Object**

Layout position information of menu buttons.

| Attribute | Type   | Description                       |
| :-------- | :----- | :-------------------------------- |
| width     | Number | Width in px.                      |
| height    | Number | Height in px.                     |
| top       | Number | Top boundary coordinate in px.    |
| right     | Number | Right boundary coordinate in px.  |
| bottom    | Number | Bottom boundary coordinate in px. |
| left      | Number | Left boundary coordinate in px.   |
