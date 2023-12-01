## Storage > Backup > Console Guide

## Backup Agent
To register a backup server, agent must be installed in the server. User's domain information is required to install an agent: check domain information on the **Register Server** page.

* User's domain
```
/TCBackup/{domain-id}
```

> [Note]  
> Domain is the unit of the backup system used to manage many servers in groups.
> It is automatically created if backup service is enabled.
> To register a backup server in user's domain, enter domain information with the parameter commanding agent installation.
>

<br/>

### Security Group Configuration

To communicate with the backup server, add the following to the server security group.

| Direction | Port | Region | CIDR |
| --- | --- | --- | --- |
| Ingress/Egress | ALL TCP | KOREA (Pangyo) | 133.186.132.0/24 |
| | | KOREA (Pyeongchon) | 133.186.207.4/32, 133.186.207.5/32 |
| | | JAPAN (Tokyo) | 133.223.17.0/24 |
| Egress | 443 | KOREA (Pangyo) | 103.243.202.188/32 |
| | | KOREA (Pyeongchon) | 103.243.202.188/32 |
| | | JAPAN (Tokyo) | 119.235.231.50/32 |

<br/>

### Install Backup CLI

* **Linux**

| Region | URL |
| --- | --- |
| KOREA (Pangyo) | https://static.toastoven.net/toastcloud/sdk_download/backup/scripts/linux/bootstrap.sh |
| KOREA (Pyeongchon) | https://static.toastoven.net/toastcloud/sdk_download/backup/kr2/scripts/linux/bootstrap.sh |
| JAPAN (Tokyo) | https://static.toastoven.net/toastcloud/sdk_download/backup/jp/scripts/linux/bootstrap.sh |

```
curl {URL} | bash
```

<br/>

### Install Backup Agent

> [Caution]
> Backup registers a server with the hostname of the server where the agent is installed.
> If you register multiple servers with the same hostname within one user domain, backup may not be performed.
> Before installing the agent, make sure that the hostname is not duplicated.

Install the agent as below:

* **Linux**

```
tcbackup install {user-domain}
```

<br/>

* **Windows**

For Windows agent, download from [Downloads of NHN Cloud](https://docs.toast.com/en/Download) and install. MC Server and MC Domain are required for installation: MC Domain refers to user's domain information and MC Server requires the following:  

| Region | MC Server |
| --- | --- |
| KOREA (Pangyo) | tcbackup1.toastmaker.net |
| KOREA (Pyeongchon) | kr2-backup-mc1.cloud.toast.com |
| JAPAN (Tokyo) | tcbackup.nhn-japan.com |

<br/>

### Re-register Backup Agent
If the hostname of backup server has changed, agent needs to be re-registered. Here's the command:

* **Linux**

```
tcbackup re-register
```

<br/>

* **Windows**

Download and execute the PowerShell script as below.

[re-register.ps1](https://static.toastoven.net/toastcloud/sdk_download/backup/scripts/windows/re-register.ps1)

<br/>

### Close Backup Agent
To suspend backup for a while, you can close an agent.

* **Linux**

```
tcbackup stop
```

<br/>

* **Windows**

Right-click the backup agent icon in the system tray and press **Close**.

<br/>

### Restart Backup Agent
To restart the closed backup agent, use the following command:

* **Linux**

```
tcbackup restart
```

<br/>

* **Windows**

Execute **EMC Avamar > Client** on the start menu.

<br/>

## Register Server
Install agent in the backup server and select a server in which agent is registered from **Select Server** in **Register Server**.

<br/>

### Add Backup Plan
Multiple backup plans can be added to one server. Backup plan can be added even after completing the server registration.

> [Caution]
> So as to not put a strain on the server, backup is conducted slowly in the background.
> **If 1TB or more of bulk data** or **1 million or more of numbers of files are exceeded**when backing up, more than 3 hours can be spent, leading to backup failure.
> We recommend that you back up in serial order by dividing the paths if a backup path exceeds a standard amount.
> In case of NAS(offline) product data or large-capacity data backup, we recommend that you contact the customer service center.

* **Backup Paths**

Specify a path for backup. Make sure the path is entered correctly; otherwise, backup may fail or end up in a wrong path. When soft link is set as the backup path, only soft link file is backed up.

```
e.g)
Windows :   c:\backup
Linux   :   /home/backup
```

<br/>

* **Backup Cycle**

Cycle of backup execution: choose either daily or weekly.

<br/>

* **Backup Time**

Start time of backup: select by the hour. It is recommended to select time when file change is the least and server is idle. Actual backup start time may differ up to 1 hour, depending on the situation.

<br/>

* **Retention Cycle**

Retention period for backed up copies: choose one of 7 days, 14 days, 21 days, 30 days, 6 months(180 days), 1 year(365 days), 3 years(1095 days) or 5 years(1825 days).

<br/>

### Backup Plan List
Select the checkbox to the left of the server name in the server list and a list of backup plans for the selected server is displayed on the details screen at the bottom of the screen.

<br/>

### Retrieve Results
Click the backup path in the backup plan list to view the backup result. Backup results are aggregated within a maximum of one hour from the time of backup completion.

| Backup Result  | Description |
| --- | --- |
| Successful | Backup succeeded |
| Successful (with caution) | Backup is completed, but original file has changed during backup |
| Failed  | Backup failed |

> [Note]
> If a backup is not done within three hours, due to network status, volume of backup data, and lots of backup schedule configured to start all at once, it will be recorded as a failure.
>

<br/>

### Change of Backup Policy

Change the backup plan by clicking the **Change** button to the right of each item in the backup plan list. The items that can be changed are the `backup cycle`, `backup time`, and `retention cycle`.

<br/>

## Apply for Restoration
If the registered backup plan has been conducted more than once, the data can be requested for recovery.

* **Backup Path**

User can select one of the added backup paths.   

<br/>

* **Backup Date**

Select a date when a copy to restore was backed up. When there is no backup data since all has failed, message will show there is no data to restore.

<br/>

* **Requests**

Feel free to request for details required for restoration. Restoration can be made to the backup server, or to a new server.  

```
e.g)
Hostname of the server to recover  : backup.guide
Path to recover : /home/debian
```

<br/>

* **Contact**

Enter contact information to serve as a dialogue channel between administrator and requester for flawless restoration. Collected personal information will not be saved, to be immediately discarded when restoration is completed.

Restoration status is displayed as below:

| Status | Description |
| --- | --- |
| Received | Application for restoration has been received. |
| Processing | Operator started restoration. |
| Completed  | Restoration has been completed. |


<br/>

## Unregister Server

The registered backup plan must be deleted before unregistering the server. If there is a remaining backup plan, a message will appear and unregistering will stop.

> [Caution]
> If a server is unregistered, its retained backup data will also be deleted. If you need backup data, ask for restoration in advance and restore it to the server you want.
>

After unregistering a server, you must access the server, stop the agent, and cancel the registration of the agent. Otherwise, the server cannot be registered again. The cancellation command is as follows.

* **Linux**

```
tcbackup uninstall
```

<br/>

* **Windows**

Close the agent. To use it again, open Enable Client and enter new domain information.
