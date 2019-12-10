---
title: "Using filters to refine Dynamic Discovery"
excerpt: ""
---
You can use filters to refine Dynamic Discovery results based on specific discovery criteria. For example, you can limit discovery to assets that are managed by a specific resource pool or those with a specific operating system.
[block:callout]
{
  "type": "info",
  "body": "This process does not apply to McAfee ePolicy Orchestrator, McAfee Data Exchange Layer, or Active Directory connections."
}
[/block]

[block:callout]
{
  "type": "warning",
  "body": "If a set of filters is associated with a dynamic site, and if you change filters to include more assets than the maximum number of scan targets in your license, you will see an error message instructing you to change your filter criteria to reduce the number of discovered assets."
}
[/block]
Using filters has a number of benefits. You can limit the sheer number of assets that appear in the discovery results table. This can be useful in an environment with a high number of virtual assets. Also, filters can help you discover very specific assets. You can discover all assets within an IP address range, all assets that belong to a particular resource pool, or all assets that are powered on or off. You can combine filters to produce more granular results. For example, you can discover all of Windows 7 virtual assets on a particular host that are powered on.

For every filter that you select, you also select an operator that determines how that filter is applied. Then, depending on the filter and operator, you enter a string or select a value for that operator to apply.

You can create dynamic sites based on different sets of discovery results and track the security issues related to these types of assets by running scans and reports. See [Configuring a site using a Dynamic Discovery connection](doc:configuring-a-site-using-a-dynamic-discovery-connection) .

##Selecting filters for mobile devices

Three filters are available for mobile device connections:
* Operating System
* User
* Last Sync Time (WinRM/PowerShell and WinRM/Office 365 connections only)

###Operating System
With the _Operating System_ filter, you can discover assets based on their operating systems. This filter works with the following operators:
* _contains_ returns all assets with operating systems whose names contain an entered string.
* _does not contain_ returns all assets with operating systems whose names do not contain an entered string.

###User
With the _User_ filter, you can discover assets based on their associated user accounts. This filter works with the following operators:
* _contains_ returns all assets with user accounts whose names contain an entered string.
* _does not contain_ returns all assets with user accounts whose names do not contain an entered string.
* _is_ returns all assets with user accounts whose names match an entered string exactly.
* _is not_ returns all assets with user accounts whose names do not match an entered string.
* _starts_ with returns all assets with user accounts whose names begin with the same characters as an entered string.

###Last Sync Time
[block:callout]
{
  "type": "warning",
  "body": "This filter is only available with WinRM/PowerShell and WinRM/Office 365 Dynamic Discovery connections."
}
[/block]
With the _Last Synch Time_ filter, you can track mobile devices based on the most recent time they synchronized with the Exchange server. This filter can be useful if you do not want your reports to include data from old devices that are no longer in use on the network. It works with the following operators.

* _earlier than_ returns all mobile devices that synchronized earlier than a number of preceding days that you enter in a text box.
* _within the last_ returns all mobile devices that synchronized within a number of preceding days that you enter in a text box.

##Selecting filters and operators for AWS connections

Eight filters are available for AWS connections:
* Availability Zone
* Guest OS family
* Instance ID
* Instance Name
* Instance state
* Instance Type
* Region

### Availability Zone

With the _Availability Zone_ filter, you can discover assets located in specific Availability Zones. This filter works with the following operators:
* _contains_ returns all assets that belong to Availability Zones whose names contain an entered string.
* _does not contain_ returns all assets that belong to Availability Zones whose names do not contain an entered string.

### Guest OS family

With the _Guest OS family_ filter, you can discover assets that have, or do not have, specific operating systems. This filter works with the following operators:
* _contains_ returns all assets that have operating systems whose names contain an entered string.
* _does not contain_ returns all assets that have operating systems whose names do not contain an entered string.

### Instance ID

With the _Instance ID_ filter, you can discover assets that have, or do not have, specific Instance IDs. This filter works with the following operators:
* _contains_ returns all assets whose instance names whose instance IDs contain an entered string.
* _does not contain_ returns all assets whose instance IDs do not contain an entered string.

