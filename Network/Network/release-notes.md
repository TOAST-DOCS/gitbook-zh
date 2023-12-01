## Network > Release Notes

### November 28, 2023

#### Added Features

##### Load Balancer

* Added the feature to apply subnet static routes to load balancers. You can apply static routes set on the subnet to which the load balancer belongs to load balancers as well as to instances.

##### Private DNS

* Added the Private DNS service. You can configure independent DNS for each VPC. 
  * Private DNS is only available in the Korea (Pyeongchon) region and Korea (Pangyo) region.

### August 29, 2023

#### Added Features

##### Transit Hub

* Added the Transit Hub service. The service manages VPCs through a centralized connectivity and provides routing and multicast communication between connected resources.
    * Transit Hub is only available in the Korea (Pyeongchon) and Korea (Pangyo) regions.

##### VPN Gateway

* Added the VPN Gateway feature to the Korea (Pangyo) region.

##### NAT Instance

* Added the NAT Instance feature to the Korea (Pangyo) region.

##### VPC

* Added the Routing API to Public API. See [VPC API Guide](https://docs.nhncloud.com/zh/Network/VPC/zh/public-api/).

##### Network ACL

* [Pyeongchon region, Korea]  Released Public API. See [Network ACL API Guide](https://docs.nhncloud.com/zh/Network/Network%20ACL/zh/public-api/).

### May 30, 2023

#### Feature Updates

##### Network Interface

* Improved the Network Interface UI
    * Added the search feature.
    * Improved to display device names.

### March 28, 2023

#### Added Features

##### Traffic Mirroring

* Added the Traffic Mirroring feature. Packets can be captured and routed to detection tools for purposes such as content security, threat analysis, and troubleshooting.
    * Traffic Mirroring is only available in Korea (Pyeongchon) and Korea (Pangyo) regions.

#### Feature Updates

##### VPC

* Added the VPC and VPC Subnet API to Public API. For more information, see [VPC API Guide](https://docs.nhncloud.com/zh/Network/VPC/zh/public-api/). 

##### VPC, Floating IP, Security Groups, Load Balancer

* Changed API endpoint addresses.

### January 31, 2023

#### Feature Updates

##### Colocation Gateway

* [Pyeongchon/Pangyo region, Korea] Added the feature to set a route to colocation gateway.

##### Service Gateway

* Removed the constraint where communication is only possible for service gateway within the same VPC. 
* You can use the service gateway of other VPCs via peering gateway and colocation gateway.

### November, 29, 2022

#### Added Features

##### Peering Gateway

* [Pyeongchon/Pangyo region, Korea] Added the feature to configure a route for Peering, Project peering, and Region peering.

### October 26, 2022

#### Feature Updates

##### Service Gateway

* Added a supported service
    * NCR

### June 30, 2022

#### Feature Updates

##### Service Gateway

* Added a supported service
    * CloudTrail

### May 24, 2022

#### Added Features

##### Peering Gateway

* Added the project peering feature, which allows you to connect two VPCs created in the same region but in different projects.
    * Project peering is only available in the Korea (Pyeongchon) region and the Korea (Pangyo) region.

##### VPN Gateway

* [Pyeongchon region, Korea] Added the VPN Gateway feature.

##### NAT Gateway

* [Pangyo region, Korea] Added the NAT Gateway feature.


### March 29, 2022

#### Added Features

##### VPC

* Added the service gateway feature. You can use the service gateway IP to connect to the service selected when creating the service gateway.
    * The service gateway feature is only available in the Korea (Pyeongchon) region and the Korea (Pangyo) region.
* Added the inter-region peering feature, which allows you to connect two VPCs created in different regions.
    * Inter-region peering is only available in the Korea (Pyeongchon) region and the Korea (Pangyo) region.

### January 18, 2022

#### Added Features

##### VPC

* Added the static route configuration feature to subnets. You can configure static routes to forward via DHCP to instances within a subnet.
* Added the feature to create and change a "centralized virtual routing table".

##### Network Interface

* Added the feature to create virtual IP for redundancy. You can preempt an IP to use as a virtual IP, and add a route to the IP in the routing table.
* Added the feature to disable network interface security settings so that the instance can be used as a gateway, firewall, etc.

#### Feature Updates

##### Load Balancer

* Enhanced to use TLS version 1.3 with load balancers that use the TERMINATED_HTTPS protocol.

### August 24, 2021

#### Added Features

##### DNS Plus

* Added the Create multiple record sets feature.


### April 27, 2021

#### Added Features

##### NAT instance

* [Pyeongchon region, Korea] Added the NAT Instance feature.

##### Load Balancer

* [Pyeongchon region, Korea] Physical load balancers can be created online. To learn more about the changes from the previous load balancers, see [Load Balancer Guide](https://docs.toast.com/en/Network/Load%20Balancer/en/console-guide/#difference-between-physical-load-balancers-and-regular-load-balancer).

### March 23, 2021

#### Added Features

##### NAT Gateway

* [Pyeongchon region, Korea] Added the NAT Gateway feature.

##### Load Balancer

* [Korea/Japan/United States] Added the Block Invalid Request feature.
* [Korea/Japan/United States regions] The default connection limit of newly created load balancers is changed from 2,000 to 60,000.

### February 6, 2021

#### Feature Updates

##### VPC

* [Pangyo region, Korea] Fixed the issue where the default route (local route to the whole VPC address area) of routing table is not properly applied. Previously, even subnets within the VPC same could communicate with one another only if they are all connected to the same routing table. Now, communication is possible between subnets connected to different routing tables.


### November 24, 2020

#### Feature Updates

#### Network Interface
* Added Network Interface service.

### September 22, 2020

#### Feature Updates

##### DNS Plus

* Improved the application to enable the editing of the record set type when editing a record set.

### August 25, 2020

#### Added Features

##### Network ACL

* [Pyeongchon region, Korea] Network ACL function added. Using the ACL function, you can control the access per protocol, IP, and port.

##### Load Balancer

* Public API v2 supports IP access control function. For details, refer to [Load Balancer API Guide](https://docs.toast.com/en/Network/Load%20Balancer/en/public-api/#ip-acl).

### June 23, 2020

#### Features Updates

##### VPC
* [Korea/Japan/United States] Changed the way to enter the IP of a gateway from manually typing in the address to selecting the device owning the IP from the Create Route window of a routing table. The devices that are not explicitly associated with a routing table in the subnet can also be selected.
* [Korea/Japan/United States] Changed the Internet gateway list to display the information of the associated routing table instead of the IP information. The name of the associated Internet gateway is also displayed in the Route tab of a routing table.

### May 26, 2020
#### Feature Updates

##### VPC

* Released Public API v2, which is compatible with OpenStack API.

##### Load Balancer

* The instance of a different subnet that belongs to the same VPC as Load Balancer can be registered as a member of Load Balancer. The subnet to which Load Balancer belongs and the subnet of the instance need to be connected to the routing table.
* The instance that belongs to a peer VPC can be registered as a member of Load Balancer if the VPC to which Load Balancer belongs has a peering connection. Only the instances of the subnet connected to the default routing table of the peer VPC can be connected.
* Now, the member instance of each listener can be configured differently. Previously, all the listeners needed to have the same member instance when running multiple listeners in Load Balancer.
* Released Public API v2, which is compatible with OpenStack API.

### March 24, 2020

#### Feature Updates

##### Load Balancer

* Added Certificate management through the Cert Manager service.
* By registering a certificate at Cert Manager and connecting it to the listener, you can receive an email on certificate expiration date.

### February 25, 2020

#### Feature Updates

##### Security Group

* Added "Description" entry to security group rules. You can add description for each security group rule.

### December 24, 2019

#### Added Features

##### DNS Plus

* Added GSLB (Global Server Load Balancing) to allow stable load balancing of traffic at an endpoint server.
* The GSLB domain can be configured either, according to routing rules, Disaster Recovery (DR), Random, or Global Load Balancing.
* The pool serves as a grouping element for endpoint servers at the minimum unit so as to apply the routing rule.
* Health check is conducted on a regular basis for endpoint servers included to a pool so as to support stable services. Health check is supported for HTTP/HTTPS/TCP.

#### Feature Updates

##### DNS Plus

* Updated to select user's GSLB domain for CNAME record set type, for creating/updating the record set.

### December 17. 2019

#### Feature Updates
* [Korea/Japan/US Region] Every network interface connected with an instance can be assosicated with each floating IP.

### October 29, 2019

#### Feature Updates

##### Load Balancer

* Added the feature of notification via web console, for chain certificate registration, when an individual certificate which is included in the certificate file has an invalid format.

### August 27, 2019

#### Feature Updates

##### Load Balancer

* It is available to specify TLS version to communicate with clients via TERMINATED_HTTPS load balancer.
    * For more details on the setting of load balancer in TLS version, see [user guide](https://docs.toast.com/en/Network/Load%20Balancer/en/overview/#ssltls-version-for-load-balancer).

##### DNS Plus

* Exceeded the maximum available number of record sets to be created. For each DNS zone, up to 5,000 record sets can be created.
* Modified, in the query of record set statistics for CNAME, to query A record set type along with AAAA record set type.

### June 25, 2019

#### Release of New Products

##### DNS Plus

* DNS Plus provides features for domain management.
* It is easy to configure a DNS server.

### May 30, 2019

#### Feature Updates

##### Load Balancer

* [Japan Region] IP access control is available.
    * IP-based access control is available for load balancer.
    * For more details on IP access control, see user guides.

### May 28, 2019

#### Feature Updates

##### VPC

* [Korea Region] Creating a peering can be made available again.

### April 25, 2019

#### Feature Updates

##### Load Balancer

* IP access control is available.
    * IP-based access control is available at load balancer.
    * For more details on IP access control features, see User Guide.
    * List of IPs for control has been auto-applied to the IP access control group named Default.

### December 27, 2018

#### Feature Updates

##### VPC

* Creating a new peering is not going to be provided for the time being, due to concerns for packet flooding between peered VPCs.
	Such concerns, however, are not related to communication between previously created peering, and features are provided as usual, except peering creation.

### November 27, 2018

#### Bug Fixes

##### Load Balancer

* Fixed a bug occurring when a listener is added to load balancer, in which, an instance member that is newly added to a deactivate instance is created while activated.

#### Feature Updates

##### Load Balancer

* Added the statistics feature for load balancing, with the following statistical volume provided on a chart.
    * Session count, Session increase volume of client per second, Session increase volume of instance per second, In/Out traffic volume, Number of exceptions to load balancing
    * Statistics on deleted load balancers, listeners, or members are not provided.
    * Traffic volume does not include L2, L3, and L4 headers.
    * For more details, see User Guide.


### September 20, 2018

#### Bug Fixes

##### Load Balancer

* Fixed an issue in which some listener members still remain after an instance which is registered as member of load balancer is deleted.

#### Feature Updates

##### Load Balancer

* Added dedicated load balancer services.
* Since dedicated load balancer services are created by occupying hardware resources, 1Gbps bandwidth for 48 thousand concurrent sessions are supported.

### August 28, 2018

#### Bug Fixes

##### VPC

* Fixed an issue in which deleting may be tried to VPC with subnets that have routes

#### Feature Updates

##### VPC

* Updated the maximum available numbers to create subnet, routing table, and route.
* Check the maximum available numbers to create each resource of VPC from description on the right of the popup.
    * Subnet: Available up to 10 for each VPC.
    * Routing Table: Available up to 10 for each VPC.
    * Route: Available up to 10 for each routing table.

##### Load Balancer

* For TCP or HTTPS protocol, a proxy protocol can be activated to check client IP.
* Keepalive timeout can be configured for load balancer.


### April 24, 2018

#### Bug Fixes

##### VPC

* Fixed failed access to load balancer of a peer VPC from instance of a local VPC.

#### Feature Updates

##### VPC

* You can find information of attached resources on Overview of VPC, Subnet, Routing Table, and Internet Gateway.

##### Floating IP

* Applied pagination to Floating IP list.

##### Security Group

* Added rule editing.

##### Load Balancer

* Changed the Keeaplive Timeout to 5 minutes.
* Up to 60,000 session limit can be configured for listener.

### March 22, 2018

#### Bug Fixes

##### VPC

* Fixed failure in getting an IP via DHCP when an instance is attached to a newly added subnet.
* Fixed an issue in which the same target of a previous routing policy may be entered to add a routing policy.
* Fixed infrequently failed communication of an instance associated to a floating IP with an instance located at a different subnet.

### February 22, 2018

#### Bug Fixes

##### VPC

* Fixed failed traffic from an instance associated with floating IP to a local network.

#### Feature Updates

##### Adopted VPC as Basic Model for Network

* You can use many subnets.
* A port can be created by the subnet and attached to an instance.
* More routing policies can be added.
* Added the peering feature for communication between VPCs.
* Many VPC ports may be added to or deleted from an instance.
* For more details, Overview and User Guide of VPC.


### November 23, 2017

#### Bug Fixes

##### Load Balancer
* Fixed the display of invalid connection limit for listener, when a load balancer is created.

### October 26, 2017

#### Bug Fixes

##### Load Balancer
* Fixed failure in certificate registration when a load balancer is created.

### September 21, 2017

#### Added Features

##### Added Public API

* Like Object Storage, you can also manage Compute & Network by using APIs.
* The feature is limited at the moment, but will be extended by adding more APIs.

#### Bug Fixes

* Fixed to disallow users without project admin authority to modify security group.
* Updated not to show the Network menu to users, except authorized admin users of a project.

### August 24, 2017

#### Bug Fixes

##### Load Balancer
* Fixed a bug in which the session persistence of load balancer did not show properly.

### April 20, 2017

#### Bug Fixes
##### Load Balancer
* Fixed a bug in which the popup for certificate registration is frequently missing while uploading certificate files to listener.


### March 23, 2017

#### Bug Fixes
##### Floating IP
* Fixed failed display of the "Create" button on the popup for associating with floating IP.


### February 23, 2017

#### Feature Updates

##### Load Balancer

* Updated to notify that deleting a listener is unavailable, if there is only one registered listener to a load balancer.
	  * There's no defacto change in the process: sending no notification may have been confusing to some users.
	  * The updated version now allows the user to be notified clearly that it is unavailable to delete.

##### Floating IP

* Updated to prevent a floating IP from being deleted, if it is associated with an instance or a load balancer.
	  * Previously, deleting a floating IP which is associated with an instance or a load balancer might have caused a failure to service.
	  * To prevent any potential error, the updated version disallows an associated floating IP to be deleted.
* Name Changes: 'Port' -> 'Network Interface'
	  * Name for the target of floating IP to be associated with is changed from "Port" to "Network Interface".


### January 19, 2017

#### Bug Fixes
##### Load Balancer
* Fixed the issue in which the restricted connection setting was not applied when creating a load balancer.



### December 22, 2016

#### Bug Fixes

##### Load Balancer
* Fixed failed editing of listener when the Health Check Protocol is TCP.

##### Floating IP
* Fixed failed display of the name of load balancer associated with floating IP.

##### Security Group
* Fixed an issue in which security group list disappears when a duplicate rule is added.






### December 8, 2016

#### Bug Fixes

##### Load Balancer
* Fixed failed display of Health Check URL of load balancer.
* Fixed the show of "/", instead of a registered Health Check URL, at the click of Edit Listener,








### November 29, 2016

#### Bug Fixes
##### Load Balancer
* Fixed failure in creating TERMINATED_HTTPS-type load balancers.



### November 24, 2016

#### Feature Updates
##### Load Balancer
* Updated to show the value of session limit per listener of load balancer.

#### Bug Fixes
##### Load Balancer
* Fixed failure in creating load balancers at a particular project.

### August 4, 2016

#### Feature Updates
##### Load Balancer
* Added SSL offloading of load balancer.

#### Bug Fixes
##### Load Balancer
* Fixed infrequent failure in closing when load balancer is removed.
