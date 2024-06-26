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
---
# NFC 
This section consists of the list of all NFC APIs.
*** 
- [getNFCAdapter](doc:nfc#nfcadapter-wxgetnfcadapter) 
- [NFCAdapter](doc:nfc#nfcadapter)
- [IsoDep](doc:nfc#isodep-nfcadaptergetisodep)
- [MifareClassic](doc:nfc#mifareclassic-nfcadaptergetmifareclassic)
- [MifareUltralight](doc:nfc#mifareultralight-nfcadaptergetmifareultralight)
- [Ndef](doc:nfc#ndef-nfcadaptergetndef)
- [NfcA](doc:nfc#nfca-nfcadaptergetnfca)
- [NfcB](doc:nfc#nfcb-nfcadaptergetnfcb)
- [NfcF](doc:nfc#nfcf-nfcadaptergetnfcf)
- [NfcV](doc:nfc#nfcv-nfcadaptergetnfcv)

# NFCAdapter wx.getNFCAdapter()

> Support:  
> Android: Supported  
> iOS: Not supported

## Feature description

Gets the NFC instance.

## Returned value

[NFCAdapter](doc:nfc#nfcadapter)

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

[NFCAdapter.startDiscovery()](doc:nfc#nfcadapterstartdiscoveryobject-object)  
[NFCAdapter.stopDiscovery()](doc:nfc#nfcadapterstopdiscoveryobject-object)  
[Ndef NFCAdapter.getNdef()](doc:nfc#ndef-nfcadaptergetndef)  
Gets the Ndef instance, which can read and write the NDEF data on NFC tags in NDEF format.

[NfcA NFCAdapter.getNfcA()](doc:nfc#nfca-nfcadaptergetnfca)  
Gets the NfcA instance, which can read and write data on tags in NFC-A (ISO 14443-3A) standard.

[NfcB NFCAdapter.getNfcB()](doc:nfc#nfcb-nfcadaptergetnfcb)  
431  
Gets the NfcB instance, which can read and write data on tags in NFC-B (ISO 14443-3B) standard.

[IsoDep NFCAdapter.getIsoDep()](doc:nfc#isodep-nfcadaptergetisodep)  
Gets the IsoDep instance, which can read and write data on tags in ISO-DEP (ISO 14443-4) standard.

[NfcF NFCAdapter.getNfcF()](doc:nfc#nfcf-nfcadaptergetnfcf)  
Gets the NfcF instance, which can read and write data on tags in NFC-F (JIS 6319-4) standard.

[NfcV NFCAdapter.getNfcV()](doc:nfc#nfcv-nfcadaptergetnfcv)  
Gets the NfcV instance, which can read and write data on tags in NFC-V (ISO 15693) standard.

[MifareClassic NFCAdapter.getMifareClassic()](doc:nfc#mifareclassic-nfcadaptergetmifareclassic)  
Gets the MifareClassic instance, which can read and write data on MIFARE Classic tags.

[MifareUltralight NFCAdapter.getMifareUltralight()](doc:nfc#mifareultralight-nfcadaptergetmifareultralight)  
Gets the MifareUltralight instance, which can read and write data on MIFARE Ultralight tags.

[NFCAdapter.onDiscovered(function listener)](doc:nfc#nfcadapterondiscoveredfunction-listener)  
Listens for NFC tags.

[NFCAdapter.offDiscovered(function listener)](doc:nfc#nfcadapteroffdiscoveredfunction-listener)  
Unlistens for NFC tags.

# [IsoDep](doc:nfc#isodep-nfcadaptergetisodep) NFCAdapter.getIsoDep()

## Feature description

Gets the `IsoDep` instance, which can read and write data on tags in ISO-DEP (ISO 14443-4) standard.

## Returned value

### [IsoDep](doc:nfc#isodep-nfcadaptergetisodep)

# [MifareClassic](doc:nfc#mifareclassic-nfcadaptergetmifareclassic) NFCAdapter.getMifareClassic()

## Feature description

Gets the `MifareClassic` instance, which can read and write data on MIFARE Classic tags.

## Returned value

### [MifareClassic](doc:nfc#mifareclassic-nfcadaptergetmifareclassic)

# [MifareUltralight](doc:nfc#mifareultralight-nfcadaptergetmifareultralight) NFCAdapter.getMifareUltralight()

## Feature description

Gets the `MifareUltralight` instance, which can read and write data on MIFARE Ultralight tags.

## Returned value

### [MifareUltralight](doc:nfc#mifareultralight-nfcadaptergetmifareultralight)

# [Ndef](doc:nfc#ndef-nfcadaptergetndef) NFCAdapter.getNdef()

## Feature description

Gets the `Ndef `instance, which can read and write the NDEF data on NFC tags in NDEF format.

## Returned value

### [Ndef](doc:nfc#ndef-nfcadaptergetndef)

# [NfcA](doc:nfc#nfca-nfcadaptergetnfca) NFCAdapter.getNfcA()

## Feature description

Gets the [NfcA](doc:nfc#nfca-nfcadaptergetnfca) instance, which can read and write data on tags in NFC-A (ISO 14443-3A) standard.

## Returned value

### [NfcA](doc:nfc#nfca-nfcadaptergetnfca)

# [NfcB](doc:nfc#nfcb-nfcadaptergetnfcb) NFCAdapter.getNfcB()

## Feature description

Gets the `NfcB` instance, which can read and write data on tags in NFC-B (ISO 14443-3B) standard.

## Returned value

### [NfcB](doc:nfc#nfcb-nfcadaptergetnfcb)

# [NfcF](doc:nfc#nfcf-nfcadaptergetnfcf) NFCAdapter.getNfcF()

## Feature description

Gets the NfcF instance, which can read and write data on tags in NFC-F (JIS 6319-4) standard.

## Returned value

### [NfcF](doc:nfc#nfcf-nfcadaptergetnfcf)

# [NfcV](doc:nfc#nfcv-nfcadaptergetnfcv) NFCAdapter.getNfcV()

## Feature description

Gets the `NfcV` instance, which can read and write data on tags in NFC-V (ISO 15693) standard.

## Returned value

### [NfcV](doc:nfc#nfcv-nfcadaptergetnfcv)

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

[IsoDep.connect()](doc:nfc#isodepconnectobject-object)

Connects to the NFC tag.

[IsoDep.close()](doc:nfc#isodepcloseobject-object)

Closes the connection.

[IsoDep.setTimeout(Object object)](doc:nfc#isodepsettimeoutobject-object)

Sets the timeout period.

[IsoDep.isConnected()](doc:nfc#isodepisconnectedobject-object)

Checks whether the connection is established.

[IsoDep.getMaxTransceiveLength()](doc:nfc#isodepgetmaxtransceivelengthobject-object)

Gets the maximum length of the transferred data.

[IsoDep.transceive(Object object)](doc:nfc#isodeptransceiveobject-object)

Sends data.

[IsoDep.getHistoricalBytes()](doc:nfc#isodepgethistoricalbytesobject-object)

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

[MifareClassic.connect()](doc:nfc#mifareclassicconnectobject-object)

Connects to the NFC tag.

[MifareClassic.close()](doc:nfc#mifareclassiccloseobject-object)

Closes the connection.

[MifareClassic.setTimeout(Object object)](doc:nfc#mifareclassicsettimeoutobject-object)

Sets the timeout period.

[MifareClassic.isConnected()](doc:nfc#mifareclassicisconnectedobject-object)

Checks whether the connection is established.

[MifareClassic.getMaxTransceiveLength()](doc:nfc#mifareclassicgetmaxtransceivelengthobject-object)

Gets the maximum length of the transferred data.

[MifareClassic.transceive(Object object)](doc:nfc#mifareclassictransceiveobject-object)

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

[MifareUltralight.connect()](doc:nfc#mifareultralightconnectobject-object)  
Connects to the NFC tag.

[MifareUltralight.close()](doc:nfc#mifareultralightcloseobject-object)  
Closes the connection.

[MifareUltralight.setTimeout(Object object)](doc:nfc#mifareultralightsettimeoutobject-object)  
Sets the timeout period.

[MifareUltralight.isConnected()](doc:nfc#mifareultralightisconnectedobject-object)  
Checks whether the connection is established.

[MifareUltralight.getMaxTransceiveLength()](doc:nfc#mifareultralightgetmaxtransceivelengthobject-object)  
Gets the maximum length of the transferred data.

[MifareUltralight.transceive(Object object)](doc:nfc#mifareultralighttransceiveobject-object)  
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

[Ndef.connect()](doc:nfc#ndefconnectobject-object)  
Connects to the NFC tag.

[Ndef.close()](doc:nfc#ndefcloseobject-object)  
Closes the connection.

[Ndef.setTimeout(Object object)](doc:nfc#ndefsettimeoutobject-object)  
Sets the timeout period.

[Ndef.isConnected()](doc:nfc#ndefisconnectedobject-object)  
Checks whether the connection is established.

[Ndef.onNdefMessage(function callback)](doc:nfc#ndefonndefmessagefunction-callback)  
Listens for the Ndef message.

[Ndef.offNdefMessage(function callback)](doc:nfc#ndefoffndefmessagefunction-callback)  
Unlistens for the Ndef message.

[Ndef.writeNdefMessage(Object object)](doc:nfc#ndefwritendefmessageobject-object)  
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

[block:parameters]
{
  "data": {
    "h-0": "Attribute",
    "h-1": "Type",
    "h-2": "Default",
    "h-3": "Required",
    "h-4": "Description",
    "0-0": "uris",
    "0-1": "Array",
    "0-2": "",
    "0-3": "No",
    "0-4": "`uri `array",
    "1-0": "texts",
    "1-1": "Array",
    "1-2": "",
    "1-3": "No",
    "1-4": "`text `array",
    "2-0": "records",
    "2-1": "Array",
    "2-2": "",
    "2-3": "No",
    "2-4": "Binary object array. You need to specify` id` , `type` , and `payload` (all are of the ArrayBuffer  \ntype).",
    "3-0": "success",
    "3-1": "Function",
    "3-2": "",
    "3-3": "No",
    "3-4": "Callback function for successful API call",
    "4-0": "fail",
    "4-1": "Function",
    "4-2": "",
    "4-3": "No",
    "4-4": "Callback function for failed API call",
    "5-0": "complete",
    "5-1": "Function",
    "5-2": "",
    "5-3": "No",
    "5-4": "Callback function for API call end (executed for both successful and failed calls)"
  },
  "cols": 5,
  "rows": 6,
  "align": [
    "left",
    "left",
    "left",
    "left",
    "left"
  ]
}
[/block]


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

[NfcA.connect()](doc:nfc#nfcaconnectobject-object)  
Connects to the NFC tag.

[NfcA.close()](doc:nfc#nfcacloseobject-object)  
Closes the connection.

[NfcA.setTimeout(Object object)](doc:nfc#nfcasettimeoutobject-object)  
Sets the timeout period.

[NfcA.isConnected()](doc:nfc#nfcaisconnectedobject-object)  
Checks whether the connection is established.

[NfcA.getMaxTransceiveLength()](doc:nfc#nfcagetmaxtransceivelengthobject-object)  
Gets the maximum length of the transferred data.

[NfcA.transceive(Object object)](doc:nfc#nfcatransceiveobject-object)  
Sends data.

[NfcA.getAtqa()](doc:nfc#nfcagetatqaobject-object)  
Gets the ATQA information.

[NfcA.getSak()](doc:nfc#nfcagetsakobject-object)  
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

[NfcB.connect()](doc:nfc#nfcbconnectobject-object)  
Connects to the NFC tag.

[NfcB.close()](doc:nfc#nfcbcloseobject-object)  
Closes the connection.

[NfcB.setTimeout(Object object)](doc:nfc#nfcbsettimeoutobject-object)  
Sets the timeout period.

[NfcB.isConnected()](doc:nfc#nfcbisconnectedobject-object)  
Checks whether the connection is established.

[NfcB.getMaxTransceiveLength()](doc:nfc#nfcbgetmaxtransceivelengthobject-object)  
Gets the maximum length of the transferred data.

[NfcB.transceive(Object object)](doc:nfc#nfcbtransceiveobject-object)  
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

[NfcF.connect()](doc:nfc#nfcfconnectobject-object)  
Connects to the NFC tag.

[NfcF.close()](doc:nfc#nfcfcloseobject-object)  
Closes the connection.

[NfcF.setTimeout(Object object)](doc:nfc#nfcfsettimeoutobject-object)  
Sets the timeout period.

[NfcF.isConnected()](doc:nfc#nfcfisconnectedobject-object)  
Checks whether the connection is established.

[NfcF.getMaxTransceiveLength()](<>)  
Gets the maximum length of the transferred data.

[NfcF.transceive(Object object)](doc:nfc#nfcftransceiveobject-object)  
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

[NfcV.connect()](doc:nfc#nfcvconnectobject-object)  
Connects to the NFC tag.

[NfcV.close()](doc:nfc#nfcvcloseobject-object)  
Closes the connection.

[NfcV.setTimeout(Object object)](doc:nfc#nfcvsettimeoutobject-object)  
Sets the timeout period.

[NfcV.isConnected()](doc:nfc#nfcvisconnectedobject-object)  
Checks whether the connection is established.

[NfcV.getMaxTransceiveLength()](doc:nfc#nfcvgetmaxtransceivelengthobject-object)  
Gets the maximum length of the transferred data.

[NfcV.transceive(Object object)](doc:nfc#nfcvtransceiveobject-object)  
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
