# Implementing Security Policies

## Configure Account Lockout Policy

1. The Group Policy Management Console was opened
2.A new GPO was created and its editor window was opened (for more in-depth steps on GPO creation click [here](https://github.com/ShadiK1999/Helpdesk-Homelab-Projects/tree/main/Active%20Directory/GroupPolicy/GPO%20Creation).
3. The Account Lockout configurations were accessed via Computer Configuration > Policies > Windows Settings > Security Settings > Account Policies > Account Lockout Policy
4. The following configurations were added: 
- Account lockout duration - 30 minutes
- Account lockout threshold - 3 attempts
- Lockout counter reset - 30 minutes
5. The Account Lockout GPO was linked to the USA > Computer GPO
6. This GPO was tested by attempting to log into a client PC with the incorrect password

## Assigning User Rights
This section limits user access to remote desktop and local log on to the Domain Controller.


1. The Group Policy Management Console was opened
2. The User Rights configurations were accessed via Computer Configuration > Policies > Windows Settings > Security Settings > Local Policies > User Rights Assignment.
3. The following configurations were made:
	1. USA HR group was denied log on locally.
		- Deny log on locally properties were opened.
		- USA HR group was selected.
	2. USA IT group was granted remote desktop log on rights.
		- Allow log on through remote desktop properties were opened.
		- USA IT group was added.
4. The local log on policy was tested by attempting to log onto the server locally as a HR user
5. The remote desktop policy was tested by attempting to use the tool as a regular user. 

##Implementing Fine-Grained Password Policies
This section applies different password policies for specific security groups.

1. Active Directory Administrative Center was opened.
2. The password settings container was accessed via mydomain > System > Password Settings Container.
3. A new Password Settings Object (PSO) was created by selecting New > Password Settings.
4. the following PSO was created:
- Name: ITPasswordPolicy
- Precedence: 2
- Enforce min password: 15
- Enforce password history: 3
- All other settings remain with defaults.