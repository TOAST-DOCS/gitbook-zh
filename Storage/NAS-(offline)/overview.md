## Storage > NAS (offline) > Overview

With NAS, data sharing becomes easier by connecting a shared storage to an instance.   

## Glossary 

### NAS (Network Attached Storage)

A file-level data storage device connected to a computer network which provides control of access by heterogeneous clients.  

### Volume

A logical unit of data storage space of NAS. 
An instance can mount NAS volume to save or read data.   

### Snapshot

A backup of NAS volume as reference of data duplication of a time. With snapshot, data can be recovered to a particular point in time.   
NAS service allows saving a snapshot per day, for three times, and data may be reverted back to records of three days before.     
However, saving snapshots may not be used, as it uses a part of NAS volume. 


## Features 

### Sharing

NAS volume can be mounted to more than one instance.
Supported Protocol: NFS v3(Linux)

### Convenient 

No additional file system configuration is required as file-level volume is mounted.

### Flexible 

Even while NAS volume is used, storage volume can be scaled up or down.  

### Secure   

Accessing NAS volume is made via a project network, which is isolated from a different project network. 

