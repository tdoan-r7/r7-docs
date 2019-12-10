---
title: "Working with asset groups"
excerpt: ""
---
Asset groups provide different ways for members of your organization to grant access to, view, scan, and report on asset information. Asset groups allow you to create logical groupings that you can configure to dynamically incorporate new assets that meet specific criteria. You can define an asset group within a site in order to scan based on these groupings.

###Using asset groups to your advantage

One use case illustrates how asset groups can “spin off” organically from sites. A bank purchases InsightVM with a fixed-number IP address license. The network topology includes one head office and 15 branches, all with similar “cookie-cutter” IP address schemes. The IP addresses in the first branch are all 10.1.1.x.; the addresses in the second branch are 10.1.2.x; and so on. For each branch, whatever integer equals .x is a certain type of asset. For example .5 is always a server.

The security team scans each site and then “chunks” the information in various ways by creating reports for specific asset groups. It creates one set of asset groups based on locations so that branch managers can view vulnerability trends and high-level data. The team creates another set of asset groups based on that last integer in the IP address. The users in charge of remediating server vulnerabilities will only see “.5” assets. If the “x” integer is subject to more granular divisions, the security team can create more finally specialized asset groups. For example .51 may correspond to file servers, and .52 may correspond to database servers.

Another approach to creating asset groups is categorizing them according to membership. For example, you can have an “Executive” asset group for senior company officers who see high-level business-sensitive reports about all the assets within your enterprise. You can have more technical asset groups for different members of your security team, who are responsible for remediating vulnerabilities on specific types of assets, such as databases, workstations, or Web servers.

The page for an asset group displays charts so you can track your risk or number of vulnerabilities in relation to the assets in that group.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/3c06404-s_nx_asset_group_risk_assets_time.jpg",
        "s_nx_asset_group_risk_assets_time.jpg",
        675,
        306,
        "#e2e4e5"
      ],
      "caption": "Asset Risk and Vulnerabilites Over Time"
    }
  ]
}
[/block]
The _Assets by Risk and Vulnerabilities_ chart to the right of the _Asset Risk and Vulnerabilites Over Time_ line graph appears as a scatter chart, unless you have 7,000 assets or more in the asset group. In that case, it appears as a bubble chart, and you can click on a bubble to see a scatter chart of a specific group of assets.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/e2eb366-s_nx_asset_group_assets_by_risk_and_vulns.PNG",
        "s_nx_asset_group_assets_by_risk_and_vulns.PNG",
        556,
        308,
        "#edb90b"
      ],
      "caption": "Assets by Risk and Vulnerabilities"
    }
  ]
}
[/block]
On the scatter chart, each dot represents an asset. Hover over the dot to see information about the asset. Click it to go to the page for that asset.

##Comparing dynamic and static asset groups

One way to think of an asset group is as a snapshot of your environment.

This snapshot provides important information about your assets and the security issues affecting them:

* their network location
* the operating systems running on them
* the number of vulnerabilities discovered on them
* whether exploits exist for any of the vulnerabilities
* their risk scores

With InsightVM, you can create two different kinds of “snapshots.” The dynamic asset group is a snapshot that potentially changes with every scan; and the static asset group is an unchanging snapshot. Each type of asset group can be useful depending on your needs.

###Using dynamic asset groups

