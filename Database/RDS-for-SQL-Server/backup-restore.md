## Database > RDS for MS-SQL > Backup and Restoration

## Backups

You can prepare for restoring database of a DB instance. RDS for MS-SQL executes backups sequentially for each database.
Backups can be manually created at a time of choice or automatically created by setting backup retention period.
You can perform restoration to a particular time by using manually created backups, or to a point in time during backup retention period.

> [Caution]
> While backup is underway, performance may be degraded due to the backup.
> To minimize the impact on service, backup is recommended while service workload is low.

### Backup Storage

RDS for MS-SQL stores all backup files at a separate object storage.
All auto backup files are deleted when the DB instance is deleted, whereas manual backup files are permanently stored in the object storage, unless the user explicitly delete them.

### Auto Backup

By setting up the backup retention period for more than a day, auto backup is enabled and executed during specified backup execution period. Unless the backup execution time is specified, daily auto backup shall be executed when there is the minimum workload. By specifying backup time, auto backup is executed within 15 minutes from the specified time. Auto backups can be saved for up to 30 days. When the backup retention period setting is N/A, auto backup is disabled, deleting all auto backup files saved from backup storage. With the auto backup disabled, restoration to a point of time during backup retention period becomes unavailable, while restoration to a particular time with manual backup only is available.

> [Caution]
>If auto backup is enabled, make sure to use the `Full` database recovery model.
>If the `Simple` or `Bulk logged` model is used, it will be forced to use the `Full` recovery model and perform a full backup again from the beginning.

### Log Backup

By setting up the backup retention period of DB instances for more than a day, log backup is enabled and executed every 5 to 10 minutes.
If log backup fails and the log is lost, point-in-time restoration from the point of loss to the point of new auto backup creation is not possible. If log backup fails, the auto backup button is activated on the DB instance list screen, and you can click the button to proceed with auto backup.
Restoration is possible from the point after the specified backup execution time or auto backup is completed by clicking the auto backup button.

### Manual Backup

Regardless of auto backup enabling, a backup to a time of choice can be manually executed. To create a manual backup, it must be named to meet the following rules:

* Must be unique for each region.
* Must consist of alphabets, numbers, -, _, and . only, between 4 and 100 characters.
* Must start with a letter.

## Restoration

RDS for MS-SQL helps to restore to a backup moment by using backup files, or to a point in time. With restoration, a new DB instance is created, which is irrelevant to an existing DB instance. Since restored DB instance regards to database only, a new setting of a parameter and a security group is required. Setting of a new parameter group is available, but it is recommended to restore with the parameter group from the backup time.

### Restoration with Backup

With manual or auto backups, DB instance can be restored. Restoration time depends on the backup size, from a few minutes to tens of minutes.
It is recommended to apply the same type of backup DB instance and parameter group for restoration.

> [Caution]
> If a DB instance has many databases, each in big size, backup time might be different for each.
> Since backup is executed for each database one by one, recovery is not ensured for all databases from a certain backup time.

### Point-in-Time Restoration during Backup Retention Period

If auto backup is enabled for a DB instance, it is available to restore data to a time point during retention period. To enable a point-in-time restoration, log backup is required. RDS for MS-SQL executes auto log backups at every 5 minutes, and stores them at a backup storage.
If the auto backup is enabled, it detects the database created by user every 5 minutes and performs a full backup separately. Therefore, if users try to roll back to the time the DB was just created, the newly created DB won't be recovered properly. Using a reliable DB instance without separate modification, a point in time which as at least five minutes after the time of creation must be selected.

## Export and Import Backup using Object Storage

Users can back up to their DB instance object storage or recover a backup file from the user object storage as a DB instance.

> [Cautions]
> You can export and import backups to and from object storages in the same region.

### Differential Backup to Object Storage

You can export backup files that have already been backed up or export backup files simultaneously with differential backup. Backup files are exported to each database, but can be exported to NHN Cloud object storage that has been set up to use Object Storage REST API.

To export backups to object storage, you must create a container in which backup files will be stored. After creating the container, you can export backups by using **Backup to Object Storage** in the web console.
If the backup file exceeds 1GB, it is uploaded in multiple parts.

### Restore from Backup in Object Storage

For only compatible Microsoft SQL Server backup files, object storage can be used to recover to the DB instance of RDS for MS-SQL.
After uploading external backup files to NHN Cloud object storage that has been set up to use REST API, you can restore backup files by using **Restore from Backup in Object Storage** in the web console.

If the backup file to restore exceeds 5GB, it must be uploaded in multiple parts. For more information, please refer to [Multi-part upload](https://docs.toast.com/ko/Storage/Object%20Storage/ko/api-guide/#_53).
Restoration is performed for each individual database, and can be performed onto an existing DB instance. If there is not enough space in the DB instance's storage, restoration may fail.

You can also restore differential backups created based on full backups by selecting **Yes** for whether to restore differential backups and adding a differential backup path.

> [Caution]
> Since the `master` database is not recovered, the user login information in the recovered database is edited so that only users entered at the time of DB creation have access to it.

If you are restoring to a high availability DB instance, high availability configuration starts as soon as the database is restored.