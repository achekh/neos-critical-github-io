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
---
# Interaction

| Name                                                             | Feature Description           |
| :--------------------------------------------------------------- | :---------------------------- |
| [showToast](doc:interaction#showtoast)                           | Shows the message prompt box. |
| [showModal](doc:interaction#showmodal-object-object)             | Shows the modal dialog box.   |
| [showLoading](doc:interaction#showloading-object-object)         | Shows the loading prompt box. |
| [showActionSheet](doc:interaction#showactionsheet-object-object) | Shows the operation menu.     |
| [hideToast](doc:interaction#hidetoast-object-object)             | Hides the message prompt box. |
| [hideLoading](doc:interaction#hideloading-object-object)         | Hides the loading prompt box. |

# Navigation

| Name                                                                            | Feature Description                             |
| :------------------------------------------------------------------------------ | :---------------------------------------------- |
| [setNavigationBarTitle](doc:navigation-bar#setnavigationbartitle-object-object) | Dynamically sets the title of the current page. |
| [setNavigationBarColor](doc:navigation-bar#setnavigationbarcolor-object-object) | Sets the color of the page navigation bar.      |
| [hideHomeButton](doc:navigation-bar#hidehomebuttonobject-object)                | Hides the "Back to Home" button.                |

# Background

| Name                                                                            | Feature Description                                                  |
| :------------------------------------------------------------------------------ | :------------------------------------------------------------------- |
| [setBackgroundColor](doc:background#setbackgroundcolor-object-object)           | Dynamically sets the background color of the window.                 |
| [setBackgroundTextStyle](doc:background#wxsetbackgroundtextstyle-object-object) | Dynamically sets the style of the background font and loading image. |

# Tab Bar

| Name                                                              | Feature Description                                                                                                              |
| :---------------------------------------------------------------- | :------------------------------------------------------------------------------------------------------------------------------- |
| [showTabBar](doc:tab-bar#showtabbar-object-object)                | Shows the tab bar.                                                                                                               |
| [setTabBarStyle](doc:tab-bar#settabbarstyle-object-object)        | Dynamically sets the overall style of the tab bar.                                                                               |
| [setTabBarItem](doc:tab-bar#settabbaritem-object-object)          | Dynamically sets the content of a tab bar item. Starting from v2.7.0, temporary files and online files are supported for images. |
| [hideTabBar](doc:tab-bar#hidetabbar-object-object)                | Hides the tab bar.                                                                                                               |
| [showTabBarRedDot](doc:tab-bar#wxshowtabbarreddotobject-object)   | Shows the red dot in the top-right corner of an item on the tab bar.                                                             |
| [setTabBarBadge](doc:tab-bar#wxsettabbarbadgeobject-object)       | Adds text in the top-right corner of an item on the tab bar.                                                                     |
| [removeTabBarBadge](doc:tab-bar#wxremovetabbarbadgeobject-object) | Removes the text in the top-right corner of an item on the tab bar.                                                              |
| [hideTabBarRedDot](doc:tab-bar#wxhidetabbarreddotobject-object)   | Hides the red dot in the top-right corner of an item on the tab bar.                                                             |

# Pull-to-Refresh

| Name                                                                        | Feature Description                        |
| :-------------------------------------------------------------------------- | :----------------------------------------- |
| [stopPullDownRefresh](doc:pull-to-refresh#stoppulldownrefreshobject-object) | Stops pull-to-refresh on the current page. |
| [startPullDownRefresh](doc:pull-to-refresh#startpulldownrefresh)            | Starts pull-to-refresh.                    |

# Scroll

| Name                                                   | Feature Description                                                                                           |
| :----------------------------------------------------- | :------------------------------------------------------------------------------------------------------------ |
| [pageScrollTo](doc:scroll#wxpagescrolltoobject-object) | Scrolls the page to the target position. Two positioning methods are supported: selector and scroll distance. |

## ScrollViewContext

| Name                                                                                          | Feature Description                |
| :-------------------------------------------------------------------------------------------- | :--------------------------------- |
| [ScrollViewContext.scrollIntoView](doc:scroll#scrollviewcontextscrollintoviewstring-selector) | Scrolls to the specified position. |
| [ScrollViewContext.scrollTo](doc:scroll#scrollviewcontextscrolltoobject-object)               | Scrolls to the specified position  |

# Animation

| Name                                               | Feature Description            |
| :------------------------------------------------- | :----------------------------- |
| [createAnimation](doc:animation#wxcreateanimation) | Creates an animation instance. |

## Animation

| Name                                                                                         | Feature Description                                |
| :------------------------------------------------------------------------------------------- | :------------------------------------------------- |
| [Animation.backgroundColor](doc:animation#animationbackgroundcolorstring-value)              | Sets the background color.                         |
| [Animation.bottom](doc:animation#animationbottomnumberstring-value)                          | Sets the `bottom` value.                           |
| [Animation.export](doc:animation#array-animationexport)                                      | Exports the animation queue.                       |
| [Animation.height](doc:animation#animationheightnumberstring-value)                          | Sets the height.                                   |
| [Animation.left](doc:animation#animationleftnumberstring-value)                              | Sets the `left` value.                             |
| [Animation.matrix](doc:animation#animationmatrix)                                            | Same as transform-function matrix.                 |
| [Animation.matrix3d](doc:animation#animationmatrix3d)                                        | Same as transform-function matrix3d.               |
| [Animation.opacity](doc:animation#animationopacitynumber-value)                              | Sets the opacity.                                  |
| [Animation.right](doc:animation#animationrightnumberstring-value)                            | Sets the `right` value.                            |
| [Animation.rotate](doc:animation#animationrotatenumber-angle)                                | Rotates clockwise from the origin by an angle.     |
| [Animation.rotate3d](doc:animation#animationrotate3dnumber-x-number-y-number-z-number-angle) | Rotates clockwise from the fixed axis by an angle. |
| [Animation.rotateX](doc:animation#animationrotatexnumber-angle)                              | Rotates clockwise from the X-axis by an angle.     |
| [Animation.rotateY](doc:animation#animationrotateynumber-angle)                              | Rotates clockwise from the Y-axis by an angle.     |
| [Animation.rotateZ](doc:animation#animationrotateznumber-angle)                              | Rotates clockwise from the Z-axis by an angle.     |
| [Animation.scale](doc:animation#animationscalenumber-sx-number-sy)                           | Performs zooming.                                  |
| [Animation.scale3d](doc:animationscale3dnumber-sx-number-sy-number-sz)                       | Performs zooming.                                  |
| [Animation.scaleX](doc:animation#animationscalexnumber-scale)                                | Zooms the X-axis.                                  |
| [Animation.scaleY](doc:animation#animationscaleynumber-scale)                                | Zooms the Y-axis.                                  |
| [Animation.scaleZ](doc:animation#animationscaleznumber-scale)                                | Zooms the Z-axis.                                  |
| [Animation.skew](doc:animation#animationskewnumber-ax-number-ay)                             | Tilts X/Y-axis coordinates.                        |
| [Animation.skewX](doc:animation#animationskewxnumber-angle)                                  | Tilts the X-axis coordinate.                       |
| [Animation.skewY](doc:animation#animationskewynumber-angle)                                  | Tilts the Y-axis coordinate.                       |
| [Animation.step](doc:animation#animationstepobject-object)                                   | End of the set of animations.                      |
| [Animation.top](doc:animation#animationtopnumberstring-value)                                | Sets the `top` value.                              |
| [Animation.translate](doc:animation#animationtranslatenumber-tx-number-ty)                   | Performs translation.                              |
| [Animation.translate3d](doc:animation#animationtranslate3dnumber-tx-number-ty-number-tz)     | Translates X, Y, and Z-axes.                       |
| [Animation.translateX](doc:animation#animationtranslatexnumber-translation)                  | Translates the X-axis.                             |
| [Animation.translateY](doc:animation#animationtranslateynumber-translation)                  | Translates the Y-axis.                             |
| [Animation.translateZ](doc:animation#animationtranslateznumber-translation)                  | Translates the Z-axis.                             |
| [Animation.width](doc:animation#animationwidthnumberstring-value)                            | Sets the width.                                    |

# Custom component

| Name                                      | Feature Description                                       |
| :---------------------------------------- | :-------------------------------------------------------- |
| [nextTick](doc:custom-component#nexttick) | Delays a part of the operation until the next time slice. |

# Menu

| Name                                                                                 | Feature Description                                                                               |
| :----------------------------------------------------------------------------------- | :------------------------------------------------------------------------------------------------ |
| [getMenuButtonBoundingClientRect](doc:menu#object-wxgetmenubuttonboundingclientrect) | Gets the layout position information of the menu button (capsule button in the top-right corner). |

# Window

| Name                                        | Feature Description                       |
| :------------------------------------------ | :---------------------------------------- |
| [onWindowResize](doc:window#onwindowresize) | Listens for the window size change event. |
