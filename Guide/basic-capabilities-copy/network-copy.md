---
title: "Network"
slug: "network-copy"
excerpt: "This section explains the concept of network in Mini Programs/Games."
hidden: false
createdAt: "Mon May 08 2023 06:16:57 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Tue Nov 28 2023 10:11:12 GMT+0000 (Coordinated Universal Time)"
layout: "default"
parent: "Basic Capabilities"
grand_parent: "Guide"
---
# Network

When using web-related APIs in Mini Programs/Mini Games, developers should note the following issues in advance.

## 1. Configuration of Server Domain Name

Each Mini Program needs to be set with a communication domain name in advance. The Mini Program can only communicate with the specified domain name over the network. This includes normal HTTPS request (wx.request), file upload (wx.uploadFile, file download (wx.downloadFile), and WebSocket communication (wx.connectSocket).

From base library 2.4.0 and later, network APIs allow communication with LAN IP addresses, but **do not allow communication with the local device's IP address**.

UDP communication (wx.createUDPSocket) is supported from base library version 2.7.0 and later. Only communication with an IP address (different from the local device's IP address) in the same LAN are allowed.

### Configuration process

Configure the server domain name in **Mini Program Console > Settings > Development Settings > Server Domain Name**. 

**Configuration notes**:

- Domain names only support https (wx.request, wx.uploadFile, wx.downloadFile) and wss (wx.connectSocket) protocols.
- An IP address (except for the Mini Program's IP address in the LAN) or localhost cannot be used for a domain name.
- You can configure a port, such as <https://myserver.com:8080>. However after configuration, requests can only be sent to <https://myserver.com:8080>, and those sent to <https://myserver.com>, <https://myserver.com:9091> or another URL will fail.
- If you do not configure a port, such as <https://myserver.com>, the request URL cannot include a port, not even the default port 443; otherwise, requests sent to <https://myserver.com:443> will fail.
- The domain name must be ICP licensed.
- **For security reasons, `api.weixin.qq.com` cannot be configured as a server domain name, and related APIs cannot be called in Mini Programs.** Developers should save the AppSecret to the backend server and use the getAccessToken API to get access_token and call the relevant APIs via the server.
- Each API can be configured with up to 20 domain names.

## 2. Network Request

## Timeout

- The default timeout and maximum timeout are both 60s.
- The timeout can be configured in `app.json` or `game.json` via networktimeout.

## Use Limits

- The `referer` header of a network request is optional. Its format is always <https://servicewechat.com/{appid}/{version}/page-frame.html>, in which {appid} is the Mini Program's appid and `{version}` is the version number of the Mini Program. A version number of `0` means it is a developer version, trial version, or review version. A version number of `devtools` means it is the Weixin DevTools. Those with a version number other than the above ones are formal versions.
- The maximum concurrency of wx.request, wx.uploadFile, and wx.downloadFile is 10.
- The maximum concurrency of wx.connectSocket is 5.
- When the Mini Program is running in the background, if a network request does not end within 5s, an error message of `fail interrupted` will be called back. The network request API cannot be called until the Mini Program client is re-opened.

## Return value encoding

- The values returned by the server should be UTF-8 encoded. The Mini Program will try to convert non-UTF-8 encoded return values but may fail.
- The Mini Program automatically filters the BOM header (only one BOM header is filtered)

## Callback function

- As long the value returned by the server is received, the `success` callback is triggered regardless of `statusCode`. Determine the return value based on the business logic.

## 3. FAQ

## HTTPS certificate

**Mini Programs must use HTTPS/WSS to initiate a network request**. During the request, the system verifies the HTTPS certificate used by the server domain name. If the verification fails, the request is not successfully initiated. Due to system limitations, different platforms have different levels of stringency for certificates. To ensure the compatibility of Mini Programs, we recommend that developers configure the certificate according to the highest standard and use the relevant tools to check whether the existing certificate meets the requirements.

The requirements for certificates are as follows:

- The HTTPS certificate must be valid.
  - Use a trusted certificate, i.e., the root certificate has been built into the system.
  - The domain name of the website where the SSL certificate is deployed must be the same as the domain name for which the certificate was issued.
  - The certificate must not have expired.
  - The certificate's trust chain must be complete (server configuration is required).
- Self-signed certificates is not supported for iOS.
- Certificates in `iOS`must meet Apple's App Transport Security (ATS) requirements.
- TLS 1.2 or above is required. However, TLS 1.2 is not supported on some older Android models, so make sure HTTPS server supports TLS 1.2 or below.
- Some CAs may not be trusted by the operating system. Take note of the announcements of the Mini Program and other systems when selecting certificates.
  - Notice of Limits on WoSign and StartCom Certificates from Chrome 56/57 Kernel

> Certificate validity can be verified via the openssl s_client -connect example.com:443 command or other online tools.

In addition to the network request API, if there are exceptions in any other `HTTPS` requests in the Mini Program, such as failure to load HTTPS images or failure to play audio or video, follow the above process for troubleshooting.

## Skip domain name verification

In the Weixin DevTools, the  
`Do not verify the request domain name, TLS version, and HTTPS certificate in development environment` option can be enabled to skip verification of the server domain name. In this case, the server domain name will not be verified in the Weixin DevTools or when debugging mode is enabled on your phone.

**After the server domain name is configured, we recommend you disable this option during development and test the domain name on each platform to ensure it is correct.**

> If your phone can only send requests in debugging mode, confirm whether the domain name verification has been skipped and whether the server domain name and the certificate are correct configured.

# Communication over LAN

Base library 2.4.0 provides a variety of mDNS APIs such as wx.startLocalServiceDiscovery to get the IP addresses of devices that provide mDNS services in the LAN. The url parameter for wx.request/wx.connectSocket/wx.uploadFile/wx.downloadFile should be in the format of `${IP}:${PORT}/${PATH}`. The request or connection is successful only when the IP address is in the same IP address range as the mobile phone's IP address but is different from the local device's IP address (generally, it is in the same LAN, for example, connected to the same Wi-Fi network).

In this case, no security domain check is performed and https/wss is not necessarily required (http/ws can be used instead).

```Text code
wx.request({
  url: 'http://10.9.176.40:828'
  // The other parameters are omitted
})

wx.connectSocket({
  url: 'ws://10.9.176.42:828'
  // The other parameters are omitted
})
```

From base library 2.7.0 and later, we provide the wx.createUDPSocket API for UDP communication. The above communication rules apply, that is, only communication with an IP address (different from the local device's IP address) in the same LAN is allowed.
