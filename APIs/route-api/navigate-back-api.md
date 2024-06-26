---
title: "navigateBack (Object object)"
slug: "navigate-back-api"
excerpt: "Closes the current page and returns to a previous page."
hidden: false
metadata: 
  robots: "index"
createdAt: "Mon Apr 17 2023 12:07:30 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Fri May 19 2023 10:35:14 GMT+0000 (Coordinated Universal Time)"
layout: "default"
parent: "Route"
grand_parent: "APIs"
---
# navigateBack (Object object) 
Closes the current page and returns to a previous page.

***

# Parameters

**Object object**

| Attribute | Type     | Default | Required | Description                                                                                                     |
| :-------- | :------- | :------ | :------- | :-------------------------------------------------------------------------------------------------------------- |
| delta     | Number   | 1       | No       | The number of pages returned or return to the first page if delta is greater than the number of existing pages. |
| success   | Function |         | No       | Callback function for a successful API call.                                                                    |
| fail      | Function |         | No       | Callback function for a failed API call.                                                                        |
| complete  | Function |         | No       | Callback function for an API call end (executed for both successful and failed calls).                          |

### Sample code

```javascript
// JavaScript
// Note: When `navigateTo` is called for a redirect. Pages calling this method will be added to the stack, while pages calling the `redirectTo`
method will not. See the sample code below.
// Here is page A
wx.navigateTo({
	url: 'B?id=1'
})
// Here is page B
wx.navigateTo({
	url: 'C?id=1'
})
// Calling `navigateBack` on page C will redirect to page A.
wx.navigateBack({
	delta: 2
})
```
