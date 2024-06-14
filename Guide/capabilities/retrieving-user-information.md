---
title: "Retrieving user information"
slug: "retrieving-user-information"
excerpt: ""
hidden: false
metadata: 
  image: []
  robots: "index"
createdAt: "Thu May 18 2023 06:28:20 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Fri Jul 14 2023 11:24:59 GMT+0000 (Coordinated Universal Time)"
layout: "default"
parent: "Backend assisted capabilities"
grand_parent: "Guide"
---
# Retrieving user information 
*** 
### Getting the user's code from the Mini App

The first step of retrieving the user's information is to call `wx.login()` from the Mini App, you will get back a code for the user, you can exchange this code with the user's information through backend calls:

```javascript
wx.login({
  success(res) {
    console.log(res.code)
  }
})
```

> 📘 Note
> 
> Please make sure to run the Mini App on the device to get a real code, code returned from the simulator won't work.

### Exchanging the user code for an access token

Once you retrieve the user code in the first step, you can make an API call through the Mini App backend to exchange the code for an access token:

**URL:** <https://qa.neuxnet.com/neuopenapi/oauth/mini/accessToken>  
**Request method:** POST  
**Request Sample:**

```curl
curl --location --request POST
'https://qa.neuxnet.com/neuopenapi/oauth/mini/accessToken' \
--header 'Content-Type: application/json' \
--data-raw '{
"clientId": "tmfxzpo3g02unycoyl",
"code": "9d77061e-47dc-498d-8c72-ef44a53cc8c9",
"grantType": "authorization_code",
"scope": "user.info",
"timestamp": 1671009392999,
"sign":
"00d857bb9ae87de5913cf4d9a3e90108026817b6d524c1a30dc35a42b8718924"
}'
```

Request Parameters:

| Parameter | Type   | Required | Description                                                                  | Example                                                          |
| :-------- | :----- | :------- | :--------------------------------------------------------------------------- | :--------------------------------------------------------------- |
| clientId  | String | Yes      | Mini App ID                                                                  | tmfxzpo3g02unycoyl                                               |
| code      | String | Yes      | Retrieved user code through `wx.login()`                                     | 9d77061e-47dc498d-8c72-ef44a53cc8c9                              |
| grantType | String | Yes      | User info retrieval method                                                   | authorization_code                                               |
| scope     | String | Yes      | User's information scope                                                     | user.info                                                        |
| timestamp | Long   | Yes      | A millisecond timestamp, no more than 15 minutes later than the current time | 1685267592465                                                    |
| sign      | String | Yes      | Request parameters signature                                                 | 00d857bb9ae87de5913cf4d9a3e90108026817b6d524c1a30dc35a42b8718924 |

Response Result:

```json
{
  "responseHeader": {
    "status": 200,
    "msg": "OK"
  },
  "response": {
    "accessToken":
    "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzUxMiJ9.eyJpYXQiOjE2NzEwMDk1NDMsIm5iZiI6MTY3MTAwOTU0MywiZXhwIjoxNjcxNjE0MzQzLCJvcGVuSWQiOiIyMjEyZDRmMmYwYTBmNTUyOWYyYjVlYjgzMjQ2ODc5YyIsImNsaWVudElkIjoidG1meHpwbzNnMDJ1bnljb3lsIn0.pa54O9Da_W8TF4hEF7O3-UFVGWHNfMHyCJYcJKBMdcZoeAuqpktnMLPygnbsWbe_Q5MWQlYgp73i__h6-D3UBA",
    "expire": 604800,
    "tokenType": "bearer"
  }
}
```

Response Parameters:

| Parameter      | Description               | Type   |
| :------------- | :------------------------ | :----- |
| responseHeader | Holds request information | Object |
| response       | Holds response data       | Object |

responseHeader object parameters:

| Parameter | Description                    | Type |
| :-------- | :----------------------------- | :--- |
| status    | Corresponding HTTP status code | int  |
| msg       | Results message                | "OK" |

response object parameters:

| Parameter   | Description             | Type   |
| :---------- | :---------------------- | :----- |
| accessToken | OAuth token             | String |
| expire      | Token expiry in seconds | Long   |
| tokenType   | Token type              | String |

### Exchanging the access token for user's information:

Once the access token is retrieved, it can be exchanged with the user information:

**URL:** <https://qa.neuxnet.com/neuopenapi/oauth/mini/user/info?accessToken={accessToken}>  
**Request method:** POST  
**Request Sample:**

```curl
curl --location --request GET
'https://qa.neuxnet.com/neuopenapi/oauth/mini/user/info?accessToken=eyJ0eX
AiOiJKV1QiLCJhbGciOiJIUzUxMiJ9.eyJpYXQiOjE2NzEwMDk1NDMsIm5iZiI6MTY
3MTAwOTU0MywiZXhwIjoxNjcxNjE0MzQzLCJvcGVuSWQiOiIyMjEyZDRmMmYw
YTBmNTUyOWYyYjVlYjgzMjQ2ODc5YyIsImNsaWVudElkIjoidG1meHpwbzNnMD
J1bnljb3lsIn0.pa54O9Da_W8TF4hEF7O3-
UFVGWHNfMHyCJYcJKBMdcZoeAuqpktnMLPygnbsWbe_Q5MWQlYgp73i__h6-
D3UBA'
```

Response results:

```json
{
  "responseHeader": {
    "status": 200,
    "msg": "OK"
  },
  "response": {
    "openId": "2212d4f2f0a0f5529f2b5eb83246879c",
    "nickName": "MiniAppUser",
    "avatar":
    "http://static.satest.neuxnet.com/avatar/user/th_16003aab3b840f89f8d3b3cf87a84846.jpg",
    "email": null,
    "unionId": "dbc9f53ccc51c2e611b7d39e620bc315"
  }
}
```

Response Parameters:

| Parameter      | Description               | Type   |
| :------------- | :------------------------ | :----- |
| responseHeader | Holds request information | Object |
| response       | Holds response data       | Object |

responseHeader object parameters:

| Parameter | Description                    | Type |
| :-------- | :----------------------------- | :--- |
| status    | Corresponding HTTP status code | int  |
| msg       | Results message                | "OK" |

response object parameters:

| Parameter | Description                                   | Type   |
| :-------- | :-------------------------------------------- | :----- |
| openId    | User's open ID (Mini App specific)            | String |
| nickName  | Username                                      | String |
| avatar    | User's profile image address                  | String |
| email     | User's email                                  | String |
| unionId   | User's ID (generic across multiple Mini Apps) | String |
