---
title: "Planning a deployment"
excerpt: ""
---
This chapter will help you deploy the application strategically to meet your organization’s security goals. If you have not yet defined these goals, this guide will give you important questions to ask about your organization and network, so that you can determine what exactly you want to achieve.

The deployment and configuration options in the application address a wide variety of security issues, business models, and technical complexities. With a clearly defined deployment strategy, you can use the application in a focused way for maximum efficiency.

## Understanding key concepts

Understanding the fundamentals of the application and how it works is key to determining how best to deploy it.

### Understanding the application

Your Security Console is a unified vulnerability solution that scans networks to identify the devices running on them and to probe these devices for vulnerabilities. It analyzes the scan data and processes it for reports. You can use these reports to help you assess your network security at various levels of detail and remediate any vulnerabilities quickly.

The vulnerability checks identify security weaknesses in all layers of a network computing environment, including operating systems, databases, applications, and files. The application can detect configuration failures and vulnerabilties across your assets and the applications running on them in order to reduce your exposure to attack.

### Understanding the components

The application consists of two main components:

_Scan Engines_ perform asset discovery and vulnerability detection operations. You can deploy Scan Engines outside your firewall, within your secure network perimeter, or inside your DMZ to scan any network asset.

The _Security Console_ communicates with Scan Engines to start scans and retrieve scan information. All exchanges between the Security Console and Scan Engines occur via encrypted SSL sessions over a dedicated TCP port that you can select. For better security and performance, Scan Engines do not communicate with each other; they only communicate with the Security Console after the Security Console establishes a secure communication channel.

When the application scans an asset for the first time, the Security Console creates a repository of information about that asset in its database. With each ensuing scan that includes that asset, the Security Console updates the repository.

The Security Console includes a Web-based interface for configuring and operating the application. An authorized user can log onto this interface securely, using HTTPS from any location, to perform any application-related task that his or her role permits. See [Understanding user roles and permissions](doc:planning-a-deployment#section-understanding-user-roles-and-permissions). The authentication database is stored in an encrypted format on the Security Console server, and passwords are never stored or transmitted in plain text.

Other Security Console functions include generating user-configured reports and regularly downloading patches and other critical updates from the Rapid7 central update system.

InsightVM components are available as a dedicated hardware/software combination called an _Appliance_. You also can download software-only Linux or Windows versions for installation on one or more hosts, depending on your InsightVM license. Another option is to purchase remote scanning services from Rapid7.

### Understanding sites and asset groups

The Security Console interface enables you to plan scans effectively by organizing your network assets into sites and asset groups.

When you create a site, you identify the assets to be scanned, and then define scan parameters, such as scheduling and frequency. Each site can have a set of scan configurations that allow you to specify how you want to collect data for that site. For example, you may define a full vulnerability audit scan to happen once per week and a discovery scan to happen every day if you want.

You may define the type of scan you wish to run for each scan configuration, the scan engine or Scan Engine pool to be used, and the scan template to be used for each Scan Configuration. There are many built in scan templates including Penetration Test, Microsoft Hotfix, and Full Audit. You can also create custom scan templates that define which vulnerabilities and compliance policies you are checking and the network settings necessary to run those checks.

You also define the type of scan you wish to run for that site. Each site is associated with a specific scan. The application supplies a variety of scan templates, which can expose different vulnerabilities at all network levels. Template examples include Penetration Test, Microsoft Hotfix, Denial of Service Test, and Full Audit. You also can create custom scan templates.

Another level of asset organization is an asset group. Like the site, this is a logical grouping of assets, but it is not defined for scanning. An asset group typically is assigned to a user who views scan reports about that group in order to perform any necessary remediation. An asset must be included within a site before you can add it to an asset group.
[block:callout]
{
  "type": "info",
  "body": "If you are using RFC1918 addressing (192.168.x.x or 10.0.x.x addresses) different assets may have the same IP address. You can use site organization to enable separate Scan Engines located in different parts of the network to access assets with the same IP address."
}
[/block]
Only designated users are authorized to create sites and asset groups. For more details about access permissions, see [Understanding user roles and permissions](doc:planning-a-deployment#section-understanding-user-roles-and-permissions).

Asset groups can include assets listed in multiple sites. Therefore, if you wish to generate reports about assets scanned with multiple Scan Engines, use the asset group arrangement. You also can configure reports for combination of sites, asset groups, and assets.

### Understanding user roles and permissions

User access to Security Console functions is based on roles. You can assign default roles that include pre-defined sets of permissions, or you can create custom roles with permission sets that are more practical for your organization. See [Managing and creating user accounts](doc:managing-users-and-authentication#section-managing-and-creating-user-accounts). Once you give a role to a user, you restrict access in the Security Console to those functions that are necessary for the user to perform that role.

There are five default roles:
* [Global Administrator](doc:managing-users-and-authentication#section-global-administrator)
* [Security Manager and Site Owner](doc:managing-users-and-authentication#section-security-manager-and-site-owner)
* [Asset Owner](doc:managing-users-and-authentication#section-asset-owner)
* [Managing users and authentication](doc:managing-users-and-authentication)