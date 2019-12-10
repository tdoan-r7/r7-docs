---
title: "Database Backup, Restore, and Data Retention"
excerpt: ""
---
Your Security Console features a built-in database backup function that you can run manually or according to a configured schedule. You can use these backups to restore your Security Console on a new or existing host machine.

In addition to these backup and restore functions, the Security Console also allows you to configure retention settings for the various types of data stored as a result of your scans and generated reports. Configuring data retention settings allows the Security Console to automatically purge historical data that ages beyond a specified timeframe, which optimizes console performance and saves disk space.

This article covers the following topics:

* [Included Data Types](#section-included-data-types)
* [Maintenance Mode Overview](#section-maintenance-mode-overview)
* [Standard and Platform-Independent Backups](#section-standard-and-platform-independent-backups)
* [Pre-Backup and Restore Checklist](#section-pre-backup-and-restore-checklist)
* [Perform a Backup](#section-perform-a-backup)
* [Create a Backup Schedule](#section-create-a-backup-schedule)
* [Restore a Local Backup](#section-restore-a-local-backup)
* [Migrate a Backup to a New Security Console Host](#section-migrate-a-backup-to-a-new-security-console-host)
* [Configure Data Retention Settings](#section-configure-data-retention-settings)
[block:callout]
{
  "type": "danger",
  "title": "IMPORTANT - Read the pre-backup and restore checklist",
  "body": "Rapid7 strongly recommends that you review the [pre-backup and restore checklist](#section-pre-backup-and-restore-checklist) before you begin so you can verify that your environment is prepared for backup and restore tasks."
}
[/block]
# Included Data Types

A Security Console backup includes the following data types:

* The contents of the database itself
* Configuration files:
 * `nsc.xml`
 * `nse.xml`
 * `userdb.xml`
 * `consoles.xml`
* Licenses
* Keystores
* Report images
* Custom report templates
* Custom scan templates
* Generated reports
* Custom risk strategies
* Custom SCAP data
* Scan logs

# Maintenance Mode Overview

“Maintenance mode” is a Security Console startup mode that allows the console to perform a backup or restore operation, as well as recover from a critical failure. While in maintenance mode, normal Security Console operations like scanning and report generation are unavailable. Maintenance mode renders the Security Console inaccessible for most users, but Global Administrators can still log in to view the progress of ongoing backup, restore, and recovery processes.

# Standard and Platform-Independent Backups

The Security Console can produce two types of database backups: a **standard** backup and a **platform-independent** backup. These backup types have different characteristics and are best suited to specific use cases.

## Standard Backup

A standard backup is a basic copy of the database as is. Standard backup operations are quicker than platform-independent backup operations, but also produce a backup with a larger file size than a platform-independent operation would. Since standard backups are raw duplicates of your current operating system-specific database, they are only suitable for restorations on your existing Security Console host.

## Platform-Independent Backup

Common in Security Console migration scenarios, a platform-independent backup is composed of an export of your database instead of a raw copy. This export operation takes longer to complete than a standard backup operation does, but the resulting backup file is compatible with any supported Security Console host machine. In addition, platform-independent backup files have a smaller storage impact than their standard counterparts.
[block:callout]
{
  "type": "warning",
  "title": "NOTE - Storage considerations during restoration",
  "body": "While platform-independent backups are smaller in size than standard ones, they do require more free storage during a restoration. In the course of restoring a platform-independent backup on a new Security Console, the import operation extracts the contents of the database export first, effectively doubling the size of the backup files. Although these temporary files are removed when the restoration finishes, you still need to make sure your new Security Console host has enough disk space available to accommodate this database export extraction step."
}
[/block]
Platform-independent backups are also useful in certain troubleshooting scenarios. If your existing database is experiencing indexing errors, a database export operation conducted during a platform-independent backup might resolve the issue.

# Pre-Backup and Restore Checklist
To ensure that your database backup and restore procedures go smoothly, consider the following points before you start:

* **DO NOT deactivate the Security Console on the Insight platform** - Deactivating your existing Security Console prematurely will result in the permanent loss of all your cloud data. Your backup contains all the required data to restore the pairing between your new Security Console and the Insight platform, so deactivation is unnecessary.
* **If possible, create your backup immediately before attempting to restore** - Restoring from a recent backup helps maintain data synchronization between the Security Console and the Insight platform.
* **Make sure no scans are running** - Backup and restore functions put the Security Console in a limited startup state called maintenance mode. Scans and other typical console operations cannot run while maintenance mode is active.
* **Locate and note the password to your private key** - All installations of the Security Console include a randomly generated password to the private key. This private key maintains the credentials that you have configured for authenticated scanning purposes and is password protected to ensure it remains secure. If you attempt to restore a backup with a private key password that does not match the current private key password of your new Security Console installation, you will be prompted for the original password in order to transfer your credentials during the restoration. You can still restore without providing this password, but doing so will prevent your scan credentials from restoring. You can locate the password to your private key in the `creds.kspw` file in your Security Console installation directory:
 * **Linux** - `/opt/rapid7/nexpose/shared/conf/creds.kspw`
 * **Windows** - `C:\Program Files\Rapid7\nexpose\shared\conf\creds.kspw`
* **For database migrations to a new server, create the** `/backups` **directory on the new host** - You must manually place your migrated backup in the `/backups` directory on your new Security Console host in order to restore it. This directory does not exist on fresh installations of the Security Console, so you must also create this directory manually. It’s a good idea to make sure this directory is already in place by the time your backup is ready to move. Create your `/backups` directory on your new host in the following location:
 * **Linux** - `/opt/rapid7/nexpose/nsc`
 * **Windows** - `C:\Program Files\Rapid7\nexpose\nsc`

# Perform a Backup

If you want to perform a manual backup of the Security Console, follow these steps:

1. In your Security Console, expand the left menu and click the **Administration** tab.
2. In the “Maintenance, Storage and Troubleshooting” section, click **maintenance**. The “Maintenance” screen displays the **Backup/Restore** tab.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/e99bd2f-backup_restore_tab.png",
        "backup_restore_tab.png",
        1731,
        620,
        "#b6babe"
      ],
      "caption": ""
    }
  ]
}
[/block]
3. In the “Create Backup” section, give your backup a brief description for reference purposes.
4. If desired, check the **Platform-independent** box.
5. Click **Start Backup** when ready.

Your Security Console will restart in maintenance mode while the backup process takes place. Global Administrators can log in to the Security Console to view the backups tasks as they progress. The Security Console will automatically restart when the backup completes successfully.
[block:callout]
{
  "type": "danger",
  "title": "IMPORTANT",
  "body": "If the backup is unsuccessful for any reason or if the Security Console does not restart automatically, contact [Rapid7 Support](https://www.rapid7.com/for-customers/)."
}
[/block]
After your Security Console restarts, your backup will appear in the “Restore Local Backup” section of the **Backup/Restore** tab.

# Create a Backup Schedule

You can configure a schedule to allow the Security Console to perform backups on its own, saving you from the need to create these backups manually. If you want to mitigate against critical failure scenarios, a backup schedule significantly improves your recovery position.

**To configure a backup schedule:**

1. In your Security Console, expand the left menu and click the **Administration** tab.
2. In the “Maintenance, Storage and Troubleshooting” section, click **maintenance**.
3. On the “Maintenance” screen, click the **Schedules** tab.
4. In the upper right corner of the screen, click **+ Create Backup Schedule**. The “Create Backup Schedule” window appears.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/a9cc64f-database_backup_schedule.png",
        "database_backup_schedule.png",
        616,
        544,
        "#f2f3f3"
      ]
    }
  ]
}
[/block]
5. Verify that the **Enabled** option is selected.
 * You can still save a backup schedule without enabling it, but doing so prevents the Security Console from performing scheduled backups.
6. Choose a start date.
 * This will default to today’s date, but you can choose a date in the future if necessary.
7. Specify the time of day that the Security Console will perform the backup.
8. Specify a “Cancel Backup” time limit.
 * The Security Console will not start a backup procedure if the local Scan Engine is currently in use. The “Cancel Backup” function allows the Security Console to cancel a scheduled backup if it’s unable to start it within the time limit you specify here. A value of `0` ensures that the Security Console will wait as long as it needs to before starting the backup process.

[block:callout]
{
  "type": "warning",
  "title": "NOTE",
  "body": "Scans running on distributed Scan Engines do not affect scheduled database operations. However, InsightVM users should verify that scans from both **local and distributed Scan Engines** are not running at the time of a backup operation to ensure that cloud data synchronizes properly."
}
[/block]
9. Select a frequency setting from the dropdown list, or select **Other** to configure your own.
10. If desired, give your backup schedule a description for reference purposes.
11. If you intend to restore the Security Console on a different host, make sure the **Platform-independent** box is checked.
12. Finally, check the **Pause all local scans before starting** box if you want your backup to always run immediately at its scheduled time.
 * When enabled, this option pauses all local Scan Engine scans so the backup can start. Any paused scans must be resumed manually. This option functionally overrides any “Cancel Backup” value that you set earlier.
13. Click **Save** when finished.

# Restore a Local Backup

If you already have an existing backup on your host machine and want to restore the Security Console to that state, follow these steps:

1. In your Security Console, expand the left menu and click the **Administration** tab.
2. In the “Maintenance, Storage and Troubleshooting” section, click **maintenance**. The “Maintenance” screen displays the **Backup/Restore** tab.
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
      "caption": ""
    }
  ]
}
[/block]
3. In the “Restore Local Backup” section, browse to your desired backup in the provided table and click the icon in the “Restore” column. A dialog box will appear asking for confirmation.
[block:callout]
{
  "type": "warning",
  "title": "NOTE - Restoring a backup from a remote location",
  "body": "If you elect to restore a backup from a remote location other than the local backup directory, note that the Security Console can only upload and restore remote backups that are a maximum of 2GB in size.\n\nIf your remote backup file exceeds this size limit, you'll need to move the backup file to the local `/backups` directory to restore it."
}
[/block]
4. Click **Restore System** to continue.

