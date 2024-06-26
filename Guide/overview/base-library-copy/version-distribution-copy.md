---
title: "Version Distribution"
slug: "version-distribution-copy"
excerpt: "This section explains the concept of version distribution."
hidden: true
metadata: 
  image: []
  robots: "index"
createdAt: "Tue May 09 2023 07:15:22 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Thu May 11 2023 08:55:39 GMT+0000 (Coordinated Universal Time)"
layout: "default"
parent: "Overview"
grand_parent: "Guide"
---
# Version Distribution 
This section explains the concept of version distribution.

***

# Best Practices

## 1. Avoid JS exceptions

JavaScript Exceptions may interfere with the interaction of the programs. Hence, we should pursue zero exceptions to ensure the high robustness and high availability of programs.

**Scoring condition: no JS exceptions**

## 2. Avoid Network Request Exceptions

Failure of a request can cause the program to fail to interact. Hence, it is important that all requests should be guaranteed to succeed.

**Scoring conditions**: All authorized network requests must return normally, and unauthorized network requests must be given 401 and 403 state codes.

## 3. Use of deprecated interfaces

Using a deprecated interface or abandoned interface can cause the Mini Program to run abnormally. In general, the interface will not be immediately removed, but to be on the safe side, it is recommended to avoid the sudden abnormal run of the subsequent Mini Program.

**Score Condition**: Do not use any deprecated interface.

## 4. Using HTTPS

Using `HTTPS`, can make your Mini Program more secure, while `HTTP` is transmitted in plaintext, that expose the security of the content.

**Scoring conditions**: All network requests use HTTPS.

## 5. Avoid setData data redundancy

The setData operation causes the framework to handle some of the work associated with rendering the interface. An unbound variable means that it is irrelevant to the rendering of the interface, and passing in setDatas can cause unnecessary performance costs.

**Scoring conditions**:`setData`All data passed in has related dependencies in template rendering.

## 6. Minimum base library version

When the components used/API When the supported version of the library is larger than the configured lowest online base version, it may cause the corresponding functionality to be unavailable. Developers can adjust the minimum base library version by [adjusting]\(../compatibility.md#Set the lowest base library version) or compatible on the code in a way that solves the problem.

Because users can solve the problem in a code-compatible way, this metric is used only as a reminder of the score and is not included in the overall score.

**Judgment criteria**: There is no component in use and no API of supported versions is greater than the lowest online configured base library version.

## 7. Remove inaccessible pages

The package size of the Mini Program will affect the load time. You should try to control package size to avoid packing files that will not be used.

Because this metric relies on the developer's operating path, it serves as a reminder of the score and is not included in the overall score.

**Criteria**: No inaccessible pages are packaged into a Mini Program.

## 8. WXSS usage

We should introduce on-demand wxss resources. If there are a large number of unused styles in the Mini Program, it will increase the size of the package size, thus affecting the loading speed to some extent.

Because this metric relies on the developer's operating path, it serves as a reminder of the score, and it is not included in the overall score.

Judgment Criteria: For each wxss, the unused portion of the resource does not exceed 2KB.

## 9. Timely recovery timer

The timer is global and not bound to the page. When the Mini Program is routed from one page to another, the previous page timer should be manually recycled.

Because this metric relies on the developer's operating path, it serves as a reminder of the score and is not included in the overall score.

**Criteria**: All timers' callbacks are executed on the same page as those on which the timer is set.
