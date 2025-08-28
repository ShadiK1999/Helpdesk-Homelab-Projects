# Implementing Service Accounts

This project demonstrates the implementation and use of Service Accounts in displaying a webpage constantly.

## Create Service Account
1. A new Organisational Unit was created to house the Service Accounts.

| Creating Services Accounts OU.                                              |
| ----------------------------------------------|
| ![](./Screenshots/1%20new%20OU.png)                 						|

2. A user object was created within the Service Accounts OU with the following information.

```
Name: Website Login 
Logon name: $Website-login
Password: Password1
```

note: using a special character for the logon name helps to differentiate from user accounts.

| Inputting service account details.                                               |  Service account successfully created.                                             |
| ----------------------------------------------|----------------------------------------------|
| ![](./Screenshots/2%20new%20account.png)                 						| ![](./Screenshots/3%20account%20created.png)                 					    |

3. A description was added to the account, following best practices.

## Installing and configuring Sysinternals Suite

1. Navigated to the [Sysintenals Suite download site](https://learn.microsoft.com/en-us/sysinternals/downloads/sysinternals-suite) on the client computer and downloaded the first option.

|   Sysinternals download page.                                            |
| ----------------------------------------------|
| ![](./Screenshots/4%20sysinternals%20site.png)                 						|

2. Once downloaded and extracted, The Autologon tool was opened and the service account login information was inputted.

| Inputting service account details to Autologon.                                              |    Successful configuration.                                           |
| ----------------------------------------------|----------------------------------------------|
| ![](./Screenshots/5%20configure%20autologon.png)                 						| ![](./Screenshots/6%20successsfully%20configures.png)                 					    |

3. After configurations were completed, the system was tested by rebooting.

|Client PC automatically logs into service account.|
|--------|
|![](./Screenshots/7%20autologin%20success.png)|

## Setup browser for automatic startup

1. On the client machine, the Mozilla Firefox browser settings were opened.

|   Firefox settings page.                                            |
| ----------------------------------------------|
| ![](./Screenshots/8%20firefox%20settings.png)                 						|

2. To specify a webpage on startup, the custom URLs section was opened via Settings>Home>Homepage and new windows>Custom URLs.

| Configuring startup page.                                              |
| ----------------------------------------------|
| ![](./Screenshots/9%20custom%20url.png)                 						|

3. This feature was tested by closing and reopening the browser.

| Browser successfully autoloads the specified URL.                                              |
| ----------------------------------------------|
| ![](./Screenshots/10%20page%20openes.png)                 						|

4. To make the browser run in full screen automatically, the browser shortcut properties were opened and the command --kiosk was inputted into the Target field.

| Firefox shortcut properties with added command.                                              |
| ----------------------------------------------|
| ![](./Screenshots/11%20auto%20fullscreen.png)                 						|

5. To make sure the site opens on startup, Firefox was then added to the Startup programs folder

| Firefox added to startup programs                                              |
| ----------------------------------------------|
| ![](./Screenshots/12%20startup%20program.png)                 						|

6. The client computer was set to never sleep via the Power and Sleep settings

| PC sleep settings.                                              |
| ----------------------------------------------|
| ![](./Screenshots/13%20never%20sleep.png)                 						|


## Create GPO to restrict local logon

1. The Group Policy Management Console was opened and a new GPO was created, named Restrict Service Account Logon.

| New GPO created.                                              |
| ----------------------------------------------|
| ![](./Screenshots/14%20new%20gpo.png)                 						|

2. Local logon settings were accessed via Computer `Configuration > Policies > Windows Settings > Security Settings > Local Policies > User Rights Assignment > Deny log on locally`.

3. Local logon access was denied to the #All-Employees group and the GPO was linked to the `USA > Computers` OU.

| Enabling deny local logon.                                              | Linking GPO to `USA > Computer` OU.                                              |
| ----------------------------------------------| ----------------------------------------------|
| ![](./Screenshots/15%20deny%20local%20logon.png)                 						| ![](./Screenshots/16%20linked%20gpo.png)                 						|

4. The GPO was tested by attempting to log on as a different user on the client machine.

| Attempting to log on as unauthorised user.                                              | Access Denied.                                               |
| ----------------------------------------------|----------------------------------------------|
| ![](./Screenshots/17%20logon%20attmpted.png)                 						| ![](./Screenshots/18%20logon%20denied.png)                 					    |

