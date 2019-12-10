---
title: "Managing versions, updates, and licenses"
excerpt: ""
---
This section addresses how to keep the application updated.

##Viewing version and update information

It is important to keep track of updates and to know which version of the application you are running. For example, a new vulnerability check may require the latest product update in order to work. If you are not seeing expected results for that check, you may want to verify that the application has installed the latest product update. Also, if you contact Technical Support with an issue, the support engineer may ask you which version and update of the application you are running.

1. Click the **Administration** tab of the Security Console interface.
The Security Console displays the _Administration_ page.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/c973da1-s_home_new_administrationtab.jpg",
        "s_home_new_administrationtab.jpg",
        643,
        694,
        "#222425"
      ],
      "caption": "Administration tab"
    }
  ]
}
[/block]
2. In Global and Console Settings, click **Administer**.  
The _General_ page of the Security Console Configuration panel will display.
On this page you can view the current version of the application. You can also view the dates and update IDs for the current product and content updates. Release announcements always include update IDs, so you can match the IDs displayed on the Security Console page with those in the announcement to verify that you are running the latest updates.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/b8fdf1e-s_security_console_general_nexpose.jpg",
        "s_security_console_general_nexpose.jpg",
        1833,
        878,
        "#1c2736"
      ],
      "caption": "The General page of the Security Console Configuration panel"
    }
  ]
}
[/block]
##Viewing, activating, renewing, or changing your license

On the _Licensing_ page, you can see license-related information about your Security Console. You also can activate a new license or start the process to modify or renew your license. Your Security Console must be connected to the Internet to activate your license.
[block:callout]
{
  "type": "info",
  "body": "If your Security Console is not connected to the Internet, see [Managing updates without an Internet connection](doc:managing-versions-updates-and-licenses#section-managing-updates-without-an-internet-connection)."
}
[/block]
The _License Activation_ area displays general information about your license.
* If your license is _active_, you will see a link for contacting Rapid7 to modify your license, which is optional.
* If your license is _expired_, you will see a link for contacting Rapid7 to renew your license. You will need an active license in order to run scans and create reports.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/1c0d2fb-s_nx_activate_1st_step.jpg",
        "s_nx_activate_1st_step.jpg",
        1799,
        916,
        "#1d2837"
      ],
      "caption": "The Licensing page with the activation button"
    }
  ]
}
[/block]
####Activating your license with a license key

If your Security Console has Internet access, you can activate your license with a license key. Provided to you by the Account Management team, the key is a string of 16 numbers and letters separated into four groups by hyphens.

1. On the _Licensing_ page, click **Activate a New License**.
The Security Console displays a text box.
2. Enter the key in the text box.
You can copy the key from the e-mail that was sent to you from the Account Management team.
3. Click **Activate with key**.
The Security Console displays a success message.
You do not have to click **Save**. The application does not have to restart.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/4dc7dd8-s_nx_activate_key.jpg",
        "s_nx_activate_key.jpg",
        1802,
        762,
        "#1b2737"
      ],
      "caption": "Entering a license key for activation"
    }
  ]
}
[/block]
####Activating your license with a license file

Watch a [video](https://kb.help.rapid7.com/docs/nexpose-videos#section-activating-nexpose-with-a-license-file) about this feature.

If your Security Console does not have access to the Internet or to the updates.rapid7.com server, you can activate your license with a license file. Provided to you by the Account Management team, this file has a _.lic_ extension and lists all the features and scanning capacities that are available with your license.

To activate with a license file:
1. After you receive the license file from the Account Management team, download it.
2. Using the computer that you downloaded the file on, log onto the Security Console.
3. Click the **Administration** tab.
The Security Console displays the _Administration_ page.
4. Click the **Manage** link for _Security Console_.
The Security Console displays the _Security Console Configuration_ panel.
5. Click **Licensing** in the left navigation pane.
The Security Console displays the _Licensing_ page.
6. Click **Activate a New License**.
7. Click the link labeled **Use a license file**.
A button appears for choosing a file.
8. Click the **Choose file** button.
9. Find the downloaded _.lic_ file in your file system and select it.
The file name appears on the _Licensing_ page.
10. Click the **Activate with file** button.
The Security Console displays a success message.
11. Click the **OK** button.
The _Licensing_ page refreshes and displays the updated license information in the _License Details_ area.
You do not have to click **Save**, and the Security Console does not have to restart.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/a2f5bee-s_nx_activate_file.jpg",
        "s_nx_activate_file.jpg",
        1835,
        729,
        "#1b2736"
      ],
      "caption": "Uploading a license file for activation"
    }
  ]
}
[/block]
####Viewing license details

