# GPO Implementation and Testing

## Systems Used

- Host PC with Hypervisor (VMWare)
- Windows Server 2019 VM (Domain Controller)
- Windows 10 Enterprise Edition VM (Client PC)

## Pre-lab Setup 

1. The host PC was logged into using a random user created in a previous lab.
2. AD Users and Computers was double checked on the DC to confirm that the client PC was part of the domain.
3. The client PC was moved from default Computers OU to the USA > Computer OU and given a description (following best practices).
4. The user account being used on the client PC (mchestnut) was moved to the USA > Users OU. 
5. The Group Policy Management Console was opened on the Domain Controller to view the previously creates GPO's.

## GPO Implementation

1. Within the Group Police Management Console, the Restrict Control Panel GPO was moved to the USA > Users OU via drag and drop as it is a user configuration GPO.
2. The same process was utilised to move other previously created GPO's in their respective OU's.
3. By default there's a 90 minute wait for GPO's to apply, to bypass this the gpupdate /force command was used on the client PC. 

## GPO Testing

1. The Restrict Control Panel GPO was tested on the client PC by attempting to open the Control panel
2. The Password Policy GPO was tested by attempting to change the user's password to "password".
3. The Desktop Wallpaper GPO could not be tested as personalisation setting require windows activation and the VM uses an evaluation ISO.
4. The Disable USB Devices GPO was tested by inserting a USB into the host PC and connecting it to the client PC VM.
5. The Drive Mapping GPO could not be tested as there is no real drive connected and a false path was used in the configuration of the GPO purely as an example.