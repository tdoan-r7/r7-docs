---
title: "Running a manual scan"
excerpt: ""
---
Running an unscheduled scan at any given time may be necessary in various situations, such as when you want to assess your network for a new zero-day vulnerability or verify a patch for that same vulnerability. This section provides guidance for starting a manual scan and for useful actions you can take while a scan is running.

##Starting a manual scan for a site

To start a scan manually for a site right away from the _Home_ page, click the **Scan** icon for a given site in the _Site Listing_ table of the _Home_ page. Or click the **Scan** button that appears below the table labeled _Current Scans for All Sites_.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/2d3bd6d-s_nx_scan_status_multiple_engines.jpg",
        "s_nx_scan_status_multiple_engines.jpg",
        2619,
        376,
        "#ecf3f4"
      ],
      "caption": "Starting a manual scan"
    }
  ]
}
[/block]
Or, you can click the **Scan** button on the _Sites_ page or on the page for a specific site.

##Starting a manual scan for a single asset

Scanning a single asset at any given time can be useful. For example, a given asset may contain sensitive data, and you may want to find out right away if it is exposed with a zero-day vulnerability.

To scan a single asset, go to the page for that asset by linking to it from any _Assets_ table on a site page, asset group page, or any other pertinent location. Click the **Scan asset now** button that appears below the asset information pane.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/759863d-s_nx_scan_asset_now.png",
        "s_nx_scan_asset_now.png",
        1998,
        541,
        "#f4f7f7"
      ],
      "caption": "Starting a scan for a single asset"
    }
  ]
}
[/block]
###How scanning a single asset works with asset linking

With asset linking enabled, an asset in multiple sites is regarded as a single entity. See [Linking assets across sites](doc:linking-assets-across-sites) for more information. If asset linking has been enabled in your InsightVM deployment, be aware of how it affects the scanning of individual assets.

####Asset linking and site permissions

With asset linking, an asset will be updated with scan data in every site, even if the user running the scan does not have access to at least one of the sites to which an asset belongs. For example: A user wants to scan a single asset that belongs to two sites, Los Angeles and Belfast. This user has access to the Los Angeles site, but not the Belfast site. But the scan will update the asset in the Belfast site.

####Asset linking and blackouts

Blackouts are scheduled periods in which scans are prevented from running. With asset linking enabled, if you attempt to scan an asset that belongs to any site with a blackout currently in effect, the Security Console displays a warning and prevents the scan from starting. If you are a Global Administrator, you can override the blackout.

##Changing settings for a manual scan

When you start a manual scan, the Security Console displays the _Start New Scan_ dialog box.

In the _Manual Scan Targets_ area, select either the option to scan all assets within the scope of a site, or to specify certain target assets. Specifying the latter is useful if you want to scan a particular asset as soon as possible, for example, to check for critical vulnerabilities or verify a patch installation.
[block:callout]
{
  "type": "warning",
  "body": "You can only manually scan assets that were specified as addresses or in a range."
}
[/block]
If you select the option to scan specific assets, enter their IP addresses or host names in the text box. Refer to the lists of included and excluded assets for the IP addresses and host names. You can copy and paste the addresses.
[block:callout]
{
  "type": "info",
  "body": "If you are scanning Amazon Web Services (AWS) instances, and if your Security Console and Scan Engine are located outside the AWS network, you do not have the option to manually specify assets to scan. See [Inside or outside the AWS network?](doc:managing-dynamic-discovery-of-assets#section-inside-or-outside-the-aws-network-)."
}
[/block]
Several configuration settings can expand your scanning options:

* If you are scanning a single asset that belongs to multiple sites, you can select the specific site to scan it in. This can be useful in situations such as verification of a Patch Tuesday update on a Windows asset.
* You can use a scan template other than the one assigned for the selected site. If, for example, you've addressed an issue that cause the asset to fail a PCI scan, you can apply the appropriate PCI template and confirm that the issue has been corrected.
* If you are scanning a site, you can use a Scan Engine other than the one assigned for the site. If you know that the currently assigned engine is in use, you can switch to a free one. Or you can change the perspective with which you will "see" the asset. For example, if the currently assigned engine is a Rapid7 Hosted engine, which provides an "outsider" view of your network, you can switch to a distributed engine located behind the firewall for an interior view.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/01d7dd3-s_nx_scan_progress_bar.png",
        "s_nx_scan_progress_bar.png",
        2599,
        458,
        "#eaf1f1"
      ],
      "caption": "The Start New Scan window"
    }
  ]
}
[/block]
Click the **Start Now** button to begin the scan immediately.
[block:callout]
{
  "type": "info",
  "body": "You can start as many manual scans as you want. However, if you have manually started a scan of all assets in a site, or if a full site scan has been automatically started by the scheduler, the application will not permit you to run another full site scan."
}
[/block]
When the scan starts, the Security Console displays a status page for the scan, which will display more information as the scan continues.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/7dca2cd-s_status_for_starting_scan.jpg",
        "s_status_for_starting_scan.jpg",
        2650,
        1383,
        "#ebf2f2"
      ],
      "caption": "The status page for a newly started scan"
    }
  ]
}
[/block]
##Monitoring the progress and status of a scan

###Viewing scan progress

When a scan starts, you can keep track of how long it has been running and the estimated time remaining for it to complete. You can even see how long it takes for the scan to complete on an indi­vidual asset. These metrics can be useful to help you anticipate whether a scan is likely to complete within an allotted window.

You also can view the assets and vulnerabilities that the in-progress scan is discovering if you are scanning with any of the following configurations:

* distributed Scan Engines (if the Security Console is configured to retrieve incremental scan results)
* the local Scan Engine (which is bundled with the Security Console)

If your scan includes asset groups and more than one Scan Engine is used, the table will list a count of Scan Engines used.

Viewing these discovery results can be helpful in monitoring the security of critical assets or determin­ing if, for example, an asset has a zero-day vulnerability.

To view the progress of a scan:

1. Locate the _Site Listing_ table on the _Home_ page.
2. In the table, locate the site that is being scanned.
3. In the _Status_ column, click the **Scan in progress** link.

OR

1. On the _Home_ page, locate the _Current Scan Listing for All Sites_ table.
2. In the table, locate the site that is being scanned.
3. In the _Progress_ column, click the **In Progress** link.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/af39a22-s_home_view_progress_of_scan.jpg",
        "s_home_view_progress_of_scan.jpg",
        2545,
        948,
        "#f1f5f7"
      ],
      "caption": "The progress links for scans that are currently running"
    }
  ]
}
[/block]
You will also find progress links in the _Site Listing_ table on the _Sites_ page or the _Current Scan Listing_ table on the page for the site that is being scanned.

When you click the progress link in any of these locations, the Security Console displays a progress page for the scan.

At the top of the page, the _Scan Progress_ table shows the scan’s current status, start date and time, elapsed time, estimated remaining time to complete, and total discovered vulnerabilities. It lists the number of assets that have been discovered, as well as the following asset information:

* _Active_ assets are those that are currently being scanned for vulnerabilities.
* _Completed_ assets are those that have been scanned for vulnerabilities.
* _Pending_ assets are those that have been discovered, but not yet scanned for vulnerabilities.

These values appear below a progress bar that indicates the percentage of completed assets. The bar is helpful for tracking progress at a glance and estimating how long the remainder of the scan will take. .

You can click the icon for the scan log to view detailed information about scan events. For more infor­mation, see [Viewing the scan log](doc:running-a-manual-scan#section-viewing-the-scan-log).

The _Completed Assets_ table lists assets for which scanning completed successfully, failed due to an error, or was stopped by a user.

The _Incomplete Assets_ table lists assets for which the scan is pending, in progress, or has been paused by a user. Additionally, any assets that could not be completely scanned because they went offline during the scan are marked _Incomplete_ when the entire scan job completes.
[block:callout]
{
  "type": "info",
  "body": "If a scan failed to complete and restarted, you may temporarily see duplicate entries for the same scan - one for the failed attempt and another for the new scan that has yet to complete."
}
[/block]
These tables list every asset's fingerprinted operating system (if available), the number of vulnerabilities discovered on it, and its scan duration and status. You can click the address or name link for any asset to view more details about, such as all the specific vulnerabilities discovered on it.

The table refreshes throughout the scan with every change in status. You can disable the automatic refresh by clicking the icon at the bottom of the table. This may be desirable with scans of large environments because the constant refresh can be a distraction.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/6862239-s_nx_scan_progress_bar.jpg",
        "s_nx_scan_progress_bar.jpg",
        2599,
        458,
        "#e7eeef"
      ],
      "caption": "A scan progress page with a single Scan Engine used"
    }
  ]
}
[/block]

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/0e49e80-s_nx_scan_progress_multiple_engines.jpg",
        "s_nx_scan_progress_multiple_engines.jpg",
        2016,
        1432,
        "#edf4f4"
      ],
      "caption": "A scan progress page with multiple Scan Engines used"
    }
  ]
}
[/block]
##Understanding different Scan Engine statuses

