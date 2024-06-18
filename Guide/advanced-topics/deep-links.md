---
title: "Deep links"
slug: "deep-links"
excerpt: ""
hidden: false
metadata: 
  image: []
  robots: "index"
createdAt: "Thu May 18 2023 11:11:46 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Fri Jul 14 2023 11:26:03 GMT+0000 (Coordinated Universal Time)"
layout: "default"
parent: "Advanced topics"
grand_parent: "Guide"
nav_order: 2
---
# Deep links 
*** 
You can set up links to take users to a link's specific content directly in your app, bypassing the app-selection dialog.

```http
https://{domain.com}/applet/?appId={appId}&pagepath={pagePath}
```

**domain.com:** Super app domain, e.g: stage environment is stage.neuxnet.com  
**appId:** Mini app id, Required  
**pagePath:** Mini app path, Optional, needs UrlEncode.
