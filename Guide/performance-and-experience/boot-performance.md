---
title: "Boot performance"
slug: "boot-performance"
excerpt: "This section explains the concept of boot performance."
hidden: true
metadata: 
  robots: "index"
createdAt: "Tue May 09 2023 06:17:48 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Tue May 30 2023 05:23:04 GMT+0000 (Coordinated Universal Time)"
layout: "default"
parent: "Performance and Experience"
grand_parent: "Guide"
---
# Boot performance 
*** 
# Starting performance

Mini Program startup is an extremely important part of the user experience of Mini Program, and too long to start will cause the loss of Mini Program users and affect the user experience.

> The "start" in this section refers specifically to the cold start of the Mini Program, excluding the hot start of the background of the Mini Program. For the definition of cold/warm start, refer to the operation mechanism of the mini program.

## I. Start the process

Before starting optimization, the following Mini Program startup process is briefly introduced. In the process of Mini Program startup, it includes the following:

- Mini Program startup of these parts is not done serially, as much as possible in parallel.
- Mini Program start each part is not every start complete, will try to use the cache.

### 1. Resource Preparation

**1.1 Mini Programs related information preparation**

When the user accesses the Mini Program, the client needs to obtain the configuration, version, permission and other related information from the app background, so as to carry out the necessary version management, permission control and verification of Mini Program.

#### Impact on startup time consuming

The acquisition and updating of information can affect the start-up time of the Mini Program, especially when the user first accesses it.

In order to minimize the impact of startup time to ensure real-time information, the information is cached locally and updated regularly through a certain mechanism.

**1.2 Mini Program runtime environment preparation**

Before executing the Mini Program code, the client needs to prepare the basic environment in which it will run.

An Mini Program's running environment includes the Mini Program process, the native part of the UI Elements (such as Navigation bar, tabBar, etc.), rendering pages using the WebView Containers, running developers JS Code JS Engine, Mini Program base library, and more.

#### Impact on startup time consuming

It takes a long time to prepare the running environment, which has an obvious effect on the startup time of the Mini Program.

In order to minimize the impact of running environment preparation on startup time, the client preloads the running environment in advance according to user's usage scenario and device resource usage. However, due to the influence of device resources and operating system scheduling, it is difficult to ensure that every Mini Program startup has a pre-loaded environment.

**1.3 Mini Program Code Package Preparation**

#### Impact on startup time consuming

Download time is an important bottleneck in startup time and is positively related to the size of code package or incremental package.  Adoption ZSTD algorithm compresses the Mini Program code package to reduce as much as possible the amount of data transmitted during downloading.

Considering the impact of package size on user experience, platforms limit the size of individual code packages to 2M。 The increase in the code package cap enables richer functionality for developers, but also increases the amount of downloadable traffic and local space for users. To ensure startup speed, developers should control the code package size as much as possible.

### 2. Developer code injection (logical layer)

Mini Program startup requires reading the Mini Program's configuration and code from within the code package and injecting it into the JS In the engine. During main package code injection, the Mini Program's `App.onLaunch` And first `App.onShow` Life cycle. After the developer code injection is completed, the framework side will carry on some page data initialization according to the page visited by the user, triggering the first page of the `Page.onLoad`, `Page.onShow` Events.

#### Impact on startup time consuming

The time spent injecting developer code directly affects the time taken to start the Mini Program. In mainstream JS In the engine, code injection time includes compilation and execution. Code volume, synchronous interface calls and some complicated calculations all affect the injection time.

Since home page rendering requires data sent from the logic layer, if developer code injection takes too long, it can also delay the start of home page render.

At the top of the level, microaccess is used. V8 Engine Code Caching Technique caches the result of code compilation, which reduces the compilation time of secondary injection.

### 3. Developer Code Injection (Rendering Layer)

Developer's wxss and wxml Is compiled and injected into the rendering layer, containing page structure and style information required for page rendering. The time to inject the rendering layer is mainly related to the complexity of the page structure and the number of custom components used.

Developer code injection for the rendering and logic layers is performed in parallel.

#### Impact on startup time consuming

Since home page rendering requires the page structure and style information of the rendering layer, if the developer code injection takes too long, it will delay the start of the first page rendering.

### 4. Home (initial) rendering

After the completion of developer code injection, combined with the logic layer data and the rendering layer page structure and style information, the Mini Program frameworkwork will render the front page of the Mini Programs, display the first screen of the Mini Programs, and trigger the first page of `Page.onReady` Events.`Page.onReady` **Event triggers flag Mini Program startup process completed**.

#### Impact on startup time consuming

Home page rendering time is mainly affected by the page structure and the amount of data involved in rendering.

## II. KEY CONCEPTS

When discussing Mini Program startup time consuming, several concepts need to be clarified:

### 1. Mini Program first screen rendering completed

From the developer perspective, Mini Program first screen rendering completed sign is the home page `Page.onReady` Event triggered.

From the perspective of the frameworkwork, the contents of the Mini Program's first screen are based on the initial data of the Mini Programs, as well as those that arrive before rendering begins setData Of data rendering.

