---
title: "Development Principles and Considerations"
slug: "development-principles-and-considerations"
excerpt: "This section explains the developmental principles and considerations."
hidden: true
metadata: 
  image: []
  robots: "index"
createdAt: "Mon May 08 2023 10:44:01 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Mon May 29 2023 11:24:16 GMT+0000 (Coordinated Universal Time)"
---
This document collates some common security risks and vulnerabilities in the development of Mini Programs, used to help developers find and repair related vulnerabilities in development links, to avoid business and data losses after the launch. Developers must base their development on the following principles:

- Non-trust principle, do not trust the data submitted by users, including data provided by third-party systems, necessary data verification must be put in the background verification.
- Minimum permission principle, code, module and so on can only complete the task of the minimum permission, not given unnecessary permissions.
- Prevent the preservation of user sensitive data in plain text.
- Mini Program code (excluding cloud function code) with traditional Web The front-end code of an application is similar and can be acquired and de-confused externally. Important business logic should be placed in the back-end code or cloud functions.
- Background interface calls and cloud function calls must have valid authentication.

# currency

## Interface authentication

Interface authentication means that background interfaces (including self-built background interfaces and cloud functions) need to verify the permissions of this interface when they are called, otherwise it is easy to occur overreach. If a product delete interface, the backend should verify the caller's identity when receiving the request (such as openid ip Address, developer - defined login state information, etc.), only the specified user can be deleted by checking.

Overreach is usually divided into parallel and vertical:

- Parallel overreach

> Parallel overreach refers to overreach between the same roles. A1、 A2 Are ordinary users, A1 By requesting a backend interface userinfo.phpid=A1 To get users A1 Own information, if userinfo.php Permission verification is not performed, the user A1 Change the request to userinfo.phpid=A2 You can access the A2 User's information, causing A2 Disclosure of user information.

- Vertical overreach

> Vertical overreach refers to overreach between different roles. B1 Is the administrator, B2 Are normal users, administrators B1 By requesting a backend interface getalluserinfo.php Can obtain information about all registered users if getalluserinfo.php No permission check was performed, B2 The user may also request getalluserinfo.php To obtain all registered user information, there is ultra vires.

## Development suggestions:

1. Sensitive data and capacity-related interfaces need authentication in the background. Usually checkable openid、 IP Address, custom landing state and other information.
2. Authentication logic should be put in the background, should not be replaced by hidden pages and hidden ons in the front of the Mini Program. Reference to Principle 4.
3. Example authentication code (for reference only)
   > 1. Self-built backstage authentication rights
   >
   > > ```
   > > function actionDelete(){
   > >     $item_id = $_POST["item_id"] 
   > >     $openid = $_POST["openid"]
   > >     $ip = $_SERVER['REMOTE_ADDR']
   > >     $user_role = $_SESSION["user_role"]
   > >     if ($openid === "xxx" &&
   > >         $ip === "192.168.0.101" &&
   > >         $user_role === "admin") {
   > >             // Perform a delete operation
   > >             // ...
   > >             return 0
   > >         } else {
   > >             // Record illegal requests
   > >             // ...
   > >             return -1
   > >         }
   > > }
   > > ```

> > > > ii. Cloud function interface authentication
> > >
> > > ```Text code
> > > exports.main = async (event, context) => {
> > >     const { OPENID, APPID, UNIONID } = cloud.getWXContext()
> > >     if (OPENID === "xxx") {
> > >         // Perform a delete operation
> > >         // ...
> > >     } else {
> > >         // Record illegal requests
> > >         // ...
> > >     }
> > > }
> > > ```

## Code Management and Leaks

1. Use git、 svn And other version management tools, will produce .git And other directories. Some editors or software also generate temporary files while running. Source leaks can occur if these directories or files are brought to production.
2. Using Mini Program code management platform or github And other third-party platforms need to pay attention to the project permissions, do not open sensitive, internal projects.

### Development suggestions:

Backup files and files produced by version management tools do not sync to Web Directory.  
External access prohibited .git And other directories with files.  
In [Mini Program Code Management Platform]\(<https://Configure> appropriate access within management platforms such as git.weixin.qq.com).

# Mini Program

## Information leaks

Sensitive Information refers to data that, if disclosed, may be harmful to the developer's business, partners and users, including but not limited to**accounts App secret, privileged account information, background encryption key, login account password, user ID number, phone number, bank card number, etc**.

### Development suggestions:

1. Sensitive information should not be encoded in plaintext, annotated, reversible (as Base64), unsafe hash functions such as MD5、 SHA1) and other forms appear within the Mini Program file.
2. Part of the sensitive information such as the user's bank card number, mobile phone number and so on need to be used for display, need to conduct desensitization processing. Common desensitization specifications are as follows:

