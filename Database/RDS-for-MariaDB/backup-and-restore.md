## Database > RDS for MariaDB > Backup and Restoration

## Backup

You can prepare in advance to recover the database of DB instance in case of failure. You can perform backups through the web console whenever necessary, and you can configure to perform backups periodically. During backup, storage performance of the DB instance on which the backup is performed can be degraded. To avoid affecting service, it is better to perform back up at a time when the service is under low load. If you do not want the backup to degrade performance, you can use a
high-availability configuration or perform backups from read replica.

> [Note]
> High availability DB instances are backed up on the extra master without compromising the master's storage performance.

### Auto Backup

If you set the backup archive period for a DB instance to 1 or more days, automatic backups are enabled, and backups are performed at the specified backup run time. Automatic backups have the same life cycle as DB instances. When DB instance is deleted, all archived automatic backups are deleted. When you create DB instance, you can set the settings for automatic backups, and you can also change the backup settings for the DB instance that is already created. Automatic Backup supports the
following settings.

**Backup Retention Period**

* Sets the time period for storing backups on storage. It can be kept for up to 730 days, and if the backup archive period changes, the expired automatic backup files will be deleted immediately.

**Use Table Lock**

* `FLUSH TABLES WITH READ LOCK` ets whether the syntax is enabled or disabled.
* Table lock enables the `FLUSH TABLES WITH READ LOCK` syntax periodically during backups to ensure consistency in backup data. If `FLUSH TABLES WITH READ LOCK` syntax fails to run, the backup will fail.
* You can disable table locking if the DML query load is high during a backup. If you do not use table lock, `FLUSH TABLES WITH READ LOCK` syntax will not run, so a high DML load does not cause the backup to fail. However, backups without table lock may not ensure consistency of backup data and do not support point-in-time restoration.

** Query Latency Dash Time (second)**

* When using table lock, set the wait time for `FLUSH TABLES WITH READ LOCK` syntax. `FLUSH TABLES WITH READ LOCK` syntax will wait for the query latency dash time. It can be set from 0 to 21,600 seconds. Longer settings reduce the likelihood of backup failures due to DML query load, but may result in longer overall backup times.

**Back Retry Times**

* You can set the backup to retry if it fails due to DML query load or for other various reasons. You can retry maximum 10 times. Depending on the backup run time setting, you might not try again because there are still more retries.

**Backup Run Time**

* Allows you set the time that the backup takes place. It consists of the backup start time, the backup window, and the backup retry expiration time. You can set the backup run time multiple times so that it does not overlap. Performs backup at any point in the backup window based on the start time of the backup. The backup window is not related to the total running time of the backup. Backup time is proportional to the size of the database and the service load. If the backup fails, retry the
  backup based on the number of backups retries if it does not exceed the backup retries times.

Auto backup name is given in the format of `{DB instance name} yyyy-MM-dd-HH-mm`.

> [Caution]
> If you are unable to perform backup, for example, if the previous backup does not end, the backup may not be performed.

### Manual Backup

If you need to permanently store databases at a certain point in time, you can perform backups manually from the web console. Unlike automatic backups, manual backups are not deleted, unless you explicitly delete the backup, as they are when DB instance is deleted Manual backups require you to enter a name for the backup and have the following limitations.

* Backup name has to be unique for each region.
* Backup names are alphabetic, numeric, and - _ between 1 and 100 Only, and the first character has to be an alphabet.

### Backup Storage and Pricing

All backup files are uploaded to the internal object storage and stored. For manual backups, they are stored permanently until you delete them separately, and object storage charges are incurred depending on the backup capacity. For automatic backups, it is stored for the set retention period and charges for the full size of the automatic backup file, which exceeds the storage size of the DB instance. If you do not have direct access to the internal object storage where the backup file is
stored, and when you need backup file, you can export the backup file to the object storage in NHN Cloud.

### Export Backup

You can export backup files stored on internal object storage to user object storage on NHN Cloud. You can also export a manual or automatic backup file, or export the backup file to user object storage at the same time as you perform the backup. While exporting backups, network performance of the source DB instance may degrade.

> [Note]
> For manual backups, if the source DB instance that performed the backup was deleted, you cannot export the backup.

