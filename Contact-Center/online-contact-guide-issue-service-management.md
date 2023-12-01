## Contact Center > Online Contact > Service Guide (Issue) > Service Management

Service Management menu in Issue Management service includes **detailed setting functions for accepting and processing escalated inquiries** including ticket, agent, external channel.

## Ticket
From the Ticket menu, you can **manage categories and fields** which are used when processing inquiries, **use trigger features** that can improve business efficiency, **manage templates**, and **set up email**.

### Manage Category
In Issue Management service, ticket categories are used as below :

- Submission Type: Categories which agents of Consultation Management service selects when escalating tickets
- Processing Type: Categories which agents of Issue Management service selects when processing escalated tickets

#### Submission Type
![](http://static.toastoven.net/prod_contact_center/2.2.3-(1)-1_im_en.png)
**①** When adding lower level categories, please click the upper level category first and check whether it is properly selected. Categories will be created below the highlighted category. **Duplicate** category names are not allowed within the same depth.

**②** If you click the created category, **delete** button will appear. You can **edit category names** by double clicking the category.
**③** You could copy **Category ID** through **Copy** button, and **download overall category information** into excel format through **Download** button.

#### Processing Type
![](http://static.toastoven.net/prod_contact_center/2.2.3-(1)-2_im_en.png)
**①** When adding lower level categories, please click the upper level category first and check whether it is properly selected. Categories will be created below the highlighted category. **Duplicate** category names are not allowed within the same depth. **②** You could modify or delete categories through **Edit**, **Delete** button.

**③** You could copy **Category ID** through **Copy** button, and **download overall category information** into excel format through **Download** button.

### Trigger
![](http://static.toastoven.net/prod_contact_center/2.2.3-(2)_im_en.png)
Triggers are designed to increase task productivity by **automating** repetitive tasks. By using triggers, resulting behaviors are automatically executed when certain conditions are met. You can also set up notification mails to be sent for results.

Example) If `Submission Type` of the ticket = `Billing`, `Assign` ticket to `test01` agent of `Billing` group `necessarily`

Click the **① Add Trigger** button, enter all the title, conditions, and results, and click the **Save** button to save and activate the trigger. Enabled triggers can be disabled via the **② Disable** button, and conditions or results can be modified via the **③ Edit** button.

✔ **\[FAQ]** [How can I automatically forward the received inquiry?](https://nhn-contact.oc.toast.com/oceng/hc/article/126/)
✔ **\[FAQ]** [Can notification emails be sent under certain conditions?](https://nhn-contact.oc.toast.com/oceng/hc/article/125/)

#### Trigger Condition Types
![](http://static.toastoven.net/prod_contact_center/2.2.3-(2)a_1_im_en.png)

#### Trigger Condition Details
![](http://static.toastoven.net/prod_contact_center/2.2.3-(2)b_1_en.png)

#### Trigger Condition Details
![](http://static.toastoven.net/prod_contact_center/2.2.3-(2)c_1_en.png)

#### Trigger Result Details
##### Ticket : Assign
![](http://static.toastoven.net/prod_contact_center/2.2.3-(2)d_im_en.png)
Select and save the group of agents, the agents to distribute tickets, and the distribution method(random/linear/select agent), and the tickets will be assigned according to the selected results when the trigger conditions are met.

For **random allocation**, tickets are randomly assigned to selected agents, and for **linear allocation**, tickets are assigned in the order in which agents are added to the group.

If there are multiple triggers with different agents on the same condition, tickets will continue to be assigned only to agent set to the last trigger after all triggers have been triggered sequentially, rather than randomly assigned to one of these agents. Therefore, if you want to set the ticket to be assigned randomly within the group, please select **linear allocation**.

##### Notification
![](http://static.toastoven.net/prod_contact_center/2.2.3-(2)e_im_en.png)
Notification is the type of result that **notification mail is sent** to the specified recipient when the trigger condition is met.
After selecting the person to send the notification mail, you can set the title and content of the notification mail through the **① Notification Settings** button. For notification mail sent through triggers, the mail layout set in the Service Management → Ticket → Email Settings menu **is not applied**, and it is sent **alone as you set it** on the notification settings pop-up.

##### Forward
![](http://static.toastoven.net/prod_contact_center/2.2.3-(2)f_en.png)
Forward is the type of result that **ticket information being emailed** to the specified recipient when the trigger condition is met. You can check the information and inquiries of the ticket through the e-mail. If you click the **① Online Contact Shortcut** link at the bottom of the inquiry, **ticket screen would be popped-up**, and you can process the ticket directly on the screen. If you chose to **complete the ticket after forwarding**, the inquiry will be emailed and your ticket will be automatically processed as**completed**.

##### Callback url
Callback url is the type of result that the **entered callback address is called** when the trigger condition is met.

##### Dooray Notification
![](http://static.toastoven.net/prod_contact_center/2.2.3-(2)g_en.png)
If the trigger conditions are met, information of the ticket is sent via Dooray notification based on the template set by the **① Template Settings** button. For the link URL, see [Dooray Messenger Service Guide](https://helpdesk.dooray.com/share/pages/4Ws8UzbnT7KbP9R5fAQBjg/2956645181839458938) for instructions.

### Field
![](http://static.toastoven.net/prod_contact_center/2.2.3-(3)_im_en.png)
Fields are divided into **① Customer Field** and **① Agent Field**. Please select whether you want to manage before selecting field setting or field management.

In Issue Management service, customer and agent fields are used as follows:

- **Agent Field**: Fields which agents of Issue Management service enters when processing escalated tickets
- **Customer Field**: Fields which are entered according to the designated category when a ticket is escalated

#### Field Setting
![](http://static.toastoven.net/prod_contact_center/2.2.3-(4)_im_en.png)
**①** Depending on the submission type you added earlier in Service Management → Ticket → Manage Category menu, you can set the fields required for ticket escalation differently. Click **Submission Type** to view the fields you have set up, and you can change the **②** order of fields except for personal information field. In the case of personal information field, it is always pinned to the bottom.

You can also **③ add** and **④ remove** the fields you previously added on the Field Management menu.

#### Field Management
![](http://static.toastoven.net/prod_contact_center/2.2.3-(5)_im_en.png)
**①** You can manage fields in **Field Management** tab. Settings of **System Fields** could only be **modified** or **initialized**. **User Fields** could be **added**, **modified**, or **deleted**.

### Manage Template
Template managing is a feature that allows you to quickly process tickets by **pre-adding answer templates** for frequently asked questions.

#### Template Registration
![](http://static.toastoven.net/prod_contact_center/2.2.3-(7)_1_im_en.png)
At **Template Registration** tab, you could **add** templates, **② search** templates by setting **① search criteria**, **modify** or **delete** templates.
You could serach templates by title, processing type, search code. In the **③ template list**, information are displayed as follows:

- Title
- Processing Type: Type **connected** to the template
- Search Code: **Code** which can be used when searching templates
- Number of Use: The **number of times** which the template was **selected**

![](http://static.toastoven.net/prod_contact_center/2.2.3-(7)_2_im_en.png)
If you click **① Add Template** button, pop-up screen for setting template will be displayed.

- **② Template Title**
- **③ Contents**: **Replacement code** could be used when writing contents. **Double-click** adds the code to the contents, and data is inserted into code area of the template when processing tickets, making it more convenient to write replies.
- **④ Search Code**: **Code** which can be used when searching templates. (English or number combination within 20 characters)
- **⑤ Template Connection**: You can **select processing types** to connect to the template. **Check** the type you want to move, and press the **arrow** button.

You can insert **links**, **images**, and **tables** into the body when you right-click on the body of the content, and when inserting images, you can use the path of the uploaded image from the Service Management → Help Center → Manage File Uploads menu or by attaching the image directly.

#### Template Connection
![](http://static.toastoven.net/prod_contact_center/2.2.3-(7)_3_im_en.png)
You can **view the templates linked to each processing type**, **add** templates to each processing type, or **delete** added templates.
If you select a processing type from the list, you will see the list of connected templates, and you can add templates through **① Add** button.

✔ **\[FAQ]** [How can I use answer templates?](https://nhn-contact.oc.toast.com/oceng/hc/article/122/)
✔ **\[FAQ]** [I registered answer templates, but they are not shown when processing tickets.](https://nhn-contact.oc.toast.com/oceng/hc/article/143/)

### Email Settings
![](http://static.toastoven.net/prod_contact_center/2.2.3-(8)_im_1_en.png)
In the **Email Settings** menu, you can create a **① representative account address** through the domain provided by Online Contact, and if you have a separate **② external account**, you can register to receive inquiries.
You can set the **③ sender information** to specify the sender name and address of the email sent via Online Contact.

![](http://static.toastoven.net/prod_contact_center/2.2.3-(8)_im_2_en.png)
**④ Mail layout** settings allow you to set a common layout for mail sent during ticket processing by ticket status.
From using **replacement codes**, you can set ticket related information to be automatically entered at the selected location. Among the replacement codes, the answer(#{content}) code must be included in the layout.

✔ **\[FAQ]** [How can I connect my external email to Online Contact?](https://nhn-contact.oc.toast.com/oceng/hc/article/127/)

### Sensitive
![](http://static.toastoven.net/prod_contact_center/2.2.3-(15)_im_en.png)
You can manage sensitive words to prevent errors or incorrect instructions from being included in ticket replies.
If you proceed **ticket preview** or **resolve/pend** tickets while the **① added** sensitive text is included in the content, a **② pop-up** will be displayed indicating that sensitive words are included.

## Agent
In this menu, you can add and edit agents and groups for processing escalated tickets, and set up groups and permissions for each agent.

### Agent
![](http://static.toastoven.net/prod_contact_center/2.2.4-(1)_im_en.png)
User must be registered as **IAM Member** to be added as an agent.

#### Register IAM Member
- Click **① Invite Members** button → Enter name, ID, email
- NHN Cloud CONSOLE → Manage Member → IAM Member tab → Click Register IAM Member button → Enter ID, name, mail, and mobile phone number

Select one of the above two methods to register IAM member., and click **② Add Agent** → **View Agent** → search registered IAM Member by entering name/account/email, and add the member as the service agent.

When adding a agent, assigning group is mandatory. Thus, adding groups should be proceeded before adding agents.

The **permission** of agents is as follows. Setting organization administrator permission is available from [Global Management → Organization Administrator] menu.

- Administrator: Permission which features related to **service setting** added to the permission of **agents**.
- Agent: Permission for **ticket consultation**.

### Group
![](http://static.toastoven.net/prod_contact_center/2.2.4-(2)_im_en.png)
In Group menu, you can **① add**, **② edit**, **③ delete** groups. When configuring agents into groups, you can assign type-specific inquiries to the appropriate group, or set up notification mails.

#### Add Group
![](http://static.toastoven.net/prod_contact_center/2.2.4-(3)_im_en.png)
Click **Add Group**, enter group name, choose agent to be assigned, and click **①** ‘**>** ‘button to move agent to ‘Assigned Agent’. Conversely, when you unassign a agent, click ‘**<**’ button to move agent to ‘Unassigned Agent’. After assigning agents, press **② Save** button to apply group settings. A group can be added without assigning agents.

## External Channel
You can communicate with customers by connecting **external channel** with Online Contact. **SMS** is currently supported in Issue Management service.

### SMS
![](http://static.toastoven.net/prod_contact_center/2.2.6-(6)_im_en.png)
You could send SMS/MMS through linking **[NHN Cloud Notification → SMS]** service with Online Contact.
If **SMS** function is **activated** in Global Management → Contract Service Status → Contract Details, SMS menu tab is shown in Service Management → External Channel menu.

To **① activate** SMS linkage, please **activate [NHN Cloud Notification → SMS] service** first, and **② save** the **APP KEY** which you could find in NHN CLOUD CONSOLE. If you enter and save a valid APP KEY, the SMS function is automatically **activated**, and **sending number** list is displayed.

If you click **③ Add** button, pop-up screen for **selecting sending number** will be shown. The numbers which are registered in NHN Cloud Notification → SMS service are shown in the kist, thus please check if there are registered sending numbers before adding in Online Contact. Check the number you want to add, and click confirm button to add the number to the sending number list. The added numbers could be used as **sending number** when sending SMS/MMS in Online Contact.

After activating SMS service and adding sending number, you could proceed to sending/managing SMS in **Additional Business Management → SMS Send** menu.

## Security Management
![](http://static.toastoven.net/prod_contact_center/2.2.6-(5)_en.png)
If you have enabled the Service Management → Security Service feature in the contract information through prior consultation, you can activate **log linkage**, and use **personal information masking** function for encrypting personal information transmitted during and ticket consultation.  

**Personal information masking** function can be used in ticket management menu without further settings if **Security Service** function is **activated**, and **log linkage** function can be used after activating in Security management menu → log linkage tab.

Please contact the Online Contact administrator for activating log linkage through **Online Contact Customer Center**. ([Online Contact Customer Center](https://nhn-contact.oc.toast.com/oceng/hc/))
