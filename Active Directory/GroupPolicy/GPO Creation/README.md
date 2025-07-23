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

| Name Password Policy GPO.                     |
| ------------------------------------------------------------------------------------- |
| ![](./Screenshots/2%20create%20new%20gpo.png)                 |

4. Once created, the GPO was right-clicked to access the editing window.

| Group Policy Management Editor. .                     |
| ------------------------------------------------------------------------------------- |
| ![](./Screenshots/3%20policy%20editor.png)                 |

5. Navigated to `Computer Configuration > Policies > Windows Settings > Security Settings > Account Policies > Password Policy`.

| Password policy features.                     |
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
1. The `Group Policy Management Console` was re-accessed.
2. The domain location was right-clicked and `Create new gpo` was selected from the menu.
3. In the GPO creation window, the new GPO was named "password policy"

| Name Drive Mapping GPO.                     |
| ------------------------------------------------------------------------------------- |
| ![](./Screenshots/8%20create%20new%20gpo.png)                 |

4. Once created, the GPO was right-clicked to access the editing window.
5. Navigated to `User Configuration > Preferences > Windows Setting > Drive Maps`

| Dive Maps configuration window.                     |
| ------------------------------------------------------------------------------------- |
| ![](./Screenshots/9%20drive%20maps.png)                 |

6. The Drive Maps location was right-clicked and `new > mapped drive` was selected.
7. The drive location was specified in the window and a drive letter was selected to use. In this lab, the `E:` drive was selected.

| Creating new network drive.                     								|Verifying new network drive has been created.                   								  |
| ------------------------------------------------------------------------------------- |-------------------------------------------------------------------------------------|
| ![](./Screenshots/10%20new%20drive%20properties.png)                 						|![](./Screenshots/11%20new%20drive%20configures.png)                					  |

note: there is no actual network drive and only an example path was provided.

## Create Desktop Wallpaper Policy GPO
1. The `Group Policy Management Console` was re-accessed.
2. The domain location was right-clicked and `Create new gpo` was selected from the menu.
3. In the GPO creation window, the new GPO was named "Desktop Wallpaper"

| Name Desktop Wallpaper GPO.                     |
| ------------------------------------------------------------------------------------- |
| ![](./Screenshots/19%20new%20gpo.png)                 |

4. Once created, the GPO was right-clicked to access the editing window.
5. Navigated to `User Configuration > Administrative Templates > Desktop > Desktop > Desktop Wallpaper`

| Desktop policy features.                     |
| ------------------------------------------------------------------------------------- |
| ![](./Screenshots/12%20desktop%20wallpaper.png)                 |

6. Once opened, the policy was enabled and path as well as a style was provided for the new wallpaper.

| Configuring desktop wallpaper policy.                     |
| ------------------------------------------------------------------------------------- |
| ![](./Screenshots/13%20edit%20wallpaper%20policy.png)                 |

## Create Restrict Access to Control Panel GPO
1. The `Group Policy Management Console` was re-accessed.
2. The domain location was right-clicked and `Create new gpo` was selected from the menu.
3. In the GPO creation window, the new GPO was named "password policy"

| Name Restrict Control Panel GPO.                     |
| ------------------------------------------------------------------------------------- |
| ![](./Screenshots/14%20create%20new%20gpo.png)                 |

4. Once created, the GPO was right-clicked to access the editing window.
5. Navigated to `User Configuration > Administrative Templates > Control Panel > Prohibit access to Control Panel and PC settings`
6. Once opened, the policy was enabled and applied.

| Enabling Control Panel restriction.                     |
| ------------------------------------------------------------------------------------- |
| ![](./Screenshots/15%20enabled%20restrict%20access%20gpo.png)                 |

## Create Disable USB Storage GPO
1. The `Group Policy Management Console` was re-accessed.
2. The domain location was right-clicked and `Create new gpo` was selected from the menu.
3. In the GPO creation window, the new GPO was named "password policy"

| Name USB storage GPO.                     |
| ------------------------------------------------------------------------------------- |
| ![](./Screenshots/16%20create%20new%20gpo.png)                 |

4. Once created, the GPO was right-clicked to access the editing window.
5. Navigated to `Computer Configuration > Administrative Templates > System > Removable Storage Access > All Removable Storage Classes: Deny All Access` 
6. Once opened, the policy was enabled and applied.