| Type of sensitive information | Display sample                                                                                                                                                                                                                                                                                                                                                    |
| :---------------------------- | :---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Full name                     | Name is only two words. Type the first word, such as:3. More than two words, only the first and last, the rest are coded, such as: WangIV. O\*\*five                                                                                                                                                                                                              |
| ID                            | Show only the first and last bits, such as: 3**\*\***\*\*\*\***\*\***1                                                                                                                                                                                                                                                                                            |
| Cell phone number             | After removing the international code of the mobile phone, when the number is not less than 10 digits, only the first three and the last two digits are displayed, such as: 156\*77。 When the number of mobile phone number is less than 10 digits, only the first two and the last two digits are displayed, such as: 1289。 Country code can be fully displayed. |
| Bank card                     | Show only the last 4 digits like:\***\*\*\*\***1234                                                                                                                                                                                                                                                                                                               |

3. If there is sensitive information leakage problem, WeChat open platform will likely remove the Mini Program, and suspend the relevant services of this Mini Program.

# Background (including cloud functions and self-built background)

## Injection loophole

Injection vulnerability (SQL, Commands, etc.) typically refers to the user bypassing background code restrictions and directly running a database, shell Executes custom code within.

Common injection vulnerabilities are:

## SQL Injection

SQL Injection means Web Program code for the user submitted parameters without effective filtering directly spliced to SQL Statement, causing the special character in the parameter to break the SQL Statement original logic, hackers can use this vulnerability to execute arbitrary SQL Statement.

### Development suggestions:

1. Database operations are performed using parameterized queries provided by the database. It is not allowed to synthesize directly by stitching strings SQL Statement.
2. If there is a part of the case that needs to be synthesized by splicing SQL , spliced variables must be processed:
   1. For integers, you need to determine whether the variable is of an integer type.
   2. For strings, you need to escape single quotes, double quotes, etc.
3. avoid Web Application Display SQL Error message.
4. ensure Web The coding of each data layer in the application is unified.

## Command injection

Command injection vulnerability refers to Web If user parameters are not effectively filtered, the attacker can construct malicious parameters to spell the command to execute arbitrary commands.

### Development suggestions:

- To the data entered by the user (such as 、|, &, etc.) for filtering or escaping.

## Weak password

Weak password refers to the user name, password, or use the default account. Attackers can login these accounts to modify the background data or conduct the next intrusion operations.

### Development suggestions:

1. Background service disable default account, modify background weak password.
2. Sensitive services add secondary verification mechanism, such as SMS verification code, mailbox verification code and so on.

## File upload vulnerability

File upload vulnerability refers to Web The application allows users to upload specified files, but does not verify the legality of file types, formats, etc., resulting in the upload of unexpected format files.

### Development suggestions:

- Correctly resolve the file types of uploaded files and limit the types of files that can be uploaded by whitelist.

## File Downloads

File download vulnerability refers to the Web The application allows users to download the corresponding file by specifying the path and file name, but does not correctly limit the scope of the directory where the downloadable file is located, resulting in the expected range of files outside the download leak.

### Development suggestions:

1. Correctly limit the range of directories where downloadable files reside
2. By specifying the file id Way to find and download the corresponding file

## Directory traversal

Directory traversal refers to leakage of server directory contents caused by insufficient validation of user input or lax configuration by back-end services. External may obtain system files, background code and other sensitive files through directory traversal.

### Development suggestions:

1. web Service configuration
   1. Server Disable Display Directory
   2. Set directory access rights
   3. In each directory, place an empty index.html page
2. web Application Code

<!---->

1. Strict checking of file path parameters, limiting the scope of the file

## Conditional competition

A more common example of conditional competition is an attacker passing concurrent https Request and achieve multiple awards, multiple harvests, multiple gifts and other abnormal logic can trigger the effect.

- Vulnerability code example

```Text code
// Query the remaining number of awards from DB, the initial value is 1
int remain_times = SelectRemainTimes()

if(remain_times > 0){
    EarnRewards()          // Users get rewards
    ClearRemainTimes()     // Zero out the remaining number of awards in the DB
}
```

Developers are designed to allow users to receive rewards only once, but when concurrent requests occur, there is a chance that requests A And requests B Both just finished executing the second line of code, at which point the two requested remain_times Both are 1, that is, can be judged by the fourth line of code, get two rewards.

### Development suggestions:

- Lock the key (complete) logic or process it as a queue task.
