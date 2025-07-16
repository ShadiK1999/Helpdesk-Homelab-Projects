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
3. Configure and test network with client PC

## Virtual Machine Setup

1. Install Hypervisor:
 
The hypervisor used for this project was VMWare Workstation Pro. The installation software can be downloaded from Broadcom's website [here](https://www.vmware.com/products/desktop-hypervisor/workstation-and-fusion).

2. Download Windows Server 2019 and Windows 10 ISO files:

ISO files for these versions of windows were downloaded from the Microsoft Evaluation Center.
- [Windows Server 2019](https://www.microsoft.com/en-us/evalcenter/evaluate-windows-server-2019)
- [Windows 10](https://www.microsoft.com/en-us/evalcenter/evaluate-windows-10-enterprise)

3. Configure hardware for Virtual Machines (additional NIC for windows server VM)

Hardware delegation for each machine was as follows (note the Windows Server Machine has an additional network card to facilitate both internal and external networks):

4. Power up virtual machines:

Each machine was powered up to allow for the windows installation process to take place.

## Domain Controller Configuration
  ### Setup
	1. Change PC name to DC
	2. Rename each NIC to distinguish them (Internet facing and internal network facing)
	3. configure IPv4 for internal network
  
  ### Active Directory Domain Service
	1. install AD DS via server manager
	2. Create domain 
	3. create dedicated domain admin account
	4. Create _ADMINS organisational unit and add new account to it
	5. login as newly created admin account
  
  ### RAS/NAT - allows clients to access the internet through the domain controller
	1. Install Remote Access role via server manager
	2. Open routing and remote access tool
	3. Enable NAT from the configure and enable remote access wizard
	4. select the internet facing NIC as the internet connection

  ### DHCP
	1. Install DHCP server via server manager
	2. create DHCP Scope
	3. Configure DHCP options

  ### Create Users
	1. download powershell script

## Client Testing
	1. Login to client
	2. Open terminal and check connection with ipconfig
		a. client should have been delegated an IP and gateway from dhcp server
		b. client should be able to connect to the internet from their PC
	3. login as a randomly created user to test user login