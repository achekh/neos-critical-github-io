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
---
# scanCode

Opens the client's code scanning UI to scan a code.

# Parameters

**Object object**

[block:parameters]
{
  "data": {
    "h-0": "Attribute",
    "h-1": "Type",
    "h-2": "Valid Value",
    "h-3": "Default",
    "h-4": "Required",
    "h-5": "Description",
    "0-0": "onlyFromCamera",
    "0-1": "Boolean",
    "0-2": "",
    "0-3": "false",
    "0-4": "No",
    "0-5": "Whether to allow scanning codes only from the camera but not the album.",
    "1-0": "scanType",
    "1-1": "Array",
    "1-2": "`barCode`  \n`qrCode`  \n`datamatrix`  \n`pdf417`",
    "1-3": "`['barCode','qrCode']`",
    "1-4": "No",
    "1-5": "Type of the scanned code.",
    "2-0": "success",
    "2-1": "Function",
    "2-2": "",
    "2-3": "",
    "2-4": "No",
    "2-5": "Callback function for successful API call.",
    "3-0": "fail",
    "3-1": "Function",
    "3-2": "",
    "3-3": "",
    "3-4": "No",
    "3-5": "Callback function for failed API call.",
    "4-0": "complete",
    "4-1": "Function",
    "4-2": "",
    "4-3": "",
    "4-4": "No",
    "4-5": "Callback function for API call end (executed for both successful and failed calls)."
  },
  "cols": 6,
  "rows": 5,
  "align": [
    "left",
    "left",
    "left",
    "left",
    "left",
    "left"
  ]
}
[/block]


`object.success `callback function

# Parameters

**Object res**

[block:parameters]
{
  "data": {
    "h-0": "Attribute",
    "h-1": "Type",
    "h-2": "Valid Value",
    "h-3": "Description",
    "0-0": "result",
    "0-1": "String",
    "0-2": "",
    "0-3": "Content of the scanned code.",
    "1-0": "scanType",
    "1-1": "String",
    "1-2": "QR_CODE: QR code  \nAZTEC: Barcode  \nCODABAR: Barcode  \nCODE_39: Barcode  \nCODE_93: Barcode  \nCODE_128: Barcode  \nDATA_MATRIX: QR  \ncode  \nEAN_8: Barcode  \nEAN_13: Barcode  \nITF: Barcode  \nMAXICODE: Barcode  \nPDF_417: QR code  \nRSS_14: Barcode  \nRSS_EXPANDED: Barcode  \nUPC_A: Barcode  \nUPC_E: Barcode  \nUPC_EAN_EXTENSI  \nON: Barcode  \nWX_CODE: QR code  \nCODE_25: Barcode",
    "1-3": "Type of the scanned code.",
    "2-0": "charSet",
    "2-1": "String",
    "2-2": "",
    "2-3": "Character set of the scanned code.",
    "3-0": "path",
    "3-1": "String",
    "3-2": "",
    "3-3": "When the scanned code is the QR code of the current Mini App, this field will be returned, and the content will be the path carried by the QR code.",
    "4-0": "rawData",
    "4-1": "String",
    "4-2": "",
    "4-3": "Base64-encoded raw data."
  },
  "cols": 4,
  "rows": 5,
  "align": [
    "left",
    "left",
    "left",
    "left"
  ]
}
[/block]


### Sample code

```javascript JavaScript
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