As noted in the [pre-backup and restore checklist](#section-pre-backup-and-restore-checklist), the Security Console will prompt you for your original keystore password if your current keystore password does not match.
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
5. If prompted, enter the keystore password associated with the backup you are trying to restore and click **Restore**.
 * If necessary, click **Restore (No Password)** to restore without providing the original keystore password. For security reasons, this method prevents your saved site credentials from being restored.

Your Security Console will restart in maintenance mode while the restore process takes place. Global Administrators can log in to the Security Console to view the restore tasks as they progress. The Security Console will automatically restart when the restore completes successfully.

[block:callout]
{
  "type": "danger",
  "title": "IMPORTANT",
  "body": "If the restore is unsuccessful for any reason or if the Security Console does not restart automatically, contact [Rapid7 Support](https://www.rapid7.com/for-customers/)."
}
[/block]
6. Finally, reset any external authentication resources if you had them configured previously:
 * **LDAP** - Restart your Security Console after the restoration completes to reestablish communication with your LDAP server.
 * **SAML** - Respecify your Base Entity URL and reimport the metadata from your IdP. Fully restart your Security Console before allowing users to connect through your IdP again.
7. Verify that all your restored content is available, such as your sites and scan templates.

# Migrate a Backup to a New Security Console Host

If you need to migrate your Security Console to a new host, you can do so by running a restore operation with some additional steps.
[block:callout]
{
  "type": "danger",
  "title": "IMPORTANT - Maintaining cloud synchronization",
  "body": "As an InsightVM subscriber, you will need to observe some extra precautions in order to ensure that your new Security Console remains synchronized with your existing cloud data. We will indicate these important steps to you throughout this procedure."
}
[/block]
**To migrate your Security Console to a new host:**

1. Verify that your existing host is running the latest version of the Security Console. If your existing host is not running the latest version, update your Security Console before you continue.
2. Make sure that no scans are running.
 * In order to maintain cloud synchronization, all local and distributed Scan Engines should be idle at this time.
3. Disable the internet access on your existing Security Console host.

[block:callout]
{
  "type": "danger",
  "title": "IMPORTANT",
  "body": "DO NOT re-enable internet access on this existing console host at any time unless you need to start the entire procedure over again. If the existing console has connectivity at the same time as the new console, the Insight platform will incorrectly sync with both of them."
}
[/block]
4. Create a [platform-independent backup](#section-perform-a-backup) of your existing Security Console.
[block:callout]
{
  "type": "warning",
  "title": "NOTE - Disaster recovery scenarios",
  "body": "If you are restoring from a backup as a result of a disaster recovery situation and creating a new backup is not an option, Rapid7 Support must deactivate your Insight platform activation for a period of 48 hours to prevent sync errors.\n\nIf your restoration scenario requires this deactivation step, contact [Rapid7 Support](https://www.rapid7.com/for-customers/) before proceeding."
}
[/block]
5. Navigate to the `/backups` directory on your existing host and copy your newly created backup to external media:
 * **Linux** - `/opt/rapid7/nexpose/nsc/backups`
 * **Windows** - `C:\Program Files\Rapid7\nexpose\nsc\backups`
6. [Install](doc:install) a new Security Console on a new host and make sure to update to the latest version.
[block:callout]
{
  "type": "danger",
  "title": "IMPORTANT",
  "body": "DO NOT [activate your new Security Console on the Insight platform](doc:activating-your-console-on-the-insight-platform). Any reactivation will cause synchronization issues and is unnecessary since your existing Security Console was already activated."
}
[/block]

[block:callout]
{
  "type": "info",
  "title": "TIP",
  "body": "You do not need to request a license key or activate your license over again in the course of your new installation."
}
[/block]
7. In accordance with the [pre-backup and restore checklist](#section-pre-backup-and-restore-checklist), create the `/backups` directory in the following location of your new Security Console installation:
 * **Linux** - `/opt/rapid7/nexpose/nsc`
 * **Windows** - `C:\Program Files\Rapid7\nexpose\nsc`
8. Transfer your backup files from your external media to this new directory.
9. In your new Security Console, expand the left menu and click the **Administration** tab.
10. In the “Maintenance, Storage and Troubleshooting” section, click **maintenance**. The “Maintenance” screen displays the **Backup/Restore** tab.
11. In the “Restore Local Backup” section, browse to your desired backup in the provided table and click the icon in the “Restore” column. A dialog box will appear asking for confirmation.
12. Click **Restore System** to continue.

As noted in the [pre-backup and restore checklist](#section-pre-backup-and-restore-checklist), the Security Console will prompt you for your original keystore password if your current keystore password does not match.

13. If prompted, enter the keystore password associated with the backup you are trying to restore and click **Restore**.
 * If necessary, click **Restore (No Password)** to restore without providing the original keystore password. For security reasons, this method prevents your saved site credentials from being restored.

Your Security Console will restart in maintenance mode while the restore process takes place. Global Administrators can log in to the Security Console to view the restore tasks as they progress. The Security Console will automatically restart when the restore completes successfully.

[block:callout]
{
  "type": "danger",
  "title": "IMPORTANT",
  "body": "If the restore is unsuccessful for any reason or if the Security Console does not restart automatically, contact [Rapid7 Support](https://www.rapid7.com/for-customers/)."
}
[/block]
14. Reset any external authentication resources if you had them configured previously:
 * **LDAP** - Restart your Security Console after the restoration completes to reestablish communication with your LDAP server.
 * **SAML** - Respecify your Base Entity URL and reimport the metadata from your IdP. Fully restart your Security Console before allowing users to connect through your IdP again.
15. Contact Rapid7 Support and open a case indicating that your new Security Console needs to be reset for platform synchronization purposes. Make sure you fill out your case fields with the following information:
 * Issue Type: **Dashboards**
 * Issue Sub-Type: **Data incorrect**

Rapid7 Support will also reset the update history of your license. This is necessary in migration scenarios since your new Security Console update history must match that of your old Security Console.

16. Verify that all your restored content is available, such as your sites and scan templates.
17. Finally, de-provision the server that housed your previous Security Console to guard against accidental duplicate synchronization errors.

# Configure Data Retention Settings

By default, the Security Console retains all scan, report, asset, and agent data indefinitely. To optimize performance and disk space, you can change this policy by modifying the retention settings for each data type according to your organizational requirements.

Custom data retention settings rely on a period of time in days, months, or years that you specify for each data type. After the relevant data ages beyond the time frame you configure, the Security Console purges it from the database.

Selectable data types are as follows.

## Scan Data

Scan data consists of the results of your completed scans. Configuring a retention setting for scan data ensures that any historical scan data older than the time frame specified will be purged. The Security Console uses the scan completion date as a basis for scan data retention.

## Report Data

Report data consists of all your generated reports. Configuring a retention setting for report data ensures that any generated report older than the specified time frame will be purged.

## Asset Data

Asset data consists of the following objects:

* IP address
* Hostname
* MAC address
* Vulnerabilities
* Risk score
* User-applied tags
* Site membership
* Asset ID
 * The asset ID is a unique identifier applied by the Security Console when the asset data is integrated into the database.

Configuring a retention setting for asset data ensures that any asset that was **not** scanned within the specified time frame will be purged. However, note that asset data retention settings **do not** affect historical scan data. Assets removed as a result of asset data retention settings will still remain in trending data sets if they were present in earlier scans.
[block:callout]
{
  "type": "info",
  "title": "TIP",
  "body": "Assets purged by asset data retention settings will no longer count against your product license limit."
}
[/block]
## Agent Data

Agent data consists of any assets in your Security Console that have the Insight Agent installed. Configuring a retention setting for agent data ensures that any agent-related assets that have not synchronized with the Security Console within the time frame specified will be purged. Similarly to asset data, agent data retention settings **do not** affect historical scan data.
[block:callout]
{
  "type": "warning",
  "title": "NOTE",
  "body": "In order to optimize the data integration process for those assets assessed by the Insight Agent, the Security Console only integrates and stores agent assessment data if it differs from the previous agent assessment. In other words, the Security Console will not record two identical agent assessments in a row, but it will update the last scan completion date.\n\nGiven this condition, be aware that any agent-related assets that are removed as a result of agent data retention settings may not re-appear after subsequent assessments unless the assessment returns data with changes."
}
[/block]
**To configure a custom data retention policy:**

1. In your Security Console, expand the left menu and click the **Administration** tab.
2. In the “Maintenance, Storage and Troubleshooting” section, click the **maintenance** link.
3. On the “Maintenance” screen, click the **Data Retention** tab.
4. Click the **Retain only data within a specific time frame** radio button to make the data type checkboxes clickable.
5. Check any and all data types as needed and configure a time frame for each.
6. Click **Save** when finished.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/02f25d2-dataretention_insightvm.png",
        "dataretention_insightvm.png",
        784,
        456,
        "#a4a8ad"
      ]
    }
  ]
}
[/block]
After saving your policy, the Security Console will run a nightly routine where it will remove data that falls outside the retention time (or times) that you set. This routine begins at 12:00AM and will not interrupt your normal Security Console operations. If the routine itself is interrupted, it will resume where it left off the following evening. The overall duration of this routine depends on how much data is targeted for removal.
[block:callout]
{
  "type": "danger",
  "title": "IMPORTANT",
  "body": "You cannot stop the purge routine once it has started. Be aware that all data removed by this routine is permanent and not retrievable."
}
[/block]