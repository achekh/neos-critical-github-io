---
title: "FAQs"
slug: "faqs"
excerpt: ""
hidden: false
metadata: 
  image: []
  robots: "index"
createdAt: "Tue May 16 2023 11:25:41 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Sun May 28 2023 13:13:44 GMT+0000 (Coordinated Universal Time)"
layout: "default"
parent: "Introduction"
grand_parent: "Guide"
---
**Can I use another JavaScript library (e.g. ReactJS) to build Mini Apps?**

Unfortunately, no, the only way to develop a Mini App is using our development technologies and workflows.

**Can I write native code inside my Mini App?**

Unfortunately, no, however, you have most of the native APIs at your disposal, if you need an API that is not yet supported by our ecosystem, please drop us an email at: [hub.support@neom.com](mailto:hub.support@neom.com).

**Is there a limitation on the Mini App bundle size?**

Currently there is no limitation on the Mini App bundle size, but we recommend making it as small as possible for a better user experience.

**Can I use JavaScript 3rd-party packages in my Mini App?**

Due to the special nature of the runtime environment of Mini Apps, not all JavaScript 3rd-party packages will work with Mini Apps. Libraries that access the DOM won't work (e.g., jQuery). Libraries that depend on vanilla JavaScript do work with Mini Apps (e.g., lodash).

**Can Mini Apps have animations? **

Yes, either through WXSS (using CSS animations) or through the `wx` global object.

**Can I send a push notification to a Mini App? **

Yes, you can send by using our push notification API end point. You can even attach a deep link to the push notification to open a specific page in the Mini App and provide it with extra data.

**Once permission is granted to the mini app, can the user revoke it later from settings? **

Yes, user can always revoke or regrant permissions to Mini Apps from the Mini App settings page.

**Can Mini Apps have a long running background service? **

For security reasons, this is not supported currently, we might consider it in the future.

**Can I test the Mini App on a real device? **

Yes, you can, by downloading the Super Hub app, you can scan the QR code from the Super Hub Mini App Studio and load the Mini App on a real device.

**Does Mini Apps support wearable devices?**

Currently, it is not supported, we might consider it in the future.

**How can I suggest a feature or report an issue in the developer ecosystem?**

Our team is happy to assist you anytime you want, feel free to drop us an email at: [hub.support@neom.com](mailto:hub.support@neom.com).
