---
title: "Scroll"
slug: "scroll"
excerpt: "Scrolling related APIs."
hidden: false
metadata: 
  image: []
  robots: "index"
createdAt: "Tue May 02 2023 10:48:07 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Wed May 17 2023 07:05:01 GMT+0000 (Coordinated Universal Time)"
---
- pageScrollTo
- ScrollViewContext
  - ScrollViewContext.scrollIntoView
  - ScrollViewContext.scrollTo

# wx.pageScrollTo(Object object)

Scrolls the page to the target position.

# Parameters

**Object object**

| Attribute | Type     | Default | Required | Description                                                                            |
| :-------- | :------- | :------ | :------- | :------------------------------------------------------------------------------------- |
| scrollTop | Number   |         | Yes      | Target position on the page to scroll to in px.                                        |
| duration  | Number   | 300     | No       | Scroll animation duration in ms.                                                       |
| success   | Function |         | No       | Callback function for a successful API call.                                           |
| fail      | Function |         | No       | Callback function for a failed API call.                                               |
| complete  | Function |         | No       | Callback function for an API call end (executed for both successful and failed calls). |

### Sample code

```javascript JavaScript
wx.pageScrollTo({
  scrollTop: 0,
  duration: 300
})
```

# ScrollViewContext

Enhanced ScrollView instance, which can be obtained through the `NodesRef.node` method of `wx.createSelectorQuery`. It takes effect only after the `enhanced` attribute is enabled for the ScrollView component.

## Attributes

- **boolean scrollEnabled** Toggles on scroll.
- **boolean bounces** Sets the scroll boundary elasticity (for iOS only).
- **boolean showScrollbar** Sets whether to show the scroll bar.
- **boolean pagingEnabled** Toggles on paged scroll.
- **boolean fastDeceleration** Sets the scroll deceleration rate.
- **boolean decelerationDisabled** Cancels scroll inertia (for iOS only).

## Methods

- **ScrollViewContext.scrollTo(Object object)** Scrolls to the specified position.
- **ScrollViewContext.scrollIntoView(string selector)** Scrolls to the specified position.

### Sample code

```javascript JavaScript
wx.createSelectorQuery()
  .select('#scrollview')
  .node()
  .exec((res) => {
    const scrollView = res[0].node;
    scrollView.scrollEnabled = false;
  })
```

# ScrollViewContext.scrollIntoView(string selector)

Scrolls to the specified position based on the WXSS selector.

# Parameters

**string selector** Element selector.

# ScrollViewContext.scrollTo(Object object)

Scrolls to the specified position.

# Parameters

**Object object**

| Attribute | Type    | Required | Description                         |
| :-------- | :------ | :------- | :---------------------------------- |
| top       | Number  | No       | Top margin.                         |
| left      | Number  | No       | Left margin.                        |
| velocity  | Number  | No       | Initial velocity.                   |
| duration  | Number  | No       | Scroll animation duration.          |
| animated  | Boolean | No       | Whether to enable scroll animation. |
