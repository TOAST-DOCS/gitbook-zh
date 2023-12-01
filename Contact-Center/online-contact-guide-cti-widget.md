## Contact Center > Online Contact > Service Guide (Consultation) > Ticket Management (Call)

### Call Consultation
When call function is activated, **call icon** is displayed to the call authorized agent. CTI screen will be displayed in the upper right side of Online Contact if call icon is clicked.

#### CTI Login, Base Status
![](http://static.toastoven.net/prod_contact_center/2.2.3-(10)_en.png)
Agent which CTI information is registered in Global Management → CTI Management → CTI Agent Management menu could login to the CTI through **① Login** button. After login is completed, the CTI screen is changed to **② default screen**, and the following functions are able to use.

- Logout
- Rest: Set agent status to rest, call request not allocated in this status.
- Ready: Set Agent status to ready, call request allocated when inbound call exists.
- Business: Can choose between Education, Report, Meeting, Ticket, Chat, Monitor. Call request not allocated in this status.
- Dial up: Can make outbound call after setting customer number, calling number. (Can set in Service Management → Call → Send No Management menu)

✔ **\[FAQ]** [I have problems with CTI login.](https://nhn-contact.oc.toast.com/oceng/hc/article/152/)

#### Inbound Call
![](http://static.toastoven.net/prod_contact_center/2.2.3-(11)_en.png)
If call is requested when agent status is set to ready, **① alert about inbound call** which notifies if call consultation is connected, current screen will be changed to the ticket processing screen of the service which call is requested is displayed.

Call would be connected by clicking **② Confirm** button, and ticket would be automatically created to the service which call is requested. When cancel button is clicked, the call goes back to the scenario to navigate agents in ready status, and if the agent status is changed to 'ready' again, the agent would be able to receive call again.

#### Outbound Call
![](http://static.toastoven.net/prod_contact_center/2.2.3-(12)_en.png)
When clicking **① Dial up** button in the CTI screen, screen for **② dial up** will be displayed.
After entering **customer number**, and selecting **sending number**, click **③ confirm** to make outbound call.
When calling is proceeded, the agent status would be changed to **Dialing**, and when call is connected, ticket would be automatically created to the service which call is made.

#### Process Call
![](http://static.toastoven.net/prod_contact_center/2.2.3-(13)_en.png)
In **Talking** status, you can use the following functions through the CTI screen.

- Transfer: You can **transfer** the currently connected call to other agent. After entering agent number or searching agent, you can discuss with the other agent through **transfer try** button, and can transfer the call through **transfer connect** button. 
- Disconnect: In the case of a situation where **normal consultation is difficult to take place due to the customer's strong attitude**, click disconnect to finish call with an ARS announcement.
- Hold: If you need a moment of confirmation or inquiry while consulting, select Hold. **Music will be transmissed** to the customer, and agent status will be changed to **holding**. Click **retrieve** to reconnect call.
- Hang up: Call will be finished.

#### Finish Call
![](http://static.toastoven.net/prod_contact_center/2.2.3-(14)_en.png)
When call is finished, **alert about change of agent status** will be displayed, and if **① Confirm** button is clicked, agent status will be changed to **ready**.

If **② Cancel** is selected, status will be changed to **Ticket**, and you could process ticket created for the proceeded call consultation. For call tickets, you could process through selecting the following items: **Resolved**, **Pending**, **Add a Comment**.
