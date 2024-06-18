---
title: "Compatibility with Older Versions"
slug: "compatibility-with-older-versions-copy"
excerpt: "This section explains the compatibility of new mini programs with the older versions of the mini app."
hidden: true
metadata: 
  image: []
  robots: "index"
createdAt: "Tue May 09 2023 07:15:25 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Thu May 11 2023 08:55:46 GMT+0000 (Coordinated Universal Time)"
layout: "default"
parent: "Overview"
grand_parent: "Guide"
---
# Compatibility with Older Versions 
*** 
# Compatibility

The functions of the Mini Program are constantly increasing, but the old version of the WeChat client does not support new features, so it needs to be compatible when using these new capabilities.

Developers can make lower version compatibility in the following ways:

## 1. Version Comparison

Versions of the Mini app and Mini Program base library are expressed in the format of Major.Minor.Patch (major version number.minor version number.patch version number).

In the documentation, the minimum base library versions are specified for the features described in component, API, and other pages.

In a Mini Program, developers can call [wx.getSystemInfo](<>) or [wx.getSystemInfoSync](<>) to get the version of the base library run by the Mini Program. The version comparison method is used to run a lower version for compatibility purposes.

Version comparison can be used in any circumstance. In some cases, you can also use the methods discussed below.

> 📘 Note
> 
> Do not compare versions by directly comparing the strings.

See the sample code below:

```Text
// code
function compareVersion(v1, v2) {
  v1 = v1.split('.')
  v2 = v2.split('.')
  const len = Math.max(v1.length, v2.length)

  while (v1.length < len) {
    v1.push('0')
  }
  while (v2.length < len) {
    v2.push('0')
  }

  for (let i = 0; i < len; i++) {
    const num1 = parseInt(v1[i])
    const num2 = parseInt(v2[i])

    if (num1 > num2) {
      return 1
    } else if (num1 < num2) {
      return -1
    }
  }

  return 0
}

compareVersion('1.11.0', '1.9.9') // 1
```

```Text
// code
const version = wx.getSystemInfoSync().SDKVersion

if (compareVersion(version, '1.1.0') >= 0) {
  wx.openBluetoothAdapter()
} else {
  // If you want users to experience the Mini Program in the latest app, you can display a prompt like this:
  wx.showModal({
    title: 'Prompt',
    content: 'Your cannot use this feature due to low Weixin version. Please upgrade to the latest Weixin version and try again.'
  })
}
```

## 2. API Existence Judgment

For a new API, you can judge the existence of the API to determine if a user’s base library is supported. For example:

```Text
// code
if (wx.openBluetoothAdapter) {
  wx.openBluetoothAdapter()
} else {
  // If you want users to experience the Mini Program in the latest app, you can display a prompt like this:
  wx.showModal({
    title: 'Prompt',
    content: 'Your cannot use this feature due to low Weixin version. Please upgrade to the latest Weixin version and try again.'
  })
}
```

## 3. wx.canIUse

In addition to a direct judgment by the version number, you can also use wx.canIUse to determine if a feature can be used directly under the current base library version. For example:

### API parameters and return values

When API parameters and return values contain a new parameter, you can determine compatibility using the following code.

```Text
// code
wx.showModal({
  success: function(res) {
    if (wx.canIUse('showModal.success.cancel')) {
      console.log(res.cancel)
    }
  }
})
```

### Components

New components or properties cannot be processed by older versions, and no error is reported. In special cases, you can downgrade components for compatibility with older versions.

```Text
// code
Page({
  data: {
    canIUse: wx.canIUse('cover-view')
  }
})
```

```Text
// code
<video controls="{{!canIUse}}">
  <cover-view wx:if="{{canIUse}}">play</cover-view>
</video>
```

> canIUse data files are updated along with the base library. However, some files may not be updated due to new features in the new version, we recommend developers test the new version in advance.

## Setting Minimum Base Library Version

> Supported in Weixin 6.5.8 for iOS/Weixin 6.5.7 for Andriod and later

To easily solve the incompatibility of older base library versions with new Mini Program features, developers can set minimum base library version requirements.

Developers can log in to the Mini Program admin console and go to **Settings > Basic Settings** > **Set Minimum Base Library Version**. Before configuration, developers should look at the proportion of different base library versions used by users who have accessed the Mini Program in the past 30 days.

![](https://files.readme.io/c745654-small-7000a7e-42.translated.jpg)

After the minimum version is set, if a user's base library version is lower than the set value, the user will not be able to access the Mini Program and will be prompted to update the Mini app.

![](https://files.readme.io/37e7a3f-small-f8b1723-43.translated.jpg)