The completion of the first screen rendering does not mean that the Mini Program page must have complete content, the developer triggered `setData`(e.g. by `wx.request` Asynchronous request data) may not necessarily participate in first-screen rendering.

Due to differences in the frameworkwork and startup processes, the completion of the first screen of the Mini Program definition is not equivalent to the browser's load Events.

### 2. Mini Program startup phase

From user click access Mini Program to Mini Program first screen rendering complete (home `Page.onReady` Event triggered).

### 3. Open rate/Arrival rate

Mini Program first screen rendering completed PV and User click to access Mini Program PV The ratio of...`Attrition rate = 1 - Open rate`

## III. Optimization of start-up performance

In the startup process, Mini Program code package preparation, developer code injection and home page rendering are related to developers, developers can carry out certain optimization work. Other parts of the current developers can not intervene, the frameworkwork side is responsible for continuous optimization.

### 1. Mini Program code package optimization

The core of code package optimization is to reduce code package size, which directly affects the download time and user experience when starting Mini Programs.

Developers can optimize code package sizes by:

### 1.1 Subcontract loading

use **sub-packageing load Is the most obvious means of optimizing Mini Program startup**It is suggested that developers divide the function of the Mini Program into sub-packages according to the usage frequency and scene, and load the code package on demand.

Subcontracting loading has the following advantages:

- Carry more functionality: The size of a single package of Mini Program code is capped at 2M, the use of sub-packageing can increase the overall volume limit of Mini Program code packages, carrying more functions and services.
- Reduce the code package download time: after the use of sub-packageing can significantly start the need to download code packages size, without affecting the normal use of functional significantly improve startup time.
- Reduce Developer Code Injection Time: When the Mini Program starts, it injects all the developer code at once. Using sub-packageing reduces the amount of code injected, thus reducing injection time.
- Reduce page rendering time

Furthermore, combined with several extended features of sub-packageing loading, startup time can be further optimized:

[subcontract predownload](<>)

When usingSubcontract loadingAlthough the startup speed of the Mini Program can be significantly improved, when the user jumps to the subcontract page in the process of using an Mini Program, Need to wait for subcontract download to complete before entering the page, resulting in page switching delay, affect the use of Mini Program experience. Subcontract pre-download is designed to solve the problem of delay when first entering the subcontract page.

[independent subcontracting](<>)

However, some scenarios in the Mini Program (such as advertisement page, activity page, payment page, etc.), usually the function is not very complex and relatively independent, which has high requirements for startup performance. Independent sub-packageing can operate independently of master and other sub-packageing. You do not need to download the main package when entering the Mini Program from a separate subcontract. It is recommended that developers put some pages with high startup performance into special independent sub-packageing.

Independent sub-packageing and sub-packageing pre-download can be used together to get better results. For more details, please refer to [Tutorial on Independent and Subcontracting Pre-download](<>)

### 1.2 Code refactoring and optimization

Reduce code redundancy through code refactoring. In the use of such Webpack When packaging tools and so on, try to take advantage of tree-shaking Features such as the following remove redundant code. Care should also be taken to prevent the introduction of unneeded libraries and dependencies when packaging.

### 1.3 Control resources such as pictures in code packages

Avoid including in code packages or in WXSS Use in base64 Inline too much, too big picture, should try to use network picture. Images in code packs should generally contain only small icons. Other types of resources, such as sound and video, should be kept out of code packages.

The Mini Program code package, when downloaded, uses ZSTD The algorithm is compressed to reduce the amount of data transmitted when downloading. These resource files take up a lot of code package volume and are often difficult to compress further, making them much more time-consuming to download than code files.

### 1.4 Clean up unused code and resources in a timely manner

During daily development, we may have introduced some new library files, After a while, for various reasons, we don't use the library anymore. We often just remove references from the code and forget to delete the library files.

At present, Mini Program packaging will all the files under the project into the code package, that is to say, these are not actually used library files and resources will also be into code packages, thus affecting the size of the overall code package.

### 2. Developer Code Injection Optimization

The optimization of developer code injection can be done from two parts: optimizing execution time and optimizing code volume.

### 2.1 Reduce synchronous calls to startup procedures

During the Mini Program startup process, the developer code is injected and sequentially executed `App.onLaunch`, `App.onShow`, `Page.onLoad`, `Page.onShow`. After the Mini Program initialization code (Page, App Beyond definition) and startup related for several life cycles, should avoid performing complex computational logic or overusing`Sync`The synchronization API at the end, such as wx.getStorageSync，wx.getSystemInfoSync Etc. for getSystemInfo, `getSystemInfoSync` Should be cached to avoid duplicate calls.

### 2.2 Using [lazy-injection](../../../reference/configuration/app.md#lazyCodeLoading)[](../../../reference/configuration/app.md#lazyCodeLoading)

Typically, all the JS code of the subcontract and the main package (except the standalone subcontract) in which the startup page is located are all merged and injected at Mini Program startup, Including other unvisited pages and not using custom components, resulting in a lot of unused code injected into the Mini Program running environment, affecting injection time and memory footprint.

