## Database > RDS for MS-SQL > DB Instance

## DB Instance

DB instance encompasses virtual equipment and installed Microsoft SQL Server, serving as the unit of Microsoft SQL Server provided by RDS for MS-SQL.
Direct access to a DB instance is not allowed, but access is enabled only through the port entered when creating the DB instance.
DB instances can be identified by user-specified name or automatically assigned 32-bit ID.
A DB instance name has the following constraints:

* Must be unique for each region.
* Must consist of alphabets, numbers, -, _, and . only, between 4 and 100 characters.
* Must start with a letter.

To create a DB instance, user account and password setting is required, considering the following constraints:

* User account must be between 4 and 16 characters, comprised of alphabets and numbers only, starting with a letter.
* Password must be between 8 and 128, comprised of alphabets, numbers, !, $, #, and % only.
* Password cannot include user's account name.
* Password must include at least three categories out of capital letters, small-case letters, numbers, and special characters.

### Availability Zone

RDS for MS-SQL has many availability zones under one system so as to prepare against failure in physical hardware. A failure that occurs within an availability zone does not affect other availability zones, increasing availability of the entire service. DB instances that are dispersed and created in different availability zones can communicate via network, with no charges.

> [Caution]
> You cannot change the availability zone of a DB instance that has already been created.

### Version of Microsoft SQL Server

The following versions are supported.

* SQL Server 2016 Standard (13.0.5850.14)
* SQL Server 2017 Standard (14.0.3294.2)
* SQL Server 2019 Standard (15.0.4223.1)

> [Caution]
> You cannot create a different version when restoring using a backup file since the backup files for each version are incompatible.

### DB Instance Type

Each type of DB instance has different CPU core count and memory volume.
To create a DB instance, an appropriate type must be selected depending on the database workload.

| Type    | Description |
| ------- | -------------------------------------------------|
| m2 | Configures balance between CPU and memory.   |
| c2 | Has higher performance setting for CPU. |
| r2 | Available when memory takes more volume than other resources |
| x1 | A type that supports high performance CPUs and memory. Used for services and applications that require high performance. |

You can use the web console to easily change the type of a DB instance that has already been created.

> [Caution]
> When the type of an already created DB instance is changed, the DB instance is terminated, resulting in several minutes of downtime.

### DB Instance Status

DB instance status consists of the following values, and it may change depending on the user's action and current status.

| Status    | Description |
| ------- | -------------------------------------------------|
| Available | The DB instance is stable and capable of performing other actions |
| Connection failed | Cannot access the database |
| Force restart | DB instance is being force restarted |
| Not enough storage | DB instance storage does not have enough free space |
| Creating | DB instance is being created |
| Changing | DB instance is being changed |
| Backing up | The backup of DB instance is being made |
| Deleting | DB instance is being deleted |
| Rebooting | DB instance is being rebooted |
| Recovering high availability configuration | Reconfiguring the secondary server and monitoring server of a high availability DB instance |
| Recovering the monitoring server | Reconfiguring the monitoring server of a high availability DB instance |
| Exporting backup | Exporting backup of DB instance to object storage |
| Failing over | Failover is in progress for the DB instance |
| Failed over | The DB instance is successfully failed over and stopped. |
| Migrating | Hypervisor migration is in progress |
| Error | Cannot use the DB instance due to unknown reasons |

### DB Instance Monitoring Status

DB instance monitoring status consists of the following values, and it may change depending on the user's action and current status.

| Status    | Description |
| ------- | -------------------------------------------------|
| MS-SQL monitoring always enabled | MS-SQL monitoring is enabled |
| MS-SQL monitoring disabled at specific time | MS-SQL monitoring is disabled at a specific time |
| MS-SQL monitoring disabled | MS-SQL monitoring is disabled |

### Storage Type

DB instances support two storage types: HDD or SSD.
Since each storage type provides different performance and pricing, an appropriate storage type must be selected depending on the database workload.
A storage type can be created from 20GB up to 2,000 GB.
You can use the web console to easily change the size of a storage that has already been created.

