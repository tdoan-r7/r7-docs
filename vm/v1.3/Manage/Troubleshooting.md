---
title: "Troubleshooting"
excerpt: ""
---
This section provides descriptions of problems commonly encountered when using the application and guidance for dealing with them. If you do need to contact Technical Support, this section will help you gather the information that Support needs to assist you.

##Working with log files

If you are encountering problems with the Security Console or Scan Engine, you may find it helpful to consult log files for troubleshooting. Log files can also be useful for routine maintenance and debugging purposes.

The section does not cover the scan log, which is related to scan events. See [Viewing the scan log](doc:troubleshooting#section-viewing-the-scan-log).

###Locating each log file and understanding its purpose

Log files are located in [installation_directory]/nsc/logs directory on the Security Console and [installation_directory]/nse/logs on Scan Engines. The following log files are available:
* _access.log_ (on the Security Console only): This file captures information about resources that are being accessed, such as pages in the Web interface. At the INFO level, access.log captures useful information about API events, such as APIs that are being called, the API version, and the IP address of the API client. This is useful for monitoring API use and troubleshooting API issues. The file was called *access_log* in earlier product versions.
* _auth.log_ (on the Security Console only): This file captures each logon or logoff as well as authentication events, such as authentication failures and lockouts. It is useful for tracking user sessions. This file was called *um_log* in earlier product versions.
* _nsc.log_ (on the Security Console only): This file captures system- and application-level events in the Security Console. It is useful for tracking and troubleshooting various issues associated with updates, scheduling of operations, or communication issues with distributed Scan Engines. Also, if the Security Console goes into Maintenance Mode, you can log on as a global administrator and use the file to monitor Maintenance Mode activity.
* _nse.log_ (on the Security Console and distributed Scan Engines): This file is useful for troubleshooting certain issues related to vulnerability checks. For example, if a check produces an unexpected result, you can look at the nse.log file to determine how the scan target was fingerprinted. On distributed Scan Engines only, this file also captures system- and application-level events not recorded in any of the other log files.
* _mem.log_ (on the Security Console and distributed Scan Engines): This file captures events related to memory use. It is useful for troubleshooting problems with memory-intensive operations, such as scanning and reporting.
* _bootstrap.\*.log_: This file contains relevant logs for the installation and registration of the collector.
* _collector.log\*_: This file contains relevant logs for general collector errors.
* *engine\_communication.log*: This file contains relevant logs for communication between the Security Console and remote scan engines.
* _eso.log_: This file contains relevant logs for Automated Actions.
* _initdb.log_: This file contains relevant logs for the database.

In earlier product versions, API information was stored in nsc.log.

###Structure and contents of log files

Log files have the following format:
```
[yyyy-mm-ddThh:mm:ss GMT] [LEVEL] [Thread: NAME] [MESSAGE]
```
Example:
```
2011-12-20T16:54:48 [INFO] [Thread: Security Console] Security Console started in 12 minutes 54 seconds
```
The date and time correspond to the occurrence of the event that generates the message.

Every log message has a severity level:
[block:parameters]
{
  "data": {
    "h-0": "Level",
    "h-1": "Meaning",
    "h-2": "Example",
    "0-0": "ERROR",
    "0-1": "an abnormal event that prevents successful execution of system processes and can prevent user operations, such as scanning",
    "0-2": "the Security Console’s failure to connect to the database",
    "1-0": "WARN",
    "1-1": "an abnormal event that prevents successful execution of system processes but does not completely prevent a user operation, such as scanning",
    "1-2": "disruption in communication between the Security Console and a remote Scan Engine",
    "2-0": "INFO",
    "2-1": "a normal, expected event that is noteworthy for providing useful information about system activity",
    "2-2": "the Security Console’s attempts to establish a connection with a remote Scan Engine",
    "3-0": "DEBUG",
    "3-1": "a normal, expected event that need not be viewed except for debugging purposes",
    "3-2": "the execution of operations within the Security Console/Scan Engine protocol"
  },
  "cols": 3,
  "rows": 4
}
[/block]
When reading through a log file to troubleshoot major issues, you may find it useful look for ERROR- and WARN-level messages initially.
_Thread_ identifies the process that generated the message.

###Configuring which log severity levels are displayed

By default, all log files display messages with severity levels of INFO and higher. This means that they display INFO, WARN, ERROR messages and do not display DEBUG messages. You can change which severity levels are displayed in the log files. For example, you might want to filter out all messages except for those with WARN and ERROR severity levels. Or, you may want to include DEBUG messages for maintenance and debugging purposes.

Configuration steps are identical for the Security Console and distributed Scan Engines. To configure which log severity levels are displayed, take the following steps:
[block:callout]
{
  "type": "info",
  "body": "In the user-log-settings.xml file, default refers to the nsc.log file or nse.log file, depending on whether the installed component is the Security Console or a distributed Scan Engine."
}
[/block]
1. In a text editor, open the user-log-settings.xml file, which is located in the [installation_directory]/nsc/conf directory.
2. Un-comment the following line by removing the opening and closing comment tags: ```<!--``` and ```-->```:
```<!-- <property name="default-level" value="INFO"/> -->```
3. If you want to change the logging level for the nsc.log (for Security Console installations) or nse.log file (for Scan Engine installations), leave the value _default_ unchanged. Otherwise, change the value to one of the following to specify a different log file:
   * auth
   * access
   * mem
4. Change the value in the line to your preferred severity level: DEBUG, INFO, WARN, or ERROR. Example: ```<property name="default-level" value="DEBUG"/>```
5. To change log levels for additional log files, simply copy and paste the un-commented line, changing the values accordingly. Examples:
```
<property name="default-level" value="DEBUG"/>
<property name="auth-level" value="DEBUG"/>
<property name="access-level" value="DEBUG"/>
<property name="mem-level" value="DEBUG"/>
```
6. Save and close the file.

The change is applied after approximately 30 seconds.

##Send diagnostic logs to Rapid7 Support

Diagnostic logs generated by the Security Console and Scan Engines can be sent to Rapid7 Support via the diagnostics page:

1. In your Security Console, navigate to the **Administration** page.
2. Under the “Maintenance, Storage and Troubleshooting” section, click **Diagnose**. 
3. Check the desired diagnostics boxes.
4. Click **Send Logs**.

##Send logs via a proxy server

If the Security Console does not have direct internet access, you can use a proxy server for sending logs to Rapid7 Support.

To configure proxy settings for sending logs:

1. In your Security Console, navigate to the **Administration** page.
2. Under the "Global and Console Settings" section, click **Administer**.
3. Click the **Proxy Settings** tab.
4. Enter the proxy server information in the appropriate fields.
   * The “Name or address” field refers to the fully qualified domain name or IP address of the proxy server.
   * The “Port” field is the port number on the proxy server that the Security Console connects to when sending log files.
   * The Security Console uses the information in the “Domain,” “User ID,” and “Password” fields to be authenticated on the proxy server.
5. Check the “Send support logs” box.
6. Click **Save**. 

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/0509b8a-proxy_settings.png",
        "proxy_settings.png",
        1527,
        579,
        "#c5c6c8"
      ],
      "caption": "Security Console Configuration panel - Proxy Settings for sending logs to Rapid7 Support"
    }
  ]
}
[/block]
##Troubleshooting scan accuracy issues with logs

