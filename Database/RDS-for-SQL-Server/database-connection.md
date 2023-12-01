## Database > RDS for MS-SQL > Database Connection

Access is not directly allowed to an operating system of a DB instance but is available only via such port entered when creating a DB instance.

## Domain

Once the DB instance is created, an internal domain is issued, which can be accessed through the VPC subnet. Using the floating IP will additionally issue an external domain which can be accessed externally. The format of a domain is as follows: `xxxx.yyyy.kr1.mssql.rds.nhncloudservice.com`. In `xxxx`, a random 32-character string is entered. In `yyyy`, either `internal` (for internal domains) or `external` (for external domains) is entered depending on the domain type.

> [Caution]
> The previously used domain `xxxx.yyyy.sqlserver.rds.cloud.toast.com` will be deleted on August 31, 2022.
> Please change the domain you are using to `xxxx.yyyy.kr1.mssql.rds.nhncloudservice.com`.

## Database Port

A random port between 1150 and 65535 can be specified as a database port.

> [Caution]
> When a port for the kernel, service, or an application program of Windows server is specified, database may not run properly.
> When there is a change in the database port for a created DB instance, database shall restart.
> The user's ISP may block a well-known port for security purposes. In such cases, the user might not be able to connect to the NHN Cloud's RDS and must use a different port number in that case.

## VPC Subnet

To create a DB instance, you must select the VPC subnet of the Compute & Network service of the user. Network connection is activated between a DB instance and an instance of the Compute & Network service within the same VPC subnet. DB instance is disconnected from external networks, except for the user's VPC subnet. To allow external connection, it must be associated with a floating IP.

## DB Security Group

A database security group is used to protect DB instances from other traffic. A 'Positive Security Model' is used, which allows specific traffic while blocking the other traffic. When the service is first started, a default security group is created, which blocks all incoming traffic. Therefore, even if you associate a floating IP, you cannot access immediately, and you can access only by setting the required policies. A database security group is applied equally to both external access using a floating IP and internal access using a private IP. Multiple security groups can be set for a DB instance. By creating additional security groups along with multiple policies and setting them to an instance, policies of all configured security groups are applied to the instance.

| Item        | Description                                                         |
| ----------- | ------------------------------------------------------------ |
| Direction        | Inbound refers to inflow to an instance, while outbound means outflow from instance.  |
| Ether Type  | Version of EtherType IP: specify IPv4 or IPv6.  |
| Port        | You can select one among DB port, port, or port range. <br> When set to DB port, the security group is applied to the port of the database. <br> When set to port, only one port entered is applied. <br> When you select a port range, all ports including the minimum and maximum values are applied. |
| Remote        | The range of an IP address can be specified. If the direction of the rule is 'Outbound', the destination is remote, but if it is 'Inbound', the source is remote. <br>Depending on the direction of the policy, compares whether the traffic source or destination is IP address or range.  |
| Description        | Description for a security group policy can be added.  |

If a DB security group is created with a DB port, the DB security group policy is automatically changed when the database port is changed.