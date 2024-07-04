---
title: "UI"
slug: "ui-api"
excerpt: "This section consists of all UI related APIs."
hidden: false
createdAt: "Tue Apr 18 2023 09:23:55 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Wed Nov 29 2023 08:24:20 GMT+0000 (Coordinated Universal Time)"
layout: "default"
parent: "APIs"
has_children: true
has_toc: false
nav_order: 5
---
# UI 
This section consists of all UI related APIs.

***

# Interaction

| Name                                                             | Feature Description           |
| :--------------------------------------------------------------- | :---------------------------- |
| [showToast](ui-api/interaction#showtoast)                           | Shows the message prompt box. |
| [showModal](ui-api/interaction#showmodal-object-object)             | Shows the modal dialog box.   |
| [showLoading](ui-api/interaction#showloading-object-object)         | Shows the loading prompt box. |
| [showActionSheet](ui-api/interaction#showactionsheet-object-object) | Shows the operation menu.     |
| [hideToast](ui-api/interaction#hidetoast-object-object)             | Hides the message prompt box. |
| [hideLoading](ui-api/interaction#hideloading-object-object)         | Hides the loading prompt box. |

# Navigation

| Name                                                                            | Feature Description                             |
| :------------------------------------------------------------------------------ | :---------------------------------------------- |
| [setNavigationBarTitle](ui-api/navigation-bar#setnavigationbartitle-object-object) | Dynamically sets the title of the current page. |
| [setNavigationBarColor](ui-api/navigation-bar#setnavigationbarcolor-object-object) | Sets the color of the page navigation bar.      |
| [hideHomeButton](ui-api/navigation-bar#hidehomebuttonobject-object)                | Hides the "Back to Home" button.                |

# Background

| Name                                                                            | Feature Description                                                  |
| :------------------------------------------------------------------------------ | :------------------------------------------------------------------- |
| [setBackgroundColor](ui-api/background#setbackgroundcolor-object-object)           | Dynamically sets the background color of the window.                 |
| [setBackgroundTextStyle](ui-api/background#wxsetbackgroundtextstyle-object-object) | Dynamically sets the style of the background font and loading image. |

# Tab Bar

| Name                                                              | Feature Description                                                                                                              |
| :---------------------------------------------------------------- | :------------------------------------------------------------------------------------------------------------------------------- |
| [showTabBar](ui-api/tab-bar#showtabbar-object-object)                | Shows the tab bar.                                                                                                               |
| [setTabBarStyle](ui-api/tab-bar#settabbarstyle-object-object)        | Dynamically sets the overall style of the tab bar.                                                                               |
| [setTabBarItem](ui-api/tab-bar#settabbaritem-object-object)          | Dynamically sets the content of a tab bar item. Starting from v2.7.0, temporary files and online files are supported for images. |
| [hideTabBar](ui-api/tab-bar#hidetabbar-object-object)                | Hides the tab bar.                                                                                                               |
| [showTabBarRedDot](ui-api/tab-bar#wxshowtabbarreddotobject-object)   | Shows the red dot in the top-right corner of an item on the tab bar.                                                             |
| [setTabBarBadge](ui-api/tab-bar#wxsettabbarbadgeobject-object)       | Adds text in the top-right corner of an item on the tab bar.                                                                     |
| [removeTabBarBadge](ui-api/tab-bar#wxremovetabbarbadgeobject-object) | Removes the text in the top-right corner of an item on the tab bar.                                                              |
| [hideTabBarRedDot](ui-api/tab-bar#wxhidetabbarreddotobject-object)   | Hides the red dot in the top-right corner of an item on the tab bar.                                                             |

# Pull-to-Refresh

| Name                                                                        | Feature Description                        |
| :-------------------------------------------------------------------------- | :----------------------------------------- |
| [stopPullDownRefresh](ui-api/pull-to-refresh#stoppulldownrefreshobject-object) | Stops pull-to-refresh on the current page. |
| [startPullDownRefresh](ui-api/pull-to-refresh#startpulldownrefresh)            | Starts pull-to-refresh.                    |

# Scroll

| Name                                                   | Feature Description                                                                                           |
| :----------------------------------------------------- | :------------------------------------------------------------------------------------------------------------ |
| [pageScrollTo](ui-api/scroll#wxpagescrolltoobject-object) | Scrolls the page to the target position. Two positioning methods are supported: selector and scroll distance. |

## ScrollViewContext

| Name                                                                                          | Feature Description                |
| :-------------------------------------------------------------------------------------------- | :--------------------------------- |
| [ScrollViewContext.scrollIntoView](ui-api/scroll#scrollviewcontextscrollintoviewstring-selector) | Scrolls to the specified position. |
| [ScrollViewContext.scrollTo](ui-api/scroll#scrollviewcontextscrolltoobject-object)               | Scrolls to the specified position  |

# Animation

| Name                                               | Feature Description            |
| :------------------------------------------------- | :----------------------------- |
| [createAnimation](ui-api/animation#wxcreateanimation) | Creates an animation instance. |

## Animation

| Name                                                                                         | Feature Description                                |
| :------------------------------------------------------------------------------------------- | :------------------------------------------------- |
| [Animation.backgroundColor](ui-api/animation#animationbackgroundcolorstring-value)              | Sets the background color.                         |
| [Animation.bottom](ui-api/animation#animationbottomnumberstring-value)                          | Sets the `bottom` value.                           |
| [Animation.export](ui-api/animation#array-animationexport)                                      | Exports the animation queue.                       |
| [Animation.height](ui-api/animation#animationheightnumberstring-value)                          | Sets the height.                                   |
| [Animation.left](ui-api/animation#animationleftnumberstring-value)                              | Sets the `left` value.                             |
| [Animation.matrix](ui-api/animation#animationmatrix)                                            | Same as transform-function matrix.                 |
| [Animation.matrix3d](ui-api/animation#animationmatrix3d)                                        | Same as transform-function matrix3d.               |
| [Animation.opacity](ui-api/animation#animationopacitynumber-value)                              | Sets the opacity.                                  |
| [Animation.right](ui-api/animation#animationrightnumberstring-value)                            | Sets the `right` value.                            |
| [Animation.rotate](ui-api/animation#animationrotatenumber-angle)                                | Rotates clockwise from the origin by an angle.     |
| [Animation.rotate3d](ui-api/animation#animationrotate3dnumber-x-number-y-number-z-number-angle) | Rotates clockwise from the fixed axis by an angle. |
| [Animation.rotateX](ui-api/animation#animationrotatexnumber-angle)                              | Rotates clockwise from the X-axis by an angle.     |
| [Animation.rotateY](ui-api/animation#animationrotateynumber-angle)                              | Rotates clockwise from the Y-axis by an angle.     |
| [Animation.rotateZ](ui-api/animation#animationrotateznumber-angle)                              | Rotates clockwise from the Z-axis by an angle.     |
| [Animation.scale](ui-api/animation#animationscalenumber-sx-number-sy)                           | Performs zooming.                                  |
| [Animation.scale3d](ui-api/animationscale3dnumber-sx-number-sy-number-sz)                       | Performs zooming.                                  |
| [Animation.scaleX](ui-api/animation#animationscalexnumber-scale)                                | Zooms the X-axis.                                  |
| [Animation.scaleY](ui-api/animation#animationscaleynumber-scale)                                | Zooms the Y-axis.                                  |
| [Animation.scaleZ](ui-api/animation#animationscaleznumber-scale)                                | Zooms the Z-axis.                                  |
| [Animation.skew](ui-api/animation#animationskewnumber-ax-number-ay)                             | Tilts X/Y-axis coordinates.                        |
| [Animation.skewX](ui-api/animation#animationskewxnumber-angle)                                  | Tilts the X-axis coordinate.                       |
| [Animation.skewY](ui-api/animation#animationskewynumber-angle)                                  | Tilts the Y-axis coordinate.                       |
| [Animation.step](ui-api/animation#animationstepobject-object)                                   | End of the set of animations.                      |
| [Animation.top](ui-api/animation#animationtopnumberstring-value)                                | Sets the `top` value.                              |
| [Animation.translate](ui-api/animation#animationtranslatenumber-tx-number-ty)                   | Performs translation.                              |
| [Animation.translate3d](ui-api/animation#animationtranslate3dnumber-tx-number-ty-number-tz)     | Translates X, Y, and Z-axes.                       |
| [Animation.translateX](ui-api/animation#animationtranslatexnumber-translation)                  | Translates the X-axis.                             |
| [Animation.translateY](ui-api/animation#animationtranslateynumber-translation)                  | Translates the Y-axis.                             |
| [Animation.translateZ](ui-api/animation#animationtranslateznumber-translation)                  | Translates the Z-axis.                             |
| [Animation.width](ui-api/animation#animationwidthnumberstring-value)                            | Sets the width.                                    |

# Custom component

| Name                                      | Feature Description                                       |
| :---------------------------------------- | :-------------------------------------------------------- |
| [nextTick](ui-api/custom-component#nexttick) | Delays a part of the operation until the next time slice. |

# Menu

| Name                                                                                 | Feature Description                                                                               |
| :----------------------------------------------------------------------------------- | :------------------------------------------------------------------------------------------------ |
| [getMenuButtonBoundingClientRect](ui-api/menu#object-wxgetmenubuttonboundingclientrect) | Gets the layout position information of the menu button (capsule button in the top-right corner). |

# Window

| Name                                        | Feature Description                       |
| :------------------------------------------ | :---------------------------------------- |
| [onWindowResize](ui-api/window#onwindowresize) | Listens for the window size change event. |
