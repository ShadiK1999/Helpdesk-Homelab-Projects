# File Services Configuration

This project demonstrates setting up file sharing services to manage network resources and permissions.

## What's Being Covered

- File Sharing
- Shared permissions
- NTFS permissions 
- Sharing methods
    - Mapped sharing
    - Network sharing
- File Server Resource Manager (FSRM)
    - Installation
    - Configuring quotas and thresholds

## Configure Shared Permissions on a Folder 

1. On the Domain Controller, a folder was created on the C: drive with the filename SHARED 

| Creating `SHARED` folder.                     |
| ------------------------------------------------------------------------------------- |
| ![](./Screenshots/1%20create%20folder.png)                 |

2. The `SHARED` folder's advanced sharing options were access by right-clicking on it and selecting `Properties > Sharing > Advanced Sharing`.

| Opening folder share properties.                     |
| ------------------------------------------------------------------------------------- |
| ![](./Screenshots/2%20folder%20properties.png)                 |

3. Network sharing was enabled via the "Share this folder" checkbox. This also enabled permissions configuration for the folder buy clicking the "Permissions" button.

| Enabling network sharing.                     |
| ------------------------------------------------------------------------------------- |
| ![](./Screenshots/3%20advanced%20sharing.png)                 |

4. Domain users were added to the SHARED folder's access permissions.

| `SHARED` folder permissions.                     								|Adding Domain Users to folder access.                   								  |Permissions with added users|
| ------------------------------------------------------------------------------------- |-------------------------------------------------------------------------------------|----------|
| ![](./Screenshots/4%20advanced%20sharing%20permissions.png)                 						|![](./Screenshots/5%20add%20domain%20users.png)                					  |![](./Screenshots/6%20show%20domain%20users.png)|


## Configure NTFS Permissions

1. NTFS permissions of the SHARED folder were accessed via the Security tab of the folder's properties. Though no permissions were configured here.

| NTFS permissions.                     |
| ------------------------------------------------------------------------------------- |
| ![](./Screenshots/7%20NTFS.png)                 |


## Sharing Methods

### Mapped Sharing Method

1. The client PC was logged into using a domain user account.
2. The SHARED folder was mapped to a network drive via the "Map Network Drive" function in file explorer using the location `\\DC\SHARED`.

| Mapping the network drive.                     | Network drive accessible |
| ------------------------------------------------------------------------------------- |----------|
| ![](./Screenshots/8%20map%20network%20drive.png)                 |![](./Screenshots/9%20show%20network%20drive.png)|


note: this method does not persist and the network drive will disappear on reboot.

### Network Sharing Method

1. Group Policy Management Console was access on the Domain Controller.
2. A GPO named Mapped Drives was created and the and the drive maps User Configuration was accessed in the Group Policy Management Editor.

note: for in-depth GPO explanations see the [Group Policy Management](https://github.com/ShadiK1999/Helpdesk-Homelab-Projects/tree/main/Active%20Directory/GroupPolicy) projects. 

3. A new mapped drive was configured by right clicking the Drive Maps location and selecting New > Mapped Drive. The location `\\DC\SHARED` was provided in the input field as well as the label SHARED and the drive letter S.

| Drive Maps configuration.                     								|Mapping the network drive.                   								  |
| ------------------------------------------------------------------------------------- |-------------------------------------------------------------------------------------|
| ![](./Screenshots/10%20drive%20maps.png)                 						|![](./Screenshots/11%20new%20drive%20properties.png)                					  |

4. After the GPO was created, it was linked to the USA > Users OU.

| Linking the GPO.                     |
| ------------------------------------------------------------------------------------- |
| ![](./Screenshots/12%20linked%20gpo.png)                 |

5. The client PC was logged into using a domain user account.
6. File Explorer was opened and in the SHARED folder was present within the Network locations.

| Network drive accessible.                     |
| ------------------------------------------------------------------------------------- |
| ![](./Screenshots/13%20see%20network%20folder.png)                 |

note: this will persist even after the computer is rebooted.

## File Server Resource Manager 

This application be used to configure data quotas and thresholds, file screening and file classification management.

### Installation

1. Server Manager was opened and the Add Roles and Features wizard was accessed
2. In the Select Server Roles section, FSRM was selected through File and Storage Services > File and iSCI Services > File Server Resource Manager

| Selecting FSRM in Add ROles and Features.                     |
| ------------------------------------------------------------------------------------- |
| ![](./Screenshots/14%20add%20roles%20and%20features.png)                 |

3. Defaults were selected for the rest of the wizard and the feature was installed.

| FSRM installed and opened.                     |
| ------------------------------------------------------------------------------------- |
| ![](./Screenshots/15%20FSRM.png)                 |

### Quota Management Configuration

This feature sets a quota for the amount of data available within a folder and also can be used to configure threshold notifications for shared folders.

1. Quota Management was opened within the FSRM.

| Quota Management window.                     |
| ------------------------------------------------------------------------------------- |
| ![](./Screenshots/16%20quota%20management.png)                 |

2. The Create Quote window was opened by right-clicking the Quotas location.
3. A custom quota of 100MB was set and an email alert was configured when the 80% threshold is passed. This was configured by clicking the custom properties button and adding the configurations within the window.

| Creating custom quota.                     |Configuring threshold with email alert.|
| ------------------------------------------------------------------------------------- |----------|
| ![](./Screenshots/18%20create%20quota%20.png)                 |![](./Screenshots/19%20add%20threshold.png)|

### File Screening Management

This feature controls what file types are allowed on the shared folder.

1. File Screening Management was opened within the FSRM
2. The Create File Screen window was opened by right-clicking the File Screens location.

| Create File Screen window.                     |
| ------------------------------------------------------------------------------------- |
| ![](./Screenshots/20%20create%20file%20screen.png)                 |



3. The `SHARED` folder path was inputted in the location field. 
4. A custom file screen was created with the following blocks:
- Audio and Video files
- Executable files
- Image files
- Web Page files

note: different template options for file screens can be selected via the dropdown menu instead of creating a custom screen.

| Creating the custom file screen.                     |
| ------------------------------------------------------------------------------------- |
| ![](./Screenshots/21%20custom%20screen.png)                 |
 
5. The custom screen was given the name SHARED

| Custom file screen created.                     |
| ------------------------------------------------------------------------------------- |
| ![](./Screenshots/22%20verify%20file%20screen.png)                 |

6. The file screen was tested by attempting to save a screenshot on the client pc to the SHARED folder

| Attempt to save image file.                     								|File screen blocks save attempt.                   								  |
| ------------------------------------------------------------------------------------- |-------------------------------------------------------------------------------------|
| ![](./Screenshots/23%20saving%20image%20attempt.png)                 						|![](./Screenshots/24%20image%20blocked%20.png)                					  |