If your scans are producing inaccurate results, such as false positives, false negatives, or incorrect fingerprints, you can use a scan logging feature to collect data that could help the Technical Support team troubleshoot the cause. Enhanced logging is a feature that collects information useful for troubleshooting, such as Windows registry keys, SSH command executions, and file versions, during a scan.

Following is a sample from an Enhanced logging file:
```
<ace:collected_object>
<ace:source-id>0</ace:source-id>
<ace:thread-activity>do-unix-create-system-fingerprint@example.com:22</ace:thread-activity>
<ace:remote_execution_item id="42">
<ace:command>freebsd-version</ace:command>
<ace:rc datatype="int">0</ace:rc>
<ace:stdin status="does not exist"/>
<ace:stdout>10.0-RELEASE
</ace:stdout>
<ace:stderr status="does not exist"/>
<ace:start_time datatype="int">1443208125966</ace:start_time>
<ace:end_time datatype="int">1443208125982</ace:end_time>
</ace:remote_execution_item>
</ace:collected_object>
```
Using this feature involves two major steps:
1. Run a scan with a template that has Enhanced logging fully enabled on assets where inaccurate results are occurring.
2. Send a file containing Enhanced logging data to Technical Support.
[block:callout]
{
  "type": "info",
  "body": "It is recommended that you scan individual assets or small sites with Enhanced Logging enabled."
}
[/block]
#####Enable Enhanced logging in a custom scan template

