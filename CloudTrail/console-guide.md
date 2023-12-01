
## CloudTrail > Console Guide

### Getting Started
CloudTrail is a service provided by default when an organization is activated. If an organization has already been created, no further action is necessary.
CloudTrail can be used by selecting it from Select Service after an organization is created.

![cloudtrail_01](https://static.toastoven.net/prod_cloudtrail/IMG01_EN.png)

### List

The following screen appears when the CloudTrail service is selected.

![cloudtrail_02](https://static.toastoven.net/prod_cloudtrail/IMG02_EN.png)

User events are logged in the organization and users can view them.

### Searching and sorting

![cloudtrail_03](https://static.toastoven.net/prod_cloudtrail/IMG03_EN.png)

1. Searches for projects. They can be searched by name unit only.
2. Searches by source (the location where event occurred).
    - ADMIN_CONSOLE: Events occurred in the admin console
    - API: Events occurred within the system
        - [Note] Events such as batch tasks, scheduled tasks, and alarms are logged.
    - USER_CONSOLE: Events occurred in the console of an insider member
3. Searches by service.
    - Multiple services can be searched for.
    - [Note] Service is the unit of the NHN Cloud service.
4. Searches by event.
    - Multiple events can be searched for.
5. Searches for users.
6. Searches for requests and response values.
7. Specifies the scope of a search. The filter options are 24 hours, 1 week, 2 weeks, and 3 months. Users can enter a filter value as well.
    - [Note] Events are retained up to 3 months.
8. Specifies the list display unit. You can display 25, 50, or 100 items at once on the screen.

---

* The sort feature can only be used in the time item.

### Detailed view

![cloudtrail_04](https://static.toastoven.net/prod_cloudtrail/IMG04_EN.png)

When a column is selected, the column is expanded and event details are displayed.

Shows requests and response results so that users can see the history of attempted requests.

### Log Save/Download Settings
You can save/download user event logs written within the organization through an external object storage.
Click the **Log Save/Download Settings** button and enable/disable it in the dialog box.

![cloudtrail_07](https://static.toastoven.net/prod_cloudtrail/IMG07_EN.png)

* The following describes how to save/download logs using [NHN Cloud Object Storage](/Storage/Object%20Storage/en/Overview/)
    * **Access key** and **Secret key** can be verified with **Register and View EC2 Credential** using [AWS S3 API](https://github.com/TOAST-DOCS/CloudTrail/blob/de2ee3d8ad32a2eb189d15d5b266d0eac6e3642f/Storage/Object Storage/ko/s3-api-guide/#_1).
    * **Bucket name** is the name of the object storage container where logs will be saved.
    * **Endpoint** and **Region** are information that manages the object storage where logs will be saved. For more information, see [Amazon S3 Compatibility API Guide - AWS SDK](/Storage/Object%20Storage/en/s3-api-guide#aws-sdk).
    * Once setup is complete, logs will begin to be saved in the object storage.
    * Saved logs can be viewed two to two and a half hours after being uploaded in the object storage.
    * After three or more failed upload attempts, the saved authentication information will be disabled. The details will be sent to the email address registered in the **Receive Result (email)** field.
    * **Alert External Log Tampering** is a feature to notify users by email when the logs in Object Storage are arbitrarily modified or deleted.
    * When external logs are tampered, the email in **Receive Results (Email)** is notified.
    * **Alert External Log Teampering** is only available in Object Storage from NHN Cloud.
        * **Tenant ID**, **Password** can be found in **Set API Endpoint** of Object Storage where logs are stored.
        * For **User ID**, enter the email of the NHN Cloud user with permissions to the Object Storage.
