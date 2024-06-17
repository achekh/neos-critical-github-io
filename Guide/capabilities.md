---
title: "Backend assisted capabilities"
slug: "capabilities"
excerpt: ""
hidden: false
metadata: 
  image: []
  robots: "index"
createdAt: "Thu May 18 2023 06:27:13 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Fri Jul 14 2023 11:24:31 GMT+0000 (Coordinated Universal Time)"
layout: "default"
parent: "Guide"
has_children: true
has_toc: false
nav_order: 8
---
# Backend assisted capabilities 
*** 
This section goes over the Mini App capabilities that require backend integration:

- [Sending push notifications](capabilities/sending-push-notifications)
- [Retrieving user information](capabilities/retrieving-user-information)
- [Accepting payments](capabilities/accepting-payments)

## API requests

### Common parameters

| Parameter | Description                  | Type   | Remarks                                                                                    |
| :-------- | :--------------------------- | :----- | :----------------------------------------------------------------------------------------- |
| appid     | Mini App ID                  | String |                                                                                            |
| timestamp | Unix epoch in milliseconds   | Long   | Validate the request for a valid period, the default  request's valid period is 5 minutes. |
| sign      | Encrypted request parameters | String | Use SHA256 encryption.                                                                     |

### Signing the request parameters

Signing steps:

1. List all the request parameters and their values except for sign.
2. Add Mini App secret to the list of parameters (you can get the secret from the Mini App developer platfrom), key is `secret`.
3. Sort all parameters (including secret) alphabetically.
4. Concatenate the sorted parameters.
5. Generate the SHA256 hex of the concatenated sorted parameters.

Code sample:

```javascript
// NodeJS
import { createHash } from 'crypto';

// List all parameters except of sign:
const parameters = ["appid=7sao49ynf5vw48l", "timestamp=1685274898", "secret=eghhc4s5vxvd5wqzkmkl"];
// Sort parameters alphabetically
const sortedParameters = ["appid=7sao49ynf5vw48l", "secret=eghhc4s5vxvd5wqzkmkl", "timestamp=1685274898"];
// Concatinate parameters
const concatenatedParameters = sortedParameters.join(); // appid=7sao49ynf5vw48lsecret=eghhc4s5vxvd5wqzkmkltimestamp=1685274898
// Generate SHA256 signature
const signature = createHash('sha256').update(concatenatedParameters).digest('hex');
```

### Error codes

| Error code | Description                                 |
| :--------- | :------------------------------------------ |
| 2000       | Failed to verify signature.                 |
| 2001       | Request timeout.                            |
| 2002       | The user has not opened the open interface. |
