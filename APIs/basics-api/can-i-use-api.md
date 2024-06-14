---
title: "canIUse"
slug: "can-i-use-api"
excerpt: "This API is used for checking the compatibility of features with the current version."
hidden: false
metadata: 
  image: []
  robots: "index"
createdAt: "Fri Apr 14 2023 08:26:21 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Fri Jul 14 2023 11:11:52 GMT+0000 (Coordinated Universal Time)"
layout: "default"
parent: "Basic"
grand_parent: "APIs"
---
# canIUse 
*** 
`canIUse` API determines if the Mini App APIs, callbacks, parameters, and components are available in the current version.  

# Parameters

## String schema

Call with` ${API}.${method}.${param}.${options}` or `${component}.${attribute}.${option}`

# Returned value

**Boolean:** Whether they are available on the current version.

# Parameter description

- `${API}`: API name
- `${method}`: API call method. Valid values: `return`, ` success`, `object `, `callback`.
- `${param}`: Parameter or returned value.
- `${options}`: Valid values of the parameter.
- `${component}`: Component name.
- `${attribute}`: Component attribute.
- `${option}`: Valid values of the component attribute.

### Sample code

```javascript JavaScript
wx.canIUse('openBluetoothAdapter')
wx.canIUse('getSystemInfoSync.return.screenWidth')
wx.canIUse('getSystemInfo.success.screenWidth')
wx.canIUse('showToast.object.image')
wx.canIUse('onCompassChange.callback.direction')
wx.canIUse('request.object.method.GET')
wx.canIUse('text.selectable')
```
