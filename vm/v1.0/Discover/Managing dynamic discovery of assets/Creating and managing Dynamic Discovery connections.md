---
title: "Creating and managing Dynamic Discovery connections"
excerpt: ""
---
This action provides InsightVM with the information it needs to contact a server or process that manages the asset environment.

You must have Global Administrator permissions to create or manage Dynamic Discovery connections. See [Managing users and authentication](doc:managing-users-and-authentication).

* [Creating a connection](doc:creating-and-managing-dynamic-discovery-connections#section-creating-a-connection)
  * [Adding a Mobile Device Connection](doc:creating-and-managing-dynamic-discovery-connections#section-adding-a-mobile-device-connection)
  * [Adding an AWS Legacy Connection](doc:creating-and-managing-dynamic-discovery-connections#section-adding-an-aws-connection)
  * [Adding an Amazon Web Services Asset Sync Connection](doc:creating-and-managing-dynamic-discovery-connections#section-adding-an-amazon-web-services-asset-sync-connection)
  * [Adding a VMware vSphere Connection](doc:creating-and-managing-dynamic-discovery-connections#section-adding-a-vmware-vsphere-connection)
  * [Adding a DHCP-Directory Watcher Connection](doc:creating-and-managing-dynamic-discovery-connections#section-adding-a-dhcp-directory-watcher-connection)
  * [Adding a DHCP-Syslog Connection](doc:creating-and-managing-dynamic-discovery-connections#section-adding-a-dhcp-syslog-connection)
  * [Adding a McAfee ePolicy Orchestrator Connection](doc:creating-and-managing-dynamic-discovery-connections#section-adding-a-mcafee-epolicy-orchestrator-connection)
  * [Adding an Active Directory Connection](doc:creating-and-managing-dynamic-discovery-connections#section-adding-an-active-directory-connection)
  * [Adding a McAfee Data Exchange Layer Connection](doc:creating-and-managing-dynamic-discovery-connections#section-adding-a-mcafee-data-exchange-layer-connection)
  * [Adding a Microsoft Azure Connection](doc:creating-and-managing-dynamic-discovery-connections#section-adding-a-microsoft-azure-connection)
  * [Viewing and changing available connections](doc:creating-and-managing-dynamic-discovery-connections#section-viewing-and-changing-available-connections)
* [Creating a connection in a site configuration](doc:creating-and-managing-dynamic-discovery-connections#section-creating-a-connection-in-a-site-configuration)
  * [Adding an Exchange ActiveSync (LDAP) Connection](doc:creating-and-managing-dynamic-discovery-connections#section-adding-an-exchange-activesync-ldap-connection)
  * [Adding an Exchange ActiveSync (WinRM/PowerS/hell or WinRM/Office 365) Connection](doc:creating-and-managing-dynamic-discovery-connections#section-adding-an-exchange-activesync-winrm-powers-hell-or-winrm-office-365-connection)
  * [Adding an AWS Legacy Connection](doc:creating-and-managing-dynamic-discovery-connections#section-adding-an-aws-connection-site-configuration-)
  * [Adding a VMware vSphere Connection](doc:creating-and-managing-dynamic-discovery-connections#section-adding-a-vmware-vsphere-connection-site-configuration-)
  * [Adding a DHCP-Directory Watcher Connection](doc:creating-and-managing-dynamic-discovery-connections#section-adding-a-dhcp-directory-watcher-connection-site-configuration-)
  * [Adding a DHCP-Syslog Connection](doc:creating-and-managing-dynamic-discovery-connections#section-adding-a-dhcp-syslog-connection-site-configuration-)

##Creating a connection

1. Click the **Administration** tab.
2. On the _Administration_ page, under _Discovery Options_, click the **create** link for _Connections_.
The Security Console displays the _General_ page of the _Asset Discovery Connection_ panel.
3. On the _New Discovery Connection_ page, select a connection type:


* _Exchange ActiveSync (LDAP)_ is for mobile devices managed by an Active Directory (AD) server.
* _Exchange ActiveSync (WinRM/PowerShell)_ is for mobile devices managed by an on-premise Exchange server accessed with PowerShell.
* _Exchange ActiveSync (WinRM/Office 365)_ is for mobile devices managed by Cloud-based Exchange server running Microsoft Office 365.
* _vmware vSphere_ is for environments managed by VMware vCenter or ESX/ESXi.
* _AWS_ is for environments managed by Amazon Web Services.
* _DHCP Service_ is for assets that Scan Engines discover by collecting log data from DHCP servers.
* _McAfee Security ePolicy Orchestrator_ is for assets managed by Intel Security ePolicy Orchestrator (ePO).
* _Active Directory (LDAP)_ is for devices managed by an Active Directory (AD) server.
* _Intel Security Data Exchange_ Layer is for identifying malicious events on files present in systems managed by ePO, and for communicating Nexpose assessment data for consumption in Intel Security products.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/c5d4b01-Asset_Sync_Multiple_Regions.png",
        "Asset_Sync_Multiple_Regions.png",
        627,
        366,
        "#2e363e"
      ],
      "caption": "Selecting a discovery connection type"
    }
  ]
}
[/block]
### Adding a Mobile Device Connection

1. Enter a unique name for the new connection on the _New Discovery Connection_ page.
2. Enter the name of the Active Directory (AD) server to which the Security Console will connect.
3. Select a protocol from the drop-down list.
LDAPS, which is LDAP over SSL, is the more secure option and is recommended if it is enabled on your AD server.
4. Enter a user name and password for a member of the _Organization Management Security_ Group in Microsoft Exchange.
This account will enable the Security Console to discover mobile devices connected to the AD server.
5. Click **Save**.
6. Continue with [Initiating Dynamic Discovery](doc:initiating-dynamic-discovery).

### Adding an AWS Connection
[block:callout]
{
  "type": "warning",
  "title": "REMINDER",
  "body": "The _AWS_ connection is a **completely separate** connection type from _Amazon Web Services Asset Sync_.\n\n_AWS_ connections require a **dynamic** site."
}
[/block]
1. Enter a unique name for the new connection on the _New Discovery Connection_ page.
2. From the drop-down list, select the geographic region where your AWS instances are deployed.
3. If the Security Console is deployed inside the AWS network, select the appropriate check box. (Note that this is an unusual configuration; in most cases, the Security Console will be outside the AWS network.) If you indicate that the Security Console is inside the AWS network, the Credentials link disappears from the left navigation pane. You do not need to configure credentials, since the AWS API recognizes the IAM role of the AWS instance that the Security Console is installed on.
4. If the Scan Engine you will use to scan the AWS environment is deployed inside the AWS network, select the appropriate check box. This will enable the application to scan private IP addresses. See  [Inside or Outside the AWS network?](https://insightvm.help.rapid7.com/v1.0/docs/discovering-amazon-web-services-instances#section-inside-or-outside-the-aws-network). 
5. If you indicate that the Security Console is inside the AWS network, the access key fields will be removed. You do not need to configure credentials, since the AWS API recognizes the IAM role of the AWS instance that the Security Console is installed on. In this case, simply click **Save** and ignore the following steps.
6. If you do _not_ indicate that the Security Console is inside the AWS network, Enter an Access Key ID and Secret Access Key with which the application will log on to the AWS API.
7. Click **Save**.
8. Continue with [Initiating Dynamic Discovery](doc:initiating-dynamic-discovery).

### Adding an Amazon Web Services Asset Sync Connection
[block:callout]
{
  "type": "warning",
  "title": "REMINDER",
  "body": "The _Amazon Web Services Asset Sync_ connection is a **completely separate** connection type from _AWS_.\n\n_Amazon Web Services Asset Sync_ connections require a **static** site."
}
[/block]
1. Enter a unique name for the new connection.
2. From the drop-down list, select the geographic region where your AWS instances are deployed. A single connection can specify multiple regions, if necessary.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/b84aa2c-Asset_Sync_Multiple_Regions.png",
        "Asset_Sync_Multiple_Regions.png",
        627,
        366,
        "#2e363e"
      ]
    }
  ]
}
[/block]
3. If the Security Console is deployed inside the AWS network, select the appropriate check box. 
If you indicate that the Security Console is inside the AWS network, the Credentials link disappears from the left navigation pane. You do not need to configure credentials, since the AWS API recognizes the IAM role of the AWS instance that the Security Console is installed on.
4. If the Scan Engine you will use to scan the AWS environment is deployed inside the AWS network, select the appropriate check box. This will enable the application to scan private IP addresses. See [Inside or outside the AWS network?](https://insightvm.help.rapid7.com/v1.0/docs/discovering-amazon-web-services-instances#section-inside-or-outside-the-aws-network) .
5. Enter an Access Key ID and Secret Access Key with which the application will log on to the AWS API.
6. If you are using AWS AssumeRole for cross-account access, enter **one** role ARN per line and an optional Session Name for the assumed role session. The session name is a string of characters consisting of upper- and lower-case alphanumeric characters with no spaces. You can also include underscores or any of the following characters: =,.@-
[block:callout]
{
  "type": "info",
  "title": "TIP",
  "body": "When multiple ARNs are present, the application will iterate over each ARN and attempt to import assets from the region(s) specified."
}
[/block]

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/0d2777b-ARN_session_name.png",
        "ARN_session_name.png",
        964,
        708,
        "#e9cfcd"
      ]
    }
  ]
}
[/block]
7. If desired, click **Test Credential** to confirm that the connection is successful.
8. Select **Synchronize Amazon Web Services Asset Sync assets** to import AWS assets and remove stale assets.
9. Select a site to associate the assets with.
To exclude specific assets from being imported, enter the tags in the **Do not import assets with the following tags**: box. The format is key:value + key:value +... If this box is empty, all assets are imported.
10. Select **Import tags** to import all Amazon Web Services tags.
To include specific tags, enter these tags in the **Only import the following tags**: box. The format is key:value + key:value +... If this box is empty, all tags are imported. AWS tags are imported as custom tags on the corresponding asset, and can be easily identified by the prefix *Amazon-web-services*.
[block:callout]
{
  "type": "info",
  "body": "By default, and regardless of the state of the **Import Tags** check box, the _Amazon Web Services Asset Sync_ connection will create a Security Console tag based on the imported VPC ID of the instance.",
  "title": "Default Tag Creation"
}
[/block]
11. Click **Save**.


### Adding a VMware vSphere Connection

1. Enter a unique name for the new connection on the _New Discovery Connection_ page.
2. Enter a fully qualified domain name for the server that the Security Console will contact in order to discover assets.
4. Enter a port number and select the protocol for the connection.
5. Enter a user name and password with which the Security Console will log on to the server. Make sure that the account has access to any virtual machine that you want to discover.
6. Click **Save**.
7. Continue with [Initiating Dynamic Discovery](doc:initiating-dynamic-discovery).

### Adding a DHCP-Directory Watcher Connection

1. Enter a unique name for the new connection on the _New Discovery Connection_ page.
2. Select an event source.
3. Select _Directory Watcher_ as the collection method.
4. Enter a network path to the folder containing the DHCP server logs to be monitored. Use the format _//server/path/to/folder_. The server can be either a host name or IP address.
5. Select the Scan Engine that will collect the DHCP server log information.
6. Enter the administrative user name and password for accessing the DHCP server.
7. Click **Save**.
8. Continue with [Initiating Dynamic Discovery](doc:initiating-dynamic-discovery).

**Tip:** If you create a connection and later change it to reference a different DHCP server, your asset discovery results will change. Therefore, if it is important to you to associate assets with specific DHCP servers in InsightVM, consider associating the name of the connection with the DHCP server and changing that name if you change the referenced server. Also, note that you cannot create duplicate DHCP connections.

### Adding a DHCP-Syslog Connection
[block:callout]
{
  "type": "info",
  "body": "Syslog is the only available data collection method for the Infoblox Trinzic event source."
}
[/block]
1. Enter a unique name for the new connection on the _New Discovery Connection_ page.
2. Select an event source type.
3. Select the _Syslog_ collection method.
4. Select the number of the port that the syslog parser listens on for log entries related to asset information.
5. Select the protocol for the port that the syslog parser listens on for log entries related to asset information.
6. Select the Scan Engine that will collect the DHCP server log information.
7. Click **Save**.
8. Continue with [Initiating Dynamic Discovery](doc:initiating-dynamic-discovery).

### Adding a McAfee ePolicy Orchestrator Connection

1. Enter a unique name for the new connection.
2. Enter the username and password for the user to connect to McAfee ePolicy Orchestrator (ePO). For security best practices, this should be a service user exclusively for use with the Nexpose integration. The Nexpose ePo extension automatically creates a user called NexposeServiceUser.
3. Enter the IP address or the hostname of the server where ePO is installed.
4. Enter the port on which ePO is running.
5. If the ePO server uses a self-signed certificate, select **Untrusted Certificate Permitted**. Otherwise, leave it clear.
6. Select **Consume McAfee ePolicy Orchestrator assets**. This setting is necessary for the initial configuration in order for InsightVM to collect information about the assets. If you do not want to continue to collect information about the assets on an ongoing basis (for instance, if you believe the information will seldom change), you can return to the configuration at a later time and clear this setting.
7. Select a site to which to associate the assets.
8. To populate the **Rapid7 Nexpose Insight: Top 10 Riskiest Systems** dashboard in ePO with data, select **Push risk scores**. The data will be automatically updated whenever an InsightVM scan finds risk score changes in ePO managed assets.
9. If desired, click **Test Credential** to confirm that the username and password connect as expected.
10. Click **Save**.
11. Navigate back to the site. The assets will have populated within the site. You can now create dynamic asset groups and scan the assets.

### Adding an Active Directory Connection

1. Enter a unique name for the new connection.
2. Enter the Server IP or host name of the Active Directory (AD) server to which the Security Console will connect.
3. Select a protocol from the drop-down list.
LDAPS, which is LDAP over SSL, is the more secure option and is recommended if it is enabled on your AD server.
4. Enter a user name and password, and optionally click **Test Credential** to confirm that the credentials connect as expected.
5. If desired, use the Base Query field to specify the portion of the Domain Component (DC) tree you would like to import, and the Search Query field to further qualify the computers you would like to discover, using an LDAP Query: https://technet.microsoft.com/en-us/library/aa996205(v=exchg.65).aspx
6. Select **Consume Active Directory (LDAP) assets**. This setting is necessary for the initial configuration in order for InsightVM to collect information about the assets. If you do not want to continue to collect information about the assets on an ongoing basis (for instance, if you believe the information will seldom change), you can return to the configuration at a later time and clear this setting.
7. Select a site to which to associate the assets.
8. If desired, click the **Preview** button to see the top 50 results of your query to make sure your query is working as expected.
9. Click **Save**.
10. Navigate back to the site. The assets will have populated within the site. The time it takes to completely populate the site will vary, based on how long it takes the active directory to respond to the query. You can now create dynamic asset groups and scan the assets.

### Adding a McAfee Data Exchange Layer Connection

1. Enter a unique name for the new connection.
2. Enter the username and password for the user to connect to McAfee ePolicy Orchestrator (ePO), which generates certificates that allow communication with McAfee Data Exchange Layer (DXL). For security best practices, this should be a service user that was created specifically for use with the Nexpose integration. The user should be in an ePO permission set with the DXL McAfee MePO Certificate Creation permission assigned. Your IP address and hostname will be the same as for your ePO connection, but the username and password should be different
3. Enter the IP address or the hostname of the server where ePO with McAfee Data Exchange Layer is installed.
4. Enter the port on which ePO is running.
5. Select **Find details of a vulnerability** to gather vulnerability details that have already been collected. This setting is checked by default and cannot be modified. The setting is mandatory because it enables clients to get additional details for a particular vulnerability that InsightVM publishes.
6. Select **Publish vulnerabilities** to publish information about vulnerabilities discovered by Nexpose back to McAfee Data Exchange Layer.
7. If desired, click **Test Credential** to confirm that the username and password connect to ePO as expected.
8. Click **Save**.
[block:callout]
{
  "type": "warning",
  "body": "Once a Security McAfee Data Exchange Layer (DXL) connection has been saved, additional changes will not apply until the InsightVM Security Console is restarted. You can edit, test, and save the credential configuration but the changes will only be applied upon InsightVM Security Console restart. This also applies to deleting a connection; although the deleted connection will no longer appear in the InsightVM Security Console interface, you will not be able to create a new DXL connection with the same credential configuration until a InsightVM Security Console restart."
}
[/block]
### Adding a Microsoft Azure Connection

1. Enter a unique name for the new connection.
2. Enter the tenant ID associated with your Azure instance.
3. Enter the application ID associated with the Rapid7 application created in your Azure AD instance.
4. Enter the application secret key generated for the Rapid7 application created in your Azure AD instance.
5. If desired, click **Test Credential** to confirm that the connection is successful.
6. If the Scan Engine you will use to scan the Azure environment is deployed inside the Azure network, select the appropriate check box. This will enable the application to scan private IP addresses.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/59f3e55-Azure_discovery_connection.png",
        "Azure_discovery_connection.png",
        759,
        755,
        "#e9f2f2"
      ]
    }
  ]
}
[/block]
7. Select **Synchronize Microsoft Azure assets** to import Azure assets and remove stale assets.
8. Select a site to which to associate the assets.
9. To exclude specific assets from being imported, enter the tags in the **Do not import assets with the following tags:** box. The format is key: ```value + key: value +...``` If this box is empty, all assets are imported.
10. Select **Import tags** to import all Azure tags.
11. To include specific tags, enter these tags in the Only import the following tags: box. The format is key: ```value + key: value +...``` If this box is empty, all tags are imported.
12. Click **Save**.

###Viewing and changing available connections

To view available connections or change a connection configuration take the following steps:
1. Go to the _Administration_ page.
2. Click **manage** for _Discovery Connections_.
The Security Console displays the _Discovery Connections_ page.
3. Click **Edit** for a connection that you wish to change.
4. Enter information in the _Asset Discovery Connection_ panel.
5. Click **Save**.
6. Continue with [Initiating Dynamic Discovery](doc:initiating-dynamic-discovery).

OR

1. Click the **Dynamic Discovery** link that appears in the upper-right corner of the Security Console Web interface, below the user name.
The Security Console displays the _Filtered asset discovery_ page.
2. Click the **Manage** for connections.
The Security Console displays the _Asset Discovery Connection_ panel
3. Enter the information in the appropriate fields.
4. Click **Save**.
5. Continue with [Initiating Dynamic Discovery](doc:initiating-dynamic-discovery).

On the _Discovery Connections_ page, you can also delete connections or export connection information to a CSV file, which you can view in a spreadsheet for internal purposes.

You cannot delete a connection that has a dynamic site or an in-progress scan associated with it. Also, changing connection settings may affect asset membership of a dynamic site. See [Configuring a site using a Dynamic Discovery connection](doc:configuring-a-site-using-a-dynamic-discovery-connection). You can determine which dynamic sites are associated with any connection by going to the _Discovery Management_ page. See [Monitoring Dynamic Discovery](doc:monitoring-dynamic-discovery).

If you change a connection by using a different account, it may affect your discovery results depending which virtual machines the new account has access to. For example: You first create a connection with an account that only has access to all of the advertising department’s virtual machines. You then initiate discovery and create a dynamic site. Later, you update the connection configuration with credentials for an account that only has access to the human resources department’s virtual machines. Your dynamic site and discovery results will still include the advertising department’s virtual machines; however, information about those machines will no longer be dynamically updated. Information is only dynamically updated for machines to which the connecting account has access.

## Creating a connection in a site configuration
[block:callout]
{
  "type": "info",
  "title": "NOTE",
  "body": "Only the connections listed below can be created within a site configuration."
}
[/block]
If you want to create a connection while configuring a new site, click the **Create site** button on the _Home_ page.
OR
Click the **Create** tab at the top of the page and then select _Site_ from the drop-down list.

If you want to create a connection for an existing site, click that site's **Edit** icon in the _Sites_ table on the _Home_ page.

1. Click the **Assets** link in the site configuration .
2. Select **Connection** as the option for specifying assets.
3. Click **Create Connection**.
4. Select a connection type:


* _Exchange ActiveSync (LDAP)_ is for mobile devices managed by an Active Directory (AD) server.
* _Exchange ActiveSync (WinRM/PowerShell)_ is for mobile devices managed by an on-premise Exchange server accessed with PowerShell.
* _Exchange ActiveSync (WinRM/Office 365)_ is for mobile devices managed by Cloud-based Exchange server running Microsoft Office 365.
* _vmware vSphere_ is for environments managed by VMware vCenter or ESX/ESXi.
* _AWS_ is for environments managed by Amazon Web Services.
* _DHCP Service_ is for assets that Scan Engines discover by collecting log data from DHCP servers.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/0715601-s_nx_site_config_select_connection.jpg",
        "s_nx_site_config_select_connection.jpg",
        2243,
        788,
        "#1e2939"
      ],
      "caption": "Selecting a discovery connection type within a site configuration"
    }
  ]
}
[/block]
### Adding an Exchange ActiveSync (LDAP) Connection

1. Enter a unique name for the new connection on the _New connection_ tab.
2. Enter the name of the Active Directory (AD) server to which the Security Console will connect.
3. Select a protocol from the drop-down list.
LDAPS, which is LDAP over SSL, is the more secure option and is recommended if it is enabled on your AD server.
4. Enter a user name and password for a member of the _Organization Management_ Security Group in Microsoft Exchange.
This account will enable the Security Console to discover mobile devices connected to the AD server.
**Note:** Once you save credentials in this setting, changes will not take effect until you restart InsightVM.
5. Click **Save**. The connection appears in the **Connection** drop-down list, which you can view by clicking **Select Connection**.
6. Continue with [Initiating Dynamic Discovery](doc:initiating-dynamic-discovery).

### Adding an Exchange ActiveSync (WinRM/PowerS/hell or WinRM/Office 365) Connection

1. Enter a unique name for the new connection on the _New connection_ tab.
2. Enter the name of the of the WinRM gateway server to which the Security Console will connect.
3. Enter a user name and password for an account that has WinRM permissions for the gateway server.
4. Enter the fully qualified domain name of the Exchange server that manages the mobile device information.
5. Enter a user name and password for an administrator account or a user account that has View-Only Organizational Management or higher role of the _Organization Management_ Security Group in Microsoft Exchange.
6. Click **Save**. The connection appears in the **Connection** drop-down list, which you can view by clicking **Select Connection**.
7. Continue with [Initiating Dynamic Discovery](doc:initiating-dynamic-discovery).

### Adding an AWS Connection (site configuration)
[block:callout]
{
  "type": "warning",
  "title": "REMINDER",
  "body": "The _AWS_ connection is a **completely separate** connection type from _Amazon Web Services Asset Sync_.\n\n_AWS_ connections require a **dynamic** site."
}
[/block]
1. Enter a unique name for the new connection on the _New connection_ tab.
2. From the drop-down list, select the geographic region where your AWS instances are deployed.
3. If the Security Console is deployed inside the AWS network, select the appropriate check box. (Note that this is an unusual configuration; in most cases, the Security Console will be outside the AWS network.) If you indicate that the Security Console is inside the AWS network, the Credentials link disappears from the left navigation pane. You do not need to configure credentials, since the AWS API recognizes the IAM role of the AWS instance that the Security Console is installed on.
4. If the Scan Engine you will use to scan the AWS environment is deployed inside the AWS network, select the appropriate check box. This wil enable the application to scan private IP addresses.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/4a42654-s_nx_AWS_site_connection_settings.jpg",
        "s_nx_AWS_site_connection_settings.jpg",
        851,
        371,
        "#222b39"
      ],
      "caption": "Setting up a connection with InsightVM Scan Engine inside the AWS network and Security Console outside"
    }
  ]
}
[/block]
5. If prompted to do so (Security Console outside the AWS network), enter an Access Key ID and Secret Access Key with which the application will log on to the AWS API.
6. Click **Save**. The connection appears in the **Connection** drop-down list, which you can view by clicking **Select Connection**.
7. Continue with [Initiating Dynamic Discovery](doc:initiating-dynamic-discovery).

