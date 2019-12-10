---
title: "Initiating Dynamic Discovery"
excerpt: ""
---
This action involves having the Security Console contact the server or API and begin discovering virtual assets. After the application performs initial discovery and returns a list of discovered assets, you can refine the list based on criteria filters, as described in the following topic. To perform Dynamic Discovery, you must have the _Manage sites_ permission. See [Configuring roles and permissions](doc:managing-users-and-authentication#section-configuring-roles-and-permissions).
[block:callout]
{
  "type": "info",
  "body": "This process does not apply to McAfee ePolicy Orchestrator, McAfee Data Exchange Layer, or Active Directory connections. With those connection types, discovery takes place automatically when you initiate the connection."
}
[/block]
1. After creating a connection (see [Creating a connection in a site configuration](doc:creating-and-managing-dynamic-discovery-connections#section-creating-a-connection-in-a-site-configuration)), click **Select Connection**.
2. Select the desired option from the drop-down list.
InsightVM establishes the connection and performs discovery. A table appears and lists information about each discovered asset.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/d1d7bf2-s_nx_dynamic_discovery_vsphere_assets.jpg",
        "s_nx_dynamic_discovery_vsphere_assets.jpg",
        2066,
        1183,
        "#212b3b"
      ],
      "caption": "Assets displayed in a VMware connection"
    }
  ]
}
[/block]

[block:callout]
{
  "type": "info",
  "body": "Assets discovered through a dynamic connection also appear on the _Assets_ page. See [Comparing scanned and discovered assets](doc:locating-assets#section-comparing-scanned-and-discovered-assets)"
}
[/block]
## Initiating discovery outside of a site configuration

1. Click the **Administration** icon.
2. On the _Administration_ page, under _Discovery Options_, click the **create** link for _Connections_.
The Security Console displays the _General_ page of the _Asset Discovery Connection_ panel.
3. Select the appropriate discovery connection name from the drop-down list labeled Connection.
4. Click **Discover Assets**.
[block:callout]
{
  "type": "info",
  "body": "With new, changed, or reactivated discovery connections, the discovery process must complete before new discovery results become available. There may be a slight delay before new results appear in the Web interface."
}
[/block]
InsightVM establishes the connection and performs discovery. A table appears and lists the following information about each discovered asset.

### Displayed values for discovered assets

For mobile devices, the table includes the following:

* the operating system of the mobile device
* the account user name for the mobile device
* the last time the device synced with the Exchange server (WinRM/PowerShell and WinRM/Office 365 only)

For AWS connections, the table includes the following:

* the name of the AWS instance (asset)
* the instance's IP address
* the instance ID
* the instance's Availability Zone, which is a location within a geographic region that is insulated from failures in other Availability Zones and provides low-latency network connectivity to other Availability Zones in the same region
* the instance's geographic region
* the instance type, which defines its memory, CPU, storage capacity, and hourly cost
* the instance's operating system
* the operational state of the instance

For VMware connections, the table includes the following:

* the asset’s name
* the asset’s IP address
* the VMware datacenter in which the asset is managed
* the asset’s host computer
* the cluster to which the asset belongs
* the resource pool path that supports the asset
* the asset’s operating system
* the asset’s power status

For DHCP connections, the table includes the following:

* the asset's host name
* the asset's IP address
* the asset's MAC address

After performing the initial discovery, the application continues to discover assets as long as the discovery connection remains active. The Security Console displays a notification of any inactive discovery connections in the bar at the top of the Security Console Web interface. You can also check the status of all discovery connections on the Discovery Connections page. See [Creating and managing Dynamic Discovery connections](doc:creating-and-managing-dynamic-discovery-connections) .

If you create a discovery connection but don’t initiate discovery with that connection, or if you initiate a discovery but the connection becomes inactive, you will see an advisory icon in the top, left corner of the Web interface page. Roll over the icon to see a message about inactive connections. The message includes a link that you can click to initiate discovery.

After InsightVM discovers assets, they also appear in the Discovered by Connection table on the Assets page. See [Locating and working with assets](doc:locating-assets) for more information.