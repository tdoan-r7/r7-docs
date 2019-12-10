---
title: "Authentication on Windows: best practices"
excerpt: ""
---
When scanning Windows assets, we recommend that you use domain or local administrator accounts in order to get the most accurate assessment. Administrator accounts have the right level of access, including registry permissions, file-system permissions, and either the ability to connect remotely using Common Internet File System (CIFS) or Windows Management Instrumentation (WMI) read permissions. In general, the higher the level of permissions for the account used for scanning, the more exhaustive the results will be. If you do not have access, or want to limit the use of domain or local administrator accounts within the application, then you can use an account that has the following permissions:

* The account should be able to log on remotely and not be limited to Guest access.
* The account should be able to read the registry and file information related to installed software and operating system information.

**Note:**  If you are not using administrator permissions then you will not be granted access to administrator shares and non-administrative shares will need to be created for read access to the file system for those shares.

InsightVM and the network environment should also be configured in the following ways:

* For scanning domain controllers, you must use a domain administrator account because local administrators do not exist on domain controllers.
* Make sure that no firewalls are blocking traffic from the InsightVM Scan Engine to port 135, either 139 or 445 (see note), and a random high port for WMI on the Windows endpoint. You can set the random high port range for WMI using WMI Group Policy Object (GPO) settings.

**Note:**  Port 445 is preferred as it is more efficient and will continue to function when a name conflict exists on the Windows network.

* If using a domain administrator account for your scanning, make sure that the domain administrator is also a member of the local administrators group. Otherwise, domain administrators will get treated as non-administrative users. If domain administrators are not members of local administrators, they may have limited to no access, and also User Account Control (UAC) will block their access unless the next step is taken.
* If you are using a local administrator with UAC, you must add a DWORD registry key value ```HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\system\LocalAccountTokenFilterPolicy``` and set the value to **1**. Make sure it is a DWORD and not a string.
* If running an antivirus tool on the Scan Engine host, make sure that antivirus whitelists the application and all traffic that the application is sending to the network and receiving from the network. Having antivirus inspecting the traffic can lead to performance issues and potential false-positives.
* Verify that the account being used can log on to one or more of the assets being assessed by using the [Test Credentials](doc:configuring-site-specific-scan-credentials#section-testing-the-credentials) feature in the application.
* If you are using CIFS, make sure that assets being scanned have Remote Registry service enabled. If you are using WMI, then the Remote Registry service is not required.
[block:callout]
{
  "type": "info",
  "title": "TIP",
  "body": "Limiting permissions on credentials will affect the visibility of your scans.  If your organization’s policies restrict or prevent any of these configuration methods, consider deploying Insight Agents on your target assets as an alternative collection method.\n\nRead more about the Insight Agent on our [Help pages](https://insightagent.help.rapid7.com/docs/overview)."
}
[/block]