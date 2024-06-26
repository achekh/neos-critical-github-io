---
title: "Calender"
slug: "calender-api"
excerpt: "This section consists of the list of Calendar related APIs."
hidden: false
createdAt: "Mon Apr 24 2023 08:05:31 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Wed Dec 13 2023 07:29:39 GMT+0000 (Coordinated Universal Time)"
layout: "default"
parent: "Device"
grand_parent: "APIs"
---
# Calender 
This section consists of the list of Calendar related APIs.

***

- [ addPhoneRepeatCalendar](doc:calender-api#addphonerepeatcalendarobject-object)
- [addPhoneCalendar](doc:calender-api#addphonecalendarobject-object)

# addPhoneRepeatCalendar(Object object)

Adds a repeated event to the system calendar.

# Parameters

**Object object**

| Attribute      | Type     | Required | Description                                                                                                    |
| :------------- | :------- | :------- | :------------------------------------------------------------------------------------------------------------- |
| title          | String   | Yes      | Calendar event title.                                                                                          |
| startTime      | Number   | Yes      | UNIX timestamp of the start time (the number of seconds elapsed since January 1, 1970).                        |
| allDay         | Boolean  | No       | Whether it is an all day event. Default value: `false`.                                                        |
| description    | String   | No       | Event description.                                                                                             |
| location       | String   | No       | Event location.                                                                                                |
| endTime        | String   | No       | UNIX timestamp of the end time, which is the same as the start time by default.                                |
| alarm          | Boolean  | No       | Whether to remind. Default value: `true`.                                                                      |
| alarmOffset    | Number   | No       | Reminder offset in seconds. Default values: 0 (reminds upon start).                                            |
| repeatInterval | String   | No       | Repeat interval. Default value: `month` (repeats monthly).                                                     |
| repeatEndTime  | Number   | No       | UNIX timestamp of the repeat end time. If this parameter is left empty, the reminder will be repeated forever. |
| success        | Function | No       | Callback function for successful API call.                                                                     |
| fail           | Function | No       | Callback function for failed API call.                                                                         |
| complete       | Function | No       | Callback function for API call end (executed for both successful and failed calls).                            |

**repeatInterval**

| Valid Value | Description                                                    |
| :---------- | :------------------------------------------------------------- |
| day         | Daily                                                          |
| week        | Weekly                                                         |
| month       | Monthly. In this mode, the date cannot be greater than day 28. |
| year        | Yearly                                                         |

# addPhoneCalendar(Object object)

Adds an event to the system calendar.

# Parameters

**Object object**

| Attribute   | Type     | Required | Description                                                                         |
| :---------- | :------- | :------- | :---------------------------------------------------------------------------------- |
| title       | String   | Yes      | Calendar event title.                                                               |
| startTime   | Number   | Yes      | UNIX timestamp of the start time.                                                   |
| allDay      | Boolean  | No       | Whether it is an all day event. Default value: `false`.                             |
| description | String   | No       | Event description.                                                                  |
| location    | String   | No       | Event location.                                                                     |
| endTime     | String   | No       | UNIX timestamp of the end time, which is the same as the start time by default.     |
| alarm       | Boolean  | No       | Whether to remind. Default value: `true`.                                           |
| alarmOffset | Number   | No       | Reminder offset in seconds. Default values: 0 (reminds upon start).                 |
| success     | Function | No       | Callback function for successful API call.                                          |
| fail        | Function | No       | Callback function for failed API call.                                              |
| complete    | Function | No       | Callback function for API call end (executed for both successful and failed calls). |