> [Caution]
> When the size of an already created storage is changed, the DB instance is terminated, resulting in several minutes of downtime.
> You cannot change the type of a storage that has already been created.

### Task Schedule Time

The time during which a scheduled task is scheduled. A scheduled task can be DB instance modification, or DB instance restart that is registered when a parameter group is changed.

> [Caution]
> The task may not be completed within the set time.
> If another task is running at the set time, the scheduled task will be retried at the scheduled time the next day.

## High Availability DB Instance

A high availability DB instance increases availability and data durability, and provides fault-tolerant database.
RDS for MS-SQL uses the mirroring function of the Microsoft SQL Server, consisting of a primary server, a secondary server, and an event monitor server, to offer high availability. The primary and secondary servers are created in different availability zones.

### Automatic Failover

A failover automatically takes place when the primary server becomes unavailable due to an unexpected failure. The failed primary server is halted to prevent split brain and the secondary server takes over the role of primary server. Applications do not have to be adjusted for this change, as the A record of the internal and external domains that are used for connection is switched from the primary server to the secondary server.
When failover is complete, high availability DB instances will disappear and the rest of DB instances are separated into two groups: the failed DB instances and the DB instances promoted due to the failure. The promoted DB instances inherit all the configurations of existing DB instances except backups. The promoted DB instances do not perform automatic backup immediately after the promotion. This is to prevent any system load due to the failover.
The DB instances with failover completed can be restarted by pressing the **Restart** button.

### Manual Failover

A high availability DB instance can be failed over manually through restart using failover. When restarting a DB instance using failover, manual failover is performed and the roles of the primary and secondary servers are switched. During failover, both primary and secondary servers will restart their Microsoft SQL Server process and their internal and external domain IPs will be changed. Connection to those servers may fail from several seconds to several minutes until the domain change is completed. Backup is performed automatically when failover is complete.

### High Availability Auto Recovery

The high availability auto recovery feature schedules a high availability reconfiguration task that runs one hour after the completion of automatic failover. The created scheduled task can be adjusted to the desired time or deleted in the **Scheduled Task** tab.

### Cautions and constraints

* You can use the high availability DB instance only if the storage backup period is at least 1 day.
* High availability configuration of different regions is not supported.
* You cannot use a secondary server for high availability for read load balancing.
* A mirroring configuration is proceeded anew when you change the name of a high availability instance's database, and the process takes a certain amount of time. You may experience performance degradation during the mirroring configuration, and the failover action may not be executed properly when a failure occurs.
* Database of high availability DB instances only supports Full Recovery Model. When change of recovery model is detected, it will be changed back to the Full Recovery Model.
* DB instances with completed failover may fail to operate or operate properly due to issues such as data loss on the account of failures.
* As the high availability feature is based on domains, if a Compute & Network service instance for a user is in a network environment where it cannot reach any DNS server, the relevant instance cannot access the DB instance through a domain and normal access will be blocked when a failover occurs.
* When a new database is created in a DB instance, it may take at least 5 minutes up to dozens of minutes for the database to be mirrored.
  * If a failover occurs before the mirroring is complete, the failover of the database won't be properly done.
* All databases of high availability DB instances operate in the same server. When a failure occurs on a specific database, all databases will fail over.
* Failover is not performed if there is no mirrored database.
* User, login, and permission of the primary server will be replicated to the secondary server.
  * Replication takes at least 10 seconds up to dozens of minutes.
  * When a failure occurs before the copying process is complete, the corrections will be lost.
* SQL Server Agent jobs cannot be replicated. When failover is complete, it needs to be created again in the promoted DB instance.
* The failover time is impacted by the recovery process; the larger the transaction, the longer the time.
* The auto failover feature will be temporarily disabled while changing a DB instance.
* Instances of which memory is less than 8GB cannot use the high availability feature.
