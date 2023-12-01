## Security > Webshell Threat Detector > Console Guide

This document explains how to enable a checking agent. 

## Enable Agent

Select an instance OS to import an agent execution script.

![WebshellThreatDetector_01_20221129.png](https://static.toastoven.net/prod_webshellthreatdetector/WebshellThreatDetector_en_01_20221129.png)

### For Linux

1. Click Copy Clipboard to copy the installation script.

2. Access the instance terminal for installation.

3. Create and execute the agent script as administrator.

* Acquire the root permission.
* Create a script using editors such as the vi editor.
* Change the permission of the created script file.
* Execute the file.
```
[root@centos7 ~]# cd ~
[root@centos7 ~]# sudo su
[root@centos7 ~]# vi installer.sh
[root@centos7 ~]# chmod 744 installer.sh
[root@centos7 ~]# ./installer.sh
Configure the work directory..
Configure the data directory..
Install Finished!
```

## Disable Agent

1. Cpoy the delete script.

```
pkill pfcont && pkill pfmont && pkill pfrmont && pkill pfinstor && pkill pfsder && pkill acontroller && rm -rf /nwtd
```

2. Access the instance terminal for deletion.

3. Execute the delete script as administrator.

* End the Webshell Threat Detector process.
* Delete the Webshell Threat Detector file.

4. To make sure that it is deleted normally, check if the /nwtd directory exists.

## Operational Inquiry

### Inquiry Item

1. To inquire about failure in agent installation

2. To report on misuse of check results

### How to Inquire

1. Procedure: go to **Customer Center > 1:1 Inquiry**

2. Response Time: Business Hours 09:00～18:00
