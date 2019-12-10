---
title: "Distributing, sharing, and exporting reports"
excerpt: ""
---
When configuring a report, you have a number of options related to how the information will be consumed and by whom. You can restrict report access to one user or a group of users. You can restrict sections of reports that contain sensitive information so that only specific users see these sections. You can control how reports are distributed to users, whether they are sent in e-mails or stored in certain directories. If you are exporting report information to external databases, you can specify certain properties related to the data export.

##Working with report owners

After a report is generated, only a Global Administrator and the designated report owner can see that report on the _Reports_ page. You also can have a copy of the report stored in the report owner’s directory. See [Storing reports in report owner directories](doc:distributing-sharing-and-exporting-reports#section-storing-reports-in-report-owner-directories) .

If you are a Global Administrator, you can assign ownership of the report one of a list of users.

If you are not a Global Administrator, you will automatically become the report owner.

###Storing reports in report owner directories

When the application generates a report, it stores it in the reports directory on the Security Console host:
```
[installation_directory]/nsc/reports/[user_name]/
```
You can configure the application to also store a copy of the report in a user directory for the report owner. It is a subdirectory of the reports folder, and it is given the report owner's user name.

1. Click **Configure advanced settings...** on the _Create a report_ panel.  
2. Click **Report File Storage**.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/fb32204-s_report_owner.jpg",
        "s_report_owner.jpg",
        1017,
        149,
        "#e8e9e5"
      ],
      "caption": "Report File Storage"
    }
  ]
}
[/block]
3. Enter the report owner’s name in the directory field ```$(install_dir)/nsc/reports/$(user)```. Replace (```user```) with the report owner’s name.

You can use string literals, variables, or a combination of these to create a directory path.

Available variables include:

* _$(date)_: the date that the report is created; format is yyyy-MM-dd
* _$(time)_: the time that the report is created; format is HH-mm-ss
* _$(user)_: the report owner’s user name
* _$(report_name)_: the name of the report, which was created on the _General_ section of the _Create a Report_ panel

After you create the path and run the report, the application creates the report owner’s user directory and the subdirectory path that you specified on the _Output_ page. Within this subdirectory will be another directory with a hexadecimal identifier containing the report copy.

For example, if you specify the path ```windows_scans/$(date)```, you can access the newly created report at:
```
reports/[report_owner]/windows_scans/$(date)/[hex_number]/[report_file_name]
```
Consider designing a path naming convention that will be useful for classifying and organizing reports. This will become especially useful if you store copies of many reports.

