## Compute > GPU Instance > Console User Guide

## Enabling GPU Instances  

To enable a GPU instance, you must request for creating one from Compute > GPU Instance.

**Click Select Service > GPU Instance.**

![en_GPU_Instance_activation_1_modify.png](http://static.toastoven.net/prod_gpu/en_GPU_Instance_activation_1_modify.png)  

**Click OK for Enable Service.**

![en_GPU_Instance_activation_2_modify.png](http://static.toastoven.net/prod_gpu/en_GPU_Instance_activation_2_modify.png)



## Request for Creating GPU Instances 

**Go to Compute > GPU Instance, and click Apply (1:1 Inquiries).**

![en_GPU_Instance_apply_1_modify.png](http://static.toastoven.net/prod_gpu/en_GPU_Instance_apply_1_modify.png)


**Fill out the title and content of your inquiry and click OK.**

![en_GPU_Instance_apply_2_modify.png](http://static.toastoven.net/prod_gpu/en_GPU_Instance_apply_2_modify.png)


**Requirements for the Request for Creating GPU Instances **

```
Enter relevant information to enable GPU.  
=============================================================================
* User's TOAST ID Email (e.g. email@toast.com):

* User's Project ID (e.g. ae1bfd024d8841a295988638d90979a4):
   Available at Network > VPC > Subnet > Project ID.

* Availability Area (e.g. pub-a):
  Select either pub-a or pub-b.

* Name of Instance to Install (e.g. gpu-instance-001):
  Enter less than 20 characters: only English, numbers, '-', and '.' are available.

* Type and Volume of Instance (e.g. 1 g2.c8m96 instance):
   g2.c8m96: 8 Core, Memory 96 GB + 1 GPU
   g2.c16m192 : 16 Core, Memory 192 GB + 2 GPUs

* Name of Keypair for the Instance to Install (e.g. gpu_connect_key):
   Create one, if there is no keypair you need.

* Block Storage Type and Volume of Instance (GB) (e.g. HDD 100 GB):
   Block Storage Type: Select either SSD or HDD.
   Volume can be created between 20 GB and 1000 GB.

* Information of Subnet to be Connected with  (e.g. Default Network / 7245176d-1402-47fa-87a6-2c2eafe8807b)
  Network Name/ID/Multiple number is available

=============================================================================


To enable GPU Instances, refer to the following information.   
=============================================================================
* Service is not readily available but may be enabled after consultation. Consultation may take 2 to 3 days. 

* GPU instances are installed on Ubuntu 18.04. 

* The IP is automatically assigned. 

* Once a GPU instance is created, it is guided by email. 

=============================================================================
```

* User's TOAST ID Email: Enter ID information to be requested for creating a GPU instance.  
* User's Project ID: Available at **Network > VPC > Subnet > Project ID**, as below.
* Availability Area: Select either pub-a or pub-b.  
* Name of Instance to Install: Enter less than 20 characters: only English, numbers, '-', and '.' are available. 
* Type of GPU Instance and Number of Instances 

| Instance Type | GPU Count | Core Count | Memory Volume (GB) |
| --- | --- | --- | --- |
| g2.c8m96 | 1 | 8 | 96 |
| g2.c16m192 | 2 | 16 | 192 |

* Name of Key pair for Instance to Install: Create one, if there is no key pair you need. 
* Block Storage Type and Volume of Instance (GB): Select either HDD or SSD for the type, and the volume can be created between 20 GB and 1000 GB. 
* Information of Subnet to be Connected with: Go to **Network > VPC > Subnet > Subnet Name, CIDR** and find.
* For more details regarding creating instances, see [Instance Overview](http://docs.toast.com/ko/Compute/Instance/ko/overview/).


![en_GPU_Instance_subnetID_1](http://static.toastoven.net/prod_gpu/en_GPU_Instance_subnetID_1.png)


**Information for Enabling GPU Instances **

* Service is not readily available, but may be enabled after consultation. Consultation may take 2 to 3 days. 

* GPU instances are installed upon Ubuntu 18.04.

* The IP is automatically assigned. 

* Once a GPU instance is created, it is guided by email.  


## Accessing GPU Instances 

After instance is created, go to the instance by using SSH.  
The instance must be associated with floating IP, while TCP port 22 (SSH) must be allowed by the security group. 

Use SSH Client and configured key pair to access the instance. 
For more details regarding SSH connection, see [Guide for SSH Connection](https://docs.toast.com/ko/Compute/Instance/ko/overview/#linux).



## Finding GPU Information 

```
# Find GPU Information
shell > nvidia-smi
```

![GPU_assign_1.png](http://static.toastoven.net/prod_gpu/GPU_assign_1.png)


* GPU: 0 (1 GPU assigned)
* Name: Tesla V100-SXM2 (GPU model)
* Persistence_mode: On (the persistence mode is enabled)
* Temp: 30 C (current GPU temperature)
* Pwr Usage/Capacity: 36W / 300W (current electricity usage/ maximum capacity)
* Memory-Usage: 32480MiB (maximum memory assigned to GPU)
* GPU-Util: 0% (usage rate of GPU Util)

## Differences between General and GPU Instances 

* For GPU instances, specifications cannot be changed.  
