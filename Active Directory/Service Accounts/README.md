# Implementing Service Accounts

## Create Service Account
1. A new Organisational Unit was created to house the Service Accounts.
2. A user object was created within the Service Accounts OU with the following information
- Name: Website Login
- Logon name: $Website-login
- Password: Password1

note: using a special character for the logon name helps to differentiate from user accounts.

3. A description was added to the account, following best practices.

## Installing and configuring Sysinternals Suite

1. Navigated to the [Sysintenals Suite download site](https://learn.microsoft.com/en-us/sysinternals/downloads/sysinternals-suite) on the client computer.
2. Once downloaded and extracted, The Autologon tool was opened and the service account login information was inputted.
3. After configurations were completed, the system was tested by rebooting.

## Setup browser for automatic startup

1. on the client machine, the Mozilla Firefox browser settings were opened.
2. To specify a webpage on startup, the custom URLs section was opened via Settings>Home>Homepage and new windows>Custom URLs.
3. This feature was tested by closing and reopening the browser.
4. To make the browser run in full screen automatically, the browser shortcut properties were opened and the command --kiosk was inputted into the Target field.
5. To make sure the site opens on startup, Firefox was then added to the Startup programs folder
6. The client computer was set to never sleep via the Power and Sleep settings

## Create GPO to restrict local logon

1. The Group Policy Management Console was opened and a new GPO was created, named Restrict Service Account Logon.
2. Local logon settings were accessed via Computer Configuration>Policies>Windows Settings>Security Settings>Local Policies>User Rights Assignment>Deny log on locally
3. Local logon access was denied to the #All-Employees group and the GPO was linked to the USA>Computers OU.
4. The GPO was tested by attempting to log on as a different user on the client machine.
