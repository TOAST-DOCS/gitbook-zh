## Network > VPN Gateway (Site-to-Site VPN) > Console User Guide

This guide describes how to use the VPN Gateway (Site-to-Site VPN) service from the console.

## Create a VPN Gateway

* Name: Enter the name of the VPN gateway to be created.
* VPC: Select the VPC in which to create the VPN gateway.
* Subnet: Select the subnet in which to create the VPN gateway.
* Description: Enter the required description.
* The network interface information of the created VPN gateway can also be found in the Network Interface menu.
* You can create one VPN gateway for each VPC.

## Modify a VPN Gateway

* You can modify the name and description.

## Delete a VPN Gateway

* You can delete the selected gateway.
* To delete a gateway, there must be no attached VPN connections.

## Create a VPN Connection

* You can create a VPN connection by selecting the tunnel options.
* It may take a few minutes to complete the creation of the VPN connection.
* When the creation is completed, the status indicator changes to `ACTIVE`.
* If there are VPN connections pending for deletion or creation, the tasks must be completed before any other VPN connections can be created.
* The range used for the VPN connection must not overlap in local and remote networks. It must not overlap with the subnet' range as well as the VPC's range.
* In the Routing menu, you must create a route so that the peer range is routed to the VPN gateway.
* Each VPN gateway can have a maximum of 10 VPN connections.
* When connecting your VPC to an on-premises network, you must use address ranges with no overlapping network addresses.
* For the peer gateway address, you cannot use the same address in duplicate.
* The local range cannot be used in duplicate within the same VPC.
* The peer range can be used in duplicate in different VPCs.

### VPN Tunnel Options

* Local Range: IPv4 CIDR range on the NHN Cloud side that is allowed for communication through VPN tunnel
    * The range of the selected subnet is entered.
* Peer Range: IPv4 CIDR range on the customer gateway (on-premises) side that is allowed for communication through VPN tunnel.
* Peer Gateway Address: Public IP address of the customer-side gateway
* IKE1 Encryption/Integrity Algorithms: Encryption and integrity algorithms allowed for the VPN tunnel for phase 1 IKE negotiation
    * (Choose one among aes192, aes256, des, 3des)-(Choose one among md5, sha1, sha256)
* IKE1 Authentication Lifetime: Lifetime of phase 1 IKE negotiation (in seconds).
    * You can specify a number between 900 and 28,800.
* Phase 1 Diffie-Hellman (DH) Group: DH group number allowed for the VPN tunnel in the phase 1 of IKE negotiation.
    * Choose one among 5, 2, 1
* IKE2 Encryption/Integrity Algorithms: Encryption and integrity algorithms allowed for the VPN tunnel for phase 2 IKE negotiation
    * (Choose one among aes192, aes256, des, 3des)-(Choose one among md5, sha1, sha256)
* IKE2 Authentication Lifetime: Lifetime of phase 2 IKE negotiation (in seconds).
    * You can specify a number between 900 and 28,800.
* IKE2 Diffie-Hellman (DH) Group: DH group number allowed for the VPN tunnel in the phase 2 of IKE negotiation.
    * Choose one among 5, 2, 1
* Bandwidth: Determine the bandwidth to use for the connection.
    * Choose 1 among 20M, 50M, 100M, and 1G
    * Indicates the outbound bandwidth.
* Pre-Shared Key: A pre-shared key (PSK) establishes an initial Internet Key Exchange (IKE) secure connection between the target gateway and the customer gateway.
    * You can use English letters, numbers, and special characters.
    * Use a value between 8 and 32 bytes.

## Modify a VPN Connection

* You can modify the name and description.

## Delete a VPN Connection

* You can delete the selected VPN connection.
* If there are VPN connections pending for deletion or creation, the tasks must be completed before any other VPN connections can be deleted.
