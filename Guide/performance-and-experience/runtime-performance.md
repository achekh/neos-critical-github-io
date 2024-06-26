---
title: "Runtime Performance"
slug: "runtime-performance"
excerpt: "This section explains the concept of runtime performance."
hidden: true
metadata: 
  robots: "index"
createdAt: "Tue May 09 2023 06:17:50 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Tue May 30 2023 05:23:49 GMT+0000 (Coordinated Universal Time)"
layout: "default"
parent: "Performance and Experience"
grand_parent: "Guide"
---
# Runtime Performance 
This section explains the concept of runtime performance.
*** 
## setData

`setData` is the most frequently used interface in Mini Program development and it is also the most likely to cause performance problems. A brief introduction before introducing common incorrect usage `setData` How it works behind it.

### Working principle

The view layer of the Mini Program currently uses WebView As rendering vectors, while the logical layer is made up of independent JavascriptCore As a running environment. On architecture, WebView and JavascriptCore Are independent modules, and do not have a direct data sharing channel. Currently, the data transfer between the view and logic layers is actually transmitted through the `evaluateJavascript` Achieved. That is, users transfer data, which need to be converted to the form of string transmission, while the converted data content spliced into a copy JS Script, and then by executing the JS Scripts are passed to both independent environments.

and `evaluateJavascript` There are many ways in which the execution of the image can be affected, and data arriving at the image layer is not real time.

## Common setData Operation error

### 1. Frequent going setData

In some cases we have analyzed, some Mini Programs go very frequently (in milliseconds)`setData`, which leads to two consequences:

- Android Lower users will feel Caton when swiping, and the operational feedback delay is severe because JS The thread has been compiling and performing rendering, and failed to pass user action events to logical layer in time, and logical layer failed to deliver action processing results to view layer.
- Rendering has a delay due to WebView of JS The thread is busy all the time, the communication from the logic layer to the page layer is time-consuming, the data message received by the view layer is hundreds of milliseconds from the time it was sent out, the rendering result is not real-time.

### 2. Every time setData Are passing lots of new data

By`setData`Our data transfer is actually one time `evaluateJavascript` Script process, when the amount of data is too large will increase the compilation execution time of the script, taking WebView JS Thread,

### 3. Background state page setData

When the page is in the background state (not visible to the user), it should not proceed`setData`, background state page rendering users are unable to feel, in addition background state pages to`setData`Also preempts the execution of the foreground page.

## Photo Resources

The main performance problems with image resources at present are on large images and long list images, both of which can cause iOS The client memory footprint rises, which triggers the system recycling Mini Program page.

### Effect of pictures on memory

In iOS Up, the Mini Program's page is composed of multiple WKWebView Composed of, when the system memory is tight, will recover a portion WKWebView。 From past cases we have analyzed, the use of large pictures and long list pictures can cause WKWebView Of recycling.

### The Effect of Images on Page Switching

In addition to memory problems, large images can also cause page switching Caton. We have analyzed the case, there are some Mini Programs in the page will reference large images, in the back of the page switch will appear to drop frame caton.

Currently we recommend that developers minimize the use of large image resources.