In the _License Details_ area of the _Licensing_ page, you can see more information about your license:
* The value for _License Status_ is one of four different modes, depending on the status of your license.
* The value for _Expiration_ is the date that your current license expires.
* The value for _Max. Scan Engines_ is the total number of internal Scan Engines that you can use. These Scan Engines can be installed on any host computers on your network.
* The value for _Max. Assets to Scan_ is the total number of assets that you can scan with your internal Scan Engines.
* The value for _Max. Assets to Scan w/ Hosted Engine_ is the total number of assets that you can scan with a Hosted Scan Engine.
* If the value for _SCADA Scanning_ is Enabled, you can scan assets with the SCADA scan template. For a description of this template, see [Where to find SCAP update information and OVAL files](doc:scap-compliance#section-where-to-find-scap-update-information-and-oval-files).
* If the value for _Discovery Scanning is Enabled_, you can run discovery scans to determine what assets are available on your network without performing vulnerability checks on those assets.
* If the value for _PCI Reporting is Enabled_, you can create reports using the PCI Executive Overview and PCI Audit report templates. If this feature is disabled, it will still appear to be available in your scan template, but it will not be active during scans.
* If the value for _Web Application Scanning is Enabled_, you can scan Web applications with the spider. If this feature is disabled, it will still appear to be available in your scan template, but it will not be active during scans.
* If the value for _Policy Scanning is Enabled_, you can scan assets to verify compliance with configuration policies. If this feature is disabled, it will still appear to be available in your scan template, but it will not be active during scans.

##Managing updates with an Internet connection

By default, the Security Console automatically downloads and applies two types of updates.

###Content updates

Content updates include new checks for vulnerabilities, patch verification, and security policy compliance. Content updates always occur automatically when they are available. However, it is possible to disable automatic content updates in the _Security Console Configuration_ and schedule them at a time of your choosing.

###Product updates

Product updates include performance improvements, bug fixes, and new product features. It is possible to disable automatic product updates in the _Security Console Configuration_ and update the product manually.
[block:callout]
{
  "type": "info",
  "body": "When you apply a product update, the latest available content updates up to the current date will also be applied."
}
[/block]

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/7da1e65-s_nx_updates.jpg",
        "s_nx_updates.jpg",
        1829,
        1119,
        "#1e2938"
      ],
      "caption": "The Security Console Updates page"
    }
  ]
}
[/block]
###Disabling automatic product updates

You can disable automatic product updates and initiate one-time product updates on an as-needed basis. This gives your organization the time and flexibility to train staff or otherwise prepare for updates that might cause changes in workflow. For example, a new feature may streamline a particular workflow by eliminating certain steps.
[block:callout]
{
  "type": "warning",
  "body": "Some new vulnerability and policy checks, which are included in content updates, require concurrent product updates in order to work properly."
}
[/block]
To disable automatic product updates:
1. Click the **Administration** tab.
2. Click **manage** next to _Security Console_.
The _Security Console Configuration_ panel appears.
3. Select **Updates** from the menu on the left-hand side.
4. Clear the checkbox labeled **Enable automatic product updates**.
A warning dialog box appears about the risks of disabling automatic product updates.
Click **Disable automatic product updates** to confirm that you want to turn off this feature.
Or click **Cancel** to leave automatic product updates enabled.
5. Click **Save**.
Whenever you change this setting and click **Save**, the application downloads any available product updates. If you have disabled the setting, it does not apply any downloaded product updates.

###Enabling automatic product updates
[block:callout]
{
  "type": "info",
  "body": "Your PostgreSQL database must be version 9. Otherwise, the application will not apply product updates. If you are using an earlier version of PostgreSQL, see [Migrating the database](doc:managing-the-security-console#section-migrating-the-database)."
}
[/block]
Enabling automatic product updates ensures that you are always running the most current version of the application.

