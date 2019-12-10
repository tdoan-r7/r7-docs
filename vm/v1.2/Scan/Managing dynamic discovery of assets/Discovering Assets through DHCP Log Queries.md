---
title: "Discovering Assets through DHCP Log Queries"
excerpt: ""
---
This connection extends your visibility into your asset inventory by exposing assets that may not be otherwise apparent. Scan Engines query DHCP server logs, which dynamically update with fresh asset information every five seconds. The engines pass the results of these queries to the Security Console. For each DHCP connection, you assign a specific Scan Engine.

On first connection, the method will yield the current DHCP lease table. When initially established, the connection discovers assets in the current DHCP lease table. While the connection remains active, it continuously discovers new assets the DHCP server detects and existing assets that renew their IP addresses.

You can leverage the number of distributed Scan Engines to communicate with multiple DHCP servers and to connect with these servers in less accessible locations, such as behind firewalls or on the network perimeter.
[block:callout]
{
  "type": "info",
  "body": "The DHCP method only discovers assets that have not yet been discovered by the Security Console through a different method or through a scan."
}
[/block]
Two DHCP collection options are available:

* _Directory Watcher_ monitors a specified directory on a DHCP server host and uploads new DHCP entries added to the directory at 10-second intervals. Use this method for log files that roll over to new files, such as Microsoft DHCP or Internet Information Services (IIS) files.
* _Syslog_ operates like a syslog server, listening on a TCP or UDP port to receive syslog messages. Use this method if you are managing DHCP information with an Infoblox Trinzic appliance.

## Preparing the target environment for Dynamic Discovery through DHCP Directory Watcher method
[block:callout]
{
  "type": "info",
  "body": "The current implementation of DHCP discovery with the _Directory Watcher_ method supports Microsoft Server 2008 and 2012."
}
[/block]
Make sure your Microsoft DHCP configuration enables logging. Also, it is strongly recommended that you move the log files to a directory that is separate from the DHCP database files. Microsoft DHCP stores log data in a separate file for each day of the week and overwrites each file on a weekly basis.

**Tip:** The default directory path of the DHCP log file is in Windows 2008 is ```%windir%\System32\Dhcp```. The path in Windows 2012 is ```%systemroot%\System32\Dhcp```.

## Adding assets by IP address instead of host name

In environments with duplicate host names across sites, it is possible to correlate DHCP assets by IP address rather than by host name.

### Step 1: Prefer an IP Address over a Hostname when adding assets to sites

The following needs to be added to the `nsc/CustomEnvironment.properties` file:

    com.rapid7.eso.sites.prefer.ip=true

Assets should now be added to sites as IP addresses rather than by host names.

### Step 2: Configure DHCP to prefer an IP Address when correlating assets

Be sure to delete all assets discovered via DHCP and remove related asset definitions from sites first.  The following needs to be added to the `nsc/CustomEnvironment.properties` file:

    com.rapid7.nsc.dhcp.prefer.ip=true

Once this is done, rediscover all deleted assets via DHCP.  DHCP discovered assets should now correlate properly with a preference for an IP address.