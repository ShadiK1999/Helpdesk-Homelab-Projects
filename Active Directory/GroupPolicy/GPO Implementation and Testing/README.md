# GPO Implementation and Testing

This project tests the Group Policy Objects that were created in the previous lab.

## Systems Used

- Host PC with Hypervisor (VMWare)
- Windows Server 2019 VM (Domain Controller)
- Windows 10 Enterprise Edition VM (Client PC)

## Pre-lab Setup 

1. The host PC was logged into using a user created in a previous lab.
2. The command prompt was used to confirm that the client PC was part of the domain via the `ipconfig` command.

| Confirm PC is part of domain.                     |
| ------------------------------------------------------------------------------------- |
| ![](./Screenshots/0%20confirm%20host%20pc%20config.png)                 |

3. The client PC was moved from the default Computers OU to the USA > Computer OU and given a description (following best practices).

| Moving client PC to USA > Computer OU.                     								| Assign description to client PC.                   								  |
| ------------------------------------------------------------------------------------- |-------------------------------------------------------------------------------------|
| ![](./Screenshots/5%20move%20client%20pc%20to%20USA.png)                 						|![](./Screenshots/6%20give%20pc%20a%20desc.png)                					  |

4. The user account being used on the client PC (mchestnut) was moved to the USA > Users OU.

| Moving user to USA > Users OU.                     |
| ------------------------------------------------------------------------------------- |
| ![](./Screenshots/7%20move%20user%2010%20USA.png)                 |

5. The Group Policy Management Console was opened on the Domain Controller to view the previously creates GPO's.

## GPO Implementation

1. Within the Group Police Management Console, the Restrict Control Panel GPO was moved to the USA > Users OU via drag and drop as it is a user configuration GPO.

| Implementing Restrict Control Panel GPO in the USA > Users OU.                     								|GPO implemented.                   								  |
| ------------------------------------------------------------------------------------- |-------------------------------------------------------------------------------------|
| ![](./Screenshots/2%20restric%20access%20to%20users.png)                 						|![](./Screenshots/3%20gpo%20moved.png)                					  |

2. The same process was utilised to move other previously created GPO's in their respective OU's.

| Remaining GPO's implemented.                     |
| ------------------------------------------------------------------------------------- |
| ![](./Screenshots/4%20move%20rest%20of%20gpos.png)                 |

3. By default there's a 90 minute wait for GPO's to apply, to bypass this the `gpupdate /force` command was used on the client PC. 

| Using `gpupdate /force` command.                     |
| ------------------------------------------------------------------------------------- |
| ![](./Screenshots/8%20gpupdate.png)                 |

## GPO Testing

1. The Restrict Control Panel GPO was tested on the client PC by attempting to open the Control panel
2. The Password Policy GPO was tested by attempting to change the user's password to "password".
3. The Desktop Wallpaper GPO could not be tested as personalisation setting require windows activation and the VM uses an evaluation ISO.
4. The Disable USB Devices GPO was tested by inserting a USB into the host PC and connecting it to the client PC VM.
5. The Drive Mapping GPO could not be tested as there is no real drive connected and a false path was used in the configuration of the GPO purely as an example.