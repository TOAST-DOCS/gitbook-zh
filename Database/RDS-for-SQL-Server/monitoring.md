## Database > RDS for MS-SQL > Monitoring

You can monitor performance metrics of a DB instance, as well as various events that occurred in each DB instance, backup, parameter group, or security group.

## Server Dashboard

Server Dashboard helps to visualize performance metrics on a chart. Metrics are collected at every minute and retained for up to 5 years. Metric data are collected by the average of 5 minutes, 30 minutes, 2 hours, or 1 day. Each collecting unit provides different retention period like below:

| Collecting Unit | Retention Period |
| --- | --- |
| 1 minute | 7 days |
| 5 minutes | 1 month |
| 30 minutes | 6 months |
| 2 hours | 2 years |
| 1 day | 5 years |

A chart can be arranged in a desired layout, and you can create multiple layouts and manage them for your purpose.

### Layout

To view a chart, you need to configure a layout first. A layout consists of multiple charts and stores the position and size of each chart.
RDS for MS-SQL provides two default layouts, **Basic system metrics** and **Basic SQL server metrics**. Default layouts cannot be modified or deleted by users.

### Chart

You can view various performance metrics of DB instances in chart format. The format of chart is different for each performance metric.
In addition to the basic system metrics, the performance metrics provided by `sys.dm_os_performance_counters` of SQL Server are provided as charts.

| Chart | Metric (Unit) | Note |
| --- | --- | --- |
| CPU Usage | cpu used (%) | |
| CPU Details | cpu user (%)<br> cpu system (%)<br> cpu interrupt (%)<br> cpu privileged (%)<br> cpu processor (%) | |
| Memory Usage | memory used (%) | |
| Memory Details | memory used (bytes)<br> memory free (bytes) | |
| Memory Page Details | pages (count)<br> page read (count)<br> page write (count) | |
| Memory Page Fault | page faults (count) | |
| Memory Pool Page | memory pool paged (bytes) <br> memory pool nonpaged (bytes) | |
| Memory Standby Cache Details | core (bytes)<br> normal priority (bytes)<br> reserve (bytes) | |
| Memory Cache Fault | cache faults (count) | |
| Memory Transition Fault | transition faults (count) | |
| Memory Demand Zero Fault | zero faults (count) | |
| Swap Usage | swap used (%) | |
| Swap Usage Amount | swap used (bytes)<br> swap total (bytes) | |
| Disk Usage | storage used (%) | |
| Disk Transfer | disk read (bytes)<br> disk write (bytes) | |
| Disk Queue Length | queue length (count) | |
| Disk Free | disk free (bytes) | |
| Disk Time Details | disk time (%)<br> disk idle (%)<br> disk read (%)<br> disk write (%) | |
| Disk Split IO | split io (counts) | |
| Network Transfer | nic incoming (bytes)<br> nic outgoing (bytes) | The basic network data transfer used by Windows occurs. |
| Network Transfer Rate (pps) | nic incoming (pps)<br> nic outgoing (pps) | The basic network data transfer used by Windows occurs. |
| Network Discarded Packet | nic incoming (pps)<br> nic outgoing (pps) | |
| Network Error Packet | nic incoming (pps)<br> nic outgoing (pps) | |
| Batch requests/sec | Batch requests/sec (count) | |
| Buffer cache hit ratio | Buffer cache hit ratio (%) | |
| Checkpoint pages/sec | Checkpoint pages/sec (count) | |
| Errors/sec | Errors/sec (count) | |
| Full Scans/sec | Full Scans/sec (count) | |
| Latch Waits/sec | Latch Waits/sec (count) | |
| Lazy writes/sec | Lazy writes/sec (count) | |
| Lock Waits/sec | Lock Waits/sec (count) | |
| Number of Deadlocks/sec | Number of Deadlocks/sec (count) | |
| Page Life Expectancy | Page life expectancy (seconds) | |
| Page Lookups/sec | Page lookups/sec (count) | |
| SQL Compilations/sec | SQL Compilations/sec (count) | |
| SQL Re-Compilations/sec | SQL Re-Compilations/sec (count) | |
| Transactions/sec | Transactions/sec (count) | |
| User Connections | User Connections (count) | |
| Database Connection Status | Database Connection Status | Connection unavailable: 0, Connection available: 1 |
| System Context Switch | context switches (count) | |
| System Process | processes (count) | |
| System Call | system call (count) | |
| System Uptime | uptime | |
| System Thread | treads (count) | |
| Process Handle | sql server (count)<br> sql server vss (count) | |
| Process Processor Time | sql server (%)<br> sql server vss (%) | |
| Process Thread | sql server (count)<br> sql server vss (count) | |
| Process Private Memory Size | sql server (bytes)<br> sql server vss (bytes) | |
| Process Virtual Memory Size | sql server (bytes)<br> sql server vss (bytes) | |
| Process Working Set Memory Size | sql server (bytes)<br> sql server vss (bytes) | |


