---
title: "Request"
slug: "request"
excerpt: "This API initiates a HTTPS network request."
hidden: false
createdAt: "Wed Apr 19 2023 07:56:33 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Wed Nov 29 2023 10:19:30 GMT+0000 (Coordinated Universal Time)"
layout: "default"
parent: "Network"
grand_parent: "APIs"
nav_order: 1
---
# Request 
This API initiates a HTTPS network request.

***

- [request](request#request)
- [RequestTask](request#requesttask)
  - RequestTask.abort()
  - RequestTask.offHeadersReceived
  - RequestTask.onHeadersReceived

# Request

Initiates an HTTPS network request. See [Network](../network) before using this API.

## Parameters

**Object object**

| Attribute | Type | Default | Required | Description |
| :-------- | :--- | :------ | :------- | :---------- |
| url | String |  | Yes | The server API address. |
| data | String/Object/Ar  \nrayBuffer |  | No | Request parameters. |
| header | Object |  | No | Request headers, where `Referer` cannot be set. |
| content-type |  | application/json |  | Content-type header value. |
| method | String | GET | No | HTTP request method. |
| dataType | String | json | No | Returned data format. |
| responseType | String | text | No | Response data type. |
| success | Function |  | No | Callback function for a successful API call. |
| fail | Function |  | No | Callback function for a failed API call. |
| complete | Function |  | No | Callback function for an API call end (executed for  \nboth successful and failed calls). |

## Valid values of `object.method`

| Value   | Description           |
| :------ | :-------------------- |
| OPTIONS | HTTP request: OPTIONS |
| HEAD    | HTTP request: HEAD    |
| POST    | HTTP request: POST    |
| PUT     | HTTP request: PUT     |
| DELETE  | HTTP request: DELETE  |
| TRACE   | HTTP request: TRACE   |
| CONNECT | HTTP request: CONNECT |

## Valid values of `object.dataType`

| Value        | Description                                                                               |
| :----------- | :---------------------------------------------------------------------------------------- |
| json         | The returned data is in JSON format. `JSON.parse` will be performed on the returned data. |
| Other values | JSON.parse will not be performed on the returned data.                                    |

## Valid values of `object.responseType`

|             | The response data is text.        |
| :---------- | :-------------------------------- |
| text        | The response data is text.        |
| arraybuffer | The response data is ArrayBuffer. |

**`object.success` callback function**

# Parameters

**Object res**

| Attribute  | Type                      | Description                                       |
| :--------- | :------------------------ | :------------------------------------------------ |
| data       | string/Object/Arraybuffer | The data returned by the server.                  |
| statusCode | number                    | The HTTP status code returned by the server.      |
| header     | Object                    | The HTTP response headers returned by the server. |

## Returned value

[RequestTask](network#requesttask)

Request task object

### `data` parameter description

The data eventually sent to the server is of string type. If the input data is of another type, it will be converted to the string type first. The conversion rules are as follows:

- Data of the `GET` method will be converted into a query string  
  `(encodeURIComponent(k)=encodeURIComponent(v)&encodeURIComponent(k)=encodeURIComponent(v)... ).`
- Data of the `POST` method with `header['content-type'] `being `application/json` will be JSON serialized.
- Data of the `POST` method with `header['content-type']` being `application/xwww-form-urlencoded` will be converted into a query string  
  `(encodeURIComponent(k)=encodeURIComponent(v)&encodeURIComponent(k)=encodeURIComponent(v)... ).`

### Sample code

```javascript
// JavaScript
wx.request({
  url: 'test.url', // This is just an example but not a real API address.
  data: {
    x: '',
    y: ''
  },
  header: {
    'content-type': 'application/json' // Default value
  },
  success(res) {
  	console.log(res.data)
  }
})
```

# RequestTask

Network request task object

## Methods

### [RequestTask.abort()](request#requesttaskabort-1)

Aborts a request task.

### [RequestTask.onHeadersReceived(function listener)](request#requesttaskonheadersreceivedfunction-listener-1)

Listens for the HTTP response header event, which occurs earlier than the request completion event.

### [RequestTask.offHeadersReceived(function listener)](request#requesttaskoffheadersreceivedfunction-listener-1)

Unlistens for the HTTP response header event.

### Sample code

```javascript
// JavaScript
const requestTask = wx.request({
  url: 'test.url', // This is just an example but not a real API address.
  data: {
    x: '' ,
    y: ''
  },
  header: {
 	 'content-type': 'application/json'
  },
  success (res) {
 	  console.log(res.data)
  }
})
requestTask.abort() // Abort the request task
```

# RequestTask.abort()

Aborts a request task.

# RequestTask.onChunkReceived(function listener)

Listens for the Transfer-Encoding Chunk Received event, which is triggered when a new chunk is received.

# Parameters

## Function listener

Listener function for the Transfer-Encoding Chunk Received event

# Parameters

**Object res**

| Attribute | Type   | Description                                                    |
| :-------- | :----- | :------------------------------------------------------------- |
| res       | Object | The response returned each time the server returns a new chunk |

**res**

| Structure Attribute | Type        | Description               |
| :------------------ | :---------- | :------------------------ |
| data                | ArrayBuffer | The returned chunk buffer |

# RequestTask.onHeadersReceived(function listener)

Listens for the HTTP response header event, which occurs earlier than the request completion event.

# Parameters

## Function listener

Listener function for the HTTP response header event

# Parameters

**Object res**

| Attribute | Type   | Description                                     |
| :-------- | :----- | :---------------------------------------------- |
| header    | Object | The HTTP response header returned by the server |

# RequestTask.offChunkReceived(function listener)

Unlistens for the Transfer-Encoding Chunk Received event.

# Parameters

## Function listener

The listener function passed in when `onChunkReceived` is called. If this parameter is not passed in, all listener functions will be removed.

## Sample code

```javascript
// JavaScript
const listener = function (res) { console.log(res) }

RequestTask.onChunkReceived(listener)
RequestTask.offChunkReceived(listener) // You should pass in the same function object as for the listener.
```

# RequestTask.offHeadersReceived(function listener)

Unlistens for the HTTP response header event.

# Parameters

## Function listener

The listener function passed in when `onHeadersReceived` is called. If this parameter is not passed in, all listener functions will be removed.

### Sample code

```javascript
// JavaScript
const listener = function (res) { console.log(res) }

RequestTask.onHeadersReceived(listener)
RequestTask.offHeadersReceived(listener) // You should pass in the same function object as for the listener.
```
