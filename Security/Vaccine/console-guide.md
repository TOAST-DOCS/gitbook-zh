## Security > Vaccine > Console Guide 

This document describes the procedure of enabling and disabling vaccine agents, and how to apply the service. 

## Enabling Vaccine Agents 

Import vaccine installation script, for each OS of an instance image. 

![vaccine_01_en_2021_06.png](https://static.toastoven.net/prod_vaccine/vaccine_01_en_2021_06.png)

### For Linux 

1\. To copy installation script, click  **Copy Clipboard**.

2\. Access terminal for an instance to install. 

3\. At the administrator's authority, create and execute an agent script. 

* Create a script by using vi editor. 
* Change authority of the script file which is created. 
* Execute file. 
```
[root@vaccine-test ~]# cd ~
[root@vaccine-test ~]# vi agent.sh
[root@vaccine-test ~]# chmod 744 agent.sh
[root@vaccine-test ~]# ./agent.sh
/tmp/DownloadInstallAgentPackage: OK
Downloading agent package ...
curl https://106.249.21.88:4119/software/agent/RedHat_EL7/x86_64/ -o /tmp/agent.rpm --insecure --silent
Installing agent package ...
Preparing...                          ################################# [100%]
Updating / installing...
   1:ds_agent-10.0.0-2775.el7         ################################# [100%]
Starting ds_agent (via systemctl):  [  OK  ]
HTTP Status: 200 - OK
Activation will be re-attempted 30 time(s) in case of failure
dsa_control
HTTP Status: 200 - OK
Response:
Attempting to connect to https://106.249.21.88:4120/
SSL handshake completed successfully - initiating command session.
Connected with (NONE) to peer at 106.249.21.88
Received a 'GetHostInfo' command from the manager.
Received a 'GetHostInfo' command from the manager.
Received a 'SetDSMCert' command from the manager.
Received a 'SetAgentCredentials' command from the manager.
Received a 'GetAgentEvents' command from the manager.
Received a 'GetInterfaces' command from the manager.
Received a 'GetAgentEvents' command from the manager.
Received a 'GetAgentStatus' command from the manager.
Received a 'GetAgentEvents' command from the manager.
Received a 'GetHostMetaData' command from the manager.
Received a 'SetSecurityConfiguration' command from the manager.
Received a 'GetAgentEvents' command from the manager.
Received a 'GetAgentStatus' command from the manager.
Command session completed.
[root@vaccine-test ~]#
```

### For Windows 

1\. Copy console script. 

2\. Access terminal for an instance to install.  

3\. At the administrator's authority, create and execute agent script. 

* Create a script file by using text editor, like memo pad. 
* Enable the **Command Prompt** (cmd) window, at the administrator's authority.   
* Execute in the format of powershell -file "file path/file name". 
```
Microsoft Windows [Version 6.3.9600]
(c) 2013 Microsoft Corporation. All rights reserved.

C:\Users\Administrator>powershell -file "agent.ps1"


    Directory: C:\Users\Administrator\AppData\Roaming\Trend Micro\Deep Security Agent


Mode                LastWriteTime     Length Name
----                -------------     ------ ----
d----      2018-06-05   2:37 pm            installer
Recording has started. The output is C:\Users\Administrator\AppData\Roaming\Trend Micro\Deep Security Agent\installer\dsa_deploy.log.
2:37:23 pm - DSA download started
2:37:23 pm - Download Deep Security Agent Package
https://106.249.21.88:4119/software/agent/Windows/x86_64/
2:37:24 pm - Downloaded File Size:
13897728
2:37:24 pm - DSA install started
2:37:24 pm - Installer Exit Code:
0
2:37:32 pm - DSA activation started
HTTP Status: 200 - OK
Activation will be re-attempted 30 time(s) in case of failure
dsa_control
HTTP Status: 200 - OK
Response:
Attempting to connect to https://106.249.21.88:4120/
SSL handshake completed successfully - initiating command session.
Connected with AES256-SHA256 to peer at 106.249.21.88
Received a 'GetHostInfo' command from the manager.
Received a 'GetHostInfo' command from the manager.
Received a 'SetDSMCert' command from the manager.
Received a 'SetAgentCredentials' command from the manager.
Received a 'GetAgentEvents' command from the manager.
Received a 'GetInterfaces' command from the manager.
Received a 'GetAgentEvents' command from the manager.
Received a 'GetAgentStatus' command from the manager.
Received a 'GetAgentEvents' command from the manager.
Received a 'GetHostMetaData' command from the manager.
Received a 'SetSecurityConfiguration' command from the manager.
Received a 'GetAgentEvents' command from the manager.
Received a 'GetAgentStatus' command from the manager.
Command session completed.
Recording is suspended. The output is C:\Users\Administrator\AppData\Roaming\Trend Micro\Deep Security Agent\installer\dsa_deploy.log.
2:38:29 pm - DSA Deployment Finished

C:\Users\Administrator>
```
### Start Service 

![vaccine_02_en_20210628.png](https://static.toastoven.net/prod_vaccine/vaccine_02_en_20210628.png)

Click Refresh to find information of agents that are installed on the list of current status. 
Click **Start Service** to start the service. 

## Disabling Vaccine Agents 

![vaccine_03_en_210628.png](https://static.toastoven.net/prod_vaccine/vaccine_03_en_210628.png)

1\. Suspend Web Console Service 

* Click **Close Service** to stop vaccine service. 
### For Linux 
* Access instance and delete vaccine agent. 
    * CentOS: Execute rpm -e ds_agent 
    * Debian/Ubuntu: Execute apt-get remove ds-agent 

### For Windows 
* Access instance and delete vaccine agent. 
    * On Programs and Features, delete **Trend Micro Deep Security Agent**.

## Applying Vaccine Service 

### Guide for File Restoration 
1\. File Restoration 

* [Download](http://static.toastoven.net/prod_vaccine/QFAdminUtil_win32.zip) a restoration tool. 
* Decompress QFAdminUtil_win32.zip, which is downloaded, on Windows. 
* Execute QDecrypt.exe and open isolated files and restore them.  

2\. Location of Isolated Files 

* Linux : /var/opt/ds_agent/guest/0000-0000-0000/quarantined
* Windows : C:\ProgramData\Trend Micro\AMSP\quarantine
    * If you cannot find isolated files, click **Folder and Search Option** in **Computer** or **File Search**,  <br>deselect **Hide Protected Operating System Files** from the **View** tab, and select **Show Hidden Files, Folders and Drives**. 
      

### Temporary Solution Guide 

1\. Delete 

#### For Linux 
* Access instance and delete vaccine agent. 
    * CentOS: Execute rpm -e ds_agent 
    * Debian/Ubuntu: Execute apt-get remove ds-agent 

#### For Windows 
* Access instance and delete vaccine agent. 
    * On Programs and Features, delete **Trend Micro Deep Security Agent**.

2\. Deliver Analysis Files 

* To analyze causes to prevent recurrence, collect files of the following paths and request to Customer Center for analysis.  
    * Linux
        * Execute /opt/ds_agent/dsa_control -d 
        * Request for analysis of /var/opt/ds_agent/diag/random 10-digit numbers.zip file 
    * Windows
        * Execute C:\Program Files\Trend Micro\Deep Security Agent\dsa_control -d 
        * Request for analysis of C:\Program Files\Trend Micro\Deep Security Agent\diag\random 10-digit numbers. zip file 
* To analyze in more details, when an issue occurs, you may perform debugging first and request for more created files.

### User Guide for Image Replication 

This guide regards to using vaccines for the creation of private image-based instances, including vaccine agents. 

* Access instance, and install each script by creation or execution. 
* Following the guide to enable vaccine agents, click Refresh and **Start Service** on the service page. 

※ Caution 

* Change Appkey of "group:Appkey" in the script, into that of **URL & Appkey** on the service page. 
* For unwanted replication instances, it is recommended to delete installed agents so as not to waste unnecessary resources.   
* After 'Start Service', the service status immediately enables 'Close Service', but vaccines start to operate in no more than 10 minutes, like the initial installation.  

1\. Agent Script for Linux


```
touch /etc/use_dsa_with_iptables

IP=`ifconfig eth0 | grep -w -o '[0-9]\{1,3\}\.[0-9]\{1,3\}\.[0-9]\{1,3\}\.[0-9]\{1,3\}' | head -1`
uuidInfo=`curl -s 169.254.169.254/openstack/latest/meta_data.json | python -c 'import json,sys;obj=json.load(sys.stdin);print (str(obj["uuid"])+":"+str("user_metadata.server_group" in obj["meta"]))'`
/opt/ds_agent/dsa_control -r
/opt/ds_agent/dsa_control -a dsm://106.249.21.88:4120/ "group:앱키" "displayname:$IP" "description:$uuidInfo"
```

2\. Agent Script for Windows 

```
$idx=(Get-WmiObject -Class Win32_IP4RouteTable | where { $_.destination -eq '0.0.0.0' -and $_.mask -eq '0.0.0.0'} | Sort-Object metric1).interfaceindex[0]

$IP=((Get-WmiObject win32_networkadapterconfiguration | where { $_.interfaceindex -eq $idx} | select ipaddress)| findstr .*[0-9].\.).Split(",")[0].Split("{")[-1].Split("}")[0]
$uuid=((invoke-webrequest -uri 169.254.169.254/openstack/latest/meta_data.json -UseBasicParsing).content | convertfrom-json).uuid
$as="user_metadata.server_group" -in ((invoke-webrequest -uri 169.254.169.254/openstack/latest/meta_data.json -UseBasicParsing).content | convertfrom-json).meta.psobject.properties.name
$uuidInfo=$uuid+":"+$as`

& $Env:ProgramFiles"\Trend Micro\Deep Security Agent\dsa_control" -r
& $Env:ProgramFiles"\Trend Micro\Deep Security Agent\dsa_control" -a dsm://106.249.21.88:4120/ "group:앱키" "displayname:$IP" "description:$uuidInfo"
```
※ Script must be created in batch file (.bat) for execution. 

### User Guide for Auto Scale 
Regarding the use of vaccines by auto scale, contact Customer Center.   

## Operational Inquiries 

### Inquiries 

1\. Handling exceptions for particular files and folders 
2\. Failure in agent installation 
3\. Detecting vaccine events 
4\. Wrong report of normal files and restorations 
5\. Solutions to abnormal instance operations due to vaccine issues, and cause analysis 

### To Inquire 

1\. To Inquire: Go to **Customer Center > 1:1 Inquiry**
2\. Business Hours: 9 to 6, weekdays

