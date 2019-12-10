---
title: "Managing the Security Console"
excerpt: ""
---
* [Viewing general configuration settings](doc:managing-the-security-console#section-viewing-general-configuration-settings)
* [Changing the Security Console Web server default settings](doc:managing-the-security-console#section-changing-the-security-console-web-server-default-settings)
* [Managing the HTTPS certificate](doc:managing-the-security-console#section-managing-the-https-certificate)
* [Setting the Subject Alternative Name field](doc:managing-the-security-console#section-setting-the-subject-alternative-name-field)
* [Changing default Scan Engine settings](doc:managing-the-security-console#section-changing-default-scan-engine-settings)
* [Changing Scan Engine communication direction in the Console](doc:managing-the-security-console#section-changing-scan-engine-communication-direction-in-the-console)
* [Managing the Security Console database](doc:managing-the-security-console#section-managing-the-security-console-database)
* [Running in maintenance mode](doc:managing-the-security-console#section-running-in-maintenance-mode)

Although the default Security Console settings should work for a broad range of network environments, you can change settings to meet specific scanning requirements.
[block:callout]
{
  "type": "info",
  "body": "Click **Administer** next to _Console_ on the _Administration_ page to launch the Security Console Configuration panel."
}
[/block]
##Viewing general configuration settings

On the _General_ page, you can view the version and serial numbers for the instance of the Security Console that you are using.

##Changing the Security Console Web server default settings

The Security Console runs its own Web server, which delivers the user interface.

To change the Security Console web server default settings:
1. Go to the _Administration_ page.
2. Click **Manage** settings for the Security Console, under _Global and Console Settings_.
3. Go to the _Web Server_ page.
4. Enter a new number for the access port.
5. Enter a new session time-out. This value is the allowed number of seconds of user inactivity after which the Security Console times out, requiring a new logon.
6. Enter new numbers for initial request and maximum request handler threads, if necessary.
It is recommended that you consult Technical Support first. In this context, threads refer to the number of simultaneous connections that the Security Console will allow. Typically a single browser session accounts for one thread. If simultaneous user demand is high, you can raise the thread counts to improve performance. The Security Console will increase the thread count dynamically if required, so manual increases may be unnecessary.
7. Enter a new number for failed logon threshold if desired. This is the number of failed logon attempts that the Security Console permits before locking out the would-be user.
8. Click **Save**.

##Managing the HTTPS certificate

The application provides a self-signed X.509 certificate, which is created during installation. It is recommended that you replace it with a certificate that is signed by a trusted certifying authority (CA).
[block:callout]
{
  "type": "info",
  "body": "The signed certificate must be based on an application-generated CSR. The application does not allow you to import an arbitrary key pair or certificate that you generated."
}
[/block]
To manage certificates and generate a new certificate signing request (CSR):
1. Go to the _Administration_ page.
2. Click **Administer** settings for the Security Console.
3. Go to the _Web Server_ page.
4. Click **Manage Certificate**.
The Security Console displays a box titled _Manage Certificate_.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/29624da-s_manage_certificate.jpg",
        "s_manage_certificate.jpg",
        978,
        782,
        "#e4ecee"
      ],
      "caption": "Manage Certificate"
    }
  ]
}
[/block]
5. Click **Create New Certificate**.
The Security Console displays a box for new certificate information.
6. Enter the information and click **Create**.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/c89fc26-s_manage_certificate_create.png",
        "s_manage_certificate_create.png",
        655,
        535,
        "#e8f1f0"
      ],
      "caption": "Manage Certificate–Create New Certificate"
    }
  ]
}
[/block]
A dialog box appears indicating that a new self-signed certificate was created.

7. Click **Create CSR now**.
You can click **Later** to come back to this step and continue the process at another time.
8. Copy the generated CSR and send it to your CA.
9. Click **Import Certificate** on the _Manage Certificate_ dialog after it is signed by your CA.
10. Paste it in the text box and click **Import**.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/d38005d-s_manage_certificate_import.jpg",
        "s_manage_certificate_import.jpg",
        983,
        473,
        "#e7edee"
      ],
      "caption": "Manage Certificate–Import certificate signing request"
    }
  ]
}
[/block]
11. Click **Save** to save the new Security Console information.
The new certificate name appears on the _Web Server_ page.

