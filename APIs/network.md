---
title: "Network"
slug: "network"
excerpt: "This sections consists of list of network related APIs."
hidden: false
createdAt: "Wed Apr 19 2023 07:54:28 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Wed Nov 29 2023 10:14:53 GMT+0000 (Coordinated Universal Time)"
layout: "default"
parent: "APIs"
has_children: true
has_toc: false
nav_order: 6
---
# Network 
This sections consists of list of network related APIs.

***

# Request

| Name                           | Feature Description                 |
| :----------------------------- | :---------------------------------- |
| [request](network/request#request) | Initiates an HTTPS network request. |

# RequestTask

| Name                                                                                           | Feature Description                           |
| :--------------------------------------------------------------------------------------------- | :-------------------------------------------- |
| [RequestTask.abort](network/request#requesttaskabort-1)                                            | Aborts a request task.                        |
| [RequestTask.offHeadersReceived](network/request#requesttaskoffheadersreceivedfunction-listener-1) | Unlistens for the HTTP response header event. |
| [RequestTask.onHeadersReceived](network/request#requesttaskonheadersreceivedfunction-listener-1)   | Listens for the HTTP response header event.   |

# Upload

| Name                                              | Feature Description                     |
| :------------------------------------------------ | :-------------------------------------- |
| [uploadFile](network/upload#uploadfile-object-object) | Uploads a local resource to the server. |

# UploadTask

| Name                                                                                      | Feature Description                             |
| :---------------------------------------------------------------------------------------- | :---------------------------------------------- |
| [UploadTask.abort()](network/upload#uploadtaskabort)                                          | Aborts an upload task.                          |
| [UploadTask.offProgressUpdate](network/upload#uploadtaskoffprogressupdatefunction-callback)   | Unlistens for the upload progress change event. |
| [UploadTask.onProgressUpdate](network/upload#uploadtaskonprogressupdatefunction-callback)     | Listens for the upload progress change event.   |
| [UploadTask.offHeadersReceived](network/upload#uploadtaskoffheadersreceivedfunction-callback) | Unlistens for the HTTP response header event.   |
| [UploadTask.onHeadersReceived](network/upload#uploadtaskonheadersreceivedfunction-callback)   | Listens for the HTTP response header event.     |