### Instance name

With the _Instance Name_ filter, you can discover assets that have, or do not have, specific Instance IDs. This filter works with the following operators:
* _is_ returns all assets whose instance names match an entered string exactly.
* _is not_ returns all assets whose instance names do not match an entered string.
* _contains_ returns all assets whose instance names contain an entered string.
* _does not contain_ returns all assets whose instance names do not contain an entered string.
* _starts with_ returns all assets whose instance names begin with the same characters as an entered string.

###Instance state

With the _Instance state_ filter, you can discover assets (instances) that are in, or are not in, a specific operational state. This filter works with the following operators:

* _is_ returns all assets that are in a state selected from a drop-down list.
* _is not_ returns all assets that are not in a state selected from a drop-down list.

Instance states include _Pending_, _Running_, _Shutting down_, _Stopped_, or _Stopping_.

### Instance type

With the _Instance type_ filter, you can discover assets that are, or are not, a specific instance type. This filter works with the following operators:
* _is_ returns all assets that are a type selected from a drop-down list.
* _is not_ returns all assets that are not a type selected from a drop-down list.

Instance types include _c1.medium_, _c1.xlarge_,_c3.2xlarge_, _c3.4xlarge_, or _c3.8xlarge_.
[block:callout]
{
  "type": "info",
  "body": "Dynamic Discovery search results may also include m1.small or t1.micro instance types, but Amazon does not currently permit scanning of these types."
}
[/block]
### IP address

With the _IP address_ filter, you can discover assets that match or do not have a specific IP address, or that have IP addresses, or do not have IP addresses, within a specific range. This filter works with the following operators:

* _is_ returns an asset with the specified IP address.
* _is not_ returns all assets that do not have the specified IP address.
* _is in the range of_ returns all assets with IP addresses that fall within the IP address range.
* _is not in the range of_ returns all assets whose IP addresses do not fall into the IP address range.
* _like_ returns all assets whose IP addresses match the specified IP address.
* _not like_ returns all assets whose IP addresses do not match the specified IP address.

When you select the _is in the range of_ or _is not in the range of_ filters, you will see two blank fields separated by the word to. You use the left field to enter the start of the IP address range, and use the right to enter the end of the range.

The format for IPv4 addresses is a “dotted quad.” Example:
```
192.168.2.1 to 192.168.2.254
```
You can combine multiple search types in your query to focus on very specific assets. For instance, you can search for IP addresses in the range 192.168.2.1 to 192.168.2.254, but exclude 192.168.2.7 and 192.168.2.199.

### Region

With the _Region type_ filter, you can discover assets that are in, or are not in, a specific geographic region. This filter works with the following operators:

* _is_ returns all assets that are in a region selected from a drop-down list.
* _is not_ returns all assets that are in a not a region selected from a drop-down list.
Regions include _Asia Pacific (Singapore)_, _Asia Pacific (Sydney)_, _Asia Pacific (Tokyo)_, _EU (Ireland)_, or _South American (Sao Paulo)_.

## Selecting filters and operators for VMware connections

Eight filters are available for VMware connections:
* Cluster
* Datacenter
* Guest OS family
* Host
* IP address range
* Power state
* Resource pool path
* Virtual machine name

###Cluster

With the _Cluster_ filter, you can discover assets that belong, or don’t belong, to specific clusters. This filter works with the following operators:
* _is_ returns all assets that belong to clusters whose names match an entered string exactly.
* _is not_ returns all assets that belong to clusters whose names do not match an entered string.
* _contains_ returns all assets that belong to clusters whose names contain an entered string.
* _does not contain_ returns all assets that belong to clusters whose names do not contain an entered string.
* _starts with_ returns all assets that belong to clusters whose names begin with the same characters as an entered string.

###Datacenter

