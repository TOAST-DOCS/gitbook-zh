## Security > Security Advisor > Overview

Security Advisor checks the security setting status of NHN Cloud organization and project resources created by customers and provides recommendations. <br> You can utilize our recommended guides for a secure cloud environment.<br>Security Advisor is activated on a project basis, and activating the service in a specific region also activates the service in all other regions.<br>However, since the cloud services provided are different for each region, the inspection target and scope may vary.

## Main Features
* Inspects the governance settings of NHN Cloud organizations and applies recommended actions to improve the security of your cloud environment.
* Checks long-term idle accounts in a NHN Cloud project and provides recommendations.
* Checks security groups to confirm the security rules applied to instances.
* Inspects access settings to RDS and blocks unnecessary access.
* Provides periodic auto inspection and sends the result via email.

## Target Resources and Supported Region
### Supported Range for Selected Inspection per Region
|Category|Supported Region|
|---|---|
|Inspection Items by organization|Korea (Pangyo) region, Korea (Pyeongchon) region, Japan (Tokyo) region, and USA (California) region|
|Inspection Items by project|Korea (Pangyo) region, Korea (Pyeongchon) region, and Japan (Tokyo) region|

### Target Resources in Project Inspection Item for Selected Inspection Items
|Category&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;|Inspection Item|Target Resources|Notes|
|---|---|---|---|
|Project &nbsp;&nbsp;&nbsp;&nbsp;&nbsp; |Security Groups|Instance, Security Groups|Database Instance and NKS clusters are excluded|
|Project &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;|Database Security Groups|Database Instance(MS-SQL Instance, MySQL Instance, PostgreSQL Instance, CUBIRD Instance, MariaDB Instance, Tibero Instance, Redis Instance), Security Groups|
|Project &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; |RDS Access Control &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;|RDS for MySQL, RDS for MariaDB, RDS for MS-SQL|Inspection is only available in Korea (Pangyo) region because RDS for MariaDB and RDS for MS-SQL are available in the Pangyo region.|

## Roles for Project Members

Security Advisor is a project service.
Project managers can grant roles to NHN Cloud members or IAM members registered in the project.

|Service|Role|Description |
|---|---|---|
|Security Advisor|ADMIN|You can manage all services of Security Advisor.<br> Create, Read, Update, Delete the Security Advisor service<br><br>You can use all the features provided by the Security Advisor service.<br>- View dashboard, save to Excel<br>- Selected inspection, view inspection item basic information, view detected resources, selected exception of detected resources, view excepted resources, disable exception of resources<br>- Result reception settings, auto inspection settings|
||PERMISSION|You can enable or disable the Security Advisor service.<br>- Service Enable, Disable|
||VIEWER|You can check the Security Advisor service inspection results.<br>- View dashboard, download Excel<br>- View inspection item basic information, view detected resources, view excepted resources<br>\* The 'Settings' screen is not provided for the VIEWER role.|

## Service Usage Procedures
### Service Activation Procedure
Log in to NHN Cloud with an account that has permissions to activate services. In the Security category, click Security Advisor to enable the service.
![Image 1](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_securityadvisor/overview_en_01.png)

### Service Deactivation Procedure
Log in to NHN Cloud with an account that has permissions to activate services. Click the gear icon next to the project name to go to **Project Management**.
Click **Disable** for Security Advisor from **Services in Use** to terminate the service.
![Image 2](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_securityadvisor/overview_en_02.png)