The scan progress page also reports the status of the Scan Engine used for the site.

If you are scanning an asset group that is configured to use the Scan Engine most recently used for each asset, you may see statuses reported for more than one Scan Engine. For more information, see [Determining how to scan each asset when scanning asset groups](doc:selecting-a-scan-engine-for-a-site#section-determining-how-to-scan-each-asset-when-scanning-asset-groups) .

The _Status_ column reports the status of the Scan Engine. These statuses correspond to the scan states. See [Understanding different scan states](doc:running-a-manual-scan#section-understanding-different-scan-states). An additional possible Scan Engine status is:

* _Unknown_: The Scan Engine could not be contacted. You can check whether the Scan Engine is running and reachable.

##Understanding different scan states

It is helpful to know the meaning of the various scan states listed in the _Status_ column of the _Scan Progress_ table. While some of these states are fairly routine, others may point to problems that you can troubleshoot to ensure better performance and results for future scans. It is also helpful to know how certain states affect scan data integration or the ability to resume a scan. In the _Status_ column, a scan may appear to be in any one of the following states:

_In progress_: A scan is gathering information on a target asset. The Security Console is importing data from the Scan Engine and performing data integration operations such as correlating assets or applying vulner­ability exceptions. In certain instances, if a scan’s status remains _In progress_ for an unusually long period of time, it may indicate a problem. See [Determining if scans with normal states are having problems](doc:running-a-manual-scan#section-determining-if-scans-with-normal-states-are-having-problems).

_Completed successfully_: The Scan Engine has finished scanning the targets in the site, and the Security Console has finished processing the scan results. If a scan has this state but there are no scan results displayed, see [Determining if scans with normal states are having problems](doc:running-a-manual-scan#section-determining-if-scans-with-normal-states-are-having-problems).

_Stopped_: A user has manually stopped the scan before the Security Console could finish importing data from the Scan Engine. The data that the Security Console had imported before the stop is integrated into the scan database, whether or not the scan has completed for an individual asset. You cannot resume a stopped scan. You will need to run a new scan.

_Paused_: One of the following events occurred:

* A scan was manually paused by a user.
* A scan has exceeded its scheduled duration window. If it is a recurring scan, it will resume where it paused instead of restarting at its next start date/time.
* A scan has exceeded the Security Console's memory threshold before the Secu­rity Console could finish importing of data from the Scan Engine

In all cases, the Security Console processes results for targets that have a status of _Completed Successfully_ at the time the scan is paused. You can resume a paused scan manually.
[block:callout]
{
  "type": "info",
  "body": "When you resume a paused scan, the application will scan any assets in that site that did not have a status of _Completed Successfully_ at the time you paused the scan. Since it does not retain the partial data for the assets that did not reach the completed state, it begins gathering information from those assets over again on restart."
}
[/block]
_Failed_: A scan has been disrupted due to an unexpected event. It cannot be resumed. An explanatory message will appear with the _Failed_ status. You can use this information to troubleshoot the issue with Technical Support. One cause of failure can be the Security Console or Scan Engine going out of service. In this case, the Security Console cannot recover the data from the scan that preceded the disruption.

Another cause could be a communication issue between the Security Console and Scan Engine. The Security Console typically can recover scan data that preceded the disruption. You can determine if this has occurred by one of the following methods:
* Check the connection between your Security Console and Scan Engine with a ICMP (ping) request.
* Click the _Administration_ tab and then go to the _Scan Engines_ page. Click on the **Refresh** icon for the Scan Engine associated with the failed scan. If there is a communication issue, you will see an error message.
* Open the nsc.log file located in the \nsc directory of the Security Console and look for error-level messages for the Scan Engine associated with the failure.

_Aborted_: A scan has been interrupted due to crash or other unexpected events. The data that the Security Con­sole had imported before the scan was aborted is integrated into the scan database. You cannot resume an aborted scan. You will need to run a new scan.

###Determining if scans with normal states are having problems

If a scan has an _In progress_ status for an unusually long time, this may indicate that the Security Con­sole cannot determine the actual state of the scan due to a communication failure with the Scan Engine. To test whether this is the case, try to stop the scan. If a communication failure has occurred, the Security Console will display a message indicating that no scan with a given ID exists.

If a scan has a _Completed successfully_ status, but no data is visible for that scan, this may indicate that the Scan Engine has stopped associating with the scan job. To test whether this is the case, try start­ing the scan again manually. If this issue has occurred, the Security Console will display a message that a scan is already running with a given ID.

In either of these cases, contact Technical Support.

##Pausing, resuming, and stopping a scan

If you are a user with appropriate site permissions, you can pause, resume or stop manual scans and scans that have been started automatically by the application scheduler.

You can pause, resume, or stop scans in several areas:
* the _Home_ page
* the _Sites_ page
* the page for the site that is being scanned
* the page for the actual scan

To pause a scan, click the **Pause** icon for the scan on the _Home_, _Sites_, or specific site page; or click the **Pause Scan** button on the specific scan page.

A message displays asking you to confirm that you want to pause the scan. Click **OK**.

To resume a paused scan, click the **Resume** icon for the scan on the _Home_, _Sites_, or specific site page; or click the **Resume Scan** button on the specific scan page. The console displays a message, asking you to confirm that you want to resume the scan. Click **OK**.

To stop a scan, click the **Stop** icon for the scan on the _Home_, _Sites_, or specific site page; or click the **Stop Scan** button on the specific scan page. The console displays a message, asking you to confirm that you want to stop the scan. Click **OK**.

The stop operation may take 30 seconds or more to complete pending any in-progress scan activity.

##Viewing scan results

The Security Console lists scan results by ascending or descending order for any category depending on your sorting preference. In the _Asset Listing_ table, click the desired category column heading, such as _Address_ or _Vulnerabilities_, to sort results by that category.

Two columns in the _Asset Listing_ table show the numbers of known exposures for each asset. The column with the ![Alt](https://files.readme.io/bec1647-Ch_Running_a_manual_scan00001.jpg)™ icon enumerates the number of vulnerability exploits known to exist for each asset. The number may include exploits available in Metasploit and/or the Exploit Database. The column with the ![Alt](https://files.readme.io/b967a3e-i_malware.jpg) icon enumerates the number of malware kits that can be used to exploit the vulnerabilities detected on each asset.

Click the link for an asset name or address to view scan-related, and other information about that asset. Remember that the application scans sites, not asset groups, but asset groups can include assets that also are included in sites.

To view the results of a scan, click the link for a site’s name on the _Home_ page. Click the site name link to view assets in the site, along with pertinent information about the scan results. On this page, you also can view information about any asset within the site by clicking the link for its name or address.

##Viewing the scan log

* [Finding the scan log](doc:running-a-manual-scan#section-finding-the-scan-log) 
* [Downloading the scan log](doc:running-a-manual-scan#downloading-the-scan-log) 
* [Tracking scan events in logs](doc:running-a-manual-scan#section-tracking-scan-events-in-logs) 

To troubleshoot problems related to scans or to monitor certain scan events, you can download and view the log for any scan that is in progress or complete.

###Understanding scan log file names

Scan log files have a .log extension and can be opened in any text editing program. A scan log’s file name consists of three fields separated by hyphens: the respective site name, the scan’s start date, and scan’s start time in military format. Example: localsite-20111122-1514.log.

If the site name includes spaces or characters not supported by the name format, these characters are converted to hexadecimal equivalents. For example, the site name _my site_ would be rendered as _my_20site_ in the scan log file name.

The following characters are supported by the scan log file format:
* numerals
* letters
* hyphens (-)
* underscores (_)

The file name format supports a maximum of 64 characters for the site name field. If a site name contains more than 64 characters, the file name only includes the first 64 characters.

You can change the log file name after you download it. Or, if your browser is configured to prompt you to specify the name and location of download files, you can change the file name as you save it to your hard drive.

###Finding the scan log

You can find and download scan logs wherever you find information about scans in the Web interface. You can only download scan logs for sites to which you have access, subject to your permissions.

* On the _Home_ page, in the _Site Listing_ table, click any link in the _Scan Status_ column for in-progress or most recent scan of any site. Doing so opens the summary page for that scan. In the _Scan Progress_ table, find the _Scan Log_ column.
* On any site page, click the **View scan history** button in the _Site Summary_ table. Doing so opens the _Scans_ page for that site. In the _Scan History_ table, find the _Scan Log_ column.
* The _Scan History_ page lists all scans that have been run in your deployment. On any page of the Web interface, click the **Administration** tab. On the _Administration_ page, click the **view** link for _Scan History_. In the _Scan History_ table, find the _Scan Log_ column.

###Downloading the scan log

To download a scan log click the **Download** icon for a scan log.

A pop-up window displays the option to open the file or save it to your hard drive. You may select either option.

If you do not see an option to open the file, change your browser configuration to include a default program for opening a .log file. Any text editing program, such as Notepad or gedit, can open a .log file. Consult the documentation for your browser to find out how to select a default program.

To ensure that you have a permanent copy of the scan log, choose the option to save it. This is recommended in case the scan information is ever deleted from the scan database.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/a6f0846-s_scan_page_scan_log.jpg",
        "s_scan_page_scan_log.jpg",
        2186,
        421,
        "#e5f0f3"
      ],
      "caption": "Downloading a scan log"
    }
  ]
}
[/block]
##Tracking scan events in logs

While the Web interface provides useful information about scan progress, you can use scan logs to learn more details about the scan and track individual scan events. This is especially helpful if, for example, certain phases of the scan are taking a long time. You may want to verify that the prolonged scan is running normally and isn't "hanging". You may also want to use certain log information to troubleshoot the scan.

This section provides common scan log entries and explains their meaning. Each entry is preceded with a time and date stamp; a severity level (DEBUG, INFO, WARN, ERROR); and information that identifies the scan thread and site.

####The beginning and completion of a scan phase

_2013-06-26T15:02:59 [INFO] [Thread: Scan default:1] [Site: Chicago_servers] Nmap phase started._ 
The Nmap (Network Mapper) phase of a scan includes asset discovery and port-scanning of those assets. Also, if enabled in the scan template, this phase includes IP stack fingerprinting.

_2013-06-26T15:25:32 [INFO] [Thread: Scan default:1] [Site: Chicago_servers] Nmap phase complete._ 
The Nmap phase has completed, which means the scan will proceed to vulnerability or policy checks.

####Information about scan threads

_2013-06-26T15:02:59 [INFO] [Thread: Scan default:1] [Site: Chicago_servers] Nmap will scan 1024 IP addresses at a time._ 
This entry states the maximum number of IP addresses each individual Nmap process will scan before that Nmap process exits and a new Nmap process is spawned. These are the work units assigned to each Nmap process. Only 1 Nmap process exists per scan.

_2013-06-26T15:04:12 [INFO] [Thread: Scan default:1] [Site: Chicago_servers] Nmap scan of 1024 IP addresses starting._
This entry states the number of IP addresses that the current Nmap process for this scan is scanning. At a maximum, this number can be equal to the maximum listed in the preceding entry. If this number is less than the maximum in the preceding entry, that means the number of IP addresses remaining to be scanned in the site is less than the maximum. Therefore, the process reflected in this entry is the last process used in the scan.

####Information about scan tasks within a scan phase

_2013-06-26T15:04:13 [INFO] [Thread: Scan default:1:nmap:stdin] [Site: Chicago_servers] Nmap task Ping Scan started._
A specific task in the Nmap scan phase has started. Some common tasks include the following:

* _Ping Scan:_ Asset discovery
* _SYN Stealth Scan:_ TCP port scan using the SYN Stealth Scan method (as configured in the scan template)
* _Connect Scan:_ TCP port scan using the Connect Scan method (as configured in the scan template)
* _UDP Scan:_ UDP port scan

_2013-06-26T15:04:44 [INFO] [Thread: Scan default:1:nmap:stdin] [Site: Chicago_servers] Nmap task Ping Scan is an estimated 25.06% complete with an estimated 93 second(s) remaining._ 
This is a sample progress entry for an Nmap task.

####Discovery and port scan status

_2013-06-26T15:06:04 [INFO] [Thread: Scan default:1:nmap:stdin] [Site: Chicago_servers] [10.0.0.1] DEAD (reason=no-response)_
The scan reports the targeted IP address as _DEAD_ because the host did not respond to pings.

_2013-06-26T15:06:04 [INFO] [Thread: Scan default:1:nmap:stdin] [Site: Chicago_servers] [10.0.0.2] DEAD (reason=host-unreach)_
The scan reports the targeted IP address as _DEAD_ because it received an _ICMP host unreachable_ response. Other ICMP responses include _network unreachable, protocol unreachable, administratively prohibited_. See the RFC4443 and RFC 792 specifications for more information.

_2013-06-26T15:07:45 [INFO] [Thread: Scan default:1:nmap:stdin] [Site: Chicago_servers] [10.0.0.3:3389/TCP] OPEN (reason=syn-ack:TTL=124)_
_2013-06-26T15:07:45 [INFO] [Thread: Scan default:1:nmap:stdin] [Site: Chicago_servers] [10.0.0.4:137/UDP] OPEN (reason=udp-response:TTL=124)_ 
The preceding two entries provide status of a scanned port and the reason for that status. _SYN-ACK_ reflects a SYN-ACK response to a SYN request. Regarding TTL references, if two open ports have different TTLs, it could mean that a man-in-the-middle device between the Scan Engine and the scan target is affecting the scan.

_2013-06-26T15:07:45 [INFO] [Thread: Scan default:1:nmap:stdin] [Site: Chicago_servers] [10.0.0.5] ALIVE (reason=echo-reply:latency=85ms:variance=13ms:timeout=138ms)_
This entry provides information on the reason that the scan reported the host as _ALIVE_, as well as the quality of the network the host is on; the latency between the Scan Engine and the host; the variance in that latency; and the timeout Nmap selected when waiting for responses from the target. This type of entry is typically used by Technical Support to troubleshoot unexpected scan behavior.  For example, a host is reported _ALIVE_, but does not reply to ping requests. This entry indicates that the scan found the host through a TCP response.

The following list indicates the most common reasons for discovery and port scan results as reported by the scan:

* _conn-refused_: The target refused the connection request.
* _reset_: The scan received an RST (reset) response to a TCP packet.
* _syn-ack_: The scan received a SYN|ACK response to a TCP SYN packet.
* _udp-response_: The scan received a UDP response to a UDP probe.
* _perm-denied_: The Scan Engine operating system denied a request sent by the scan. This can occur in a full-connect TCP scan. For example, the firewall on the Scan Engine host is enabled and prevents Nmap from sending the request.
* _net-unreach_: This is an ICMP response indicating that the target asset's network was unreachable. See the RFC4443 and RFC 792 specifications for more information.
* _host-unreach_: This is an ICMP response indicating that the target asset was unreachable. See the RFC4443 and RFC 792 specifications for more information.
* _port-unreach_: This is an ICMP response indicating that the target port was unreachable. See the RFC4443 and RFC 792 specifications for more information.
* _admin-prohibited_: This is an ICMP response indicating that the target asset would not allow ICMP echo requests to be accepted. See the RFC4443 and RFC 792 specifications for more information.
* _echo-reply_: This is an ICMP echo response to an echo request. It occurs during the asset discovery phase.
* _arp-response_: The scan received an ARP response. This occurs during the asset discovery phase on the local network segment.
* _no-response_: The scan received no response, as in the case of a filtered port or dead host.
* _localhost-response_: The scan received a response from the local host. In other words, the local host has a Scan Engine installed, and it is scanning itself.
* _user-set_: As specified by the user in the scan template configuration, host discovery was disabled. In this case, the scan does not verify that target hosts are alive; it "assumes" that the targets are alive.

##Viewing history for all scans

You can quickly browse the scan history for your entire deployment by seeing the _Scan History_ page.

On any page of the Web interface, click the **Administration** icon. On the _Administration_ page, click the **view** link for _Scan History_.

The interface displays the _Scan History_ page, which lists all scans, plus who started or restarted the scan, the total number of scanned assets, discovered vulnerabilities, and other information pertaining to each scan. You can click the date link in the _Completed_ column to view details about any scan.

You can download the log for any scan as discussed in the preceding topic.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/75122df-s_scan_history_show_user.JPG",
        "s_scan_history_show_user.JPG",
        1117,
        359,
        "#ecf1f4"
      ],
      "caption": "Viewing scan history"
    }
  ]
}
[/block]