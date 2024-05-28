---
title: "Device"
slug: "device-api"
excerpt: ""
hidden: false
createdAt: "Wed Mar 15 2023 08:08:41 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Wed Nov 29 2023 13:45:35 GMT+0000 (Coordinated Universal Time)"
layout: "default"
parent: "Home"
has_children: true
---
### Bluetooth-general

| Name                                                                                          | Feature Description                                                           |
| :-------------------------------------------------------------------------------------------- | :---------------------------------------------------------------------------- |
| [openBluetoothAdapter](doc:bluetooth-api#wxopenbluetoothadapterobject-object)                 | Initializes the Bluetooth module.                                             |
| [getConnectedBluetoothDevices](doc:bluetooth-api#wxgetconnectedbluetoothdevicesobject-object) | Gets the connected Bluetooth device based on the UUID of the primary service. |
| [getBluetoothDevices](doc:bluetooth-api#wxgetbluetoothdevicesobject-object)                   | Gets all the Bluetooth devices found when the Bluetooth module is in effect.  |
| [getBluetoothAdapterState](doc:bluetooth-api#wxgetbluetoothadapterstateobject-object)         | Gets the status of the local Bluetooth adapter.                               |
| [closeBluetoothAdapter](doc:bluetooth-api#wxclosebluetoothadapterobject-object)               | Disables the Bluetooth module.                                                |

### NFC read/write

| Name                                                | Feature Description    |
| :-------------------------------------------------- | :--------------------- |
| [getNFCAdapter](doc:nfc#nfcadapter-wxgetnfcadapter) | Gets the NFC instance. |

### NFC Adapter

| Name                                                                                     | Feature Description                                                                                  |
| :--------------------------------------------------------------------------------------- | :--------------------------------------------------------------------------------------------------- |
| [NFCAdapter.getIsoDep](doc:nfc#isodep-nfcadaptergetisodep)                               | Gets the `IsoDep` instance, which can read and write data on tags in ISO-DEP (ISO 14443-4) standard. |
| [NFCAdapter.getMifareClassic](doc:nfc#mifareclassic-nfcadaptergetmifareclassic)          | Gets the `MifareClassic` instance, which can read and write data on MIFARE Classic tags.             |
| [NFCAdapter.getMifareUltralight](doc:nfc#mifareultralight-nfcadaptergetmifareultralight) | Gets the `MifareUltralight` instance, which can read and write data on MIFARE Ultralight tags.       |
| [NFCAdapter.getNdef](doc:nfc#ndef-nfcadaptergetndef)                                     | Gets the `Ndef` instance, which can read and write the NDEF data on NFC tags in NDEF format.         |
| [NFCAdapter.getNfcA](doc:nfc#nfca-nfcadaptergetnfca)                                     | Gets the `NfcA` instance, which can read and write data on tags in NFC-A (ISO 14443-3A) standard.    |
| [NFCAdapter.getNfcB](doc:nfc#nfcb-nfcadaptergetnfcb)                                     | Gets the NfcB instance, which can read and write data on tags in NFC-B (ISO 14443-3B) standard.      |
| [NFCAdapter.getNfcF](doc:nfc#nfcf-nfcadaptergetnfcf)                                     | Gets the NfcF instance, which can read and write data on tags in NFC-F (JIS 6319-4) standard.        |
| [NFCAdapter.offDiscovered](doc:nfc#nfcadapteroffdiscoveredfunction-listener)             | Unlistens for NFC tags.                                                                              |
| [NFCAdapter.onDiscovered](doc:nfc#nfcadapterondiscoveredfunction-listener)               | Listens for NFC tags.                                                                                |
| [NFCAdapter.startDiscovery](doc:nfc#nfcadapterstartdiscoveryobject-object)               | -                                                                                                    |
| [NFCAdapter.stopDiscovery](doc:nfc#nfcadapterstopdiscoveryobject-object)                 | -                                                                                                    |

### IsoDep

| Name                                                                               | Feature Description                              |
| :--------------------------------------------------------------------------------- | :----------------------------------------------- |
| [IsoDep.close](doc:nfc#isodepcloseobject-object)                                   | Closes the connection.                           |
| [IsoDep.connect](doc:nfc#isodepconnectobject-object)                               | Connects to the NFC tag.                         |
| [IsoDep.getHistoricalBytes](doc:nfc#isodepgethistoricalbytesobject-object)         | Gets the reset information.                      |
| [IsoDep.getMaxTransceiveLength](doc:nfc#isodepgetmaxtransceivelengthobject-object) | Gets the maximum length of the transferred data. |
| [IsoDep.isConnected](doc:nfc#isodepisconnectedobject-object)                       | Checks whether the connection is established.    |
| [IsoDep.setTimeout](doc:nfc#isodepsettimeoutobject-object)                         | Sets the timeout period.                         |
| [IsoDep.transceive](doc:nfc#isodeptransceiveobject-object)                         | Sends data.                                      |

### MifareClassic

| Name                                                                                             | Feature Description                              |
| :----------------------------------------------------------------------------------------------- | :----------------------------------------------- |
| [MifareClassic.close](doc:nfc#mifareclassiccloseobject-object)                                   | Closes the connection.                           |
| [MifareClassic.connect](doc:nfc#mifareclassicconnectobject-object)                               | Connects to the NFC tag.                         |
| [MifareClassic.getMaxTransceiveLength](doc:nfc#mifareclassicgetmaxtransceivelengthobject-object) | Gets the maximum length of the transferred data. |
| [MifareClassic.isConnected](doc:nfc#mifareclassicisconnectedobject-object)                       | Checks whether the connection is established.    |
| [MifareClassic.setTimeout](doc:nfc#mifareclassicsettimeoutobject-object)                         | Sets the timeout period.                         |
| [MifareClassic.transceive](doc:nfc#mifareclassictransceiveobject-object)                         | Sends data.                                      |

### MifareUltralight

| Name                                                                                                   | Feature Description                              |
| :----------------------------------------------------------------------------------------------------- | :----------------------------------------------- |
| [MifareUltralight.close](doc:nfc#mifareultralightcloseobject-object)                                   | Closes the connection.                           |
| [MifareUltralight.connect](doc:nfc#mifareultralightconnectobject-object)                               | Connects to the NFC tag.                         |
| [MifareUltralight.getMaxTransceiveLength](doc:nfc#mifareultralightgetmaxtransceivelengthobject-object) | Gets the maximum length of the transferred data. |
| [MifareUltralight.isConnected](doc:nfc#mifareultralightisconnectedobject-object)                       | Checks whether the connection is established.    |
| [MifareUltralight.setTimeout](doc:nfc#mifareultralightsettimeoutobject-object)                         | Sets the timeout period.                         |
| [MifareUltralight.transceive](doc:nfc#mifareultralighttransceiveobject-object)                         | Sends data.                                      |

### Ndef

| Name                                                               | Feature Description                           |
| :----------------------------------------------------------------- | :-------------------------------------------- |
| [Ndef.close](doc:nfc#ndefcloseobject-object)                       | Closes the connection.                        |
| [Ndef.connect](doc:nfc#ndefconnectobject-object)                   | Connects to the NFC tag.                      |
| [Ndef.isConnected](doc:nfc#ndefisconnectedobject-object)           | Checks whether the connection is established. |
| [Ndef.offNdefMessage](doc:nfc#ndefoffndefmessagefunction-callback) | Unlistens for the Ndef message.               |
| [Ndef.onNdefMessage](doc:nfc#ndefonndefmessagefunction-callback)   | Listens for the Ndef message.                 |
| [Ndef.setTimeout](doc:nfc#ndefsettimeoutobject-object)             | Sets the timeout period.                      |
| [Ndef.writeNdefMessage](doc:nfc#ndefwritendefmessageobject-object) | Rewrites the content of the Ndef tag.         |

### NfcA

| Name                                                                           | Feature Description                              |
| :----------------------------------------------------------------------------- | :----------------------------------------------- |
| [NfcA.close](doc:nfc#nfcacloseobject-object)                                   | Closes the connection.                           |
| [NfcA.connect](doc:nfc#nfcaconnectobject-object)                               | Connects to the NFC tag.                         |
| [NfcA.getAtqa](doc:nfc#nfcagetatqaobject-object)                               | Gets the ATQA information.                       |
| [NfcA.getMaxTransceiveLength](doc:nfc#nfcagetmaxtransceivelengthobject-object) | Gets the maximum length of the transferred data. |
| [NfcA.getSak](doc:nfc#nfcagetsakobject-object)                                 | Gets the SAK information.                        |
| [NfcA.isConnected](doc:nfc#nfcaisconnectedobject-object)                       | Checks whether the connection is established.    |
| [NfcA.setTimeout](doc:nfc#nfcasettimeoutobject-object)                         | Sets the timeout period.                         |
| [NfcA.transceive](doc:nfc#nfcatransceiveobject-object)                         | Sends data.                                      |

### NfcB

| Name                                                                           | Feature Description                              |
| :----------------------------------------------------------------------------- | :----------------------------------------------- |
| [NfcB.close](doc:nfc#nfcbcloseobject-object)                                   | Closes the connection.                           |
| [NfcB.connect](doc:nfc#nfcbconnectobject-object)                               | Connects to the NFC tag.                         |
| [NfcB.getMaxTransceiveLength](doc:nfc#nfcbgetmaxtransceivelengthobject-object) | Gets the maximum length of the transferred data. |
| [NfcB.isConnected](doc:nfc#nfcbisconnectedobject-object)                       | Checks whether the connection is established.    |
| [NfcB.setTimeout](doc:nfc#nfcbsettimeoutobject-object)                         | Sets the timeout period.                         |
| [NfcB.transceive](doc:nfc#nfcbtransceiveobject-object)                         | Sends data.                                      |

### NfcF

| Name                                                                           | Feature Description                              |
| :----------------------------------------------------------------------------- | :----------------------------------------------- |
| [NfcF.close](doc:nfc#nfcfcloseobject-object)                                   | Closes the connection.                           |
| [NfcF.connect](doc:nfc#nfcfconnectobject-object)                               | Connects to the NFC tag.                         |
| [NfcF.getMaxTransceiveLength](doc:nfc#nfcfgetmaxtransceivelengthobject-object) | Gets the maximum length of the transferred data. |
| [NfcF.isConnected](doc:nfc#nfcfisconnectedobject-object)                       | Checks whether the connection is established.    |
| [NfcF.setTimeout](doc:nfc#nfcfsettimeoutobject-object)                         | Sets the timeout period.                         |
| [NfcF.transceive](doc:nfc#nfcftransceiveobject-object)                         | Sends data.                                      |

### NFcV

| Name                                                                           | Feature Description                              |
| :----------------------------------------------------------------------------- | :----------------------------------------------- |
| [NfcV.close](doc:nfc#nfcvcloseobject-object)                                   | Closes the connection.                           |
| [NfcV.connect](doc:nfc#nfcvconnectobject-object)                               | Connects to the NFC tag.                         |
| [NfcV.getMaxTransceiveLength](doc:nfc#nfcvgetmaxtransceivelengthobject-object) | Gets the maximum length of the transferred data. |
| [NfcV.isConnected](doc:nfc#nfcvisconnectedobject-object)                       | Checks whether the connection is established.    |
| [NfcV.setTimeout](doc:nfc#nfcvsettimeoutobject-object)                         | Sets the timeout period.                         |
| [NfcV.transceive](doc:nfc#nfcvtransceiveobject-object)                         | Sends data.                                      |

### Wi-Fi

| Name                                                                  | Feature Description      |
| :-------------------------------------------------------------------- | :----------------------- |
| [onWifiConnected](doc:wi-fi-api#wxonwificonnectedfunction-listener)   | Closes the connection.   |
| [offWifiConnected](doc:wi-fi-api#wxoffwificonnectedfunction-listener) | Connects to the NFC tag. |
| [WifiInfo](doc:wi-fi-api#wifiinfo)                                    | Wi-Fi information.       |

### Calender

| Name                                                                           | Feature Description                           |
| :----------------------------------------------------------------------------- | :-------------------------------------------- |
| [addPhoneRepeatCalendar](doc:calender-api#addphonerepeatcalendarobject-object) | Adds a repeated event to the system calendar. |
| [addPhoneCalendar](doc:calender-api#addphonecalendarobject-object)             | Adds an event to the system calendar.         |

### Contacts

| Name                                                           | Feature Description                           |
| :------------------------------------------------------------- | :-------------------------------------------- |
| [chooseContact](doc:contacts-api#wxchoosecontactobject-object) | Opens the phone contacts to select a contact. |

### Clipboard

| Name                                                                  | Feature Description                       |
| :-------------------------------------------------------------------- | :---------------------------------------- |
| [setClipboardData](doc:clipboard-api#wxsetclipboarddataobject-object) | Sets the content in the system clipboard. |
| [getClipboardData](doc:clipboard-api#wxgetclipboarddataobject-object) | Gets the content in the system clipboard. |

### Network

| Name                                                                              | Feature Description                          |
| :-------------------------------------------------------------------------------- | :------------------------------------------- |
| [onNetworkStatusChange](doc:network-api#wxonnetworkstatuschangefunction-callback) | Listens for the network status change event. |
| [getNetworkType](doc:network-api#wxgetnetworktypeobject-object)                   | Gets the network type.                       |

### Keyboard

| Name                                                                                   | Feature Description                                                                          |
| :------------------------------------------------------------------------------------- | :------------------------------------------------------------------------------------------- |
| [onKeyboardHeightChange](doc:keyboard-api#onkeyboardheightchangefunction-listener)     | Listens for the keyboard height change event.                                                |
| [hideKeyboard](doc:keyboard-api#hidekeyboardobject-object)                             | Hides the keyboard manually after it appears because of the focus in the input or text area. |
| [offKeyboardHeightChange](doc:keyboard-api#wxoffkeyboardheightchangefunction-listener) | Unlistens for the keyboard height change event.                                              |
| [getSelectedTextRange](doc:keyboard-api#wxgetselectedtextrangeobject-object)           | Gets the cursor position of the input box after `input` and `textarea` are focused.          |

### Phone

| Name                                         | Feature Description |
| :------------------------------------------- | :------------------ |
| [makePhoneCall](doc:phone-api#makephonecall) | Makes a call.       |

### Accelerometer

| Name                                                                                      | Feature Description                         |
| :---------------------------------------------------------------------------------------- | :------------------------------------------ |
| [stopAccelerometer](doc:accelerometer-api#wxstopaccelerometerobject-object)               | Unlistens for accelerometer data.           |
| [startAccelerometer](doc:accelerometer-api#wxstartaccelerometerobject-objectr)            | Listens for accelerometer data.             |
| [onAccelerometerChange](doc:accelerometer-api#wxonaccelerometerchangefunction-callback)   | Listens for the accelerometer data event.   |
| [offAccelerometerChange](doc:accelerometer-api#wxoffaccelerometerchangefunction-listener) | Unlistens for the accelerometer data event. |

### Compass

| Name                                                                    | Feature Description                          |
| :---------------------------------------------------------------------- | :------------------------------------------- |
| [stopCompass](doc:compass-api#wxstopcompassobject-object)               | Unlistens for compass data.                  |
| [startCompass](doc:compass-api#wxstartcompassobject-object)             | Listens for compass data.                    |
| [onCompassChange](doc:compass-api#wxoncompasschangefunction-callback)   | Listens for the compass data change event.   |
| [offCompassChange](doc:compass-api#wxoffcompasschangefunction-listener) | Unlistens for the compass data change event. |

### Gyroscope

| Name                                                                        | Feature Description                          |
| :-------------------------------------------------------------------------- | :------------------------------------------- |
| [stopGyroscope](doc:gyroscope-api#wxstopgyroscopeobject-object)             | Unlistens for gyroscope data.                |
| [startGyroscope](doc:gyroscope-api#wxstartgyroscopeobject-object)           | Listens for gyroscope data.                  |
| [onGyroscopeChange](doc:gyroscope-api#wxongyroscopechangefunction-callback) | Listens for the gyroscope data change event. |

### Code scan

| Name                                   | Feature Description                                 |
| :------------------------------------- | :-------------------------------------------------- |
| [scanCode](doc:code-scan-api#scancode) | Opens the client's code scanning UI to scan a code. |

### SMS

| Name                                          | Feature Description               |
| :-------------------------------------------- | :-------------------------------- |
| [sendSms](doc:sms-api#wxsendsmsobject-object) | Opens the phone's SMS sending UI. |

### Vibration

| Name                                                          | Feature Description                                         |
| :------------------------------------------------------------ | :---------------------------------------------------------- |
| [vibrateShort](doc:vibration-api#wxvibrateshortobject-object) | Makes the phone vibrate for a short period of time (15 ms). |
| [vibrateLong](doc:vibration-api#wxvibratelongobject-object)   | Makes the phone vibrate for a long period of time (400 ms). |
