---
title: "Phone"
slug: "phone-api"
excerpt: "Phone calls related functionality."
hidden: false
metadata: 
  image: []
  robots: "index"
createdAt: "Mon Apr 24 2023 08:22:16 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Fri Jul 14 2023 11:22:34 GMT+0000 (Coordinated Universal Time)"
---
# makePhoneCall

Makes a phone call.

# Parameters

**Object object**

| Attribute   | Type     | Required | Description                                                                         |
| :---------- | :------- | :------- | :---------------------------------------------------------------------------------- |
| phoneNumber | String   | Yes      | The phone number to be called.                                                      |
| success     | Function | No       | Callback function for successful API call.                                          |
| fail        | Function | No       | Callback function for failed API call.                                              |
| complete    | Function | No       | Callback function for API call end (executed for both successful and failed calls). |

### Sample code

```javascript JavaScript
wx.makePhoneCall({
	phoneNumber: '1340000' // This is just an example but not a real phone number.
})
```
