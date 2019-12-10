---
title: "Performing filtered asset searches"
excerpt: ""
---
When dealing with networks of large numbers of assets, you may find it necessary or helpful to concentrate on a specific subset. The filtered asset search feature allows you to search for assets based on criteria that can include IP address, site, operating system, software, services, vulnerabilities, and asset name. You can then save the results as a dynamic asset group for tracking, scanning, and reporting purposes. See [Using the search feature](doc:using-the-web-interface#section-using-the-search-feature).

Using search filters, you can find assets of immediate interest to you. This helps you to focus your remediation efforts and to manage the sheer quantity of assets running on a large network.

To start a filtered asset search:

Click the **Asset Filter** icon ![Alt](https://files.readme.io/6d02c9a-i_asset_filtered_search.jpg), which appears below and to the right of the **Search** box in the Web interface. 
OR
Click the **Create** tab at the top of the page and then select _Dynamic Asset Group_ from the drop-down list.
The _Filtered asset search_ page appears.
OR
Click the **Administration** icon to go to the _Administration_ page, and then click the _dynamic_ link next to _Asset Groups_.
OR
[block:callout]
{
  "type": "info",
  "body": "Performing a filtered asset search is the first step in creating a dynamic asset group"
}
[/block]
Click **New Dynamic Asset Group** if you are on the _Asset Groups_ page.

##Configuring asset search filters

A search filter allows you to choose the attributes of the assets that you are interested in. You can add multiple filters for more precise searches. For example, you could create filters for a given IP address range, a particular operating system, and a particular site, and then combine these filters to return a list of all the assets that simultaneously meet all the specified criteria. Using fewer filters typically increases the number of search results.

You can combine filters so that the search result set contains only the assets that meet all of the criteria in all of the filters (leading to a smaller result set). Or you can combine filters so that the search result set contains any asset that meets all of the criteria in any given filter (leading to a larger result set). See [Combining filters](doc:performing-filtered-asset-searches#section-combining-filters).

The following asset search filters are available:

   [Filtering by asset name](doc:performing-filtered-asset-searches#section-filtering-by-asset-name)

   [Filtering by container image](doc:performing-filtered-asset-searches#section-filtering-by-container-image)

   [Filtering by container status](doc:performing-filtered-asset-searches#section-filtering-by-container-status)

   [Filtering by containers](doc:performing-filtered-asset-searches#section-filtering-by-containers)

   [Filtering by CVE ID](doc:performing-filtered-asset-searches#section-filtering-by-cve-id)

   [Filtering by host type](doc:performing-filtered-asset-searches#section-filtering-by-host-type)

   [Filtering by IP address](doc:performing-filtered-asset-searches#section-filtering-by-ip-address)

   [Filtering by IP address type](doc:performing-filtered-asset-searches#section-filtering-by-ip-address-type)

   [Filtering by last scan date](doc:performing-filtered-asset-searches#section-filtering-by-last-scan-date)

   [Filtering by mobile device last sync time](doc:performing-filtered-asset-searches#section-filtering-by-asset-name)

   [Filtering by other IP address type](doc:performing-filtered-asset-searches#section-filtering-by-other-ip-address-type)

   [Filtering by operating system name](doc:performing-filtered-asset-searches#section-filtering-by-operating-system-name)

   [Filtering by PCI compliance status](doc:performing-filtered-asset-searches#section-filtering-by-pci-compliance-status)

   [Filtering by service name](doc:performing-filtered-asset-searches#section-filtering-by-service-name)

   [Filtering by open port numbers](doc:performing-filtered-asset-searches#section-filtering-by-open-port-numbers)

   [Filtering by operating system name](doc:performing-filtered-asset-searches#section-filtering-by-operating-system-name)

   [Filtering by software name](doc:performing-filtered-asset-searches#section-filtering-by-software-name)

   [Filtering by presence of validated vulnerabilities](doc:performing-filtered-asset-searches#section-filtering-by-presence-of-validated-vulnerabilities)

   [Filtering by user-added criticality level](doc:performing-filtered-asset-searches#section-filtering-by-user-added-criticality-level)

   [Filtering by user-added custom tag](doc:performing-filtered-asset-searches#section-filtering-by-user-added-custom-tag)

   [Filtering by user-added tag (location)](doc:performing-filtered-asset-searches#section-filtering-by-user-added-tag-location-)

   [Filtering by user-added tag (owner)](doc:performing-filtered-asset-searches#section-filtering-by-user-added-tag-owner-)

   [Filtering by vAsset cluster](doc:performing-filtered-asset-searches#section-filtering-by-vasset-cluster)

   [Filtering by vAsset datacenter](doc:performing-filtered-asset-searches#section-filtering-by-vasset-datacenter)

   [Filtering by vAsset host](doc:performing-filtered-asset-searches#section-filtering-by-vasset-host)

   [Filtering by vAsset power state](doc:performing-filtered-asset-searches#section-filtering-by-vasset-power-state)

   [Filtering by vAsset resource pool path](doc:performing-filtered-asset-searches#section-filtering-by-vasset-resource-pool-path)

   [Filtering by CVSS risk vectors](doc:performing-filtered-asset-searches#section-filtering-by-cvss-risk-vectors)

   [Filtering by vulnerabilities assessed](doc:performing-filtered-asset-searches#section-filtering-by-vulnerabilities-assessed)

   [Filtering by vulnerability category](doc:performing-filtered-asset-searches#section-filtering-by-vulnerability-category)

   [Filtering by vulnerability CVSS score](doc:performing-filtered-asset-searches#section-filtering-by-vulnerability-cvss-score)

   [Filtering by vulnerability exposures](doc:performing-filtered-asset-searches#section-filtering-by-vulnerability-exposures)

   [Filtering by vulnerability risk scores](doc:performing-filtered-asset-searches#section-filtering-by-vulnerability-risk-scores)

   [Filtering by vulnerability title](doc:performing-filtered-asset-searches#section-filtering-by-vulnerability-title)

To select filters in the _Filtered asset search_ panel take the following steps:
1. Use the first drop-down list.
When you select a filter, the configuration options, _operators_, for that filter dynamically become available.
2. Select the appropriate operator. Note: Some operators allow text searches. You can use the * wildcard in any of the text searches.
3. Use the **+** button to add filters.
4. Use the **-** button to remove filters.
5. Click **Reset** to remove all filters.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/3b139a7-s_DAG_search.jpg",
        "s_DAG_search.jpg",
        1439,
        211,
        "#e7e8e6"
      ],
      "caption": "Asset search filters"
    }
  ]
}
[/block]
###Filtering by asset name

The asset name filter lets you search for assets based on the asset name. The filter applies a search string to the asset names, so that the search returns assets that meet the specified criteria. It works with the following operators:

* _is_ returns all assets whose names match the search string exactly.
* _is not_ returns all assets whose names do not match the search string.
* _starts with_ returns all assets whose names begin with the same characters as the search string.
* _ends with_ returns all assets whose names end with the same characters as the search string.
* _contains_ returns all assets whose names contain the search string anywhere in the name.
* _does not contain_ returns all assets whose names do not contain the search string.

After you select an operator, you type a search string for the asset name in the blank field.

You can search using regex (regular expressions) to match or filter assets based on the particular regex entered using the options of like or not like from the drop-down list. For more information on using regex, see [Using regular expressions](doc:using-regular-expressions).

###Filtering by container image

The container image filter lets you search for assets by a container image name. The filter applies a search string to the container image name, so that the search returns assets that meet the specified criteria. It works with the following operators:

* _is_ returns all assets whose image names match the search string exactly.
* _is not_ returns all assets whose image names do not match the search string.
* _starts with_ returns all assets whose image names begin with the same characters as the search string.
* _ends with_ returns all assets whose image names contain the search string anywhere in the name.
* _contains_ returns all assets whose image names contain the search string anywhere in the name.
* _does not contain_ returns all assets whose image names do not contain the search string.

After you select an operator, enter a search string for the container image name in the blank field.
[block:callout]
{
  "type": "info",
  "title": "NOTE",
  "body": "Assets that run Docker services are considered **container hosts**.  This can include assets with no images or containers."
}
[/block]
You can search using regex (regular expressions) to match or filter assets based on the particular regex entered using the options of _like_ or _not like_ from the drop-down list.  For more information on using regex, see [Using regular expressions](doc:using-regular-expressions).

###Filtering by container status

The container status filter lets you search for assets based on the current condition of its containers.  Containers can be queried based on the following statuses:

* _created_
* _running_
* _paused_
* _restarted_
* _exited_
* _dead_

Two operators can be used for checking against these statuses:

* _is_ will return all assets with containers that match the specified status.
* _is not_ will return all assets with containers that DO NOT match the specified status.

###Filtering by containers

The containers filter lets you search for assets based on whether or not they are hosting containers.  The _are_ operator can be used with the following conditions:

* _present_ will return all assets that are hosting containers.
* _not present_ will return all assets that are NOT hosting containers.
[block:callout]
{
  "type": "info",
  "title": "NOTE",
  "body": "Assets with containers in a dead status are **still considered** container hosts, and as a result, will be returned by the _present_ condition."
}
[/block]
###Filtering by CVE ID

The _CVE ID_ filter lets you search for assets based on the CVE ID. The CVE identifiers (IDs) are unique, common identifiers for publicly known information security vulnerabilities. For more information, see [https://cve.mitre.org/cve/identifiers/index.html](https://cve.mitre.org/cve/identifiers/index.html). The filter applies a search string to the CVE IDs, so that the search returns assets that meet the specified criteria. It works with the following operators:

* _is_ returns all assets whose CVE IDs match the search string exactly.
* _is not_ returns all assets whose CVE IDs do not match the search string.
* _contains_ returns all assets whose CVE IDs contain the search string anywhere in the name.
* _does not contain_ returns all assets whose CVE IDs do not contain the search string.

After you select an operator, you type a search string for the CVE ID in the blank field.

###Filtering by host type

The _Host type_ filter lets you search for assets based on the type of host system, where assets can be any one or more of the following types:

* _Bare metal_ is physical hardware.
* _Hypervisor_ is a host of one or more virtual machines.
* _Virtual machine_ is an all-software guest of another computer.
* _Unknown_ is a host of an indeterminate type.

You can use this filter to track, and report on, security issues that are specific to host types. For example, a hypervisor may be considered especially sensitive because if it is compromised then any guest of that hypervisor is also at risk.

The filter applies a search string to host types, so that the search returns a list of assets that either match, or do not match, the selected host types.

It works with the following operators:

* _is_ returns all assets that match the host type that you select from the adjacent drop-down list.
* _is not_ returns all assets that do not match the host type that you select from the adjacent drop-down list.

You can combine multiple host types in your criteria to search for assets that meet multiple criteria. For example, you can create a filter for “is Hypervisor” and another for “is virtual machine” to find all-software hypervisors.

###Filtering by IP address type

If your environment includes IPv4 and IPv6 addresses, you can find assets with either address format. This allows you to track and report on specific security issues in these different segments of your network. The _IP address type_ filter works with the following operators:

* _is_ returns all assets that have the specified address format.
* _is not_ returns all assets that do not have the specified address formats.

After selecting the filter and desired operator, select the desired format: _IPv4_ or _IPv6_.

###Filtering by IP address

With the _IP address_ filter, you can discover assets that match or do not have a specific IP address, or that have IP addresses, or do not have IP addresses, within a specific range. This filter works with the following operators:

* _is_ returns an asset with the specified IP address.
* _is not_ returns all assets that do not have the specified IP address.
* _is in the range of_ returns all assets with IP addresses that fall within the IP address range.
* _is not in the range of_ returns all assets whose IP addresses do not fall into the IP address range.
* _like_ returns all assets whose IP addresses match the specified IP address.
* _not like_ returns all assets whose IP addresses do not match the specified IP address.

When you select the is in the range of or is not in the range of filters, you will see two blank fields separated by the word to. You use the left field to enter the start of the IP address range, and use the right to enter the end of the range.

The format for IPv4 addresses is a “dotted quad.” Example:
```
192.168.2.1 to 192.168.2.254
```
You can combine multiple search types in your query to focus on very specific assets. For instance, you can search for IP addresses in the range 192.168.2.1 to 192.168.2.254, but exclude 192.168.2.7 and 192.168.2.199.

###Filtering by last scan date

The last scan date filter lets you search for assets based on when they were last scanned. You may want, for example, to run a report on the most recently scanned assets. Or, you may want to find assets that have not been scanned in a long time and then delete them from the database because they are no longer be considered important for tracking purposes. The filter works with the following operators:

* _on or before_ returns all assets that were last scanned on or before a particular date. After selecting this operator, click the calendar icon to select the date.
* _on or after_ returns all assets that were last scanned on or after a particular date. After selecting this operator, click the calendar icon to select the date.
* _between and including_ returns all assets that were last scanned between, and including, two dates. After selecting this operator, click the calendar icon next to the left field to select the first date in the range. Then click the calendar icon next to the right field to select the last date in the range.
* _earlier than_ returns all assets that were last scanned earlier than a specified number of days preceding the date on which you initiate the search. After selecting this operator, enter a number in the days ago field. The starting point of the search is midnight of the day that the search is performed. For example, you initiate a search at 3 p.m. on January 23. You select this operator and enter 3 in the days ago field. The search returns all assets that were last scanned prior to midnight on January 20.
* _within the last_ returns all assets that were last scanned within a specified number of preceding days. After selecting this operator, enter a number in the days field. The starting point of the search is midnight of the day that the search is performed. For example: You initiate the search at 3 p.m. on January 23. You select this operator and enter 1 in the days field. The search returns all assets that were last scanned since midnight on January 22.

Keep several things in mind when using this filter:

* The search only returns _last_ scan dates. If an asset was scanned within the time frame specified in the filter, and if that scan was not the most recent scan, it will not appear in the search results.
* Dynamic asset group membership can change as new scans are run.
* Dynamic asset group membership is recalculated daily at midnight. If you create a dynamic asset group based on searches with the relative-day operators (_earlier than_ or _within the last_), the asset membership will change accordingly.
* This filter returns results for all types of scans - e.g. discovery, vulnerability, or policy scans. If you are specifically interested in vulnerability scans, you should look into [Filtering by vulnerabilities assessed](doc:performing-filtered-asset-searches#section-filtering-by-vulnerabilities-assessed).

###Filtering by mobile device last sync time
[block:callout]
{
  "type": "warning",
  "body": "This filter is only available with WinRM/PowerShell and WinRM/Office 365 Dynamic Discovery connections."
}
[/block]
With the _Last Synch Time_ filter, you can track mobile devices based on the most recent time they synchronized with the Exchange server. This filter can be useful if you do not want your reports to include data from old devices that are no longer in use on the network. It works with the following operators.

* _earlier_ than returns all mobile devices that synchronized earlier than a number of preceding days that you enter in a text box.
* _within_ the last returns all mobile devices that synchronized within a number of preceding days that you enter in a text box.

###Filtering by open port numbers

Having certain ports open may violate configuration policies. The _open port number_ filter lets you search for assets with a specified port open. By isolating assets with open ports, you can then close those ports and then re-scan them to verify that they are closed. Select an operator, and then enter your port or port range. Depending on your criteria, search results will return assets that have open ports, assets that do not have open ports, and assets with a range of open ports.

The filter works with the following operators:

* _is_ returns all assets with that port open.
* _is not_ returns all assets that do not have that port open.
* _is in the range of_ returns all assets within a range of designated ports.

###Filtering by operating system name

The _operating system name_ filter lets you search for assets based on their hosted operating systems. Depending on the search, you choose from a list of operating systems, or enter a search string. The filter returns a list of assets that meet the specified criteria.

It works with the following operators:

* _contains_ returns all assets running on the operating system whose name contains the characters specified in the search string. You enter the search string in the adjacent field. You can use an asterisk (*) as a wildcard character.
* _does not contain_ returns all assets running on the operating system whose name does not contain the characters specified in the search string. You enter the search string in the adjacent field. You can use an asterisk (*) as a wildcard character.
* _is empty_ returns all assets that do not have an operating system identified in their scan results. If an operating system is not listed for a scanned asset in the Web interface or reports, this means that the asset may not have been fingerprinted. If the asset was scanned with credentials, failure to fingerprint indicates that the credentials were not authenticated on the target asset. Therefore, this operator is useful for finding assets that were scanned with failed credentials or without credentials.
* _is not empty_ returns all assets that have an operating system identified in their scan results. This operator is useful for finding assets that were scanned with authenticated credentials and fingerprinted.

###Filtering by other IP address type

This filter allows you to find assets that have other IPv4 or IPv6 addresses in addition to the address(es) that you are aware of. When the application scans an IP address that has been included in a site configuration, it discovers any other addresses for that asset. This may include addresses that have not been scanned. For example: A given asset may have an IPv4 address and an IPv6 address. When configuring scan targets for your site, you may have only been aware of the IPv4 address, so you included only that address to be scanned in the site configuration. When you run the scan, the application discovers the IPv6 address. By using this asset search filter, you can search for all assets to which this scenario applies. You can add the discovered address to a site for a future scan to increase your security coverage.

After you select the filter and operators, you select either _IPv4_ or _IPv6_ from the drop-down list.

The filter works with one operator:

* _is_ returns all assets that have other IP addresses that are either IPv4 or IPv6.

###Filtering by PCI compliance status

The _PCI status_ filter lets you search for assets based on whether they return Pass or Fail results when scanned with the PCI audit template. Finding assets that fail compliance scans can help you determine at a glance which require remediation in advance of an official PCI audit.

It works with two operators:

* _is_ returns all assets that have a _Pass_ or _Fail_ status.
* _is not_ returns all assets that do not have a _Pass_ or _Fail_ status.

After you select an operator, select the _Pass_ or _Fail_ option from the drop-down list.

###Filtering by service name

The _service name_ filter lets you search for assets based on the services running on them. The filter applies a search string to service names, so that the search returns a list of assets that either have or do not have the specified service.

It works with the following operators:

* _contains_ returns all assets running a service whose name contains the search string. You can use an asterisk (*) as a wildcard character.
* _does not contain_ returns all assets that do not run a service whose name contains the search string. You can use an asterisk (*) as a wildcard character.

After you select an operator, you type a search string for the service name in the blank field.

###Filtering by site name

The _site name_ filter lets you search for assets based on the name of the site to which the assets belong.

This is an important filter to use if you want to control users’ access to newly discovered assets in sites to which users do not have access. See the note in [Using dynamic asset groups](doc:working-with-asset-groups#section-using-dynamic-asset-groups) .

The filter applies a search string to site names, so that the search returns a list of assets that either belong to, or do not belong to, the specified sites.

It works with the following operators:

* _is_ returns all assets that belong to the selected sites. You select one or more sites from the adjacent list.
* _is not_ returns all assets that do not belong to the selected sites. You select one or more sites from the adjacent list.

###Filtering by software name

The _software name filter lets you search for assets based on software installed on them. The filter applies a search string to software names, so that the search returns a list of assets that either runs or does not run the specified software.

It works with the following operators:

* _contains_ returns all assets with software installed such that the software’s name contains the search string. You can use an asterisk (*) as a wildcard character.
* _does not contain_ returns all assets that do not have software installed such that the software’s name does not contain the search string. You can use an asterisk (*) as a wildcard character.

After you select an operator, you enter the search string for the software name in the blank field.

###Filtering by presence of validated vulnerabilities

The _Validated vulnerabilities_ filter lets you search for assets with vulnerabilities that have been validated with exploits through Metasploit integration. By using this filter, you can isolate assets with vulnerabilities that have been proven to exist with a high degree of certainty. For more information, see [Working with validated vulnerabilities](doc:working-with-vulnerabilities#section-working-with-validated-vulnerabilities).

The filter works with one operator:

* The _are_ operator, combined with the _present_ drop-down list option, returns all assets with validated vulnerabilities.
* The _are_ operator, combined with the _not present_ drop-down list option, returns all assets without validated vulnerabilities.

###Filtering by user-added criticality level

The _user-added criticality level_ filter lets you search for assets based on the criticality tags that you and your users have applied to them. For example, a user may set all assets belonging to company executives to be of a “Very High” criticality in their organization. Using this filter, you could identify assets with that criticality set, regardless of their sites or other associations. You can search for assets with or without a specific criticality level, assets whose criticality is above or below a specific level, or assets with or without any criticality set. For more information on criticality levels, see [Applying RealContext with tags](doc:applying-realcontext-with-tags).

The filter works with the following operators:

* _is_ returns all assets that are set to a specified criticality level.
* _is not_ returns all assets are not set to a specified criticality level.
* _is higher than_ returns all assets whose criticality level is higher than the specified level.
* _is lower than_ returns all assets whose criticality level is lower than the specified level.
* _is applied_ returns all assets that have any criticality set.
* _is not applied_ returns all assets that have no criticality set.

After you select an operator, you select a criticality level from the drop-down menu. Available criticality levels are _Very High_, _High_, _Medium_, _Low_, and _Very Low_.

###Filtering by user-added custom tag

The _user-added custom tag_ filter lets you search for assets based on the custom tags that users have applied to them. For example, your company may have assets involved in an online banking process distributed throughout various locations and subnets, and a user may have tagged the involved assets with a custom “Online Banking” tag. Using this filter, you could identify assets with that tag, regardless of their sites or other associations. You can search for assets with or without a specific tag, assets whose custom tags meet certain criteria, or assets with or without any user-added custom tags. For more information on user-added custom tags, see [Applying RealContext with tags](doc:applying-realcontext-with-tags).

The filter works with the following operators:

* _is_ returns all assets with custom tags that match the search string exactly.
* _is not_ returns all assets that do not have a custom tag that matches the exact search string.
* _starts with_ returns all assets with custom tags that begin with the same characters as the search string.
* _ends with_ returns all assets with custom tags that end with the same characters as the search string.
* _contains_ returns all assets whose custom tags contain the search string anywhere in their names.
* _does not contain_ returns all assets whose custom tags do not contain the search string.
* _is applied_ returns all assets that have any custom tag applied.
* _is not applied_ returns all assets that have no custom tags applied.

After you select an operator, you type a search string for the custom tag in the blank field.

###Filtering by user-added tag (location)

The _user-added tag (location)_ filter lets you search for assets based on the location tags that users have applied to them. For example, a user may have created and applied tags for “Akron” and “Cincinnati” to clarify the physical location of assets in a user-friendly way. Using this filter, you could identify assets with that tag, regardless of their other associations. You can search for assets with or without a specific tag, assets whose location tags meet certain criteria, or assets with or without any user-added location tags. For more information on user-added location tags, see [Applying RealContext with tags](doc:applying-realcontext-with-tags).

The filter works with the following operators:

* _is_ returns all assets with location tags that match the search string exactly.
* _is not_ returns all assets that do not have a location tag that matches the exact search string.
* _starts with_ returns all assets with location tags that begin with the same characters as the search string.
* _ends with_ returns all assets with location tags that end with the same characters as the search string.
* _contains_ returns all assets whose location tags contain the search string anywhere in their names.
* _does not contain_ returns all assets whose location tags do not contain the search string.
* _is applied_ returns all assets that have any location tag applied.
* _is not applied_ returns all assets that have no location tags applied.

After you select an operator, you type a search string for the location tag in the blank field.

###Filtering by user-added tag (owner)

The _user-added tag (owner)_ filter lets you search for assets based on the owner tags that users have applied to them. For example, a company may have different people responsible for different assets. A user can tag the assets each person is responsible for and use this information to track the risk level of those assets. You can search for assets with or without a specific tag, assets whose owner tags meet certain criteria, or assets with or without any user-added owner tags. For more information on user-added owner tags, see [Applying RealContext with tags](doc:applying-realcontext-with-tags).

The filter works with the following operators:

* _is_ returns all assets with owner tags that match the search string exactly.
* _is not_ returns all assets that do not have an owner tag that matches the exact search string.
* _starts with_ returns all assets with owner tags that begin with the same characters as the search string.
* _ends with_ returns all assets with owner tags that end with the same characters as the search string.
* _contains_ returns all assets whose owner tags contain the search string anywhere in their names.
* _does not contain_ returns all assets whose owner tags do not contain the search string.
* _is applied_ returns all assets that have any owner tag applied.
* _is not applied_ returns all assets that have no owner tags applied.

After you select an operator, you type a search string for the location tag in the blank field.

###Using vAsset filters

The following _vAsset_ filters let you search for virtual assets that you track with vAsset discovery. Creating dynamic asset groups for virtual assets based on specific criteria can be useful for analyzing different segments of your virtual environment. For example, you may want to run reports or assess risk for all the virtual assets used by your accounting department, and they are all supported by a specific resource pool. For information about vAsset discovery, see [Discovering virtual machines managed by VMware vCenter or ESX/ESXi](doc:managing-dynamic-discovery-of-assets#section-discovering-virtual-machines-managed-by-vmware-vcenter-or-esx-esxi) .

###Filtering by vAsset cluster

The _vAsset cluster_ filter lets you search for virtual assets that belong, or don’t belong, to specific clusters. This filter works with the following operators:

* _is_ returns all assets that belong to clusters whose names match an entered string exactly.
* _is not_ returns all assets that belong to clusters whose names do not match an entered string.
* _contains_ returns all assets that belong to clusters whose names contain an entered string.
* _does not contain_ returns all assets that belong to clusters whose names do not contain an entered string.
* _starts with_ returns all assets that belong to clusters whose names begin with the same characters as an entered string.

After you select an operator, you enter the search string for the cluster in the blank field.

###Filtering by vAsset datacenter

The _vAsset datacenter_ filter lets you search for assets that are managed, or are not managed, by specific datacenters. This filter works with the following operators:

* _is_ returns all assets that are managed by datacenters whose names match an entered string exactly.
* _is not_ returns all assets that are managed by datacenters whose names do not match an entered string.

After you select an operator, you enter the search string for the datacenter name in the blank field.

###Filtering by vAsset host

The _vAsset host_ filter lets you search for assets that are guests, or are not guests, of specific host systems. This filter works with the following operators:

* _is_ returns all assets that are guests of hosts whose names match an entered string exactly.
* _is not_ returns all assets that are guests of hosts whose names do not match an entered string.
* _contains_ returns all assets that are guests of hosts whose names contain an entered string.
* _does not contain_ returns all assets that are guests of hosts whose names do not contain an entered string.
* _starts with_ returns all assets that are guests of hosts whose names begin with the same characters as an entered string.

After you select an operator, you enter the search string for the host name in the blank field.

###Filtering by vAsset power state

The _vAsset power state_ filter lets you search for assets that are in, or are not in, a specific power state. This filter works with the following operators:

* _is_ returns all assets that are in a power state selected from a drop-down list.
* _is not_ returns all assets that not are in a power state selected from a drop-down list.

After you select an operator, you select a power state from the drop-down list. Power states include on, off, or suspended.

###Filtering by vAsset resource pool path

The _vAsset resource pool path_ filter lets you discover assets that belong, or do not belong, to specific resource pool paths. This filter works with the following operators:

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

The virtual machines that belong to the _Management_ and _Workstations_ levels are different in each path. If you only specify _Management_ in your filter, the search will return all virtual machines that belong to the _Management_ and _Workstations_ levels in both resource pool paths.

However, if you specify _Advertising_ -> _Management_ -> _Workstations_, the search will only return virtual assets that belong to the Workstations pool in the path with _Advertising_ as the highest level.

After you select an operator, you enter the search string for the resource pool path in the blank field.

###Filtering by CVSS risk vectors

The filters for the following Common Vulnerability Scoring System (CVSS) risk vectors let you search for assets based on vulnerabilities that pose different types or levels of risk to your organization’s security:

* _CVSS Access Complexity (AC)_
* _CVSS Access Vector (AV)_
* _CVSS Authentication Required (Au)_
* _CVSS Availability Impact (A)_
* _CVSS Confidentiality Impact (C)_
* _CVSS Integrity Impact (I)_

You can also apply filters based on the newer CVSS Version 3 risk vectors:

* _CVSSV3 Attack Complexity (AC)_
* _CVSSV3 Attack Vector (AV)_
* _CVSSV3 Availability Impact (A)_
* _CVSSV3 Confidentiality Impact (C)_
* _CVSSV3 Integrity Impact (I)_
* _CVSSV3 Privileges Required (PR)_
* _CVSSV3 User Interaction (UI)_
[block:callout]
{
  "type": "warning",
  "body": "It is possible that a vulnerability might **not** have Version 3 data, so be mindful of this when applying Version 3 filters to an asset search.  Assets excluded by a Version 3 filter may still be affected by Version 2 vectors."
}
[/block]
These filters refer to the industry-standard vectors used in calculating CVSS scores and PCI severity levels. They are also used in risk strategy calculations for risk scores. For detailed information about CVSS vectors, go to the National Vulnerability Database Web site at [https://nvd.nist.gov/](https://nvd.nist.gov/).

Using these filters, you can find assets based on different exploitability attributes of the vulnerabilities found on them, or based on the different types and degrees of impact to the asset in the event of compromise through the vulnerabilities found on them. Isolating these assets can help you to make more informed decisions on remediation priorities or to prepare for a PCI audit.

All CVSS filters work with two operators:

* _is_ returns all assets that match a specific risk level or attribute associated with the CVSS vector.
* _is not_ returns all assets that do not match a specific risk level or attribute associated with the CVSS vector.

After you select a filter and an operator, select the desired impact level or likelihood attribute from the drop-down list. Version 2 attributes are as follows:

* For each of the three impact vectors (_Confidentiality_, _Integrity_, and _Availability_), the options are _Complete_, _Partial_, or _None_.
* For _CVSS Access Vector_, the options are _Local (L)_, _Adjacent (A)_, or _Network (N)_.
* For _CVSS Access Complexity_, the options are _Low_, _Medium_, or _High_.
* For _CVSS Authentication Required_, the options are _None_, _Single_, or _Multiple_.

Version 3 attributes:

* For each of the three impact vectors _(Confidentiality, Integrity, and Availability)_, the options are _None_, _Low_, or _High_.
* For _CVSSV3 Attack Vector_, the options are _Network (N)_, _Adjacent (A)_, _Local (L)_, or _Physical (P)_.
* For _CVSSV3 Attack Complexity_, the options are _Low_ or _High_.
* For _CVSSV3 Privileges Required_, the options are _None_, _Low_, or _High_.
* For _CVSSV3 User Interaction_, the options are _None_ or _Required_.


###Filtering by vulnerabilities assessed

The vulnerabilities assessed filter lets you search for assets based on when they were last scanned for vulnerabilities. In contrast to the [last scan](doc:performing-filtered-asset-searches#section-filtering-by-last-scan-date)  filter, this option lets you focus specifically on vulnerability assessments. You may want, for example, to run a report on the most recently scanned assets. Or, you may want to find assets that have not been scanned in a long time and then delete them from the database because they are no longer be considered important for tracking purposes. The filter works with the following operators:

* _on or before_ returns all assets that were last scanned for vulnerabilities on or before a particular date. After selecting this operator, click the calendar icon to select the date.
* _on or after_ returns all assets that were last scanned for vulnerabilities on or after a particular date. After selecting this operator, click the calendar icon to select the date.
* _between and including_ returns all assets that were last scanned for vulnerabilities between, and including, two dates. After selecting this operator, click the calendar icon next to the left field to select the first date in the range. Then click the calendar icon next to the right field to select the last date in the range.
* _earlier than_ returns all assets that were last scanned for vulnerabilities earlier than a specified number of days preceding the date on which you initiate the search. After selecting this operator, enter a number in the days ago field. The starting point of the search is midnight of the day that the search is performed. For example, you initiate a search at 3 p.m. on January 23. You select this operator and enter 3 in the days ago field. The search returns all assets that were last scanned prior to midnight on January 20.
* _within the last_ returns all assets that were last scanned for vulnerabilities within a specified number of preceding days. After selecting this operator, enter a number in the days field. The starting point of the search is midnight of the day that the search is performed. For example: You initiate the search at 3 p.m. on January 23. You select this operator and enter 1 in the days field. The search returns all assets that were last scanned since midnight on January 22.

Keep several things in mind when using this filter:

* The search only returns _last_ scan dates. If an asset was scanned within the time frame specified in the filter, and if that scan was not the most recent scan, it will not appear in the search results.
* Dynamic asset group membership can change as new scans are run.
* Dynamic asset group membership is recalculated daily at midnight. If you create a dynamic asset group based on searches with the relative-day operators (_earlier than_ or _within the last_), the asset membership will change accordingly.

###Filtering by vulnerability category

The _vulnerability category_ filter lets you search for assets based on the categories of vulnerabilities that have been flagged on them during scans. This is a useful filter for finding out at a quick glance how many, and which, assets have a particular type of vulnerability, such as ones related to Adobe, Cisco, or Telnet. Lists of vulnerability categories can be found in the _Vulnerability Checks_ section of the scan template configuration or the report configuration, where you can filter report scope based on vulnerabilities.

The filter applies a search string to vulnerability categories, so that the search returns a list of assets that either have or do not have vulnerabilities in categories that match that search string. It works with the following operators:

* _contains_ returns all assets with a vulnerability whose category contains the search string. You can use an asterisk (*) as a wildcard character.
* _does not contain_ returns all assets that do not have a vulnerability whose category contains the search string. You can use an asterisk (*) as a wildcard character.
* _is_ returns all assets with that have a vulnerability whose category matches the search string exactly.
* _is not_ returns all assets that do not have a vulnerability whose category matches the exact search string.
* _starts with_ returns all assets with vulnerabilities whose categories begin with the same characters as the search string.
* _ends with_ returns all assets with vulnerabilities whose categories end with the same characters as the search string.

After you select an operator, you type a search string for the vulnerability category in the blank field.

###Filtering by vulnerability CVSS score

The _Vulnerability CVSS score_ filter lets you search for assets with vulnerabilities that have a specific CVSS score or fall within a range of scores. You may find it helpful to create asset groups according to CVSS score ranges that correspond to PCI severity levels: low (0.0-3.9), medium (4.0-6.9), and high (7.0-10). Doing so can help you prioritize assets for remediation.

The filter works with the following operators:

* _is_ returns all assets with vulnerabilities that have a specified CVSS score.
* _is not_ returns all assets with vulnerabilities that do not have a specified CVSS score.
* _is in the range of_ returns all assets with vulnerabilities that fall within the range of two specified CVSS scores and include the high and low scores in the range.
* _is higher than_ returns all assets with vulnerabilities that have a CVSS score higher than a specified score.
* _is lower than_ returns all assets with vulnerabilities that have a CVSS score lower than a specified score.

After you select an operator, type a score in the blank field. If you select the range operator, you would type a low score and a high score to create the range. Acceptable values include any numeral from 0.0 to 10. You can only enter one digit to the right of the decimal. If you enter more than one digit, the score is automatically rounded up. For example, if you enter a score of 2.25, the score is automatically rounded up to 2.3.

###Filtering by vulnerability exposures

The _vulnerability exposures_ filter lets you search for assets based on the following types of exposures known to be associated with vulnerabilities discovered on those assets:

* Malware kit exploits
* Metasploit exploits
* Exploit Database exploits

This is a useful filter for isolating and prioritizing assets that have a higher likelihood of compromise due to these exposures.

The filter applies a search string to one or more of the vulnerability exposure types, so that the search returns a list of assets that either have or do not have vulnerabilities associated with the specified exposure types. It works with the following operators:

* _includes_ returns all assets that have vulnerabilities associated with specified exposure types.
* _does not include_ returns all assets that do not have vulnerabilities associated with specified exposure types.

After you select an operator, select one or more exposure types in the drop-down list. To select multiple types, hold down the **<Ctrl>** key and click all desired types.

###Filtering by vulnerability risk scores

The _vulnerability risk score_ filter lets you search for assets with vulnerabilities that have a specific risk score or fall within a range of scores. Isolating and tracking assets with higher risk scores, for example, can help you prioritize remediation for those assets.

The filter works with the following operators:

* _is in the range of_ returns all assets with vulnerabilities that fall within the range of two specified risk scores and include the high and low scores in the range.
* _is higher than_ returns all assets with vulnerabilities that have a risk score higher than a specified score.
* _is lower than_ returns all assets with vulnerabilities that have a risk score lower than a specified score.

After you select an operator, enter a score in the blank field. If you select the range operator, you would type a low score and a high score to create the range. Keep in mind your currently selected risk strategy when searching for assets based on risk scores. For example, if the currently selected strategy is Real Risk, you will not find assets with scores higher than 1,000. Refer to the risk scores in your vulnerability and asset tables for guidance.

###Filtering by vulnerability title

The _vulnerability title_ filter lets you search for assets based on the vulnerabilities that have been flagged on them during scans. This is a useful filter to use for verifying patch applications, or finding out at a quick glance how many, and which, assets have a particular high-risk vulnerability.

The filter applies a search string to vulnerability titles, so that the search returns a list of assets that either have or do not have the specified string in their titles. It works with the following operators:

* _contains_ returns all assets with a vulnerability whose name contains the search string. You can use an asterisk (*) as a wildcard character.
* _does not contain_ returns all assets that do not have a vulnerability whose name contains the search string. You can use an asterisk (*) as a wildcard character.
* _is_ returns all assets with that have a vulnerability whose name matches the search string exactly.
* _is not_ returns all assets that do not have a vulnerability whose name matches the exact search string.
* _starts with_ returns all assets with vulnerabilities whose names begin with the same characters as the search string.
* _ends with_ returns all assets with vulnerabilities whose names end with the same characters as the search string.

After you select an operator, you type a search string for the vulnerability name in the blank field.

###Combining filters

If you create multiple filters, you can have InsightVM return a list of assets that match all the criteria specified in the filters, or a list of assets that match _any_ of the criteria specified in the filters. You can make this selection in a drop-down list at the bottom of the _Search Criteria_ panel.

The difference between _All_ and _Any_ is that the _All_ setting will only return assets that match the search criteria in all of the filters, whereas the _Any_ setting will return assets that match any given filter. For this reason, a search with _All_ selected typically returns fewer results than _Any_.

For example, suppose you are scanning a site with 10 assets. Five of the assets run Linux, and their names are linux01, linux02, linux03, linux04, and linux05. The other five run Windows, and their names are win01, win02, win03, win04, and win05.

Suppose you create two filters. The first filter is an operating system filter, and it returns a list of assets that run Windows. The second filter is an asset filter, and it returns a list of assets that have “linux” in their names.

If you perform a filtered asset search with the two filters using the _All_ setting, the search will return a list of assets that run Windows and have “linux” in their asset names. Since no such assets exist, there will be no search results. However, if you use the same filters with the _Any_ setting, the search will return a list of assets that run Windows or have “linux” in their names. Five of the assets run Windows, and the other five assets have “linux” in their names. Therefore, the result set will contain all of the assets.