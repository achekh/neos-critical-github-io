---
title: "NFC"
slug: "nfc"
excerpt: "This section consists of the list of all NFC APIs."
hidden: false
createdAt: "Mon Apr 24 2023 07:03:03 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Wed Nov 29 2023 17:58:29 GMT+0000 (Coordinated Universal Time)"
layout: "default"
parent: "Device"
grand_parent: "APIs"
nav_order: 2
---
# NFC 
This section consists of the list of all NFC APIs.

***

- [getNFCAdapter](nfc#nfcadapter-wxgetnfcadapter) 
- [NFCAdapter](nfc#nfcadapter)
- [IsoDep](nfc#isodep-nfcadaptergetisodep)
- [MifareClassic](nfc#mifareclassic-nfcadaptergetmifareclassic)
- [MifareUltralight](nfc#mifareultralight-nfcadaptergetmifareultralight)
- [Ndef](nfc#ndef-nfcadaptergetndef)
- [NfcA](nfc#nfca-nfcadaptergetnfca)
- [NfcB](nfc#nfcb-nfcadaptergetnfcb)
- [NfcF](nfc#nfcf-nfcadaptergetnfcf)
- [NfcV](nfc#nfcv-nfcadaptergetnfcv)

# NFCAdapter wx.getNFCAdapter()

> Support:  
> Android: Supported  
> iOS: Not supported

## Feature description

Gets the NFC instance.

## Returned value

[NFCAdapter](nfc#nfcadapter)

NFC instance

## Error codes

| Error Code | Error Message                            | Description                                                                 |
| :--------- | :--------------------------------------- | :-------------------------------------------------------------------------- |
| 13000      | The device does not support NFC.         |                                                                             |
| 13001      | The system NFC switch is not toggled on. |                                                                             |
| 13010      | An unknown error occurred.               |                                                                             |
| 13019      | user is not authorized                   | The user has not granted the permission.                                    |
| 13011      | invalid parameter                        | The parameter is invalid.                                                   |
| 13012      | parse NdefMessage failed                 | Failed to parse the parameter into `NdefMessage `.                          |
| 13021      | NFC discovery already started            | NFC scanning has been started.                                              |
| 13018      | NFC discovery has not started            | An attempt was made to stop NFC scanning when NFC scanning was not started. |
| 13022      | Tech already connected                   | The tag has been connected.                                                 |
| 13023      | Tech has not connected                   | An attempt was made to disconnect the tag when the tag was not connected.   |
| 13013      | NFC tag has not been discovered          | No NFC tags were found.                                                     |
| 13014      | invalid tech                             | The tag technology is invalid.                                              |
| 13015      | unavailable tech                         | Failed to obtain the corresponding technology from the tag.                 |
| 13024      | function not support                     | The current tag technology does not support this feature.                   |
| 13017      | system internal error                    | Relevant read/write operations failed.                                      |
| 13016      | connect fail                             | The connection failed.                                                      |

# NFCAdapter

> Support:  
> Android: Supported  
> iOS: Not supported

## Attributes

### Object tech

Tag type enumeration

| Attribute        | Type   | Description                                                                                 |
| :--------------- | :----- | :------------------------------------------------------------------------------------------ |
| ndef             | String | `Ndef` instance, which can read and write the NDEF data on NFC tags in NDEF format.         |
| nfcA             | String | `NfcA` instance, which can read and write data on tags in NFC-A (ISO 14443-3A) standard.    |
| nfcB             | String | `NfcB` instance, which can read and write data on tags in NFC-B (ISO 14443-3B) standard.    |
| isoDep           | String | `IsoDep` instance, which can read and write data on tags in ISO-DEP (ISO 14443-4) standard. |
| nfcF             | String | NfcF instance, which can read and write data on tags in NFC-F (JIS 6319-4) standard.        |
| nfcV             | String | NfcV instance, which can read and write data on tags in NFC-V (ISO 15693) standard.         |
| mifareClassic    | String | MifareClassic instance, which can read and write data on MIFARE Classic tags.               |
| mifareUltralight | String | MifareUltralight instance, which can read and write data on MIFARE Ultralight tags.         |

# Methods

[NFCAdapter.startDiscovery()](nfc#nfcadapterstartdiscoveryobject-object)  
[NFCAdapter.stopDiscovery()](nfc#nfcadapterstopdiscoveryobject-object)  
[Ndef NFCAdapter.getNdef()](nfc#ndef-nfcadaptergetndef)  
Gets the Ndef instance, which can read and write the NDEF data on NFC tags in NDEF format.

[NfcA NFCAdapter.getNfcA()](nfc#nfca-nfcadaptergetnfca)  
Gets the NfcA instance, which can read and write data on tags in NFC-A (ISO 14443-3A) standard.

[NfcB NFCAdapter.getNfcB()](nfc#nfcb-nfcadaptergetnfcb)  
431  
Gets the NfcB instance, which can read and write data on tags in NFC-B (ISO 14443-3B) standard.

[IsoDep NFCAdapter.getIsoDep()](nfc#isodep-nfcadaptergetisodep)  
Gets the IsoDep instance, which can read and write data on tags in ISO-DEP (ISO 14443-4) standard.

[NfcF NFCAdapter.getNfcF()](nfc#nfcf-nfcadaptergetnfcf)  
Gets the NfcF instance, which can read and write data on tags in NFC-F (JIS 6319-4) standard.

[NfcV NFCAdapter.getNfcV()](nfc#nfcv-nfcadaptergetnfcv)  
Gets the NfcV instance, which can read and write data on tags in NFC-V (ISO 15693) standard.

[MifareClassic NFCAdapter.getMifareClassic()](nfc#mifareclassic-nfcadaptergetmifareclassic)  
Gets the MifareClassic instance, which can read and write data on MIFARE Classic tags.

[MifareUltralight NFCAdapter.getMifareUltralight()](nfc#mifareultralight-nfcadaptergetmifareultralight)  
Gets the MifareUltralight instance, which can read and write data on MIFARE Ultralight tags.

[NFCAdapter.onDiscovered(function listener)](nfc#nfcadapterondiscoveredfunction-listener)  
Listens for NFC tags.

[NFCAdapter.offDiscovered(function listener)](nfc#nfcadapteroffdiscoveredfunction-listener)  
Unlistens for NFC tags.

# [IsoDep](nfc#isodep-nfcadaptergetisodep) NFCAdapter.getIsoDep()

## Feature description

Gets the `IsoDep` instance, which can read and write data on tags in ISO-DEP (ISO 14443-4) standard.

## Returned value

### [IsoDep](nfc#isodep-nfcadaptergetisodep)

# [MifareClassic](nfc#mifareclassic-nfcadaptergetmifareclassic) NFCAdapter.getMifareClassic()

## Feature description

Gets the `MifareClassic` instance, which can read and write data on MIFARE Classic tags.

## Returned value

### [MifareClassic](nfc#mifareclassic-nfcadaptergetmifareclassic)

# [MifareUltralight](nfc#mifareultralight-nfcadaptergetmifareultralight) NFCAdapter.getMifareUltralight()

## Feature description

Gets the `MifareUltralight` instance, which can read and write data on MIFARE Ultralight tags.

## Returned value

### [MifareUltralight](nfc#mifareultralight-nfcadaptergetmifareultralight)

# [Ndef](nfc#ndef-nfcadaptergetndef) NFCAdapter.getNdef()

## Feature description

Gets the `Ndef `instance, which can read and write the NDEF data on NFC tags in NDEF format.

## Returned value

### [Ndef](nfc#ndef-nfcadaptergetndef)

# [NfcA](nfc#nfca-nfcadaptergetnfca) NFCAdapter.getNfcA()

## Feature description

Gets the [NfcA](nfc#nfca-nfcadaptergetnfca) instance, which can read and write data on tags in NFC-A (ISO 14443-3A) standard.

## Returned value

### [NfcA](nfc#nfca-nfcadaptergetnfca)

# [NfcB](nfc#nfcb-nfcadaptergetnfcb) NFCAdapter.getNfcB()

## Feature description

Gets the `NfcB` instance, which can read and write data on tags in NFC-B (ISO 14443-3B) standard.

## Returned value

### [NfcB](nfc#nfcb-nfcadaptergetnfcb)

# [NfcF](nfc#nfcf-nfcadaptergetnfcf) NFCAdapter.getNfcF()

## Feature description

Gets the NfcF instance, which can read and write data on tags in NFC-F (JIS 6319-4) standard.

## Returned value

### [NfcF](nfc#nfcf-nfcadaptergetnfcf)

# [NfcV](nfc#nfcv-nfcadaptergetnfcv) NFCAdapter.getNfcV()

## Feature description

Gets the `NfcV` instance, which can read and write data on tags in NFC-V (ISO 15693) standard.

## Returned value

### [NfcV](nfc#nfcv-nfcadaptergetnfcv)

# NFCAdapter.offDiscovered(function listener)

## Feature description

Unlistens for NFC tags.

## Parameters

### function listener

The listener function passed in when `onDiscovered` is called. If this parameter is not passed in, all listener functions will be removed.

### Sample code

```javascript
// JavaScript
const listener = function (res) { console.log(res) }
NFCAdapter.onDiscovered(listener)
NFCAdapter.offDiscovered(listener) // You should pass in the same function object as for the listener.
```

# NFCAdapter.onDiscovered(function listener)

## Feature description

Listens for NFC tags.

## Parameters

### function listener

Listener function

### Parameters

**Object res**

| Attribute | Type  | Description                                                                                                         |
| :-------- | :---- | :------------------------------------------------------------------------------------------------------------------ |
| techs     | Array | Array of `tech` values used to match the specific standards (instances such as `NfcA` ) for processing the NFC card |
| messages  | Array | Array of `NdefMessage` values in the format of` {id: ArrayBuffer, type: ArrayBuffer, payload: ArrayBuffer}`         |

# NFCAdapter.startDiscovery(Object object)

## Feature description

# Parameters

**Object object**

| Attribute | Type     | Default | Required | Description                                                                        |
| :-------- | :------- | :------ | :------- | :--------------------------------------------------------------------------------- |
| success   | Function |         | No       | Callback function for successful API call                                          |
| fail      | Function |         | No       | Callback function for failed API call                                              |
| complete  | Function |         | No       | Callback function for API call end (executed for both successful and failed calls) |

## Error codes

| Error Code | Error Message                            | Description                                                                 |
| :--------- | :--------------------------------------- | :-------------------------------------------------------------------------- |
| 13000      | The device does not support NFC.         |                                                                             |
| 13001      | The system NFC switch is not toggled on. |                                                                             |
| 13010      | An unknown error occurred.               |                                                                             |
| 13019      | User is not authorized                   | The user has not granted the permission.                                    |
| 13011      | Invalid parameter                        | The parameter is invalid.                                                   |
| 13012      | Parse Ndef Message failed                | Failed to parse the parameter into `NdefMessage .`                          |
| 13021      | NFC discovery already started            | NFC scanning has been started.                                              |
| 13018      | NFC discovery has not started            | An attempt was made to stop NFC scanning when NFC scanning was not started. |
| 13022      | Tech already connected                   | The tag has been connected.                                                 |
| 13023      | Tech has not connected                   | An attempt was made to disconnect the tag when the tag was not connected.   |
| 13013      | NFC tag has not been discovered          | No NFC tags were found.                                                     |
| 13014      | Invalid tech                             | The tag technology is invalid.                                              |
| 13015      | Unavailable tech                         | Failed to obtain the corresponding technology from the tag.                 |
| 13024      | Function not support                     | The current tag technology does not support this feature.                   |
| 13017      | System internal error                    | Relevant read/write operations failed.                                      |
| 13016      | Connect fail                             | The connection failed.                                                      |

# NFCAdapter.stopDiscovery(Object object)

## Feature description

# Parameters

**Object object**

| Attribute | Type     | Default | Required | Description                                                                        |
| :-------- | :------- | :------ | :------- | :--------------------------------------------------------------------------------- |
| success   | Function |         | No       | Callback function for successful API call                                          |
| fail      | Function |         | No       | Callback function for failed API call                                              |
| complete  | Function |         | No       | Callback function for API call end (executed for both successful and failed calls) |

## Error codes

| Error Code | Error Message                            | Description                                                                 |
| :--------- | :--------------------------------------- | :-------------------------------------------------------------------------- |
| 13000      | The device does not support NFC.         |                                                                             |
| 13001      | The system NFC switch is not toggled on. |                                                                             |
| 13010      | An unknown error occurred.               |                                                                             |
| 13019      | User is not authorized                   | The user has not granted the permission.                                    |
| 13011      | Invalid parameter                        | The parameter is invalid.                                                   |
| 13012      | Parse Ndef Message failed                | Failed to parse the parameter into `NdefMessage .`                          |
| 13021      | NFC discovery already started            | NFC scanning has been started.                                              |
| 13018      | NFC discovery has not started            | An attempt was made to stop NFC scanning when NFC scanning was not started. |
| 13022      | Tech already connected                   | The tag has been connected.                                                 |
| 13023      | Tech has not connected                   | An attempt was made to disconnect the tag when the tag was not connected.   |
| 13013      | NFC tag has not been discovered          | No NFC tags were found.                                                     |
| 13014      | Invalid tech                             | The tag technology is invalid.                                              |
| 13015      | Unavailable tech                         | Failed to obtain the corresponding technology from the tag.                 |
| 13024      | Function not support                     | The current tag technology does not support this feature.                   |
| 13017      | System internal error                    | Relevant read/write operations failed.                                      |
| 13016      | Connect fail                             | The connection failed.                                                      |

# IsoDep

`IsoDep` tag

## Methods

[IsoDep.connect()](nfc#isodepconnectobject-object)

Connects to the NFC tag.

[IsoDep.close()](nfc#isodepcloseobject-object)

Closes the connection.

[IsoDep.setTimeout(Object object)](nfc#isodepsettimeoutobject-object)

Sets the timeout period.

[IsoDep.isConnected()](nfc#isodepisconnectedobject-object)

Checks whether the connection is established.

[IsoDep.getMaxTransceiveLength()](nfc#isodepgetmaxtransceivelengthobject-object)

Gets the maximum length of the transferred data.

[IsoDep.transceive(Object object)](nfc#isodeptransceiveobject-object)

Sends data.

[IsoDep.getHistoricalBytes()](nfc#isodepgethistoricalbytesobject-object)

Gets the reset information.

# IsoDep.close(Object object)

> WeChat for iOS: Not supported  
> WeChat for Android: Supported

## Feature description

Closes the connection.

# Parameters

**Object object**

| Attribute | Type     | Default | Required | Description                                                                        |
| :-------- | :------- | :------ | :------- | :--------------------------------------------------------------------------------- |
| success   | Function |         | No       | Callback function for successful API call                                          |
| fail      | Function |         | No       | Callback function for failed API call                                              |
| complete  | Function |         | No       | Callback function for API call end (executed for both successful and failed calls) |

## Error codes

| Error Code | Error Message                            | Description                                                                 |
| :--------- | :--------------------------------------- | :-------------------------------------------------------------------------- |
| 13000      | The device does not support NFC.         |                                                                             |
| 13001      | The system NFC switch is not toggled on. |                                                                             |
| 13010      | An unknown error occurred.               |                                                                             |
| 13019      | User is not authorized                   | The user has not granted the permission.                                    |
| 13011      | Invalid parameter                        | The parameter is invalid.                                                   |
| 13012      | Parse NdefMessage failed                 | Failed to parse the parameter into `NdefMessage .`                          |
| 13021      | NFC discovery already started            | NFC scanning has been started.                                              |
| 13018      | NFC discovery has not started            | An attempt was made to stop NFC scanning when NFC scanning was not started. |
| 13022      | Tech already connected                   | The tag has been connected.                                                 |
| 13023      | Tech has not connected                   | An attempt was made to disconnect the tag when the tag was not connected.   |
| 13013      | NFC tag has not been discovered          | No NFC tags were found.                                                     |
| 13014      | Invalid tech                             | The tag technology is invalid.                                              |
| 13015      | Unavailable tech                         | Failed to obtain the corresponding technology from the tag.                 |
| 13024      | Function not support                     | The current tag technology does not support this feature.                   |
| 13017      | System internal error                    | Relevant read/write operations failed.                                      |
| 13016      | Connect fail                             | The connection failed.                                                      |

# IsoDep.connect(Object object)

> WeChat for iOS: Not supported  
> WeChat for Android: Supported

## Feature description

Connects to the NFC tag.

# Parameters

**Object object**

| Attribute | Type     | Default | Required | Description                                                                        |
| :-------- | :------- | :------ | :------- | :--------------------------------------------------------------------------------- |
| success   | Function |         | No       | Callback function for successful API call                                          |
| fail      | Function |         | No       | Callback function for failed API call                                              |
| complete  | Function |         | No       | Callback function for API call end (executed for both successful and failed calls) |

## Error codes

| Error Code | Error Message                            | Description                                                                 |
| :--------- | :--------------------------------------- | :-------------------------------------------------------------------------- |
| 13000      | The device does not support NFC.         |                                                                             |
| 13001      | The system NFC switch is not toggled on. |                                                                             |
| 13010      | An unknown error occurred.               |                                                                             |
| 13019      | User is not authorized                   | The user has not granted the permission.                                    |
| 13011      | Invalid parameter                        | The parameter is invalid.                                                   |
| 13012      | Parse NdefMessage failed                 | Failed to parse the parameter into `NdefMessage .`                          |
| 13021      | NFC discovery already started            | NFC scanning has been started.                                              |
| 13018      | NFC discovery has not started            | An attempt was made to stop NFC scanning when NFC scanning was not started. |
| 13022      | Tech already connected                   | The tag has been connected.                                                 |
| 13023      | Tech has not connected                   | An attempt was made to disconnect the tag when the tag was not connected.   |
| 13013      | NFC tag has not been discovered          | No NFC tags were found.                                                     |
| 13014      | Invalid tech                             | The tag technology is invalid.                                              |
| 13015      | Unavailable tech                         | Failed to obtain the corresponding technology from the tag.                 |
| 13024      | Function not support                     | The current tag technology does not support this feature.                   |
| 13017      | System internal error                    | Relevant read/write operations failed.                                      |
| 13016      | Connect fail                             | The connection failed.                                                      |

# IsoDep.getHistoricalBytes(Object object)

> WeChat for iOS: Not supported  
> WeChat for Android: Supported

## Feature description

Gets the reset information.

# Parameters

**Object object**

| Attribute | Type     | Default | Required | Description                                                                        |
| :-------- | :------- | :------ | :------- | :--------------------------------------------------------------------------------- |
| success   | Function |         | No       | Callback function for successful API call                                          |
| fail      | Function |         | No       | Callback function for failed API call                                              |
| complete  | Function |         | No       | Callback function for API call end (executed for both successful and failed calls) |

`object.success` callback function

**Parameters**

**Object res**

| Attribute | Type        | Description                     |
| :-------- | :---------- | :------------------------------ |
| histBytes | ArrayBuffer | Returned historical binary data |

## Error codes

| Error Code | Error Message                            | Description                                                                 |
| :--------- | :--------------------------------------- | :-------------------------------------------------------------------------- |
| 13000      | The device does not support NFC.         |                                                                             |
| 13001      | The system NFC switch is not toggled on. |                                                                             |
| 13010      | An unknown error occurred.               |                                                                             |
| 13019      | User is not authorized                   | The user has not granted the permission.                                    |
| 13011      | Invalid parameter                        | The parameter is invalid.                                                   |
| 13012      | Parse NdefMessage failed                 | Failed to parse the parameter into `NdefMessage .`                          |
| 13021      | NFC discovery already started            | NFC scanning has been started.                                              |
| 13018      | NFC discovery has not started            | An attempt was made to stop NFC scanning when NFC scanning was not started. |
| 13022      | Tech already connected                   | The tag has been connected.                                                 |
| 13023      | Tech has not connected                   | An attempt was made to disconnect the tag when the tag was not connected.   |
| 13013      | NFC tag has not been discovered          | No NFC tags were found.                                                     |
| 13014      | Invalid tech                             | The tag technology is invalid.                                              |
| 13015      | Unavailable tech                         | Failed to obtain the corresponding technology from the tag.                 |
| 13024      | Function not support                     | The current tag technology does not support this feature.                   |
| 13017      | System internal error                    | Relevant read/write operations failed.                                      |
| 13016      | Connect fail                             | The connection failed.                                                      |

# IsoDep.getMaxTransceiveLength(Object object)

> WeChat for iOS: Not supported  
> WeChat for Android: Supported

## Feature description

Gets the maximum length of the transferred data.

# Parameters

**Object object**

| Attribute | Type     | Default | Required | Description                                                                        |
| :-------- | :------- | :------ | :------- | :--------------------------------------------------------------------------------- |
| success   | Function |         | No       | Callback function for successful API call                                          |
| fail      | Function |         | No       | Callback function for failed API call                                              |
| complete  | Function |         | No       | Callback function for API call end (executed for both successful and failed calls) |

`object.success` callback function

**Parameters**

**Object res**

| Attribute | Type   | Description                            |
| :-------- | :----- | :------------------------------------- |
| length    | Number | Maximum length of the transferred data |

## Error codes

| Error Code | Error Message                            | Description                                                                 |
| :--------- | :--------------------------------------- | :-------------------------------------------------------------------------- |
| 13000      | The device does not support NFC.         |                                                                             |
| 13001      | The system NFC switch is not toggled on. |                                                                             |
| 13010      | An unknown error occurred.               |                                                                             |
| 13019      | User is not authorized                   | The user has not granted the permission.                                    |
| 13011      | Invalid parameter                        | The parameter is invalid.                                                   |
| 13012      | Parse NdefMessage failed                 | Failed to parse the parameter into `NdefMessage .`                          |
| 13021      | NFC discovery already started            | NFC scanning has been started.                                              |
| 13018      | NFC discovery has not started            | An attempt was made to stop NFC scanning when NFC scanning was not started. |
| 13022      | Tech already connected                   | The tag has been connected.                                                 |
| 13023      | Tech has not connected                   | An attempt was made to disconnect the tag when the tag was not connected.   |
| 13013      | NFC tag has not been discovered          | No NFC tags were found.                                                     |
| 13014      | Invalid tech                             | The tag technology is invalid.                                              |
| 13015      | Unavailable tech                         | Failed to obtain the corresponding technology from the tag.                 |
| 13024      | Function not support                     | The current tag technology does not support this feature.                   |
| 13017      | System internal error                    | Relevant read/write operations failed.                                      |
| 13016      | Connect fail                             | The connection failed.                                                      |

# IsoDep.isConnected(Object object)

> WeChat for iOS: Not supported  
> WeChat for Android: Supported

## Feature description

Checks whether the connection is established.

# Parameters

**Object object**

| Attribute | Type     | Default | Required | Description                                                                        |
| :-------- | :------- | :------ | :------- | :--------------------------------------------------------------------------------- |
| success   | Function |         | No       | Callback function for successful API call                                          |
| fail      | Function |         | No       | Callback function for failed API call                                              |
| complete  | Function |         | No       | Callback function for API call end (executed for both successful and failed calls) |

## Error codes

| Error Code | Error Message                            | Description                                                                 |
| :--------- | :--------------------------------------- | :-------------------------------------------------------------------------- |
| 13000      | The device does not support NFC.         |                                                                             |
| 13001      | The system NFC switch is not toggled on. |                                                                             |
| 13010      | An unknown error occurred.               |                                                                             |
| 13019      | User is not authorized                   | The user has not granted the permission.                                    |
| 13011      | Invalid parameter                        | The parameter is invalid.                                                   |
| 13012      | Parse NdefMessage failed                 | Failed to parse the parameter into `NdefMessage .`                          |
| 13021      | NFC discovery already started            | NFC scanning has been started.                                              |
| 13018      | NFC discovery has not started            | An attempt was made to stop NFC scanning when NFC scanning was not started. |
| 13022      | Tech already connected                   | The tag has been connected.                                                 |
| 13023      | Tech has not connected                   | An attempt was made to disconnect the tag when the tag was not connected.   |
| 13013      | NFC tag has not been discovered          | No NFC tags were found.                                                     |
| 13014      | Invalid tech                             | The tag technology is invalid.                                              |
| 13015      | Unavailable tech                         | Failed to obtain the corresponding technology from the tag.                 |
| 13024      | Function not support                     | The current tag technology does not support this feature.                   |
| 13017      | System internal error                    | Relevant read/write operations failed.                                      |
| 13016      | Connect fail                             | The connection failed.                                                      |

# IsoDep.setTimeout(Object object)

> WeChat for iOS: Not supported  
> WeChat for Android: Supported

## Feature description

Sets the timeout period.

# Parameters

**Object object**

| Attribute | Type     | Default | Required | Description                                                                        |
| :-------- | :------- | :------ | :------- | :--------------------------------------------------------------------------------- |
| timeout   | Number   |         | Yes      | Sets the timeout period in ms                                                      |
| success   | Function |         | No       | Callback function for successful API call                                          |
| fail      | Function |         | No       | Callback function for failed API call                                              |
| complete  | Function |         | No       | Callback function for API call end (executed for both successful and failed calls) |

## Error codes

| Error Code | Error Message                            | Description                                                                 |
| :--------- | :--------------------------------------- | :-------------------------------------------------------------------------- |
| 13000      | The device does not support NFC.         |                                                                             |
| 13001      | The system NFC switch is not toggled on. |                                                                             |
| 13010      | An unknown error occurred.               |                                                                             |
| 13019      | User is not authorized                   | The user has not granted the permission.                                    |
| 13011      | Invalid parameter                        | The parameter is invalid.                                                   |
| 13012      | Parse NdefMessage failed                 | Failed to parse the parameter into `NdefMessage .`                          |
| 13021      | NFC discovery already started            | NFC scanning has been started.                                              |
| 13018      | NFC discovery has not started            | An attempt was made to stop NFC scanning when NFC scanning was not started. |
| 13022      | Tech already connected                   | The tag has been connected.                                                 |
| 13023      | Tech has not connected                   | An attempt was made to disconnect the tag when the tag was not connected.   |
| 13013      | NFC tag has not been discovered          | No NFC tags were found.                                                     |
| 13014      | Invalid tech                             | The tag technology is invalid.                                              |
| 13015      | Unavailable tech                         | Failed to obtain the corresponding technology from the tag.                 |
| 13024      | Function not support                     | The current tag technology does not support this feature.                   |
| 13017      | System internal error                    | Relevant read/write operations failed.                                      |
| 13016      | Connect fail                             | The connection failed.                                                      |

# IsoDep.transceive(Object object)

> WeChat for iOS: Not supported  
> WeChat for Android: Supported

## Feature description

Sends data.

# Parameters

**Object object**

| Attribute | Type        | Default | Required | Description                                                                        |
| :-------- | :---------- | :------ | :------- | :--------------------------------------------------------------------------------- |
| data      | ArrayBuffer |         | Yes      | The binary data that needs to be transferred                                       |
| success   | Function    |         | No       | Callback function for successful API call                                          |
| fail      | Function    |         | No       | Callback function for failed API call                                              |
| complete  | Function    |         | No       | Callback function for API call end (executed for both successful and failed calls) |

`object.success` callback function

# Parameters

**Object res**

| Attribute | Type        | Description |
| :-------- | :---------- | :---------- |
| data      | ArrayBuffer |             |

## Error codes

| Error Code | Error Message                            | Description                                                                 |
| :--------- | :--------------------------------------- | :-------------------------------------------------------------------------- |
| 13000      | The device does not support NFC.         |                                                                             |
| 13001      | The system NFC switch is not toggled on. |                                                                             |
| 13010      | An unknown error occurred.               |                                                                             |
| 13019      | User is not authorized                   | The user has not granted the permission.                                    |
| 13011      | Invalid parameter                        | The parameter is invalid.                                                   |
| 13012      | Parse NdefMessage failed                 | Failed to parse the parameter into `NdefMessage .`                          |
| 13021      | NFC discovery already started            | NFC scanning has been started.                                              |
| 13018      | NFC discovery has not started            | An attempt was made to stop NFC scanning when NFC scanning was not started. |
| 13022      | Tech already connected                   | The tag has been connected.                                                 |
| 13023      | Tech has not connected                   | An attempt was made to disconnect the tag when the tag was not connected.   |
| 13013      | NFC tag has not been discovered          | No NFC tags were found.                                                     |
| 13014      | Invalid tech                             | The tag technology is invalid.                                              |
| 13015      | Unavailable tech                         | Failed to obtain the corresponding technology from the tag.                 |
| 13024      | Function not support                     | The current tag technology does not support this feature.                   |
| 13017      | System internal error                    | Relevant read/write operations failed.                                      |
| 13016      | Connect fail                             | The connection failed.                                                      |

# MifareClassic

`MifareClassic` tag

## Methods

[MifareClassic.connect()](nfc#mifareclassicconnectobject-object)

Connects to the NFC tag.

[MifareClassic.close()](nfc#mifareclassiccloseobject-object)

Closes the connection.

[MifareClassic.setTimeout(Object object)](nfc#mifareclassicsettimeoutobject-object)

Sets the timeout period.

[MifareClassic.isConnected()](nfc#mifareclassicisconnectedobject-object)

Checks whether the connection is established.

[MifareClassic.getMaxTransceiveLength()](nfc#mifareclassicgetmaxtransceivelengthobject-object)

Gets the maximum length of the transferred data.

[MifareClassic.transceive(Object object)](nfc#mifareclassictransceiveobject-object)

Sends data.

Block read/write for `MifareClassic`

- Use the instruction 0x30 + block number to read data from a certain block.
- Use the instruction 0xA0 + block number + target data to write data to a certain block.

# MifareClassic.close(Object object)

> WeChat for iOS: Not supported  
> WeChat for Android: Supported

## Feature description

Closes the connection.

# Parameters

**Object object**

| Attribute | Type     | Default | Required | Description                                                                        |
| :-------- | :------- | :------ | :------- | :--------------------------------------------------------------------------------- |
| success   | Function |         | No       | Callback function for successful API call                                          |
| fail      | Function |         | No       | Callback function for failed API call                                              |
| complete  | Function |         | No       | Callback function for API call end (executed for both successful and failed calls) |

# Error codes

| Error Code | Error Message                            | Description                                                                 |
| :--------- | :--------------------------------------- | :-------------------------------------------------------------------------- |
| 13000      | The device does not support NFC.         |                                                                             |
| 13001      | The system NFC switch is not toggled on. |                                                                             |
| 13010      | An unknown error occurred.               |                                                                             |
| 13019      | User is not authorized                   | The user has not granted the permission.                                    |
| 13011      | Invalid parameter                        | The parameter is invalid.                                                   |
| 13012      | Parse Ndef Message failed                | Failed to parse the parameter into `NdefMessage .`                          |
| 13021      | NFC discovery already started            | NFC scanning has been started.                                              |
| 13018      | NFC discovery has not started            | An attempt was made to stop NFC scanning when NFC scanning was not started. |
| 13022      | Tech already connected                   | The tag has been connected.                                                 |
| 13023      | Tech has not connected                   | An attempt was made to disconnect the tag when the tag was not connected.   |
| 13013      | NFC tag has not been discovered          | No NFC tags were found.                                                     |
| 13014      | Invalid tech                             | The tag technology is invalid.                                              |
| 13015      | Unavailable tech                         | Failed to obtain the corresponding technology from the tag.                 |
| 13024      | Function not support                     | The current tag technology does not support this feature.                   |
| 13017      | System internal error                    | Relevant read/write operations failed.                                      |
| 13016      | Connect fail                             | The connection failed.                                                      |

# MifareClassic.connect(Object object)

> WeChat for iOS: Not supported  
> WeChat for Android: Supported

## Feature description

Connects to the NFC tag.

# Parameters

**Object object**

| Attribute | Type     | Default | Required | Description                                                                        |
| :-------- | :------- | :------ | :------- | :--------------------------------------------------------------------------------- |
| success   | Function |         | No       | Callback function for successful API call                                          |
| fail      | Function |         | No       | Callback function for failed API call                                              |
| complete  | Function |         | No       | Callback function for API call end (executed for both successful and failed calls) |

## Error codes

| Error Code | Error Message                            | Description                                                                 |
| :--------- | :--------------------------------------- | :-------------------------------------------------------------------------- |
| 13000      | The device does not support NFC.         |                                                                             |
| 13001      | The system NFC switch is not toggled on. |                                                                             |
| 13010      | An unknown error occurred.               |                                                                             |
| 13019      | User is not authorized                   | The user has not granted the permission.                                    |
| 13011      | Invalid parameter                        | The parameter is invalid.                                                   |
| 13012      | Parse NdefMessage failed                 | Failed to parse the parameter into `NdefMessage .`                          |
| 13021      | NFC discovery already started            | NFC scanning has been started.                                              |
| 13018      | NFC discovery has not started            | An attempt was made to stop NFC scanning when NFC scanning was not started. |
| 13022      | Tech already connected                   | The tag has been connected.                                                 |
| 13023      | Tech has not connected                   | An attempt was made to disconnect the tag when the tag was not connected.   |
| 13013      | NFC tag has not been discovered          | No NFC tags were found.                                                     |
| 13014      | Invalid tech                             | The tag technology is invalid.                                              |
| 13015      | Unavailable tech                         | Failed to obtain the corresponding technology from the tag.                 |
| 13024      | Function not support                     | The current tag technology does not support this feature.                   |
| 13017      | System internal error                    | Relevant read/write operations failed.                                      |
| 13016      | Connect fail                             | The connection failed.                                                      |

# MifareClassic.getMaxTransceiveLength(Object object)

> WeChat for iOS: Not supported  
> WeChat for Android: Supported

## Feature description

Gets the maximum length of the transferred data.

# Parameters

**Object object**

| Attribute | Type     | Default | Required | Description                                                                        |
| :-------- | :------- | :------ | :------- | :--------------------------------------------------------------------------------- |
| success   | Function |         | No       | Callback function for successful API call                                          |
| fail      | Function |         | No       | Callback function for failed API call                                              |
| complete  | Function |         | No       | Callback function for API call end (executed for both successful and failed calls) |

`object.success` callback function

# Parameters

**Object res**

| Attribute | Type   | Description                            |
| :-------- | :----- | :------------------------------------- |
| length    | Number | Maximum length of the transferred data |

## Error codes

| Error Code | Error Message                            | Description                                                                 |
| :--------- | :--------------------------------------- | :-------------------------------------------------------------------------- |
| 13000      | The device does not support NFC.         |                                                                             |
| 13001      | The system NFC switch is not toggled on. |                                                                             |
| 13010      | An unknown error occurred.               |                                                                             |
| 13019      | User is not authorized                   | The user has not granted the permission.                                    |
| 13011      | Invalid parameter                        | The parameter is invalid.                                                   |
| 13012      | Parse Ndef Message failed                | Failed to parse the parameter into `NdefMessage .`                          |
| 13021      | NFC discovery already started            | NFC scanning has been started.                                              |
| 13018      | NFC discovery has not started            | An attempt was made to stop NFC scanning when NFC scanning was not started. |
| 13022      | Tech already connected                   | The tag has been connected.                                                 |
| 13023      | Tech has not connected                   | An attempt was made to disconnect the tag when the tag was not connected.   |
| 13013      | NFC tag has not been discovered          | No NFC tags were found.                                                     |
| 13014      | Invalid tech                             | The tag technology is invalid.                                              |
| 13015      | Unavailable tech                         | Failed to obtain the corresponding technology from the tag.                 |
| 13024      | Function not support                     | The current tag technology does not support this feature.                   |
| 13017      | System internal error                    | Relevant read/write operations failed.                                      |
| 13016      | Connect fail                             | The connection failed.                                                      |

# MifareClassic.isConnected(Object object)

> WeChat for iOS: Not supported  
> WeChat for Android: Supported

## Feature description

Checks whether the connection is established.

# Parameters

**Object object**

| Attribute | Type     | Default | Required | Description                                                                        |
| :-------- | :------- | :------ | :------- | :--------------------------------------------------------------------------------- |
| success   | Function |         | No       | Callback function for successful API call                                          |
| fail      | Function |         | No       | Callback function for failed API call                                              |
| complete  | Function |         | No       | Callback function for API call end (executed for both successful and failed calls) |

## Error codes

| Error Code | Error Message                            | Description                                                                 |
| :--------- | :--------------------------------------- | :-------------------------------------------------------------------------- |
| 13000      | The device does not support NFC.         |                                                                             |
| 13001      | The system NFC switch is not toggled on. |                                                                             |
| 13010      | An unknown error occurred.               |                                                                             |
| 13019      | User is not authorized                   | The user has not granted the permission.                                    |
| 13011      | Invalid parameter                        | The parameter is invalid.                                                   |
| 13012      | Parse Ndef Message failed                | Failed to parse the parameter into `NdefMessage .`                          |
| 13021      | NFC discovery already started            | NFC scanning has been started.                                              |
| 13018      | NFC discovery has not started            | An attempt was made to stop NFC scanning when NFC scanning was not started. |
| 13022      | Tech already connected                   | The tag has been connected.                                                 |
| 13023      | Tech has not connected                   | An attempt was made to disconnect the tag when the tag was not connected.   |
| 13013      | NFC tag has not been discovered          | No NFC tags were found.                                                     |
| 13014      | Invalid tech                             | The tag technology is invalid.                                              |
| 13015      | Unavailable tech                         | Failed to obtain the corresponding technology from the tag.                 |
| 13024      | Function not support                     | The current tag technology does not support this feature.                   |
| 13017      | System internal error                    | Relevant read/write operations failed.                                      |
| 13016      | Connect fail                             | The connection failed.                                                      |

# MifareClassic.setTimeout(Object object)

> WeChat for iOS: Not supported  
> WeChat for Android: Supported

## Feature description

Sets the timeout period.

# Parameters

**Object object**

| Attribute | Type     | Default | Required | Description                                                                        |
| :-------- | :------- | :------ | :------- | :--------------------------------------------------------------------------------- |
| timeout   | Number   |         | Yes      | Sets the timeout period in ms                                                      |
| success   | Function |         | No       | Callback function for successful API call                                          |
| fail      | Function |         | No       | Callback function for failed API call                                              |
| complete  | Function |         | No       | Callback function for API call end (executed for both successful and failed calls) |

## Error codes

| Error Code | Error Message                            | Description                                                                 |
| :--------- | :--------------------------------------- | :-------------------------------------------------------------------------- |
| 13000      | The device does not support NFC.         |                                                                             |
| 13001      | The system NFC switch is not toggled on. |                                                                             |
| 13010      | An unknown error occurred.               |                                                                             |
| 13019      | user is not authorized                   | The user has not granted the permission.                                    |
| 13011      | invalid parameter                        | The parameter is invalid.                                                   |
| 13012      | parse NdefMessage failed                 | Failed to parse the parameter into `NdefMessage .`                          |
| 13021      | NFC discovery already started            | NFC scanning has been started.                                              |
| 13018      | NFC discovery has not started            | An attempt was made to stop NFC scanning when NFC scanning was not started. |
| 13022      | Tech already connected                   | The tag has been connected.                                                 |
| 13023      | Tech has not connected                   | An attempt was made to disconnect the tag when the tag was not connected.   |
| 13013      | NFC tag has not been discovered          | No NFC tags were found.                                                     |
| 13014      | invalid tech                             | The tag technology is invalid.                                              |
| 13015      | unavailable tech                         | Failed to obtain the corresponding technology from the tag.                 |
| 13024      | function not support                     | The current tag technology does not support this feature.                   |
| 13017      | system internal error                    | Relevant read/write operations failed.                                      |
| 13016      | connect fail                             | The connection failed.                                                      |

# MifareClassic.transceive(Object object)

> WeChat for iOS: Not supported  
> WeChat for Android: Supported

## Feature description

Sends data.

## Parameters

**Object object**

| Attribute | Type        | Default | Required | Description                                                                        |
| :-------- | :---------- | :------ | :------- | :--------------------------------------------------------------------------------- |
| data      | ArrayBuffer |         | Yes      | The binary data that needs to be transferred                                       |
| success   | function    |         | No       | Callback function for successful API call                                          |
| fail      | function    |         | No       | Callback function for failed API call                                              |
| complete  | function    |         | No       | Callback function for API call end (executed for both successful and failed calls) |

`object.success` callback function

**Parameters**

**Object res**

| Attribute | Type        | Description |
| :-------- | :---------- | :---------- |
| data      | ArrayBuffer |             |

## Error codes

| Error Code | Error Message                            | Description                                                                 |
| :--------- | :--------------------------------------- | :-------------------------------------------------------------------------- |
| 13000      | The device does not support NFC.         |                                                                             |
| 13001      | The system NFC switch is not toggled on. |                                                                             |
| 13010      | An unknown error occurred.               |                                                                             |
| 13019      | user is not authorized                   | The user has not granted the permission.                                    |
| 13011      | invalid parameter                        | The parameter is invalid.                                                   |
| 13012      | parse NdefMessage failed                 | Failed to parse the parameter into `NdefMessage .`                          |
| 13021      | NFC discovery already started            | NFC scanning has been started.                                              |
| 13018      | NFC discovery has not started            | An attempt was made to stop NFC scanning when NFC scanning was not started. |
| 13022      | Tech already connected                   | The tag has been connected.                                                 |
| 13023      | Tech has not connected                   | An attempt was made to disconnect the tag when the tag was not connected.   |
| 13013      | NFC tag has not been discovered          | No NFC tags were found.                                                     |
| 13014      | invalid tech                             | The tag technology is invalid.                                              |
| 13015      | unavailable tech                         | Failed to obtain the corresponding technology from the tag.                 |
| 13024      | function not support                     | The current tag technology does not support this feature.                   |
| 13017      | system internal error                    | Relevant read/write operations failed.                                      |
| 13016      | connect fail                             | The connection failed.                                                      |

# MifareUltralight

`MifareUltralight` tag

## Methods

[MifareUltralight.connect()](nfc#mifareultralightconnectobject-object)  
Connects to the NFC tag.

[MifareUltralight.close()](nfc#mifareultralightcloseobject-object)  
Closes the connection.

[MifareUltralight.setTimeout(Object object)](nfc#mifareultralightsettimeoutobject-object)  
Sets the timeout period.

[MifareUltralight.isConnected()](nfc#mifareultralightisconnectedobject-object)  
Checks whether the connection is established.

[MifareUltralight.getMaxTransceiveLength()](nfc#mifareultralightgetmaxtransceivelengthobject-object)  
Gets the maximum length of the transferred data.

[MifareUltralight.transceive(Object object)](nfc#mifareultralighttransceiveobject-object)  
Sends data.

# MifareUltralight.close(Object object)

> WeChat for iOS: Not supported  
> WeChat for Android: Supported

## Feature description

Closes the connection.

# Parameters

**Object object**

| Attribute | Type     | Default | Required | Description                                                                        |
| :-------- | :------- | :------ | :------- | :--------------------------------------------------------------------------------- |
| success   | Function |         | No       | Callback function for successful API call                                          |
| fail      | Function |         | No       | Callback function for failed API call                                              |
| complete  | Function |         | No       | Callback function for API call end (executed for both successful and failed calls) |

## Error codes

| Error Code | Error Message                            | Description                                                                 |
| :--------- | :--------------------------------------- | :-------------------------------------------------------------------------- |
| 13000      | The device does not support NFC.         |                                                                             |
| 13001      | The system NFC switch is not toggled on. |                                                                             |
| 13010      | An unknown error occurred.               |                                                                             |
| 13019      | user is not authorized                   | The user has not granted the permission.                                    |
| 13011      | invalid parameter                        | The parameter is invalid.                                                   |
| 13012      | parse NdefMessage failed                 | Failed to parse the parameter into `NdefMessage .`                          |
| 13021      | NFC discovery already started            | NFC scanning has been started.                                              |
| 13018      | NFC discovery has not started            | An attempt was made to stop NFC scanning when NFC scanning was not started. |
| 13022      | Tech already connected                   | The tag has been connected.                                                 |
| 13023      | Tech has not connected                   | An attempt was made to disconnect the tag when the tag was not connected.   |
| 13013      | NFC tag has not been discovered          | No NFC tags were found.                                                     |
| 13014      | invalid tech                             | The tag technology is invalid.                                              |
| 13015      | unavailable tech                         | Failed to obtain the corresponding technology from the tag.                 |
| 13024      | function not support                     | The current tag technology does not support this feature.                   |
| 13017      | system internal error                    | Relevant read/write operations failed.                                      |
| 13016      | connect fail                             | The connection failed.                                                      |

# MifareUltralight.connect(Object object)

> WeChat for iOS: Not supported  
> WeChat for Android: Supported

## Feature description

Connects to the NFC tag.

## Parameters

**Object object**

| Attribute | Type     | Default | Required | Description                                                                        |
| :-------- | :------- | :------ | :------- | :--------------------------------------------------------------------------------- |
| success   | function |         | No       | Callback function for successful API call                                          |
| fail      | function |         | No       | Callback function for failed API call                                              |
| complete  | function |         | No       | Callback function for API call end (executed for both successful and failed calls) |

## Error codes

| Error Code | Error Message                            | Description                                                                 |
| :--------- | :--------------------------------------- | :-------------------------------------------------------------------------- |
| 13000      | The device does not support NFC.         |                                                                             |
| 13001      | The system NFC switch is not toggled on. |                                                                             |
| 13010      | An unknown error occurred.               |                                                                             |
| 13019      | User is not authorized                   | The user has not granted the permission.                                    |
| 13011      | Invalid parameter                        | The parameter is invalid.                                                   |
| 13012      | Parse NdefMessage failed                 | Failed to parse the parameter into `NdefMessage .`                          |
| 13021      | NFC discovery already started            | NFC scanning has been started.                                              |
| 13018      | NFC discovery has not started            | An attempt was made to stop NFC scanning when NFC scanning was not started. |
| 13022      | Tech already connected                   | The tag has been connected.                                                 |
| 13023      | Tech has not connected                   | An attempt was made to disconnect the tag when the tag was not connected.   |
| 13013      | NFC tag has not been discovered          | No NFC tags were found.                                                     |
| 13014      | Invalid tech                             | The tag technology is invalid.                                              |
| 13015      | Unavailable tech                         | Failed to obtain the corresponding technology from the tag.                 |
| 13024      | Function not support                     | The current tag technology does not support this feature.                   |
| 13017      | System internal error                    | Relevant read/write operations failed.                                      |
| 13016      | Connect fail                             | The connection failed.                                                      |

# MifareUltralight.getMaxTransceiveLength(Object object)

> WeChat for iOS: Not supported  
> WeChat for Android: Supported

## Feature description

Gets the maximum length of the transferred data.

## Parameters

**Object object**

| Attribute | Type     | Default | Required | Description                                                                        |
| :-------- | :------- | :------ | :------- | :--------------------------------------------------------------------------------- |
| success   | Function |         | No       | Callback function for successful API call                                          |
| fail      | Function |         | No       | Callback function for failed API call                                              |
| complete  | Function |         | No       | Callback function for API call end (executed for both successful and failed calls) |

`object.success` callback function

# Parameters

**Object res**

| Attribute | Type   | Description                            |
| :-------- | :----- | :------------------------------------- |
| length    | Number | Maximum length of the transferred data |

## Error codes

| Error Code | Error Message                            | Description                                                                 |
| :--------- | :--------------------------------------- | :-------------------------------------------------------------------------- |
| 13000      | The device does not support NFC.         |                                                                             |
| 13001      | The system NFC switch is not toggled on. |                                                                             |
| 13010      | An unknown error occurred.               |                                                                             |
| 13019      | User is not authorized                   | The user has not granted the permission.                                    |
| 13011      | Invalid parameter                        | The parameter is invalid.                                                   |
| 13012      | Parse NdefMessage failed                 | Failed to parse the parameter into `NdefMessage .`                          |
| 13021      | NFC discovery already started            | NFC scanning has been started.                                              |
| 13018      | NFC discovery has not started            | An attempt was made to stop NFC scanning when NFC scanning was not started. |
| 13022      | Tech already connected                   | The tag has been connected.                                                 |
| 13023      | Tech has not connected                   | An attempt was made to disconnect the tag when the tag was not connected.   |
| 13013      | NFC tag has not been discovered          | No NFC tags were found.                                                     |
| 13014      | Invalid tech                             | The tag technology is invalid.                                              |
| 13015      | Unavailable tech                         | Failed to obtain the corresponding technology from the tag.                 |
| 13024      | Function not support                     | The current tag technology does not support this feature.                   |
| 13017      | System internal error                    | Relevant read/write operations failed.                                      |
| 13016      | Connect fail                             | The connection failed.                                                      |

# MifareUltralight.isConnected(Object object)

> WeChat for iOS: Not supported  
> WeChat for Android: Supported

## Feature description

Checks whether the connection is established.

## Parameters

**Object object**

| Attribute | Type     | Default | Required | Description                                                                        |
| :-------- | :------- | :------ | :------- | :--------------------------------------------------------------------------------- |
| success   | Function |         | No       | Callback function for successful API call                                          |
| fail      | Function |         | No       | Callback function for failed API call                                              |
| complete  | Function |         | No       | Callback function for API call end (executed for both successful and failed calls) |

## Error codes

| Error Code | Error Message                            | Description                                                                 |
| :--------- | :--------------------------------------- | :-------------------------------------------------------------------------- |
| 13000      | The device does not support NFC.         |                                                                             |
| 13001      | The system NFC switch is not toggled on. |                                                                             |
| 13010      | An unknown error occurred.               |                                                                             |
| 13019      | User is not authorized                   | The user has not granted the permission.                                    |
| 13011      | Invalid parameter                        | The parameter is invalid.                                                   |
| 13012      | Parse NdefMessage failed                 | Failed to parse the parameter into `NdefMessage .`                          |
| 13021      | NFC discovery already started            | NFC scanning has been started.                                              |
| 13018      | NFC discovery has not started            | An attempt was made to stop NFC scanning when NFC scanning was not started. |
| 13022      | Tech already connected                   | The tag has been connected.                                                 |
| 13023      | Tech has not connected                   | An attempt was made to disconnect the tag when the tag was not connected.   |
| 13013      | NFC tag has not been discovered          | No NFC tags were found.                                                     |
| 13014      | Invalid tech                             | The tag technology is invalid.                                              |
| 13015      | Unavailable tech                         | Failed to obtain the corresponding technology from the tag.                 |
| 13024      | Function not support                     | The current tag technology does not support this feature.                   |
| 13017      | System internal error                    | Relevant read/write operations failed.                                      |
| 13016      | Connect fail                             | The connection failed.                                                      |

# MifareUltralight.setTimeout(Object object)

> WeChat for iOS: Not supported  
> WeChat for Android: Supported

## Feature description

Sets the timeout period.

# Parameters

**Object object**

| Attribute | Type     | Default | Required | Description                                                                        |
| :-------- | :------- | :------ | :------- | :--------------------------------------------------------------------------------- |
| timeout   | Number   |         | Yes      | Sets the timeout period in ms                                                      |
| success   | Function |         | No       | Callback function for successful API call                                          |
| fail      | Function |         | No       | Callback function for failed API call                                              |
| complete  | Function |         | No       | Callback function for API call end (executed for both successful and failed calls) |

## Error codes

| Error Code | Error Message                            | Description                                                                 |
| :--------- | :--------------------------------------- | :-------------------------------------------------------------------------- |
| 13000      | The device does not support NFC.         |                                                                             |
| 13001      | The system NFC switch is not toggled on. |                                                                             |
| 13010      | An unknown error occurred.               |                                                                             |
| 13019      | User is not authorized                   | The user has not granted the permission.                                    |
| 13011      | Invalid parameter                        | The parameter is invalid.                                                   |
| 13012      | Parse NdefMessage failed                 | Failed to parse the parameter into `NdefMessage .`                          |
| 13021      | NFC discovery already started            | NFC scanning has been started.                                              |
| 13018      | NFC discovery has not started            | An attempt was made to stop NFC scanning when NFC scanning was not started. |
| 13022      | Tech already connected                   | The tag has been connected.                                                 |
| 13023      | Tech has not connected                   | An attempt was made to disconnect the tag when the tag was not connected.   |
| 13013      | NFC tag has not been discovered          | No NFC tags were found.                                                     |
| 13014      | Invalid tech                             | The tag technology is invalid.                                              |
| 13015      | Unavailable tech                         | Failed to obtain the corresponding technology from the tag.                 |
| 13024      | Function not support                     | The current tag technology does not support this feature.                   |
| 13017      | System internal error                    | Relevant read/write operations failed.                                      |
| 13016      | Connect fail                             | The connection failed.                                                      |

# MifareUltralight.transceive(Object object)

> WeChat for iOS: Not supported  
> WeChat for Android: Supported

## Feature description

Sends data.

# Parameters

**Object object**

| Attribute | Type        | Default | Required | Description                                                                        |
| :-------- | :---------- | :------ | :------- | :--------------------------------------------------------------------------------- |
| data      | ArrayBuffer |         | Yes      | The binary data that needs to be transferred                                       |
| success   | Function    |         | No       | Callback function for successful API call                                          |
| fail      | Function    |         | No       | Callback function for failed API call                                              |
| complete  | Function    |         | No       | Callback function for API call end (executed for both successful and failed calls) |

`object.success` callback function

# Parameters

**Object res**

| Attribute | Type        | Description |
| :-------- | :---------- | :---------- |
| data      | ArrayBuffer |             |

## Error codes

| Error Code | Error Message                            | Description                                                                 |
| :--------- | :--------------------------------------- | :-------------------------------------------------------------------------- |
| 13000      | The device does not support NFC.         |                                                                             |
| 13001      | The system NFC switch is not toggled on. |                                                                             |
| 13010      | An unknown error occurred.               |                                                                             |
| 13019      | User is not authorized                   | The user has not granted the permission.                                    |
| 13011      | Invalid parameter                        | The parameter is invalid.                                                   |
| 13012      | Parse NdefMessage failed                 | Failed to parse the parameter into `NdefMessage .`                          |
| 13021      | NFC discovery already started            | NFC scanning has been started.                                              |
| 13018      | NFC discovery has not started            | An attempt was made to stop NFC scanning when NFC scanning was not started. |
| 13022      | Tech already connected                   | The tag has been connected.                                                 |
| 13023      | Tech has not connected                   | An attempt was made to disconnect the tag when the tag was not connected.   |
| 13013      | NFC tag has not been discovered          | No NFC tags were found.                                                     |
| 13014      | Invalid tech                             | The tag technology is invalid.                                              |
| 13015      | Unavailable tech                         | Failed to obtain the corresponding technology from the tag.                 |
| 13024      | Function not support                     | The current tag technology does not support this feature.                   |
| 13017      | System internal error                    | Relevant read/write operations failed.                                      |
| 13016      | Connect fail                             | The connection failed.                                                      |

# Ndef

Ndef tag

## Methods

[Ndef.connect()](nfc#ndefconnectobject-object)  
Connects to the NFC tag.

[Ndef.close()](nfc#ndefcloseobject-object)  
Closes the connection.

[Ndef.setTimeout(Object object)](nfc#ndefsettimeoutobject-object)  
Sets the timeout period.

[Ndef.isConnected()](nfc#ndefisconnectedobject-object)  
Checks whether the connection is established.

[Ndef.onNdefMessage(function callback)](nfc#ndefonndefmessagefunction-callback)  
Listens for the Ndef message.

[Ndef.offNdefMessage(function callback)](nfc#ndefoffndefmessagefunction-callback)  
Unlistens for the Ndef message.

[Ndef.writeNdefMessage(Object object)](nfc#ndefwritendefmessageobject-object)  
Rewrites the content of the Ndef tag.

# Ndef.close(Object object)

> WeChat for iOS: Not supported  
> WeChat for Android: Supported

## Feature description

Closes the connection.

# Parameters

**Object object**

| Attribute | Type     | Default | Required | Description                                                                        |
| :-------- | :------- | :------ | :------- | :--------------------------------------------------------------------------------- |
| success   | Function |         | No       | Callback function for successful API call                                          |
| fail      | Function |         | No       | Callback function for failed API call                                              |
| complete  | Function |         | No       | Callback function for API call end (executed for both successful and failed calls) |

## Error codes

| Error Code | Error Message                            | Description                                                                 |
| :--------- | :--------------------------------------- | :-------------------------------------------------------------------------- |
| 13000      | The device does not support NFC.         |                                                                             |
| 13001      | The system NFC switch is not toggled on. |                                                                             |
| 13010      | An unknown error occurred.               |                                                                             |
| 13019      | User is not authorized                   | The user has not granted the permission.                                    |
| 13011      | Invalid parameter                        | The parameter is invalid.                                                   |
| 13012      | Parse NdefMessage failed                 | Failed to parse the parameter into `NdefMessage .`                          |
| 13021      | NFC discovery already started            | NFC scanning has been started.                                              |
| 13018      | NFC discovery has not started            | An attempt was made to stop NFC scanning when NFC scanning was not started. |
| 13022      | Tech already connected                   | The tag has been connected.                                                 |
| 13023      | Tech has not connected                   | An attempt was made to disconnect the tag when the tag was not connected.   |
| 13013      | NFC tag has not been discovered          | No NFC tags were found.                                                     |
| 13014      | Invalid tech                             | The tag technology is invalid.                                              |
| 13015      | Unavailable tech                         | Failed to obtain the corresponding technology from the tag.                 |
| 13024      | Function not support                     | The current tag technology does not support this feature.                   |
| 13017      | System internal error                    | Relevant read/write operations failed.                                      |
| 13016      | Connect fail                             | The connection failed.                                                      |

# Ndef.connect(Object object)

> WeChat for iOS: Not supported  
> WeChat for Android: Supported

## Feature description

Connects to the NFC tag.

# Parameters

**Object object**

| Attribute | Type     | Default | Required | Description                                                                        |
| :-------- | :------- | :------ | :------- | :--------------------------------------------------------------------------------- |
| success   | Function |         | No       | Callback function for successful API call                                          |
| fail      | Function |         | No       | Callback function for failed API call                                              |
| complete  | Function |         | No       | Callback function for API call end (executed for both successful and failed calls) |

## Error codes

| Error Code | Error Message                            | Description                                                                 |
| :--------- | :--------------------------------------- | :-------------------------------------------------------------------------- |
| 13000      | The device does not support NFC.         |                                                                             |
| 13001      | The system NFC switch is not toggled on. |                                                                             |
| 13010      | An unknown error occurred.               |                                                                             |
| 13019      | User is not authorized                   | The user has not granted the permission.                                    |
| 13011      | Invalid parameter                        | The parameter is invalid.                                                   |
| 13012      | Parse NdefMessage failed                 | Failed to parse the parameter into `NdefMessage .`                          |
| 13021      | NFC discovery already started            | NFC scanning has been started.                                              |
| 13018      | NFC discovery has not started            | An attempt was made to stop NFC scanning when NFC scanning was not started. |
| 13022      | Tech already connected                   | The tag has been connected.                                                 |
| 13023      | Tech has not connected                   | An attempt was made to disconnect the tag when the tag was not connected.   |
| 13013      | NFC tag has not been discovered          | No NFC tags were found.                                                     |
| 13014      | Invalid tech                             | The tag technology is invalid.                                              |
| 13015      | Unavailable tech                         | Failed to obtain the corresponding technology from the tag.                 |
| 13024      | Function not support                     | The current tag technology does not support this feature.                   |
| 13017      | System internal error                    | Relevant read/write operations failed.                                      |
| 13016      | Connect fail                             | The connection failed.                                                      |

# Ndef.isConnected(Object object)

> WeChat for iOS: Not supported  
> WeChat for Android: Supported

## Feature description

Checks whether the connection is established.

# Parameters

**Object object**

| Attribute | Type     | Default | Required | Description                                                                        |
| :-------- | :------- | :------ | :------- | :--------------------------------------------------------------------------------- |
| success   | Function |         | No       | Callback function for successful API call                                          |
| fail      | Function |         | No       | Callback function for failed API call                                              |
| complete  | Function |         | No       | Callback function for API call end (executed for both successful and failed calls) |

## Error codes

| Error Code | Error Message                            | Description                                                                 |
| :--------- | :--------------------------------------- | :-------------------------------------------------------------------------- |
| 13000      | The device does not support NFC.         |                                                                             |
| 13001      | The system NFC switch is not toggled on. |                                                                             |
| 13010      | An unknown error occurred.               |                                                                             |
| 13019      | User is not authorized                   | The user has not granted the permission.                                    |
| 13011      | Invalid parameter                        | The parameter is invalid.                                                   |
| 13012      | Parse NdefMessage failed                 | Failed to parse the parameter into `NdefMessage .`                          |
| 13021      | NFC discovery already started            | NFC scanning has been started.                                              |
| 13018      | NFC discovery has not started            | An attempt was made to stop NFC scanning when NFC scanning was not started. |
| 13022      | Tech already connected                   | The tag has been connected.                                                 |
| 13023      | Tech has not connected                   | An attempt was made to disconnect the tag when the tag was not connected.   |
| 13013      | NFC tag has not been discovered          | No NFC tags were found.                                                     |
| 13014      | Invalid tech                             | The tag technology is invalid.                                              |
| 13015      | Unavailable tech                         | Failed to obtain the corresponding technology from the tag.                 |
| 13024      | Function not support                     | The current tag technology does not support this feature.                   |
| 13017      | System internal error                    | Relevant read/write operations failed.                                      |
| 13016      | Connect fail                             | The connection failed.                                                      |

# Ndef.offNdefMessage(function callback)

> WeChat for iOS: Not supported  
> WeChat for Android: Supported

## Feature description

Unlistens for the Ndef message.

## Parameters

### Function callback

# Ndef.onNdefMessage(function callback)

> WeChat for iOS: Not supported  
> WeChat for Android: Supported

## Feature description

Listens for the Ndef message.

# Parameters

## Function callback

# Ndef.setTimeout(Object object)

> WeChat for iOS: Not supported  
> WeChat for Android: Supported

## Feature description

Sets the timeout period.

# Parameters

**Object object**

| Attribute | Type     | Default | Required | Description                                                                        |
| :-------- | :------- | :------ | :------- | :--------------------------------------------------------------------------------- |
| timeout   | Number   |         | Yes      | Sets the timeout period in ms                                                      |
| success   | Function |         | No       | Callback function for successful API call                                          |
| fail      | Function |         | No       | Callback function for failed API call                                              |
| complete  | Function |         | No       | Callback function for API call end (executed for both successful and failed calls) |

## Error codes

| Error Code | Error Message                            | Description                                                                 |
| :--------- | :--------------------------------------- | :-------------------------------------------------------------------------- |
| 13000      | The device does not support NFC.         |                                                                             |
| 13001      | The system NFC switch is not toggled on. |                                                                             |
| 13010      | An unknown error occurred.               |                                                                             |
| 13019      | User is not authorized                   | The user has not granted the permission.                                    |
| 13011      | Invalid parameter                        | The parameter is invalid.                                                   |
| 13012      | Parse NdefMessage failed                 | Failed to parse the parameter into `NdefMessage .`                          |
| 13021      | NFC discovery already started            | NFC scanning has been started.                                              |
| 13018      | NFC discovery has not started            | An attempt was made to stop NFC scanning when NFC scanning was not started. |
| 13022      | Tech already connected                   | The tag has been connected.                                                 |
| 13023      | Tech has not connected                   | An attempt was made to disconnect the tag when the tag was not connected.   |
| 13013      | NFC tag has not been discovered          | No NFC tags were found.                                                     |
| 13014      | Invalid tech                             | The tag technology is invalid.                                              |
| 13015      | Unavailable tech                         | Failed to obtain the corresponding technology from the tag.                 |
| 13024      | Function not support                     | The current tag technology does not support this feature.                   |
| 13017      | System internal error                    | Relevant read/write operations failed.                                      |
| 13016      | Connect fail                             | The connection failed.                                                      |

# Ndef.writeNdefMessage(Object object)

> WeChat for iOS: Not supported  
> WeChat for Android: Supported

## Feature description

Rewrites the content of the Ndef tag.

# Parameters

**Object object**

| Attribute | Type | Default | Required | Description |
| :-------- | :--- | :------ | :------- | :---------- |
| uris | Array |  | No | `uri `array |
| texts | Array |  | No | `text `array |
| records | Array |  | No | Binary object array. You need to specify` id` , `type` , and `payload` (all are of the ArrayBuffer type). |
| success | Function |  | No | Callback function for successful API call |
| fail | Function |  | No | Callback function for failed API call |
| complete | Function |  | No | Callback function for API call end (executed for both successful and failed calls) |

## Error codes

| Error Code | Error Message                            | Description                                                                 |
| :--------- | :--------------------------------------- | :-------------------------------------------------------------------------- |
| 13000      | The device does not support NFC.         |                                                                             |
| 13001      | The system NFC switch is not toggled on. |                                                                             |
| 13010      | An unknown error occurred.               |                                                                             |
| 13019      | User is not authorized                   | The user has not granted the permission.                                    |
| 13011      | Invalid parameter                        | The parameter is invalid.                                                   |
| 13012      | Parse NdefMessage failed                 | Failed to parse the parameter into `NdefMessage .`                          |
| 13021      | NFC discovery already started            | NFC scanning has been started.                                              |
| 13018      | NFC discovery has not started            | An attempt was made to stop NFC scanning when NFC scanning was not started. |
| 13022      | Tech already connected                   | The tag has been connected.                                                 |
| 13023      | Tech has not connected                   | An attempt was made to disconnect the tag when the tag was not connected.   |
| 13013      | NFC tag has not been discovered          | No NFC tags were found.                                                     |
| 13014      | Invalid tech                             | The tag technology is invalid.                                              |
| 13015      | Unavailable tech                         | Failed to obtain the corresponding technology from the tag.                 |
| 13024      | Function not support                     | The current tag technology does not support this feature.                   |
| 13017      | System internal error                    | Relevant read/write operations failed.                                      |
| 13016      | Connect fail                             | The connection failed.                                                      |

# NfcA

NfcA tag

## Methods

[NfcA.connect()](nfc#nfcaconnectobject-object)  
Connects to the NFC tag.

[NfcA.close()](nfc#nfcacloseobject-object)  
Closes the connection.

[NfcA.setTimeout(Object object)](nfc#nfcasettimeoutobject-object)  
Sets the timeout period.

[NfcA.isConnected()](nfc#nfcaisconnectedobject-object)  
Checks whether the connection is established.

[NfcA.getMaxTransceiveLength()](nfc#nfcagetmaxtransceivelengthobject-object)  
Gets the maximum length of the transferred data.

[NfcA.transceive(Object object)](nfc#nfcatransceiveobject-object)  
Sends data.

[NfcA.getAtqa()](nfc#nfcagetatqaobject-object)  
Gets the ATQA information.

[NfcA.getSak()](nfc#nfcagetsakobject-object)  
Gets the SAK information.

# NfcA.close(Object object)

> WeChat for iOS: Not supported  
> WeChat for Android: Supported

## Feature description

Closes the connection.

# Parameters

**Object object**

| Attribute | Type     | Default | Required | Description                                                                        |
| :-------- | :------- | :------ | :------- | :--------------------------------------------------------------------------------- |
| success   | Function |         | No       | Callback function for successful API call                                          |
| fail      | Function |         | No       | Callback function for failed API call                                              |
| complete  | Function |         | No       | Callback function for API call end (executed for both successful and failed calls) |

## Error codes

| Error Code | Error Message                            | Description                                                                 |
| :--------- | :--------------------------------------- | :-------------------------------------------------------------------------- |
| 13000      | The device does not support NFC.         |                                                                             |
| 13001      | The system NFC switch is not toggled on. |                                                                             |
| 13010      | An unknown error occurred.               |                                                                             |
| 13019      | User is not authorized                   | The user has not granted the permission.                                    |
| 13011      | Invalid parameter                        | The parameter is invalid.                                                   |
| 13012      | Parse NdefMessage failed                 | Failed to parse the parameter into `NdefMessage .`                          |
| 13021      | NFC discovery already started            | NFC scanning has been started.                                              |
| 13018      | NFC discovery has not started            | An attempt was made to stop NFC scanning when NFC scanning was not started. |
| 13022      | Tech already connected                   | The tag has been connected.                                                 |
| 13023      | Tech has not connected                   | An attempt was made to disconnect the tag when the tag was not connected.   |
| 13013      | NFC tag has not been discovered          | No NFC tags were found.                                                     |
| 13014      | Invalid tech                             | The tag technology is invalid.                                              |
| 13015      | Unavailable tech                         | Failed to obtain the corresponding technology from the tag.                 |
| 13024      | Function not support                     | The current tag technology does not support this feature.                   |
| 13017      | System internal error                    | Relevant read/write operations failed.                                      |
| 13016      | Connect fail                             | The connection failed.                                                      |

# NfcA.connect(Object object)

> WeChat for iOS: Not supported  
> WeChat for Android: Supported

## Feature description

Connects to the NFC tag.

## Parameters

**Object object**

| Attribute | Type     | Default | Required | Description                                                                        |
| :-------- | :------- | :------ | :------- | :--------------------------------------------------------------------------------- |
| success   | Function |         | No       | Callback function for successful API call                                          |
| fail      | Function |         | No       | Callback function for failed API call                                              |
| complete  | Function |         | No       | Callback function for API call end (executed for both successful and failed calls) |

## Error codes

| Error Code | Error Message                            | Description                                                                 |
| :--------- | :--------------------------------------- | :-------------------------------------------------------------------------- |
| 13000      | The device does not support NFC.         |                                                                             |
| 13001      | The system NFC switch is not toggled on. |                                                                             |
| 13010      | An unknown error occurred.               |                                                                             |
| 13019      | User is not authorized                   | The user has not granted the permission.                                    |
| 13011      | Invalid parameter                        | The parameter is invalid.                                                   |
| 13012      | Parse NdefMessage failed                 | Failed to parse the parameter into `NdefMessage .`                          |
| 13021      | NFC discovery already started            | NFC scanning has been started.                                              |
| 13018      | NFC discovery has not started            | An attempt was made to stop NFC scanning when NFC scanning was not started. |
| 13022      | Tech already connected                   | The tag has been connected.                                                 |
| 13023      | Tech has not connected                   | An attempt was made to disconnect the tag when the tag was not connected.   |
| 13013      | NFC tag has not been discovered          | No NFC tags were found.                                                     |
| 13014      | Invalid tech                             | The tag technology is invalid.                                              |
| 13015      | Unavailable tech                         | Failed to obtain the corresponding technology from the tag.                 |
| 13024      | Function not support                     | The current tag technology does not support this feature.                   |
| 13017      | System internal error                    | Relevant read/write operations failed.                                      |
| 13016      | Connect fail                             | The connection failed.                                                      |

# NfcA.getAtqa(Object object)

> WeChat for iOS: Not supported  
> WeChat for Android: Supported

## Feature description

Gets the ATQA information.

# Parameters

**Object object**

| Attribute | Type     | Default | Required | Description                                                                        |
| :-------- | :------- | :------ | :------- | :--------------------------------------------------------------------------------- |
| success   | Function |         | No       | Callback function for successful API call                                          |
| fail      | Function |         | No       | Callback function for failed API call                                              |
| complete  | function |         | No       | Callback function for API call end (executed for both successful and failed calls) |

`object.success` callback function

# Parameter

**Object res**

| Attribute | Type        | Description                  |
| :-------- | :---------- | :--------------------------- |
| atqa      | ArrayBuffer | Returned ATQA/SENS_RES data. |

## Error codes

| Error Code | Error Message                            | Description                                                                 |
| :--------- | :--------------------------------------- | :-------------------------------------------------------------------------- |
| 13000      | The device does not support NFC.         |                                                                             |
| 13001      | The system NFC switch is not toggled on. |                                                                             |
| 13010      | An unknown error occurred.               |                                                                             |
| 13019      | User is not authorized                   | The user has not granted the permission.                                    |
| 13011      | Invalid parameter                        | The parameter is invalid.                                                   |
| 13012      | Parse NdefMessage failed                 | Failed to parse the parameter into `NdefMessage .`                          |
| 13021      | NFC discovery already started            | NFC scanning has been started.                                              |
| 13018      | NFC discovery has not started            | An attempt was made to stop NFC scanning when NFC scanning was not started. |
| 13022      | Tech already connected                   | The tag has been connected.                                                 |
| 13023      | Tech has not connected                   | An attempt was made to disconnect the tag when the tag was not connected.   |
| 13013      | NFC tag has not been discovered          | No NFC tags were found.                                                     |
| 13014      | Invalid tech                             | The tag technology is invalid.                                              |
| 13015      | Unavailable tech                         | Failed to obtain the corresponding technology from the tag.                 |
| 13024      | Function not support                     | The current tag technology does not support this feature.                   |
| 13017      | System internal error                    | Relevant read/write operations failed.                                      |
| 13016      | Connect fail                             | The connection failed.                                                      |

# NfcA.getMaxTransceiveLength(Object object)

> WeChat for iOS: Not supported  
> WeChat for Android: Supported

## Feature description

Gets the maximum length of the transferred data.

# Parameters

**Object object**

| Attribute | Type     | Default | Required | Description                                                                        |
| :-------- | :------- | :------ | :------- | :--------------------------------------------------------------------------------- |
| success   | Function |         | No       | Callback function for successful API call                                          |
| fail      | Function |         | No       | Callback function for failed API call                                              |
| complete  | Function |         | No       | Callback function for API call end (executed for both successful and failed calls) |

`object.success` callback function

# Parameters

**Object res**

| Attribute | Type   | Description                            |
| :-------- | :----- | :------------------------------------- |
| length    | Number | Maximum length of the transferred data |

## Error codes

| Error Code | Error Message                            | Description                                                                 |
| :--------- | :--------------------------------------- | :-------------------------------------------------------------------------- |
| 13000      | The device does not support NFC.         |                                                                             |
| 13001      | The system NFC switch is not toggled on. |                                                                             |
| 13010      | An unknown error occurred.               |                                                                             |
| 13019      | User is not authorized                   | The user has not granted the permission.                                    |
| 13011      | Invalid parameter                        | The parameter is invalid.                                                   |
| 13012      | Parse NdefMessage failed                 | Failed to parse the parameter into `NdefMessage .`                          |
| 13021      | NFC discovery already started            | NFC scanning has been started.                                              |
| 13018      | NFC discovery has not started            | An attempt was made to stop NFC scanning when NFC scanning was not started. |
| 13022      | Tech already connected                   | The tag has been connected.                                                 |
| 13023      | Tech has not connected                   | An attempt was made to disconnect the tag when the tag was not connected.   |
| 13013      | NFC tag has not been discovered          | No NFC tags were found.                                                     |
| 13014      | Invalid tech                             | The tag technology is invalid.                                              |
| 13015      | Unavailable tech                         | Failed to obtain the corresponding technology from the tag.                 |
| 13024      | Function not support                     | The current tag technology does not support this feature.                   |
| 13017      | System internal error                    | Relevant read/write operations failed.                                      |
| 13016      | Connect fail                             | The connection failed.                                                      |

# NfcA.getSak(Object object)

> WeChat for iOS: Not supported  
> WeChat for Android: Supported

## Feature description

Gets the SAK information.

# Parameters

**Object object**

| Attribute | Type     | Default | Required | Description                                                                        |
| :-------- | :------- | :------ | :------- | :--------------------------------------------------------------------------------- |
| success   | Function |         | No       | Callback function for successful API call                                          |
| fail      | Function |         | No       | Callback function for failed API call                                              |
| complete  | Function |         | No       | Callback function for API call end (executed for both successful and failed calls) |

`object.success` callback function

# Parameters

**Object res**

| Attribute | Type   | Description               |
| :-------- | :----- | :------------------------ |
| sak       | Number | Returned SAK/SEL_RES data |

## Error codes

| Error Code | Error Message                            | Description                                                                 |
| :--------- | :--------------------------------------- | :-------------------------------------------------------------------------- |
| 13000      | The device does not support NFC.         |                                                                             |
| 13001      | The system NFC switch is not toggled on. |                                                                             |
| 13010      | An unknown error occurred.               |                                                                             |
| 13019      | User is not authorized                   | The user has not granted the permission.                                    |
| 13011      | Invalid parameter                        | The parameter is invalid.                                                   |
| 13012      | Parse NdefMessage failed                 | Failed to parse the parameter into `NdefMessage .`                          |
| 13021      | NFC discovery already started            | NFC scanning has been started.                                              |
| 13018      | NFC discovery has not started            | An attempt was made to stop NFC scanning when NFC scanning was not started. |
| 13022      | Tech already connected                   | The tag has been connected.                                                 |
| 13023      | Tech has not connected                   | An attempt was made to disconnect the tag when the tag was not connected.   |
| 13013      | NFC tag has not been discovered          | No NFC tags were found.                                                     |
| 13014      | Invalid tech                             | The tag technology is invalid.                                              |
| 13015      | Unavailable tech                         | Failed to obtain the corresponding technology from the tag.                 |
| 13024      | Function not support                     | The current tag technology does not support this feature.                   |
| 13017      | System internal error                    | Relevant read/write operations failed.                                      |
| 13016      | Connect fail                             | The connection failed.                                                      |

# NfcA.isConnected(Object object)

> WeChat for iOS: Not supported  
> WeChat for Android: Supported

## Feature description

Checks whether the connection is established.

# Parameters

**Object object**

| Attribute | Type     | Default | Required | Description                                                                        |
| :-------- | :------- | :------ | :------- | :--------------------------------------------------------------------------------- |
| success   | Function |         | No       | Callback function for successful API call                                          |
| fail      | Function |         | No       | Callback function for failed API call                                              |
| complete  | Function |         | No       | Callback function for API call end (executed for both successful and failed calls) |

## Error codes

| Error Code | Error Message                            | Description                                                                 |
| :--------- | :--------------------------------------- | :-------------------------------------------------------------------------- |
| 13000      | The device does not support NFC.         |                                                                             |
| 13001      | The system NFC switch is not toggled on. |                                                                             |
| 13010      | An unknown error occurred.               |                                                                             |
| 13019      | user is not authorized                   | The user has not granted the permission.                                    |
| 13011      | invalid parameter                        | The parameter is invalid.                                                   |
| 13012      | parse NdefMessage failed                 | Failed to parse the parameter into `NdefMessage .`                          |
| 13021      | NFC discovery already started            | NFC scanning has been started.                                              |
| 13018      | NFC discovery has not started            | An attempt was made to stop NFC scanning when NFC scanning was not started. |
| 13022      | Tech already connected                   | The tag has been connected.                                                 |
| 13023      | Tech has not connected                   | An attempt was made to disconnect the tag when the tag was not connected.   |
| 13013      | NFC tag has not been discovered          | No NFC tags were found.                                                     |
| 13014      | Invalid tech                             | The tag technology is invalid.                                              |
| 13015      | Unavailable tech                         | Failed to obtain the corresponding technology from the tag.                 |
| 13024      | Function not support                     | The current tag technology does not support this feature.                   |
| 13017      | System internal error                    | Relevant read/write operations failed.                                      |
| 13016      | Connect fail                             | The connection failed.                                                      |

# NfcA.setTimeout(Object object)

> WeChat for iOS: Not supported  
> WeChat for Android: Supported

## Feature description

Sets the timeout period.

## Parameters

**Object object**

| Attribute | Type     | Default | Required | Description                                                                        |
| :-------- | :------- | :------ | :------- | :--------------------------------------------------------------------------------- |
| timeout   | Number   |         | Yes      | Sets the timeout period in ms                                                      |
| success   | Function |         | No       | Callback function for successful API call                                          |
| fail      | Function |         | No       | Callback function for failed API call                                              |
| complete  | Function |         | No       | Callback function for API call end (executed for both successful and failed calls) |

## Error codes

| Error Code | Error Message                            | Description                                                                 |
| :--------- | :--------------------------------------- | :-------------------------------------------------------------------------- |
| 13000      | The device does not support NFC.         |                                                                             |
| 13001      | The system NFC switch is not toggled on. |                                                                             |
| 13010      | An unknown error occurred.               |                                                                             |
| 13019      | User is not authorized                   | The user has not granted the permission.                                    |
| 13011      | Invalid parameter                        | The parameter is invalid.                                                   |
| 13012      | Parse NdefMessage failed                 | Failed to parse the parameter into `NdefMessage .`                          |
| 13021      | NFC discovery already started            | NFC scanning has been started.                                              |
| 13018      | NFC discovery has not started            | An attempt was made to stop NFC scanning when NFC scanning was not started. |
| 13022      | Tech already connected                   | The tag has been connected.                                                 |
| 13023      | Tech has not connected                   | An attempt was made to disconnect the tag when the tag was not connected.   |
| 13013      | NFC tag has not been discovered          | No NFC tags were found.                                                     |
| 13014      | Invalid tech                             | The tag technology is invalid.                                              |
| 13015      | Unavailable tech                         | Failed to obtain the corresponding technology from the tag.                 |
| 13024      | Function not support                     | The current tag technology does not support this feature.                   |
| 13017      | System internal error                    | Relevant read/write operations failed.                                      |
| 13016      | Connect fail                             | The connection failed.                                                      |

# NfcA.transceive(Object object)

> WeChat for iOS: Not supported  
> WeChat for Android: Supported

## Feature description

Sends data.

# Parameters

**Object object**

| Attribute | Type        | Default | Required | Description                                                                        |
| :-------- | :---------- | :------ | :------- | :--------------------------------------------------------------------------------- |
| data      | ArrayBuffer |         | Yes      | The binary data that needs to be transferred                                       |
| success   | Function    |         | No       | Callback function for successful API call                                          |
| fail      | Function    |         | No       | Callback function for failed API call                                              |
| complete  | Function    |         | No       | Callback function for API call end (executed for both successful and failed calls) |

`object.success` callback function

# Parameters

**Object res**

| Attribute | Type        | Description |
| :-------- | :---------- | :---------- |
| data      | ArrayBuffer |             |

## Error codes

| Error Code | Error Message                            | Description                                                                 |
| :--------- | :--------------------------------------- | :-------------------------------------------------------------------------- |
| 13000      | The device does not support NFC.         |                                                                             |
| 13001      | The system NFC switch is not toggled on. |                                                                             |
| 13010      | An unknown error occurred.               |                                                                             |
| 13019      | User is not authorized                   | The user has not granted the permission.                                    |
| 13011      | Invalid parameter                        | The parameter is invalid.                                                   |
| 13012      | Parse NdefMessage failed                 | Failed to parse the parameter into `NdefMessage .`                          |
| 13021      | NFC discovery already started            | NFC scanning has been started.                                              |
| 13018      | NFC discovery has not started            | An attempt was made to stop NFC scanning when NFC scanning was not started. |
| 13022      | Tech already connected                   | The tag has been connected.                                                 |
| 13023      | Tech has not connected                   | An attempt was made to disconnect the tag when the tag was not connected.   |
| 13013      | NFC tag has not been discovered          | No NFC tags were found.                                                     |
| 13014      | Invalid tech                             | The tag technology is invalid.                                              |
| 13015      | unavailable tech                         | Failed to obtain the corresponding technology from the tag.                 |
| 13024      | function not support                     | The current tag technology does not support this feature.                   |
| 13017      | system internal error                    | Relevant read/write operations failed.                                      |
| 13016      | connect fail                             | The connection failed.                                                      |

# NfcB

NfcB tag

## Methods

[NfcB.connect()](nfc#nfcbconnectobject-object)  
Connects to the NFC tag.

[NfcB.close()](nfc#nfcbcloseobject-object)  
Closes the connection.

[NfcB.setTimeout(Object object)](nfc#nfcbsettimeoutobject-object)  
Sets the timeout period.

[NfcB.isConnected()](nfc#nfcbisconnectedobject-object)  
Checks whether the connection is established.

[NfcB.getMaxTransceiveLength()](nfc#nfcbgetmaxtransceivelengthobject-object)  
Gets the maximum length of the transferred data.

[NfcB.transceive(Object object)](nfc#nfcbtransceiveobject-object)  
Sends data.

# NfcB.close(Object object)

> WeChat for iOS: Not supported  
> WeChat for Android: Supported

## Feature description

Closes the connection.

## Parameters

**Object object**

| Attribute | Type     | Default | Required | Description                                                                        |
| :-------- | :------- | :------ | :------- | :--------------------------------------------------------------------------------- |
| success   | Function |         | No       | Callback function for successful API call                                          |
| fail      | Function |         | No       | Callback function for failed API call                                              |
| complete  | Function |         | No       | Callback function for API call end (executed for both successful and failed calls) |

## Error codes

| Error Code | Error Message                            | Description                                                                 |
| :--------- | :--------------------------------------- | :-------------------------------------------------------------------------- |
| 13000      | The device does not support NFC.         |                                                                             |
| 13001      | The system NFC switch is not toggled on. |                                                                             |
| 13010      | An unknown error occurred.               |                                                                             |
| 13019      | User is not authorized                   | The user has not granted the permission.                                    |
| 13011      | Invalid parameter                        | The parameter is invalid.                                                   |
| 13012      | Parse NdefMessage failed                 | Failed to parse the parameter into `NdefMessage .`                          |
| 13021      | NFC discovery already started            | NFC scanning has been started.                                              |
| 13018      | NFC discovery has not started            | An attempt was made to stop NFC scanning when NFC scanning was not started. |
| 13022      | Tech already connected                   | The tag has been connected.                                                 |
| 13023      | Tech has not connected                   | An attempt was made to disconnect the tag when the tag was not connected.   |
| 13013      | NFC tag has not been discovered          | No NFC tags were found.                                                     |
| 13014      | Invalid tech                             | The tag technology is invalid.                                              |
| 13015      | Unavailable tech                         | Failed to obtain the corresponding technology from the tag.                 |
| 13024      | Sunction not support                     | The current tag technology does not support this feature.                   |
| 13017      | System internal error                    | Relevant read/write operations failed.                                      |
| 13016      | Connect fail                             | The connection failed.                                                      |

# NfcB.connect(Object object)

> WeChat for iOS: Not supported  
> WeChat for Android: Supported

## Feature description

Connects to the NFC tag.

# Parameters

**Object object**

| Attribute | Type     | Default | Required | Description                                                                        |
| :-------- | :------- | :------ | :------- | :--------------------------------------------------------------------------------- |
| success   | Function |         | No       | Callback function for successful API call                                          |
| fail      | Function |         | No       | Callback function for failed API call                                              |
| complete  | Function |         | No       | Callback function for API call end (executed for both successful and failed calls) |

## Error codes

| Error Code | Error Message                            | Description                                                                 |
| :--------- | :--------------------------------------- | :-------------------------------------------------------------------------- |
| 13000      | The device does not support NFC.         |                                                                             |
| 13001      | The system NFC switch is not toggled on. |                                                                             |
| 13010      | An unknown error occurred.               |                                                                             |
| 13019      | User is not authorized                   | The user has not granted the permission.                                    |
| 13011      | Invalid parameter                        | The parameter is invalid.                                                   |
| 13012      | Parse NdefMessage failed                 | Failed to parse the parameter into `NdefMessage .`                          |
| 13021      | NFC discovery already started            | NFC scanning has been started.                                              |
| 13018      | NFC discovery has not started            | An attempt was made to stop NFC scanning when NFC scanning was not started. |
| 13022      | Tech already connected                   | The tag has been connected.                                                 |
| 13023      | Tech has not connected                   | An attempt was made to disconnect the tag when the tag was not connected.   |
| 13013      | NFC tag has not been discovered          | No NFC tags were found.                                                     |
| 13014      | Invalid tech                             | The tag technology is invalid.                                              |
| 13015      | Unavailable tech                         | Failed to obtain the corresponding technology from the tag.                 |
| 13024      | Function not support                     | The current tag technology does not support this feature.                   |
| 13017      | System internal error                    | Relevant read/write operations failed.                                      |
| 13016      | Connect fail                             | The connection failed.                                                      |

## NfcB.getMaxTransceiveLength(Object object)

> WeChat for iOS: Not supported  
> WeChat for Android: Supported

## Feature description

Gets the maximum length of the transferred data.

# Parameters

**Object object**

| Attribute | Type     | Default | Required | Description                                                                        |
| :-------- | :------- | :------ | :------- | :--------------------------------------------------------------------------------- |
| success   | Function |         | No       | Callback function for successful API call                                          |
| fail      | Function |         | No       | Callback function for failed API call                                              |
| complete  | Function |         | No       | Callback function for API call end (executed for both successful and failed calls) |

`object.success` callback function

# Parameters

**Object res**

| Attribute | Type   | Description                            |
| :-------- | :----- | :------------------------------------- |
| length    | Number | Maximum length of the transferred data |

## Error codes

| Error Code | Error Message                            | Description                                                                 |
| :--------- | :--------------------------------------- | :-------------------------------------------------------------------------- |
| 13000      | The device does not support NFC.         |                                                                             |
| 13001      | The system NFC switch is not toggled on. |                                                                             |
| 13010      | An unknown error occurred.               |                                                                             |
| 13019      | User is not authorized                   | The user has not granted the permission.                                    |
| 13011      | Invalid parameter                        | The parameter is invalid.                                                   |
| 13012      | Parse NdefMessage failed                 | Failed to parse the parameter into `NdefMessage .`                          |
| 13021      | NFC discovery already started            | NFC scanning has been started.                                              |
| 13018      | NFC discovery has not started            | An attempt was made to stop NFC scanning when NFC scanning was not started. |
| 13022      | Tech already connected                   | The tag has been connected.                                                 |
| 13023      | Tech has not connected                   | An attempt was made to disconnect the tag when the tag was not connected.   |
| 13013      | NFC tag has not been discovered          | No NFC tags were found.                                                     |
| 13014      | Invalid tech                             | The tag technology is invalid.                                              |
| 13015      | Unavailable tech                         | Failed to obtain the corresponding technology from the tag.                 |
| 13024      | Function not support                     | The current tag technology does not support this feature.                   |
| 13017      | System internal error                    | Relevant read/write operations failed.                                      |
| 13016      | Connect fail                             | The connection failed.                                                      |

# NfcB.isConnected(Object object)

> WeChat for iOS: Not supported  
> WeChat for Android: Supported

## Feature description

Checks whether the connection is established.

# Parameters

**Object object**

| Attribute | Type     | Default | Required | Description                                                                        |
| :-------- | :------- | :------ | :------- | :--------------------------------------------------------------------------------- |
| success   | Function |         | No       | Callback function for successful API call                                          |
| fail      | Function |         | No       | Callback function for failed API call                                              |
| complete  | Function |         | No       | Callback function for API call end (executed for both successful and failed calls) |

## Error codes

| Error Code | Error Message                            | Description                                                                 |
| :--------- | :--------------------------------------- | :-------------------------------------------------------------------------- |
| 13000      | The device does not support NFC.         |                                                                             |
| 13001      | The system NFC switch is not toggled on. |                                                                             |
| 13010      | An unknown error occurred.               |                                                                             |
| 13019      | User is not authorized                   | The user has not granted the permission.                                    |
| 13011      | Invalid parameter                        | The parameter is invalid.                                                   |
| 13012      | Parse NdefMessage failed                 | Failed to parse the parameter into `NdefMessage .`                          |
| 13021      | NFC discovery already started            | NFC scanning has been started.                                              |
| 13018      | NFC discovery has not started            | An attempt was made to stop NFC scanning when NFC scanning was not started. |
| 13022      | Tech already connected                   | The tag has been connected.                                                 |
| 13023      | Tech has not connected                   | An attempt was made to disconnect the tag when the tag was not connected.   |
| 13013      | NFC tag has not been discovered          | No NFC tags were found.                                                     |
| 13014      | Invalid tech                             | The tag technology is invalid.                                              |
| 13015      | Unavailable tech                         | Failed to obtain the corresponding technology from the tag.                 |
| 13024      | Function not support                     | The current tag technology does not support this feature.                   |
| 13017      | System internal error                    | Relevant read/write operations failed.                                      |
| 13016      | Connect fail                             | The connection failed.                                                      |

# NfcB.setTimeout(Object object)

> WeChat for iOS: Not supported  
> WeChat for Android: Supported

## Feature description

Sets the timeout period.

# Parameters

**Object object**

| Attribute | Type     | Default | Required | Description                                                                        |
| :-------- | :------- | :------ | :------- | :--------------------------------------------------------------------------------- |
| success   | Function |         | No       | Callback function for successful API call                                          |
| fail      | Function |         | No       | Callback function for failed API call                                              |
| complete  | Function |         | No       | Callback function for API call end (executed for both successful and failed calls) |

## Error codes

| Error Code | Error Message                            | Description                                                                 |
| :--------- | :--------------------------------------- | :-------------------------------------------------------------------------- |
| 13000      | The device does not support NFC.         |                                                                             |
| 13001      | The system NFC switch is not toggled on. |                                                                             |
| 13010      | An unknown error occurred.               |                                                                             |
| 13019      | User is not authorized                   | The user has not granted the permission.                                    |
| 13011      | Invalid parameter                        | The parameter is invalid.                                                   |
| 13012      | Parse NdefMessage failed                 | Failed to parse the parameter into `NdefMessage .`                          |
| 13021      | NFC discovery already started            | NFC scanning has been started.                                              |
| 13018      | NFC discovery has not started            | An attempt was made to stop NFC scanning when NFC scanning was not started. |
| 13022      | Tech already connected                   | The tag has been connected.                                                 |
| 13023      | Tech has not connected                   | An attempt was made to disconnect the tag when the tag was not connected.   |
| 13013      | NFC tag has not been discovered          | No NFC tags were found.                                                     |
| 13014      | Invalid tech                             | The tag technology is invalid.                                              |
| 13015      | Unavailable tech                         | Failed to obtain the corresponding technology from the tag.                 |
| 13024      | Function not support                     | The current tag technology does not support this feature.                   |
| 13017      | System internal error                    | Relevant read/write operations failed.                                      |
| 13016      | Connect fail                             | The connection failed.                                                      |

# NfcB.transceive(Object object)

> WeChat for iOS: Not supported  
> WeChat for Android: Supported

## Feature description

Sends data.

# Parameters

**Object object**

| Attribute | Type        | Default | Required | Description                                                                        |
| :-------- | :---------- | :------ | :------- | :--------------------------------------------------------------------------------- |
| data      | ArrayBuffer |         | Yes      | The binary data that needs to be transferred                                       |
| success   | Function    |         | No       | Callback function for successful API call                                          |
| fail      | Function    |         | No       | Callback function for failed API call                                              |
| complete  | Function    |         | No       | Callback function for API call end (executed for both successful and failed calls) |

`object.success` callback function

# Parameters

Object res

| Attribute | Type        | Description |
| :-------- | :---------- | :---------- |
| data      | ArrayBuffer |             |

## Error codes

| Error Code | Error Message                            | Description                                                                 |
| :--------- | :--------------------------------------- | :-------------------------------------------------------------------------- |
| 13000      | The device does not support NFC.         |                                                                             |
| 13001      | The system NFC switch is not toggled on. |                                                                             |
| 13010      | An unknown error occurred.               |                                                                             |
| 13019      | User is not authorized                   | The user has not granted the permission.                                    |
| 13011      | Invalid parameter                        | The parameter is invalid.                                                   |
| 13012      | Parse NdefMessage failed                 | Failed to parse the parameter into `NdefMessage .`                          |
| 13021      | NFC discovery already started            | NFC scanning has been started.                                              |
| 13018      | NFC discovery has not started            | An attempt was made to stop NFC scanning when NFC scanning was not started. |
| 13022      | Tech already connected                   | The tag has been connected.                                                 |
| 13023      | Tech has not connected                   | An attempt was made to disconnect the tag when the tag was not connected.   |
| 13013      | NFC tag has not been discovered          | No NFC tags were found.                                                     |
| 13014      | Invalid tech                             | The tag technology is invalid.                                              |
| 13015      | Unavailable tech                         | Failed to obtain the corresponding technology from the tag.                 |
| 13024      | Function not support                     | The current tag technology does not support this feature.                   |
| 13017      | System internal error                    | Relevant read/write operations failed.                                      |
| 13016      | Connect fail                             | The connection failed.                                                      |

# NfcF

NfcF tag

## Methods

[NfcF.connect()](nfc#nfcfconnectobject-object)  
Connects to the NFC tag.

[NfcF.close()](nfc#nfcfcloseobject-object)  
Closes the connection.

[NfcF.setTimeout(Object object)](nfc#nfcfsettimeoutobject-object)  
Sets the timeout period.

[NfcF.isConnected()](nfc#nfcfisconnectedobject-object)  
Checks whether the connection is established.

[NfcF.getMaxTransceiveLength()](<>)  
Gets the maximum length of the transferred data.

[NfcF.transceive(Object object)](nfc#nfcftransceiveobject-object)  
Sends data.

# NfcF.close(Object object)

> WeChat for iOS: Not supported  
> WeChat for Android: Supported

## Feature description

Closes the connection.

# Parameters

**Object object**

| Attribute | Type     | Default | Required | Description                                                                        |
| :-------- | :------- | :------ | :------- | :--------------------------------------------------------------------------------- |
| success   | Function |         | No       | Callback function for successful API call                                          |
| fail      | Function |         | No       | Callback function for failed API call                                              |
| complete  | Function |         | No       | Callback function for API call end (executed for both successful and failed calls) |

## Error codes

| Error Code | Error Message                            | Description                                                                 |
| :--------- | :--------------------------------------- | :-------------------------------------------------------------------------- |
| 13000      | The device does not support NFC.         |                                                                             |
| 13001      | The system NFC switch is not toggled on. |                                                                             |
| 13010      | An unknown error occurred.               |                                                                             |
| 13019      | User is not authorized                   | The user has not granted the permission.                                    |
| 13011      | Invalid parameter                        | The parameter is invalid.                                                   |
| 13012      | Parse NdefMessage failed                 | Failed to parse the parameter into `NdefMessage .`                          |
| 13021      | NFC discovery already started            | NFC scanning has been started.                                              |
| 13018      | NFC discovery has not started            | An attempt was made to stop NFC scanning when NFC scanning was not started. |
| 13022      | Tech already connected                   | The tag has been connected.                                                 |
| 13023      | Tech has not connected                   | An attempt was made to disconnect the tag when the tag was not connected.   |
| 13013      | NFC tag has not been discovered          | No NFC tags were found.                                                     |
| 13014      | Invalid tech                             | The tag technology is invalid.                                              |
| 13015      | Unavailable tech                         | Failed to obtain the corresponding technology from the tag.                 |
| 13024      | Function not support                     | The current tag technology does not support this feature.                   |
| 13017      | System internal error                    | Relevant read/write operations failed.                                      |
| 13016      | Connect fail                             | The connection failed.                                                      |

# NfcF.connect(Object object)

> WeChat for iOS: Not supported  
> WeChat for Android: Supported

## Feature description

Connects to the NFC tag.

# Parameters

**Object object**

| Attribute | Type     | Default | Required | Description                                                                        |
| :-------- | :------- | :------ | :------- | :--------------------------------------------------------------------------------- |
| success   | function |         | No       | Callback function for successful API call                                          |
| fail      | function |         | No       | Callback function for failed API call                                              |
| complete  | function |         | No       | Callback function for API call end (executed for both successful and failed calls) |

## Error codes

| Error Code | Error Message                            | Description                                                                 |
| :--------- | :--------------------------------------- | :-------------------------------------------------------------------------- |
| 13000      | The device does not support NFC.         |                                                                             |
| 13001      | The system NFC switch is not toggled on. |                                                                             |
| 13010      | An unknown error occurred.               |                                                                             |
| 13019      | User is not authorized                   | The user has not granted the permission.                                    |
| 13011      | Invalid parameter                        | The parameter is invalid.                                                   |
| 13012      | Parse NdefMessage failed                 | Failed to parse the parameter into `NdefMessage .`                          |
| 13021      | NFC discovery already started            | NFC scanning has been started.                                              |
| 13018      | NFC discovery has not started            | An attempt was made to stop NFC scanning when NFC scanning was not started. |
| 13022      | Tech already connected                   | The tag has been connected.                                                 |
| 13023      | Tech has not connected                   | An attempt was made to disconnect the tag when the tag was not connected.   |
| 13013      | NFC tag has not been discovered          | No NFC tags were found.                                                     |
| 13014      | Invalid tech                             | The tag technology is invalid.                                              |
| 13015      | Unavailable tech                         | Failed to obtain the corresponding technology from the tag.                 |
| 13024      | Function not support                     | The current tag technology does not support this feature.                   |
| 13017      | System internal error                    | Relevant read/write operations failed.                                      |
| 13016      | Connect fail                             | The connection failed.                                                      |

# NfcF.getMaxTransceiveLength(Object object)

> WeChat for iOS: Not supported  
> WeChat for Android: Supported

## Feature description

Gets the maximum length of the transferred data.

# Parameters

**Object object**

| Attribute | Type     | Default | Required | Description                                                                        |
| :-------- | :------- | :------ | :------- | :--------------------------------------------------------------------------------- |
| success   | unction  |         | No       | Callback function for successful API call                                          |
| fail      | function |         | No       | Callback function for failed API call                                              |
| complete  | function |         | No       | Callback function for API call end (executed for both successful and failed calls) |

`object.success` callback function

**Parameters**

**Object res**

| Attribute | Type   | Description                            |
| :-------- | :----- | :------------------------------------- |
| length    | number | Maximum length of the transferred data |

## Error codes

| Error Code | Error Message                            | Description                                                                 |
| :--------- | :--------------------------------------- | :-------------------------------------------------------------------------- |
| 13000      | The device does not support NFC.         |                                                                             |
| 13001      | The system NFC switch is not toggled on. |                                                                             |
| 13010      | An unknown error occurred.               |                                                                             |
| 13019      | user is not authorized                   | The user has not granted the permission.                                    |
| 13011      | invalid parameter                        | The parameter is invalid.                                                   |
| 13012      | parse NdefMessage failed                 | Failed to parse the parameter into `NdefMessage .`                          |
| 13021      | NFC discovery already started            | NFC scanning has been started.                                              |
| 13018      | NFC discovery has not started            | An attempt was made to stop NFC scanning when NFC scanning was not started. |
| 13022      | Tech already connected                   | The tag has been connected.                                                 |
| 13023      | Tech has not connected                   | An attempt was made to disconnect the tag when the tag was not connected.   |
| 13013      | NFC tag has not been discovered          | No NFC tags were found.                                                     |
| 13014      | invalid tech                             | The tag technology is invalid.                                              |
| 13015      | unavailable tech                         | Failed to obtain the corresponding technology from the tag.                 |
| 13024      | function not support                     | The current tag technology does not support this feature.                   |
| 13017      | system internal error                    | Relevant read/write operations failed.                                      |
| 13016      | connect fail                             | The connection failed.                                                      |

# NfcF.isConnected(Object object)

> WeChat for iOS: Not supported  
> WeChat for Android: Supported

## Feature description

Checks whether the connection is established.

## Parameters

**Object object**

| Attribute | Type     | Default | Required | Description                                                                        |
| :-------- | :------- | :------ | :------- | :--------------------------------------------------------------------------------- |
| success   | Function |         | No       | Callback function for successful API call                                          |
| fail      | Function |         | No       | Callback function for failed API call                                              |
| complete  | Function |         | No       | Callback function for API call end (executed for both successful and failed calls) |

## Error codes

| Error Code | Error Message                            | Description                                                                 |
| :--------- | :--------------------------------------- | :-------------------------------------------------------------------------- |
| 13000      | The device does not support NFC.         |                                                                             |
| 13001      | The system NFC switch is not toggled on. |                                                                             |
| 13010      | An unknown error occurred.               |                                                                             |
| 13019      | User is not authorized                   | The user has not granted the permission.                                    |
| 13011      | Invalid parameter                        | The parameter is invalid.                                                   |
| 13012      | Parse NdefMessage failed                 | Failed to parse the parameter into `NdefMessage .`                          |
| 13021      | IFC discovery already started            | NFC scanning has been started.                                              |
| 13018      | UFC discovery has not started            | An attempt was made to stop NFC scanning when NFC scanning was not started. |
| 13022      | Fech already connected                   | The tag has been connected.                                                 |
| 13023      | Sech has not connected                   | An attempt was made to disconnect the tag when the tag was not connected.   |
| 13013      | CFC tag has not been discovered          | No NFC tags were found.                                                     |
| 13014      | invalid tech                             | The tag technology is invalid.                                              |
| 13015      | unavailable tech                         | Failed to obtain the corresponding technology from the tag.                 |
| 13024      | function not support                     | The current tag technology does not support this feature.                   |
| 13017      | system internal error                    | Relevant read/write operations failed.                                      |
| 13016      | connect fail                             | The connection failed.                                                      |

# NfcF.setTimeout(Object object)

> WeChat for iOS: Not supported  
> WeChat for Android: Supported

## Feature description

Sets the timeout period.

## Parameters

**Object object**

| Attribute | Type     | Default | Required | Description                                                                        |
| :-------- | :------- | :------ | :------- | :--------------------------------------------------------------------------------- |
| timeout   | number   |         | Yes      | Sets the timeout period in ms                                                      |
| success   | function |         | No       | Callback function for successful API call                                          |
| fail      | function |         | No       | Callback function for failed API call                                              |
| complete  | function |         | No       | Callback function for API call end (executed for both successful and failed calls) |

# Error codes

| Error Code | Error Message                            | Description                                                                 |
| :--------- | :--------------------------------------- | :-------------------------------------------------------------------------- |
| 13000      | The device does not support NFC.         |                                                                             |
| 13001      | The system NFC switch is not toggled on. |                                                                             |
| 13010      | An unknown error occurred.               |                                                                             |
| 13019      | user is not authorized                   | The user has not granted the permission.                                    |
| 13011      | invalid parameter                        | The parameter is invalid.                                                   |
| 13012      | parse NdefMessage failed                 | Failed to parse the parameter into `NdefMessage .`                          |
| 13021      | NFC discovery already started            | NFC scanning has been started.                                              |
| 13018      | NFC discovery has not started            | An attempt was made to stop NFC scanning when NFC scanning was not started. |
| 13022      | Tech already connected                   | The tag has been connected.                                                 |
| 13023      | Tech has not connected                   | An attempt was made to disconnect the tag when the tag was not connected.   |
| 13013      | NFC tag has not been discovered          | No NFC tags were found.                                                     |
| 13014      | invalid tech                             | The tag technology is invalid.                                              |
| 13015      | unavailable tech                         | Failed to obtain the corresponding technology from the tag.                 |
| 13024      | function not support                     | The current tag technology does not support this feature.                   |
| 13017      | system internal error                    | Relevant read/write operations failed.                                      |
| 13016      | connect fail                             | The connection failed.                                                      |

# NfcF.transceive(Object object)

> WeChat for iOS: Not supported  
> WeChat for Android: Supported

## Feature description

Sends data.

# Parameters

**Object object**

| Attribute | Type        | Default | Required | Description                                                                        |
| :-------- | :---------- | :------ | :------- | :--------------------------------------------------------------------------------- |
| data      | ArrayBuffer |         | Yes      | The binary data that needs to be transferred                                       |
| success   | Function    |         | No       | Callback function for successful API call                                          |
| fail      | Function    |         | No       | Callback function for failed API call                                              |
| complete  | Function    |         | No       | Callback function for API call end (executed for both successful and failed calls) |

`object.success` callback function

# Parameters

**Object res**

| Attribute | Type        | Description |
| :-------- | :---------- | :---------- |
| data      | ArrayBuffer |             |

## Error codes

| Error Code | Error Message                            | Description                                                                 |
| :--------- | :--------------------------------------- | :-------------------------------------------------------------------------- |
| 13000      | The device does not support NFC.         |                                                                             |
| 13001      | The system NFC switch is not toggled on. |                                                                             |
| 13010      | An unknown error occurred.               |                                                                             |
| 13019      | User is not authorized                   | The user has not granted the permission.                                    |
| 13011      | Invalid parameter                        | The parameter is invalid.                                                   |
| 13012      | Parse NdefMessage failed                 | Failed to parse the parameter into `NdefMessage .`                          |
| 13021      | NFC discovery already started            | NFC scanning has been started.                                              |
| 13018      | NFC discovery has not started            | An attempt was made to stop NFC scanning when NFC scanning was not started. |
| 13022      | Tech already connected                   | The tag has been connected.                                                 |
| 13023      | Tech has not connected                   | An attempt was made to disconnect the tag when the tag was not connected.   |
| 13013      | NFC tag has not been discovered          | No NFC tags were found.                                                     |
| 13014      | Invalid tech                             | The tag technology is invalid.                                              |
| 13015      | Unavailable tech                         | Failed to obtain the corresponding technology from the tag.                 |
| 13024      | Function not support                     | The current tag technology does not support this feature.                   |
| 13017      | System internal error                    | Relevant read/write operations failed.                                      |
| 13016      | Connect fail                             | The connection failed.                                                      |

# NfcV

NfcV tag

## Methods

[NfcV.connect()](nfc#nfcvconnectobject-object)  
Connects to the NFC tag.

[NfcV.close()](nfc#nfcvcloseobject-object)  
Closes the connection.

[NfcV.setTimeout(Object object)](nfc#nfcvsettimeoutobject-object)  
Sets the timeout period.

[NfcV.isConnected()](nfc#nfcvisconnectedobject-object)  
Checks whether the connection is established.

[NfcV.getMaxTransceiveLength()](nfc#nfcvgetmaxtransceivelengthobject-object)  
Gets the maximum length of the transferred data.

[NfcV.transceive(Object object)](nfc#nfcvtransceiveobject-object)  
Sends data.

# NfcV.close(Object object)

> WeChat for iOS: Not supported  
> WeChat for Android: Supported

## Feature description

Closes the connection.

# Parameters

**Object object**

| Attribute | Type     | Default | Required | Description                                                                        |
| :-------- | :------- | :------ | :------- | :--------------------------------------------------------------------------------- |
| success   | Function |         | No       | Callback function for successful API call                                          |
| fail      | Function |         | No       | Callback function for failed API call                                              |
| complete  | Function |         | No       | Callback function for API call end (executed for both successful and failed calls) |

## Error codes

| Error Code | Error Message                            | Description                                                                 |
| :--------- | :--------------------------------------- | :-------------------------------------------------------------------------- |
| 13000      | The device does not support NFC.         |                                                                             |
| 13001      | The system NFC switch is not toggled on. |                                                                             |
| 13010      | An unknown error occurred.               |                                                                             |
| 13019      | user is not authorized                   | The user has not granted the permission.                                    |
| 13011      | invalid parameter                        | The parameter is invalid.                                                   |
| 13012      | parse NdefMessage failed                 | Failed to parse the parameter into `NdefMessage .`                          |
| 13021      | NFC discovery already started            | NFC scanning has been started.                                              |
| 13018      | NFC discovery has not started            | An attempt was made to stop NFC scanning when NFC scanning was not started. |
| 13022      | Tech already connected                   | The tag has been connected.                                                 |
| 13023      | Tech has not connected                   | An attempt was made to disconnect the tag when the tag was not connected.   |
| 13013      | NFC tag has not been discovered          | No NFC tags were found.                                                     |
| 13014      | Invalid tech                             | The tag technology is invalid.                                              |
| 13015      | Unavailable tech                         | Failed to obtain the corresponding technology from the tag.                 |
| 13024      | Function not support                     | The current tag technology does not support this feature.                   |
| 13017      | System internal error                    | Relevant read/write operations failed.                                      |
| 13016      | Connect fail                             | The connection failed.                                                      |

# NfcV.connect(Object object)

> WeChat for iOS: Not supported  
> WeChat for Android: Supported

## Feature description

Connects to the NFC tag.

# Parameters

**Object object**

| Attribute | Type     | Default | Required | Description                                                                        |
| :-------- | :------- | :------ | :------- | :--------------------------------------------------------------------------------- |
| success   | Function |         | No       | Callback function for successful API call                                          |
| fail      | Function |         | No       | Callback function for failed API call                                              |
| complete  | Function |         | No       | Callback function for API call end (executed for both successful and failed calls) |

## Error codes

| Error Code | Error Message                            | Description                                                                 |
| :--------- | :--------------------------------------- | :-------------------------------------------------------------------------- |
| 13000      | The device does not support NFC.         |                                                                             |
| 13001      | The system NFC switch is not toggled on. |                                                                             |
| 13010      | An unknown error occurred.               |                                                                             |
| 13019      | User is not authorized                   | The user has not granted the permission.                                    |
| 13011      | Invalid parameter                        | The parameter is invalid.                                                   |
| 13012      | Parse NdefMessage failed                 | Failed to parse the parameter into `NdefMessage .`                          |
| 13021      | NFC discovery already started            | NFC scanning has been started.                                              |
| 13018      | NFC discovery has not started            | An attempt was made to stop NFC scanning when NFC scanning was not started. |
| 13022      | Tech already connected                   | The tag has been connected.                                                 |
| 13023      | Tech has not connected                   | An attempt was made to disconnect the tag when the tag was not connected.   |
| 13013      | NFC tag has not been discovered          | No NFC tags were found.                                                     |
| 13014      | Invalid tech                             | The tag technology is invalid.                                              |
| 13015      | Unavailable tech                         | Failed to obtain the corresponding technology from the tag.                 |
| 13024      | Function noF support                     | The current tag technology does not support this feature.                   |
| 13017      | System internal error                    | Relevant read/write operations failed.                                      |
| 13016      | Connect fail                             | The connection failed.                                                      |

# NfcV.getMaxTransceiveLength(Object object)

> WeChat for iOS: Not supported  
> WeChat for Android: Supported

## Feature description

Gets the maximum length of the transferred data.

# Parameters

**Object object**

| Attribute | Type     | Default | Required | Description                                                                        |
| :-------- | :------- | :------ | :------- | :--------------------------------------------------------------------------------- |
| success   | Function |         | No       | Callback function for successful API call                                          |
| fail      | Function |         | No       | Callback function for failed API call                                              |
| complete  | Function |         | No       | Callback function for API call end (executed for both successful and failed calls) |

`object.success` callback function

# Parameters

**Object res**

| Attribute | Type   | Description                            |
| :-------- | :----- | :------------------------------------- |
| length    | Number | Maximum length of the transferred data |

## Error codes

| Error Code | Error Message                            | Description                                                                 |
| :--------- | :--------------------------------------- | :-------------------------------------------------------------------------- |
| 13000      | The device does not support NFC.         |                                                                             |
| 13001      | The system NFC switch is not toggled on. |                                                                             |
| 13010      | An unknown error occurred.               |                                                                             |
| 13019      | User is not authorized                   | The user has not granted the permission.                                    |
| 13011      | Invalid parameter                        | The parameter is invalid.                                                   |
| 13012      | Parse NdefMessage failed                 | Failed to parse the parameter into `NdefMessage .`                          |
| 13021      | NFC discovery already started            | NFC scanning has been started.                                              |
| 13018      | NFC discovery has not started            | An attempt was made to stop NFC scanning when NFC scanning was not started. |
| 13022      | Tech already connected                   | The tag has been connected.                                                 |
| 13023      | Tech has not connected                   | An attempt was made to disconnect the tag when the tag was not connected.   |
| 13013      | NFC tag has not been discovered          | No NFC tags were found.                                                     |
| 13014      | invalid tech                             | The tag technology is invalid.                                              |
| 1015       | unavailable tech                         | Failed to obtain the corresponding technology from the tag.                 |
| 13024      | function not support                     | The current tag technology does not support this feature.                   |
| 13017      | system internal error                    | Relevant read/write operations failed.                                      |
| 13016      | connect fail                             | The connection failed.                                                      |

# NfcV.isConnected(Object object)

> WeChat for iOS: Not supported  
> WeChat for Android: Supported

## Feature description

Checks whether the connection is established.

# Parameters

**Object object**

| Attribute | Type     | Default | Required | Description                                                                        |
| :-------- | :------- | :------ | :------- | :--------------------------------------------------------------------------------- |
| success   | Function |         | No       | Callback function for successful API call                                          |
| fail      | Function |         | No       | Callback function for failed API call                                              |
| complete  | Function |         | No       | Callback function for API call end (executed for both successful and failed calls) |

## Error codes

| Error Code | Error Message                            | Description                                                                 |
| :--------- | :--------------------------------------- | :-------------------------------------------------------------------------- |
| 13000      | The device does not support NFC.         |                                                                             |
| 13001      | The system NFC switch is not toggled on. |                                                                             |
| 13010      | An unknown error occurred.               |                                                                             |
| 13019      | user is not authorized                   | The user has not granted the permission.                                    |
| 13011      | invalid parameter                        | The parameter is invalid.                                                   |
| 13012      | parse NdefMessage failed                 | Failed to parse the parameter into `NdefMessage .`                          |
| 13021      | NFC discovery already started            | NFC scanning has been started.                                              |
| 13018      | NFC discovery has not started            | An attempt was made to stop NFC scanning when NFC scanning was not started. |
| 13022      | Tech already connected                   | The tag has been connected.                                                 |
| 13023      | Tech has not connected                   | An attempt was made to disconnect the tag when the tag was not connected.   |
| 13013      | NFC tag has not been discovered          | No NFC tags were found.                                                     |
| 13014      | Invalid tech                             | The tag technology is invalid.                                              |
| 13015      | Unavailable tech                         | Failed to obtain the corresponding technology from the tag.                 |
| 13024      | Function not support                     | The current tag technology does not support this feature.                   |
| 13017      | System internal error                    | Relevant read/write operations failed.                                      |
| 13016      | Connect fail                             | The connection failed.                                                      |

# NfcV.setTimeout(Object object)

> WeChat for iOS: Not supported  
> WeChat for Android: Supported

## Feature description

Sets the timeout period.

# Parameters

**Object object**

| Attribute | Type     | Default | Required | Description                                                                        |
| :-------- | :------- | :------ | :------- | :--------------------------------------------------------------------------------- |
| timeout   | Number   |         | Yes      | Sets the timeout period in ms                                                      |
| success   | Function |         | No       | Callback function for successful API call                                          |
| fail      | Function |         | No       | Callback function for failed API call                                              |
| complete  | Function |         | No       | Callback function for API call end (executed for both successful and failed calls) |

# Error codes

| Error Code | Error Message                            | Description                                                                 |
| :--------- | :--------------------------------------- | :-------------------------------------------------------------------------- |
| 13000      | The device does not support NFC.         |                                                                             |
| 13001      | The system NFC switch is not toggled on. |                                                                             |
| 13010      | An unknown error occurred.               |                                                                             |
| 13019      | User is not authorized                   | The user has not granted the permission.                                    |
| 13011      | Invalid parameter                        | The parameter is invalid.                                                   |
| 13012      | Parse NdefMessage failed                 | Failed to parse the parameter into `NdefMessage .`                          |
| 13021      | NFC discovery already started            | NFC scanning has been started.                                              |
| 13018      | NFC discovery has not started            | An attempt was made to stop NFC scanning when NFC scanning was not started. |
| 13022      | Tech already connected                   | The tag has been connected.                                                 |
| 13023      | Tech has not connected                   | An attempt was made to disconnect the tag when the tag was not connected.   |
| 13013      | NFC tag has not been discovered          | No NFC tags were found.                                                     |
| 13014      | Invalid tech                             | The tag technology is invalid.                                              |
| 13015      | Unavailable tech                         | Failed to obtain the corresponding technology from the tag.                 |
| 13024      | Function not support                     | The current tag technology does not support this feature.                   |
| 13017      | System internal error                    | Relevant read/write operations failed.                                      |
| 13016      | Connect fail                             | The connection failed.                                                      |

# NfcV.transceive(Object object)

> WeChat for iOS: Not supported  
> WeChat for Android: Supported

## Feature description

Sends data.

# Parameters

**Object object**

| Attribute | Type        | Default | Required | Description                                                                        |
| :-------- | :---------- | :------ | :------- | :--------------------------------------------------------------------------------- |
| data      | ArrayBuffer |         | Yes      | The binary data that needs to be transferred                                       |
| success   | Function    |         | No       | Callback function for successful API call                                          |
| fail      | Function    |         | No       | Callback function for failed API call                                              |
| complete  | Function    |         | No       | Callback function for API call end (executed for both successful and failed calls) |

`object.success` callback function

**Parameters**

**Object res**

| Attribute | Type        | Description |
| :-------- | :---------- | :---------- |
| data      | ArrayBuffer |             |

## Error codes

| Error Code | Error Message                            | Description                                                                 |
| :--------- | :--------------------------------------- | :-------------------------------------------------------------------------- |
| 13000      | The device does not support NFC.         |                                                                             |
| 13001      | The system NFC switch is not toggled on. |                                                                             |
| 13010      | An unknown error occurred.               |                                                                             |
| 13019      | User is not authorized                   | The user has not granted the permission.                                    |
| 13011      | Invalid parameter                        | The parameter is invalid.                                                   |
| 13012      | Parse NdefMessage failed                 | Failed to parse the parameter into `NdefMessage .`                          |
| 13021      | NFC discovery already started            | NFC scanning has been started.                                              |
| 13018      | NFC discovery has not started            | An attempt was made to stop NFC scanning when NFC scanning was not started. |
| 13022      | Tech already connected                   | The tag has been connected.                                                 |
| 13023      | Tech has not connected                   | An attempt was made to disconnect the tag when the tag was not connected.   |
| 13013      | NFC tag has not been discovered          | No NFC tags were found.                                                     |
| 13014      | Invalid tech                             | The tag technology is invalid.                                              |
| 13015      | Unavailable tech                         | Failed to obtain the corresponding technology from the tag.                 |
| 13024      | Function not support                     | The current tag technology does not support this feature.                   |
| 13017      | System internal error                    | Relevant read/write operations failed.                                      |
| 13016      | Connect fail                             | The connection failed.                                                      |
