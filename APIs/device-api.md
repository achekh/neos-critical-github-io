---
title: "Device"
slug: "device-api"
excerpt: ""
hidden: false
createdAt: "Wed Mar 15 2023 08:08:41 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Wed Nov 29 2023 13:45:35 GMT+0000 (Coordinated Universal Time)"
layout: "default"
parent: "APIs"
has_children: true
has_toc: false
nav_order: 12
---
# Device 
*** 
### Bluetooth-general

| Name                                                                                          | Feature Description                                                           |
| :-------------------------------------------------------------------------------------------- | :---------------------------------------------------------------------------- |
| [openBluetoothAdapter](device-api/bluetooth-api#wxopenbluetoothadapterobject-object)                 | Initializes the Bluetooth module.                                             |
| [getConnectedBluetoothDevices](device-api/bluetooth-api#wxgetconnectedbluetoothdevicesobject-object) | Gets the connected Bluetooth device based on the UUID of the primary service. |
| [getBluetoothDevices](device-api/bluetooth-api#wxgetbluetoothdevicesobject-object)                   | Gets all the Bluetooth devices found when the Bluetooth module is in effect.  |
| [getBluetoothAdapterState](device-api/bluetooth-api#wxgetbluetoothadapterstateobject-object)         | Gets the status of the local Bluetooth adapter.                               |
| [closeBluetoothAdapter](device-api/bluetooth-api#wxclosebluetoothadapterobject-object)               | Disables the Bluetooth module.                                                |

### NFC read/write

| Name                                                | Feature Description    |
| :-------------------------------------------------- | :--------------------- |
| [getNFCAdapter](device-api/nfc#nfcadapter-wxgetnfcadapter) | Gets the NFC instance. |

### NFC Adapter

| Name                                                                                     | Feature Description                                                                                  |
| :--------------------------------------------------------------------------------------- | :--------------------------------------------------------------------------------------------------- |
| [NFCAdapter.getIsoDep](device-api/nfc#isodep-nfcadaptergetisodep)                               | Gets the `IsoDep` instance, which can read and write data on tags in ISO-DEP (ISO 14443-4) standard. |
| [NFCAdapter.getMifareClassic](device-api/nfc#mifareclassic-nfcadaptergetmifareclassic)          | Gets the `MifareClassic` instance, which can read and write data on MIFARE Classic tags.             |
| [NFCAdapter.getMifareUltralight](device-api/nfc#mifareultralight-nfcadaptergetmifareultralight) | Gets the `MifareUltralight` instance, which can read and write data on MIFARE Ultralight tags.       |
| [NFCAdapter.getNdef](device-api/nfc#ndef-nfcadaptergetndef)                                     | Gets the `Ndef` instance, which can read and write the NDEF data on NFC tags in NDEF format.         |
| [NFCAdapter.getNfcA](device-api/nfc#nfca-nfcadaptergetnfca)                                     | Gets the `NfcA` instance, which can read and write data on tags in NFC-A (ISO 14443-3A) standard.    |
| [NFCAdapter.getNfcB](device-api/nfc#nfcb-nfcadaptergetnfcb)                                     | Gets the NfcB instance, which can read and write data on tags in NFC-B (ISO 14443-3B) standard.      |
| [NFCAdapter.getNfcF](device-api/nfc#nfcf-nfcadaptergetnfcf)                                     | Gets the NfcF instance, which can read and write data on tags in NFC-F (JIS 6319-4) standard.        |
| [NFCAdapter.offDiscovered](device-api/nfc#nfcadapteroffdiscoveredfunction-listener)             | Unlistens for NFC tags.                                                                              |
| [NFCAdapter.onDiscovered](device-api/nfc#nfcadapterondiscoveredfunction-listener)               | Listens for NFC tags.                                                                                |
| [NFCAdapter.startDiscovery](device-api/nfc#nfcadapterstartdiscoveryobject-object)               | -                                                                                                    |
| [NFCAdapter.stopDiscovery](device-api/nfc#nfcadapterstopdiscoveryobject-object)                 | -                                                                                                    |

### IsoDep

| Name                                                                               | Feature Description                              |
| :--------------------------------------------------------------------------------- | :----------------------------------------------- |
| [IsoDep.close](device-api/nfc#isodepcloseobject-object)                                   | Closes the connection.                           |
| [IsoDep.connect](device-api/nfc#isodepconnectobject-object)                               | Connects to the NFC tag.                         |
| [IsoDep.getHistoricalBytes](device-api/nfc#isodepgethistoricalbytesobject-object)         | Gets the reset information.                      |
| [IsoDep.getMaxTransceiveLength](device-api/nfc#isodepgetmaxtransceivelengthobject-object) | Gets the maximum length of the transferred data. |
| [IsoDep.isConnected](device-api/nfc#isodepisconnectedobject-object)                       | Checks whether the connection is established.    |
| [IsoDep.setTimeout](device-api/nfc#isodepsettimeoutobject-object)                         | Sets the timeout period.                         |
| [IsoDep.transceive](device-api/nfc#isodeptransceiveobject-object)                         | Sends data.                                      |

### MifareClassic

| Name                                                                                             | Feature Description                              |
| :----------------------------------------------------------------------------------------------- | :----------------------------------------------- |
| [MifareClassic.close](device-api/nfc#mifareclassiccloseobject-object)                                   | Closes the connection.                           |
| [MifareClassic.connect](device-api/nfc#mifareclassicconnectobject-object)                               | Connects to the NFC tag.                         |
| [MifareClassic.getMaxTransceiveLength](device-api/nfc#mifareclassicgetmaxtransceivelengthobject-object) | Gets the maximum length of the transferred data. |
| [MifareClassic.isConnected](device-api/nfc#mifareclassicisconnectedobject-object)                       | Checks whether the connection is established.    |
| [MifareClassic.setTimeout](device-api/nfc#mifareclassicsettimeoutobject-object)                         | Sets the timeout period.                         |
| [MifareClassic.transceive](device-api/nfc#mifareclassictransceiveobject-object)                         | Sends data.                                      |

### MifareUltralight

| Name                                                                                                   | Feature Description                              |
| :----------------------------------------------------------------------------------------------------- | :----------------------------------------------- |
| [MifareUltralight.close](device-api/nfc#mifareultralightcloseobject-object)                                   | Closes the connection.                           |
| [MifareUltralight.connect](device-api/nfc#mifareultralightconnectobject-object)                               | Connects to the NFC tag.                         |
| [MifareUltralight.getMaxTransceiveLength](device-api/nfc#mifareultralightgetmaxtransceivelengthobject-object) | Gets the maximum length of the transferred data. |
| [MifareUltralight.isConnected](device-api/nfc#mifareultralightisconnectedobject-object)                       | Checks whether the connection is established.    |
| [MifareUltralight.setTimeout](device-api/nfc#mifareultralightsettimeoutobject-object)                         | Sets the timeout period.                         |
| [MifareUltralight.transceive](device-api/nfc#mifareultralighttransceiveobject-object)                         | Sends data.                                      |

### Ndef

| Name                                                               | Feature Description                           |
| :----------------------------------------------------------------- | :-------------------------------------------- |
| [Ndef.close](device-api/nfc#ndefcloseobject-object)                       | Closes the connection.                        |
| [Ndef.connect](device-api/nfc#ndefconnectobject-object)                   | Connects to the NFC tag.                      |
| [Ndef.isConnected](device-api/nfc#ndefisconnectedobject-object)           | Checks whether the connection is established. |
| [Ndef.offNdefMessage](device-api/nfc#ndefoffndefmessagefunction-callback) | Unlistens for the Ndef message.               |
| [Ndef.onNdefMessage](device-api/nfc#ndefonndefmessagefunction-callback)   | Listens for the Ndef message.                 |
| [Ndef.setTimeout](device-api/nfc#ndefsettimeoutobject-object)             | Sets the timeout period.                      |
| [Ndef.writeNdefMessage](device-api/nfc#ndefwritendefmessageobject-object) | Rewrites the content of the Ndef tag.         |

### NfcA

| Name                                                                           | Feature Description                              |
| :----------------------------------------------------------------------------- | :----------------------------------------------- |
| [NfcA.close](device-api/nfc#nfcacloseobject-object)                                   | Closes the connection.                           |
| [NfcA.connect](device-api/nfc#nfcaconnectobject-object)                               | Connects to the NFC tag.                         |
| [NfcA.getAtqa](device-api/nfc#nfcagetatqaobject-object)                               | Gets the ATQA information.                       |
| [NfcA.getMaxTransceiveLength](device-api/nfc#nfcagetmaxtransceivelengthobject-object) | Gets the maximum length of the transferred data. |
| [NfcA.getSak](device-api/nfc#nfcagetsakobject-object)                                 | Gets the SAK information.                        |
| [NfcA.isConnected](device-api/nfc#nfcaisconnectedobject-object)                       | Checks whether the connection is established.    |
| [NfcA.setTimeout](device-api/nfc#nfcasettimeoutobject-object)                         | Sets the timeout period.                         |
| [NfcA.transceive](device-api/nfc#nfcatransceiveobject-object)                         | Sends data.                                      |

### NfcB

| Name                                                                           | Feature Description                              |
| :----------------------------------------------------------------------------- | :----------------------------------------------- |
| [NfcB.close](device-api/nfc#nfcbcloseobject-object)                                   | Closes the connection.                           |
| [NfcB.connect](device-api/nfc#nfcbconnectobject-object)                               | Connects to the NFC tag.                         |
| [NfcB.getMaxTransceiveLength](device-api/nfc#nfcbgetmaxtransceivelengthobject-object) | Gets the maximum length of the transferred data. |
| [NfcB.isConnected](device-api/nfc#nfcbisconnectedobject-object)                       | Checks whether the connection is established.    |
| [NfcB.setTimeout](device-api/nfc#nfcbsettimeoutobject-object)                         | Sets the timeout period.                         |
| [NfcB.transceive](device-api/nfc#nfcbtransceiveobject-object)                         | Sends data.                                      |

### NfcF

| Name                                                                           | Feature Description                              |
| :----------------------------------------------------------------------------- | :----------------------------------------------- |
| [NfcF.close](device-api/nfc#nfcfcloseobject-object)                                   | Closes the connection.                           |
| [NfcF.connect](device-api/nfc#nfcfconnectobject-object)                               | Connects to the NFC tag.                         |
| [NfcF.getMaxTransceiveLength](device-api/nfc#nfcfgetmaxtransceivelengthobject-object) | Gets the maximum length of the transferred data. |
| [NfcF.isConnected](device-api/nfc#nfcfisconnectedobject-object)                       | Checks whether the connection is established.    |
| [NfcF.setTimeout](device-api/nfc#nfcfsettimeoutobject-object)                         | Sets the timeout period.                         |
| [NfcF.transceive](device-api/nfc#nfcftransceiveobject-object)                         | Sends data.                                      |

### NFcV

| Name                                                                           | Feature Description                              |
| :----------------------------------------------------------------------------- | :----------------------------------------------- |
| [NfcV.close](device-api/nfc#nfcvcloseobject-object)                                   | Closes the connection.                           |
| [NfcV.connect](device-api/nfc#nfcvconnectobject-object)                               | Connects to the NFC tag.                         |
| [NfcV.getMaxTransceiveLength](device-api/nfc#nfcvgetmaxtransceivelengthobject-object) | Gets the maximum length of the transferred data. |
| [NfcV.isConnected](device-api/nfc#nfcvisconnectedobject-object)                       | Checks whether the connection is established.    |
| [NfcV.setTimeout](device-api/nfc#nfcvsettimeoutobject-object)                         | Sets the timeout period.                         |
| [NfcV.transceive](device-api/nfc#nfcvtransceiveobject-object)                         | Sends data.                                      |

### Wi-Fi

| Name                                                                  | Feature Description      |
| :-------------------------------------------------------------------- | :----------------------- |
| [onWifiConnected](device-api/wi-fi-api#wxonwificonnectedfunction-listener)   | Closes the connection.   |
| [offWifiConnected](device-api/wi-fi-api#wxoffwificonnectedfunction-listener) | Connects to the NFC tag. |
| [WifiInfo](device-api/wi-fi-api#wifiinfo)                                    | Wi-Fi information.       |

### Calender

| Name                                                                           | Feature Description                           |
| :----------------------------------------------------------------------------- | :-------------------------------------------- |
| [addPhoneRepeatCalendar](device-api/calender-api#addphonerepeatcalendarobject-object) | Adds a repeated event to the system calendar. |
| [addPhoneCalendar](device-api/calender-api#addphonecalendarobject-object)             | Adds an event to the system calendar.         |

### Contacts

| Name                                                           | Feature Description                           |
| :------------------------------------------------------------- | :-------------------------------------------- |
| [chooseContact](device-api/contacts-api#wxchoosecontactobject-object) | Opens the phone contacts to select a contact. |

### Clipboard

| Name                                                                  | Feature Description                       |
| :-------------------------------------------------------------------- | :---------------------------------------- |
| [setClipboardData](device-api/clipboard-api#wxsetclipboarddataobject-object) | Sets the content in the system clipboard. |
| [getClipboardData](device-api/clipboard-api#wxgetclipboarddataobject-object) | Gets the content in the system clipboard. |

### Network

| Name                                                                              | Feature Description                          |
| :-------------------------------------------------------------------------------- | :------------------------------------------- |
| [onNetworkStatusChange](device-api/network-api#wxonnetworkstatuschangefunction-callback) | Listens for the network status change event. |
| [getNetworkType](device-api/network-api#wxgetnetworktypeobject-object)                   | Gets the network type.                       |

### Keyboard

| Name                                                                                   | Feature Description                                                                          |
| :------------------------------------------------------------------------------------- | :------------------------------------------------------------------------------------------- |
| [onKeyboardHeightChange](device-api/keyboard-api#onkeyboardheightchangefunction-listener)     | Listens for the keyboard height change event.                                                |
| [hideKeyboard](device-api/keyboard-api#hidekeyboardobject-object)                             | Hides the keyboard manually after it appears because of the focus in the input or text area. |
| [offKeyboardHeightChange](device-api/keyboard-api#wxoffkeyboardheightchangefunction-listener) | Unlistens for the keyboard height change event.                                              |
| [getSelectedTextRange](device-api/keyboard-api#wxgetselectedtextrangeobject-object)           | Gets the cursor position of the input box after `input` and `textarea` are focused.          |

### Phone

| Name                                         | Feature Description |
| :------------------------------------------- | :------------------ |
| [makePhoneCall](device-api/phone-api#makephonecall) | Makes a call.       |

### Accelerometer

| Name                                                                                      | Feature Description                         |
| :---------------------------------------------------------------------------------------- | :------------------------------------------ |
| [stopAccelerometer](device-api/accelerometer-api#wxstopaccelerometerobject-object)               | Unlistens for accelerometer data.           |
| [startAccelerometer](device-api/accelerometer-api#wxstartaccelerometerobject-objectr)            | Listens for accelerometer data.             |
| [onAccelerometerChange](device-api/accelerometer-api#wxonaccelerometerchangefunction-callback)   | Listens for the accelerometer data event.   |
| [offAccelerometerChange](device-api/accelerometer-api#wxoffaccelerometerchangefunction-listener) | Unlistens for the accelerometer data event. |

### Compass

| Name                                                                    | Feature Description                          |
| :---------------------------------------------------------------------- | :------------------------------------------- |
| [stopCompass](device-api/compass-api#wxstopcompassobject-object)               | Unlistens for compass data.                  |
| [startCompass](device-api/compass-api#wxstartcompassobject-object)             | Listens for compass data.                    |
| [onCompassChange](device-api/compass-api#wxoncompasschangefunction-callback)   | Listens for the compass data change event.   |
| [offCompassChange](device-api/compass-api#wxoffcompasschangefunction-listener) | Unlistens for the compass data change event. |

### Gyroscope

| Name                                                                        | Feature Description                          |
| :-------------------------------------------------------------------------- | :------------------------------------------- |
| [stopGyroscope](device-api/gyroscope-api#wxstopgyroscopeobject-object)             | Unlistens for gyroscope data.                |
| [startGyroscope](device-api/gyroscope-api#wxstartgyroscopeobject-object)           | Listens for gyroscope data.                  |
| [onGyroscopeChange](device-api/gyroscope-api#wxongyroscopechangefunction-callback) | Listens for the gyroscope data change event. |

### Code scan

| Name                                   | Feature Description                                 |
| :------------------------------------- | :-------------------------------------------------- |
| [scanCode](device-api/code-scan-api#scancode) | Opens the client's code scanning UI to scan a code. |

### SMS

| Name                                          | Feature Description               |
| :-------------------------------------------- | :-------------------------------- |
| [sendSms](device-api/sms-api#wxsendsmsobject-object) | Opens the phone's SMS sending UI. |

### Vibration

| Name                                                          | Feature Description                                         |
| :------------------------------------------------------------ | :---------------------------------------------------------- |
| [vibrateShort](device-api/vibration-api#wxvibrateshortobject-object) | Makes the phone vibrate for a short period of time (15 ms). |
| [vibrateLong](device-api/vibration-api#wxvibratelongobject-object)   | Makes the phone vibrate for a long period of time (400 ms). |
