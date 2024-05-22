---
title: "Update"
slug: "update"
excerpt: "A collection of APIs to check Mini App updates and apply them."
hidden: false
metadata: 
  image: []
  robots: "index"
createdAt: "Fri Apr 14 2023 12:23:04 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Fri Jul 14 2023 11:12:10 GMT+0000 (Coordinated Universal Time)"
---
- [getUpdateManager](doc:update#wxgetupdatemanager)
- [UpdateManager](doc:update#updatemanager)
  - [UpdateManager.applyUpdate](doc:update#wxgetupdatemanager)
  - [UpdateManager.onCheckForUpdate](doc:update#updatemanageroncheckforupdatefunction-callback)
  - [UpdateManager.onUpdateFailed](update#updatemanageronupdatefailedfunction-callback)
  - [UpdateManager.onUpdateReady](doc:update#updatemanageronupdatereadyfunction-callback)

# wx.getUpdateManager

## [UpdateManager](doc:update#updatemanager-1) wx.getUpdateManager()

Gets the globally unique version of update manager for managing Mini App updates.

## Returned value

### [UpdateManager](doc:update#updatemanager-1)

Update manager object.

### Sample code

```javascript JavaScript
const updateManager = wx.getUpdateManager()
updateManager.onCheckForUpdate(function (res) {
  // Callback after requesting the new version information
  console.log(res.hasUpdate)
})
updateManager.onUpdateReady(function () {
  wx.showModal({
    title: 'Update prompt',
    content: 'The new version is ready. Restart the app?',
    success(res) {
      if (res.confirm) {
        // The new version has been downloaded. Call `applyUpdate` to apply it and restart the app.
        updateManager.applyUpdate()
			}
		}
	})
})

updateManager.onUpdateFailed(function () {
	// Failed to download the new version.
})
```

> 📘 Notes
> 
> - In the Super Hub Mini App Studio, you can use the Simulate update at the next compilation switch in compilation mode for debugging.
> - Mini App development and test versions do not have the "version" concept. So they cannot be used to test version updates.

# UpdateManager

## UpdateManager.applyUpdate()

Forces the mini app to restart and update to the new version. It is called after the new mini app version is downloaded (i.e., when the `onUpdateReady` callback is received).

## onCheckForUpdate

### UpdateManager.onCheckForUpdate(function callback)

Listens for the event that a request for checking for updates is sent to the backend. The backend automatically checks for updates when the mini app is cold started. The developer doesn't need to trigger this method.

## Parameters

### Function callback

Callback function for the event to make a request for checking for updates is sent to the backend.

### Object response

| Attribute | Type    | Description                                   |
| :-------- | :------ | :-------------------------------------------- |
| hasUpdate | Boolean | Determines Whether a new version is available |

## onUpdateFailed

### UpdateManager.onUpdateFailed(function callback)

Listens for the mini app update failure event. The client triggers the download when a new version is available (the developer doesn't need to trigger this method). A callback is performed when the download fails (probably due to network errors).

## Parameters

### Function callback

Callback function for the Mini app update failure event.

## onUpdateReady

### UpdateManager.onUpdateReady(function callback)

Listens for the event that a newer mini app version is available. The client actively triggers the download (the developer doesn't need to trigger this method). A callback is performed after successful download.

## Parameters

### Function callback

Callback function for the event to show a newer Mini app version is available.