Another option for sharing reports is to distribute them via e-mail. Click the **Distribution** link in the left navigation column to go the Distribution page. See [Managing the sharing of reports](doc:distributing-sharing-and-exporting-reports#section-managing-the-sharing-of-reports).

##Managing the sharing of reports

Every report has a designated owner. When a Global Administrator creates a report, he or she can select a report owner. When any other user creates a report, he or she automatically becomes the owner of the new report.

In the console Web interface, a report and any generated instance of that report, is visible only to the report owner or a Global Administrator. However, it is possible to give a report owner the ability to share instances of a report with other individuals via e-mail or a distributed URL. This expands a report owner’s ability to provide important security-related updates to a targeted group of stakeholders. For example, a report owner may want members of an internal IT department to view vulnerability data about a specific set of servers in order to prioritize and then verify remediation tasks.
[block:callout]
{
  "type": "info",
  "body": "The granting of this report-sharing permission potentially means that individuals will be able to view asset data to which they would otherwise not have access."
}
[/block]
Administering the sharing of reports involves two procedures for administrators:

* configuring the application to redirect users who click the distributed report URL link to the appropriate portal
* granting users the report-sharing permission
[block:callout]
{
  "type": "info",
  "body": "If a report owner creates an access list for a report and then copies that report, the copy will not retain the access list of the original report. The owner would need to create a new access list for the copied report."
}
[/block]
Report owners who have been granted report-sharing permission can then create a report access list of recipients and configure report-sharing settings.

###Configuring URL redirection

By default, URLs of shared reports are directed to the Security Console. To redirect users who click the distributed report URL link to the appropriate portal, you have to add an element to the oem.xml configuration file.

The element reportLinkURL includes an attribute called altURL, with which you can specify the redirect destination.

To specify a redirected URL:

1. Open the oem.xml file, which is located in ```[product_installation-directory]/nsc/conf```. If the file does not exist, you can create the file.
[block:callout]
{
  "type": "warning",
  "body": "If you are creating the oem.xml file, make sure to specify the tag at the beginning and the tag at the end."
}
[/block]
2. Add or edit the reports sub-element to include the reportLinkURL element with the altURL attribute set to the appropriate destination, as in the following example:
```
<reports>
<reportEmail>
<reportSender>account@exampleinc.com</reportSender>
<reportSubject>${report-name}
</reportSubject>
<reportMessage type="link">Your report (${report-name}) was generated on ${report-date}: ${report-url}
</reportMessage>
<reportMessage type="file">Your report (${report-name}) was generated on ${report-date}. See attached files.
</reportMessage>
<reportMessage type="zip">Your (${report-name}) was generated on ${report-date}. See attached zip file.
</reportMessage>
</reportEmail>
<reportLinkURL altURL="base_url.net/directory_path${variable}?loginRedir="/>
</reports>
```
3. Save and close the oem.xml file.
4. Restart the application.

##Granting users the report-sharing permission

Global Administrators automatically have permission to share reports. They can also assign this permission to others users or roles.

Assigning the permission to a new user involves the following steps.

1. Go to the _Administration_ page, and click the **Create** link next to _Users_.
(_Optional_) Go to the _Users_ page and click **New user**.
2. Configure the new user’s account settings as desired.
3. Click the **Roles** link in the _User Configuration_ panel.
4. Select the **Custom** role from the drop-down list on the _Roles_ page.
5. Select the permission **Add Users to Report**.
Select any other permissions as desired.
6. Click **Save** when you have finished configuring the account settings.

To assign the permission to an existing user use the following procedure:

1. Go to the _Administration_ page, and click the **manage** link next to _Users_.
(_Optional_) Go to the _Users_ page and click the **Edit** icon for one of the listed accounts.
2. Click the Roles link in the _User Configuration_ panel.
3. Select the **Custom** role from the drop-down list on the _Roles_ page.
4. Select the check box labeled **Add Users to Report**.
Select any other permissions as desired.
[block:callout]
{
  "type": "info",
  "body": "You also can grant this permission by making the user a Global Administrator."
}
[/block]
5. Click **Save** when you have finished configuring the account settings.

###Creating a report access list

If you are a Global Administrator, or if you have been granted permission to share reports, you can create an access list of users when configuring a report. These users will only be able to view the report. They will not be able to edit or copy it.

####Using the Web-based interface to create a report access list

To create a report access list with the Web-based interface, take the following steps:

1. Click **Configure advanced settings...** on the _Create a report_ panel. 
2. Click **Access**.
If you are a Global Administrator or have Super-User permissions, you can select a report owner. Otherwise, you are automatically the report owner.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/878ad09-s_report_access_list.jpg",
        "s_report_access_list.jpg",
        986,
        253,
        "#e2ecef"
      ],
      "caption": "Report Access"
    }
  ]
}
[/block]
3. Click **Add User** to select users for the report access list.
A list of user accounts appears.
4. Select the check box for each desired user, or select the check box in the top row to select all users.
5. Click **Done**.
The selected users appear in the report access list.
[block:callout]
{
  "type": "info",
  "body": "Adding a user to a report access list potentially means that individuals will be able to view asset data to which they would otherwise not have access."
}
[/block]
6. Click **Run the report** when you have finished configuring the report, including the settings for sharing it.

##Using the Web-based interface to configure report-sharing settings
[block:callout]
{
  "type": "warning",
  "body": "Before you distribute the URL, you must configure URL redirection."
}
[/block]
You can share a report with your access list either by sending it in an e-mail or by distributing a URL for viewing it.

To share a report, use the following procedure:

