---
title: "Page Configuration"
slug: "page-configuration"
excerpt: ""
hidden: false
metadata: 
  image: []
  robots: "index"
createdAt: "Mon May 15 2023 09:18:36 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Fri Jul 14 2023 10:57:32 GMT+0000 (Coordinated Universal Time)"
layout: "default"
parent: "Mini App configuration"
grand_parent: "Guide"
---
You can also use the `.json` file to configure the window display of each Mini App page.

For the page configuration, you need to set only the content of certain `window` configuration items in `app.json` , and the page configuration items will overwrite the same configuration items in the window section of `app.json`.

## Sample configuration

```json
{
  "navigationBarBackgroundColor": "#ffffff",
  "navigationBarTextStyle": "black",
  "navigationBarTitleText": "Super Hub API demo",
  "backgroundColor": "#eeeeee",
  "backgroundTextStyle": "light"
}
```

## List of page configuration items

| Attribute                    | Type     | Default  | Description                                                                                                                                                              |
| :--------------------------- | :------- | :------- | :----------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| navigationBarBackgroundColor | HexColor | # 000000 | Background color of the navigation bar, such as `#000000`.                                                                                                               |
| navigationBarTextStyle       | String   | white    | Title color of the navigation bar. Valid values: `black`, `white`.                                                                                                       |
| navigationBarTitleText       | String   |          | Title text of the navigation bar                                                                                                                                         |
| navigationStyle              | String   | default  | Style of the navigation bar. Valid values: `default` (default style), `custom` (custom navigation bar, which only retains the capsule button in the top-right corner).   |
| backgroundColor              | HexColor | # ffffff | Background color of the window                                                                                                                                           |
| backgroundTextStyle          | String   | dark     | Loading style during pull-to-refresh. Valid values: `dark`, `light`.                                                                                                     |
| backgroundColorTop           | String   | # ffffff | Background color of the top of the window, which is supported only on iOS.                                                                                               |
| backgroundColorBottom        | String   | # ffffff | Background color of the bottom of the window, which is supported only on iOS.                                                                                            |
| enablePullDownRefresh        | Boolean  | false    | Whether to enable pull-to-refresh globally. For more information, see [Page.onPullDown Refresh](doc:logic-layer-section#page).                                           |
| pageOrientation              | String   | portrait | Screen rotation settings. Valid values: auto , `portrait`, `landscape`.For more information, see [Response to Display Area Change](doc:response-to-display-area-change). |

> 📘 Note
> 
> In the `.json` file of a page, you can only set window configuration items to determine the window display of the page, so there is no need to write the `window` attribute.