A dynamic asset group contains scanned assets that meet a specific set of search criteria. You define these criteria with asset search filters, such as IP address range or hosted operating systems. The list of assets in a dynamic group is subject to change with every scan. In this regard, a dynamic asset group differs from a static asset group. See [How are sites different from asset groups?](doc:what-is-a-site#section-how-are-sites-different-from-asset-groups). Assets that no longer meet the group’s Asset Filter criteria after a scan will be removed from the list. Newly discovered assets that meet the criteria will be added to the list.

Note that the list does not change immediately, but after the application completes a scan and integrates the new asset information in the database.

An ever-evolving snapshot of your environment, a dynamic asset group allows you to track changes to your live asset inventory and security posture at a quick glance, and to create reports based on the most current data. For example, you can create a dynamic asset group of assets with a vulnerability that was included in a Patch Tuesday bulletin. Then, after applying the patch for the vulnerability, you can scan the dynamic asset group to determine if any assets still have this vulnerability. If the patch application was successful, the group theoretically should not include any assets.

You can create dynamic asset groups using the filtered asset search. See [Performing filtered asset searches](doc:performing-filtered-asset-searches).

You grant user access to dynamic asset groups through the _User Configuration_ panel.

A user with access to a dynamic asset group will have access to newly discovered assets that meet group criteria regardless of whether or not those assets belong to a site to which the user does not have access. For example, you have created a dynamic asset group of Windows XP workstations. You grant two users, Joe and Beth, access to this dynamic asset group. You scan a site to which Beth has access and Joe does not. The scan discovers 50 new Windows XP workstations. Joe and Beth will both be able to see the 50 new Windows XP workstations in the dynamic asset group list and include them in reports, even though Joe does not have access to the site that contains these same assets. When managing user access to dynamic asset groups, you need to assess how these groups will affect site permissions. To ensure that a dynamic asset group does not include any assets from a given site, use the site filter. See [Locating assets by sites](doc:locating-assets).
[block:callout]
{
  "type": "info",
  "body": "Dynamic Asset Groups do not gather retroactive or historical data. In order to report on historical data at the asset level, add assets into the report scope as a list of assets (i.e. using Static Asset Group)."
}
[/block]
###Using static asset groups

A static asset group contains assets that meet a set of criteria that you define according to your organization’s needs. Unlike with a dynamic asset group, the list of assets in a static group does not change unless you alter it manually.

Static asset groups provide useful time-frozen views of your environment that you can use for reference or comparison. For example, you may find it useful to create a static asset group of Windows servers and create a report to capture all of their vulnerabilities. Then, after applying patches and running a scan for patch verification, you can create a baseline report to compare vulnerabilities on those same assets before and after the scan.

You can create static asset groups through any of three options:

* using the _Group Configuration_ panel; see [Configuring a static asset group by manually selecting assets](doc:working-with-asset-groups#section-configuring-a-static-asset-group-by-manually-selecting-assets) 
* using the filtered asset search; see [Performing filtered asset searches](doc:performing-filtered-asset-searches)
* copying and modifying an existing asset group; see [Creating a dynamic or static asset group by copying an existing one](doc:working-with-asset-groups#section-creating-a-dynamic-or-static-asset-group-by-copying-an-existing-one) 

##Configuring a static asset group by manually selecting assets
[block:callout]
{
  "type": "warning",
  "body": "Only Global Administrators can create asset groups."
}
[/block]
Manually selecting assets is one of three ways to create a static asset group. This manual method is ideal for environments that have small numbers of assets. For an approach that is ideal for large numbers of assets, see [Creating a dynamic or static asset group from asset searches](doc:creating-a-dynamic-or-static-asset-group-from-asset-searches).

Start a static asset group configuration:

1. Go to the _Assets :: Asset Groups_ page by one of the following routes:
Click the **Assets** icon to go to the _Assets_ page, and then click **view** next to _Groups_.
OR
Click the **Create** tab at the top of the page and then select _Asset Group_ from the drop-down list.
OR
Click the **Administration** icon to go to the Administration page, and then click **manage** next to _Groups_.
2. Click **New Static Asset Group** to create a new static asset group.
3. Click **Edit** to change any group listed with a static asset group icon.
The _Asset Group Configuration_ panel appears.
[block:callout]
{
  "type": "info",
  "body": "You can only create an asset group after running an initial scan of assets that you wish to include in that group."
}
[/block]
4. Click **New Static Asset Group**.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/c2347a9-s_static_asset_group_new.jpg",
        "s_static_asset_group_new.jpg",
        1436,
        460,
        "#f3f6f6"
      ],
      "caption": "Creating a new static asset group"
    }
  ]
}
[/block]
OR

Click **Create** below _Asset Groups_ on the _Administration_ page.

The console displays the _General_ page of the _Asset Group Configuration_ panel.

5. Type a group name and description in the appropriate fields.
6. If you want to, add business context tags to the group. Any tag you add to a group will apply to all of the member assets. For more information and instructions, see [Applying RealContext with tags](doc:applying-realcontext-with-tags).

Adding assets to the static asset group:

1. Go to the _Assets_ page of the _Asset Group Configuration_ panel.
The console displays a page with search filters.
2. Use any of these filters to find assets that meet certain criteria, then click **Display matching assets** to run the search.
For example, you can select all of the assets within an IP address range that run on a particular operating system.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/2d667da-s_static_asset_group_conifg_asset_search.jpg",
        "s_static_asset_group_conifg_asset_search.jpg",
        1535,
        224,
        "#e3e6e7"
      ],
      "caption": "Selecting assets for a static asset group"
    }
  ]
}
[/block]
OR

3. Click **Display all assets**, which is convenient if your database contains a small number of assets.
[block:callout]
{
  "type": "info",
  "body": "There may be a delay if the search returns a very large number of assets."
}
[/block]
4. Select the assets you wish to add to the asset group. To include all assets, select the check box in the header row.
5. Click **Save**.
The assets appear on the _Assets_ page.

When you use this asset selection feature to create a new asset group, you will not see any assets displayed. When you use this asset selection feature to edit an existing report, you will see the list of assets that you selected when you created, or most recently edited, the report.

6. Click **Save** to save the new asset group information.

You can repeat the asset search to include multiple sets of search results in an asset group. You will need to save a set of results before proceeding to the next results. If you do not save a set of selected search results, the next search will clear that set.

##Creating a dynamic or static asset group by copying an existing one

You can create a new dynamic or static group by copying an existing one. This method is useful when you want to create an asset group that is similar to an existing one, but with some differences.

To copy an asset group:

1. From the _Home_ page, in the _Asset Groups_ listing, select the **Copy** icon for the asset group you want to copy.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/174bbc6-s_nx_copy_asset_group_from_home.jpg",
        "s_nx_copy_asset_group_from_home.jpg",
        1440,
        456,
        "#f1f5f6"
      ]
    }
  ]
}
[/block]
OR

From the asset group details, select **Copy Asset Group**.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/1a5f064-s_nx_copy_asset_group_from_details.jpg",
        "s_nx_copy_asset_group_from_details.jpg",
        1435,
        386,
        "#e5eaea"
      ],
      "caption": "Copying an asset group from the asset group details page"
    }
  ]
}
[/block]
2. The asset group configuration page appears. Make the changes to the settings and rename the asset group appropriately.
[block:callout]
{
  "type": "info",
  "body": "By default, _Copy_ will be appended to the original name. Additional copies of the original group will have a number appended (for example, _Copy 2_ and so on)."
}
[/block]
3. Click **Save**. The new asset group will not be created until you save