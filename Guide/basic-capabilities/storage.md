---
title: "Storage"
slug: "storage-copy"
excerpt: "This section explains the concept of storage."
hidden: false
createdAt: "Mon May 08 2023 06:17:00 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Tue Nov 28 2023 10:30:13 GMT+0000 (Coordinated Universal Time)"
layout: "default"
parent: "Basic Capabilities"
grand_parent: "Guide"
nav_order: 2
---
# Storage 
This section explains the concept of storage.

***

Each Mini Program has its own local cache. You can read, write, and clear the local cache via [wx.setStorage/wx.setStorageSync](../../APIs/data-cache#setstoragesync), [wx.getStorage/wx.getStorageSync](../../APIs/data-cache#getstoragesync), [wx.clearStorage/wx.clearStorageSync](../../APIs/data-cache#clearstorage-object-object), and [wx.removeStorage/wx.removeStorageSync](../../APIs/data-cache#removestorage-object-object).

## Isolation Policy

The storage limit of a Mini Program is 10 MB for a user. Storage is isolated based on users. On the same device, user A cannot read the data of user B. A Mini Program's user cannot read or write data of another Mini Program.

## Erasion Rules

Local cache files are erased only when the code package is erased.