## Setting the Subject Alternative Name field
[block:callout]
{
  "type": "warning",
  "title": "IMPORTANT",
  "body": "Consoles using externally signed (CA/non-CA) **must** have a SAN field. If the certificate is self signed, it does not require a SAN field."
}
[/block]
This process can be completed with the following steps:

1. In your installation directory, check the **keystores** folder for a file called **nscweb.ks**:

```
<install-dir>/nsc/keystores/nscweb.ks
```

If the file does not exist, browse to the "Manage Certificate" window, located in the **Administration** tab **>** "Global and Console Settings" window **> Administer > Web Server** tab **> Manage Certificate** button. Select **Create New Certificate**.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/2687305-Screen_Shot_2017-11-20_at_3.04.36_PM.png",
        "Screen Shot 2017-11-20 at 3.04.36 PM.png",
        649,
        529,
        "#e5eff0"
      ]
    }
  ]
}
[/block]

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/efd36dc-Manage_Certificate.png",
        "Manage_Certificate.png",
        639,
        524,
        "#e8f0f0"
      ]
    }
  ]
}
[/block]
2. Enter the SAN information and click **Create**.  Another dialogue box will appear.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/bb4cf37-Create_CSR_Now.png",
        "Create_CSR_Now.png",
        799,
        603,
        "#2a3741"
      ]
    }
  ]
}
[/block]
3. Click **Create CSR Now**.
[block:callout]
{
  "type": "warning",
  "title": "NOTE",
  "body": "In order to complete the next step successfully, make sure you have execute permission on `/opt/rapid7/Nexpose/_jvm1.8.0_102/bin/keytool`, and verify with your network administrator that assigning execute permissions for this binary is acceptable.\n\nThis can be done by running as administrator on Windows or issuing a `chmod +x` command on the Linux file from the command line."
}
[/block]
4. Open a command prompt as administrator on the host machine.

SSH into Nexpose Server and run the following as root:

```
cd [install_dir]/rapid7/nexpose/_jvm1.8.0_102/bin

./keytool -certreq \
-alias nscweb \
-sigalg sha512WithRSA \
-keystore [install_dir]/rapid7/nexpose/nsc/keystores/nscweb.ks \
-storepass 'r@p1d7k3y$t0r3' \
-ext san=dns:samplehostname.com,ip:127.0.0.1 \
-file filename.csr
```

The **console.csr** file can be sent to a CA to be signed.
[block:callout]
{
  "type": "info",
  "body": "This directory requires superuser elevation:\n\n```\n<install-dir>/_jvm1.8.0_102/bin/keytool -certreq \\\n```"
}
[/block]

[block:callout]
{
  "type": "warning",
  "title": "NOTE",
  "body": "The CA should take the SAN data in your CSR and add it to the certificate when signed. This is not automatically added through the CSR, so it is recommended to verify this ahead of time in order to make sure the CA added the SAN data during the signing process."
}
[/block]
5. Check the signed certificate returned by your CA to make sure the SAN is present:

```
openssl x509 -text -noout -in SignedCert.crt
```
The details should contain something similar to the following:
```
X509v3 extensions:
X509v3 Issuer Alternative Name:
DNS:samplehostname.com, IP Address:127.0.0.1
```
6. Import the signed certificate (a PEM file) into the InsightVM UI:
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/1278603-certificatemanager_import.png",
        "certificatemanager_import.png",
        648,
        532,
        "#e5efef"
      ]
    }
  ]
}
[/block]
##Changing default Scan Engine settings

The Security Console communicates with distributed Scan Engines over a network to initiate scans and retrieve scan results. If you want to obtain scan status information more quickly or reduce bandwidth or resource consumption required for Security Console-to-Scan-Engine communication, you can tune various settings on the Scan Engines page of the Security Console Configuration panel. 

###Configuring Security Console connections with distributed Scan Engines

