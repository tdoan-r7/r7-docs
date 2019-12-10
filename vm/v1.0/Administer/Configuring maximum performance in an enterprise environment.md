---
title: "Configuring maximum performance in an enterprise environment"
excerpt: ""
---
This section provides system configuration tips and best practices to help ensure optimal performance of the Security Console in an enterprise-scale deployment.  However smaller environments may still benefit from some of these recommendations, particularly the sections on tuning the database and disaster recovery.

## About the Security Console host

The Security Console is the base of operations in a deployment. It manages Scan Engines and creates a repository of information about each scan, each discovered asset, and each discovered vulnerability in its database. With each ensuing scan, the Security Console updates the repository while maintaining all historical data about scans, assets, and vulnerabilities. The Security Console hosts the web-based interface for configuring and operating the application, managing sites and scans, generating reports, and administering users.

The Security Console is designed to meet the scaling demands of an enterprise-level deployment. One Security Console can handle hundreds of Scan Engines, thousands of assets, and any number of reports as long as it is running on sufficient hardware resources and is configured correctly.

In an enterprise environment, the Security Console’s most resource-intensive activities are processing, storing, and displaying scan data.

For information on resources needed at different scales, see [Planning for capacity requirements](doc:planning-for-capacity-requirements).

## Selecting an Operating System to host the Security Console

The Security Console is available in Linux and Windows versions that can be installed on your organization’s hardware running a supported operating system.

Rapid7 recommends installing the Security Console on a supported Linux operating system for large enterprise deployments due to enhanced performance and scalability.

For officially supported system requirements, see [https://www.rapid7.com/products/insightvm/system-requirements](https://www.rapid7.com/products/insightvm/system-requirements/).

## Configuring an optimal RAID array

Rapid7 recommends deploying the Security Console on a high performance RAID array.

Rapid7 recommends arranging multiple disks in a configuration of striped mirrors, also known as a RAID 1+0 or RAID 10 array.  This provides better random disk I/O performance without sacrifice to redundancy. The Security Console and PostgreSQL should be installed on this RAID 10 array. The operating system, which should generate very little disk I/O, may also share this array.

For reference, Rapid7 appliances use a single RAID 10 configuration spanning 8 or 16 disks.  This configuration provides the storage performance necessary for the Security Console and the OS.  While the Security Console will benefit from SSDs, they are not required.

Rapid7 recommends the Security Console be installed on a separate partition from the operating system.

## Tuning the PostgreSQL database

For the best performance, Rapid7 recommends tuning the PostgreSQL database.
[block:callout]
{
  "type": "warning",
  "title": "Configure the Security Console JVM memory",
  "body": "By default, the Security Console will allocate 75% of the total system memory to the Java Virtual Machine (JVM).  While this is recommended for systems with up to 32GB of memory, systems with 64GB or more should reduce the memory allocated to the Security Console and provide more memory to the PostgreSQL database.\n\nWhile the Security Console can be configured with more than 31GB of memory, it is not recommended to use values between 32GB and 48GB.  For more details, on why these values are not recommended review the following article. https://blog.codecentric.de/en/2014/02/35gb-heap-less-32gb-java-jvm-memory-oddities/"
}
[/block]
**For systems with more than 40GB of memory**, create a CustomRuntimeEnvironment.env file to limit the JVM memory for the Security Console.

For example, to limit the JVM memory to 31GB.
Create **/opt/rapid7/nexpose/nsc/CustomRuntimeEnvironment.env** with the following settings.
[block:code]
{
  "codes": [
    {
      "code": "-Xmx31G\n-XX:MaxNewSize=7G",
      "language": "text",
      "name": "CustomRuntimeEnvironment.env"
    }
  ]
}
[/block]
**For systems with less than 40GB of memory**, keep the default 75% memory allocated to the Security Console.

Reserve 3GB (Linux) or 6GB (Windows) of memory for the operating system.

Tune the PostgreSQL database using the remaining memory based on the recommendations at http://pgtune.leopard.in.ua/

Here is an example allocation for a system with 128GB of memory.
Operating System (Linux): 3GB
Security Console: 31GB
PostgreSQL: 94GB

Edit **/opt/rapid7/nexpose/nsc/nxpgsql/nxpdata/postgresql.conf** with the recommended settings from pgtune.
[block:code]
{
  "codes": [
    {
      "code": "# Example for 128GB memory system\n# DB Version: 9.4\n# OS Type: linux\n# DB Type: mixed\n# Total Memory (RAM): 94 GB\n# Number of Connections: 200\nmax_connections = 200\nshared_buffers = 24064MB\neffective_cache_size = 72192MB\nwork_mem = 61603kB\nmaintenance_work_mem = 2GB\ncheckpoint_segments = 32\ncheckpoint_completion_target = 0.9\nwal_buffers = 16MB\ndefault_statistics_target = 100",
      "language": "mysql",
      "name": "postgresql.conf"
    }
  ]
}
[/block]
## Maintaining the database

Given the volume of data the application generates, it is highly recommended to perform regularly scheduled backups.

During a database backup, the Security Console enters maintenance mode and cannot run scans. Planning a deployment involves coordinating backup periods with scan windows. The time needed for backing up the database depends on the amount of data and may take several hours to complete.

For information on performing database backups and maintenance, see [Database backup/restore and data retention](doc:database-backuprestore-and-data-retention).

PostgreSQL also has an autovacuum feature that works in the background performing several necessary database maintenance chores. It is enabled by default and should remain enabled.

## Disaster recovery considerations

As previously mentioned, one Security Console is sufficient for handling all activities at the enterprise level. However, an additional, standby Security Console may be warranted for your organization’s disaster recovery plan for critical systems. If a disaster recovery plan goes into effect, this “cold standby” Security Console would require one database-restore routine in order to contain the most current data.

Disaster recovery may not warrant doubling the fleet of Scan Engines in the data center. Instead, a recovery plan could indicate having a number of spares on hand to perform a minimal requirement of scans—for example, on a weekly basis instead of daily—until production conditions return to normal. For example, if your organization has 10 Scan Engines in the data center, an additional 5 may suffice as temporary backup. Having a number of additional Scan Engines is also helpful for handling occasional scan spikes required by events such as monthly Microsoft patch verification.

## Using anti-virus software on the server

Anti-virus programs may sometimes impact critical operations that are dependent on network communication, such as downloading updates and scanning. Blocking the latter may cause degraded scan accuracy.

If you are running anti-virus software on your intended host, configure the software to allow the application to receive the files and data that it needs for optimal performance in support your security goals:

- Add the application update server, updates.rapid7.com, to a whitelist, so that the application can receive updates.
- Add the application installation directory to a whitelist to prevent the anti-virus program from deleting vulnerability- and exploit-related files in this directory that it would otherwise regard as “malicious.”

Consult your anti-virus vendor for more information on configuring the software to work with the application.