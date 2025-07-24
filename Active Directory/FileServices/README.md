# File Services Configuration

This project demonstrates setting up file sharing services to manage network resources and permissions.

## What's Being Covered

- File Sharing
- Shared permissions
- NTFS permissions 
- Mapped sharing method
- Network sharing method
- Installing and configuring File Server Resource Manager (FSRM)
## Configure Shared Permissions on a Folder 

1. On the Domain Controller, a folder was created on the C: drive with the filename SHARED 
2. The SHARED folder's advanced sharing options were access by right-clicking on it and selecting properties > Sharing > Advanced Sharing
3. Network sharing was enabled via the "Share this folder" checkbox. This also enabled permissions configuration for the folder buy clicking the "Permissions" button.
4. domain users were added to the SHARED folder's access permissions.

##Configure NTFS Permissions

1. NTFS permissions of the SHARED folder were accessed via the Security tab of the folder's properties.

## Sharing Methods

### Mapped Sharing Method

1. The client PC was logged into using a domain user account.
2. The SHARED folder was mapped to a network drive via the "Map Network Drive" function in file explorer using the location \\DC\SHARED.

note: this method does not persist and the network drive will disappear on reboot.

### Network Sharing Method

1. Group Policy Management Console was access on the Domain Controller.
2. A GPO named Mapped Drives was created and the and the drive maps User Configuration was accessed in the Group Policy Management Editor.

note: for in-depth GPO explanations see the [Group Policy Management](https://github.com/ShadiK1999/Helpdesk-Homelab-Projects/tree/main/Active%20Directory/GroupPolicy) projects. 

3. A new mapped drive was configured by right clicking the Drive Maps location and selecting New > Mapped Drive. The location \\DC\SHARED was provided in the input field as well as the label SHARED and the drive letter S.
4. After the GPO was created, it was linked to the USA > Users OU.
5. The client PC was logged into using a domain user account.
6. File Explorer was opened and in the SHARED folder was present within the Network locations.

note: this will persist even after the computer is rebooted.

## File Server Resource Manager 

This application be used to configure data quotas and thresholds, file screening and file classification management.

### Installation

1. Server Manager was opened and the Add Roles and Features wizard was accessed
2. In the Select Server Roles section, FSRM was selected through File and Storage Services > File and iSCI Servvices > File Server Resource Manager
3. Defaults were selected for the rest of the wizard and the feature was installed.

### Quota Management Configuration

This feature sets a quota for the amount of data available within a folder and also can be used to configure threshold notifications for shared folders.

1. Quota Management was opened within the FSRM.
2. The Create Quote window was opened by right-clicking the Quotas location.
3. A custom quota of 100MB was set and an email alert was configured when the 80% threshold is passed. This was configured by clicking the custom properties button and adding the configurations within the window.

### File Screening Management

This feature controls what file types are allowed on the shared folder.

1. File Screening Management was opened within the FSRM
2. The Create File Screen window was opened by right-clicking the File Screens location.
3. The SHARED folder path was inputted in the location field 
4. A custom file screen was created with the following blocks:
- Audio and Video files
- Executable files
- Image files
- Web Page files

note: different template option can be selected via the dropdown menu instead of creating a custom screen.
 
5. The custom screen was given the name SHARED
6. The file screen was tested by attempting to save a screenshot on the client pc to the SHARED folder 

