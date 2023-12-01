## Contact Center > Online Contact > Service Guide (Issue) > Global Management
**Global Management** menu in Issue Management service consists of Contract Service Status, Organization Administrator, Authority Log Management and Data Transfer menu.

## Contract service status
### Contract status
![](http://static.toastoven.net/prod_contact_center/2.1.1-(1)_im_en.png)
Through **Contract status** tab, you can **①** add service to organization using Online Contact, **②** edit basic information/contents of contract, **③** set service usage state, **④** terminate service.

![](http://static.toastoven.net/prod_contact_center/2.1.1-(2)_im_en.png)
Click **① Add Service** button to view **② Add Service screen** for entering basic information for the service. The following items require input:

- **Type**: Type of service to use(Consultation management, Issue management)
- **Service Name**: Name of service to be used
- **Service ID**: ID used to identify the service(becomes included in URL of the service’s Online Contact, and help center). English only
- **Time zone**: Time zone set in the help center(selected accordingly when help center language becomes selected. Can be modified separately)
- **Service Banner**: Can attach image. When uploaded, it becomes applied as the image of the service tab in Online Contact GNB and as a profile photo of the agent when chat consulting.

After entering all the basic information, press the next button to go to **③ Contract Details**. On the Contract Details screen, you can **activate functions** from the consultation functions provided by Online Contact for your service and calculate **Estimated Cost** that reflect your choice. After completing the contract details, press **Contract** button to complete the contract.

![](http://static.toastoven.net/prod_contact_center/2.1.1-(3)_im_en.png)
If you leave without going through all the steps of entering basic information and contract details when adding service, the status of service will be displayed **inactivated**, and the steps that were not progressed will be indicated by the button **Enrollment**. For services which contract steps are completed, you can edit basic and contract information through the **① Edit** button, activate or inactivate service through **② State** button, and terminate service through **③ Terminate** button. Please note that terminate button becomes active only when the status of the service is **inactivated**.

### Rate status
![](http://static.toastoven.net/prod_contact_center/2.1.1-(4)_im_en.png)
**Rate status** tab allows you to view monthly charges by type, individual service, and total through **① Search** button. **② Service status** will be displayed together if charges are set to be viewed based on individual services.

✔ **\[FAQ]** [I want to know about the charge criteria.](https://nhn-contact.oc.toast.com/oceng/hc/article/148/)
✔ **\[FAQ]** [When and how will the charge be paid?](https://nhn-contact.oc.toast.com/oceng/hc/article/147/)

### Organization Information
![](http://static.toastoven.net/prod_contact_center/2.1.1-(5)_im_en.png)
In **Organization Information** tab, **① NHN Cloud Organization Information**, **② OC Organization Information** is available.

#### NHN Cloud Organization Information
In the menu, users can check the information written below, and the same information could be checked and modified in **NHN Cloud Console → Organization Management → Default Organization Setting** tab.

- **NHN Cloud Organization Name**: The name set when the organization was created.
- **NHN Cloud Organization ID**: Unique ID given to each organization when the organization was created. Used to create authentication token required when using Open API.
- **NHN Cloud Organization Domain**: The name set when selecting a service after creating an organization.

#### OC Organization Information
In the menu, users can check the information written below. OC Organization Key could be changed by **Change API Key** button, and OC URL changes together when changing the NHN Cloud Organization Domain.

- **OC Organization Key**: Key used in the authentication phase when trying to process actions performed for organizational management through API.
- **OC URL**: The access URL for Online Contact. Created in the following form: https://**Organization Domain**.oc.toast.com

## Organization Adminstrator
![](http://static.toastoven.net/prod_contact_center/2.1.2-(1)_im_en.png)
**Organization Administrator** has access to functions related to managing organization, agents, and organization administrators.
Since consulting and service management functions are not available only by the organization administrator authority, getting **administrator** or **agent** authority from [Service Management → Agent] menu is needed to consult, or set service.
The user whom you want to grant permission must be registered as an IAM member.

✔ **\[FAQ]** [Types and difference between permissions](https://nhn-contact.oc.toast.com/oceng/hc/article/119/)

### Register as an IAM Member

- Click **① Invite Members** button → Enter name, ID, email
- NHN Cloud CONSOLE → Manage Member → IAM Member tab → Click **Register IAM Member** button → Enter ID, name, mail, and mobile phone number

Select one of the above two methods to register IAM member. After registering, click **② Add Organization Administrator** → click **View Agent** → Search registered IAM Member by entering name/account/email, and add IAM Member as organization administrator.
To newly registered IAM Members, **password change mail** will be sent to the registered email. Logging in Online Contact becomes available after setting password through email.

## Authority Log Management
![](http://static.toastoven.net/prod_contact_center/2.1.4-(1)_im_en.png)
**① Logs are recorded** when you change the permissions of agents inside the organization. This menu manages logs about change of permission by the organization administrator or administrator. You can **② search** by entering some of the information, including the date and time of operation, operated contents, name, IP, service, or ID.

## Data Transfer
![](http://static.toastoven.net/prod_contact_center/2.1.6-(2)_en.png)

If consultation data should be transferred to Online Contact, you could upload data and create tickets through **Data Transfer** menu.

If you click **① Add** button, you can access to the screen for **downloading transfer template**. Select the service you want to transfer consultation data, and click **② Download** to download the transfer template of the service. The field configuration set for the service is reflected in the downloaded template, thus re-download of the template is needed when the field configuration had changes.

After downloading the template, click **Next** button to access **Register Data** screen.
You can upload the file you created by clicking **③ Add** button, and after checking the service and file name once more, click **④ Confirm** button to complete data registration.

You can **delete** the reserved transfer cases before the transfer is processed, and if the transfer is completed, delete button will be deactivated.

## My Performance
![](http://static.toastoven.net/prod_contact_center/2.1.4-(2)_im_en.png)
Through clicking **① account name** displayed in the upper right corner of the screen, you could access to **② My Performance** menu.
In this menu, detailed **real-time cumulative data** about ticket, call, chat consultation in **currently accessed service** is shown.

Detailed performance classifications for different types of consultations are as follows:

**③ Ticket Achievements**

- New
- Open
- Solved
- Closed

**④ Call Achievements**

- IB Call(number of calls/minute)
- OB Call(number of calls/minute)
- Ready
- Transfer
- Ticket Treatment
- Chat Treatment
- Rest
- Eat
- Education
- Report
- Meeting
- Monitor

**⑤ Chat Achievements**

- Ready
- Online
- Rest

## Privacy Settings
![](http://static.toastoven.net/prod_contact_center/2.1.5-(1)_im_en.png)
Through clicking **① account name** displayed in the upper right corner of the screen, **② privacy settings** menu is showed. User’s personal settings could be accessed and edited through this menu.

✔ **\[FAQ]** [How can I change or delete my ID, email, and name?](https://nhn-contact.oc.toast.com/oceng/hc/article/106/)
✔ **\[FAQ]** [How can I change my password?](https://nhn-contact.oc.toast.com/oceng/hc/article/108/)

### Accessible Information

- Account
- Name
- Nickname(Editable): Displayed when communicating through chat, mail
- Phone number
- Email
- Language(Editable): Language in your environment, apart from service’s language setting
- Assign ticket(Editable): If consulting is not available due to vacation, etc., can set ticket allocation status
