---
title: "Super Hub Mini App Development Guide"
slug: "hub-mini-app-development-guide"
excerpt: ""
hidden: true
metadata: 
  image: []
  robots: "index"
createdAt: "Wed Nov 09 2022 13:49:39 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Tue Dec 06 2022 13:32:06 GMT+0000 (Coordinated Universal Time)"
layout: "default"
parent: "Documentation"
---
# Getting started

Before starting with developing the Mini app, you need to create an account on the Super Hub portal in order to test and submit your app.

Once the account is created and approved, you can download NEOS IDE, log in to your account from the IDE and create a new project.

***

# Super Hub Mini apps

A software bundle developed using the NEOS project's specific technology that runs inside the Super Hub app as a standalone app.

# IDE (Integrated Development Environment)

NEOS IDE is the official tool used for developing, debugging and submitting NEOS Mini apps.

***

# Technologies

## Templating (NXML/NSS)

**NXML** - The official language used to develop the structure of app pages

- It's similar to HTML (you can use most HTML tags) and comes with extra tags like view and block.
- You can specify the data that will be rendered inside the file by wrapping it with 2 curly braces: `{{ data_to_render }}`.
- You can apply some basic business logic using “if” and “for” statements inside the NXML file.

**NSS** - The language used to style pages and views.

- It's like CSS and you can use most of the CSS features.
- You can also import other NSS files inside an NSS file.
- NSS depends on a new dimensions unit which is called RPX (responsive pixel), which renders the dimension based on the device’s resolution.
- NSS only supports certain CSS selectors.

# Business logic (JavaScript)

Business logic is written in JavaScript, you can use all the features in ES6 to program the Mini app.

**_Note:_** JavaScript eval() is not supported, as you can’t run dynamic code inside the mini app

# Data binding

When you bind data inside the NXML file using curly brackets and change the data from the JavaScript file, changes are reflected on the view directly. Only the view that has the data bound to it will be re-rendered, not the whole page.

In order to change the data referenced in the page’s NXML file, you need to declare the data inside the JS file and call `this.setData()` to change the previously declared data and have the changes reflected on the page.

# Using 3rd party packages

Like any other JavaScript project, you can add JavaScript packages with the following steps:

- Initiate an NPM project inside the mini app home folder
- Add packages to package.json file and install them with NPMinstall
- Click on compile NPM from the IDE to compile the NPM package
- Import the package inside JavaScript files and use it normally

_**Note:**_ There is no DOM API inside the Mini app JavaScript files, so libraries that manipulate the DOM won’t work (e.g., jQuery).

The JavaScript environment that the Mini app runs in is different from the browser’s or NodeJS runtime environment, so not all JavaScript packages will work inside the Mini app.

# NEOS global object

NEOS global object is injected inside all JavaScript files. The object is used to communicate with the Super Hub app to request data, device functionality or perform an action.

- Use the QR code scanner and deliver the results to the app
- Make a payment using NEOS payments
- Request to take a photo or attach an image from gallery
- Share a link through NEOS chat or other apps
- Request user location
- Check if a new version of the Mini app is available
- Access local storage to save/retrieve data

***

# Mini app code folder structure

**Pages directory:** holds all the pages code in the app. A separate folder should be created for every page.

**App.json: **holds the global configurations for the Mini app, such as registering pages, app name and navigation bar styles.

**App.NSS: **holds the global styles for the app, which can be accessed from all pages’ NXML files.

**App.js:** holds the app creation logic and callbacks used in the app.

**Site_map.json:** holds the indexed data information, that allows the Mini app user to search through the Mini app.

**_Note:_** the app’s entry point page is going to be the first page declared in the page's array inside the app’s app.json file.

# Development flow

In order to create a new page (single screen view) in your app, you need to add the page path to the app’s app.json file and create a folder inside the pages folder that has the following page files:

**Page_name.json:** this JSON file holds data about your page, such as title, navigation bar style and background.

**Page_name.js: **holds the data and business logic of the page, a global object called ns is injected into the file in order to communicate and perform actions using NEOS APIs.

**Page_name.NXML:** holds the NXML structure of the page.

**Page_name.NSS:** holds the styles of the page, please note that you can import other NSS files into another NSS file.

# Mini app environment

Mini apps run in a special environment and it's divided into 2 layers, each layer runs in its own separate thread:

**Rendering layer:** NXML and NSS files are processed and rendered on this layer.

**Logic layer:** This is where all the JavaScript code is executed.

***

# Development SDK

Super Hub capabilities

- Identity
- Payments
- Communication

## Testing

You can test your Mini app by clicking on the QR code button in the IDE, it will generate a QR code that you can scan using the Super Hub app, once scanned. The Mini app will show inside the Super Hub app and you can interact with it on a real device.

## Debugging

The IDE provides a debugging capability using chrome’s remote debugging, you need to have Chrome browser installed. Once you click on the debugging button you can inspect your code and views.

***

# Submitting the mini app

Once the Mini app is ready to be submitted, you can click on submit Mini app from the IDE. Once a submission is complete, you can check the Mini app status from the Super Hub Mini app portal.

## NEOS Mini apps platform:

The platform allows you to perform several actions on the Mini app, and it shows various data collected from the Mini app when it's live. You can:

- check the status of the submitted Mini app, appeal a rejected Mini app
- see metrics about your Mini app, like daily active users and sessions durations
- see errors and crashes reported from your Mini app
- check the payments made through the Mini app

***

# Custom components:

NXML has lots of built-in components (buttons, forms, text views) along with the development SDK components, however, you can create your own components and include them in your NXML files.

Similar to a page, a custom component will have the following files: NXML, NSS, JSON and JS.

When you want to use a custom component, you must add the `usingComponents` property to the page’s JSON file and specify the path for the component you want to use.

Custom components can reference other custom components, the `usingComponents` property should be added to the custom component JSON file.

***

# Mini app startup

Both **hot startup** (_switching a Mini Program running in the background to the foreground_) and **cold startup** (_when a user opens a Mini Program for the first time or re-opens it after its termination_) are supported in Mini apps. The Mini app will be notified when it’s opened for the first time or resumed.

## Updating Mini apps

It may take at most 24 hours to send the new version data to all the users. The users will be prompted to update to the latest version before enabling the Mini Program next time.

## Mini app local storage

Each Mini app has allocated local storage. The Mini app can access the local storage through the global NX object. Local storage for the Mini app is isolated from other Mini apps’ local storage. Local storage for the Mini app is wiped when the Mini app is disabled.
