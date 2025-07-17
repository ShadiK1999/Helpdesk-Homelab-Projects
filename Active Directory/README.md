# Active Directory

This project demonstrates the setup of a virtual environment containing 2 PCs:

* `Domain Controller` acts as the server which runs Active Directory Domain Service, creates users and groups, and other services that will be discussed in this project.
* `Client 1` acts at the client PC and simulates an employee's workstation

## Network Diagram

![Network Diagram](/Active%20Directory/Screenshots/topoly.png)

## Steps Taken

To complete this project the following steps were taken:
1. Install hypervisor and set up virtual machines:
2. Configure Domain Controller
	- AD DS
	- NAT
	- DHCP
	- Create Users
3. Configure and test network with client PC

## Virtual Machine Setup

1. Install Hypervisor:
 
The hypervisor used for this project was VMWare Workstation Pro. The installation software can be downloaded from Broadcom's website [here](https://www.vmware.com/products/desktop-hypervisor/workstation-and-fusion).

2. Download Windows Server 2019 and Windows 10 ISO files:

ISO files for these versions of windows were downloaded from the Microsoft Evaluation Center via the following links:
- [Windows Server 2019](https://www.microsoft.com/en-us/evalcenter/evaluate-windows-server-2019)
- [Windows 10](https://www.microsoft.com/en-us/evalcenter/evaluate-windows-10-enterprise)

3. Configure hardware for Virtual Machines (additional NIC for windows server VM)

Hardware delegation for each machine was as follows (note the Windows Server Machine has an additional network card to facilitate both internal and external networks):

4. Power up virtual machines:

Each machine was powered up to allow for the windows installation process to take place.

## Domain Controller Configuration

### Setup

1. Change PC name:

The Domain Controller PC was renamed to `Domain Controller` via system settings.

| Rename PC input in system settings.                     |
| ------------------------------------------------------------------------------------- |
| ![](./Screenshots/2%20rename%20PC.png)                 |

2. Rename each NIC:

For easy recognition later in the project, each network card was renamed to reflect the network they represent.
| Before NIC name change .                     | After NIC name change.																			|
| ------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------- |
| ![](./Screenshots/1%20determine%20NIC%20connections%20and%20rename.png)                 |																						|

3. Configure IPv4 for internal network:

The Domain Controller's IPv4 settings were configured to reflect the network diagram.

- IP: 172.16.0.1 /24
- DNS: 127.0.0.1 (loopback address)

| Rename PC input in system settings.                     |
| ------------------------------------------------------------------------------------- |
| ![](./Screenshots/3%20configure%20internal%20ipv4.png)                 |

### Active Directory Domain Service

1. Begin AD DS Install: 

The AD DS installation process was accessed via server manager through the `Add Roles and Features` section.

| Rename PC input in system settings.                     |
| ------------------------------------------------------------------------------------- |
| ![](./Screenshots/4%20install%20ADDS.png)                 |

2. Create the domain:

The domain was created with default FQDN `mydomain.com`. After going through the wizard, the PC was restarted and the new domain was displayed on the login screen.

| Rename PC input in system settings.                     								|Rename PC input in system settings.                   								  |
| ------------------------------------------------------------------------------------- |-------------------------------------------------------------------------------------|
| ![](/Screenshots/5%20adding%20new%20domain.png)                 						|![](/Screenshots/7%20org%20unit.png)                					  |

3. Create an Organisational Unit:

An OU was created with the name `_ADMINS` via the recently installed Active Directory User and Computers. This OU will be populated in the next step. 

| Rename PC input in system settings.                     |
| ------------------------------------------------------------------------------------- |
| ![](/Screenshots/7%20org%20unit.png)                 |

4. Create admin user account:

A new user account was created with the prefix `a-` attached to the username, denoting that it is an admin account. The user was then made a member of `Domain Admins`, listing them in the `_ADMINS` OU.

| Rename PC input in system settings.                     								|Rename PC input in system settings.                   								  |
| ------------------------------------------------------------------------------------- |-------------------------------------------------------------------------------------|
| ![](/Screenshots/8%20new%20admin%20user%20account.png)                 						|![](/Screenshots/10%20make%20admin.png)                					  |

5. login as newly created admin account

The DC was signed out and signed in again using the credentials on the newly created admin account.

| Rename PC input in system settings.                     |
| ------------------------------------------------------------------------------------- |
| ![](/Screenshots/11%20login%20as%20new%20user.png)                 |

### RAS/NAT - allows clients to access the internet through the domain controller

1. Install Remote Access role:

The Remote Access installation process was accessed via server manager through the `Add Roles and Features` section. 

| Rename PC input in system settings.                     |
| ------------------------------------------------------------------------------------- |
| ![](/Screenshots/11%20add%20remote%20access%20role%20for%20NAT.png)                 |

2. Enable NAT:

NAT was enabled through the `Configure and Enable Remote Access` wizard

| Rename PC input in system settings.                     								|Rename PC input in system settings.                   								  |
| ------------------------------------------------------------------------------------- |-------------------------------------------------------------------------------------|
| ![](/Screenshots/12%20configure%20and%20enable%20RA.png)                 				|![](/Screenshots/13%20select%20NAT.png)                					  		  |

3. Select External NIC for NAT

During the enabling process, the internet facing NIC was selected as the internet connection.

| Rename PC input in system settings.                     								|Rename PC input in system settings.                   								  |
| ------------------------------------------------------------------------------------- |-------------------------------------------------------------------------------------|
| ![](/Screenshots/14%20select%20internet%20facing%20nic.png)                 						|![](/Screenshots/15%20successfully%20configured.png)                					  |

### DHCP

1. Install DHCP server via server manager

The DHCP installation process was accessed via server manager through the `Add Roles and Features` section, then opened via the tools menu.

| Rename PC input in system settings.                     |
| ------------------------------------------------------------------------------------- |
| ![](/Screenshots/17%20installed%20dhcp%20role.png)                 |

2. create DHCP Scope

The DHCP scope was configured to reflect the network diagram with a range from `172.16.0.100 - 172.16.0.200 /24`

| Rename PC input in system settings.                     |
| ------------------------------------------------------------------------------------- |
| ![](/Screenshots/18%20create%20scope.png)                 |

3. Configure DHCP options

The DHCP router option was configured to allow users on the client PC's to access the internet.
| Rename PC input in system settings.                     								|Rename PC input in system settings.                   								  |
| ------------------------------------------------------------------------------------- |-------------------------------------------------------------------------------------|
| ![]()                 						|![]()                					  |
### Create Users

1. Download powershell script (Lab use only):

A powershell script was downloaded from this [source](https://github.com/joshmadakor1/AD_PS/blob/master/Generate-Names-Create-Users.ps1). The script creates 1000 user accounts on active directory and adds them to an OU named `_USERS`.



2. Run powershell script:

The script was run within the DC, populated the `USERS` group.


## Client Testing

1. Log into client:

The Client PC was logged into to test the DC configurations.

2. Check client connectivity:

The command prompt was opened to check the following:

- client should have been delegated an IP and gateway from dhcp server
- client should be able to connect to the internet from their PC

| Rename PC input in system settings.                     								|Rename PC input in system settings.                   								  |
| ------------------------------------------------------------------------------------- |-------------------------------------------------------------------------------------|
| ![](/Screenshots/20%20check%20config%20for%20client%20computer.png)                 						|![](/Screenshots/21%20client%20can%20ping%20the%20internet%20.png)                					  |

3. Add Client PC to the Domain:

The client PC was added to the `mydomain.com` domain via the PC system settings. This was verified on the DC through Active Directory Users and Computers. 

| Rename PC input in system settings.                     								|Rename PC input in system settings.                   								  |
| ------------------------------------------------------------------------------------- |-------------------------------------------------------------------------------------|
| ![](/Screenshots/22%20join%20client%201%20to%20domain.png)                 						|![](/Screenshots/24%20AD%20shows%20client%201%20.png)                					  |

4. Log in as random user:

The client PC was signed out and credentials of a random user created from the powershell script was used log back in.

| Rename PC input in system settings.                     								|Rename PC input in system settings.                   								  |
| ------------------------------------------------------------------------------------- |-------------------------------------------------------------------------------------|
| ![](/Screenshots/25%20login%20with%20randomly%20created%20user%20account.png)                 						|![](/Screenshots/26%20confirmed%20random%20user%20login.png)                					  |

