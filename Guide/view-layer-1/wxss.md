---
title: "WXSS"
slug: "wxss"
excerpt: ""
hidden: false
metadata: 
  image: []
  robots: "index"
createdAt: "Tue May 23 2023 11:13:41 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Thu Jun 08 2023 10:17:58 GMT+0000 (Coordinated Universal Time)"
layout: "default"
parent: "View Layer"
grand_parent: "Guide"
---
SuperHub Style Sheets (WXSS) is a style language used to describe the style of WXML components.

WXSS determines how WXML components should be displayed.

To make it easier for frontend developers to use WXSS, WXSS has most of the features of CSS. In order to be more suitable for developing Super Hub Mini App, WXSS has been extended and modified based on CSS.

Compared with CSS, the extended features of WXSS include:

- Size unit
- Style import

> 📘 Notes
> 
> For iOS 8 and earlier, if you want to use the flexbox layout, you need to add `display: -webkit-flex;`.

## Size unit

- Responsive pixel (rpx): It is adaptive to the screen width. The specified screen width is 750 rpx. For example, on iPhone 6, the screen width is 375 px, and there are 750 physical pixels in total, then 750 rpx = 375 px = 750 physical pixels, so 1 rpx = 0.5 px = 1 physical pixel.

Device

Conversion of rpx into px (screen width/750)

Conversion of px into rpx (750/screen width)

iPhone5

1rpx = 0.42px

1px = 2.34rpx

iPhone6

1rpx = 0.5px

1px = 2rpx

iPhone6 Plus

1rpx = 0.552px

1px = 1.81rpx

**Suggestion:** Designers can use iPhone 6 as the standard for mockups when developing Super Hub Mini App.

> 📘 Notes
> 
> Some glitches are inevitable on smaller screens. Try to avoid this during development.

## Style import

Outline style sheets can be imported with the `@import` statement followed by the relative path of the outline style sheet to be imported and ending with `;`.

### Sample code:

```css
/** common.wxss **/
.small-p {
  padding:5px;
}
```

```css
/** app.wxss **/
@import "common.wxss";
.middle-p {
  padding:15px;
}
```

## Inline style

Framework components support using `style` and `class` attributes to control component styles.

- style: Static styles are uniformly written in `class`.`style` receives dynamic styles, which will be parsed at runtime. Try to avoid writing static styles into `style`; otherwise, rendering will become slower.
  ```html WXML
   <view style="color:{{color}};" />
  ```
- class: It is used to specify a style rule, and its attribute value is a collection of class selector names (style class names) in the style rule. Style class names don't need to contain `.` and are separated by space.
  ```html WXML
   <view class="normal_view" />
  ```

## Selector

Currently supported selectors include:

| Selector         | Sample           | Description                                               |
| :--------------- | :--------------- | :-------------------------------------------------------- |
| .class           | `.intro`         | Selects all components with `class` being "intro"         |
| # id             | # firstname      | Selects the components with `id` being "firstname"        |
| element          | `view`           | Selects all view components                               |
| element, element | `view, checkbox` | Selects the view and checkbox components of all documents |
| ::after          | `view::after`    | Inserts content after the view component                  |
| ::before         | `view::before`   | Inserts content before the view component                 |

## Global styles and local styles

A style defined in `app.wxss` is a global style, which applies to every page. A style defined in the `WXSS` file of a page is a local style, which applies only to the page and it overwrites the same selectors in `app.wxss`.
