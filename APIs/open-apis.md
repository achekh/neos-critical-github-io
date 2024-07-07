---
title: "Open APIs"
slug: "open-apis"
excerpt: "This section consists of list of Open APIs for the Mini App."
hidden: false
createdAt: "Fri Apr 21 2023 10:06:09 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Wed Nov 29 2023 13:24:50 GMT+0000 (Coordinated Universal Time)"
layout: "default"
parent: "APIs"
has_children: true
has_toc: false
nav_order: 11
---
# Open APIs 
This section consists of list of Open APIs for the Mini App.

***

| Name                           | Feature Description                    |
| :----------------------------- | :------------------------------------- |
| [login](open-apis/login-api#wxlogin) | Gets the login credentials` ( code )`. |

### Authorization

| Name                                           | Feature Description                                    |
| :--------------------------------------------- | :----------------------------------------------------- |
| [authorize](open-apis/authorization-api#wxauthorize) | Sends an authorization request to the user in advance. |

### Settings

| Name                                                     | Feature Description                                                            |
| :------------------------------------------------------- | :----------------------------------------------------------------------------- |
| [openSetting](open-apis/settings-api#wxopensetting)            | Calls the Mini App settings page and returns the operation result of the user. |
| [getSetting](open-apis/settings-api#wxgetsettingobject-object) | Gets the current settings of the user.                                         |
| [AuthSetting](open-apis/settings-api#authsetting)              | User authorization information.                                                |

### Biometric authentication

| Name                                                                                                                 | Feature Description                                                               |
| :------------------------------------------------------------------------------------------------------------------- | :-------------------------------------------------------------------------------- |
| [startSoterAuthentication](open-apis/biometric-authentication-api#startsoterauthentication)                                | Starts SOTER biometric authentication.                                            |
| [checkIsSupportSoterAuthentication](open-apis/biometric-authentication-api#checkissupportsoterauthenticationobject-object) | Gets the SOTER biometric authentication methods supported by the device.          |
| [checkIsSoterEnrolledInDevice](open-apis/biometric-authentication-api#checkissoterenrolledindeviceobject-object)           | Gets whether biometric information such as fingerprint is enrolled in the device. |
