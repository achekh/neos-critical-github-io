---
title: "Update Mechanism"
slug: "update-mechanism"
excerpt: "This section explains the concept of update mechanism."
hidden: true
metadata: 
  robots: "index"
createdAt: "Tue May 02 2023 10:15:17 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Wed May 03 2023 10:17:29 GMT+0000 (Coordinated Universal Time)"
layout: "default"
parent: "Mini Program Runtime"
grand_parent: "Guide"
---
# Update Mechanism 
*** 
# Update Mechanism of Mini Programs

## Update When Not Enabled

After developers release the new version of Mini Program at the admin console, the old version cached locally may still be enabled. Mini app will check at several time points if the new version exists locally. If yes, the Mini Program will be automatically updated to the latest version. In general, the new version released by developers cannot cover all the users immediately. It may take at most 24 hours to send the new version data to all the users. The users will be prompted to update to the latest version before enabling the Mini Program next time.

## Update When Enabled

Whenever a Mini Program is enabled via **cold startup**, it will check if a new version exists. If yes, the code package of the new version will be downloaded asynchronously and it will be started with the local client package, which means the new version of the Mini Program will not be applied until the next cold startup.

If you need to apply the latest version immediately, use the [wx.getUpdateManager](<>) API.

```Text code
const updateManager = wx.getUpdateManager()

updateManager.onCheckForUpdate(function (res) {
  // Callback after request of new version data
  console.log(res.hasUpdate)
})

updateManager.onUpdateReady(function () {
  wx.showModal({
    title: 'Update prompt',
    content: 'The new version is ready. Re-start now?',
    success(res) {
      if (res.confirm) {
        // The new version is downloaded. Call applyUpdate to apply the new version and re-start the Mini Program
        updateManager.applyUpdate()
      }
    }
  })
})

updateManager.onUpdateFailed(function () {
  // Failed to download the new version
})
```
