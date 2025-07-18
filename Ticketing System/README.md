# Ticketing System Labs

This project demonstrates the use of best practices when addressing tickets via the online ticketing system, Spiceworks.

## What's Covered

1. Spiceworks Setup
2. Ticket Creation
3. Ticket Closure Checklist
4. Ticket Escalation

## Spiceworks Setup

1. Account creation: 

The [Spiceworks website](https://www.spiceworks.com) was openned and inital signup and registration was completed.

| Spiceworks sign up page.                     								|Account registration page.                   								  |
| ------------------------------------------------------------------------------------- |-------------------------------------------------------------------------------------|
| ![](./Screenshots/1%20login.png)                 						|![](./Screenshots/2%20registration.png)                					  |

2. Open the help desk:

Navigated to `Cloud Help Desk` via the `IT Tools` dropdown menu and completed the help desk setup form.

| Selecting `Cloud Help Desk` from dropdown menu.                     								|Cloud Help Desk setup page.                   								  |
| ------------------------------------------------------------------------------------- |-------------------------------------------------------------------------------------|
| ![](./Screenshots/3%20cloud%20help%20desk.png)                 						|![](./Screenshots/4%20help%20desk%20setup.png)                					  |

3. Open the ticketing system:

Once the setup form was completed, the help desk ticketing system was opened.

| Cloud Help Desk ticketing system.                     |
| ------------------------------------------------------------------------------------- |
| ![](./Screenshots/5%20initial%20helpdesk%20screen'.png)                 |

## Ticket Creation

The goal of this task is to understand how tickets are created and catagorised.

1. Begin ticket creation process:

Navigated to the `Create Ticket` button and clicked, opening the ticket creation form.

| Selecting the `Create Ticket` button.                     |
| ------------------------------------------------------------------------------------- |
| ![](./Screenshots/6%20new%20ticket.png)                 |

2. Fill in the ticket information:

The ticket was filled with the following considerations:
- What device is having the issue.
- Being as descriptive as possible on the issue.
    - What programs/apps/hardware isn't working.
    - Any steps taken in an attempt to correct the issue.
    - When can the technician get ahold of the issuer.
    - How to reach the issuer if email isn't the best option.

| Ticket pre-fill.                     								|Ticket post-fill.                   								  |
| ------------------------------------------------------------------------------------- |-------------------------------------------------------------------------------------|
| ![](./Screenshots/7%20empty%20ticket.png)                 						|![](./Screenshots/8%20filled%20ticket.png)                					  |

Note: the ticket was listed as high priority as the monitor issue was impacting the user's workflow. 

3. Post the ticket:

The `Create` button was pressed and the newly created ticket was displayed on the help desk dashboard.

| Ticket created and displayed.                     |
| ------------------------------------------------------------------------------------- |
| ![](./Screenshots/9%20ticket%20created.png)                 |

## Ticket Closure Checklist

The goal of this task is to ensure that the ticket is properly resolved and documented.

For this example, it is assumed that the issue has been resolved and all that is left is to verify with the user and close the ticket.

| Ticket to be closed.                     |
| ------------------------------------------------------------------------------------- |
| ![](./Screenshots/10%20ticket%20to%20be%20resolved.png)                 |

1. Verify with user:

Once the issue was resolved on the backend, a message was sent to confirm with the user.

| Message to the user.                     |
| ------------------------------------------------------------------------------------- |
| ![](./Screenshots/11%20message%20to%20user.png)                 |

2. Document resolved issue with internal notes:

Once confirmation was received from the user, the message type was changed to an internal not via dropdown menu.

The internal note was used to document the steps taken to fix issue in case other technicians have similar tickets to resolve.

| Message type dropdown menu.                     								|Sent internal note.                   								  |
| ------------------------------------------------------------------------------------- |-------------------------------------------------------------------------------------|
| ![](./Screenshots/12%20change%20to%20internal%20note.png)                 						|![](./Screenshots/13%20post%20internal%20note.png)                					  |

3. Close the ticket:

The ticket was closed by pressing the `Close` button on the right hand side of the display.

| The `Close` button.                     |
| ------------------------------------------------------------------------------------- |
| ![](./Screenshots/Screenshot%202025-07-18%20at%204.33.23 pm.png)                 |

## Ticket Escalation

The goal of this task is to understand when and how to escalate a ticket.

Scenario: A user can't access the financial database. An attempt to reset credentials was made as well as basic network checks.
Issue: The technician is not part of the correct team so assign these credentials to the user and resolve the ticket.

1. See if software has an `Escalate` option:

It was found that Spiceworks does not offer escalate functionality, so the ticket must be reassigned manually.

| Spiceworks ticket options - no escalate option.                     |
| ------------------------------------------------------------------------------------- |
| ![](./Screenshots/14%20check%20for%20escalate.png)                 |

2. Assign ticket to member of relevant team:

Ticket was reassigned to the a different team by inputting their email in the `Assignee` input field.

| Ticket reassignment.                     |
| ------------------------------------------------------------------------------------- |
| ![](./Screenshots/15%20reassign%20ticket.png)                 |

3. Send message to  newly assigned ticket recipient:

A message was sent within the ticket to notify both the user and the newly assigned team member that the ticket has been escalated. 

| Escalation message sent within ticket messaging section.                     |
| ------------------------------------------------------------------------------------- |
| ![](./Screenshots/16%20message%20sent%20to%20team%20member.png)                 |

