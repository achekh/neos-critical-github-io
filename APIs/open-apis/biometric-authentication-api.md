---
title: "Biometric authentication"
slug: "biometric-authentication-api"
excerpt: "This section displays the details of APIs related to biometric authentication."
hidden: false
metadata: 
  image: []
  robots: "index"
createdAt: "Tue May 02 2023 14:17:15 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Fri Jul 14 2023 11:19:06 GMT+0000 (Coordinated Universal Time)"
layout: "default"
parent: "Open APIs"
grand_parent: "APIs"
---
# Biometric authentication 
*** 
# startSoterAuthentication (Object object)

Starts biometric authentication.

# Parameters

**Object object**

| Attribute   | Type     | Description                                                                                                           |
| :---------- | :------- | :-------------------------------------------------------------------------------------------------------------------- |
| authContent | String   | Authentication description, i.e., the prompt content of the dialog box displayed on the UI during the authentication. |
| success     | Function | Callback function for successful API call.                                                                            |
| fail        | Function | Callback function for failed API call.                                                                                |
| complete    | Function | Callback function for API call end (executed for both successful and failed calls).                                   |

### Sample code

```javascript
// JavaScript
wx.startSoterAuthentication({
  authContent: 'biometric authentication unlock',
  success() {
  	// Authentication succeeded
  }
})
```

# checkIsSupportSoterAuthentication(Object object)

Verifies whether the device supports biometric authentication, call back 'success' if it supports it, and call back 'fail' if it does not support it.

# Parameters

**Object object**

| Attribute | Type     | Description                                                                         |
| :-------- | :------- | :---------------------------------------------------------------------------------- |
| success   | Function | Callback function for successful API call.                                          |
| fail      | Function | Callback function for failed API call.                                              |
| complete  | Function | Callback function for API call end (executed for both successful and failed calls). |

### Sample code

```javascript
// ,JavaScript
wx.checkIsSupportSoterAuthentication({
  success() {
  	// support biometric authentication
  }
})
```

# checkIsSoterEnrolledInDevice(Object object)

Verifies whether biometric information such as fingerprint is enrolled in the device.

# Parameters

**Object object**

| Attribute | Type     | Description                                                                         |
| :-------- | :------- | :---------------------------------------------------------------------------------- |
| success   | Function | Callback function for successful API call.                                          |
| fail      | Function | Callback function for failed API call.                                              |
| complete  | Function | Callback function for API call end (executed for both successful and failed calls). |

`object.success` callback function

# Parameters

**Object res**

| Attribute  | Type    | Description                      |
| :--------- | :------ | :------------------------------- |
| isEnrolled | Boolean | Whether information is enrolled. |
| errMsg     | String  | Error message.                   |

### Sample code

```javascript
// JavaScript
wx.checkIsSoterEnrolledInDevice({
  success(res) {
  	console.log(res.isEnrolled)
  }
})
```
