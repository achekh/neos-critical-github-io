---
title: "Custom API"
slug: "custom-api"
excerpt: "This section explains the different types of Custom APIs used in Mini App."
hidden: false
createdAt: "Mon Apr 24 2023 10:04:31 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Wed Nov 29 2023 18:30:02 GMT+0000 (Coordinated Universal Time)"
layout: "default"
parent: "APIs"
nav_order: 4
---
# Custom API 
This section explains the different types of Custom APIs used in Mini App.

***

| Name                                                    | Feature Description |
| :------------------------------------------------------ | :------------------ |
| [invokeNativePlugin](doc:custom-api#invokenativeplugin) | Custom API.         |

# invokeNativePlugin

The Super Hub Mini App SDK provides APIs, and some open platform APIs can be passed through to the host app for implementation, such as login and user information acquisition. Some host app APIs can be extended to keep UIs and features consistent, such as code scanning and sharing.  
Custom APIs can also be extended for implementation in the host app.

## Usage in Mini App

```javascript
// JavaScript
var opts = {
  api_name: '', // API name
  success: function(res) {},
  fail: function(res) {},
  complete: function(res) {},
  data: { // Input parameters
    name : 'kka',
    age : 22,
    data: {...}
  }
}
wx.invokeNativePlugin(opts); // Call
```

## Usage in terminal

### Android

For usage, see `Android Access`

### iOS

`TMFAppletClient` is responsible for implementing the Super Hub Mini App delegation API and monitoring status changes. The host app can  
implement corresponding APIs to implement features accordingly.

For usage, see `iOS Access`.

### Methods

**View onCreateLoadingView()**

```Text
// code
Creates a loading view. The host is allowed to present the mini app/game's brand and custom display style. If null is returned, the default
loading view will be displayed.
```

**View onCreateCapsuleView()**

```Text
// code
Creates a capsule button. The host is allowed to customize the style of the capsule button. If null is returned, the default capsule button
will be displayed.
```

**boolean onShowMenu()**

```Text
// code
Triggered when the "..." (more) button is clicked. If `onCreateCapsuleView` returns null and `onShowMenu` returns `false`, the default menu
will be displayed.
```

**void onExit()**

```Text
// code
Triggered when the "〇" (exit) button is clicked. If `onCreateCapsuleView` returns null and `onExit` returns `false`, the default operation
will be executed.
```

**boolean onAuthorize(JSONObject params, ValueCallback callback)**

```Text
// code
`wx.authorize` API implementation. If `false` is returned, a call failure will be directly notified to the wx API.
```

**boolean onOpenSetting(JSONObject params, ValueCallback callback)**

```Text
// code
`wx.openSetting` API implementation. If `false` is returned, a call failure will be directly notified to the wx API.
```

**boolean onGetSetting(JSONObject params, ValueCallback callback)**

```Text
// code
`wx.getSetting` API implementation. If `false` is returned, a call failure will be directly notified to the wx API.
```

**boolean onLogin(JSONObject params, ValueCallback callback)**

```Text
// code
`wx.login` API implementation. If `false` is returned, a call failure will be directly notified to the wx API.
```

**boolean onRefreshSession(JSONObject params, ValueCallback callback)**

```Text
// code
`wx.checkSession` API implementation. If `false` is returned, a call failure will be directly notified to the wx API.
```

**boolean onRequestPayment(JSONObject params, ValueCallback callback)**

```Text
// code
`wx.requestPayment` API implementation. If `false` is returned, a call failure will be directly notified to the wx API.
```

**boolean onGetUserInfo(JSONObject params, ValueCallback callback)**

```Text
// code
`wx.getUserInfo` API implementation. If `false` is returned, a call failure will be directly notified to the wx API.
```

```Text
// code
-(void)onGetUserInfoWithParams:(NSDictionary *)params inApp:(NSString *)appId callbackHandler:(WebAPICallbackHandler)handler {
    //TODO
    		NSDictionary* userInfo = @{
                                  @"nickname" : @"morven",
                                  @"headimgurl" :
    @"https://wx.qlogo.cn/mmopen/vi_32/Q0j4TwGTfTKav1ib8qG43xy0resTpgfeCqH00vRpHicEdk0kKMxqTMMUG1WmBuAdgB2tmCf6joGVKlGbsicelhluw/0",
                                  @"sex" : @(1),
                                  @"province" : @"Guangdong",
                                  @"city" : @"Shenzhen",
                                  @"country" : @"China"
                                  };
        NSMutableDictionary* result = [NSMutableDictionary dictionaryWithCapacity:1];
        NSMutableDictionary* userInfoDic = [NSMutableDictionary dictionaryWithCapacity:6];
        NSMutableDictionary* resultDataDic = [NSMutableDictionary dictionaryWithCapacity:1];
        [userInfoDic setValue:userInfo[@"nickname"] forKey:@"nickName"];
        [userInfoDic setValue:userInfo[@"headimgurl"] forKey:@"avatarUrl"];
        [userInfoDic setValue:userInfo[@"sex"] forKey:@"gender"];
        [userInfoDic setValue:userInfo[@"province"] forKey:@"province"];
        [userInfoDic setValue:userInfo[@"city"] forKey:@"city"];
        [userInfoDic setValue:userInfo[@"country"] forKey:@"country"];
       
				NSData *data=[NSJSONSerialization dataWithJSONObject:userInfoDic options:NSJSONWritingPrettyPrinted error:nil];
       
			  [resultDataDic setValue:[[NSString alloc]initWithData:data encoding:NSUTF8StringEncoding] forKey:@"data"];
        [result setValue:resultDataDic forKey:@"data"];
        [result setValue:@"getUserInfo:ok" forKey:@"errMsg"];
    if (handler) {
        //success
        handler(result, nil);
    }
}
```

**boolean onShareAppMessage(JSONObject params, ValueCallback callback)**

```Text
// code
`wx.shareAppMessage` API implementation. If `false` is returned, a call failure will be directly notified to the wx API.
```

**boolean onNavigateToMiniProgram(JSONObject params, ValueCallback callback)**

```Text
// code
`wx.navigateToMiniProgram` API implementation. If `false` is returned, a call failure will be directly notified to the wx API.
```

**boolean onScanCode(JSONObject params, ValueCallback callback)**

```Text
// code
`wx.scanCode` API implementation. If `false` is returned, a call failure will be directly notified to the wx API.
```

**boolean onOpenDocument(JSONObject params, ValueCallback callback)**

```Text
// code
`wx.openDocument` API implementation. If `false` is returned, a call failure will be directly notified to the wx API.
```

**boolean onOpenLocation(JSONObject params, ValueCallback callback)**

```Text
// code
`wx.openLocation` API implementation. If `false` is returned, a call failure will be directly notified to the wx API.
```

**boolean onChooseLocation(JSONObject params, ValueCallback callback)**

```Text
// code
`wx.chooseLocation` API implementation. If `false` is returned, a call failure will be directly notified to the wx API.
```

**boolean onPreviewImage(JSONObject params, ValueCallback callback)**

```Text
// code
`wx.rviewImage` API implementation. If `false` is returned, a call failure will be directly notified to the wx API.
```

**boolean onChooseImage(JSONObject params, ValueCallback callback)**

```Text
// code
`wx.chooseImage` API implementation. If `false` is returned, a call failure will be directly notified to the wx API.
```

**boolean onChooseVideo(JSONObject params, ValueCallback callback)**

```Text
// code
`wx.chooseVideo` API implementation. If `false` is returned, a call failure will be directly notified to the wx API.
```

**boolean onShowToast(JSONObject params, ValueCallback callback)**

```Text
// code
`wx.showToast` and `wx.showLoading` API implementation. If `false` is returned, the default style will be displayed.
```

**boolean onHideToast(JSONObject params, ValueCallback callback)**

```Text
// code
`wx.hideToast` and `wx.hideLoading` API implementation. If `false` is returned, the default style will be displayed.
```

**boolean onShowModal(JSONObject params, ValueCallback callback)**

```Text
// code
`wx.showModal` API implementation. If `false` is returned, the default style will be displayed.
```

**boolean onLaunchApp(JSONObject params, ValueCallback callback)**

```Text
// code
Custom `wx msLaunchApp` API implementation to notify the third-party app to start. If `false` is returned, a call failure will be directly
notified to the wx API. If `true` is returned, the client needs to implement the corresponding feature. We recommend you use async callback.
For detailed directions, see the demo code.
```

**boolean onInvokeWebAPI(String event, JSONObject params, ValueCallback callback)**

```Text
// code
Custom wx API implementation. If `false` is returned, a call failure will be directly notified to the wx API.
```

```Text
// code
- (BOOL)onInvokeWebAPIWithEvent:(NSString*)event params:(NSDictionary*)params callbackHandler:(WebAPICallbackHandler _Nullable)handler {
    NSLog(@"onInvokeWebAPIWithEvent, event:%@, params:%@", event, params);
    if (handler) {
    		handler(@{@"errMsg" : @"onInvokeWebAPIWithEvent"}, nil);
    }
    return YES;
}
```

**boolean onReportEvent(String event, Map params)**

```Text
// code
Reports an event. Supported events are as follows:
  1. Mini app start. event: MS_EVENT_LAUNCH. params key: pagePath,d;
  2. Mini app usage duration. event: MS_EVENT_USE_TIME. params key: useTime, startId, appId. `useTime` is in milliseconds; 3. Successful mini
app start. event: MS_EVENT_LAUNCH_SUCCESS. params key: appId;
  4. In-mini app page open. event: MS_EVENT_OPEN_PAGE. params key: pagePath, appId;
  5. Failed mini app start. event: MS_EVENT_LAUNCH_FAIL. params key: pagePath, reason, appId.
```
