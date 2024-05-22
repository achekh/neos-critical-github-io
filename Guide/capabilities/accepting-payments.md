---
title: "Accepting payments"
slug: "accepting-payments"
excerpt: ""
hidden: false
metadata: 
  image: []
  robots: "index"
createdAt: "Thu May 18 2023 11:06:51 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Fri Jul 14 2023 11:25:29 GMT+0000 (Coordinated Universal Time)"
---
In order to accept payments from your Mini App, your Mini App backend needs to integrate with the Super Hub backend to authorize the payment.

### Place a transaction order (from backend)

**URI:** <https://qa.neuxnet.com/neuopenapi/pay/transactions/trade>  
**Request method:** POST  
**Content-Type:** application/x-www-form-urlencoded  
Request Parameter:

[block:parameters]
{
  "data": {
    "h-0": "Parameter",
    "h-1": "Type",
    "h-2": "Required",
    "h-3": "Description",
    "h-4": "Remark",
    "0-0": "appid",
    "0-1": "String",
    "0-2": "Yes",
    "0-3": "Mini App ID",
    "0-4": "",
    "1-0": "merchantId",
    "1-1": "String",
    "1-2": "No",
    "1-3": "Merchant ID",
    "1-4": "If it is empty, it will be searched  \naccording to the Mini App ID first, if it is not found, it will be automatically generated according to the Mini App ID.",
    "2-0": "description",
    "2-1": "String",
    "2-2": "No",
    "2-3": "Payment description.",
    "2-4": "",
    "3-0": "outTradeNo",
    "3-1": "String",
    "3-2": "Yes",
    "3-3": "Merchant order number",
    "3-4": "The internal order number can only be numbers, uppercase and lowercase letters \\_ - and unique under the same merchant number.",
    "4-0": "timeExpire",
    "4-1": "Long",
    "4-2": "No",
    "4-3": "Transaction expiry time",
    "4-4": "Timestamp in milliseconds",
    "5-0": "notifyUrl",
    "5-1": "String",
    "5-2": "Yes",
    "5-3": "The callback URL to receive payment result notifications asynchronously.",
    "5-4": "The notification URL must be an extranet-accessible URL without parameters. The public network  Domain Name must be  \nhttps. If you are accessing through a  \nleased line, use a leased line NAT IP or a private callback Domain Name that can use http.",
    "6-0": "amount",
    "6-1": "Integer",
    "6-2": "Yes",
    "6-3": "Transaction amount",
    "6-4": "Amount in cents.",
    "7-0": "currency",
    "7-1": "String",
    "7-2": "Yes",
    "7-3": "Transaction currency",
    "7-4": "SAR: Saudi Arabia",
    "8-0": "openId",
    "8-1": "String",
    "8-2": "Yes",
    "8-3": "User open ID",
    "8-4": "Openid is the unique user ID of the Super App user under the appid (if the appid is different, the obtained openid will be different), which can beused to permanently mark a user.",
    "9-0": "sign",
    "9-1": "String",
    "9-2": "Yes",
    "9-3": "Authenticated security key",
    "9-4": "",
    "10-0": "timestamp",
    "10-1": "Long",
    "10-2": "Yes",
    "10-3": "Unix Epoch timestamp within 5 minutes of the current calling interface, unit: milliseconds",
    "10-4": ""
  },
  "cols": 5,
  "rows": 11,
  "align": [
    "left",
    "left",
    "left",
    "left",
    "left"
  ]
}
[/block]


```curl
curl --location --request POST 'https://qa.neuxnet.com/neuopenapi/pay/transactions/trade' \
--header 'Content-Type: application/x-www-form-urlencoded' \
--data-urlencode 'appid=tmf4c91kjcx9d9jb5f' \
--data-urlencode 'timestamp=1671523398805' \
--data-urlencode 'sign=6306a65711351823c885e39af0a89fb033ca62cc95e2d64e742da7bbc9346dce' \
--data-urlencode 'appId=tmf4c91kjcx9d9jb5f' \
--data-urlencode 'merchantId=' \
--data-urlencode 'description=' \
--data-urlencode 'outTradeNo=test007' \
--data-urlencode 'timeExpire=' \
--data-urlencode 'notifyUrl=https://applet.axzt.net/superpay/notify' \
--data-urlencode 'amount=100' \
--data-urlencode 'currency=SAR' \
--data-urlencode 'openId=358a2136a94a67b23631c67dfe386230'
```

