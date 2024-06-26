---
title: "Experience score"
slug: "experience-score"
excerpt: "This section explains the concept of experience score."
hidden: true
metadata: 
  robots: "index"
createdAt: "Tue May 09 2023 06:17:55 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Tue May 30 2023 05:25:55 GMT+0000 (Coordinated Universal Time)"
layout: "default"
parent: "Performance and Experience"
grand_parent: "Guide"
---
# Experience score 
This section explains the concept of experience score.

***

Experience scoring is a function that scores the experience of the Mini Program, which will check in real time during the operation of the Mini Program, analyze some areas that may cause a bad experience, and locate where there are problems, and give some optimization suggestions.

## Operating environment requirements

- Download and install version 1.02.1808300 or later of the developer tools, download the address.
- The base library needs to be switched to version 2.2.0 or later.

## Using processes

1. Open the developer tools and switch the base library to version 2.2.0 or later in the details.
2. Switch to the Audits panel in the debugger area.
3. Click the "Start" button, then operate the Mini Program interface by yourself, and the running page will be detected by the "Experience Rating".

![](https://files.readme.io/754cdbe-small-8f39bee-39.translated.jpg)

4. Click "Stop" to end the detection, display the corresponding detection report in the current panel, and developers can optimize the corresponding functions according to the suggestions in the report.
5. To run Experience Score again, click "Clear Experience Score" above the report to restore the initial state. Please note that the report storage service is not available at this time, and once the Experience score is cleared, you will no longer be able to view the results of this rating.

![](https://files.readme.io/b1ed8b9-small-ccbfaec-40.translated.jpg)

## Automatic operation

In order to facilitate developers to discover experience problems in Mini Programs in time, the "Autorun" function of Experience Scoring is supported from version 1.02.1811150 of the developer tools.

This function will check in real time when developing and debugging Mini Program, and once the experience score is found to be less than 70 points, the system will print a warning message on the console panel to prompt the developer, at which time the developer can switch to the Audits panel to view the details.

Developers can turn on the "Autorun Experience Score" option in the local settings of the "Details" panel in the upper right corner of the tool.

! [autorun](<>)

## Scoring Rules

Specific scoring rules and detailed rules can be referred to the following documents:

- [scoring method](<>)
- [Performance](<>)
- [Experience](<>)
- [Best Practices](<>)

## Scoring method

At present, there are 27 rules in the experience score, which are divided into three categories: performance, experience, best practices, and the score for meeting the requirements of the rule (100 points), otherwise it must not be scored (0 points), and finally the total score is calculated according to the weight and formula of each rule..

![](https://files.readme.io/60c8bd6-small-68ac467-41.translated.jpg)

> A rule with a weight of 0, indicating that the rule does not participate in scoring and is only used as a prompt item. Developers can click Ignore in Developer Tools.
>
> The scoring conditions for each rule may also be adjusted with the version of the Mini Program.

The weights are as follows:

| classification | rule                                                    | weight |
| :------------- | :------------------------------------------------------ | :----- |
| performance    | Script execution time                                   | 7      |
|                | First screen time                                       | 6      |
|                | Render time                                             | 6      |
|                | SetData Call Frequency                                  | 6      |
|                | SetData data size                                       | 6      |
|                | Number of WXML nodes                                    | 6      |
|                | Request time-consuming                                  | 5      |
|                | Number of network requests                              | 5      |
|                | Number of picture requests                              | 5      |
|                | PictureCache                                            | 4      |
|                | Image size                                              | 4      |
|                | Network Request Cache                                   | 2      |
|                | Turn on inertia rolling                                 | 8      |
|                | Avoid using:activePseudo-class to implement click-state | 8      |
|                | Keep the picture size ratio                             | 4      |
|                | Response area for clickable elements                    | 3      |
|                | iPhone X compatible                                     | 3      |
|                | Window Change Fit                                       | 3      |
|                | Reasonable color match                                  | 0      |
| Best practices | Avoid JS exceptions                                     | 3      |
|                | Avoiding Network Request Exceptions                     | 3      |
|                | Deprecated interface                                    | 2      |
|                | Using HTTPS                                             | 1      |
|                | Avoid setData data redundancy                           | 1      |
|                | Minimum base library version                            | 0      |
|                | Remove inaccessible pages                               | 0      |
|                | WXSS usage                                              | 0      |
|                | Timely recovery timer                                   | 0      |

## Rules Explanation

For a detailed explaination of the rules, refer to the following documents:

- Performance
- Experience
- Best Practices

# Performance

## 1. First screen time

First screen time refers to the user from opening Mini Programs to see the first screen of the main content of time, first screen too long will lead to users to see a long time are white screen, affect the experience.

Optimize first screen time, can be divided into the following cases:

1. The first screen rendering content is more, need to gather multiple data for rendering. This situation requires developers to prioritize the content, high priority content to do priority display, shorten the white screen time.
2. First screen content relies on data that takes too long to request from the server. Developers need to specifically analyze the reasons for the long time to return server data from the server side.
3. One-time rendering data is too large or relies on calculations that are too complex. These problems can be solved by reducing the amount of rendered data and optimizing the rendering data.

**Scoring conditions: First screen time does not exceed 5 Seconds**

## 2. Render time

Render time refers to the time spent rendering for the first time or rendering for page structure changes caused by data changes.

The rendering interface takes too long to make the user feel that the Caton experience is poor, when this happens, you need to check whether the rendering area is too large (such as the list is too long), or the rendering dependency calculation is too complicated.

**Scoring conditions: rendering time does not exceed 500ms**

## 3. Script execution time

Script execution time is the amount of time that a JS script consumes during a synchronous execution, such as lifecycle callbacks and synchronous execution of event handlers.

It takes too long to execute a script that makes the user feel that the experience is poor, and when this happens, you need to confirm and optimize the logic of the script

**Scoring condition: Scripts run for no more than one execution cycle 1 Seconds**

## 4. SetData Call Frequency

The calling of setData interface involves thread communication between logic layer and rendering layer. Too frequent communication may lead to blocking of processing queue. The interface rendering is not timely and leads to Caton. We should avoid useless frequent calling.

**Scoring conditions: calls per secondsetDataNot to exceed the number of 20 second**

## 5. SetData data size

Since the Mini Program runs on top of the logical thread and the render thread, the call to setData transfers data from the logical layer to the render layer, which increases communication time.

**Scoring conditions:`setData`The data in the`JSON.stringify`After not exceeding 256KB**

## 6. Number of WXML nodes

It is recommended that a page use less than 1000 individual WXML Node, the node tree depth is less than 30 Layer, the number of child nodes is not greater than 60 1. A too-big WXML The node tree will increase memory usage and style rearrangements will take longer, affecting the experience.

**Scoring conditions: Page WXML nodes are less than 1000 The node tree depth is less than 30 Layer, the number of child nodes is not greater than 60 individual**

## 7. PictureCache

Open HTTP After caching control, the next load the same picture, will be directly from the cache read, greatly improve the loading speed.

**Scoring conditions: All pictures are on HTTP cache**

## 8. Image size

Picture is too big to increase download time and memory consumption, should be based on the display area size reasonable control picture size.

**Scoring conditions: Picture width height product \<= Actual display width height product \* (Device pixel ratio 2)**

## 9. Request time-consuming

Requests that take too long can make users wait or even leave. We should optimize server processing time, reduce the size of return packets, and make requests respond quickly.

**Scoring conditions: All network requests are in 1 Returns results in seconds**

## 10. Number of network requests

Too many requests in a short period of time will trigger the limitation of the number of parallel requests for Mini Programs, and too much requests may also lead to problems such as slow loading, so we should reasonably control the amount of requests, or even merge the requests.

**Scoring conditions: Pass`wx.request`Initiated takes more than 300ms The number of request concurrency of the 10 individual**

## 11. Number of picture requests

oo many image requests in a short period of time will trigger the limitation of parallel loading in the browser, which may cause images to load slowly and users to wait for processing. The quantity should be controlled reasonably. Consider using Sprite Graphics technology or lazy loading on off-screen pictures.

**Scoring conditions: the same domain name takes more than 100ms The number of picture request concurrency of not more than 6 individual**

## 12. Network Request Cache

Initiating network requests will always make users wait, which can lead to a bad experience. Try to avoid redundant requests, such as caching the same request

**Scoring conditions: 3 Within minutes the same url request does not appear twice back packet greater than 128KB And the exact same thing.**

# Experience

## 1. Turn on inertia rolling

Inertial scrolling will make scrolling smoother, in Android by default there is inertia scrolling, and in iOS Additional settings required under-`webkit-overflow-scrolling: touch`The style of

**Scoring conditions: wxss with`overflow: scroll`Of the elements in the iOS Next needs to be set`-webkit-overflow-scrolling: touch`style**

## 2. Avoid using`:active`Pseudo-class to implement click-state

use css :activePseudo-class to achieve click state, it is easy to trigger, and scrolling or sliding click state will not disappear, poor experience. Recommended to use Mini Program built-in components of the 'hover-class' Attributes to implement the

Score condition: do not use`:active`Pseudo-class, and use the`hover-class`replace`:active`

## 3. Keep the picture size ratio

If the image is not displayed according to the ratio of width to height of the original image, it may lead to distorted image, not beautiful, and even lead to user identification difficulties. Can be set in case image Component mode Property to preserve the aspect ratio of the original image.

**Scoring Conditions: High Displayed/Width and height of the original picture/Width does not exceed 15%**

## 4. Response area for clickable elements

We should reasonably set the response area size of clickable elements, if too small will lead to very difficult user experience is poor.

**Scoring conditions: clickable elements are not less than the width and height 20px**

## 5. iPhone X compatible

for`position: fixed`Of interchangeable components if rendered on an iPhone Outside the safe area of X, easy to touch by mistake Home Indicator, should render all interactive parts into a secure area.

It is recommended to use the following wxss for compatibility

```Text
// code
padding-bottom: constant(safe-area-inset-bottom)
padding-bottom: env(safe-area-inset-bottom)
```

**Scoring conditions:`position: fixed`And the height is less than 68px Of interactive components rendered within a secure area of**

## 6. Window Change Fit

For pages that support resizing, UI adaptation to different window sizes is required and a good experience has been achieved.

Can use match-media Components, MatchMediaObserver or @media Media queries add adaptation logic to the page.

**Score condition: Pages that support resizing have relevant adaptation logic**

## 7. Reasonable color match

Text color and background color needs to be matched properly, appropriate color contrast can allow users to better read, enhance the user experience of Mini Programs.

Because of the complexity of color collocation, the algorithm is still being optimized. Therefore, this indicator is only a reminder of the score and is not included in the overall score.

**Judgment Criteria:**

1. **For larger fonts (f`ont-size >= 24px`, or at the same time satisfy`font-size >= 19px`and`font-weight >= 700`), the contrast between the text color and the background color is not less than 3**
2. **Other fonts, text colors and background colors have a contrast of not less than 4.5**

> Contrast Calculation Method Reference W3C Standard

# Best practices

## 1. Avoid JS exceptions

Appear JavaScript Exceptions may lead to the interaction of programs can not continue, we should pursue zero exceptions to ensure the high robustness and high availability of programs.

**Scoring condition: no JS exceptions**

## 2. Avoiding Network Request Exceptions

Failure of a request can cause the program to fail to interact, and all requests should be guaranteed to succeed.

**Scoring conditions: all authorized network requests return normally, unauthorized network requests need to be given 401 or 403 These two state codes**

## 3. Not using deprecated interfaces

Using an interface that is about to be deprecated or has already been abandoned can cause the Mini Program to run abnormally. In general, the interface will not be immediately removed, but to be on the safe side, it is recommended not to use, to avoid subsequent Mini Program suddenly run abnormal.

**Score Condition: Not using any interface that indicates deprecation in the document**

## 4. Using HTTPS

use`HTTPS`, can make your Mini Program more secure, while`HTTP`Is transmitted in plaintext, there is a risk that the content could be altered

**Scoring conditions: All network requests use**`HTTPS`.

## 5. Avoid setData data redundancy

The setData operation causes the frameworkwork to handle some of the work associated with rendering the interface. An unbound variable means that it is irrelevant to the rendering of the interface, and passing in setDatas can cause unnecessary performance costs.

**Scoring conditions:`setData`All data passed in has related dependencies in template rendering**

## 6. Minimum base library version

When the components used/API When the supported version of the library is larger than the configured lowest online base version, it may cause the corresponding functionality to be unavailable. Developers can adjust the minimum base library version by [adjusting]\(../compatibility.md#Set the lowest base library version) or compatible on the code in a way that solves the problem.

Because users can solve the problem in a code-compatible way, this metric is used only as a reminder of the score and is not included in the overall score.

**Judgment criteria: There is no component in use/API Of supported versions is greater than the lowest online base library version configured**

## 7. Remove inaccessible pages

The package size of the Mini Program will affect the load time. You should try to control package size to avoid packing files that will not be used.

Because this metric relies on the developer's operating path, it serves as a reminder of the score and is not included in the overall score.

**Criteria: No inaccessible pages are packaged into an Mini Program**

## 8. WXSS usage

We should introduce on-demand wxss Resources, if there are a large number of unused styles in the Mini Program, will increase the size of the package size, thus affecting the loading speed to some extent.

Because this metric relies on the developer's operating path, it serves as a reminder of the score and is not included in the overall score.

**Judgment Criteria: Each wxss The unused portion of the resource does not exceed 2KB**

## 9. Timely recovery timer

The timer is global and not bound to the page. When the Mini Program is routed from one page to another, the previous page timer should be manually recycled.

Because this metric relies on the developer's operating path, it serves as a reminder of the score and is not included in the overall score.

**Criteria: All timers' callbacks are executed on the same page as those on which the timer is set**
