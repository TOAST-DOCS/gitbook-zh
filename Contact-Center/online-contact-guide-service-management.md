## Contact Center > Online Contact > Service Guide (Consultation) > Service Management

Service Management menu in Consultation Management service includes **detailed setting functions for accepting and processing inquiries** including authentication, chat, ticket, call, agent, help center, external channel and security management.

The configuration or detailed functions of the help center you set up in the menu can be checked immediately after application at the help center for each service, which can be accessed through the following route.

### Help Center Access

- **Help Center Link** in the bottom right of Online Contact web page
- https:// **Domain Name**.oc.toast.com/ **Service ID** /hc

**Domain name** is the information which was created when you added your organization. Modifying is available in NHN Cloud Console → Set Organization → Set Domain.
**Service ID** is the information which was entered when adding service from [Global Management → Contract Service Status] menu. It cannot be modified after initial creation.

## Authentication
In authentication menu, you could enable/disable **Open API**, and manage related functions.

### Open API
![](http://static.toastoven.net/prod_contact_center/2.2.1-(2)_en.png)
In Open API tab, OPEN API could be **① enabled or disabled**, and **② Service Key**, **③ Allowed IP List** could be managed.
Through **Allowed IP List**, Open API can be called only from the IP which is registered in the list.

## Chat
Functions in this menu are related to chat consultation. Chat consultation could be enabled in [Service Management → Help Center → Default Settings] menu, and could be accessed through **chat icon** which is displayed in the bottom right side after chat consultation is enabled.

✔ **\[FAQ]** [Can I access to the chat screen only from the service which I have chat permission?](https://nhn-contact.oc.toast.com/oceng/hc/article/151/)

![](http://static.toastoven.net/prod_contact_center/2.2.2-(1)_en.png)
After accessing through **chat icon**, click **① status value** in the top left of the chat screen to set your status. (initially set to ‘offline’, can choose between online/break/offline). Responding to customer's chat request is only available when chat status is set to online.

### Default Settings
![](http://static.toastoven.net/prod_contact_center/2.2.2-(2)_1_en.png)
You can set **① Greeting Message**, and **② Satisfaction Guide Message** by the help center language you set on [Global Management → Contract Service Status → Basic Information] menu.  Evaluation request could be sent through **Evaluation** button in the top of the chat screen.

### Agent Assignment Settings
![](http://static.toastoven.net/prod_contact_center/2.2.2-(3)_en.png)
**①** Could choose whether to **assign chat priority** to a counselor who has recent chat history with a customer who requested chat consultation, or to distribute **randomly**.

### Chat Screen Insertion Code
![](http://static.toastoven.net/prod_contact_center/2.2.2-(4)_en.png)
**① Chat Widget Insertion code** is provided to apply Online Contact's chat service in other external pages. Please copy the script provided and insert it in front of the </body> tag of the website's HTML source code.

### Manage Category
![](http://static.toastoven.net/prod_contact_center/2.2.2-(5)_en.png)
This menu allows you to manage the category of **Processing Type** among the consultation information which the agent inputs about the customer during chat consulting. You can set processing types 1 through 3 depth.

**① When adding category** in the lower depth after adding the upper category, click the upper category first, and then add the subcategory after checking whether the right category has been selected. Under the color-highlighted category, a new subcategory would be added.

**Duplicate category names are not allowed** within the same depth. (Possible if the depth is different)

## Ticket
From Ticket menu, you can **manage submission/processing categories**, **set trigger features** that can improve business efficiency, **configure help center inquiry fields**, **manage templates**, and **set up email**.

### Manage Category
In Consultation Management service, Ticket Categories are used as follows.

- **Submission Type**: Selected by customer when making inquiries through help center inquiry. (In the case of inquiries via phone or e-mail, categories are received as blank, and the agent can select and save when processing the ticket.)
- **Processing Type**: Selected by agents when processing tickets

#### Submission Type
![](http://static.toastoven.net/prod_contact_center/2.2.3-(1)-1_en.png)
**①** When adding lower level categories, please click the upper level category first and check whether it is properly selected. Categories will be created below the highlighted category. **Duplicate** category names are not allowed within the same depth. Category names can be set for each help center language you set on [Global Management → Contract Service Status → Basic Information] menu.

**②** If you click the created category, **delete** button will appear. You can **edit category names** by double clicking the category.

From toggle buttons, you could configure the **state** of submission types. **Activated** submission types are displayed in both **Help Center** and **Ticket Management** menu, and **deactivated** submission types are only displayed in **Ticket Management** menu. Thus, submission types could be separately managed depending on the purpose.  

**③** You could copy **Category ID** through **Copy** button, and **download overall category information** into excel format through **Download** button.

#### Processing Type
![](http://static.toastoven.net/prod_contact_center/2.2.3-(1)-2_en.png)
**①** When adding lower level categories, please click the upper level category first and check whether it is properly selected. Categories will be created below the highlighted category. **Duplicate** category names are not allowed within the same depth. **②** You could modify or delete categories through **Edit**, **Delete** button.

**③** You could copy **Category ID** through **Copy** button, and **download overall category information** into excel format through **Download** button.

### Trigger
![](http://static.toastoven.net/prod_contact_center/2.2.3-(2)_en.png)
Triggers are designed to increase task productivity by **automating** repetitive tasks. By using triggers, resulting behaviors are automatically executed when certain conditions are met. You can also set up notification mails to be sent for results.

Example) If `Submission Type` of the ticket = `Billing`, `Assign` ticket to `test01` agent of `Billing` group `necessarily`

Click the **① Add Trigger** button, enter all the title, conditions, and results, and click the **Save** button to save and activate the trigger. Enabled triggers can be disabled via the **② Disable** button, and conditions or results can be modified via the **③ Edit** button.

✔ **\[FAQ]** [How can I automatically forward the received inquiry?](https://nhn-contact.oc.toast.com/oceng/hc/article/126/)
✔ **\[FAQ]** [Can notification emails be sent under certain conditions?](https://nhn-contact.oc.toast.com/oceng/hc/article/125/)

#### Trigger Condition Types
![](http://static.toastoven.net/prod_contact_center/2.2.3-(2)a_1_en.png)

#### Trigger Condition Details
![](http://static.toastoven.net/prod_contact_center/2.2.3-(2)b_1_en.png)

#### Trigger Condition Details
![](http://static.toastoven.net/prod_contact_center/2.2.3-(2)c_1_en.png)

#### Trigger Result Details
##### Ticket : Assign
![](http://static.toastoven.net/prod_contact_center/2.2.3-(2)d_1_en.png)
Select and save the group of agents, the agents to distribute tickets, and the distribution method(random/linear/select agent), and the tickets will be assigned according to the selected results when the trigger conditions are met.

For **random allocation**, tickets are randomly assigned to selected agents, and for **linear allocation**, tickets are assigned in the order in which agents are added to the group.

If there are multiple triggers with different agents on the same condition, tickets will continue to be assigned only to agent set to the last trigger after all triggers have been triggered sequentially, rather than randomly assigned to one of these agents. Therefore, if you want to set the ticket to be assigned randomly within the group, please select **linear allocation**.

##### Notification
![](http://static.toastoven.net/prod_contact_center/2.2.3-(2)e_1_en.png)
Notification is the type of result that **notification mail is sent** to the specified recipient when the trigger condition is met.
After selecting the person to send the notification mail, you can set the title and content of the notification mail by **language of the help center** through the **① Notification Settings** button. For notification mail sent through triggers, the mail layout set in the Service Management → Ticket → Email Settings menu **is not applied**, and it is sent **alone as you set it** on the notification settings pop-up.
When setting up the notification mail, the content editor is displayed in **HTML** or **TEXT** mode according to the editor type setting value in [Global Management → Contract Service Status → Basic Information] menu.

##### Forward
![](http://static.toastoven.net/prod_contact_center/2.2.3-(2)f_en.png)
Forward is the type of result that **ticket information being emailed** to the specified recipient when the trigger condition is met. You can check the information and inquiries of the ticket through the e-mail. If you click the **① Online Contact Shortcut** link at the bottom of the inquiry, **ticket screen would be popped-up**, and you can process the ticket directly on the screen. If you chose to **complete the ticket after forwarding**, the inquiry will be emailed and your ticket will be automatically processed as**completed**.

##### Callback url
Callback url is the type of result that the **entered callback address is called** when the trigger condition is met.

##### Dooray Notification
![](http://static.toastoven.net/prod_contact_center/2.2.3-(2)g_en.png)
If the trigger conditions are met, information of the ticket is sent via Dooray notification based on the template set by the **① Template Settings** button. For the link URL, see [Dooray Messenger Service Guide](https://helpdesk.dooray.com/share/pages/4Ws8UzbnT7KbP9R5fAQBjg/2956645181839458938) for instructions.

### Field
![](http://static.toastoven.net/prod_contact_center/2.2.3-(3)_en.png)
Fields are divided into **① Customer Field** and **① Agent Field**. Please select whether you want to manage before selecting field setting or field management.

In Consultation Management service, customer and agent fields are used as follows:

- **Agent Field**: Fields which agent enters when processing ticket
- **Customer Field** : Fields shown to the customer in Help Center → Inquiry screen. Implemented on Help Center Inquiry screen as set in field setting menu. (In the case of inquiries via phone or e-mail, there is no separate field entry procedure, thus customer fields are received blankly. Agents can enter information when processing the ticket.)

#### Field Setting
![](http://static.toastoven.net/prod_contact_center/2.2.3-(4)_en.png)
**①** Depending on the submission type you added earlier in [Service Management → Ticket → Manage Category] menu, you can set the fields required for inquiry details differently. Click **Submission Type** to view the fields you have set up, and you can change the **②** order of fields except for personal information field. In the case of personal information field, it is always pinned to the bottom.

You can also **③ add** and **④ remove** the fields you previously added on the Field Management menu.

![](http://static.toastoven.net/prod_contact_center/2.2.3-(4)-1_en.png)
**Call related fields** (Consultation Time, IN/OUT, Call Reservation, Call Reservation Time, Call Reservation Phone Number) are only displayed in tickets which are submitted through call, even if they were added in activated submission types. Thus, one submission type could be used in several channels.

#### Field Management (System Field)
![](http://static.toastoven.net/prod_contact_center/2.2.3-(5)_1_en.png)
**①** You can manage fields in **Field Management** tab. Settings of **System Fields** could only be **modified** or **initialized**. 

![](http://static.toastoven.net/prod_contact_center/2.2.3-(5)_2_1_en.png)
In the case of **system fields**, it is possible to modify **'Field Name'**, **'Notice'**, **'Personal Information'**, **'Destroy Personal Information'**. **① Field names** can be set for **each help center language** you set on [Global Management → Contract Service Status → Basic Information] menu.

The modification of **② 'Required'**, **'Exposured'** is determined by the kind of field.

- System Fields required for Help Center (Type, Email, Title, Contents, Personal Information): 'Required'/'Exposured' default value 'Yes', cannot change value.
- System Fields related to Call (Consultation Time, IN/OUT, Call Reservation, Call Reservation Time, Call Reservation Phone Number): 'Exposured' default value 'No', cannot change value.

#### Field Management (User Field)
![](http://static.toastoven.net/prod_contact_center/2.2.3-(5)_3_en.png)
**①** You can manage fields in **Field Management** tab. **User Fields** could be **added**, **modified**, or **deleted**.

![](http://static.toastoven.net/prod_contact_center/2.2.3-(6)_1_en.png)
For adding customer fields, items required to be filled are as follows:

- **① Field type**: The **type of field**. If you select the field type, **Detailed Settings** and **Preview** will be displayed at the bottom of Basic Settings. Detailed settings allow you to set the values to be displayed for the field, and you can use preview to see what the field will look like on the customer's screen.
- **② Field code**: When developing inquiry feature with Open API, field code is used as a unique value to represent the field.
- **③ Field Name**: The name of the field, which appears with the field on the Inquiry screen. Can be set for each help center language set on [Global Management → Contract Service Status → Basic Information] menu.
- **④ Notice**: A guide phrase for the field, which appears with the field on the Inquiry screen. Can be set for each help center language set on [Global Management → Contract Service Status → Basic Information] menu.
- **⑤ Required**: When set, it is marked with a \*(star) to the right of the field name and must be filled before you move on to the next field. Among the default fields, type, email, title, contents, personal information must be set to ‘required’.
- **⑥ Personal information(Encrypt or not)**
- **⑦ Destroy personal information**

For agent fields, **Permission**(Administrator, Agent) item is additionally required to be filled.

### Manage Template
![](http://static.toastoven.net/prod_contact_center/2.2.3-(7)_en.png)
Template managing is a feature that allows you to quickly process tickets by **pre-adding answer templates** for frequently asked questions.

#### Template Registration
![](http://static.toastoven.net/prod_contact_center/2.2.3-(7)_1_en.png)
At **Template Registration** tab, you could **add** templates, **② search** templates by setting **① search criteria**, **modify** or **delete** templates.
You could serach templates by title, processing type, search code. In the **③ template list**, information are displayed as follows :

- Title
- Processing Type: Type **connected** to the template
- Search Code: **Code** which can be used when searching templates
- Number of Use: The **number of times** which the template was **selected**

![](http://static.toastoven.net/prod_contact_center/2.2.3-(7)_2_en.png)
If you click **① Add Template** button, pop-up screen for setting template will be displayed.

- **② Template Title**
- **③ Contents**: Content editor is displayed in **HTML** or **TEXT** mode according to the editor type setting value in [Global Management → Contract Service Status → Basic Information] menu. **Replacement code** could be used when writing contents. **Double-click** adds the code to the contents, and data is inserted into code area of the template when processing tickets, making it more convenient to write replies.
- **④ Search Code**: **Code** which can be used when searching templates. (English or number combination within 20 characters)
- **⑤ Template Connection**: You can **select processing types** to connect to the template. **Check** the type you want to move, and press the **arrow** button.

You can insert **links**, **images**, and **tables** into the body when you right-click on the body of the content, and when inserting images, you can use the path of the uploaded image from the Service Management → Help Center → Manage File Uploads menu or by attaching the image directly.

#### Template Connection
![](http://static.toastoven.net/prod_contact_center/2.2.3-(7)_3_en.png)
You can **view the templates linked to each processing type**, **add** templates to each processing type, or **delete** added templates.
If you select a processing type from the list, you will see the list of connected templates, and you can add templates through **① Add** button.

✔ **\[FAQ]** [How can I use answer templates?](https://nhn-contact.oc.toast.com/oceng/hc/article/122/)
✔ **\[FAQ]** [I registered answer templates, but they are not shown when processing tickets.](https://nhn-contact.oc.toast.com/oceng/hc/article/143/)

### Email Settings
![](http://static.toastoven.net/prod_contact_center/2.2.3-(8)_1_en.png)
In the **Email Settings** menu, you can create a **① representative account address** through the domain provided by Online Contact, and if you have a separate **② external account**, you can register to receive inquiries.
You can set the **③ sender information** to specify the sender name and address of the email sent via Online Contact.

![](http://static.toastoven.net/prod_contact_center/2.2.3-(8)_1_2_en.png)
**④ Mail layout** settings allow you to set a common layout for mail sent during ticket processing by ticket status and help center language.
The layout editor is displayed in **HTML** or **TEXT** mode according to the editor type setting value in [Global Management → Contract Service Status → Basic Information] menu. From using **replacement codes**, you can set ticket related information to be automatically entered at the selected location. Among the replacement codes, the answer(#{content}) code must be included in the layout.

✔ **\[FAQ]** [How can I connect my external email to Online Contact?](https://nhn-contact.oc.toast.com/oceng/hc/article/127/)

### Sensitive
![](http://static.toastoven.net/prod_contact_center/2.2.3-(15)_en.png)
You can manage sensitive words to prevent errors or incorrect instructions from being included in ticket replies.
If you proceed **ticket preview** or **resolve/pend** tickets while the **① added** sensitive text is included in the content, a **② pop-up** will be displayed indicating that sensitive words are included.

## Call
In Call menu, you could register **IVR Route Code, Name** for managing callback, and register **Calling Number** which is displayed to the customer when making a outbound call. This menu is only viewable in services which **Ticket Management →  Include call(using CTI)** function is **activated** in contract details.

When call function is activated, to call authorized agents **call widget** will be shown, which allows agents to access call consultation related features.

✔ **\[FAQ]** [Call icon is not displayed to the agent.](https://nhn-contact.oc.toast.com/oceng/hc/article/153/)
✔ **\[FAQ]** [Can I access the CTI screen only when accessing service with call authority?](https://nhn-contact.oc.toast.com/oceng/hc/article/150/)

### IVR Route Management
In IVR Route Management menu, you could manage **IVR Route** information.
![](http://static.toastoven.net/prod_contact_center/2.2.3-(8)-1_2_en.png)

If you click **① Add** button after **CTI Login**, you can access pop-up screen for **② Adding IVR Route**.
On the screen, you could view **unregistered counsel menus** for the current service **among all counseling menus** in linked CTI tenants.
After selecting the IVR Route to add, click **Save** button to finish adding process.

Registered IVR Route data could be only **③ deleted**. If IVR Route data has been modified in the linked CTI tenant, you could update to the revised data through **deleting** and **adding** the data again.

### Calling Number
![](http://static.toastoven.net/prod_contact_center/2.2.3-(9)_1_en.png)
In this menu, you could manage **calling number** which is displayed to the customer when making a outbound call.
It can be used by agents who conduct call consultations in multiple services by selecting calling number appropriately for the purpose of the outbound call.

The list of calling numbers is divided into **① Confirmed**, and **② Total**. In **② Total** list, you can check the registered calling numbers in all states. In **① Confirmed** list, only **confirmed** calling numbers are displayed, and the order between the calling numbers can be adjusted. The adjusted order is applied in the calling number list of the CTI widget in real time.

By clicking **③ Add** button, page for adding calling number would be shown. After entering name, number, and attaching certificate of use of communication service, click save, and the added calling number would be added to the total list as **New**. **Modifying** is only possible when the state is **new**, and **deleting** is possible regardless of the state.

Once the verification with the certificate of use of communication service is completed, the state will be changed to **Confirm** or **Reject**. **Confirmed** calling numbers will be added in the confirmed list.

## Agent
In this menu, you can add and edit agents and groups for handling customer inquiries (ticket, chat, call consultations), and set up groups and permissions for each agent.

### Agent
![](http://static.toastoven.net/prod_contact_center/2.2.4-(1)_en.png)
User must be registered as **IAM Member** to be added as an agent.

#### Register IAM Member
- Click **① Invite Members** button → Enter name, ID, email
- NHN Cloud CONSOLE → Manage Member → IAM Member tab → Click Register IAM Member button → Enter ID, name, mail, and mobile phone number

Select one of the above two methods to register IAM member., and click **② Add Agent** → **View Agent** → search registered IAM Member by entering name/account/email, and add the member as the service agent.

When adding a agent, assigning group is mandatory. Thus, adding groups should be proceeded before adding agents.

The **permission** of agents is as follows. Setting organization administrator permission is available from [Global Management → Organization Administrator](https://docs.nhncloud.com/en/Contact%20Center/en/online-contact-guide-global-management/#organization-adminstrator) menu.

- Administrator: Permission which features related to **service setting** added to the permission of **agents**.
- Agent: Permission for **ticket, call, chat consultation**.

### Group
![](http://static.toastoven.net/prod_contact_center/2.2.4-(2)_en.png)
In Group menu, you can **① add**, **② edit**, **③ delete** groups. When configuring agents into groups, you can assign type-specific inquiries to the appropriate group, or set up notification mails.

#### Add Group
![](http://static.toastoven.net/prod_contact_center/2.2.4-(3)_en.png)
Click **Add Group**, enter group name, choose agent to be assigned, and click **①** ‘**>** ‘button to move agent to ‘Assigned Agent’. Conversely, when you unassign a agent, click ‘**<**’ button to move agent to ‘Unassigned Agent’. After assigning agents, press **② Save** button to apply group settings. A group can be added without assigning agents.

## Help Center
### Template Management
![](http://static.toastoven.net/prod_contact_center/2.2.5-(1)_en.png)
In this menu, you can **manage design themes** for your Help Center. Using the provided editor, you can modify the design for each service-specific detail area.

There are two basic templates available, and you can add new templates with the **① Add Template** button. The template you added can be **② edited** or **deleted**. The template in use cannot be deleted, so please enable another template to delete it.

![](http://static.toastoven.net/prod_contact_center/2.2.5-(2)_1_en.png)
When adding or editing templates, you can directly input **① CSS / HTML / JS scripts**, or upload appropriate file (script, font, image, etc.) and enter the path of the resource in the editor to change the configuration of the Help Center. Through **② Insert multilingual code** button, you could view the list of language sets which have been set in [Service Management → Help Center → Multilingual Management] menu. The multilingual code could be inserted into the template through **Choice** button.

Through **④ Preview** button you could see the edits being applied, and after **③ saving**, you could apply the template to the help center.  

✔ **\[FAQ]** [Is there some specific examples of managing help center PC/Mobile templates?](https://nhn-contact.oc.toast.com/oceng/hc/article/141/)
✔ **\[FAQ]** [Can I change the font of the help center text or apply effects such as bold, underline, etc. ?](https://nhn-contact.oc.toast.com/oceng/hc/article/145/)

**When modifying CSS**, the key elements you can refer are as follows:

<!-- css 요소 목록 html -->

<details markdown="1">
<summary> main.css </summary>

<table>
<thead>
<tr>
<th>Element Name</th>
<th>Details</th>
</tr>
</thead>
<tbody>
<tr>
<td>.main_banner</td>
<td>Upper banner area / main page</td>
</tr>
<tr>
<td>.main_banner img</td>
<td>Image of upper banner area / main page</td>
</tr>
<tr>
<td>.carousel-caption .title_txt</td>
<td>Title of upper banner area / main page</td>
</tr>
<tr>
<td>.carousel-caption .sub_txt</td>
<td>Subtitle of upper banner area / main page</td>
</tr>
<tr>
<td>.search-box</td>
<td>Search box of upper banner area / main page</td>
</tr>
<tr>
<td>.search-box .icon-ic-search</td>
<td>Search icon of upper banner area / main page</td>
</tr>
<tr>
<td>#supports .container-con</td>
<td>Contents area / main page</td>
</tr>
<tr>
<td>#supports .support__item:nth-child(1):before</td>
<td>Notice icon / main page</td>
</tr>
<tr>
<td>#supports .support__item:nth-child(2):before</td>
<td>FAQ icon / main page</td>
</tr>
<tr>
<td>#supports .support__item:nth-child(3):before</td>
<td>Inquiry icon / main page</td>
</tr>
<tr>
<td>#supports .support__item:nth-child(4):before</td>
<td>Inquiry History icon / main page</td>
</tr>
<tr>
<td>#supports .support__item .card-title .btn</td>
<td>Title of contents area / main page</td>
</tr>
<tr>
<td>#supports .support__item .card-title .btn:hover</td>
<td>Title of contents area / main page (Color changed when hovered)</td>
</tr>
<tr>
<td>#supports .support__item .card-title .btn:after</td>
<td>Right arrow icon of contents area / main page</td>
</tr>
<tr>
<td>#supports .support__item .card-text</td>
<td>Information text of contents area / main page</td>
</tr>
<tr>
<td>#sec_contact-news .textArea</td>
<td>Bottom banner area / main page</td>
</tr>
<tr>
<td>#sec_contact-news .textArea .text-item h3</td>
<td>Title of bottom banner area / main page</td>
</tr>
<tr>
<td>#sec_contact-news .textArea .text-item .icon-more::after</td>
<td>See more icon of bottom banner area / main page</td>
</tr>
<tr>
<td>#sec_contact-news .textArea .text-item li</td>
<td>Document list of bottom banner area / main page</td>
</tr>
<tr>
<td>#chat-offline</td>
<td>Agent offline box</td>
</tr>
<tr>
<td>#chat-offline .title</td>
<td>Title of agent offline box</td>
</tr>
<tr>
<td>#chat-offline .text</td>
<td>Text of agent offline box</td>
</tr>
<tr>
<td>#chat-offline .close</td>
<td>Close icon of agent offline box</td>
</tr>
<tr>
<td>#chat-offline .btn</td>
<td>Contact us icon of agent offline box</td>
</tr>
</tbody>
</table>

</details>

<details markdown="1">
<summary> faq.css </summary>

<table>
<thead>
<tr>
<th>Element Name</th>
<th>Information</th>
</tr>
</thead>
<tbody>
<tr>
<td>.lnb--fixed .lnb--fixed__nav</td>
<td>Left LNB / details page</td>
</tr>
<tr>
<td>.help-center-title</td>
<td>Title of left LNB / details page</td>
</tr>
<tr>
<td>.lnb__nav</td>
<td>List of left LNB / details page</td>
</tr>
<tr>
<td>.lnb__nav li a</td>
<td>Item of list of left LNB / details page</td>
</tr>
<tr>
<td>.lnb__nav li.on a</td>
<td>Selected item of list of left LNB / details page</td>
</tr>
<tr>
<td>.lnb--fixed__side-divider</td>
<td>Dividing line of left LNB and contents</td>
</tr>
<tr>
<td>.lnb--fixed__content</td>
<td>Contents area / details page</td>
</tr>
<tr>
<td>.tit_txt</td>
<td>Title of contents area / details page</td>
</tr>
<tr>
<td>.data_info-box</td>
<td>Box of contents area / details page</td>
</tr>
<tr>
<td>.tab_category</td>
<td>Category tab of contents area / details page</td>
</tr>
<tr>
<td>.tab_category&gt;li.on</td>
<td>Selected category of contents area / details page</td>
</tr>
<tr>
<td>.tab_category&gt;li</td>
<td>Category of contents area / details page</td>
</tr>
<tr>
<td>.tbl_wrap</td>
<td>List of contents area / details page</td>
</tr>
<tr>
<td>.faqData th:nth-child(1)</td>
<td>Category of FAQ table</td>
</tr>
<tr>
<td>.faqData th:nth-child(2)</td>
<td>Title of FAQ table</td>
</tr>
<tr>
<td>.faqData th:nth-child(3)</td>
<td>Registered date of FAQ table</td>
</tr>
<tr>
<td>.faqData tr.hot-text td</td>
<td>Category of main-fixed document of FAQ table</td>
</tr>
<tr>
<td>.faqData tr.hot-text td .title-info a</td>
<td>Title of main-fixed document of FAQ table</td>
</tr>
<tr>
<td>.faqData td .title-info sup</td>
<td>HOT icon of main-fixed document of FAQ table</td>
</tr>
<tr>
<td>.gocont .search</td>
<td>FAQ search</td>
</tr>
<tr>
<td>.sel</td>
<td>Category in FAQ search</td>
</tr>
<tr>
<td>.search .inp</td>
<td>Search input in FAQ search</td>
</tr>
<tr>
<td>.search .btnArea</td>
<td>Search button in FAQ search</td>
</tr>
<tr>
<td>.faqData_info-con</td>
<td>Contents of FAQ document</td>
</tr>
<tr>
<td>.faqData_info-con .dataTit</td>
<td>Title of FAQ document</td>
</tr>
<tr>
<td>.faqData_info-con .dataTime</td>
<td>Registered date of FAQ document</td>
</tr>
<tr>
<td>.faqData_info-con .dataTextBox</td>
<td>Text of contents of FAQ document</td>
</tr>
</tbody>
</table>

</details>

<details markdown="1">
<summary> notice.css </summary>

<table>
<thead>
<tr>
<th>Element Name</th>
<th>Details</th>
</tr>
</thead>
<tbody>
<tr>
<td>.el-breadcrumb</td>
<td>Right-upper text area / details page</td>
</tr>
<tr>
<td>.el-breadcrumb li</td>
<td>Item of right-upper text area / details page</td>
</tr>
<tr>
<td>.noticeData</td>
<td>Notice table</td>
</tr>
<tr>
<td>.noticeData th:nth-child(1)</td>
<td>Number of notice table</td>
</tr>
<tr>
<td>.noticeData th:nth-child(2)</td>
<td>Title of notice table</td>
</tr>
<tr>
<td>.noticeData th:nth-child(3)</td>
<td>Heading of notice table</td>
</tr>
<tr>
<td>.noticeData th:nth-child(4)</td>
<td>Registered date of notice table</td>
</tr>
<tr>
<td>.noticeData tr.hot-text</td>
<td>Main-fixed document of notice table</td>
</tr>
<tr>
<td>.noticeData tr.hot-text td</td>
<td>Number of main-fixed document of notice table</td>
</tr>
<tr>
<td>.noticeData tr.hot-text td .title-info a</td>
<td>Title of main-fixed document of notice table</td>
</tr>
<tr>
<td>.noticeData td .title-info sup</td>
<td>HOT icon of main-fixed document of notice table</td>
</tr>
<tr>
<td>.icon-leavel-1</td>
<td>Heading of main-fixed document of notice table</td>
</tr>
<tr>
<td>.noticeData tr</td>
<td>Item of notice table</td>
</tr>
<tr>
<td>.noticeData td .title-info a</td>
<td>Title of item of notice table</td>
</tr>
<tr>
<td>.upload-text-memo</td>
<td>Text of attachments field of inquiry</td>
</tr>
<tr>
<td>.faqData_info-con .dataTime .noticeType</td>
<td>Heading of item of notice table</td>
</tr>
<tr>
<td>.faqData_info-con .dataTime .noticeType .icon-leavel-1</td>
<td>Heading icon of item of notice table</td>
</tr>
</tbody>
</table>

</details>

<details markdown="1">
<summary> search.css </summary>

<table>
<thead>
<tr>
<th>Element Name</th>
<th>Details</th>
</tr>
</thead>
<tbody>
<tr>
<td>.paginate</td>
<td>Pagination area</td>
</tr>
<tr>
<td>.paginate li</td>
<td>Item of pagination area</td>
</tr>
<tr>
<td>.paginate li.firstPage a</td>
<td>&lt;&lt; key of pagination area</td>
</tr>
<tr>
<td>.paginate li.firstPage a.img</td>
<td>Image of &lt;&lt; key of pagination area</td>
</tr>
<tr>
<td>.paginate li.prev a.</td>
<td>&lt; key of pagination area</td>
</tr>
<tr>
<td>.paginate li.prev a img</td>
<td>Image of &lt; key of pagination area</td>
</tr>
<tr>
<td>.paginate li a</td>
<td>Each page of pagination area</td>
</tr>
<tr>
<td>.paginate li.number.active a</td>
<td>Current page of pagination area</td>
</tr>
<tr>
<td>.paginate li.next a.</td>
<td>&gt; key of pagination area</td>
</tr>
<tr>
<td>.paginate li.next a img</td>
<td>Image of &gt; key of pagination area</td>
</tr>
<tr>
<td>.paginate li.lastPage a</td>
<td>&gt;&gt; key of pagination area</td>
</tr>
<tr>
<td>.paginate li.lastPage a.img</td>
<td>Image of &gt;&gt; key of pagination area</td>
</tr>
<tr>
<td>.search-title</td>
<td>Title of search result</td>
</tr>
<tr>
<td>.search-title strong</td>
<td>Search term (emphasized) of search result</td>
</tr>
<tr>
<td>.search-text</td>
<td>Search result</td>
</tr>
<tr>
<td>.search-text .search-title_sub</td>
<td>Subclass of search result</td>
</tr>
<tr>
<td>.search-text .search-text_lit</td>
<td>Item of search result</td>
</tr>
<tr>
<td>.search-text .search-text_lit dt a</td>
<td>Title of item of search result</td>
</tr>
<tr>
<td>.search-text .search-text_lit dd .search-text_con</td>
<td>Preview of contents of item of search result</td>
</tr>
<tr>
<td>.search-text .search-text_lit dd .search-text_time</td>
<td>Registered date of contents of item of search result</td>
</tr>
</tbody>
</table>

</details>

<details markdown="1">
<summary> inquiry.css </summary>

<table>
<thead>
<tr>
<th>Element Name</th>
<th>Details</th>
</tr>
</thead>
<tbody>
<tr>
<td>.selectStyle</td>
<td>Option of search</td>
</tr>
<tr>
<td>.inquiry-con</td>
<td>Contents area of inquiry</td>
</tr>
<tr>
<td>.inquiry-con_table</td>
<td>Inquiry table</td>
</tr>
<tr>
<td>.inquiry-con_table th</td>
<td>Field of inquiry table</td>
</tr>
<tr>
<td>.bl_ess</td>
<td>Required field of inquiry table</td>
</tr>
<tr>
<td>.inquiry-con_table td</td>
<td>Input of inquiry table</td>
</tr>
<tr>
<td>.error_txt</td>
<td>Input of inquiry table (Error)</td>
</tr>
<tr>
<td>.inquiry-btn</td>
<td>Submit button of inquiry table</td>
</tr>
<tr>
<td>.layui-icon</td>
<td>Arrow button</td>
</tr>
<tr>
<td>.layui-icon-right</td>
<td>Left arrow button</td>
</tr>
<tr>
<td>.layui-icon-up</td>
<td>Down arrow button</td>
</tr>
<tr>
<td>.check_area_wrap .td-radio .layui-form-checkbox[lay-skin="primary"] span</td>
<td>Checkbox text</td>
</tr>
<tr>
<td>.error_txt</td>
<td>Error text</td>
</tr>
</tbody>
</table>

</details>

### Manage File Uploads
![](http://static.toastoven.net/prod_contact_center/2.2.5-(3)_en.png)
As a tool for managing the files used to create templates and layouts, you can upload the files through the **① Upload File** button and use **② File Path** of the resource without having to upload files every time. File names could not be duplicated.

### Default Settings
![](http://static.toastoven.net/prod_contact_center/2.2.5-(4)_2_en.png)
You can **Enable** functions you use in the Help Center and **Disable** functions you don't use. When disabled, the function becomes hidden from the Help Center page.

Functions you can manage are as follows:

- Notice
- FAQ
- 1:1 Inquiry & My Inquiries
- Chat
- Help center navigation
- Company Informaton(Can be added/modified in Global Management → Company Information Management menu)

### Member Interlink
![](http://static.toastoven.net/prod_contact_center/2.2.5-(5)_1_en.png)
**Member Interlink** is a function to apply **member certification process** provided by the client to the help center of Online Contact. Through this function, **member inquiries** could be received, and customers could **check** the **sent inquiries**. The login method is provided by two types : **GET**, **POST**. For the linkage, API should be developed and registered according to the API guide provided by Online Contact.

Member Interlink function could be **① activated/deactivated** through the button. If the function is **activated**, you can select whether to activate **② non-member inquiry**, and **③ login method**. If **non-member inquiry** option is activated, inquiries can be received even when the customer is not logged in, and if deactivated, inquiries can only be received while customers are logged-in.

API guide for each **login method** is linked below.

- [Online Contact > API Guide for Developers > Member Integration (POST)](https://docs.nhncloud.com/en/Contact%20Center/en/online-contact-api-guide-openapi-sso/)
- [Online Contact > API Guide for Developers > Member Integration (GET)](https://docs.nhncloud.com/en/Contact%20Center/en/online-contact-api-guide-openapi-member-get/)

### Multilingual Management
For each help center language set in [Global Management → Contract Service Status → Basic Information] menu, you can manage multilingual codes and tags to use in language-specific help centers.

#### Multilingual Code
![](http://static.toastoven.net/prod_contact_center/2.2.5-(7)_en.png)
**① Multilingual Code** tab allows you to manage the multilingual language set you will use in the language-specific help center.
In the case of system language sets, only content and tags can be modified, and the value of the code cannot be changed.

From **② Registration** button, you could register **user-defined** language sets. **Input columns for each language** are displayed according to the help center language you set on the contract basic information setting screen, and you can classify language sets by use and type through setting **tags**. Registered sets can be inserted into the script when managing templates, so they can be used to configure **③ help center pages for each language**.

#### Tag
![](http://static.toastoven.net/prod_contact_center/2.2.5-(7)-1_en.png)
In the **① Tag** tab, you can manage **user-defined** tags that can be used for classifying language sets.
If you press **② Add** button after entering the tag name, user-defined tag will be added, and it will be shown in the tag list with the system tags when managing, or searching language sets.

## External Channel
Inquiries received by **external services** could be switched to tickets in Online Contact. **Twitter**, **KakaoTalk**, and **SMS** are currently supported services.

### Twitter
![](http://static.toastoven.net/prod_contact_center/2.2.6-(1)_en.png)
You can **① Enable** or **Disable** Twitter connection, and could register Twitter account by **② Register** button when Twitter connection is enabled.

![](http://static.toastoven.net/prod_contact_center/2.2.6-(2)_en.png)
When registering your account, you can set whether to switch tickets for **① Tweet(Mention)** and **② Direct message** respectively, and if you wish to convert direct messages to a ticket, please check the procedure below.

Access your Twitter account and check More → Settings and Privacy → Privacy and Safety → Direct Messages → **Receive message requests** must be enabled before a message to the linked account can be received as a ticket.

✔ **\[FAQ]** [What is the process of submitting/answering tickets when external channel is activated?](https://nhn-contact.oc.toast.com/oceng/hc/article/142/)

### Kakao Talk Plus Friend
![](http://static.toastoven.net/prod_contact_center/2.2.6-(3)_en.png)
You can **① Enable** or **Disable** KakaoTalk connection, and could register KakaoTalk ID and date to activate by **② Register** button when KakaoTalk connection is enabled. The connection takes up to 1~2 business days, and if the connection is rejected, the reason for rejection will be displayed. You must change Management → Detailed Settings → Channel Home → Enable Public Search to **ON** in the KakaoTalk channel manager center to connect with Online Contact.

![](http://static.toastoven.net/prod_contact_center/2.2.6-(4)_en.png)
Click on the **Account which is connected** to set up the details of the KakaoTalk function.

- **①** Consultation time
- **②** Days available for consultation
- **③** Auto comment
    - Out of business hours: Comment sent when chat request received **besides the consultation time**
    - First greeting: Comment sent when **chat consultation connected**
    - No agent: Comment sent when **all agents are offline**
    - Request for evaluation: Comment sent with the **evaluation request** from the agent
    - End of consultation: Comment sent when consultation **ended**

When KakaoTalk is connected and activated in Online Contact, the existing plus friend 1:1 chat will be stopped, and inquiries received through KakaoTalk will be showed in the chat screen, with ‘channel’ of the ticket marked as ‘KakaoTalk’.

✔ **\[FAQ]** [What is the process of submitting/answering tickets when external channel is activated?](https://nhn-contact.oc.toast.com/oceng/hc/article/142/)

### SMS
![](http://static.toastoven.net/prod_contact_center/2.2.6-(6)_en.png)
You could send SMS/MMS through linking **[NHN Cloud Notification → SMS]** service with Online Contact.
If **SMS** function is **activated** in Global Management → Contract Service Status → Contract Details, SMS menu tab is shown in Service Management → External Channel menu.

To **① activate** SMS linkage, please **activate [NHN Cloud Notification → SMS] service** first, and **② save** the **APP KEY** which you could find in NHN CLOUD CONSOLE. If you enter and save a valid APP KEY, the SMS function is automatically **activated**, and **sending number** list is displayed.

If you click **③ Add** button, pop-up screen for **selecting sending number** will be shown. The numbers which are registered in NHN Cloud Notification → SMS service are shown in the kist, thus please check if there are registered sending numbers before adding in Online Contact. Check the number you want to add, and click confirm button to add the number to the sending number list. The added numbers could be used as **sending number** when sending SMS/MMS in Online Contact.

After activating SMS service and adding sending number, you could proceed to sending/managing SMS in **Additional Business Management → SMS Send** menu.

## Security Management
![](http://static.toastoven.net/prod_contact_center/2.2.6-(5)_en.png)
If you have enabled the Service Management → Security Service feature in the contract information through prior consultation, you can activate **log linkage**, and use **personal information masking** function for encrypting personal information transmitted during chatting and ticket consultation.  

**Personal information masking** function can be used in ticket management, chat widget, chat log without further settings if **Security Service** function is **activated**, and **log linkage** function can be used after activating in Security management menu → log linkage tab.

Please contact the Online Contact administrator for activating log linkage through **Online Contact Customer Center**. ([Online Contact Customer Center](https://nhn-contact.oc.toast.com/oceng/hc/))
