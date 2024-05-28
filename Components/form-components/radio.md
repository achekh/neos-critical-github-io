---
title: "Radio"
slug: "radio"
excerpt: "Radio component allows the users to select only one option from multiple options."
hidden: false
metadata: 
  image: []
  robots: "index"
createdAt: "Mon Apr 10 2023 12:23:21 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Mon May 22 2023 12:12:07 GMT+0000 (Coordinated Universal Time)"
layout: "default"
parent: "Form components"
---
Radio is used for selecting one option from multiple given options and a radio component can be placed in a [radio-group](doc:radio-group).

| Attribute  | Type    | Default Value | Required | Description                                                                                                          |
| :--------- | :------ | :------------ | :------- | :------------------------------------------------------------------------------------------------------------------- |
| value      | String  |               | No       | `<radio>` ID. When the `<radio>` is selected, the change event of `<radio-group>` will have the value of `<radio>` . |
| checked    | Boolean | false         | No       | Whether radio is selected.                                                                                           |
| disabled   | Boolean | false         | No       | Whether radio is disabled.                                                                                           |
| color      | String  | # 09BB07      | No       | Radio color, which uses the same color specifications of CSS.                                                        |
| aria-label | String  |               | No       | Accessibility, which is the additional description of the element.                                                   |