With the _Datacenter_ filter, you can discover assets that are managed, or are not managed, by specific datacenters. This filter works with the following operators:
* _is_ returns all assets that are managed by datacenters whose names match an entered string exactly.
* _is not_ returns all assets that are managed by datacenters whose names do not match an entered string.

###Guest OS family

With the _Guest OS family_ filter, you can discover assets that have, or do not have, specific operating systems. This filter works with the following operators:

* _contains_ returns all assets that have operating systems whose names contain an entered string.
* _does not contain_ returns all assets that have operating systems whose names do not contain an entered string.

###Host

With the _Host_ filter, you can discover assets that are guests, or are not guests, of specific host systems. This filter works with the following operators:
* _is_ returns all assets that are guests of hosts whose names match an entered string exactly.
* _is not_ returns all assets that are guests of hosts whose names do not match an entered string.
* _contains_ returns all assets that are guests of hosts whose names contain an entered string.
* _does not contain_ returns all assets that are guests of hosts whose names do not contain an entered string.
* _starts with_ returns all assets that are guests of hosts whose names begin with the same characters as an entered string.

###IP address

With the _IP address_ filter, you can discover assets that match or do not have a specific IP address, or that have IP addresses, or do not have IP addresses, within a specific range. This filter works with the following operators:
* _is_ returns an asset with the specified IP address.
* _is not_ returns all assets that do not have the specified IP address.
* _is in the range of_ returns all assets with IP addresses that fall within the IP address range.
* _is not in the range of_ returns all assets whose IP addresses do not fall into the IP address range.
* _like_ returns all assets whose IP addresses match the specified IP address.
* _not like_ returns all assets whose IP addresses do not match the specified IP address.

When you select the _is in the range of_ or _is not in the range of filters_, you will see two blank fields separated by the word _to_. You use the left field to enter the start of the IP address range, and use the right to enter the end of the range.

###Power state

With the _Power state_ filter, you can discover assets that are in, or are not in, a specific power state. This filter works with the following operators:
* _is_ returns all assets that are in a power state selected from a drop-down list.
* _is not_ returns all assets that are not in a power state selected from a drop-down list.

Power states include _on_, _off_, or _suspended_.

###Resource pool path

With the _Resource pool path_ filter, you can discover assets that belong, or do not belong, to specific resource pool paths. This filter works with the following operators:

* _contains_ returns all assets that are supported by resource pool paths whose names contain an entered string.
* _does not contain_ returns all assets that are supported by resource pool paths whose names do not contain an entered string.

You can specify any level of a path, or you can specify multiple levels, each separated by a hyphen and right arrow: ->. This is helpful if you have resource pool path levels with identical names.

For example, you may have two resource pool paths with the following levels:

_Human Resources_ 
> _Management_
> > _Workstations_ 

_Advertising_
> _Management_ 
> > _Workstations_

The virtual machines that belong to the _Management_ and _Workstations_ levels are different in each path. If you only specify _Management_ in your filter, the application will discover all virtual machines that belong to the _Management_ and _Workstations_ levels in both resource pool paths.

However, if you specify _Advertising -> Management -> Workstations_, the application will only discover virtual assets that belong to the _Workstations_ pool in the path with _Advertising_ as the highest level.

###Virtual machine name

With the _Virtual machine name_ filter, you can discover assets that have, or do not have, a specific name. This filter works with the following operators:

* _is_ returns all assets whose names match an entered string exactly.
* _is not_ returns all assets whose names do not match an entered string.
* _contains_ returns all assets whose names contain an entered string.
* _does not contain_ returns all assets whose names do not contain an entered string.
* _starts with_ returns all assets whose names begin with the same characters as an entered string.

## Selecting filters and operators for DHCP connections

Three filters are available for VMware connections:
* Host name
* IP address
* MAC address

###Host

With the _Host_ filter, you can discover assets based on host names. This filter works with the following operators:
* _is_ returns all assets with host names that match an entered string exactly.
* _is not_ returns all assets with host names that do not match an entered string.
* _contains_ returns all assets with host names that contain an entered string.
* _does not contain_ returns all assets with host names that do not contain an entered string.
* _starts with_ returns all assets with host names that begin with the same characters as an entered string.

