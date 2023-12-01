## Contact Center > Online Contact > Service Guide (Consultation) > Chat

## Default Settings
Chat consultation is available by **enabling** chat function in help center, or by adding **chat widget** to web page through chat screen insertion code.

You could enable chat function in [Service Management → Help Center → Default Settings] menu, and if chat function is enabled you could set following functions in [Service Management → Chat] menu.

- Default Settings: Set **Greeting message** which is sent at the start of the chat, and **Satisfaction guide message** which is sent when the agent sends evaluation request to the customer.
- Agent Assignment Settings: Enable or disable **assign chat priority** to agent with recent chat history with the corresponding customer.
- Chat Screen Insertion Code: If you want to insert chat widget to your service web page to provide Online Contact’s chat consultation service to customers, check **insertion code** in this menu.
- Manage Category: Can set **processing type** which agents enter about the relevant chat consultation by 1 to 3 depth.

✔ **\[FAQ]** [Can I access to the chat screen only from the service which I have chat permission?](https://nhn-contact.oc.toast.com/oceng/hc/article/151/)
✔ **\[FAQ]** [Can I set chat function so that only logged-in users can participate?](https://nhn-contact.oc.toast.com/oceng/hc/article/136/)

## Chat inquiry Receipt/Processing
### Chat reception
![](http://static.toastoven.net/prod_contact_center/5.2-(1)_en.png)
When customer accesses to help center with chat enabled within the help center, **① chat icon** will be displayed at the bottom right of the homepage.

![](http://static.toastoven.net/prod_contact_center/5.2-(2)_en.png)
When chat icon is clicked, **Agent is absent** pop-up will be displayed when all agents are off-line, and you will be directed to **① Contact us** to leave an inquiry.

![](http://static.toastoven.net/prod_contact_center/5.2-(3)_en.png)
If there are agents on-line when chat icon is clicked, chat conversation screen will be created, and you can start chatting with agent if you **① agree with personal information collection agreement**. The following paragraph, Chat Processing, will guide you about changing agent's status.

### Chat Processing
![](http://static.toastoven.net/prod_contact_center/5.2-(4)_en.png)
When agent accesses to Online Contact with chat enabled within the help center, **① chat icon** will be displayed at the bottom right of the homepage. When you click chat icon, you can see chat screen where you can proceed with chat consultation.

![](http://static.toastoven.net/prod_contact_center/5.2-(5)_en.png)
In the **① status window** which is in the left upper side of chat screen, you could change status for processing chat consultation. You can choose from three values: Online, Break, and Offline, and chat will be assigned only when **status is set to online**.

![](http://static.toastoven.net/prod_contact_center/5.2-(6).gif)
When a customer enquiry is received, the chat icon will flash to indicate that a chat consultation has been requested. When you access to chat screen by clicking chat icon, **Chatting** count which indicates the number of ongoing consultations will be counted up, and you could view customers who requested chat consultation. If you click the name of the customer, **Chat screen**, **User Information**, **Consultation Information**, **Create Ticket** button will be displayed.

The following items can be checked and entered in customer information and consultation information.

**③ Customer Information**

- Name
- Email
- Remarks
- IP address
- Device

**④ Consultation Information**

- Channel: **The accessed path** when the customer requested chat consultation 
- Process type: **Process type** which agent enters about chat consultation with the relevant customer. Can set in [Service Management → Chat → Manage Category] menu

If there is anything that needs to be processed in addition to chat consultation, you could create tickets through **⑤ Create Ticket** button. The **channel** of the created ticket will be displayed as ‘**chatting**’, and ‘**Chat History**’ menu will be displayed when the ticket is clicked. Through the menu, you can refer to chat history when processing tickets.

If the chat consultation finishes before customer information and consultation information is saved, the entered information would be unsaved. Thus, please click **⑥ Save** button before chat is finished.

## Satisfaction Evaluation and Finish Chat
![](http://static.toastoven.net/prod_contact_center/5.3-(1)_en.png)
![](http://static.toastoven.net/prod_contact_center/5.3-(2)_en.png)
After the chat is completed, the customer can conduct a satisfaction evaluation for the chat, or the agent can send an evaluation request. If the customer clicks **① Evaluation** button, evaluation screen will be displayed directly, and if the agent clicks **① Evaluation** button, guide message(Can be set in [Service Management → Chat → Default Settings]) will be sent to the customer.

You could finish chat consulting by **② End Chat** button. When the customer finished chatting, you could enter information or create tickets before you click ‘end chat’ button, but after clicking ‘end chat’, the content of chat consulting becomes unviewable in the screen. After the chat has ended, entering and editing information, creating tickets becomes only available in [Chat → Chat log] menu.

## Chat log
![](http://static.toastoven.net/prod_contact_center/5.4-(1)_en.png)
You could check **Chat consultation logs** in this menu. If you click each chat log, **①** screen which you can view detailed information about the relevant chat consultation will be displayed. You could view or enter **customer information** and **consultation information**, and could **create ticket**, **view chat consultation history**.

You could **② search** logs and extract chat records that meet your criteria into an Excel file through **Data extraction** button.

**③ Status values** which you can view in chat logs are divided as follows:

- Processed: The case which the agent clicked the customer’s chat request, and **have replied** to the customer.
- Unprocessed: The case which the agent did not click the customer’s chat request, or did not replied to the customer. (Same with **Give up** in [Report] menu)
