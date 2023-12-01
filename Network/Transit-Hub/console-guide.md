## Network > Transit Hub > Console User Guide

This guide describes how to use the Transit Hub service from the console.

## Manage

Manage **Transit Hub** settings.

### Create Transit Hub

To create a transit hub, use the following steps.

1. Go to **Network > Transit Hub > Manage**.
2. Click **Create Transit Hub** to display the creation screen.
3. On the creation screen, enter the information about the Transit Hub.
    * Name: Enter a name for the transit hub.
    * Description: Describe the description of the transit hub.
    * Multicast support: Check if multicast communication is required.
    * Attach default routing table: When **attachment** is created, it automatically is attached to the default routing table.
    * Default routing table propagation: Automatically add the CIDR setting value of VPC related to **attachment** to the default routing table as a routing rule.
> [Caution]
> * You cannot change multicast support, default routing table attachment/propagation settings.
> * Default routing table is created only when one or more of the default routing table attachments or default routing table propagation is selected.

### Modify Transit Hub

A transit hub can be modified as follows. You can only change the name and description.

1. Go to **Network > Transit Hub > Manage**.
2. Select a transit hub that you want to modify from the list on the screen.
3. Click **Modify Transit Hub** to display the modification screen.
4. On the modification screen, make changes to an item.

### Delete Transit Hub

To delete a transit hub, use the following steps.

1. Go to **Network > Transit Hub > Manage**.
2. Select a transit hub that you want to delete from the list on the screen.
3. Click **Delete Transit Hub** to delete.

### Share with another project

Share a transit hub with another project. In another project, you can create **Attachment** to the shared transit hub.<br>
To share Transit Hub, use the following steps.

1. Go to **Network > Transit Hub > Manage**.
2. Select a transit hub that you want to share from the list on the screen.
3. Click **Share with Another Project**, and on the share screen, enter the tenant ID of the other party that you want to share with.
> [Note] How to check out the **tenant ID of another project. <br>
> [Note] If you do not have access to another project, obtain a tenant ID from the administrator of the project.
> 1. Access the console screen of the project.
> 2. Go to **Network > VPC > Management**.
> 3. Select one of the VPCs that appears in the screen list.
> 4. Copy the ID value shown in **Basic Information > Tenant ID.

## Attach

Manage **attachment** that defines the relationship between transit hubs and other resources.

### Create Attachment

To create **attachment**, use the following steps.

1. Go to **Network > Transit Hub > Attach**.
2. Click **Create Attachment** to display the creation screen.
3. On the creation screen, enter the information about the **attachment**.
    * Name: Enter a name of the **attachment**.
    * Description: Describe the description of **attachment**.
    * Transit hub type: Select **general transit hub** created by the same project or **shared transit hub** shared by another projects.
    * Transit hub: Select a **transit hub** where the **attachment** will be created.
    * Resource type: Select a resource type.
    > [Note] Currently, only VPC can be selected as the resource type.
    * Resource: Select a resource that is related to **attachment**.
    > [Note] Since only VPC can be selected as the resource type, only the VPC list is automatically output.
    * Subnet: Select a subnet where the **network interface** of the **attachment** is created.

### Modify Attachment

Attachment can be modified as follows. You can only change the name and description.

1. Go to **Network > Transit Hub > Attach**.
2. Select **attachment** you want to modify from the list on the screen.
3. Click **Modify Attachment** to display the modification screen.
4. On the modification screen, make changes to an item.

### Delete Attachment

To delete **attachment**, use the following steps.

1. Go to **Network > Transit Hub > Attach**.
2. Select **attachment** you want to delete from the list on the screen.
3. Click **Delete Attachment** to delete.

## Routing Table

Manage the **Routing Table** settings on the Transit Hub.

### Create Routing table

To create a **routing table**, use the following steps.

1. Go to **Network > Transit Hub > Routing Table**.
2. Click **Create Routing Table** to display the creation screen.
3. On the creation screen, enter the information about the routing table.
    * Name: Enter a routing table name.
    * Description: Describe the description of a routing table.
    * Transit hub: Select a **transit hub** where you want to create the routing table.