### Adding a VMware vSphere Connection (site configuration)

1. Enter a unique name for the new connection on the _New connection_ tab.
2. Enter a fully qualified domain name for the server that the Security Console will contact in order to discover assets.
3. Enter a port number and select the protocol for the connection.
4. Enter a user name and password with which the Security Console will log on to the server. Make sure that the account has access to any virtual machine that you want to discover.
5. Click **Save**. The connection appears in the **Connection** drop-down list, which you can view by clicking **Select Connection**.
6. Continue with [Initiating Dynamic Discovery](doc:initiating-dynamic-discovery)

### Adding a DHCP-Directory Watcher Connection (site configuration)

1. Enter a unique name for the new connection.
2. Select an event source type.
3. Select the _Directory Watcher_ collection method.
4. Enter a network path to the folder containing the DHCP server logs to be queried. Use the format _//server/path/to/folder_. The server can be either a host name or IP address.
5. Select the Scan Engine that will collect the DHCP server log information.
6. Enter the administrative user name and password for accessing the DHCP server.
7. Click **Save**. The connection appears in the **Connection** drop-down list, which you can view by clicking **Select Connection**.
8. Continue with [Initiating Dynamic Discovery](doc:initiating-dynamic-discovery).

### Adding a DHCP-Syslog Connection (site configuration)

**Note:** Syslog is the only available collection method for the Infoblox Trinzic event source.

1. Enter a unique name for the new connection.
2. Select an event source type.
3. Select the _Syslog_ collection method.
4. Enter the number for the port that the syslog parser listens on for log entries related to asset information.
5. Select the protocol for the port that the syslog parser listens on for log entries related to asset information.
6. Select the Scan Engine that will collect the DHCP server log information.
7. Click **Save**. The connection appears in the **Connection** drop-down list, which you can view by clicking **Select Connection**.
8. Continue with [Initiating Dynamic Discovery](doc:initiating-dynamic-discovery).