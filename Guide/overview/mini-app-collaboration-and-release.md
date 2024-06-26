---
title: "Mini Program Collaboration and Release"
slug: "mini-app-collaboration-and-release"
excerpt: "This section explains the concept of Mini Program collaboration and release."
hidden: true
metadata: 
  robots: "index"
createdAt: "Thu Apr 27 2023 10:10:42 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Wed May 03 2023 10:12:22 GMT+0000 (Coordinated Universal Time)"
layout: "default"
parent: "Overview"
grand_parent: "Guide"
---
# Mini Program Collaboration and Release 
This section explains the concept of Mini Program collaboration and release.

***

In medium and large companies, the division of labor is very fine. Generally, employees with different roles are involved in the same Mini Program project. Therefore, we designed different management permissions for the Mini Program platform to allow project managers to more effectively manage the collaboration of the entire team.

Earlier when the webpage development was completed, developers have to put the code and resources of the webpage on the server, and the users access it through the Internet. In the Mini Program platform, after completing the development, the developers need to submit the code package of the Mini Program in the Mini App DevTools. This package is then released via the Mini Program admin console,and users can access the Mini Program through searching or other entries.

In this chapter, we will introduce the considerations of the team collaboration, and the concepts and processes involved before and after the release of Mini Programs.

## Collaboration

If your Mini Program is developed by only one person, you can skip this part. If it is developed by a team, you need to understand some concepts first.

In most cases, multiple people in a team will participate in the same Mini Program project at the same time, with each role responsible for different work or authority, and the division of labor in medium and large companies is much finer. To more clearly express the relationship between different roles of a team and the management of permissions, we describe how to coordinate the daily work of a Mini Program project by virtualizing a project member structure, as shown in Figure 5-1.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/7dddb48-small-b832f43-6.translated.jpg",
        null,
        "Figure 5-1 Virtual Mini Program Project Team"
      ],
      "caption": "Figure 5-1 Virtual Mini Program Project Team"
    }
  ]
}
[/block]


The project management members are responsible for coordinating the progress and risks of the entire project and controlling the pace of Mini Program release. The product team puts forward the requirements, and the design team discusses with the product team, abstract the requirements, design the visualization process and graphics, and output the design scheme. The development team writes the program code according to the design scheme. After the code is completed, the product team and the design team experience the overall flow of the Mini Program, and the test team writes test cases and performs various boundary tests on the Mini Program. The general member relationship and workflow of the project are shown in Figure 5-2.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/8c2a17d-small-b6e9f4e-7.translated.jpg",
        null,
        "Figure 5-2 Process from Requirement to Mini Program Release"
      ],
      "caption": "Figure 5-2 Process from Requirement to Mini Program Release"
    }
  ]
}
[/block]


## Mini Program Member Management

Mini program member management includes management of Mini Program project members and test members.

- Project member: Members who participate in the development and operation of Mini Programs, including operators, developers and data analysts. Project members can log in to the Mini Program admin console. The admin can add and delete project members and can also set their roles in Member Management.
- Test member: Members who participate in the internal test of Mini Program. They can use the test version of Mini Program but are not project members. The admin and project members can add and delete test members.

Different project members have different permissions to ensure that the development of Mini Program is safe and orderly.

| Permissions                     | Operators | Developers | Data Analysts |
| :------------------------------ | :-------- | :--------- | :------------ |
| Developer permissions           |           | √          |               |
| Experience permissions          | √         | √          | √             |
| Login                           | √         | √          | √             |
| Data analysis                   |           |            | √             |
| Pay                             | √         |            |               |
| Promotion                       | √         |            |               |
| Development management          | √         |            |               |
| Development settings            |           | √          |               |
| Service suspension              | √         |            |               |
| Official Account disassociation | √         |            |               |
| Tencent Cloud management        |           | √          |               |
| Mini Program plug-in            | √         |            |               |
| Game operation management       | √         |            |               |

Permission description

- Developer permissions: perform development using Weixin DevTools and the developer version of Mini Programs
- Test member permissions: use the test version of Mini Programs
- Login: log in to the Mini Program admin console without the confirmation of the admin
- Data analysis: view Mini Program data using the Mini Program statistics module
- Pay: use the Mini Program Pay (virtual payment) module
- Promotion: use the Mini Program ad host and advertiser modules
- Development management: submit Mini Programs for review, as well as release and withdraw Mini Programs
- Development settings: set the server domain name and message push for the Mini Program, and set to scan ordinary link QR codes to open the Mini Program
- Service suspension: Suspend the online services of the Mini Program
- Official account disassociation: unlink the Official Accounts associated to the Mini Program
- Mini program plug-in: perform Mini Program plug-in development management and settings
- Game operation management: use the **Media Asset Management**, **Game Circle Management** and other features in the mini game admin console

> 📘 Note
> 
> The project manager controls the sensitive operations of the Mini Program, such as release, withdrawal, and removal. The sensitive operation permissions should not be assigned to unrelated personnel.

## Mini Program Versions

In the general software development process, the developers write and test the developer version of programs. When the program reaches a stable state ready for test, the developers will give the test version to the product manager and test engineers for experience and test. After the bugs in the program are fixed, the developers will release the program to external users for use. According to the procedure, we determined the Mini Program versions in Mini Program projects, as shown in Table 5-3.