The Security Console establishes connections with distributed Scan Engines to launch scans and retrieve scan results. This communication can be disrupted by low network bandwidth, high latency, or situations in which Scan Engines are performing high numbers of simultaneous scans. If any of these conditions exist in your environment, you may want to consider increasing connection settings on the _Scan Engines_ configuration page:
[block:callout]
{
  "type": "warning",
  "body": "It is recommended that you consult with Technical Support before tuning these settings."
}
[/block]
* The **Connection timeout** setting controls how long the Security Console waits for the creation of a connection with a distributed Scan Engine.
* The **Response timeout** setting controls how long the Security Console waits for a response from an Scan Engine that it has contacted.

To configure these settings, take the following steps:
1. Go to the _Scan Engines_ page in the _Security Console Configuration_ panel.
2. Click the _Administration_ tab.
3. On the _Administration_ page, click **manage** for the Security Console.
4. Click **Scan Engines** in the _Security Console Configuration_ panel.
5. Adjust the _Connections_ settings.
6. Edit the value in the Connection timeout field to change the number of milliseconds that elapse before a connection timeout occurs.
7. Edit the value in the Response timeout field to change the number of milliseconds that elapse before the Security Console no longer waits for a response from an Scan Engine.
8. Click **Save** in the top bar of the panel to save the changes.
9. Restart the Security Console so that the configuration changes can take effect.
[block:callout]
{
  "type": "info",
  "body": "Because millisecond values can be difficult to read, a time value that is easier to read appears to the right of each value field. As you change either timeout value, note how the equivalent value changes."
}
[/block]
###Creating a trusted pairing from a Scan Engine to a Security Console

You can create a pairing from a Scan Engine to a Security Console by creating a trusted connection between with them. A shared secret is a piece of data used so the console will recognize and trust the incoming communication from the engine.
[block:callout]
{
  "type": "info",
  "body": "Each generated shared secret can be used by multiple engines. A shared secret is valid for 60 minutes from when it was generated. After 60 minutes, you will need to generate a new Shared Secret if you want to create additional trusted pairings."
}
[/block]
To create a trusted pairing:

1. Ensure that no network-based or host-based firewall is blocking access to port 40815 on your InsightVM Security Console. If you want to use a port other than 40815, change this line in your console's nsc.xml file (\_[installation directory]_\nsc\conf\nsc.xml) to the port you want to use:
```
<EngineListener port="40815"/>
```
Restart your Security Console.
2. Generate a shared secret on the Security Console. To do so, go to the _Administration_ page and click **manage** next to _Engines_. Under _Generate Scan Engine Shared Secret_, click **Generate**. Copy the Shared Secret to a text file.
3. Log on to the host where the Scan Engine is running and access the command line interface. For Windows hosts, you can use Remote Desktop Protocol. For Unix and related hosts, you can use SSH. For Linux, access the engine's console by using the command:
```screen -r```
4. Add the Security Console on your engine using the IP address or the hostname of the machine hosting the Security Console. Example:
```add console 10.1.1.4```
5. Find the ID of the Security Console by typing
```show consoles```
6. Connect to the Security Console using the ID you just found. Example:
```connect to console 2```
7. Verify that the connection was successful. Type:
```show consoles```
For the console ID you just connected, the value of _connectTo_ should be 1.
8. Add the shared secret to that Security Console on the engine. Example:
```add shared secret 2```
At the prompt, paste in the shared secret you copied from the Security Console.
You will see a verification message if the shared secret has been applied successfully.
9. Enable the console on the engine. Example:
```enable console 2```
You will see many lines logged as the pairing takes place.
10. Return to the Scan Engines page on the Security Console Web interface. Click **Refresh displayed Engines**. Verify that the Scan Engine you just paired has been added. Click the Refresh icon for that Scan Engine to confirm that the Security Console can query it.
By default, when you have created a trusted pairing with this method, the comunication direction will be from Engine to Console. To change it, see [Changing Scan Engine communication direction in the Console](doc:managing-the-security-console#section-changing-scan-engine-communication-direction-in-the-console).

##Changing Scan Engine communication direction in the Console

You can change the direction of communication initiation between the Security Console and each remote Scan Engine. Which option is preferable depends on your network configuration. If the direction of communication is from Console to Engine, which is the default setting, the Security Console will initiate communication with the Scan Engine. If the direction of communication is from Engine to Console, the Scan Engine will actively notify the console that it is available. This option allows a Console that is behind a firewall and configured to allow inbound connections to have a communication channel with the Scan Engine.
[block:callout]
{
  "type": "info",
  "body": "The Engine to Console option is not available for the Local Scan Engine or Hosted Engines."
}
[/block]
To change the direction of Scan Engine communication:
1. Go to the _Administration_ page.
2. Select **manage** next to _Engines_.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/dcb4966-s_nx_manage_engines.jpg",
        "s_nx_manage_engines.jpg",
        1733,
        276,
        "#d5dde2"
      ]
    }
  ]
}
[/block]
3. In the _Communication Status_ column, toggle the setting so that the arrow points to and from the intended directions.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/5595e7e-s_nx_scan_engine_comm_direction.jpg",
        "s_nx_scan_engine_comm_direction.jpg",
        1759,
        643,
        "#eaf2f4"
      ]
    }
  ]
}
[/block]
You can also hover the cursor over the arrow to view the current status of the communication.