###IP address

With the _IP address_ filter, you can discover assets that match or do not have a specific IP address, or that have IP addresses, or do not have IP addresses, within a specific range. This filter works with the following operators:

* _is_ returns an asset with the specified IP address.
* _is not_ returns all assets that do not have the specified IP address.
* _is in the range of_ returns all assets with IP addresses that fall within the IP address range.
* _is not in the range of_ returns all assets whose IP addresses do not fall into the IP address range.
* _like_ returns all assets whose IP addresses match the specified IP address.
* _not like_ returns all assets whose IP addresses do not match the specified IP address.

When you select the _is in the range of_ or _is not in the range of_ filters, you will see two blank fields separated by the word to. You use the left field to enter the start of the IP address range, and use the right to enter the end of the range.

###MAC address

With the _MAC address_ filter, you can discover assets based on MAC addresses. This filter works with the following operators:

* _is_ returns all assets with MAC addresses that match an entered string exactly.
* _is not_ returns all assets with MAC addresses that do not match an entered string.
* _contains_ returns all assets with MAC addresses that contain an entered string.
* _does not contain_ returns all assets with MAC addresses that do not contain an entered string.
* _starts with_ returns all assets with MAC addresses that begin with the same characters as an entered string.

##Combining discovery filters

If you use multiple filters, you can have the application discover assets that match all the criteria specified in the filters, or assets that match any of the criteria specified in the filters.

The difference between these options is that the _all_ setting only returns assets that match the discovery criteria in all of the filters, whereas the _any_ setting returns assets that match any given filter. For this reason, a search with _all_ selected typically returns fewer results than _any_.

For example, a target environment includes 10 assets. Five of the assets run Ubuntu, and their names are Ubuntu01, Ubuntu02, Ubuntu03, Ubuntu04, and Ubuntu05. The other five run Windows, and their names are Win01, Win02, Win03, Win04, and Win05. Suppose you create two filters. The first discovery filter is an operating system filter, and it returns a list of assets that run Windows. The second filter is an asset filter, and it returns a list of assets that have “Ubuntu” in their names.

If you discover assets with the two filters using the _all_ setting, the application discovers assets that run Windows and have “Ubuntu” in their asset names. Since no such assets exist, no assets will be discovered. However, if you use the same filters with the any setting, the application discovers assets that run Windows or have “Ubuntu” in their names. Five of the assets run Windows, and the other five assets have “Ubuntu” in their names. Therefore, the result set contains all of the assets.

## Configuring and applying filters
[block:callout]
{
  "type": "warning",
  "body": "If a virtual asset doesn’t have an IP address, it can only be discovered and identified by its host name. It will appear in the discovery results, but it will not be added to a dynamic site. Assets without IP addresses cannot be scanned."
}
[/block]
After you initiate discovery as described in the preceding section, and the Security Console displays the results table, take the following steps to configure and apply filters:

Configure the filters.

1. Click **Add Filters**.
A filter row appears.
2. Select a filter type from the left drop-down list.
3. Select an operator from the right drop-down list.
4. Enter or select a value in the field to the right of the drop-down lists.
5. To add a new filter, click the **+** icon.
A new filter row appears. Set up the new filter as described in the preceding step.
6. Add more filters as desired. To delete any filter, click the appropriate **-** icon.
After you configure the filters, you can apply them to the discovery results.
Or, click **Reset** to clear all filters and start again.

Apply the filters.
1. Select the option to match _any_ or _all_ of the filters from the drop-down list below the filters.
2. Click **Filter**.

The discovery results table now displays assets based on filtered discovery.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/99b043a-s_nx_dynamic_discovery_vsphere_assets_filtered.jpg",
        "s_nx_dynamic_discovery_vsphere_assets_filtered.jpg",
        2058,
        1168,
        "#202b3a"
      ],
      "caption": "Applying Dynamic Discovery filters within a site configuration"
    }
  ]
}
[/block]