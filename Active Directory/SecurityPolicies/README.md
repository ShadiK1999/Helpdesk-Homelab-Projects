# Implementing Security Policies

## Configure Account Lockout Policy

1. The Group Policy Management Console was opened

|                  								|
| ----------------------------------------------|
| ![](./Screenshots/1%20gpmc.png)                 						|

2. A new GPO was created and its editor window was opened (for more in-depth steps on GPO creation click [here](https://github.com/ShadiK1999/Helpdesk-Homelab-Projects/tree/main/Active%20Directory/GroupPolicy/GPO%20Creation)).

|                  								|
| ----------------------------------------------|
| ![](./Screenshots/2%20gpm%20editor.png)                 						|

3. The Account Lockout configurations were accessed via Computer Configuration > Policies > Windows Settings > Security Settings > Account Policies > Account Lockout Policy

|                  								|
| ----------------------------------------------|
| ![](./Screenshots/3%20account%20lockout%20settings.png)                 						|

4. The following configurations were added: 
- Account lockout duration - 30 minutes
- Account lockout threshold - 3 attempts
- Lockout counter reset - 30 minutes

|                  								|              						      |                                         |
| ----------------------------------------------|-----------------------------------------|-----------------------------------------|
| ![](./Screenshots/4%20lockout%20duration.png)                 						|![](./Screenshots/5%20lockou%20Threshold.png)                					  |![](./Screenshots/6%20lockout%20counter%20reset.png)                                    |

5. The Account Lockout GPO was linked to the USA > Computer GPO

|                  								|
| ----------------------------------------------|
| ![](./Screenshots/7%20linking%20gpo.png)                 						|

6. This GPO was tested by attempting to log into a client PC with the incorrect password

|                  								|              						      |
| ----------------------------------------------|-----------------------------------------|
| ![](./Screenshots/8%20login%20attempt.png)                 						|![](./Screenshots/9%20account%20locked%20out.png)                					  |

## Assigning User Rights
This section limits user access to remote desktop and local log on to the Domain Controller.

1. The Group Policy Management Console was opened and the User Rights GPO was created.

|                  								|
| ----------------------------------------------|
| ![](./Screenshots/11%20new%20gpo.png)                 						|

2. In the editor window, the User Rights configurations were accessed via Computer Configuration > Policies > Windows Settings > Security Settings > Local Policies > User Rights Assignment.
3. The following configurations were made:
    1. USA HR group was denied log on locally.
		- Deny log on locally properties were opened.
		- USA HR group was selected.
	2. USA IT group was granted remote desktop log on rights.
		- Allow log on through remote desktop properties were opened.
		- USA IT group was added.

|                  								|              						      |
| ----------------------------------------------|-----------------------------------------|
| ![](./Screenshots/12%20deny%20hr%20local%20log%20on.png)                 						|![](./Screenshots/13%20allow%20IT%20to%20use%20remote%20desktop.png)                					  |

4. The local log on policy was tested by attempting to log onto the server locally as a HR user

|                  								|              						      |
| ----------------------------------------------|-----------------------------------------|
| ![](./Screenshots/15%20attempt%20local%20log%20on.png)                 						|![](./Screenshots/16%20local%20log%20on%20denied.png)                					  |

5. The remote desktop policy was tested by attempting to use the tool as a regular user. 

|                  								|
| ----------------------------------------------|
| ![](./Screenshots/14%20remote%20desktop%20test%201.png)                 						|


## Implementing Fine-Grained Password Policies
This section applies different password policies for specific security groups.

1. Active Directory Administrative Center was opened.

|                  								|
| ----------------------------------------------|
| ![](./Screenshots/17%20ADAC.png)                 						|

2. The password settings container was accessed via mydomain > System > Password Settings Container.
3. A new Password Settings Object (PSO) was created by selecting New > Password Settings.

|                  								|
| ----------------------------------------------|
| ![](./Screenshots/18%20new%20pso.png)                 						|

4. the following PSO was created:
- Name: ITPasswordPolicy
- Precedence: 2
- Enforce min password: 15
- Enforce password history: 3
- All other settings remain with defaults.

|                  								|
| ----------------------------------------------|
| ![](./Screenshots/19%20IT%20PSO.png)                 						|

