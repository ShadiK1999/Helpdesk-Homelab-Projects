# Group Policy Object Creation

This project demonstrates the creation of Group Policy Objects (GPO's) for the Homelab domain `mydomain.com`.

During the completion of this lab, the following GPO's were created:
- Password Policy
- Drive Mapping Policy
- Desktop Wallpaper Policy
- Control Panel Access Policy
- Removable Device Policy

## Pre-lab Configurations
Before this lab began a few configuration changes were made to the environment:
- OU's for USA, Asia and Europe were created.
- Each location OU was populated with a Users, Computers and Servers OU.
- The Users OU within the USA OU was populated with security groups for different departments:
    - IT
    - HR
    - Sales
    - Accounting
    - Management

| Creating IT security group within USA Users OU.                     |
| ------------------------------------------------------------------------------------- |
| ![](./Screenshots/0%20prelab%20groups%20setup.png)                 |

## Creating Password Policy GPO
1. The `Group Policy Management Console` was opened.

| Group Policy Management Console.                     |
| ------------------------------------------------------------------------------------- |
| ![](./Screenshots/1%20GPMC.png)                 |

2. The domain location was right-clicked and `Create new gpo` was selected from the menu.
3. In the GPO creation window, the new GPO was named "password policy"

| Name new GPO.                     |
| ------------------------------------------------------------------------------------- |
| ![](./Screenshots/2%20create%20new%20gpo.png)                 |

4. Once created, the GPO was right-clicked to access the editing window.

| Rename PC input in system settings.                     |
| ------------------------------------------------------------------------------------- |
| ![](./Screenshots/3%20policy%20editor.png)                 |

5. Navigated to `Computer Configurations > Policies > Windows Settings > Security Settings > Account Policies > Password Policy`.

| Rename PC input in system settings.                     |
| ------------------------------------------------------------------------------------- |
| ![](./Screenshots/4%20password%20policy.png)                 |

6. The following features were configured:
- Minimum password length - 12 characters
- Password must meet complexity requirements
- Maximum password age - 90 days

| Configure minimum password length.                     								|Configure password complexity.                   								  |Configure maximum password age.|
| ------------------------------------------------------------------------------------- |-------------------------------------------------------------------------------------|------------|
| ![](./Screenshots/5%20length.png)                 						|![](./Screenshots/6%20complexuty.png)                					  |![](./Screenshots/7%20password%20age.png)|


## Create Drive Mapping GPO
1. open GPMC
2. right click domain and select create new gpo
3. name GPO "Drive Mapping"
4. right click GPO to edit
5. navigate to User Configuration > Preferences > Windows Setting > Drive Maps
6. right click Mapped Drive location and select new > mapped drive
7. specify drive location and what drive letter to use
8. verify drive is there

## Create Desktop Wallpaper Policy GPO
1. open GPMC
2. right click domain and select create new gpo
3. name GPO "Desktop Wallpaper"
4. right click GPO to edit
5. navigate to User Configuration > Administrative Templates > Desktop > Desktop > Desktop Wallpaper
6. click Enables to enable the policy
7. enter wallpaper path and style
8. click apply and okay

## Create Restrict Access to Control Panel GPO
1. open GPMC
2. right click domain and select create new gpo
3. name GPO "Desktop Wallpaper"
4. right click GPO to edit
5. navigate to User Configuration > Administrative Templates > Control Panel > Prohibit access to Control Panel and PC settings
6. click Enabled
7. Click Apply and Okay

## Create Disable USB Storage GPO
1. open GPMC
2. right click domain and select create new gpo
3. name GPO "Desktop Wallpaper"
4. right click GPO to edit