Enhanced Logging is enabled by default on the Asset Configuration Export scan template. You may, however, want to scan with a custom template which has been tuned to perform better in your specific environment. To enable Enhanced logging on a custom scan template:
1. Click the Administration icon.
2. In the Scan Options area, click the Create link to create a new template or click the Manage link to create a custom template based on an existing template.
3. If you clicked the Manage link, select a template that you want to base the new template on click the Copy icon.
4. In the configuration of the new template, click the Logging tab.
5. Select the **Enhanced logging** check box to enable Enhanced logging.
6. Configure the rest of the template as desired and save it.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/dacf9ec-s_nx_scan_template_ACES.png",
        "s_nx_scan_template_ACES.png",
        1161,
        651,
        "#1e2838"
      ]
    }
  ]
}
[/block]
#####Run an authenticated scan with the Enhanced logging-enabled template

If you want to scan an entire site with the template, add it to a site configuration and then scan the site. See [Selecting a scan template](doc:selecting-a-scan-template).
[block:callout]
{
  "type": "info",
  "body": "Enhanced logging gathers a significant amount of data, which may impact disk space, depending on the number off assets you scan."
}
[/block]
If you want to manually scan a specific asset with the template, add the template in the scan dialog. See [Running a manual scan](doc:running-a-manual-scan).

#####Retrieve the collected Enhanced logging data and send it to Technical Support

Access the summary page of the desired scan to download the enhanced logging scan data:

1. On the **Home** tab of your Security Console, browse to the "Sites" table.
2. Click the corresponding link in the "Scan Status" column to open the summary page for your desired scan.
3. Click **Download \> Scan data**.
4. Send the downloaded zip file to Rapid7 Support via the [Support Portal](https://rapid7support.force.com/customers/login).
[block:callout]
{
  "type": "warning",
  "title": "NOTE",
  "body": "If the zip file is larger than 25MB, a Rapid7 Support engineer will facilitate a secure file transfer for your use."
}
[/block]
###Reporting incorrectly identified OS

You can report incorrectly fingerprinted Operating Systems by clicking on the _Report an incorrectly identified asset_ icon next to the listed OS on the _Asset_ or _Node_ page.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/7e87bd1-report-incorrect-fingerprint-os.png",
        "report-incorrect-fingerprint-os.png",
        847,
        367,
        "#f8faf9"
      ]
    }
  ]
}
[/block]
##Running diagnostics

You can run several diagnostic functions to catch issues that may be affecting system performance.

###Selecting diagnostic routines

To run diagnostics for internal application issues:
1. Click the **Administration** tab.
2. The Security Console displays the _Administration_ page.
3. Click **Diagnose** next to _Troubleshooting_.
The Security Console displays the _Troubleshooting_ page.
4. Click the check box for each diagnostics routine you want to perform.

After performing the requested diagnostics, the Security Console displays a table of results. Each item includes a red or green icon, indicating whether or not an issue exists with the respective system component.

##Addressing a failure during startup

If a subsystem critical error occurs during startup, then the application will attempt to queue an appropriate maintenance task to respond to that failure. Afterward, it restarts in maintenance mode.

If you are an administrator, you can log on and examine the cause of failure. If required, you can take certain steps to troubleshoot the issue.

Two types of recovery tasks are available:

* _DBConfig_ task is triggered when the application is unable to connect to the configured database. It allows you to test the database configuration settings and save it upon success.
* _Recovery_ task is a general recovery task that is triggered when an unknown failure occurs during startup. This is very rare and happens only when one or more of the configuration files is not found or is invalid. This task allows you to view the cause of the failure and upload support logs to a secure log server, where they can be used for troubleshooting.