## Restoration

Backups allow you to restore data to any point in time. Restoration always creates new DB instance and cannot be restored to the existing DB instance. You can restore only to the same DB engine version as the source DB instance from which you performed the backup. Supports restoring snapshots to the point in time when the backup was created, and restoring point in time to a specific point in time. You can restore it as backup of external MariaDB as well as backup that you created in RDS for
MariaDB.

> [Caution]
> Restoration might fail if the storage size of the DB instance that you want to restore is smaller than the storage size of the source DB instance that you backed up, or if you use a different parameter group than the parameter group of the source DB instance.

### Snapshot Restoration

Restoring a backup to a point in time is called snapshot restoration. Restoration is done with only backup files, you do not need the source DB instance from which you performed the backup.

### Point-in-time Restoration

Restoring to a particular point in time is called point-in-time restoration. You can restore to a specific position in the binary log, as well as to restore to a specific time. Point-in-time restoration requires backup file and binary log from the time you performed the backup to the time you wanted the restore. Binary logs are stored in the storage of the source DB instance where the backup is performed. Shorter binary log retention period allows you to use more storage capacity, but it may be
difficult to restore to the desired point in time. For the cases listed below, you may not be able to restore to the desired point in time because there is no binary log required for point-in-time restoration.

* When you have deleted the binary log of the source DB instance for securing capacity
* When the binary log is automatically deleted by MariaDB based on the Binary log retention period
* When a binary log is deleted due to a failover of a high availability DB instance
* When binary logs are corrupted or deleted for various other reasons

### Restoration with External MariaDB Backup

You can use an external MariaDB backup file to create a DB instance. When creating an external MariaDB backup file, refer to [Backup](backup-and-restore/#_1) and use the same version as the Percona XtraBackup used by RDS for MariaDB.

> [Caution]
> If the setting value of innodb\_data\_file\_path is not ibdata1:12M:autoextend, it is unable to restore to DB instance of RDS for MariaDB.

(1) Use the command below to perform a backup on the server where MariaDB is installed.

```
mariabackup --defaults-file={my.cnf 경로} --user {사용자} --password '{비밀번호}' --socket {MariaDB 소켓 파일 경로} --compress --compress-threads=1 --stream=xbstream {백업 파일이 생성될 디렉터리} 2>>{백업 로그 파일 경로} > {백업 파일 경로}
```

(2) Check that `completed OK!` is in the last line of the backup log file. If there is no `completed OK!`, the backup did not end successfully, so refer to the error message in the log file to proceed with the backup again.

(3) Upload the completed backup file to the object storage.

* The maximum file size that can be uploaded at a time is 5GB.
* If the backup file is larger than 5GB, you have to use a utility such as split to cut the backup file to less than 5GB and upload it in multi-part.
* For detailed information, refer to [Multipart Upload](/Storage/Object%20Storage/ko/api-guide/#_44).

(4) After accessing the web console of the project you want to restore, on the DB Instances tab, click the **Restore to Backup in Object Storage** button.

### Restoration by Using RDS for MariaDB Backup

You can use the backup file in RDS for MariaDB to restore the database in MariaDB directly. When restoring a RDS for MariaDB backup file, refer to the [Backup](backup-and-restore/#_1) and use the same version as Percona XtraBackup used by RDS for MariaDB.

(1) Export backup of RDS for MariaDB to object storage with reference to the [Export Backup](backup-and-restore/#_5).

(2) Download the backup of the object storage to the server on which you want to restore it.

(3) Stop the MariaDB service.

(4) Delete all files in the MariaDB data storage path.

``` 
rm -rf {MariaDB data storage path}/* 
```

(5) Unzip and restore the downloaded backup files.

```
cat {백업 파일 저장 경로} | xbstream -x -C {MariaDB 데이터 저장 경로}
mariabackup --decompress {MariaDB 데이터 저장 경로}
mariabackup --defaults-file={my.cnf 경로} --apply-log {MariaDB 데이터 저장 경로}
```

(6) Delete unnecessary files after unzipping files.

``` 
find {MariaDB data storage  path } -name "*.qp" -print0 | xargs -0 rm 
```

(7) Start MariaDB service. 