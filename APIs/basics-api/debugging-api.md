---
title: "Debugging"
slug: "debugging-api"
excerpt: "APIs related to debugging the functionality of Mini apps."
hidden: false
createdAt: "Mon Apr 17 2023 07:08:48 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Wed Nov 29 2023 06:12:48 GMT+0000 (Coordinated Universal Time)"
layout: "default"
parent: "Basic"
grand_parent: "APIs"
---
- [setEnableDebug](doc:debugging-api#setenabledebug-object-object)
- [getLogManager](doc:debugging-api#wxgetlogmanager)
- [console](doc:debugging-api#console)
  - [console.debug](doc:debugging-api#debug)
  - [console.error](doc:debugging-api#error)
  - [console.group](doc:debugging-api#group)
  - [console.groupEnd](doc:debugging-api#groupend)
  - [console.info](doc:debugging-api#info)
  - [console.log](doc:debugging-api#log)
  - [console.warn](doc:debugging-api#warn)
- [LogManager](doc:debugging-api#logmanager)
  - LogManager.debug
  - LogManager.info
  - LogManager.warn
  - LogManager.error

# setEnableDebug (Object object)

Sets whether to toggle on debugging. This toggle also works for production versions.

# Parameters

Object object

| Attribute   | Type     | Default | Required | Description                                                                         |
| :---------- | :------- | :------ | :------- | :---------------------------------------------------------------------------------- |
| enableDebug | Boolean  |         | Yes      | Whether to enable debugging.                                                        |
| success     | Function |         | No       | Callback function for a successful API call.                                        |
| fail        | Function |         | No       | Callback function for a failed API call.                                            |
| complete    | Function |         | No       | Callback function for API call end (executed for both successful and failed calls). |

### Sample code

```javascript JavaScript
// Enable debugging
wx.setEnableDebug({
	enableDebug: true
})

// Disable debugging
wx.setEnableDebug({
	enableDebug: false
})
```

## Tips

Another way to open debugging in the official version is to open debugging in the development version or trial version first, and then switch to the official version to see vConsole.

# wx.getLogManager

## LogManager wx.getLogManager(Object object)

Gets the global log manager object.

## Parameters

**Object object**

| Attribute | Type   | Default | Required | Description                                                                                                                                                        |
| :-------- | :----- | :------ | :------- | :----------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| level     | Number | 0       | No       | Whether to log the calls of lifecycle functions of `App` and `Page` as well as functions in the namespace. Valid values: `0` (yes); `1` (no). Default value: `0` . |

## Returned value

LogManager

### Sample code

```javascript JavaScript
const logger = wx.getLogManager({level: 1})
logger.log({str: 'hello world'}, 'basic log', 100, [1, 2, 3])
logger.info({str: 'hello world'}, 'info log', 100, [1, 2, 3])
logger.debug({str: 'hello world'}, 'debug log', 100, [1, 2, 3])
logger.warn({str: 'hello world'}, 'warn log', 100, [1, 2, 3])
```

# Console

Prints logs in the debug panel. `console` is a global object and can be accessed directly. When running the Mini app on a device it outputs logs to vConsole.

### Methods

**console.debug()** Prints DEBUG logs to the debug panel.

**console.log()** Prints LOG logs to the debug panel.

**console.info()** Prints INFO logs to the debug panel.

**console.warn()** Prints WARN logs to the debug panel.

**console.error()** Prints ERROR logs to the debug panel.

**console.group(string label)** Creates a group in the debug panel. The subsequent output will be indented to indicate that the content belongs to the current group. The group ends after `console.groupEnd()` is called.

**console.groupEnd()** Ends the group created by [console.group](doc:debugging-api#group).

> 📘 Note
> 
> - Due to the limited features of vConsole and the differences in the console supported by different clients, we recommend the developer to only use the methods provided in this document in the Mini app.
> - For restrictions on displaying certain content, see [vConsole](<>).

## .debug

**console.debug() ** Prints DEBUG logs to the debug panel.

### Parameters

**any ...args** Logs content. There can be multiple log entries.

## .error

**console.error()** Prints ERROR logs to the debug panel.

### Parameters

**any ...args** Logs content. There can be multiple log entries.

## .group

**console.group(string label)** Creates a group in the debug panel. The subsequent output will be indented to indicate that the content belongs to the current group. The group ends after [console.groupEnd](doc:debugging-api#groupend) is called.

### Parameters

**string label**  Optional group label

> 📘 Note
> 
> It's valid only in DevTools and is an empty function implementation in vConsole.

## .groupEnd

**console.groupEnd()** Ends the group created by [console.group](doc:debugging-api#group).

> 📘 Note
> 
> It's valid only in DevTools and is an empty function implementation in vConsole.

## .info

**console.info()** Prints INFO logs to the debug panel.

**any ...args** Logs content. There can be multiple log entries.

## .log

**console.log()** Prints LOG logs to the debug panel.

### Parameters

**any ...args** Log content. There can be multiple log entries.

## .warn

**console.warn() ** Prints WARN logs to the debug panel.

### Parameters

**any ...args** Logs content. There can be multiple log entries.

# LogManager

The log manager instance, which can be obtained through [getLogManager](doc:debugging-api#wxgetlogmanager).

### Methods

**LogManager.debug()** Writes DEBUG logs.

**LogManager.info()** Writes INFO logs.

**LogManager.log()** Writes LOG logs.

**LogManager.warn()** Writes WARN logs.

> 📘 Note
> 
> - A maximum of 5 MB log content can be retained, and old log content will be deleted after the size exceeds 5 MB.
> - The user can upload printed logs by using the `open-type="feedback"` of the `<Button>` component. The developer can view it on the "Feedback Management" page on the left sidebar in the Mini app console.
> - The base library logs the calls of lifecycle functions of `App` and `Page` as well as functions in the namespace by default.

## .debug

**LogManager.debug()** Writes DEBUG logs.

### Parameters

**Object|Array|number|string ...args** Logs content. There can be multiple log entries. The total size of parameters per call cannot exceed 100 KB.

## .info

**LogManager.info()** Writes INFO logs.

### Parameters

**Object|Array|number|string ...args** Logs content. There can be multiple log entries. The total size of parameters per call cannot exceed 100 KB.

## .log

**LogManager.log()** Writes LOG logs.

### Parameters

**Object|Array|number|string ...args** Logs content. There can be multiple log entries. The total size of parameters per call cannot exceed 100 KB.

## .warn

**LogManager.warn()** Writes WARN logs.

### Parameters

**Object|Array|number|string ...args** Logs content. There can be multiple log entries. The total size of parameters per call cannot exceed 100 KB.