Table 5-3 Mini Program Versions

[block:parameters]
{
  "data": {
    "h-0": "Permissions",
    "h-1": "Description",
    "0-0": "Developer version",
    "0-1": "You can use the Weixin DevTools to upload codes to the developer version, which only keeps the latest uploaded codes for each developer.  \nYou can click **Submit for review** to submit the code for review. The developer version can be deleted without affecting the codes in the online version and the in-review version.",
    "1-0": "Test version",
    "1-1": "You can select a developer version as a test version.",
    "2-0": "In-review version",
    "2-1": "Only one code version can be under review. After the review result comes out, you can release the program online, or directly resubmit it for review to overwrite the original in-review version.",
    "3-0": "Online version",
    "3-1": "The code version is used by all online users, which will be overwritten by a new version released later."
  },
  "cols": 2,
  "rows": 4,
  "align": [
    "left",
    "left"
  ]
}
[/block]


In the collaborative development mode, a Mini Program may be developed by multiple developers at the same time. Developers often need to view the actual effect on a mobile phone after writing the codes on the Super Hub Mini App DevTools, so each developer has a developer version of his own. The developer version is changeable since the developer may modify the code to overwrite his developer version at any time. To provide test engineers and the product manager with a complete and stable version for experience and test, the Mini Program platform allows you to set a developer version as the test version. Therefore, it is recommended to separately assign a developer role during the project development phase, responsible for uploading stable code for experience and test, and set the developer version uploaded by him as the test version.

## Release

A Mini Program generally goes through **Preview > Upload Code > Submit for Review > Release** from development completion to release.

### Preview

Developers can use the Super Hub Mini App DevTools to preview the Mini Program, so as to check the actual performance of the Mini Program on the mobile client.

When the developer clicks the Preview button in the action bar on the top of the Super Hub Mini App DevTools, the Super Hub Mini App DevTools will automatically pack the current project and upload the Mini Program code to the server of Super Hub Mini App. Upon success, a QR code will be displayed on the interface. Use the developer's Super Hub Mini App ID of the current Mini Program to scan QR code to view the actual performance on the mobile device.

### Upload Code

Unlike preview, the purpose of uploading code is to submit code for user experience or review.

Click the Upload button in the action bar at the top of the Weixin DevTools, and enter the version number and project remarks. Note that the version number and project remarks are used to help the admin check the version. Developers can enter the two fields according to their actual requirements.

After the code is successfully uploaded, you can log in to the Mini Program admin console, and go to Development Management > Developer Version to find the submitted version.

You can set this version as the test version or submit it for review.

### Submit for Review

In order to ensure the quality of the Mini program to comply with relevant specifications, the release of the Mini Program is subject to review.

After the Mini Program code is uploaded in the Super Hub Mini App DevTools, you can log in to the Mini Program admin console, and go to** Development Management > Developer Version** to find the submitted version.

In the developer version list, you can click **Submit for Review** and enter the relevant information according to the prompt to submit the Mini Program for review.

Note that developers must strictly test the version before submitting it for review. If the version fails to pass the review for too many times, the subsequent development may be delayed.

### Release

If the code passes the review, the admin's Weixin will receive a notification. Then you can log in to the Mini Program admin console, and go to Development Management > Review Version to find the version that passes the review.

You can click Release to release the Mini Program. We provide two Mini Program release modes: full release and phased release. Full release means that when a Mini Program is released, all users accessing the Mini Program will use the latest version. Phased release can control some users to use the latest version in different time periods, which is also known as beta release. Generally speaking, when releasing a usual Mini Program, you can use full release. As the Mini Program carries more and more features and is used by more and more users, the phased release is a very good way to control risks.

### Mini Program Code

In many scenarios, users can quickly enter a Mini Program via code-scanning. When the Mini Program was originally designed, the Mini Program platform provided the form of QR code. However, we found that when a user scans a QR code, he/she does not know what kind of service he/she will receive through this code-scanning, because the QR code may be linked to Official Account, Mini Program, web service, payment page, adding friends and other services. To give users a clear understanding of the service before scanning the QR code, Super Hub Mini App designed the Mini Program code, as shown in Figure 5-3.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/fd22188-8.png",
        null,
        "Figure 5-3 Mini Program Code of \"Mini Program Data Assistant"
      ],
      "align": "center",
      "caption": "Figure 5-3 Mini Program Code of \"Mini Program Data Assistant"
    }
  ]
}
[/block]


The Mini Program code is more recognizable and visually impactful in terms of style. Compared with the QR code, it can make the brand image of the Mini Program theme more clear and obvious, and help developers to promote their Mini Programs better. After a Mini Program is released, the Mini Program management platform will provide preview and download of the corresponding Mini Program code, and developers can download the code for online and offline Mini Program service promotion.

## Operations Data

We provide you with two methods to view the Mini Program [operation data.](<>)

Option 1:

Log in to the [Mini Program admin console](<>), and go to **Data Analysis**, and then click the desired tab to view the relevant data.

Option 2:

Use the Mini Program data assistant to easily view operation data in Mini App.