### Modify Routing Table

Routing table can be modified as follows. You can only change the name and description.

1. Go to **Network > Transit Hub > Routing Table**.
2. Select a **routing table** you want to change from the list on the screen.
3. Click **Modify Routing Table** to display the modification screen.
4. On the modification screen, make changes to an item.

### Delete Routing Table

To delete **routing table**, use the following steps.

1. Go to **Network > Transit Hub > Routing Table**.
2. Select a **routing table** you want to delete from the list on the screen.
3. Click **Delete Routing Table** to delete.

### Manage Routing Table

Check the basic information for the selected **routing table** and manage the packet handling rules and settings associated with routing.

#### Basic Information

You can check the basic information for the selected routing table.

#### Routing Association

Manage **routing association** that defines the relationship with the **attachment** for routing table to receive packets.

##### Create Routing Association

To create **routing association**, use the following steps.

1. Go to **Network > Transit Hub > Routing Table > Routing Association**.
2. Click **Create Routing Association** to display the creation screen.
3. On the creation screen, enter the information about **Routing Association**.
    * Attach: Select **attachment** for a routing table to receive packets.
    > [Note] One **attachment** on a Transit Hub can only create one **routing association** on a routing table.

##### Delete Routing Association

To delete **routing association**, use the following steps.

1. Go to **Network > Transit Hub > Routing Table > Routing Association**.
2. Select **routing association** you want to delete from the list on the screen.
3. Click **Delete Routing Association** to delete.
   
#### Routing Propagation

You can automatically create a **routing rule** in the **routing table** that manages the outbound policy for packets. Manage **routing propagation**, which defines the relationship with **attachment** to automatically create **routing rules**.
> [Caution]
> * If a **routing rule** with the same band as the CIDR to be propagated already exists, the **routing rule by routing propagation is not automatically registered.
>     * **Routing propagation** that fails automatic **routing rule** registration changes its status to ERROR. Appropriate action is required, such as reviewing the CIDR and recreating **routing propagation** or using manual setting of **routing rules**.
> * Even if **routing propagation** is added for two or more **attachments** with the same network bandwidth (CIDR), routing rules are automatically registered only for the first routing propagation created in the same way as above.

##### Create Routing Propagation

To create **routing propagation**, use the following steps.

1. Go to **Network > Transit Hub > routing table > Routing Propagation**.
2. Click **Create Routing Propagation** to display the creation screen.
3. On the creation screen, enter the information about **Routing Propagation**.
    * Attach: Select **attachment** that automatically creates a routing rule for routing table to receive packets.
    > [Note] One **attachment** in a transit hub can create up to one **routing propagation** per routing table.

##### Delete Routing Propagation

To delete **routing propagation**, use the following steps.

1. Go to **Network > Transit Hub > routing table > Routing Propagation**.
2. Select **Routing Propagation** you want to delete from the list on the screen.
3. Click **Delete Routing Propagation** to delete.
> [Caution] When deleting **routing propagation**, Routing Rule that was automatically added will be deleted together.

#### Routing Rule

Manage **routing rules** that handle the outbound rules of packets from the routing table.
> [Note] **Routing Rule** cannot be added if Routing Rule in the same band as the CIDR to be propagated already exists.

##### Create Routing Rule

To create **routing rule** , use the following steps.

1. Go to **Network > Transit Hub > Routing Table > Routing Rule**.
2. Click **Create Routing Rule** to display the creation screen.
3. On the creation screen, enter the information about **routing rule**.
    * Target CIDR: Enter the destination network band for the routing policy.
    > [Note] The priority of **routing rules** in the routing table is determined by the Longest Pre-fix Matching result of CIDR set in the routing rule.
    * Attach: Select **attachment** for routing table to receive packets.

##### Delete Routing Rule

To delete **routing rule**, use the following steps.

1. Go to **Network > Transit Hub > Routing Table > Routing Rule**.
2. Select **routing rule** you want to delete from the list on the screen.
3. Click **Delete Routing Rule** to delete.

