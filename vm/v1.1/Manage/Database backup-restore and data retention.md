---
title: "Database backup/restore and data retention"
excerpt: ""
---
Running regularly scheduled backup and restore routines ensures full recovery of the Security Console in the event of hardware failure. The application performs actual backup and restore procedures in maintenance mode. It cannot run these procedures while scans are in progress. See [Running in maintenance mode](doc:managing-the-security-console#section-running-in-maintenance-mode). However, you set up backup and restore operations while the application is in normal mode.

##Important notes on backup and restore
[block:callout]
{
  "type": "danger",
  "body": "To ensure the security of your credentials, your private key is password protected. This password can be found in the following file in your installation directory (applies to both Linux and Windows installations):\n```\n<install dir>/rapid7/nexpose/shared/conf/creds.kspw\n```\nBefore starting the backup process, open the `creds.kspw` file with a text editor and take note of the password. You will be prompted for the password if the current keystore password does not match the backup's password.",
  "title": "IMPORTANT"
}
[/block]
There are four possible options on the backup/restore page:
* Backup data onto the application’s file system.
* Restore an installation from a prior backup already on the application’s file system.
* Copy an existing backup to external media using **Browse**.
[block:callout]
{
  "type": "danger",
  "body": "You should copy backup data to external storage media to prevent loss in the event of a hardware failure."
}
[/block]
* Restore an installation from a prior backup on external storage.

##What is saved and restored

A backup will save the following items:
* database
* configuration files (_nsc.xml_, _nse.xml_, _userdb.xml_, and _consoles.xml_)
* licenses
* keystores
* report images
* custom report templates
* custom scan templates
* generated reports
* custom risk strategies
* custom SCAP data
* scan logs

##Performing a backup

To perform a backup, take the following steps:

1. Go to the _Maintenance—Backup/Restore_ page, which you can access from the **Maintenance** link on the _Administration_ page.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/f676d64-s_admin_backup_restore.jpg",
        "s_admin_backup_restore.jpg",
        1810,
        908,
        "#dbe5e9"
      ],
      "caption": "The Backup/Restore page"
    }
  ]
}
[/block]
2. In the area titled _Create Backup_, enter a short description of the new backup for your own reference.
[block:callout]
{
  "type": "info",
  "body": "Enabling the platform-independent option significantly increases backup time."
}
[/block]
3. If you want to do a platform-independent backup, select the appropriately labeled check box. This option is useful for restoring on a different host than that of the backup. It allows you to restore backup files on any host with any supported operating system. This option also reduces the size of the backup files.
4. Click **Start backup**.
The Security Console restarts in Maintenance Mode and runs the backup. In Maintenance Mode, normal operations, such as scanning, are not available. If you’re a Global Administrator, you can log on to monitor the backup process. You will see a page that lists each backup activity.
The Security Console automatically restarts when the backup completes successfully.
[block:callout]
{
  "type": "info",
  "body": "If the backup is unsuccessful for any reason or if the Security Console does not restart automatically, contact Technical Support."
}
[/block]
After you complete a backup and the Security Console restarts, the backup appears in a table on the _Maintenance—Backup/Restore_ page, under the heading _Restore Local Backup_. If you want to restore the backup on a different host or store the backup in a remote location, download the backup by clicking the link in the _Download_ column.

##Scheduling a Backup

You can set up schedules to automatically back up data in your Security Console on a regular basis.

**To schedule a backup:**

1. Select **Administration** from the left navigation menu. 
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/df35ca9-s_nx_administration_menu.jpg",
        "s_nx_administration_menu.jpg",
        278,
        413,
        "#24282c"
      ]
    }
  ]
}
[/block]
2. Under the _Maintenance_, _Storage and Troubleshooting_ options, click the **maintenance** link. 
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/c5324e9-s_nx_maintenance_link.jpg",
        "s_nx_maintenance_link.jpg",
        904,
        222,
        "#222836"
      ]
    }
  ]
}
[/block]
3. When the _Maintenance_ page appears, select the **Schedules** tab. 
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/399af95-s_nx_maintenance_schedules_tab.jpg",
        "s_nx_maintenance_schedules_tab.jpg",
        1376,
        288,
        "#172a35"
      ]
    }
  ]
}
[/block]
4. Click **Create Backup Schedule**. 
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/ef0f61e-s_nx_create_backup_schedule_button.jpg",
        "s_nx_create_backup_schedule_button.jpg",
        1377,
        342,
        "#ccd6da"
      ]
    }
  ]
}
[/block]
5. When the _Create Backup Schedule_ window appears, verify the **Enabled** option is selected. 
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/3e69643-s_nx_create_backup_schedule_enabled.jpg",
        "s_nx_create_backup_schedule_enabled.jpg",
        598,
        534,
        "#232f3c"
      ]
    }
  ]
}
[/block]
6. Enter the following information:
   * **Start Date** — The date you want the schedule to begin.
   * **Start Time** — The time you want the schedule to run at.
   * **Cancel Backup** — The amount of time you want to wait for a backup to start before canceling it. You can enter 0 if you do not want to cancel the backup; the backup will wait until all local scans are complete or paused to run.
   * **Frequency** — The frequency you want to backup your console, such as daily, weekly, or monthly