The possible options are:
* **Green** – Active
* **Orange** – Unknown
The console and engine could not communicate, but there was no error.
[block:callout]
{
  "type": "info",
  "body": "This status sometimes appears when there has been a long time since the last communication. In this case, hovering over the arrow will cause a ping, and if that communication is successful the status will become Active."
}
[/block]
* **Red** – Three options.
   * **Pending authorization**
> Authorize communication from the Scan Engine. See [Configuring distributed Scan Engines](doc:configuring-distributed-scan-engines).
   * **Incompatible**
> The console and engine are on different versions. Update them to the same version, or choose a different engine to pair.
   * **Down**
> The Scan Engine is not online. Perform troubleshooting steps to make it active again.

###Allocating threads for monitoring scans

The Security Console allocates a thread pool for retrieving scan status information. You can adjust the number of threads, which corresponds to the number of scan status messages that the Security Console can retrieve simultaneously. For example, if you increase the number of distributed Scan Engines and the number of scans running simultaneously, you can increase the threads in the pool so that the Security Console can retrieve more status messages at the same time.
[block:callout]
{
  "type": "warning",
  "body": "It is recommended that you consult with Technical Support before tuning these settings."
}
[/block]
Keep in mind that retrieval time is subject to network conditions such as bandwidth and latency. Whenever the number of active threads in use exceeds the overall number of threads in the pool, the Security Console removes unused scan status threads after specific time interval. If you notice an overall decrease in the frequency of scan status messages, you may want to consider increasing the timeout value.

To adjust pool settings for scan status threads, take the following steps:

1. Go to the _Scan Engines_ page in the _Security Console Configuration_ panel.
2. Click the **Administration** tab.
3. Click **manage** for the Security Console on the _Administration_ page.
4. Click **Scan Engines** in the _Security Console Configuration_ panel.
5. Adjust the _Scan Status_ settings.
6. Edit the value in the **Thread idle timeout** field to change the number of milliseconds that elapse before the Security Console removes unused scan threads.
7. Edit the value in the **Thread pool size** field to change the number of threads in the pool for monitoring scan status.
8. Click **Save** in the top bar of the panel to save the changes.
9. Restart the Security Console so that the configuration changes can take effect.
[block:callout]
{
  "type": "info",
  "body": "Because millisecond values can be difficult to read, a time value that is easier to read appears to the right of each value field. As you change either timeout value, note how the equivalent value changes."
}
[/block]
###Retrieving incremental scan results from distributed Scan Engines

The Security Console communicates with Scan Engines over a network to retrieve scan results. By default, the Security Console retrieves scan results from distributed Scan Engines incrementally, displaying results in the Web interface as it integrates the data, rather than retrieving the full set of results after each scan completes. This allows you to view scan results as they become available while a scan is in progress.

Incremental retrieval modulates bandwidth usage throughout the scan. It also makes it unnecessary for the Security Console to retrieve all the data at the end of the scan, which could cause a significant, temporary increase in bandwidth usage, especially with large sets of data.

