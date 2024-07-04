---
title: "Upload"
slug: "upload"
excerpt: "This section consists of the APIs related with Upload feature in the Mini App."
hidden: false
createdAt: "Wed Apr 19 2023 08:36:33 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Wed Nov 29 2023 10:20:52 GMT+0000 (Coordinated Universal Time)"
layout: "default"
parent: "Network"
grand_parent: "APIs"
nav_order: 2
---
# Upload 
This section consists of the APIs related with Upload feature in the Mini App.

***

- [uploadFile](upload#uploadfile-object-object)
- [UploadTask](upload#uploadtask)
  - UploadTask.abort()
  - UploadTask.onProgressUpdate
  - UploadTask.offProgressUpdate
  - UploadTask.onHeadersReceived
  - UploadTask.offHeadersReceived

# uploadFile (Object object)

Uploads a local resource to the server. The client initiates an HTTPS POST request with content-type as multipart/form-data. See [Network](../network) before using this API.

# Parameters

**Object object**

| Attribute | Type     | Required | Description                                                                                                         |
| :-------- | :------- | :------- | :------------------------------------------------------------------------------------------------------------------ |
| url       | String   | Yes      | The server address.                                                                                                 |
| filePath  | String   | Yes      | Local path of the file resource to be uploaded.                                                                     |
| name      | String   | Yes      | The key corresponding to the file, which the developer can use to get the binary content of the file on the server. |
| header    | Object   | No       | HTTP request headers, where `Referer` cannot be set.                                                                |
| formData  | Object   | No       | Additional form data in the HTTP request.                                                                           |
| success   | Function | No       | Callback function for a successful API call.                                                                        |
| fail      | Function | No       | Callback function for a failed API call.                                                                            |
| complete  | Function | No       | Callback function for an API call end (executed for both successful and failed calls).                              |

## `object.success` callback function

# Parameters

**Object res**

| Attribute  | Type   | Description                                  |
| :--------- | :----- | :------------------------------------------- |
| data       | Dtring | The data returned by the server.             |
| statusCode | Number | The HTTP status code returned by the server. |

### Returned value

[UploadTask](upload#uploadtask) Listens for the upload progress change event and cancels the upload task.

### Sample code

```javascript
// JavaScript
wx.chooseImage({
  success (res) {
    const tempFilePaths = res.tempFilePaths
    wx.uploadFile({
      url: 'https://test.url/upload', // This is just an example but not a real API address.
      filePath: tempFilePaths[0],
      name: 'file',
      formData: {
      	'user': 'test'
      },
      success (res){
        const data = res.data
        //do something
      }
    })
  }
})
```

# UploadTask

Listens for the upload progress change event and cancels the upload task.

## Methods

- **UploadTask.abort()** 

Aborts an upload task.

- **UploadTask.onProgressUpdate(function callback)**

Listens for the upload progress change event.

- **UploadTask.offProgressUpdate(function callback)**

Unlistens for the upload progress change event.

- **UploadTask.onHeadersReceived(function callback)**

```

```

- **UploadTask.offHeadersReceived(function callback)**

Unlistens for the HTTP response header event.

### Sample code

```javascript
// JavaScript
const uploadTask = wx.uploadFile({
  url: 'https://test.url/upload', // This is just an example but not a real API address.
  filePath: tempFilePaths[0],
  name: 'file',
  formData: {
 	 user: 'test'
  },
  success(res) {
 	 const data = res.data
  	// do something
  }
 })
  
 uploadTask.onProgressUpdate((res) => {
    console.log('Upload progress', res.progress)
    console.log('Amount of uploaded data', res.totalBytesSent)
    console.log('Total amount of data expected to be uploaded', res.totalBytesExpectedToSend)
})
uploadTask.abort() // Cancel the upload task
```

# UploadTask.abort()

Aborts an upload task.

# UploadTask.offHeadersReceived(function callback)

Unlistens for the HTTP response header event.

# Parameters

**function callback**

Callback function for the HTTP response header event

# UploadTask.offProgressUpdate(function callback)

Unlistens for the upload progress change event.

# Parameters

**function callback**

Callback function for the upload progress change event

# UploadTask.onHeadersReceived(function callback)

Listens for the HTTP response header event, which occurs earlier than the request completion event.

# Parameters

**function callback**

Callback function for the HTTP response header event

**Object res**

| Attribute | Type   | Description                                  |
| :-------- | :----- | :------------------------------------------- |
| header    | Object | HTTP response header returned by the server. |

# .onProgressUpdate

# UploadTask.onProgressUpdate(function callback)

Listens for the upload progress change event.

# Parameters

**function callback** Callback function for the upload progress change event

**Object res**

| Attribute                | Type   | Description                                            |
| :----------------------- | :----- | :----------------------------------------------------- |
| progress                 | Number | Upload progress in percentage.                         |
| totalBytesSent           | Number | Amount of uploaded data in bytes.                      |
| totalBytesExpectedToSend | Number | Total amount of data expected to be uploaded in bytes. |

# UploadTask.abort()

Aborts an upload task.

# UploadTask.onProgressUpdate(function callback)

Listens for the upload progress change event.

# Parameters

**function callback** Callback function for the upload progress change event

**Object res**

| Attribute                | Type   | Description                                            |
| :----------------------- | :----- | :----------------------------------------------------- |
| progress                 | Number | Upload progress in percentage.                         |
| totalBytesSent           | Number | Amount of uploaded data in bytes.                      |
| totalBytesExpectedToSend | Number | Total amount of data expected to be uploaded in bytes. |

# UploadTask.offProgressUpdate(function callback)

Unlistens for the upload progress change event.

# Parameters

**function callback** Callback function for the upload progress change event

# UploadTask.offHeadersReceived(function listener)

Unlistens for the HTTP response header event.

# Parameters

**function listener** The listener function passed in when onHeadersReceived is called. If this parameter is not passed in, all listener functions will be removed.

### Sample code

```javascript
// JavaScript
const listener = function (res) { console.log(res) }

UploadTask.onHeadersReceived(listener)
UploadTask.offHeadersReceived(listener) // You should pass in the same function object as for the listener.
```

# UploadTask.onHeadersReceived(function listener)

Listens for the HTTP response header event, which occurs earlier than the request completion event.

# Parameters

**function listener** Listener function for the HTTP response header event

**Object res**

| Attribute | Type   | Description                                  |
| :-------- | :----- | :------------------------------------------- |
| header    | Object | HTTP response header returned by the server. |