## Notification Group

You can receive notifications on performance metrics through notification group.
On the notification group, set the monitoring target instance and the user group to be notified.
On the monitoring settings, set the threshold and condition of performance metrics for which you want to receive notifications.
When the configured metrics meet the condition in the monitoring settings, notification is sent to the associated user group.
Depending on the notification type set on the notification group, the notification is sent as an SMS or email.

### Monitoring Settings

The monitoring settings consist of items, comparison method, threshold, and duration. Duration is important in the monitoring settings. Duration is used to specify as a condition the time for which the threshold specified by the monitoring target is reached and such state is maintained. For example, if the CPU usage threshold is over 90% and the duration is 5 minutes, the users in the user group is notified when the CPU usage of the server linked to the notification group is over 90% for over 5 minutes. If the CPU usage is over 90% but falls below 90% within 5 minutes, the notification is not sent.

## User Group

Users who receive notifications can be managed in groups. The notification target must be registered as a project member.
If the users in the user group are excluded from the project members, they will not be notified even if they belong to the user group.

> [Caution] If there is no mobile phone information because a user did not complete real-name verification, the user will not receive SMS notifications.

## Event

An event refers to an important event caused by RDS for MS-SQL or by a user. An event consists of the event category, date and time of occurrence, original source, and message. Events can be viewed on the web console, and you can receive notification of event occurrences by email, SMS, or webhook through subscription. The event categories and possible events are as follows.

