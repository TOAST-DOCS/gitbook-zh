## Contact Center > Online Contact > Service Guide (Issue) > Ticket Management

## Ticket
Escalated tickets could be assigned to groups or agents by trigger conditions(Can set in Service Management → Ticket → Trigger menu), or could be manually assigned.
Tickets can be **escalated** from consultation management service, or **created** by the agent of issue management service. 
Colors given to each inflow channel can be used to classify tickets.

## Ticket Processing
![](http://static.toastoven.net/prod_contact_center/4.1.1-(1)_im_en.png)
From **① All Tickets** Menu, you could check the **overall situation of tickets** regardless of status or agent in charge. And from other **detailed menus**, you could check the current situation of tickets categorized by **detailed conditions** such as group or ticket status.

Information which you could check by each **detailed menu** is as follows:

- **③ All Tickets in Group**: You can view the **entire ticket within the group** you belong to.
- **④ My Tickets in Progress**: When a ticket is assigned to an agent, the status changes to **processing**. In this menu, you can view tickets assigned to you.
- **⑤ My Tickets in Pending**: If a ticket needs to be additionally checked, the agent can set the ticket status to **pending**. In this menu, you can view tickets which you processed as ‘pending’.
- **⑥ My Resolved Tickets**: If an agent process a ticket as ‘**resolved**’, the status of the ticket changes to ‘resolved’ and could be viewed at this menu. If the customer resubmits inquiries to the answer mail, the ticket could be processed again.
- **⑦ My Completed Tickets**: A ticket becomes ‘**completed**’ if the administrator processes the ticket to be ‘**completed**’, or if **two weeks has been past** after the ticket was resolved. Completed tickets cannot be processed.

### Keep Tickets
![](http://static.toastoven.net/prod_contact_center/4.1.2-(1)_im_en.png)
Agents could assign **unassigned** tickets to oneself through ‘**keep**’ button. Click **① Keep** button, and select agent group if you belong to more than one group.

If ticket assign is set through trigger, tickets could be assigned according to the trigger conditions. In this case, to change automatically assigned agents, **administrator** of the service could **forward** the ticket to another agent. Click **② Forward** button, and select agent/group.

### Process Tickets
If a escalated/created ticket is assigned, the status of the ticket changes to ‘**processing**’. Customer inquiries could be processed in this state.
You could utilize **Ticket Information**, **Ticket History**, **Event** tabs when processing a ticket.

![](http://static.toastoven.net/prod_contact_center/4.1.2-(2)_im_1_en.png)

-	**① Ticket Information**: Information related to the escalated ticket
      - Ticket ID
      - Group/Agent
      - Status
      - Channel
      - Escalation-related information
      - Submission type, customer/agent field
      - Consultation processing history

![](http://static.toastoven.net/prod_contact_center/4.1.2-(3)_im_en.png)

-	**① Ticket History**: Details of the customer's previous escalated inquiries

![](http://static.toastoven.net/prod_contact_center/4.1.2-(4)_im_en.png)

-	**① Event**: Occurred events of the ticket (Ticket assign, Change of agent, etc.)

![](http://static.toastoven.net/prod_contact_center/4.1.2.-(5)_im_1_en.png)
After filling in the contents, you can pre-check whether the banned word is included, and the final reply mail including the mail layout through **① ticket preview**.
Tickets could be **② processed** as follows. When a ticket is **resolved** or **pended**, the status of the ticket in counsultation management service changes to **Escalation resolved**. 

- **Resolved**: Tickets could be resolved to send a **final answer mail** to the customer.
- **Pending**: Tickets could be pended to send a **intermediate reply** before the final reply.
- **Add a Comment**: **Comments** could be added to the ticket. 
- **Resolve Internally**: Tickets could be resolved internally when the ticket **does not need to be replied**.
    - Resolved via Chat: Inquiry resolved through chat
    - Resolved via Call: Inquiry resolved through call
    - Others

**③ Ticket Batching** function could be used when similar inquiries need to be answered at once, or when agents/groups of tickets should be changed together.

✔ **\[FAQ]** [How can I use answer templates?](https://nhn-contact.oc.toast.com/oceng/hc/article/122/)
✔ **\[FAQ]** [Can I process tickets with the same inquiry all at once?](https://nhn-contact.oc.toast.com/oceng/hc/article/121/)

### Create Tickets
![](http://static.toastoven.net/prod_contact_center/4.1.2-(6)_im_en.png)
You could create new tickets through **① Create Ticket** button. Tickets could be created when additional tickets are needed in the process of handling customer inquiries.
The following items are required to enter when creating a ticket:

- **②** Group
- **③** Agent
- **④** Submission Type
- **⑤** Title, **⑥** Contents

### Personal Data Masking
If **Security Service** function is **activated** in the contract details, **Masking Personal Information** button is showed in the ticket management page.
Through this function, the personal information of the customer could be encrypted.

![](http://static.toastoven.net/prod_contact_center/masking_1.gif)
The areas where you can mask personal information when managing tickets are **customer inquiries** and **replies from agents**.
**Drag** to select the area which needs masking, and click **Masking Personal Information** button. The personal information inside the page will be substituted with asterisks (\*). The masked data is stored in the masked state on the database.

![](http://static.toastoven.net/prod_contact_center/masking_2.gif)
To **remove** data masking, **click the substituted area**. A pop-up page asking whether to remove data masking will be showed. 
Click **confirm** to remove data masking on the page and database.

## Search Tickets
![](http://static.toastoven.net/prod_contact_center/4.1.3-(1)_1_im_en.png)
If you click the **① Search Ticket** button in top of the ticket list, conditions of searching tickets will be displayed. The conditions are as follows.

- **Created Time**
- **Priority**
- **Ticket ID**
- **Title**
- **Group/Agent**
- **Status**
- **Channel**
- **Submission Type**
- **Processing Type**
- **Name**
- **ID**
- **Email**
- **Phone**
