---
title: "User Information"
slug: "user-information"
excerpt: "This section explains the concept of Mini Program login in the application."
hidden: true
metadata: 
  image: []
  robots: "index"
createdAt: "Mon May 08 2023 09:21:01 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Mon May 29 2023 07:30:00 GMT+0000 (Coordinated Universal Time)"
---
# Mini Program Login

Mini Programs can easily obtain the user identity identification provided by WeChat through the login ability provided by WeChat official, and quickly establish a user system within the Mini Program.

![](https://files.readme.io/8fbdfbe-23.jpg)

## Description:

1. Call wx.login() to get the temporary login credential code and send it back to the developer server.
2. Call the auth.code2Session interface in exchange for the unique user identification OpenID, the unique identity UnionID of the user under the WeChat open platform account (if the current Mini Program has been bound to the WeChat open platform account), and the session key session_key.

After that, the developer server can generate a custom login state based on the user identity, which is used to identify the user's identity during front-end and back-end interactions in subsequent business logic

> 📘 Notes
> 
> 1. Session key session_key is the key that cryptographically signs user data. In order to apply its own data security, the developer server should not send the session key to the Mini Program, nor should it provide this key externally.
> 2. The temporary login credentials code can only be used once.

# UnionID Mechanism

# About UnionID Mechanism

If the developer has multiple mobile applications, website applications, and public accounts (including Mini Programs), the UnionID can be used to distinguish the uniqueness of the user, because as long as it is a mobile application, website application, and public account (including Mini Program) under the same Open Platform account, the user's UnionID is unique. In other words, UnionID is the same for the same user for different applications under the same open platform.

## UnionID Retrieval Path

For Mini Programs bound to a developer account, you can obtain the UnionID through the following methods:

1. Call the API wx.getUserInfo, and retrieve UnionID from the decrypted data. Note that this API requires authorization from the user. The developer is advised to deal with authorization rejections appropriately.
2. If the Official Account of the same entity exists under the developer account, and the user has already followed that Official Account, the developer can directly retrieve the user's UnionID through wx.login + code2Session without user re-authorization.
3. If the Official Account or mobile app of the same entity exists under the developer account, and the user has already authorized to log in to that Official Account or mobile app, the developer can directly retrieve the user's UnionID through wx.login + code2Session without user re-authorization.
4. After the user completes the payment in the Mini Program (Mini Game not supported temporarily), the developer can directly retrieve the user's UnionID through getPaidUnionId without user re-authorization. Note: This API is only valid within 5 minutes after the user's payment is completed. The developer is advised to deal with it appropriately.
5. When the Mini Program end calls the cloud function, if the Official Account of the same entity exists under the developer account, and the user has already followed that Official Account, the UnionID can be retrieved in the cloud function through Cloud.getWXContext.
6. When the Mini Program end calls the cloud function, if the Official Account or mobile apps of the same entity exist under the developer account, and the user has already authorized login to that Official Account or mobile app, the UnionID can be retrieved in the cloud function through Cloud.getWXContext.

# Authorization

Some of the APIs need users’ authorization before they can be called. We have divided these APIs into multiple `scope` according to the scope of usage. The users can select `scope` to authorize. After a `scope` is authorized, all of its APIs can be used directly.

When such an API is called:

- If the user has not accepted or rejected this authorization, a pop-up window will appear to ask the user if he/she wants to accept. The API can be called only after the user clicks to accept;
- If the user has accepted authorization, the API can be called directly;
- If the user has rejected authorization, no pop-up appears. Instead, API fail callback will be accessed directly. **Developers should make the scenario compatible where the user has rejected to authorization**.

## Obtain User Authorization Settings

The developer can use [wx.getSetting](<>) to get the user's current authorization state.

## Go to Settings

The user can control the authorization state of the Mini Program in Mini Program Settings by clicking **About** in the upper right and then **Settings** in the upper right.

The developer can call wx.openSetting to open Settings, and guide the user to enable authorization.

## Initiate the Authorization Request in Advance

The developer can use[ wx.authorize](<>) to initiate the authorization request to the user in advance before calling the API to authorize.

## Scope List

| scope                  | Corresponding APIs                                   | Description         |
| :--------------------- | :--------------------------------------------------- | :------------------ |
| scope.userInfo         | wx.getUserInfo                                       | User information    |
| scope.userLocation     | wx.getLocation, wx.chooseLocation                    | Geographic location |
| scope.address          | wx.chooseAddress                                     | Postal address      |
| scope.invoiceTitle     | wx.chooseInvoiceTitle                                | Invoice title       |
| scope.invoice          | wx.chooseInvoice                                     | Gets invoice        |
| scope.werun            | wx.getWeRunData                                      | WeRun step counts   |
| scope.record           | wx.startRecord                                       | Recording feature   |
| scope.writePhotosAlbum | wx.saveImageToPhotosAlbum, wx.saveVideoToPhotosAlbum | Saves to album      |
| scope.camera           | camera Component                                     | Camera              |

## Period of Validity

Once the user explicitly agrees or rejects authorization, his/her authorization relationship will be recorded in the backend, until the user deletes the Mini Program

## Best Practices

Initiate an authorization request to the user only when the authorization API is needed, and clearly explain the reason why you want to use it in the authorization request.

> 📘 Notes
> 
> 1. wx.authorize({scope: "scope.userInfo"}) will not pop up the authorization window. Use <button open-type="getUserInfo"/>
> 2. When scope.userLocation authorization is needed, it is necessary to configure a usage description for geographical location.

# Open Data Verification and Decryption

# Getting Open Data from Server

Open data provided by Weixin can be fetched by Mini Programs via various client APIs. While developer server can also get such data by following the methods below:

- [Method 1](<>): The developer verifies and decrypts open data in the backend
- [Method 2](<>): The open data is obtained directly via Cloud Call (Cloud Base)

## Method 1: The developer verifies, and decrypts open data in the backend

The Mini app will sign and encrypt open data. After receiving the open data, the developer can verify the signature of such data and decrypt it in the backend, to ensure that they have not been tampered with.

![](https://files.readme.io/01eb527-25.jpg)

## Data signature verification

To ensure the security of the user data returned via the open API, the plaintext data will be signed in Weixin. The developer can verify the signature of the data package as per the business requirements to ensure data integrity.

1. When an API (such as [wx.getUserInfo](<>)) is called to get data, it will return both rawData and signature, where signature = sha1 (rawData + session_key).
2. The developer sends signature and rawData to the developer server for verification. The server uses the user's session_key to calculate signature2 with the same algorithm, and compares signature and signature2 to verify the data integrity.

**For example, to verify the data for wx.getUserInfo:**

rawData returned by the API:

```Text code
{
  "nickName": "Band",
  "gender": 1,
  "language": "zh_CN",
  "city": "Guangzhou",
  "province": "Guangdong",
  "country": "CN",
  "avatarUrl": "http://wx.qlogo.cn/mmopen/vi_32/1vZvI39NWFQ9XM4LtQpFrQJ1xlgZxx3w7bQxKARol6503Iuswjjn6nIGBiaycAjAtpujxyzYsrztuuICqIM5ibXQ/0"
}
```

The user's session-key:

```Text code
HyVFkGl5F5OQWJZZaNzBBg==
```

The string for signing is:

```Text code
{"nickName":"Band","gender":1,"language":"zh_CN","city":"Guangzhou","province":"Guangdong","country":"CN","avatarUrl":"http://wx.qlogo.cn/mmopen/vi_32/1vZvI39NWFQ9XM4LtQpFrQJ1xlgZxx3w7bQxKARol6503Iuswjjn6nIGBiaycAjAtpujxyzYsrztuuICqIM5ibXQ/0"}HyVFkGl5F5OQWJZZaNzBBg==
```

The result returned when data is signed using sha1:

```Text code
75e81ceda165f4ffa64f4068af58c64b8f54b88c
```

## The decryption algorithm for encrypted data

If an API involves sensitive data (such as openId and unionId in wx.getUserInfo), the plaintext content in the API will not include such data. To fetch the sensitive data, the developer needs to symmetrically decrypt the **encrypted data (encryptedData)** returned via the API. The decryption algorithm is as follows:

1. The algorithm used for symmetrical decryption is AES-128-CBC, and the data is filled using PKCS#7.
2. The target cryptogram for symmetrical decryption is Base64_Decode(encryptedData).
3. The key for symmetrical decryption: aeskey = Base64_Decode(session_key), which is 16 bytes.
4. The initialization vector of the symmetrical decryption algorithm is Base64_Decode(iv), where iv is returned by the data API.

Sample codes in multiple programming languages are provided by Weixin ((Click to download). The names of APIs used for each programming language are the same. For call methods, see examples.

In addition, to allow apps to verify the data validity, watermark will be added to sensitive data.

**watermark parameters:**

| Parameter | Type   | Description                                                                                                                                 |
| :-------- | :----- | :------------------------------------------------------------------------------------------------------------------------------------------ |
| appid     | String | The appId of the Mini Program where the sensitive data belongs to. The developer can verify if this parameter is the same as his/her appId. |
| timestamp | Int    | The timestamp when sensitive data is fetched. The developer can use it to check the timeliness of the data.                                 |

Example of watermark in the sensitive data of the wx.getUserInfo API:

```Text code
{
    "openId": "OPENID",
    "nickName": "NICKNAME",
    "gender": GENDER,
    "city": "CITY",
    "province": "PROVINCE",
    "country": "COUNTRY",
    "avatarUrl": "AVATARURL",
    "unionId": "UNIONID",
    "watermark":
    {
        "appid":"APPID",
        "timestamp":TIMESTAMP
    }
}
```

> 📘 Note
> 
> The json data obtained via decryption may include new fields according to specific requirements, and old fields remain unchanged and will not be deleted. The developer needs to reserve enough space.

## Validity of session_key

In case of signature validation failure or decryption failure due to incorrect session_key, the developer should note the following points:

1. When wx.login is called, the user's session_key may be updated, causing the old session_key to be invalid. (The refresh mechanism has the shortest cycle. If a user calls wx.login several times in a short time, not every call results in the refresh of session_key.) The developer should call wx.login only when they are clearly requested to log in again, and they should use the auth.code2Session API to update the session_key stored on the server.
2. The validity period of session_key will not be shared to developers in Weixin. We will renew session_key according to the user's behaviors to use the Mini Program. The more frequently the user uses the Mini Program, the longer will be the validity period of session_key.
3. When session_key expires, developers can re-run the login process to obtain a valid session_key. The wx.checkSession API can be used to verify the session_key, so that the Mini Program will not be logged in repeatedly.
4. When developers implement a custom login status, they can choose to use the validity period of the session_key as that of their own login status, or use a custom timeliness policy.

## Method 2: The open data is obtained directly via cloud call

If an API (such as wx.getWeRunData) involves sensitive data, the plaintext content in the API will not include such data. However, the cloudID field of the sensitive data will be included in the returned API, and data can be obtained via the cloud function, as shown below:

### 1. Get cloudID

When base library 2.7.0 and later is used, if Cloud Base is activated for the Mini Program, the `cloudID` can be obtained via the cloudID field (the same level as `encryptedData`) in return value of the open data API. `cloudID` is valid for 5 minutes.

### 2. Call cloud function

When the cloud function is called, if the value of a top-level field is CloudID constructed via wx.cloud.CloudID for the incoming data parameter, the value of such field will be replaced with the open data corresponding to the cloudID. Up to 5 CloudID can be replaced in a call.

### Example:

A call is initiated after the Mini Program obtains the `cloudID`:

```Text code
wx.cloud.callFunction({
  name: 'myFunction',
  data: {
    weRunData: wx.cloud.CloudID('xxx'), // This CloudID value will be replaced via the cloud function.
    obj: {
      shareInfo: wx.cloud.CloudID('yyy'), // The CloudID of non-top fields will not be replaced and will be displayed as the original string.
    }
  }
})
```

Example of event received in the cloud function:

```Text code
// event
{
  // The value of weRunData has been replaced with open data
  "weRunData": {
    "cloudID": "xxx",
    "data": {
      "stepInfoList": [
        {
          "step": 5000,
          "timestamp": 1554814312,
        }
      ],
      "watermark": {
        "appid": "wx1111111111",
        "timestampe": 1554815786
      }
    }
  },
  "obj": {
    // Non-top level field remains unchanged
    "shareInfo": "yyy",
  }
}
```

If `cloudID` is invalid or expires, an object with error code, error message and original cloudID will be obtained from `event`. See the example below:

```Text code
// event
{
  "weRunData": {
    "cloudID": "xxx",
    "errCode": -601006,
    "errMsg": "cloudID expired."
  },
  // ...
}
```

# Getting Mobile Number

# Acquire Mobile Numbers

Calling thewx.login API is required before acquiring the user's mobile number linked to Weixin.

As the API for acquiring the mobile number can be initiated only by a user’s trigger, click the [button]\((button) component to trigger it rather than directly calling the API.

> 📘 Note
> 
> Currently, this API is applicable to non-individual developers, and the Mini Programs which have completed verification (not including overseas entities). It should be used with caution. If a large number of user reports are recorded, or the API is used when not necessary, Weixin has the right to permanently revoke access privileges to this API of the Mini Program.

## Usage

Set the `open-type` value of the [button]\((button) component to `getPhoneNumber`, click to agree, and then you can acquire the encrypted data returned by the Weixin server via `bindgetphonenumber` event callback. On the third party server, you candecrypt and acquire the mobile number by using `session_key` and `app_id`.

## Note

During the callback, calling wx.login login may refresh the login status. In this case, the sessionKey that the server exchanges with the code is not the sessionKey that was used during encryption, causing decryption failure. We recommend developers to conduct `login` in advance, or start with login status check using `checkSession` during callback, avoiding login status refresh due to `login`.

## Code Sample

```Text code
<button open-type="getPhoneNumber" bindgetphonenumber="getPhoneNumber"></button>
```

```Text code
Page({
  getPhoneNumber (e) {
    console.log(e.detail.errMsg)
    console.log(e.detail.iv)
    console.log(e.detail.encryptedData)
  }
})
```

## Response Parameters

| Parameter     | Type   | Description                                                                                                                                                                                                                                   |
| :------------ | :----- | :-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| encryptedData | String | The complete encrypted user data, including the sensitive data. For details, see [Decryption Algorithm for Encrypted Data]\((signature#decryption algorithm for encrypted data))                                                              |
| iv            | String | The initial vector of the encryption algorithm. For details, see [Decryption Algorithm for Encrypted Data] \((signature#decryption algorithm for encrypted data))                                                                             |
| cloudID       | String | The Cloud ID corresponding to the sensitive data will be returned only after the Mini Program of the Cloud Base is enabled. The open data can be obtained directly via cloud call. For details, see the Directly Get Open Data via Cloud Call |

There are two ways to acquire sensitive data, one is to use the [Decryption Algorithm for Encrypted Data] \((open-ability/signature#decryption algorithm for encrypted data)) to decrypt encryptedData in the developer's backend; and the other is to directly get open data nby cloudID via cloud call.

The acquired open data has the following json structure:

```Text code
{
    "phoneNumber": "13580006666",
    "purePhoneNumber": "13580006666",
    "countryCode": "86",
    "watermark":
    {
        "appid":"APPID",
        "timestamp": TIMESTAMP
    }
}
```

| Parameter       | Type   | Description                                                                         |
| :-------------- | :----- | :---------------------------------------------------------------------------------- |
| phoneNumber     | String | The user's mobile number linked to Weixin (overseas numbers may have country codes) |
| purePhoneNumber | String | The mobile number without the country code                                          |
| countryCode     | String | The country code                                                                    |

# Biometric Authentication

Mini Programs provide the following biometric authentication modes via [SOTER](<>).

Currently, only fingerprint identification verification is supported. The biometric authentication modes available for your device can be queried using [wx.checkIsSupportSoterAuthentication](<>)

## Calling Process

![](https://files.readme.io/f92560a-26.png)

## Process description

1. Call wx.startSoterAuthentication to obtain resultJSON and resultJSONSignature.
2. (Optional) Signature verification. Here resultJSONSignature uses SHA256withRSA/PSS as a signature algorithm for verification. The mathematical formulas are defined as follows: bool verification results=verify (an original string used for signing, a signature string, a public key to verify the signature)
3. Weixin provides a backend API for the trusted key signature verification service. Weixin ensures the correctness and reliability of the signature verification results returned by the API, and the API has the above characteristics in the case of Android root (it will return whether the security of root can be guaranteed).

### API address:

```Text code
POST http://api.weixin.qq.com/cgi-bin/soter/verify_signature?access_token=%access_token
```

post data contents (JSON encoded):

```Text code
{"openid":"$openid", "json_string" : "$resultJSON", "json_signature" : "$resultJSONSignature" }
```

Request to return data contents (JSON encoded):

```Text JSON encoded
// Verification successful is returned
{"is_ok":true}
// Verification failed is returned
{"is_ok":false}
// API call failed
{"errcode":"xxx,"errmsg":"xxxxx"}
```