7. Save the schedule.

###Disabling a Backup Schedule

To pause or disable a backup schedule:
1. Select **Administration** from the left navigation menu. 
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/09f29bd-s_nx_administration_menu.jpg",
        "s_nx_administration_menu.jpg",
        278,
        413,
        "#24282c"
      ]
    }
  ]
}
[/block]
2. Under the _Maintenance, Storage and Troubleshooting_ options, click the **maintenance** link. 
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/2be153b-s_nx_maintenance_link.jpg",
        "s_nx_maintenance_link.jpg",
        904,
        222,
        "#222836"
      ]
    }
  ]
}
[/block]
3. When the _Maintenance_ page appears, select the **Schedules** tab. 
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/719b150-s_nx_maintenance_schedules_tab.jpg",
        "s_nx_maintenance_schedules_tab.jpg",
        1376,
        288,
        "#172a35"
      ]
    }
  ]
}
[/block]
4. When the _Schedules_ page appears, find the backup schedule you want to disable and deselect the **Enabled** option. 
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/34578f0-s_nx_disable_backup_schedule.jpg",
        "s_nx_disable_backup_schedule.jpg",
        1381,
        303,
        "#162a34"
      ]
    }
  ]
}
[/block]
##Restoring a backup

The restore procedure reverts the application to its exact state immediately preceding the backup.

To restore a backup:
1. Select **Administration** from the left navigation menu.
2. Under the _Maintenance, Storage and Troubleshooting_ options, click the **maintenance** link.
3. Click the **Backup/Restore** tab.
   * If you are restoring a backup from a different host, make sure the backup is transferred to the local Security Console host. In the _Restore Remote Backup File_ area, click **Choose File** to locate and select the backup, and then click **Start upload and restore**.
   * If you are restoring a backup that was stored locally on the Security Console host, in the _Restore Local Backup_ area, locate the desired backup, and then click the **Restore** icon..
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/c1a6049-s_admin_backup_restore_options.jpg",
        "s_admin_backup_restore_options.jpg",
        1439,
        368,
        "#e5e8ea"
      ],
      "caption": "Options for restoring a backup"
    }
  ]
}
[/block]
4. On the dialog box that appears, click **Restore System**.
[block:callout]
{
  "type": "info",
  "body": "If the current keystore password does not match the backup's password, the **Please Enter Keystore Password** dialog box appears:\n\n* In the **Password** field, enter the keystore password for *this backup*, and then click **RESTORE**.\n* If you do not want to use a password, click **RESTORE (NO PASSWORD)**. For your security, the encryption data that is used for authentication scans will be cleared."
}
[/block]

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/801fa95-keystore_password.JPG",
        "keystore_password.JPG",
        505,
        305,
        "#29333f"
      ]
    }
  ]
}
[/block]
The Security Console restarts in Maintenance Mode and runs the restore procedure. In Maintenance mode, normal operations, such as scanning, are not available. If you are a Global Administrator, you can log on to monitor the backup process page that lists each backup activity. Once the restore begins, it may take some time.
[block:callout]
{
  "type": "warning",
  "body": "If the backup is unsuccessful for any reason or if the Security Console does not restart automatically, contact Technical Support."
}
[/block]
##Migrating a backup to a new host

If you are ever required to change the host system for the application, you will have to migrate your backup to the new host. For example, your organization may perform a hardware upgrade. Or the original host system may have failed and is no longer in service. Migrating a backup to a host system other than the one on which the backup occurred is simple and requires a few extra steps:

1. _Recommended_: Apply the latest updates to the old host. See [Managing versions, updates, and licenses](doc:managing-versions-updates-and-licenses).
This step ensures that when you install the application on the new host in step 5, the database structure will be current with that of the latest installer, preventing any compatibility issues that otherwise might occur.
2. Do a platform-independent backup, which ensures better integrity for the files when they are restored. See [Performing a backup](doc:database-backuprestore-and-data-retention#section-performing-a-backup).
3. Go to the backups directory on the host system: 
```
<install dir>/opt/rapid7/nexpose/nsc/backups
```
Copy all desired backups, including the one you just completed, to external media. Your organization’s policies may require you to keep a certain number of backups, such as for PCI audits.
[block:callout]
{
  "type": "warning",
  "body": "Do not delete the backup host installation unless it is absolutely necessary. It may be useful for troubleshooting in case you encounter issues running the restored files on the new host."
}
[/block]
4. Shut down the application on the original host.
[block:callout]
{
  "type": "danger",
  "title": "IMPORTANT",
  "body": "By default, the application checks for updates every six hours. If the update server detects more than one installation with the same serial number, it will block updates.  Failure to complete this shut down step will result in nonmatching data between the new Security Console and the existing dashboards."
}
[/block]
5. Install the application on the new host. For instructions, see the installation guide, which you can download from the _Support_ page in Help.
6. Apply any available updates to the installation on the new host.
This step ensures that the installation includes any new updates that may have occurred since the backup.
7. Manually create the backups directory on the new host: 
```
<install dir>/opt/rapid7/nexpose/nsc/backups
```
[block:callout]
{
  "type": "info",
  "body": "For this migration process, it is unnecessary to request a license key during installation on the new host. It is also unnecessary to activate the license after you finish the installation and log on to the Web interface."
}
[/block]
8. Transfer the backup files from the external media to the newly created backup directory.
9. In the application, refresh the _Administration_ page in the Web browser.
10. Restore the backup(s). See [Restoring a backup](doc:database-backuprestore-and-data-retention#section-restoring-a-backup).
> The application restarts in Maintenance Mode. Normal operations, such as scanning, are not available. If you are a Global Administrator, you can log on to monitor the backup process. You will see a page that lists each backup activity.
> The Security Console automatically restarts when the backup completes successfully.
[block:callout]
{
  "type": "warning",
  "body": "If the backup is unsuccessful for any reason or if the Security Console does not restart automatically, contact Technical Support."
}
[/block]
11. Verify that all your restored content is available, such as sites and templates.
12. **IMPORTANT:** Contact Technical Support to reset the update history for your license. Since you are transferring your license to a new host, resetting the history will cause the server to re-apply all updates on the new host. This ensures that the update version of the migrated application matches that of the backup on the old host.

##Performing database maintenance

You can initiate several maintenance operations to maximize database performance and drive space.

Database maintenance operations can take from a few minutes to a few hours, depending on the size of the database. Once you start these operations, the application shuts down and restarts in Maintenance Mode. Any in-progress scans or reports will stop before completion and any related data will be lost. You will have to rerun any reports or scans after the application completes maintenance operations and restarts in Normal Mode. For more information, see [Running in maintenance mode](doc:managing-the-security-console#section-running-in-maintenance-mode).

To perform database maintenance:
1. Go to the _Administration_ page.
2. Click **Maintenance**.
3. Go to the _Database Maintenance_ page and select any of the following options:
   * **Clean up Database** removes leftover data that is associated with deleted objects such as sites, assets, or users.
   * **Compress Database** tables frees up unused table space.
   * **Reindex Database** rebuilds indexes that may have become fragmented or corrupted over time.
4. Click **Start Database Maintenance**.

The Security Console automatically restarts when the maintenance completes successfully.

##Setting data retention preferences

The Security Console’s default policy is to retain all scan and report data. To optimize performance and disk space, you can change the policy to retain only some of this data and remove the rest.

To enact a partial data retention policy:
1. Go to the _Administration_ page.
2. Click **Maintenance** on the _Maintenance, Storage and Troubleshooting_ panel.
3. Click **Data Retention**.
4. Select the **Retain only data within a specific time frame** option.
5. Select the time frame of scan, report, and/or asset data to retain. Note: Selecting the asset data retention policy will purge asset data for assets that have not been scanned since the specified time frame. Such assets will no longer be counted towards your license.
6. Click **Save** to enact the policy.
After you enact the policy, the Security Console runs a routine nightly which removes data not included in the retention time frame. The routine begins at 12 a.m. and will not interrupt your normal Security Console operations. If the routine is interrupted, it resumes where it left off on the following evening. The duration of the routine depends on the amount of data being removed.
[block:callout]
{
  "type": "warning",
  "body": "You cannot stop the routine once it starts, and all data removal is permanent."
}
[/block]

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/70dc2d7-s_nx_data_retention_policy.jpg",
        "s_nx_data_retention_policy.jpg",
        1936,
        678,
        "#3a5f75"
      ],
      "caption": "Setting a data retention policy"
    }
  ]
}
[/block]