Response results:

```json
{
  "responseHeader": {
    "status": 200,
    "msg": "OK"
	},
  "response": {
    "outTradeNo": "test003", // merchant order number
    "tradeNo": "cf6c814f886242ffa741a809924a9f41" // transaction number
	}
}
```

### Request the payment (from the Mini App):

```javascript
var opts = {
  api_name: 'requestPayment', // api name
  success: function(res) {},
  fail: function(res) {},
  complete: function(res) {},
  data: {
    transactionNo: 'bb4988a551ef437595256adb6306843f',
    name:'xxx', // company
    amount:'xx',// payment amount
    currency: "SAR", // monetary unit
    country:"SA",// country code
  }
}
wx.invokeNativePlugin(opts);
```

### Get transaction status (from backend)

**URI:** <https://qa.neuxnet.com/neuopenapi/pay/transactions/trade-no/{tradeNo}>  
**Request method:** GET  
**Request Parameter:**

| Parameter | Type   | Required | Description                                                                                |
| :-------- | :----- | :------- | :----------------------------------------------------------------------------------------- |
| tradeNo   | String | Yes      | transaction number                                                                         |
| sign      | String | Yes      | Request parameters signature                                                               |
| timestamp | Long   | Yes      | Unix Epoch timestamp within 5 minutes of the current calling interface, unit: milliseconds |
| appid     | String | Yes      | Mini App ID                                                                                |

Request Sample:

```curl
curl --location --request GET
'https://qa.neuxnet.com/neuopenapi/pay/transactions/tradeno/
8bf6dfaad61d4206a1726a2cfec697af?timestamp=1671523502136&sign=ea3
4627c46e44eeecf99d31e1188fb832d9d6d9ad37ff2fefe90dd0d2ea12bfa&appid=t
mf4c91kjcx9d9jb5f'
```

Response Result:

```json
{
  "responseHeader": {
    "status": 200,
    "msg": "OK"
  },
  "response": {
    "tradeNo": "cf6c814f886242ffa741a809924a9f41", // transaction number
    "appId": "tmfrha41wzp08ms3x9", // mini app id
    "merchantId": "4c39d791b37741108ff2b72684d2840b", // merchant number
    "description": "", // description
    "outTradeNo": "test003", // merchant order number
    "timeExpire": null, // expire time
    "notifyUrl": "https://applet.axzt.net/superpay/notify", // notify url
    "amount": 100, // amount
    "currency": "USD", // currency
    "openId": "358a2136a94a67b23631c67dfe386230", // user openId
    "uid": 8658707941847254,
    "notifySuccess": null, 
    "payType": null,
    "payNo": null,
    "payMethod": null, //【google pay / apple pay】
    "transactionFlow": 2,
    "transactionStatus": 1 
}
```

### Close transaction

If you no longer wish to continue with a transaction, you can close it through this API:

**URI: **<https://qa.neuxnet.com/neuopenapi/pay/transactions/trade-no/{tradeNo}/close>  
**Request method:** POST  
**Request Parameter:**

| Parameter | Type   | Required | Description                                                                                |
| :-------- | :----- | :------- | :----------------------------------------------------------------------------------------- |
| tradeNo   | String | Yes      | transaction number                                                                         |
| sign      | String | Yes      | Request parameters signature                                                               |
| timestamp | Long   | Yes      | Unix Epoch timestamp within 5 minutes of the current calling interface, unit: milliseconds |
| appid     | String | Yes      | Mini App ID                                                                                |

Request Sample:

```curl
curl --location --request POST
'https://qa.neuxnet.com/neuopenapi/pay/transactions/tradeno/
8bf6dfaad61d4206a1726a2cfec697af/close?timestamp=1671523502136&sign
=ea34627c46e44eeecf99d31e1188fb832d9d6d9ad37ff2fefe90dd0d2ea12bfa&ap
pid=tmf4c91kjcx9d9jb5f'
```

Response Result:

```json
{
  "responseHeader": {
    "status": 200,
    "msg": "OK"
  },
  "response": true
}
```