To enable automatic product updates after they have been previously disabled:
1. Go to the **Administration** tab.
2. Under Global and Console settings, click **Administer**.
The _Security Console Configuration_ panel appears.
3. Select **Updates** from the left navigation pane.
4. Select the **Enable automatic product updates** check box.
5. Click **Save**.
Whenever you change this setting and click **Save**, the application downloads any available product updates. If you have enabled the setting, it also applies any downloaded product updates and restarts.

###Manual product updates

When automatic product updates have been disabled, you can manually download product updates.
[block:callout]
{
  "type": "info",
  "body": "By using this one-time update feature, you are not enabling future automatic product updates if they are not currently enabled."
}
[/block]
To manually download a new product update:
1. Go to the _Administration_ page.
2. Click **Manage** next to _UPDATES_.
[block:callout]
{
  "type": "info",
  "body": "This option only appears if you have already disabled automatic product updates as described in [Disabling automatic product updates](managing-versions-updates-and-licenses#section-disabling-automatic-product-updates)."
}
[/block]
The list of current and available updates appears.
3. Select **Updates** from the left navigation pane.
The Releases page appears.
4. To update to the most recent product release, click **Update to Latest Version**.
5. If you have not updated for a while, there may have been multiple versions released since your last update. In this case, you can select a version to which to update. To select a previous version to update to, navigate to that version and click **Update**. Releases up to and including that version will be applied.
6. On the Confirm Update dialog, click **Update**.
or (Optional) Click *Cancel** if you do not want to perform the update.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/1b564a6-s_nx_select_update_version.jpg",
        "s_nx_select_update_version.jpg",
        1875,
        887,
        "#3f4855"
      ]
    }
  ]
}
[/block]
###Scheduling automatic updates

By default, the Security Console queries the update server for updates every six hours. If an update is available, the console downloads and applies the update and then restarts. You can schedule updates to recur at specific times that are convenient for your business operations. For example, you may want updates to only occur during non-business hours or at times when they won't coincide with and disrupt scans.
[block:callout]
{
  "type": "info",
  "body": "Content updates are always applied according to the schedule, and product updates are applied according to the schedule only if they are enabled."
}
[/block]
To schedule updates:
1. Go to the _Administration_ page.
2. In the "Global and Console Settings" section, click **Administer** next to the "Console" label.
The _Security Console Configuration_ screen appears.
3. Select **Updates** from the left navigation pane.
The _Updates_ page appears.
4. If you want to prevent the Security Console from applying any available updates whenever it starts up, clear the appropriate checkbox. Disabling this default setting allows you to resume normal operations after an unscheduled restart instead of delaying these operations until any updates are applied.
5. Select a date and time to start your update schedule.
6. Select how frequently you want the Security Console to apply any available updates once the schedule is in effect.
7. Click **Save**.

##Configuring proxy settings for updates

If the Security Console does not have direct Internet access, you can use a proxy server for downloading updates. In most cases, Technical Support will advise if you need to change this setting. This topic covers configuring proxy settings for updates. You can also learn how about [Using a proxy server for sending logs](doc:troubleshooting#section-using-a-proxy-server-for-sending-logs).
[block:callout]
{
  "type": "info",
  "body": "For information on configuring updates for an Appliance, see the _Appliance Guide_ which you can download from the _Support_ page of _Help_."
}
[/block]
To configure proxy settings for updates:
1. Click the **Administration** tab.
The _Administration_ page appears.
2. On the _Administration_ page, click the **Manage** link for _Security Console_.
The _Security Console Configuration_ panel appears.
3. Go to the _Proxy Settings_ page.
4. Enter the information for the proxy server in the appropriate fields:
   * The **Name or address** field is set to _updates.rapid.7.com_ by default, which means that the Security Console is configured to contact the update server directly. If you want to use a proxy, enter the name or IP address of the proxy server.
   * The **Port** field is set to _80_ by default because the Security Console contacts the update server on that port. If you want to use a proxy, and if it uses a different port number for communication with the Security Console, enter that port number.
   * The **Response timeout** field sets the interval that the Security Console will wait to receive a requested package before initiating a timeout of the transfer. The default setting is 30,000 ms, or 30 seconds. The minimum setting is 1,000 ms, and the maximum is 2,147,483,647 ms. A proxy server may not relay an entire requested package to the Security Console until it downloads and analyzes the package in its entirety. Larger packages require more time. To determine how long to allow for a response interval, see the following topic: _Determining a response timeout interval for the proxy_.
   * The Security Console uses the information in the **Domain**, **User name**, and **Password** fields to be authenticated on a proxy server. If you want to use a proxy server, enter required values for those fields.

After you enter the information, click **Save**.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/05e8093-s_proxy_settings.jpg",
        "s_proxy_settings.jpg",
        1838,
        1160,
        "#1d2737"
      ],
      "caption": "Security Console Configuration panel - Proxy Settings page"
    }
  ]
}
[/block]
####Determining a response timeout interval for the proxy