1. Click **Configure advanced settings...** on the _Create a report_ panel. 
2. Click **Distribution**.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/687b3fc-s_report_distribution.jpg",
        "s_report_distribution.jpg",
        1004,
        488,
        "#e7f0f2"
      ],
      "caption": "Report Distribution"
    }
  ]
}
[/block]
3. Enter the sender’s e-mail address and SMTP relay server. For example, **E-mail sender address**: j_smith@example.com and **SMTP relay server**: mail.server.com.
You may require an SMTP relay server for one of several reasons. For example, a firewall may prevent the application from accessing your network’s mail server. If you leave the SMTP relay server field blank, the application searches for a suitable mail server for sending reports. If no SMTP server is available, the Security Console does not send the e-mails and will report an error in the log files.
If a global e-mail source setting has been configured, you can choose between the global setting and creating a new custom e-mail source when creating or editing a report.
If you are a Global Administrator, you have the option to save the E-mail sender address and SMTP relay server as global settings. This means that this e-mail address and SMTP relay server can be selected and used for any reports distributed by e-mail. You can save the E-mail sender address and SMTP relay server settings as global from the report configuration, if none have already been saved, or from the Security Console administration page at any time. Navigate to **Administration**, then **Administer** next to _Console_, then **SMTP**.
4. Select the check box to send the report to the report owner.
5. Select the check box to send the report to users on a report access list.
6. Select the method to send the report as: **URL**, **File**, or **Zip Archive**.
7. (_Optional_) Select the check box to send the report to users that are not part of an access list.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/bb0cfb9-s_report_owners_additional.jpg",
        "s_report_owners_additional.jpg",
        541,
        205,
        "#e5e4e2"
      ],
      "caption": "Additional Report Recipients"
    }
  ]
}
[/block]
8. (_Optional_) Select the check box to send the report to all users with access to assets in the report.
> Adding a user to a report access list potentially means that individuals will be able to view asset data to which they would otherwise not have access.
9. Enter the recipient’s e-mail addresses in the **Other recipients** field.
> **Note:** You cannot distribute a URL to users who are not on the report access list.
10. Select the method to send the report as: **File** or **Zip Archive**.
11. Click **Run the report** when you have finished configuring the report, including the settings for sharing it.

###Creating a report access list and configuring report-sharing settings with the API
[block:callout]
{
  "type": "info",
  "body": "This topic identifies the API elements that are relevant to creating report access lists and configuring report sharing. For specific instructions on using API v1.1 and Extended API v1.2, see the API guide, which you can download from the _Support_ page in Help."
}
[/block]
The elements for creating an access list are part of the ReportSave API, which is part of the API v1.1:
* With the ```Users``` sub-element of ```ReportConfig```, you can specify the IDs of the users whom you want add to the report access list.
Enter the addresses of e-mail recipients, one per line.
* With the ```Delivery``` sub-element of ```ReportConfig```, you can use the ```sendToAclAs``` attribute to specify how to distribute reports to your selected users.
Possible values include ```file```, ```zip```, or ```url```.

To create a report access list:
[block:callout]
{
  "type": "info",
  "body": "To obtain a list of users and their IDs, use the MultiTenantUserListing API, which is part of the Extended API v1.2."
}
[/block]
1. Log on to the Security Console.
For general information on accessing the API and a sample LoginRequest, see the section API overview in the API guide, which you can download from the _Support_ page in Help.
2. Specify the user IDs you want to add to the report access list and the manner of report distribution using the ReportSave API, as in the following XML example:
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/1d3f453-Ch_Managing_the_sharing_of_reports00003.jpg",
        "Ch_Managing_the_sharing_of_reports00003.jpg",
        708,
        427,
        "#d5ebe1"
      ]
    }
  ]
}
[/block]
3. If you have no other tasks to perform, log off.

For a LogoutRequest example, see the _API guide_.

For additional, detailed information about the ReportSave API, see the _API guide_.

##Restricting report sections

Every  report is based on a template, whether it is one of the preset templates that ship with the product or a customized template created by a user in your organization. A template consists of one or more sections. Each section contains a subset of information, allowing you to look at scan data in a specific way.

