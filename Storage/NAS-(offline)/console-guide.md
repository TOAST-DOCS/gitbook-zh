## Storage > NAS (offline) > Console Guide
> [Notice]
> NAS Volume can only be mounted on servers within the NHN Cloud cloud platform infrastructure.
> It is configured to communicate with private IP and is not accessible from outside.

## Apply for NAS

1. Go to **Storage > NAS (offline)** and click **Apply for Product Use**.

2. Complete application forms: 
    * Volume Name 
        * Enter a name with less than 8 characters in combination of alphabet and numbers: an actual NAS Volume is created with this name.
    * VPC & Subnet
        * NAS will be connected to this network.
    * Application Size (GB) 
        * NAS requires at least 300 GB. Choose a value between 300GB and 10,000GB with the slider.  
    * Use Snapshot  
        * Snapshot data will take space in NAS volume. To perform recovery through snapshot, please contact administrator. 

3. When NAS Volume is completely created, an email notification will be sent.  

## Increase or Delete Volume 

You can increase or delete NAS volume.
Increasing is available only when the NAS status is **Application Received**, or **In Service**.  

To increase volume:

1. Click **Increase Volume**.  

2. Enter volume information to add in the dialogue box and click **Confirm**. 

To delete:

1. Click **Delete Volume**.

3. Check  volume information to delete in the dialogue box and click **Confirm**.


## Attach Volume 

### Install nfs Package

* Debian, Ubuntu: nfs-common, rpcbind  
  ```
  sudo apt-get install nfs-common rpcbind
  ```
* CentOS: nfs-utils, rpcbind  
  ```
  sudo yum install nfs-utils rpcbind
  ```

### Run rpcbind Service 

```
sudo service rpcbind start
```

### Mount NAS Volume 

```
sudo mount -t nfs {nas source} {mount point}
```

* NAS Source: NAS volume information 
  e.g) 192.168.0.241:/data
* Mount Point: Directory to mount NAS volume   
  e.g) /mnt
