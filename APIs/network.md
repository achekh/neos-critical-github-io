---
title: "Network"
slug: "network"
excerpt: "This sections consists of list of network related APIs."
hidden: false
createdAt: "Wed Apr 19 2023 07:54:28 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Wed Nov 29 2023 10:14:53 GMT+0000 (Coordinated Universal Time)"
layout: "default"
parent: "APIs"
has_chidlren: true
---
# Network 
This sections consists of list of network related APIs.

***

# Request

| Name                           | Feature Description                 |
| :----------------------------- | :---------------------------------- |
| [request](doc:request#request) | Initiates an HTTPS network request. |

# RequestTask

| Name                                                                                           | Feature Description                           |
| :--------------------------------------------------------------------------------------------- | :-------------------------------------------- |
| [RequestTask.abort](doc:request#requesttaskabort-1)                                            | Aborts a request task.                        |
| [RequestTask.offHeadersReceived](doc:request#requesttaskoffheadersreceivedfunction-listener-1) | Unlistens for the HTTP response header event. |
| [RequestTask.onHeadersReceived](doc:request#requesttaskonheadersreceivedfunction-listener-1)   | Listens for the HTTP response header event.   |

# Upload

| Name                                              | Feature Description                     |
| :------------------------------------------------ | :-------------------------------------- |
| [uploadFile](doc:upload#uploadfile-object-object) | Uploads a local resource to the server. |

# UploadTask

| Name                                                                                      | Feature Description                             |
| :---------------------------------------------------------------------------------------- | :---------------------------------------------- |
| [UploadTask.abort()](doc:upload#uploadtaskabort)                                          | Aborts an upload task.                          |
| [UploadTask.offProgressUpdate](doc:upload#uploadtaskoffprogressupdatefunction-callback)   | Unlistens for the upload progress change event. |
| [UploadTask.onProgressUpdate](doc:upload#uploadtaskonprogressupdatefunction-callback)     | Listens for the upload progress change event.   |
| [UploadTask.offHeadersReceived](doc:upload#uploadtaskoffheadersreceivedfunction-callback) | Unlistens for the HTTP response header event.   |
| [UploadTask.onHeadersReceived](doc:upload#uploadtaskonheadersreceivedfunction-callback)   | Listens for the HTTP response header event.     |