To determine a timeout interval for the proxy server, find out how much time the Security Console requires to download a certain number of megabytes. You can, for example, locate the downloaded .JAR archive for a recent update and learn from the log file how long it took for the Security Console to download a file of that size.

Open the nsc.log file, located in the [installation_directory]/nsc directory. Look for a sequence of lines that reference the download of an update, such as the following:
```
2013-06-05T00:04:10 [INFO] [Thread: Security Console] Downloading update ID 1602503.
2013-06-05T00:04:12 [INFO] [Thread: Security Console] Response via 1.1 proxy.example.com.
2013-06-05T00:05:05 [INFO] [Thread: Security Console] Response via 1.1 proxy.example.com.
2013-06-05T00:05:07 [INFO] [Thread: Security Console] Acknowledging receipt of update ID 1602503.
```
Note the time elapsed between the first entry (```Downloading update ID...```) and the last entry (```Acknowledging receipt of update...```).

Then go to the directory on the Security Console host where the .JAR archives for updates are stored: [installation_directory]/updates/packages. Locate the file with the update ID referenced in the log entries and note its size. Using the time required for the download and the size of the file, you can estimate the timeout interval required for downloading future updates. It is helpful to use a larger update file for the estimate.
[block:callout]
{
  "type": "info",
  "body": "In most cases, a timeout interval of 5 minutes (300,000 ms) is generally sufficient for most update file sizes."
}
[/block]
##Managing updates without an Internet connection

If your network environment is isolated from the Internet, you can apply an update by running the installer that is released with that update. When you start the installer, it automatically scans your current installation for files to repair or update and then applies those changes.

An "update" installation leaves your database and configuration settings intact. The only changes it makes to your deployment are the updates.
[block:callout]
{
  "type": "warning",
  "body": "You will require one computer to have Internet access, so that you can download the installer."
}
[/block]
The first step is downloading the latest installer that is appropriate for your operating system.

Hyperlinks for downloading installers are available in the [Knowledge Base](https://kb.help.rapid7.com/docs/insightvm-and-nexpose-installers-md5sum-files-and-virtual-appliances).

You can also use the following hyperlinks:
* [Linux 64 installer](http://download2.rapid7.com/download/NeXpose-v4/NeXposeSetup-Linux64.bin)
* [Windows 64 installer](http://download2.rapid7.com/download/NeXpose-v4/NeXposeSetup-Windows64.exe)

After you download the appropriate installer, take the following steps:
1. If the InsightVM service is running, stop it to allow the installer to apply updates or repairs. See the topic [Log in and activate](doc:log-in-and-activate) for directions on stopping the service.
2. Run the installer. For detailed directions, see the installation guide, which you can download from the _Support_ page in Help.
The installer displays a message that it will update the current installation, repairing any files as necessary.
3. Click **OK** to continue with the updates and installation.
Upon completing the installation, the installer displays a success message.
4. Click **Finish** to exit the installer.
5. Restart the InsightVM service and log onto the Security Console.
The Security Console displays a page that summarizes the update. Many releases include two updates: content and product. You can click the **News** link to see if another update has been applied for the release date.