## Multicast

Manage the **Multicast settings** on Transit Hub.
> [Caution] **Multicast Domain** cannot be created if **Multicast Support** is not selected on Transit Hub and all multicast-related features are unavailable to use.

### Create Multicast Domain

To create **multicast domain**, use the following steps.

1. Go to **Network > Transit Hub > Multicast**.
2. Click **Create Multicast Domain** to display the creation screen.
3. On the creation screen, enter the information about multicast domain.
    * Name: Enter the name of multicast domain. 
    * Description: Describe the description of multicast domain.
    * Transit hub: Select a **transit hub** where you want to create multicast domain.

### Modify Multicast Domain

Multicast domain can be modified as follows. You can only change the name and description.

1. Go to **Network > Transit Hub > Multicast**.
2. Select **multicast domain** you want to modify from the list on the screen.
3. Click **Modify Multicast Domain**  to display the modification screen.
4. On the modification screen, make changes to an item.

### Delete Multicast Domain

To delete **Multicast domain**, use the following steps.

1. Go to **Network > Transit Hub > Multicast**.
2. Select **multicast domain** you want to delete from the list on the screen.
3. Click **Delete Multicast Domain** to delete.

### Manage Multicast

Check basic information for the selected **multicast domain** and manage the packet handling policy and settings associated with the multicast.

#### Basic Information

You can check the basic information for the selected multicast domain.

#### Multicast Association

Manage **multicast associations** join subnets of VPC-type **attachments** to multicast networks in multicast domains.
> [Note]
> * Only **attachment** of VPC type is available on multicast association.
> * **Attachment** created in other project by transit hubs shared with other projects cannot be used in multicast association.
> * One subnet is only available to use on one **multicast association** throughout the entire **NHN Cloud**.This means that one **subnet** can only be attached to one **multicast domain**.

##### Create Multicast Association

To create **multicast association**, use the following steps.
1. Go to **Network > Transit Hub > Multicast > Multicast Association**.
2. Click **Create Multicast Association** to display the creation screen.
3. On the creation screen, enter the information about **multicast association**.
    * Attach: Select **attachment** to join the multicast network in multicast domain.

##### Delete Multicast Association

To delete **multicast association**, use the following steps.
1. Go to **Network > Transit Hub > Multicast > Multicast Association**.
2. Select **Multicast Association** you want to delete from the list on the screen.
3. Click  **Delete Multicast Association** to delete.

#### Multicast Group

**Network interfaces** to participate in multicast communication provided by the **multicast domain** are managed as a **multicast group**. By configuring the **multicast group**, **network interfaces** with the same group IP address perform multicast communication with each other.<br>
> [Note] Only **Network Interface of VM Instance can be added as a multicast group.

##### Create Multicast Group

To create **Multicast group**, use the following steps.

1. Go to **Network > Transit Hub > Multicast**.
2. Click **Create Multicast Group** to display the creation screen.
3. On the creation screen, enter the information about multicast domain.
    * Multicast association: Select **multicast association**.
    * Network interface: Select **network interface**.
    * Group IP Address: Enter the multicast IP address.
    > [Note]
    > * Must be entered in the range of 224.0.0.0/4.
    > * 221.0.0.1 cannot be entered.  
    * Type: Choose between member and source
        * Member<br>
          Receive multicast packets whose destination is the group IP address.<br>
          **Network interface** specified as a source in the same group cannot be specified as a member.
        * Source<br>
          Send multicast packets whose destination is the group IP address.Only one **network interface** can be specified as a source for each **group IP address**.<br>
          **Network interface** specified as a source in the same group cannot be specified as a member.

##### Delete Multicast Group

To delete **multicast group**, use the following steps.

1. Go to **Network > Transit Hub > Multicast > Multicast Group**.
2. Select **multicast group** you want to delete from the list on the screen.
3. Click **Delete Multicast Group** to delete.

## Shared Transit Hub

If you have shared transit hubs owned by other projects, you can check the list of **shared transit hubs**.
> [Note] You can only check the list and the information of the selected item, and there is no setting available.
