---
title: "Configuring a site using a Dynamic Discovery connection"
excerpt: ""
---
To create a dynamic site you must meet the following prerequisites:

* You must have a live Dynamic Discovery connection.
* You must initiate Dynamic Discovery in most cases. See [Initiating Dynamic Discovery](doc:initiating-dynamic-discovery).
[block:callout]
{
  "type": "info",
  "body": "This process does not apply to McAfee ePolicy Orchestrator or McAfee Data Exchange Layer connections."
}
[/block]
If you attempt to create a site based on a number of discovered assets that exceeds the maximum number of scan targets in your license, you will see an error message instructing you to change your filter criteria to reduce the number of discovered assets. See [Using filters to refine Dynamic Discovery](doc:using-filters-to-refine-dynamic-discovery).
[block:callout]
{
  "type": "info",
  "body": "When you create a site using a Dynamic Discovery connection, all assets that meet the site’s filter criteria will not be correlated to assets that are part of existing sites. An asset that is listed in two sites is essentially regarded as two assets from a license perspective."
}
[/block]
After creating and initiating a discovery connection, you can continue configuring a site.

## Topics for site configuration
* [Selecting a Scan Engine or engine pool for a site](doc:selecting-a-scan-engine-for-a-site) 
* [Selecting a scan template](doc:selecting-a-scan-template) 
* [Scheduling scans](doc:scheduling-scans) 
* [Setting up scan alerts](doc:setting-up-scan-alerts) 
* [Configuring scan credentials](doc:configuring-scan-credentials) 
* [Giving users access to a site](doc:giving-users-access-to-a-site)

###Managing assets in a dynamically changing site

For many types of Dynamic Discovery connections, as long as the connection is active, asset membership in a the site is subject to change whenever changes occur in the target environment.
[block:callout]
{
  "type": "info",
  "body": "Types of connections whose sites can change dynamically in this way include connections to Amazon Web Services, DHCP log servers, and VMware servers. Due to the way assets are discovered through McAfee ePolicy Orchestrator (ePO) and McAfee Data Exchange Layer (DXL), sites using those types of connections will not update dynamically in this way. To learn more, see [Discovering assets managed by McAfee ePolicy Orchestrator](doc:discovering-assets-managed-by-mcafee-epolicy-orchestrator)."
}
[/block]
You can also change asset membership by changing the discovery connection or filters. See [Using filters to refine Dynamic Discovery](doc:using-filters-to-refine-dynamic-discovery).

To view and change asset membership:
1. Click that **Edit** icon of the site you want to edit in the _Sites_ table on the _Home_ page.
2. Select the **Assets** tab.
3. The _Connection_ option for specifying assets is already selected. Do not change it.
4. Click **Select Connection**.
5. Select a different connection from the drop-down list if desired.
6. Click the **Filters** button to change asset membership if desired. [Using filters to refine Dynamic Discovery](doc:using-filters-to-refine-dynamic-discovery).
7. Click **Save** in the _Site Configuration_.

Whenever a change occurs in the target discovery environment, such as new virtual machines being added or removed, that change is reflected in the dynamic site asset list. This keeps your visibility into your target environment current.

Another benefit is that if the number of discovered assets in the dynamic site list exceeds the number of maximum scan targets in your license, you will see a warning to that effect before running a scan. This ensures that you do not run a scan and exclude certain assets. If you run a scan without adjusting the asset count, the scan will target assets that were previously discovered. You can adjust the asset count by refining the discovery filters for your site.

If you change the discovery connection or discovery filter criteria for a dynamic site that has been scanned, asset membership will be affected in the following ways: All assets that have not been scanned and no longer meet new discovery filter criteria, will be deleted from the site list. All assets that have been scanned and have scan data associated with them will remain on the site list whether or not they meet new filter discovery criteria. All newly discovered assets that meet new filter criteria will be added to the dynamic site list.