The _Scan Engines_ page of the _Security Console Configuration_ panel displays a check box for incremental retrieval of scan results. It is selected by default. Do not disable this option unless directed to do so by Technical Support.

##Managing the Security Console database

###Viewing Security Console database information

You can view the name and type of the Security Console database on the _Database_ page of the Security Console configuration panel. You also can change displayed database settings.

To save the changes, click **Save**.

###Migrating the database

The application’s database is a core component for all major operations, such as scanning, reporting, asset and vulnerability management, and user administration. The efficiency with which it executes these tasks depends heavily on database performance. The current PostgreSQL database version, 9.4.1, features a number of performance and stability enhancements. The application takes full advantage of these improvements to scale flexibly with the needs of your environment. Future releases will include powerful features that will require the latest PostgreSQL version.
[block:callout]
{
  "type": "info",
  "body": "Only administrators can migrate the database."
}
[/block]
If your installation is running an earlier version of PostgreSQL, you can easily migrate it to the latest version, using a tool in the Security Console Web interface.

Migration involves the following required tasks:

* [Preparing for migration](doc:managing-the-security-console#section-preparing-for-migration)
* [Starting and monitoring the migration](doc:managing-the-security-console#section-starting-and-monitoring-the-migration)
* [Verifying the success of the migration](doc:managing-the-security-console#section-verifying-the-success-of-the-migration)
* [Backing up the post-migration database](doc:managing-the-security-console#section-backing-up-the-post-migration-database)

Restoring a backup of an older platform-dependent PostgreSQL database after migrating to the new version is not supported. After you perform and verify the migration to the latest version and ensure database consistency, it is very important that you back up the database immediately to prevent the need to restore an earlier version of the database. See [Backing up the post-migration database](doc:managing-the-security-console#section-backing-up-the-post-migration-database).

This document also provides instructions for optional post-migration tasks:
* restoring backups
* restoring tuned PostgreSQL settings

####Preparing for migration

Some preparation will ensure that migration takes the least possible amount of time and is successful:
* Make sure port 5432 is open.
* Make sure you have sufficient disk space. During the migration, the old database is backed up and a new one is created, so you need to accommodate both databases. If you are unable to run the migration because of insufficient disk space, you can take several steps to free up space. See [Freeing up disk space for migration](doc:managing-the-security-console#section-freeing-up-disk-space-for-migration).
* Make sure that you have an authenticated global administrator account, so that you can monitor the migration in the Security Console Web interface. If your account is authenticated by an external source, such as LDAP or Kerberos, you will be able to start the migration. However, when the application restarts in Maintenance Mode, you will not be able to log on to the Security Console Web interface to monitor the migration. The database stores information about the external authentication sources, and it won’t be operational during the migration. If you do not monitor the migration, you will not know if any issues have occurred requiring you to restart it or take some other action. You have several options for monitoring the migration:
* When the application restarts in Maintenance Mode, log on with an authenticated global administrator account instead of an external source. This will allow you to monitor status messages in the Security Console Web interface. If you do not have an authenticated account, you can create one or modify an existing account accordingly. See [Managing users and authentication](doc:managing-users-and-authentication). You also can log on with the default administrator account that was created during installation.
* If you do not have an authenticated administrator account you can monitor the migration by reading the nsc.log file, which is located in [installation_directory]/nsc. If you need to restart the application manually, you can do so from the command prompt using the ```restart``` command.

####Freeing up disk space for migration

In most cases the **Start Migration** button is disabled if you do not have enough disk space to perform the migration. However, in some environments, the **Start Migration** button may be enabled but disk space issues may still occur during migration. For example, see the section about Linux file systems. To free up disk space, try the solutions listed in the following sequence. Check if the **Start Migration** button is enabled after each step.
[block:callout]
{
  "type": "info",
  "body": "It is recommended that your free disk space be equal to **1.6 GB + (1.3 x database_size)**."
}
[/block]
Run the following database maintenance tasks, which remove unnecessary data and free up unused table space:

* re-indexing the database
* cleaning up the database
* compressing tables

If you have not run these tasks recently, doing so may free up considerable space. It is recommended that you run each task individually in the following sequence. After completing each task, try running the migration again. Re-indexing may provide all the space you need, making it unnecessary to clean up the database or compress tables, which can take significant time depending on the size of your database. See [Performing database maintenance](doc:database-backuprestore-and-data-retention#section-performing-database-maintenance).

Move the following directories from the host system, and restore them after the migration is complete:
* backup files—[installation_directory]/nsc/*.bak and—[installation_directory]/nsc/*.zip
* reports directory—[installation_directory]/nsc/htroot/reports
* access log directory, including the Tomcat log subdirectory—[installation_directory]/nsc/logs
* scan event data files directory—[installation_directory]/nse/scans
* Security Console logs—[installation_directory]/nsc/*.log and /nsc/*.log*
* PostgreSQL log—[installation_directory]/nsc/nxpsql/nxpgsql.log
* scan logs directory—[installation_directory]/nse/nse.log and /nse/nse.log.
[block:callout]
{
  "type": "info",
  "body": "These directories and files take up increasing amounts of disk space over time as the application accumulates data."
}
[/block]
To create free space for migration:
1. Move from the host system any files or directories extraneous to the application that are not required by other applications to run. You can restore them after the migration is complete.
2. Delete the contents of the java.io.tmpdir directory on the host system. The location depends on the operating system.
[block:callout]
{
  "type": "info",
  "body": "If the disk space problem occurs after a previous migration attempt failed, see [Addressing a failed migration](doc:managing-the-security-console#section-addressing-a-failed-migration)."
}
[/block]
After taking the preceding steps, try starting the migration again. If you still don’t have enough disk space, contact Technical Support.

####Creating free space in Linux

By default, Linux file systems reserve 5 percent of disk space for privileged, or root, processes. Although this reserved space is not available for database migration, the application includes it in the pre-migration calculation of total available space. As a result, a migration may be able to start, but then fail, because the actual amount of free disk space is lower than what was detected in the calculation. You can lower the amount of reserved disk space to make the amount of actual free space more consistent with the results of the pre-migration calculation. To do so, use the tune2fs utility. The command includes parameters for the percentage of reserved disk space and the partition on which the application is installed.

Example: ```tune2fs -m 1 /dev/sdf1```

####Starting and monitoring the migration

To monitor the migrations:

1. Go to the _Administration_ page.
2. Select **Migration**. This link will only be available if no one in your organization has performed the migration yet.
3. Review your database migration status on the migration page.
4. Click **Start Migration** if it indicates that your installed PostgreSQL version is earlier than 9.0.3 and that your system is ready for migration.
After you click **Start Migration**, the application goes into Maintenance Mode. Normal operations, such as scanning and running reports, are unavailable. See [Running in maintenance mode](doc:managing-the-security-console#section-running-in-maintenance-mode). If you’re an administrator, you can log on to monitor migration status messages.

During migration, the application copies data from the old PostgreSQL database to the new PostgreSQL database. The migration requires enough disk space for both of these databases.

It also backs up the old PostgreSQL database and stores it in the directory [installation_directory]/nsc/nxpgsql-backup-[timestamp] after the migration completes.

The estimated migration time is based on the size of the database.

After all migration processes finish, the application restarts, and you can resume normal operations.

If you click the **Cancel** button to stop the migration before it completes, the application will discontinue the migration process. You can then restart the application in normal, operational mode.

If the migration fails, your current version of the PostgreSQL database will remain intact, and you can continue using the application without interruption. See [Addressing a failed migration](doc:managing-the-security-console#section-addressing-a-failed-migration).

In very rare instances the application may display the migration FAQs while in Maintenance Mode after the migration process has been executed, instead of a status message detailing the results of the migration. If this occurs, contact Technical Support for assistance before restarting the server. You should also contact Technical Support if this situation occurred and you inadvertently restarted your server, or at any time after the migration if you note on the Database Migration page that the version of PostgreSQL running in your environment is earlier than 9.4.

####Addressing migration that takes a long time with no new status messages

Depending on the amount of data, the migration can take from 30 minutes to over an hour. Therefore, a long migration time is not unusual, and extended periods without new status messages do not necessarily indicate that the migration is “hanging.”

You can perform a couple of quick checks to confirm that the migration is still proceeding when no status messages are visible:
1. Run top in Linux or Task manager in Windows, and check if a PostgreSQL process is running and using CPU resources.
2. Check migration log files, located in [installation_directory]/nsc/nxpgsql/pgsqlpgsql/bin/pgrade_*.log, for messages about database tables being copied.

The Security Console will display a notification when the processes have completed.

####Verifying the success of the migration

To verify migration success, take the following steps:
1. Go to the _Administration_ page.
2. Click **Administer**.
3. Go to the _Database_ tab.
4. Read the installed version of PostgreSQL, which is displayed on the page.
If the migration was successful, the installed version will be 9.4.1.

OR

1. Open the nsc.log file, located in [installation_directory]\nsc\logs, to verify that PostgreSQL 9.4.1 is running.
2. Search for the string _PostgreSQL_. You will find the active PostgreSQL version number with an instance of that string.
It will appear on a line that looks like the following example:
```
NSC 2015-06-11T18:45:01 PostgreSQL 9.4.1, compiled by Visual C++ build 1500, 64-bit
```
Upon confirming that the migration was successful, take the following steps:
1. Move back any files or directories that you moved off the host system to free up disk space for migration. See [Freeing up disk space for migration](doc:managing-the-security-console#section-freeing-up-disk-space-for-migration).
2. Move the [installation_directory]/nsc/nxpgsql-backup-[timestamp] directory to an external location for storage.

It contains the pre-migration database, including the postgresql.conf file.
[block:callout]
{
  "type": "info",
  "body": "Before you resume normal operations, make sure to verify database consistency as described in the following section."
}
[/block]
If you modified postgresql.conf or pg_hba.conf prior to the migration you will need to reapply any custom settings to those configuration files. See [Restoring custom PostgreSQL settings](doc:managing-the-security-console#section-restoring-custom-postgresql-settings). You can refer to the modified configuration files in the old, archived version of PostgreSQL for custom settings.

####Ensuring database consistency

This procedure involves two steps. Checking database consistency and cleaning up the database take little time.

To verify database consistency and respond appropriately:
1. Go to the _Administration_ page.
2. Click **Diagnose**.
The Security Console displays the _Troubleshooting_ page.
3. Select only the **Database Diagnostics** check box.
4. Click **Perform Diagnostics**.
A table appears on the page, listing the results of all diagnostic tests. Red circles containing the letter _X_ indicate consistency issues.
5. Go to the _Administration_ page.
6. Click **Maintenance**.
The Security Console displays the _Database Maintenance_ page.
7. (_Optional_) Select the **Clean up Database** task to remove any unnecessary data.
8. Click **Start Database Maintenance**.
[block:callout]
{
  "type": "info",
  "body": "All diagnostics options are selected by default, but only database diagnostics are necessary for verifying database consistency after migration. To see only the information you need for this task, clear any other selected check boxes."
}
[/block]
Once you start these operations, the application shuts down and restarts in Maintenance Mode. Any in-progress scans or reports will stop before completion and any related data will be lost. You will have to rerun any reports or scans after it completes maintenance operations and restarts in Normal Mode. For more information, see [Running in maintenance mode](doc:managing-the-security-console#section-running-in-maintenance-mode).

####Backing up the post-migration database

It is very important that you back up the database immediately after you verify the success of the migration and ensure database consistency. This preserves a baseline instance of the post-migration database and prevents the need to restore a backup of a PostgreSQL 9.0 database.

Perform this step only after you have completed the preceding steps:
* migrating the database
* verifying the success of the migration
* ensuring database consistency

For instructions on backing up the database, see [Database backup/restore and data retention](doc:database-backuprestore-and-data-retention).

####Restoring a database that was backed up as part of a migration

After migration, the application backs up the PostgreSQL 9.0 database and stores it in the directory [installation_directory]/nsc/nxpgsql-backup-[timestamp].

If you want to restore this particular database, take the following steps:
1. Shut down the application.
2. Rename the pgsql directory of the post-migration database.
It is located in [installation_directory]/nsc/nxpgsql.
3. Copy the backup directory, named nxpgsql-backup-[timestamp], into the [installation_directory]/nsc directory, and rename it nxpgsql.
4. Start the application and resume operations.
[block:callout]
{
  "type": "info",
  "body": "Move the backup directory with all original permissions attributes preserved. Doing so prevents the requirement on Linux that nxpgsql be the owner of the directory, as well as the necessity on Windows to give the system user access to the directory."
}
[/block]
If you are planning to restore the database that was backed up during the migration, keep several things in mind:

If you run scans or reports after the migration and then restore the backup database, the Security Console Web interface will not list scan or report instances from the period between the migration and the restoration because the restored database does not contain those records.

When you start to run scans or reports after the restoration, the associated scan or report instances that are being populated in the restored database will overwrite the instances that were generated in the file system prior to the restoration.

Graphic charts will initially be out of synch with the restored database because they always reflect the latest site, scan, or asset group information. Each chart will refresh and synchronize with the restored database after an event associated with it. For example, running a scan will refresh and synchronize the charts for any associated sites or asset groups.

####Restoring custom PostgreSQL settings

The PostgreSQL database applies its default settings after migration. If you previously modified the postgresql.conf file to tune database performance or the pg_hba.conf to enable remote connections to the database, you will need to reapply those modified settings.

After the migration is complete, you can refer to the configuration files in the old, archived version of PostgreSQL, which is stored in the directory [instsallation_directory]/nsc/nxpgsql-backup-[timestamp].
[block:callout]
{
  "type": "danger",
  "body": "Do not simply copy the old configuration files into the new database location. This may prevent the database from starting due to compatibility issues. For each file, compare each setting one by one, and edit only the properties that you modified in the previous PostgreSQL installation."
}
[/block]
####Addressing a failed migration

If the migration fails, your current version of the PostgreSQL database will remain intact. Simply restart the application and resume normal operations.

Before you run the migration again, find out if the failure occurred due to disk space errors. In certain cases, migration may exceed available disk space before finishing, even if the automatic pre-migration check determined that sufficient disk space was available.

To troubleshoot a failed migration:
* Check your available space for the disk that the application is installed on.
* (Optional) In Windows, right-click the icon for the disk and then click **Properties** from the pop-up menu. Read the amount of available disk space.
* (Optional) In Linux, run the command to show disk space: df-hin the [installation_directory]/nsc directory. Read the amount of available disk space.
* If the available disk space is less than the database size, free up disk space, and run the migration again. See [Freeing up disk space for migration](doc:managing-the-security-console#section-freeing-up-disk-space-for-migration).
* If your free disk space is equal to at least 1.6 GB + (1.3 x database_size), this suggests that the migration did not fail due to disk space issues but for a different reason. Contact Technical Support for assistance in completing the migration.
[block:callout]
{
  "type": "warning",
  "body": "If you do not wish to retry migration after failure, you should still delete the /nxpgsql-temp directory, because it uses up considerable disk space."
}
[/block]
If the migration fails due to a system failure or power outage and you attempt to run the migration again, you may encounter a disk space limitation issue. This is because during the failed migration attempt, the application created an nxpgsql-temp directory. Simply delete this directory and start the migration again. The temp directory is located in [installation_directory]/nsc.

##Running in maintenance mode
[block:callout]
{
  "type": "info",
  "body": "Only global administrators are permitted to run the application in maintenance mode."
}
[/block]
Maintenance mode is a startup mode in which the application performs general maintenance tasks and recovers from critical failures of one or more of its subsystems. During maintenance mode, you cannot run scans or reports. Available functions include logging, the database, and the Security Console Web interface.
[block:callout]
{
  "type": "info",
  "body": "The application automatically runs in maintenance mode when a critical internal error occurs."
}
[/block]
When the application is running in maintenance mode, you see the page _/admin/maintenance/index.html_ upon logging on. This page shows all available maintenance tasks and indicates the current status of the task that is being performed. You cannot select a new task until the current task is completed. Afterward, you can switch tasks or click **Restart** to return to normal operating mode.

To work in Maintenance mode:
1. Click the _Administration_ tab.
2. On the _Administration_ page, click **Maintenance**.

The Security Console displays the _Maintenance Mode_ page.