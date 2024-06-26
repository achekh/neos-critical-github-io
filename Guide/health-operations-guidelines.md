---
title: "Health Operations Guidelines"
slug: "health-operations-guidelines"
excerpt: "This section details the health operations guidelines."
hidden: true
metadata: 
  image: []
  robots: "index"
createdAt: "Tue May 09 2023 05:20:17 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Mon May 29 2023 11:43:26 GMT+0000 (Coordinated Universal Time)"
layout: "default"
parent: "Guide"
nav_exclude: true
---
# Health Operations Guidelines 
This section details the health operations guidelines.

***

- User Security Solutions
- Content Security Solutions

# User Security Solutions

## Safe wind control interface

In order to improve the ecological security of the Mini App open platform, we aim at the possible malicious registration, marketing cheating and other black production risks and security issues in each application scenario of the Mini Program. Platform open API provides security risk control interface to developers to help developers deal with the risk of marketing fraud such as scalping, false transactions, malicious fraud subsidies, and bulk registration, forged identity and other registration black production risks, In order for developers to maintain the Mini Program operation order and security.

## Security wind control interface provides capabilities and application scenarios

- Marketing cheating scene: In the first single offer and special offer and other marketing activities effectively identify brush, false transactions, malicious fraud insurance fraud subsidies and other acts of undermining the operational order and security.
- Malicious registration: Identify and intercept malicious registration behaviors such as bulk registration, garbage trumpet, false identity, etc.

## Competency Application Process

1. Log in to the Mini Program.
2. Under the Development tab, click Development managementSecurity CenterRisk User Can app to launch it.

## Risk Rating Statement and Recommendations for Use

The number of risk levels returned by the interface allows the developer to assess the user's level of risk. In order to achieve accurate interception and safeguard the orderly and healthy growth of the business, the meaning of risk level and the corresponding business use can be understood in relation to the following guidelines and recommendations.

| Risk level   | Proposed disposal options                                                                                                                                                                                                                                                                                                       |
| :----------- | :------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| Risk Level 0 | No risk, no blocking                                                                                                                                                                                                                                                                                                            |
| Risk level 1 | Low suspicious risk, recommend simple verification (e.g. CAPTCHA, SMS, etc.)                                                                                                                                                                                                                                                    |
| Risk level 2 | Mildly suspicious risk, simple verification is recommended (e.g. CAPTCHA, SMS, etc.)                                                                                                                                                                                                                                            |
| Risk level 3 | Moderate risk of suspicion, recommended based on business scenarios to take certain measures to avoid harm. For example, marketing campaigns reduce the probability of high level rewardsList-beating activities reduce the weight of such votesLogin registration requires secondary verification, etc                         |
| Risk level 4 | Highly suspicious risk, recommended direct intercept based on business logic. For example, the Red Packet type activity returns no winning or minimum red packetNo votes are counted in the List Type Eventslog in/Registration operations require secondary verificationHigh-risk business may choose to limit this operation. |

### Develop access guidelines

calling API

***

# Content Security Solutions

In order to improve the ecological security of WeChat open platform, the security problems that may exist in each content scene of the Mini Program, Platform open API to provide developers with content security solutions to help developers to deal with text, pictures, audio content types of sensitive content identification, yellow content recognition, terrorist content recognition and other issues, so that developers maintain the Mini Program operation order and security.

## Text Content Security Detection:

**Functional Description**: Functional Description: Text audit interface can identify pornography, political violations, violence and other illegal harmful content in text information, help users timely and accurately prevent the risk of violations, can be used for content audit, sensitive information filtering, public opinion monitoring and other scenarios.

- This function is based on the 100,000-level large-scale sensitive thesaurus, combined with a variety of text confrontation methods, policy authority requirements, and the use of deep learning technology, efficient identification of high-risk harmful content. At the same time, we will continue to update and iterate according to the large-scale corpus and real-time anti-manslaughter system to ensure the continuous improvement.

**Application Scenarios**: User profile text content detectionMedia News Category Users Post Articles, Community Comments Content DetectionGamesUsersEdit Uploaded Material(Such as answer type Mini Program user uploaded questions and answers) detection and so on.

## Image Content Security Detection:

Functional Description: Image Content Security Based on Tencent's massive data resources and deep learning technology, it provides intelligent audit services for image content developers, Not only can help users reduce the risk of pornography, political violations, violence and terror, but also can greatly save manual audit costs, protect the healthy development of business.

- Pornographic recognition can be done by learning and analyzing the color, pose and scene of images.
- Provides scene recognition including facial recognition of sensitive people and sensitive events.
- Based on public opinion analysis, it provides a more rigorous model of violence and terrorism, intelligent identification of violence, bloody scenes, terrorism, extremism and other suspected banned images.

**Application Scenarios**: User custom avatar detection, tools involving photo applications(Such as P map, selfie class applications) user photo upload detectionE-commerce goods on the shelf picture detectionImage Detection in Media User ArticlesDetection of images uploaded by social users, etc

## Audio Content Security Detection:

**Functional Description:** Identify audio content in the yellow, related to politics, abuse and other violations, thereby reducing labor costs and improving audit efficiency. Application **Scenarios**: Voice detection in game chat channelsVoice Detection of Anchors in Live StreamingForum community posts audio detection of related media content.

## Develop access guidelines

- TextContentSecurityInterfaceDocument: msgSecCheck
- ImageContentSecurityInterfaceDocument: imgSecCheck
- audio frequency/Image Content Secure Asynchronous Interface Document: mediaCheckAsync

## common problems

## 1. please do not rely entirely on content security services

- The content of Mini Program UGC into content security service can effectively alleviate manual audit and reduce the risk of violations, But accessing content security services does not mean solving all problems once and for all. To further ensure content security, we still suggest setting up manual verification in some links to make up for the shortcomings of AI algorithm.
- For example, API judgment as REVIEW content, indicating that there may be risk, requiring manual confirmationAPI judged to be PASS content, may contain missed violations of content, can be in accordance with a certain proportion of spot checks.

## 2. If you have questions or needs about the use of a content security solution, how should you respond?

WeChat Open Community opened a security risk control zone, developers can go to the [security center zone](<>) post interactive communication.
