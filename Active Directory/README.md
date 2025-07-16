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

2. Rename each NIC:

For easy recognition later in the project, each network card was renamed to reflect the network they represent.

3. Configure IPv4 for internal network:

The Domain Controller's IPv4 settings were configured to reflect the network diagram.

- IP: 172.16.0.1 /24
- DNS: 127.0.0.1 (loopback address)

### Active Directory Domain Service

1. Begin AD DS Install: 

The AD DS installation process was accessed via server manager through the `Add Roles and Features` section. 

2. Create the domain:

The domain was created with default FQDN `mydomain.com`. After going through the wizard, the PC was restarted and the new domain was displayed on the login screen.

3. Create an Organisational Unit:

An OU was created with the name `_ADMINS` via the recently installed Active Directory User and Computers. This OU will be populated in the next step. 

4. Create admin user account:

A new user account was created with the prefix `a-` attached to the username, denoting that it is an admin account. The user was then made a member of `Domain Admins`, listing them in the `_ADMINS` OU.

5. login as newly created admin account

The DC was signed out and signed in again using the credentials on the newly created admin account.

### RAS/NAT - allows clients to access the internet through the domain controller

1. Install Remote Access role:

The Remote Access installation process was accessed via server manager through the `Add Roles and Features` section. 

2. Enable NAT:

NAT was enabled through the `Configure and Enable Remote Access` wizard

3. Select External NIC for NAT

During the enabling process, the internet facing NIC was selected as the internet connection.

### DHCP

1. Install DHCP server via server manager

The DHCP installation process was accessed via server manager through the `Add Roles and Features` section, then opened via the tools menu.

2. create DHCP Scope

The DHCP scope was configured to reflect the network diagram with a range from `172.16.0.100 - 172.16.0.200 /24`

3. Configure DHCP options

The DHCP router option was configured to allow users on the client PC's to access the internet.

### Create Users

1. Download powershell script (Lab use only):

A powershell script was downloaded from this [source](https://github.com/joshmadakor1/AD_PS/blob/master/Generate-Names-Create-Users.ps1). The script creates 1000 user accounts on active directory.

2. Run powershell script:

The script was run within the DC, populated the `USERS` group.


## Client Testing

1. Login to client
2. Open terminal and check connection with ipconfig
	- client should have been delegated an IP and gateway from dhcp server
	- client should be able to connect to the internet from their PC
3. login as a randomly created user to test user login