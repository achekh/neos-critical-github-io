---
title: "Basic"
slug: "basics-api"
excerpt: "This section consists of all basic APIs of Mini App."
hidden: false
metadata: 
  image: []
  robots: "index"
createdAt: "Tue Mar 14 2023 10:49:29 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Fri Jul 14 2023 11:11:32 GMT+0000 (Coordinated Universal Time)"
---
## CanIUse

| Name                         | Feature Description                                                                                               |
| :--------------------------- | :---------------------------------------------------------------------------------------------------------------- |
| [canIUse](doc:can-i-use-api) | Determines whether the Mini App APIs, callbacks, parameters, and components are available on the current version. |

## System

| Name                                                        | Feature Description              |
| :---------------------------------------------------------- | :------------------------------- |
| [getSystemInfoSync](doc:system-api#getsysteminfosync)       | Sync version of `getSystemInfo`. |
| [getSystemInfo](doc:system-api#getsysteminfo-object-object) | Gets the system information.     |

## Update

| Name                                              | Feature Description                                                                   |
| :------------------------------------------------ | :------------------------------------------------------------------------------------ |
| [getUpdateManager](doc:update#wxgetupdatemanager) | Gets the globally unique version of the update manager for managing Mini App updates. |

## UpdateManager

| Name                                                                                    | Feature Description                                                                                |
| :-------------------------------------------------------------------------------------- | :------------------------------------------------------------------------------------------------- |
| [UpdateManager.applyUpdate](doc:update#updatemanagerapplyupdate)                        | Forces the Mini App to restart and update to the new version.                                      |
| [UpdateManager.onCheckForUpdate](doc:#updatemanageroncheckforupdatefunction-callback)   | Listens for the event that a request for checking for updates has been sent to the WeChat backend. |
| [UpdateManager.onUpdateFailed](doc:update#updatemanageronupdatefailedfunction-callback) | Listens for the Mini App update failure event.                                                     |
| [UpdateManager.onUpdateReady](doc:update#updatemanageronupdatereadyfunction-callback)   | Listens for the event that a newer Mini App version is available.                                  |

# Mini App

## Lifecycle

| Name                                                                        | Feature Description                              |
| :-------------------------------------------------------------------------- | :----------------------------------------------- |
| [getLaunchOptionsSync](doc:mini-app-api#getlaunchoptionssync-object-object) | Gets the parameter when the Mini App is started. |

## App-level events

| Name                                                                 | Feature Description                       |
| :------------------------------------------------------------------- | :---------------------------------------- |
| [onError](doc:mini-app-api#wxonerror)                                | Listens for Mini App error events.        |
| [offError](doc:mini-app-api#wxofferror)                              | Unlistens for Mini App error events.      |
| [onThemeChange](doc:mini-app-api#wxonthemechangefunction-listener)   | Listens for system theme change events.   |
| [offThemeChange](doc:mini-app-api#wxoffthemechangefunction-listener) | Unlistens for system theme change events. |

## Debugging

| Name                                               | Feature Description                  |
| :------------------------------------------------- | :----------------------------------- |
| [setEnableDebug](doc:debugging-api#setEnableDebug) | Sets whether to toggle on debugging. |
| [getLogManager](doc:debugging-api-getLogManager)   | Gets the log manager object.         |

## Consoles

| Name                                                   | Feature Description                      |
| :----------------------------------------------------- | :--------------------------------------- |
| [console.debug](doc:debugging-api#console.debug)       | Prints DEBUG logs to the debug panel.    |
| [console.error](doc:debugging-api#console.error)       | Prints ERROR logs to the debug panel.    |
| [console.group](doc:debugging-api#console.group)       | Creates a group in the debug panel.      |
| [console.groupEnd](doc:debugging-api#console.groupEnd) | Ends the group created by console.group. |
| [console.info](doc:debugging-api#console.info)         | Prints INFO logs to the debug panel.     |
| [console.log](doc:debugging-api#console.log)           | Prints LOG logs to the debug panel.      |
| [console.warn](doc:debugging-api#console.warn)         | Prints WARN logs to the debug panel.     |

## LogManager

| Name                                                   |    | Feature Description |
| :----------------------------------------------------- | :- | :------------------ |
| [LogManager.debug](doc:debugging-api#LogManager.debug) |    | Writes a DEBUG log. |
| [LogManager.info](doc:debugging-api#LogManager.info)   |    | Writes an INFO log. |
| [LogManager.log](doc:debugging-api#LogManager.log)     |    | Writes a LOG log.   |
| [LogManager.warn](doc:debugging-api#LogManager.warn)   |    | Writes a WARN log.  |