| Event Category | Event Code | Event Message |
| --- | --- | --- |
| DB_INSTANCE | DB_INSTANCE_CREATE_START | Creating DB instance started |
| DB_INSTANCE | DB_INSTANCE_CREATE_END | Creating DB instance completed |
| DB_INSTANCE | DB_INSTANCE_CREATE_FAIL | Creating DB instance failed |
| DB_INSTANCE | DB_INSTANCE_SERVER_CREATE_START | Creating DB instance server started |
| DB_INSTANCE | DB_INSTANCE_SERVER_CREATE_END | Creating DB instance server finished |
| DB_INSTANCE | DB_INSTANCE_SERVER_CREATE_FAIL | Creating DB instance server failed |
| DB_INSTANCE | DB_INSTANCE_BACKUP_START | Backup of DB instance started |
| DB_INSTANCE | DB_INSTANCE_BACKUP_END | Backup of DB instance completed |
| DB_INSTANCE | DB_INSTANCE_BACKUP_FAIL | Backup of DB instance failed |
| DB_INSTANCE | DB_INSTANCE_BACKUP_TO_OBS_START | Backup of DB instance to object storage started |
| DB_INSTANCE | DB_INSTANCE_BACKUP_TO_OBS_END | Backup of DB instance to object storage finished |
| DB_INSTANCE | DB_INSTANCE_BACKUP_TO_OBS_FAIL | Backup of DB instance to object storage failed |
| DB_INSTANCE | DB_INSTANCE_LOG_BACKUP_FAIL | Backup of DB instance log failed |
| DB_INSTANCE | DB_INSTANCE_DELETED | DB instance deleted |
| DB_INSTANCE | DB_INSTANCE_DELETED_FAIL | Deleting DB instance failed |
| DB_INSTANCE | DB_INSTANCE_RESTORE_START | Restoring DB instance started |
| DB_INSTANCE | DB_INSTANCE_RESTORE_END | Restoring DB instance completed |
| DB_INSTANCE | DB_INSTANCE_RESTORE_FAIL | Restoring DB instance failed |
| DB_INSTANCE | DB_INSTANCE_MODIFY_START | Modifying DB instance started |
| DB_INSTANCE | DB_INSTANCE_MODIFY_END | Modifying DB instance completed |
| DB_INSTANCE | DB_INSTANCE_MODIFY_FAIL | Modifying DB instance failed |
| DB_INSTANCE | DB_INSTANCE_MODIFY_SECURITY_GROUP_START | Changing DB instance security group started |
| DB_INSTANCE | DB_INSTANCE_MODIFY_SECURITY_GROUP_END | Changing DB instance security group completed |
| DB_INSTANCE | DB_INSTANCE_MODIFY_SECURITY_GROUP_FAIL | Changing DB instance security group failed |
| DB_INSTANCE | DB_INSTANCE_REBOOT_START | Restarting DB instance started |
| DB_INSTANCE | DB_INSTANCE_REBOOT_END | Restarting DB instance completed |
| DB_INSTANCE | DB_INSTANCE_REBOOT_FAIL | Restarting DB instance failed |
| DB_INSTANCE | DB_INSTANCE_FORCE_RESTART | DB instance force restart |
| DB_INSTANCE | DB_INSTANCE_RECOVER_HA_START | DB instance high availability configuration recovery started |
| DB_INSTANCE | DB_INSTANCE_RECOVER_HA_END | DB instance high availability configuration recovery completed |
| DB_INSTANCE | DB_INSTANCE_RECOVER_HA_FAIL | DB instance high availability configuration recovery failed |
| DB_INSTANCE | DB_INSTANCE_RECOVER_WITNESS_START | DB instance monitoring server recovery started |
| DB_INSTANCE | DB_INSTANCE_RECOVER_WITNESS_END | DB instance monitoring server recovery completed |
| DB_INSTANCE | DB_INSTANCE_RECOVER_WITNESS_FAIL | DB instance monitoring server recovery failed |
| DB_INSTANCE | DB_INSTANCE_RESTORE_FROM_OBS_START | Restoring backup from object storage started |
| DB_INSTANCE | DB_INSTANCE_RESTORE_FROM_OBS_END | Restoring backup from object storage completed |
| DB_INSTANCE | DB_INSTANCE_RESTORE_FROM_OBS_FAIL | Restoring backup from object storage failed |
| DB_INSTANCE | DB_INSTANCE_HYPERVISOR_MIGRATION_START | Hypervisor migration started |
| DB_INSTANCE | DB_INSTANCE_HYPERVISOR_MIGRATION_END | Hypervisor migration completed |
| DB_INSTANCE | DB_INSTANCE_HYPERVISOR_MIGRATION_FAIL | Hypervisor migration failed |
| DB_INSTANCE | DB_INSTANCE_CHANGE_HA_START | DB instance high availability configuration change started |
| DB_INSTANCE | DB_INSTANCE_CHANGE_HA_END | DB instance high availability configuration change completed |
| DB_INSTANCE | DB_INSTANCE_CHANGE_HA_FAIL | DB instance high availability configuration change failed |
| DB_INSTANCE | DB_INSTANCE_CHANGE_PASSWORD_START | Changing DB instance password started |
| DB_INSTANCE | DB_INSTANCE_CHANGE_PASSWORD_END | Changing DB instance password completed |
| DB_INSTANCE | DB_INSTANCE_CHANGE_PASSWORD_FAIL | Changing DB instance password failed |
| DB_INSTANCE | DB_INSTANCE_CHANGE_PORT_START | Changing DB instance port started |
| DB_INSTANCE | DB_INSTANCE_CHANGE_PORT_END | Changing DB instance port completed |
| DB_INSTANCE | DB_INSTANCE_CHANGE_PORT_FAIL | Changing DB instance port failed |
| DB_INSTANCE | DB_INSTANCE_CHANGE_PARAMETER_GROUP_START | Changing DB instance parameter group started |
| DB_INSTANCE | DB_INSTANCE_CHANGE_PARAMETER_GROUP_END | Changing DB instance parameter group completed |
| DB_INSTANCE | DB_INSTANCE_CHANGE_PARAMETER_GROUP_FAIL | Changing DB instance parameter group failed |
| DB_INSTANCE | DB_INSTANCE_CHANGE_FLAVOR_START | Changing DB instance type started |
| DB_INSTANCE | DB_INSTANCE_CHANGE_FLAVOR_END | Changing DB instance type completed |
| DB_INSTANCE | DB_INSTANCE_CHANGE_FLAVOR_FAIL | Changing DB instance type failed |
| DB_INSTANCE | DB_INSTANCE_CHANGE_STORAGE_SIZE_START | Changing DB instance storage size started |
| DB_INSTANCE | DB_INSTANCE_CHANGE_STORAGE_SIZE_END | Changing DB instance storage size completed |
| DB_INSTANCE | DB_INSTANCE_CHANGE_STORAGE_SIZE_FAIL | Changing DB instance storage size failed |
| DB_INSTANCE | DB_INSTANCE_CHANGE_FLOATING_IP_START | Changing started for whether to use DB instance floating IP |
| DB_INSTANCE | DB_INSTANCE_CHANGE_FLOATING_IP_END | Changing completed for whether to use DB instance floating IP |
| DB_INSTANCE | DB_INSTANCE_CHANGE_FLOATING_IP_FAIL | Changing failed for whether to use DB instance floating IP |
| DB_INSTANCE | DB_INSTANCE_CHANGE_BACKUP_CONFIG_START | Changing DB instance backup setting started |
| DB_INSTANCE | DB_INSTANCE_CHANGE_BACKUP_CONFIG_END | Changing DB instance backup setting completed |
| DB_INSTANCE | DB_INSTANCE_CHANGE_BACKUP_CONFIG_FAIL | Changing DB instance backup setting failed |
| DB_INSTANCE | DB_INSTANCE_STATUS_CHANGED_TO_AVAILABLE | DB instance changed to available status |
| DB_INSTANCE | DB_INSTANCE_STATUS_CHANGED_TO_FAIL_TO_CONNECT | Unable to connect to the DB instance |
| DB_INSTANCE | DB_INSTANCE_STATUS_CHANGED_TO_STORAGE_FULL | Not enough DB instance storage |
| DB_INSTANCE | DB_INSTANCE_STATUS_CHANGED_TO_ERROR | DB instance error |
| DB_INSTANCE | HA_AUTOMATIC_FAILOVER_START | High availability DB instance auto failover started |
| DB_INSTANCE | HA_AUTOMATIC_FAILOVER_END | High availability DB instance auto failover completed |
| DB_INSTANCE | HA_AUTOMATIC_FAILOVER_FAIL | High availability DB instance auto failover failed |
| DB_INSTANCE | HA_AUTOMATIC_PROMOTE_END | Promoting high availability DB instance completed |
| DB_INSTANCE | HA_AUTOMATIC_PROMOTE_FAIL | Promoting high availability DB instance failed |
| BACKUP | BACKUP_START | Backup started |
| BACKUP | BACKUP_END | Backup completed |
| BACKUP | BACKUP_FAIL | Backup failed |
| BACKUP | BACKUP_DELETED | Backup deleted |
| BACKUP | BACKUP_EXPORT_OBS_START | Exporting backup to object storage started |
| BACKUP | BACKUP_EXPORT_OBS_END | Exporting backup to object storage finished |
| BACKUP | BACKUP_EXPORT_OBS_FAIL | Exporting backup to object storage failed |
| PARAMETER_GROUP | PARAMETER_GROUP_CREATED | Parameter group created |
| PARAMETER_GROUP | PARAMETER_GROUP_MODIFIED | Parameter group modified |
| PARAMETER_GROUP | PARAMETER_GROUP_DELETED | Parameter group deleted |
| DB_SECURITY_GROUP | DB_SECURITY_GROUP_CREATED | DB security group created |
| DB_SECURITY_GROUP | DB_SECURITY_GROUP_MODIFIED | DB security group modified |
| DB_SECURITY_GROUP | DB_SECURITY_GROUP_DELETED | DB security group deleted |
| NOTIFICATION_GROUP | NOTIFICATION_GROUP_EVENT_CREATED | DB instance event occurred |

### Subscribing Events

You may subscribe events by each category, code or source. When subscribed by event category, for example, you'll be notified on every event code included in the event category. If the range of notification is too broad, subscription may be divided by event code or source.

Only project members can be selected as notified users. By default, event notification is sent by email, and if mobile phone number is registered from real-name verification, additional notification is sent via SMS. In addition to email and SMS, with webhook registration, HTTP request is sent on a pre-defined form, which is like below.

#### Method, URL
```
POST {URL for user-registered webhook}
Content-Type: application/json;charset=UTF-8
```

#### Request Body
```json
{
    "name": "Name of Event Subscription",
    "source": "Event Source",
    "sourceId": "ID of Event Source",
    "category": "Event Category",
    "code": "Event Code"
}
```