Security policies in your organization may make it necessary to control which users can view certain report sections, or which users can create reports with certain sections. For example, if your company is an Approved Scanning Vendor (ASV), you may only want a designated group of users to be able to create reports with sections that capture Payment Card Industry (PCI)-related scan data. You can find out which sections in a report are restricted by using the API (see the section _SiloProfileConfig_ in the _API guide_.)

Restricting report sections involves two procedures:

* setting the restriction in the API
[block:callout]
{
  "type": "info",
  "body": "Only a Global Administrator can perform these procedures."
}
[/block]
* granting users access to restricted sections

###Setting the restriction for a report section in the API

The sub-element RestrictedReportSections is part of the SiloProfileCreate API for new silos and SiloProfileUpdate API for existing silos. It contains the sub-element RestrictedReportSection for which the value string is the name of the report section that you want to restrict.

In the following example, the Baseline Comparison report section will become restricted.

1. Log on to the application.
For general information on accessing the API and a sample LoginRequest, see the section API overview in the _API v1.1 guide_, which you can download from the _Support_ page in Help.
2. Identify the report section you want to restrict. This XML example of SiloProfileUpdateRequest includes the RestrictedReportSections element.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/ef33343-Ch_Managing_the_sharing_of_reports00006.jpg",
        "Ch_Managing_the_sharing_of_reports00006.jpg",
        710,
        163,
        "#d4ebe5"
      ]
    }
  ]
}
[/block]
3. If you have no other tasks to perform, log off.
[block:callout]
{
  "type": "info",
  "body": "To verify restricted report sections, use the SiloProfileConfig API. See the _API guide_."
}
[/block]
For a LogoutRequest example, see the _API guide_.

The Baseline Comparison section is now restricted. This has the following implications for users who have permission to generate reports with restricted sections:

* They can see Baseline Comparison as one of the sections they can include when creating custom report templates.
* They can generate reports that include the Baseline Comparison section.

The restriction has the following implications for users who _do not_ have permission to generate reports with restricted sections:

* These users will not see Baseline Comparison as one of the sections they can include when creating custom report templates.
* If these users attempt to generate reports that include the Baseline Comparison section, they will see an error message indicating that they do not have permission to do so.
For additional, detailed information about the SiloProfile API, see _API guide_.

###Permitting users to generate restricted reports

Global Administrators automatically have permission to generate restricted reports. They can also assign this permission to others users.

To assign the permission to a new user:

1. Go to the _Administration_ page, and click the **Create** link next to _Users_.
(_Optional_) Go to the _Users_ page and click **New user**.
2. Configure the new user’s account settings as desired.
3. Click **Roles** in the _User Configuration_ panel.
The console displays the _Roles_ page.
4. Select the **Custom** role from the drop-down list.
5. Select the check box labeled **Generate Restricted Reports**.
6. Select any other permissions as desired.
7. Click **Save** when you have finished configuring the account settings.
[block:callout]
{
  "type": "warning",
  "body": "You also can grant this permission by making the user a Global Administrator."
}
[/block]
Assigning the permission to an existing user involves the following steps.

1. Go to the _Administration_ page, and click the **manage** link next to _Users_.
OR
2. (Optional) Go to the _Users_ page and click the **Edit** icon for one of the listed accounts.
3. Click the **Roles** link in the _User Configuration_ panel.
The console displays the _Roles_ page.
4. Select the **Custom** role from the drop-down list.
5. Select the check box labeled **Generate Restricted Reports**.
6. Select any other permissions as desired.
7. Click **Save** when you have finished configuring the account settings.

##Exporting scan data to external databases

If you selected _Database Export_ as your report format, the _Report Configuration—Output_ page contains fields specifically for transferring scan data to a database.

Before you type information in these fields, you must set up a JDBC-compliant database. In Oracle, MySQL, or Microsoft SQL Server, create a new database called ```nexpose``` with administrative rights.

1. Go to the _Database Configuration_ section that appears when you select the **Database Export** template on the _Create a Report_ panel.
2. Enter the IP address and port of the database server.
3. Enter the IP address of the database server.
4. Enter a server port if you want to specify one other than the default.
5. Enter a name for the database.
6. Enter the administrative user ID and password for logging on to that database.
7. Check the database to make sure that the scan data has populated the tables after the application completes a scan.