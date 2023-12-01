## Network > Service Gateway > Overview

The **Service Gateway** service allows you to use the **services** of NHN Cloud outside the **VPC** without using a **floating IP** and having the traffic going through the internet. The **service** selected when **creating the service gateway** and the automatically assigned IP maintain a one-to-one relationship. In the **VPC**, you can use the target **service** safely through the NHN Cloud's internal network using the **service gateway**'s IP address.

### Main Features

* You can connect to the services of NHN Cloud provided by the service gateway from your VPC without going through the internet.
* You can use only the services provided in the service list when creating a service gateway.
* The IP address of the service gateway is connected one-to-one with the service selected when creating the service gateway.
* When the VM Instance in the VPC communicates with the IP address of the service gateway, it communicates with the service associated with the service gateway.
* This service is currently only available in the Korea (Pangyo) and Korea (Pyeongchon) regions, and will be supported by other regions gradually.

### Provided Services

If you need to access NHN Cloud's services from a VM Instance in the VPC without going through the internet, create a service gateway by selecting a service provided by the service gateway.
For details on how to use each service, refer to the [**User Guide**](https://docs.toast.com/zh/TOAST/zh/Overview/). The services provided will be increased gradually.

* IaaS API Identity is a service required to use object storage. For more detailed description, refer to [**User Guide > Storage > Object Storage > API Guide > Authentication Token Issuance**](https://docs.toast.com/zh/Storage/Object%20Storage/zh/api-guide/).