Self-Base Library Version 2.11.1 Mini Program supports injecting only the custom components and current page code required by the current page to reduce Mini Program startup time and runtime memory. The developer can find the file in the `app.json` Configuration in:

```Text
// code
{
  "lazyCodeLoading": "requiredComponents"
}
```

> 📘 Note
> 
> After adding this configuration, unused code files are not executed.

### 3. Page Rendering Optimization

### 3.1 Advance First Screen Data Request

Most Mini Programs rely on interface data from the server when rendering the home page. Mini Programs provide developers with the ability to initiate data requests in advance:

- [data prepull]\((Pre-fetch): Be able to pull business data to third-party servers in advance through app background when Mini Program is cold started, When the code package is loaded, the page can be rendered faster, reducing user wait times, and thus increasing the speed of Mini Program opening.
- [periodic update]\((Background-fetch): In the case of the user does not open the Mini Program, can also pull data from the server ahead of time, when the user opened Mini Program can render the page faster, reduce user waiting time.

### 3.2 Skeleton screen

In the page data is not ready (if you need to get through the network), try to avoid showing blank pages, should first show the general structure of the page through the skeleton screen, after the request data return page update. To enhance users' willingness to wait.

### 3.3 Cache request data

The Mini Program provides the [wx.setStorage](<>)、[wx.getStorage](<>), etc. The ability to read and write local caches. Data is stored locally and will be returned faster than network requests. If the developer is unable to use data prefetch and periodic updates for some reason, we recommend prefetching data from the cache to render the view and waiting for the network request to return to update.

### 3.4 Streamlined First Screen Data

We recommend that developers delay requests for non-critical rendering data, and try not to place data unrelated to visual layer rendering on data To speed up page render completion time.

## Starting performance analysis

### 1. Performance Data Acquisition

### 1.1 Mini Program helperPerformance analysisplate

> Mini Program management background performance data has not been updated, is planning revision, it is recommended that before the revision completed developers to Mini Program assistant performance data prevail.

It is recommended that developers use Mini Program Helper.Performance analysisPlate, constant focus on Mini Program performance. Performance analysis from **Startup performance, operational performance and network performance** .The three dimensions provide performance data for developers to analyze according to platform, model, network environment and access sources. Scan the following Mini Program code to immediately experience.

![](https://files.readme.io/4f6b80f-36.jpg)

### 1.2 Adopt API Get within the Mini Program

Developers can also use [wx.getPerformance] in the Mini Program, depending on their business needs]((wx.getPerformance)) for information related to the current Mini Program's performance.

After obtaining information, developers can self-report or use wx.reportPerformance For speed measurement.

### 1.3 Experience rating

In the Mini Program tool provides experience scoring tool to facilitate developers can timely find the experience of Mini Program problems.

### 2. Factors Affecting Startup Performance

According toStartup processAccording to the startup process introduced in the first section, there are many factors affecting the startup time of the Mini Program.

For the same Mini Program, the following factors directly affect the average startup time:

- **Platform**: Under different platforms (Android, iOS, PC, etc.) device performance, operating system, frameworkwork implementation, optimization scheme exist big differences, startup time also exists big differences. **It is only meaningful to compare startup time by platform (including time spent at each stage).**
- **Download Proportion**: Code package download and update will significantly affect the Mini Program startup time, in other processes time-consuming stable circumstances, download proportion will affect the large startup time.
- **Entry Page**The number and size of packages to download and the amount of code injected varies from page to page depending on the subcontract. Different page rendering time is also different.
- **Model distribution**There is a strong correlation between startup time and equipment performance. Differences in user groups of different Mini Programs or scenarios may lead to differences in model distribution, and then affect the overall startup time.
- **Network environment**Network environment mainly affects the network request time, such as Mini Program information acquisition, code package download and so on.

In addition, startup time can be indirectly affected by:

- **scene/Visit Source**: Different scenarios users visit different pages, the purpose of access and their willingness to wait is also different, to start time and open rate have a certain impact.
- **Percentage of first-time users**When users access the Mini Program for the first time, they need complete preparation of Mini Program information, code package download process, code cache also need to be regenerated, startup time will be higher than non-first access.
- **Mini Program version update**: Mini Program version update, users need to update Mini Program information and code packages, code cache also need to be regenerated, startup time will rise.

## aboutPerformance analysisSector data

Mini Program assistant provides the download time, js injection time and initial rendering time during startup process and developer optimization reference.

It is important to note here that**T`otal startup time Downloading is time-consuming js Injection time consuming Initial rendering time consuming`**. Downloads do not necessarily occur during startup, nor do they necessarily only download one code package. js Injection and rendering time can also fluctuate depending on cache updates.

**Decreases in time spent at each stage do not necessarily reflect decreases in total time spent**. For example, after the release of a new version of a Mini Program, even if the time spent at each stage is reduced, an increase in the download ratio may lead to a rise in the total time spent.

### 3. Factors Affecting Open Rate

**Starting performance**and **User's willingness to wait**Are two key factors that affect the open rate. In some cases, if the user's willingness to wait is low, even if the start-up time is very low, it is not always possible to obtain a higher open rate.
