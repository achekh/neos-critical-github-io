---
title: "Contacts"
slug: "contacts-api"
excerpt: "This section lists the contact related API details that helps in selecting a contact by opening the phone contacts."
hidden: false
metadata: 
  image: []
  robots: "index"
createdAt: "Mon Apr 24 2023 08:06:22 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Fri Jul 14 2023 11:21:33 GMT+0000 (Coordinated Universal Time)"
layout: "default"
parent: "Device"
---
# wx.chooseContact(Object object)

Opens the phone contacts to select a contact.

# Parameters

**Object object**

| Attribute | Type     | Required | Description                                                                        |
| :-------- | :------- | :------- | :--------------------------------------------------------------------------------- |
| success   | Function | No       | Callback function for successful API call                                          |
| fail      | Function | No       | Callback function for failed API call                                              |
| complete  | Function | No       | Callback function for API call end (executed for both successful and failed calls) |

`object.success` callback function

# Parameters

**Object object**

| Attribute       | Type   | Description                                                                                                                           |
| :-------------- | :----- | :------------------------------------------------------------------------------------------------------------------------------------ |
| phoneNumber     | String | Mobile number.                                                                                                                        |
| displayName     | String | Contact name.                                                                                                                         |
| phoneNumberList | String | All phone numbers of the selected contact (only contacts but not specific phone numbers can be selected on certain Android versions). |
