## Storage > Backup > Overview

Backup is a service that makes copies and keeps them safely to prepare for data loss due to security threats, user's operational mistakes, storage device failure, natural disasters, and so on. You can also restore data using the backup copy.

NHN Cloud Backup service uses both full and incremental backup methods. Initially, the service performs backup of all data in the path registered by the user. Afterwards, only incremental backups are performed using variable-length deduplication technology, which can minimize backup data by removing duplicates. This shortens backup times and reduces network usage. Data is encrypted and transferred securely to backup storage.

NHN Cloud Backup service provides a web console environment where you can easily register backup policies, view backup history, and request restoration. Backup results are collected daily and reported to the user's email.

## Service Features
* Supports various operating systems.
* Optimized for virtualization environment.
* Performs backup without interrupting the service.
* Provides a user-defined backup policy that allows you to set the backup cycle, backup time, and retention cycle.

### Backup Cycle
You can choose between 1-day interval and 7-day interval.

### Backup Time
You can select a backup start time by the hour. It is recommended to select the time when the number of file change is minimal and the server is idle. Actual backup start time may vary by up to 1 hour, depending on the situation.

### Retention Cycle
You can select a retention cycle of 7 days, 14 days, 21 days, 30 days, 6 months (180 days), 1 year (365 days), 3 years (1095 days), or 5 years (1825 days).

### View Results
Users can view backup results on the web console within 30 minutes from the backup completion time. If the backup fails, the details of failure are reported to the user's email. If the backup is not performed up to 3 hours, it is logged as a failure.

## Supported Operating Systems
NHN Cloud supports the following operating systems:

| OS | Hardware Architecture | Supported Version | Supported Configuration |
| --- | --- | --- | --- |
| CentOS | x64 | 7.8 | ext2, ext3, ext4, xfs |
| Ubuntu | x64 | 18.04 LTS<br/>20.04 LTS | ext2, ext3, ext4 |
| Debian | x64 | 9, 10 | ext2, ext3, ext4 |
| Rocky | x64 | 8.5 | xfs |
| Windows Server | x64 | 2012 R2 STD<br/>2016 STD<br/>2019 STD | NTFS |

## Application Procedure for Restoration
Once the user applies for restoration, the operator confirms the application and proceeds with the restoration. For smooth processing, the operator may contact you. The restoration application process is as follows:

1. Select a server to restore.
2. Click **Apply for Restoration** in the **Restoration** tab.
3. Fill in the content and click **Apply**.

If you apply for restoration, it will be completed within 3 business hours. If it is made after business hours, it will be completed the next day.

Restoration is available only during business hours (10 am to 6 pm on weekdays), and the operator proceeds with the restoration after confirmation.

## Charges
When a server is registered, a basic monthly fee is charged. Additional fees are charged depending on the number of registered servers and storage usage. The default specification for the monthly subscription is two servers and 100 GB of storage usage.

## Reference
### Backup Software
DELL EMC AVAMAR

### Backup Program Installation Location
* Linux : /usr/local/avamar
* Windows : C:\Program Files\avs

### Backup Program Daemon (Process) Information
* Linux : /usr/local/avamar/bin/avagent.bin
* Windows : Avamar Backup Client
