---
title: "NFC"
slug: "nfc-copy"
excerpt: "This section explains the concept of NFC in Mini App."
hidden: true
metadata: 
  image: []
  robots: "index"
createdAt: "Mon May 08 2023 07:59:37 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Mon May 29 2023 07:12:08 GMT+0000 (Coordinated Universal Time)"
---
Supports the HCE (Host-Based Card Emulation) mode, which mimics a physical smart card with an Android phone. The phone can be used as a card reader because it supports NFC read and write.

- Applicable models: Mobile phones that support NFC function and have a system version of Android 5.0 and above.
- Applicable card range: CPU cards according to ISO 14443-4.
- Supports Reader/Writer mode, which supports NFC devices to read or write passive NFC tags and stickers.
- Applicable models: Mobile phones that support NFC function and have a system version of Android 5.0 and above.

Scope of application:

- Supports reading and writing according to NFC-A (ISO 14443-3A) / NFC-B (ISO 14443-3B) / NFC-F (JIS 6319-4) / NFC-V (ISO 15693) / ISO-DEP (ISO 14443-4) standards (Some Android phones) support reading and writing the MIFARE Classic / MIFARE Ultralight tags.
- Supports reading and writing of NDEF data on NFC tags in NDEF format.

# Basic flow

In the past, NFC-A cards wrote apdu instructions as an example:

- Call wx.getNFCAdapter() to get NFC adapter instance.
- Call NFCAdapter.onDiscovered(function Callback) to register sticklistencallback.
- Call NFCAdapter.startDiscovery(Object Object) to start listening for sticker cards.
- Posted card, onDiscoveredcallback
  - The techs field of the res object is matched against the onDiscovered callback to the card that supports the NFC-A standard.
  - Get the NfcA instance via NFCAdapter.getNfcA().
- Use an NfcA instance for reading and writing:
  - Call NfcA.connect() and NFC cards to establish a connection.
  - Call NfcA.transceive(Object Object) to write apdu instructions to NFC cards and receives card return data.
  - After reading and writing, call NfcA.close() to disconnect.
- Call NFCAdapter.stopDiscovery(Object Object) to listening sticker card.
