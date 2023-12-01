## Network > VPN Gateway (Site-to-Site VPN) > Overview

This service provides the capability to establish an encrypted network connection between a VPC and a customer's on-premises network.

## Concepts

* Local gateway: A resource allocated to VPN tunnel configuration in NHN Cloud.
* Remote gateway: A resource allocated to VPN tunnel configuration on the on-premises side.
* VPN tunnel: An encrypted link that is configured between a remote gateway and a local gateway.

## Main Features

* Enables an encrypted network connection between a VPC and a customer’s on-premises network.
* The bandwidth (guaranteed on an outbound basis) can be selected among 20M, 50M, 100M, and 1G.
* The encryption algorithm can be selected among AES, DES, and 3DES.
* The integrity algorithm can be selected among MD5, SHA1 and SHA256.
* Network ACLs can be applied.
* This service is currently only available in the Korea (Pyeongchon) region, and will be supported by other regions gradually.

## Restrictions

* IPv6 traffic is not supported for VPN connections. Only IPv4 traffic is supported.
* When connecting your VPC to an on-premises network, you must use address ranges with no overlapping network addresses.
* You can create a VPN gateway per VPC and set the bandwidth to be used for the VPC. All VPN connections belonging to one VPN gateway use the same bandwidth. For example, if you create the first VPN connection at 20 Mbps, any additional VPN connections you create in that VPC will use 20 Mbps of bandwidth. To use a different bandwidth, you can create the first VPN connection in a different VPC by specifying the desired bandwidth (select among 20M, 50M, 100M, or 1G).
* You can create one VPN gateway for each VPC.
* Each VPN gateway can have a maximum of 10 connections.
* In a VPC connected with VPN, it is not supported to access other networks using peering or access other networks or services through other gateways.
