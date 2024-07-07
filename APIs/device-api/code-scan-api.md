---
title: "Code scan"
slug: "code-scan-api"
excerpt: "This section lists the Code scan related APIs."
hidden: false
metadata: 
  image: []
  robots: "index"
createdAt: "Mon Apr 24 2023 08:36:37 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Fri Jul 14 2023 11:23:08 GMT+0000 (Coordinated Universal Time)"
layout: "default"
parent: "Device"
grand_parent: "APIs"
nav_order: 13
---
# Code scan 
This section lists the Code scan related APIs.

***

# scanCode

Opens the client's code scanning UI to scan a code.

# Parameters

**Object object**

| Attribute | Type | Valid Value | Default | Required | Description |
| :-------- | :--- | :---------- | :------ | :------- | :---------- |
| onlyFromCamera | Boolean |  | false | No | Whether to allow scanning codes only from the camera 
but not the album. |
| scanType | Array | `barCode`  <br />`qrCode`  <br />`datamatrix`  <br />`pdf417` | `['barCode','qrCode']` | No | Type of the scanned code. |
| success | Function |  |  | No | Callback function for successful API call. |
| fail | Function |  |  | No | Callback function for failed API call. |
| complete | Function |  |  | No | Callback function for API call end (executed for both successful and failed calls). |

`object.success `callback function

# Parameters

**Object res**

| Attribute | Type | Valid Value | Description |
| :-------- | :--- | :---------- | :---------- |
| result | String |  | Content of the scanned code. |
| scanType | String | QR_CODE: QR code  <br />AZTEC: Barcode  <br />CODABAR: Barcode  <br />CODE_39: Barcode  <br />CODE_93: Barcode  <br />CODE_128: Barcode  <br />DATA_MATRIX: QR  <br />code  <br />EAN_8: Barcode  <br />EAN_13: Barcode  <br />ITF: Barcode  <br />MAXICODE: Barcode  <br />PDF_417: QR code  <br />RSS_14: Barcode  <br />RSS_EXPANDED: Barcode  <br />UPC_A: Barcode  <br />UPC_E: Barcode  <br />UPC_EAN_EXTENSI  <br />ON: Barcode  <br />WX_CODE: QR code  <br />CODE_25: Barcode | Type of the scanned code. |
| charSet | String |  | Character set of the scanned code. |
| path | String |  | When the scanned code is the QR code of the current Mini App, this field will be returned, and the content will be the path carried by the QR code. |
| rawData | String |  | Base64-encoded raw data. |

### Sample code

```javascript
// JavaScript
// Allow scanning codes from the camera and the album
wx.scanCode({
  success (res) {
 		 console.log(res)
  }
})
// Allow scanning codes only from the camera
wx.scanCode({
  onlyFromCamera: true,
  success (res) {
  	console.log(res)
  }
})
```