The application may fail to restart in maintenance mode in case of extremely critical failures if the maintenance Web server does not have the default port 3780 available. This may happen if there is already an instance of it running, or if one or more of the key configuration files is invalid or missing. These files have extensions such as _.nsc_, _.xml_, and _.userdb_.

##Addressing failure to refresh a session

When the Web interface session times out in an idle session, the Security Console displays the logon window so that the user can refresh the session. If a communication issue between the Web browser and the Security Console Web server prevents the session from refreshing, a user will see an error message. If the user has unsaved work, he or she should not leave the page or close the browser because the work may not be lost after the communication issue is resolved.

A communication failure may occur for one of the following reasons. If any of these is the cause, take the appropriate action:
* The Security Console is offline. Restart the Security Console.
* The Security Console has been disconnected from the Internet. Reconnect the Security Console to the Internet.
* The user’s browser has been disconnected from the Internet. Reconnect the browser to the Internet.
* The Security Console address has changed. Clear the address resolution protocol (ARP) table on the computer hosting the browser.

An extreme delay in the Security Console’s response to the user’s request to refresh the session also may cause the failure message to appear.

##Resetting account lockout

When a user attempts to log on too many times with an incorrect password, the application locks out the user until the lockout is reset for that user.

The default lockout threshold is 4 attempts. A global administrator can change this parameter on the _Security Console Configuration—Web Server_ page. See [Changing the Security Console Web server default settings](doc:managing-the-security-console#section-changing-the-security-console-web-server-default-settings).

You can reset the lockout using one of the following three methods:
* If you’re a global administrator, go to the _Users_ page, and click the padlock icon that appears next to the locked out user's name.
* Run the console command ```unlock account```. [Using the command console](doc:using-the-command-console).
* Restart the Security Console. This is the only method that will work if the locked out user is the only global administrator in your organization.

##Long or hanging scans

Occasionally, a scan will take an unusually long time, or appear to have completely stopped.

It is not possible to predict exactly how long a scan should take. Scan times vary depending on factors such as the number of target assets and the thoroughness or complexity of the scan template. However, you can observe whether a scan is taking an exceptionally long time to complete by comparing the scan time to that of previous scans.

In general, if a scan runs longer than eight hours on a single host, or 48 hours on a given site, it is advisable to check for certain problems.

###Tip for addressing delayed scan operations

If you attempt to start, pause, resume, or stop a scan, and a message appears for a long time indicating that the operation is in progress, this may be due to a network-related delay in the Security Console's communication with the Scan Engine. In networks with low bandwidth or high latency, delayed scan operations may result in frequent time-outs in Security Console/Scan Engine communication, which may cause lags in the Security Console receiving scan status information. To reduce time-outs, you can increase the Scan Engine response time out setting. See [Configuring Security Console connections with distributed Scan Engines](doc:managing-the-security-console#section-configuring-security-console-connections-with-distributed-scan-engines).

###Scan memory issues

Scans can be slow, or can fail, due to memory issues. See [Out-of-memory issues](doc:troubleshooting#section-out-of-memory-issues).

###Scan complexity

For every target host that it discovers, the application scans its ports before running any vulnerability checks. The range of target ports is a configurable scan template setting. Scan times increase in proportion to the number of ports scanned.

In particular, scans of UDP ports can be slow, since the application, by default, sends no more than two UDP packets per second in order to avoid triggering the ICMP rate-limiting mechanisms that are built into TCP/IP stacks for most network devices.

To increase scan speed, consider configuring the scan to only examine well-known ports, or specific ports that are known to host relevant services. See [Working with scan templates and tuning scan performance](doc:working-with-scan-templates-and-tuning-scan-performance).

###Scan Engine offline

If the Scan Engine goes off line during the scan, the scan will appear to hang. When a Scan Engine goes off line during the scan, the database will need to remove data from the incomplete scan. This process leaves messages similar to the following the scan log:
```DBConsistenc3/10/09 12:05 PM: Inconsistency discovered for dispatched scan ID 410, removing partially imported scan results...```

If a Scan Engine goes offline, restart it. Then, go the Scan Engine Configuration panel to confirm that the Scan Engine is active. See [Configuring distributed Scan Engines](doc:configuring-distributed-scan-engines).

###Viewing the scan log

You can download an activity log for a completed scan or send a scan data package directly to Support for troubleshooting purposes.

To access these log options:
1. On the **Home** page of your Security Console, browse to the "Sites" table.  Click the name of the site you want to inspect to open it.
2. In the "Site Scan Summary" section, click **View Scan History**.
3. Browse to the "Past Scans" table:
 * To download a scan log for the past scan of your choosing, click the corresponding icon in the "Download Log" column.
 * To send a scan data package to Support for troubleshooting purposes, click the icon in the "Send log" column.

Alternatively, scan log and data options are also available from the "Scan Progress" section of the past scan detail view.  Click the date and time link in the "Completed" column to access this page for a particular past scan.
[block:callout]
{
  "type": "info",
  "title": "Scan data packages",
  "body": "The **Scan data** package also includes the scan log, but is much larger and contains information usable only by the Support team for troubleshooting purposes."
}
[/block]
###Scan stopped by a user

If another user stops a scan, the scan will appear to have hung. To determine if this is the case, examine the log for a message similar to the following:
```
InsightVM3/16/09 7:22 PM: Scan [] stopped: "maylor" <>
```
See [Viewing the scan log](doc:troubleshooting#section-viewing-the-scan-log).

##Long or hanging reports

Occasionally, report generation will take an unusually long time, or appear to have completely stopped. You can find reporting errors in the Security Console logs.

###Reporting memory issues

Report generation can be slow, or can fail, due to memory issues. See [Out-of-memory issues](doc:troubleshooting#section-out-of-memory-issues).

###Stale scan data

Database speed affects reporting speed. Over time, data from old scans will accumulate in the database. This causes the database to slow down.

If you find that reporting has become slow, look in the Security Console logs for reporting tasks whose durations are inconsistent with other reporting tasks, as in the following example:
```
nsc.log.0:Reportmanage1/5/09 3:00 AM: Report task serviceVulnStatistics finished in 2 hours 1 minute 23 seconds
```
You can often increase report generation speed by cleaning up the database. Regular database maintenance removes leftover scan data and host information. See [Viewing the scan log](doc:troubleshooting#section-viewing-the-scan-log) and [Database backup/restore and data retention](doc:database-backuprestore-and-data-retention).

##Out-of-memory issues

Scanning and reporting are memory-intensive tasks, so errors related to these activities may often be memory issues. You can control memory use by changing settings. Some memory issues are related how system resources are controlled.

###java.lang.OutofMemoryError

If the application has crashed, you can verify that the crash was due to lack of memory by checking the log files for the following message:
```java.lang.OutOfMemoryError: Java heap space```

If you see this message, contact Technical Support. Do not restart the application unless directed to do so.

###Fixing memory problems

Since scanning is memory-intensive and occurs frequently, it is important to control how much memory scans use so that memory issues do not, in turn, affect scan performance. There are a number of strategies for ensuring that memory limits do not affect scans.

####Reduce scan complexity

As the number of target hosts increases, so does the amount of memory needed to store scan information. If the hosts being scanned have an excessive number of vulnerabilities, scans could hang due to memory shortages.

To reduce the complexity of a given scan, try a couple of approaches:
* Reduce the number of target hosts by excluding IP addresses in your site configuration.
* Reduce the number of target vulnerabilities by excluding lower-priority checks from your scan template.

After patching any vulnerabilities uncovered by one scan, add the excluded IP addresses or vulnerabilities to the site configuration, and run the scan again.

For more information, see [Configuring distributed Scan Engines](doc:configuring-distributed-scan-engines) and [Working with scan templates and tuning scan performance](doc:working-with-scan-templates-and-tuning-scan-performance).

####Reduce Scan Count

Running several simultaneous scans can cause the Security Console to run out of memory. Reduce the number of simultaneous scans to conserve memory.

####Upgrade Hosts

If scans are consistently running out of memory, consider adding more memory to the servers. To add memory, it might be necessary to upgrade the server operating system as well. On a 64-bit operating system, the application can address more memory than when it runs on a 32-bit operating system. However, it requires 8 Gb of memory to run on a 64-bit operating system.

####More information on managing scan-related resources

See the following chapters for more detailed information on making scans more memory-friendly:

* [Planning a deployment](doc:planning-a-deployment).
* [Working with scan templates and tuning scan performance](doc:working-with-scan-templates-and-tuning-scan-performance).

##Update failures

Occasionally, system updates will be unsuccessful. You can find out why by examining the system logs.

###Corrupt update table

The application keeps track of previously-applied updates in an update table. If the update table becomes corrupt, the application will not know which updates need to be downloaded and applied.

If it cannot install updates due to a corrupt update table, the Scan Console log will contain messages similar to the following:
```
AutoUpdateJo3/12/09 5:17 AM: NSC update failed: com.rapid7.updater.UpdateException: java.io.EOFException
at com.rapid7.updater.UpdatePackageProcessor.getUpdateTable(Unknown Source)
at com.rapid7.updater.UpdatePackageProcessor.getUpdates(Unknown Source)
at com.rapid7.updater.UpdatePackageProcessor.getUpdates(Unknown Source)
at com.rapid7.nexpose.nsc.U.execute(Unknown Source)
at com.rapid7.scheduler.Scheduler$_A.run(Unknown Source)
```
If this occurs, contact Technical Support. See [Viewing the scan log](doc:troubleshooting#section-viewing-the-scan-log.

##Interrupted update

By default, the application automatically downloads and installs updates. The application may download an update, but its installation attempt may be unsuccessful.

You can find out if this happened by looking at the scan log.

Check for update time stamps that demonstrate long periods of inactivity.
```
AU-BE37EE72A11/3/08 5:56 PM: updating file: nsc/htroot/help/html/757.htm
NSC 11/3/08 9:57 PM: Logging initialized (system time zone is SystemV/PST8PDT)
```
You can use the ```update now``` command prompt to re-attempt the update manually:
1. Click the **Administration** tab to go to the _Administration_ page.
2. Click **Run** console commands in the Troubleshooting section. 
The _Command Console_ page appears.
3. Enter the command ```update now``` in the text box and click **Execute**.

The Security Console displays a message to indicate whether the update attempt was successful. See [Viewing the scan log](doc:troubleshooting#section-viewing-the-scan-log).

###Corrupt File

If the application cannot perform an update due to a corrupt file, the Scan Console log will contain messages similar to the following:
```
AU-892F7C6793/7/09 1:19 AM: Applying update id 919518342
AU-892F7C6793/7/09 1:19 AM: error in opening zip file
AutoUpdateJo3/7/09 1:19 AM: NSC update failed: com.rapid7.updater.UpdateException:
java.util.zip.ZipException: error in opening zip file
at com.rapid7.updater.UpdatePackageProcessor.B(Unknown Source)
at com.rapid7.updater.UpdatePackageProcessor.getUpdates(Unknown Source)
at com.rapid7.updater.UpdatePackageProcessor.getUpdates(Unknown Source)
at com.rapid7.nexpose.nsc.U.execute(Unknown Source)
at com.rapid7.scheduler.Scheduler$_A.run(Unknown Source)
```
If the update fails due to a corrupt file, it means that the update file was successfully downloaded, but was invalid. If this occurs, contact Technical Support. See [Viewing the scan log](doc:troubleshooting#section-viewing-the-scan-log).

###Interrupted connection to the update server

If a connection between the Security Console and the update server cannot be made, it will appear in the logs with a message similar to the following.
```
AU-A7F0FF3623/10/09 4:53 PM: downloading update: 919518342
AutoUpdateJo3/10/09 4:54 PM: NSC update failed: java.net.SocketTimeoutException
```
The java.net.SocketTimeoutException is a sign that a connection cannot be made to the update server. If the connection has been interrupted, other updates prior to the failure will have been successful.

You can use the update now command prompt to re-attempt the update manually. See [Interrupted update](doc:troubleshooting#section-interrupted-update) and [Viewing the scan log](doc:troubleshooting#section-viewing-the-scan-log).