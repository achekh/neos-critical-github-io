---
title: "Data Cache"
slug: "data-cache"
excerpt: "This section consists of list of all APIS related with data storage."
hidden: false
createdAt: "Wed Apr 19 2023 10:19:41 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Wed Nov 29 2023 10:24:53 GMT+0000 (Coordinated Universal Time)"
layout: "default"
parent: "APIs"
---
# Data Cache 
*** 
| Name                                                                  | Feature Description                                                        |
| :-------------------------------------------------------------------- | :------------------------------------------------------------------------- |
| [setStorageSync](doc:data-cache#setstoragesync)                       | Stores the data in the specified key in the local cache.                   |
| [setStorage](doc:data-cache#setstorage-object-object)                 | Stores the data in the specified key in the local cache.                   |
| [removeStorageSync](doc:data-cache#removestoragesync-object-object)   | Sync version of `removeStorage`.                                           |
| [removeStorage](doc:data-cache#removestorage-object-object)           | Removes the specified key from the local cache.                            |
| [getStorageSync](doc:data-cache#getstoragesync)                       | Synchronously gets the content of the specified key from the local cache.  |
| [getStorageInfoSync](doc:data-cache#getstorageinfosync-object-object) | Sync version of `getStorageInfo`.                                          |
| [getStorageInfo](doc:data-cache#wxgetstorageinfoobject-object)        | Asynchronously gets the information of the current storage.                |
| [getStorage](doc:data-cache#getstorage-object-object)                 | Asynchronously gets the content of the specified key from the local cache. |
| [clearStorageSync](doc:data-cache#clearstoragesync)                   | Sync version of `clearStorage`.                                            |
| [clearStorage](doc:data-cache#clearstorage-object-object)             | Clears the local data cache.                                               |

# setStorage (Object object)

Stores the data in the specified key in the local cache. The original content will be overwritten in the key The data will be always available unless the user actively deletes it, or it is cleaned up by the system for reasons related to storage space. The maximum size of data stored per key is 1 MB, and there can be up to 10 MB of data in total.

# Parameters

**Object object**

| Attribute | Type     | Required | Description                                                                                                                                      |
| :-------- | :------- | :------- | :----------------------------------------------------------------------------------------------------------------------------------------------- |
| key       | String   | Yes      | The key specified in the local cache.                                                                                                            |
| data      | Any      | Yes      | The content that needs to be stored. Only objects of native types, dates, and objects that can be serialized via `JSON.stringify` are supported. |
| success   | Function | No       | Callback function for a successful API call.                                                                                                     |
| fail      | Function | No       | Callback function for a failed API call.                                                                                                         |
| complete  | Function | No       | Callback function for an API call end (executed for both successful and failed calls).                                                           |

# Sample code

```javascript JavaScript
wx.setStorage({
  key:"key",
  data:"value"
})
```

# setStorageSync

Synchronous version of wx.setStorage.

## Parameters

**string key** 

The key specified in the local cache

**any data** 

The content that needs to be stored. Only objects of native types, dates, and objects that can be serialized via `JSON.stringify` are supported.

### Sample code

```javascript JavaScript
try {
	wx.setStorageSync('key', 'value')
} catch (e) {
	// log exception
}
```

# removeStorage (Object object)

Removes the specified key from the local cache.

# Parameters

**Object object**

| Attribute | Type     | Required | Description                                                                            |
| :-------- | :------- | :------- | :------------------------------------------------------------------------------------- |
| key       | String   | Yes      | The key specified in the local cache.                                                  |
| success   | function | No       | Callback function for a successful API call.                                           |
| fail      | function | No       | Callback function for a failed API call.                                               |
| complete  | function | No       | Callback function for an API call end (executed for both successful and failed calls). |

### Sample code

```javascript JavaScript
wx.removeStorage({
  key: 'key',
  success (res) {
  	console.log(res)
  }
})
```

# removeStorageSync (Object object)

Synchronous version of wx.removeStorage.

# Parameters

**string key** 

The key specified in the local cache

### Sample code

```javascript JavaScript
try {
	wx.removeStorageSync('key')
} catch (e) {
	// Do something when catch error
}
```

# getStorage (Object object)

Asynchronously gets the content of the specified key from the local cache.

# Parameters

**Object object**

| Attribute | Type     | Required | Description                                                                            |
| :-------- | :------- | :------- | :------------------------------------------------------------------------------------- |
| key       | String   | Yes      | The key specified in the local cache.                                                  |
| success   | Function | No       | Callback function for a successful API call.                                           |
| fail      | Function | No       | Callback function for a failed API call.                                               |
| complete  | Function | No       | Callback function for an API call end (executed for both successful and failed calls). |

## `object.success` callback function

# Parameters

**Object res**

| Attribute | Type | Description                       |
| :-------- | :--- | :-------------------------------- |
| data      | Any  | Content corresponding to the key. |

# Sample code

```javascript JavaScript
wx.getStorage({
  key: 'key',
  success (res) {
  	console.log(res.data)
  }
})
```

# getStorageSync

Synchronously gets the content of the specified key from the local cache.

# Parameters

**string key** 

The key specified in the local cache.

## Returned value

**any** 

The content corresponding to the key.

### Sample code

```javascript JavaScript
try {
  var value = wx.getStorageSync('key')
  if (value) {
  // Do something with return value
  }
} catch (e) {
	// Do something when catch error
}
```

# wx.getStorageInfo(Object object)

Asynchronously gets the information of the current storage.

# Parameters

**Object object**

| Attribute | Type     | Required | Description                                                                            |
| :-------- | :------- | :------- | :------------------------------------------------------------------------------------- |
| success   | Function | No       | Callback function for a successful API call.                                           |
| fail      | Function | No       | Callback function for a failed API call.                                               |
| complete  | Function | No       | Callback function for an API call end (executed for both successful and failed calls). |

## `object.success` callback function

# Parameters

**Object object**

| Attribute   | Type    | Description                      |
| :---------- | :------ | :------------------------------- |
| keys        | Array   | All keys in the current storage. |
| currentSize | Number0 | Currently used space size in KB. |
| limitSize   | Number  | Restricted space size in KB.     |

### Sample code

```javascript JavaScript
wx.getStorageInfo({
  success(res) {
    console.log(res.keys)
    console.log(res.currentSize)
    console.log(res.limitSize)
  }
})
```

# getStorageInfoSync (Object object)

Synchronous version of wx.getStorageInfo.

## Returned value

**Object object**

| Attribute   | Type   | Description                      |
| :---------- | :----- | :------------------------------- |
| keys        | Array  | All keys in the current storage. |
| currentSize | Number | Currently used space size in KB. |
| limitSize   | Number | Restricted space size in KB.     |

# Sample code

```javascript JavaScript
try {
  const res = wx.getStorageInfoSync()
  console.log(res.keys)
  console.log(res.currentSize)
  console.log(res.limitSize)
} catch (e) {
  // Do something when catch error
}
```

# clearStorage (Object object)

Clears the local data cache.

# Parameters

**Object object**

| Attribute | Type     | Required | Description                                                                            |
| :-------- | :------- | :------- | :------------------------------------------------------------------------------------- |
| success   | Function | No       | Callback function for a successful API call.                                           |
| fail      | Function | No       | Callback function for a failed API call.                                               |
| complete  | Function | No       | Callback function for an API call end (executed for both successful and failed calls). |

### Sample code

```javascript JavaScript
wx.clearStorage()
```

# clearStorageSync

Synchronous version of wx.clearStorage.

### Sample code

```javascript JavaScript
try {
	wx.clearStorageSync()
} catch(e) {
	// Do something when catch error
}
```
