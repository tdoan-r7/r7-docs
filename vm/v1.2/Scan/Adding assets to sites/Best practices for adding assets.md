---
title: "Best practices for adding assets"
excerpt: ""
---
Consider several things when selecting assets for a site. Asset selection can have an impact on the quality of scans and reports.

## Choosing a grouping strategy for creating a site with manually selected assets

There are many ways to divide network assets into sites. The most obvious grouping principle is physical location. A company with assets in Philadelphia, Honolulu, Osaka, and Madrid could have four sites, one for each of these cities. Grouping assets in this manner makes sense, especially if each physical location has its own dedicated Scan Engine. Remember, each site is assigned to a specific Scan Engine.

With that in mind, you may find it practical simply to base site creation on Scan Engine placement. Scan engines are most effective when they are deployed in areas of separation and connection within your network. So, for example, you could create sites based on subnetworks.

Other useful grouping principles include common asset configurations or functions. You may want have separate sites for all of your workstations and your database servers. Or you may wish to group all your Windows 2008 Servers in one site and all your Debian machines in another. Similar assets are likely to have similar vulnerabilities, or they are likely to present identical logon challenges.

If you are performing scans to test assets for compliance with a particular standard or policy, such as Payment Card Industry (PCI) or Federal Desktop Core Configuration (FDCC), you may find it helpful to create a site of assets to be audited for compliance. This method focuses scanning resources on compliance efforts. It also makes it easier to track scan results for these assets and include them in reports and asset groups.

## Being flexible with site membership

When selecting assets for sites, flexibility can be advantageous. You can include an asset in more than one site. For example, you may wish to run a monthly scan of all your Windows Vista workstations with the Microsoft hotfix scan template to verify that these assets have the proper Microsoft patches installed. But if your organization is a medical office, some of the assets in your “Windows Vista” site might also be part of your “Patient support” site, which you may have to scan annually with the HIPAA compliance template.

You can also define an asset group within a site, in order to scan based on a specific logical grouping.

## Grouping options for Example, Inc.

Your grouping scheme can be fairly broad or more granular.

The following table shows a serviceable high-level site grouping for Example, Inc. The scheme provides a very basic guide for scanning and makes use of the entire network infrastructure.

[block:parameters]
{
  "data": {
    "h-0": "Site name",
    "h-1": "Address Space",
    "h-2": "Number of Assets",
    "h-3": "Component",
    "0-1": "10.1.0.0/22\n10.1.0.0/23\n10.1.0.0/24",
    "0-0": "New York",
    "0-2": "360",
    "0-3": "Security Console",
    "1-0": "New York DMZ",
    "1-1": "172.16.0.0/22",
    "1-2": "30",
    "1-3": "Scan Engine 1",
    "2-0": "Madrid",
    "2-1": "10.2.0.0/22\n10.2.10.0/23\n10.2.20.0/24",
    "2-2": "233",
    "2-3": "Scan Engine 1",
    "3-0": "Madrid DMZ",
    "3-1": "172.16.10.0/24",
    "3-2": "15",
    "3-3": "Scan Engine 1"
  },
  "cols": 4,
  "rows": 4
}
[/block]
A potential problem with this grouping is that managing scan data in large chunks is time consuming and difficult. A better configuration groups the elements into smaller scan sites for more refined reporting and asset ownership.

In the following configuration, Example, Inc., introduces asset function as a grouping principle. The New York site from the preceding configuration is subdivided into Sales, IT, Administration, Printers, and DMZ. Madrid is subdivided by these criteria as well. Adding more sites reduces scan time and promotes more focused reporting.
[block:parameters]
{
  "data": {
    "h-0": "Site name",
    "h-1": "Address space",
    "h-2": "Number of assets",
    "h-3": "Component",
    "0-1": "10.1.0.0/22",
    "0-0": "New York Sales",
    "0-2": "254",
    "0-3": "Security Console",
    "1-0": "New York IT",
    "1-1": "10.1.10.0/24",
    "1-2": "25",
    "1-3": "Security Console",
    "2-0": "New York Administration",
    "2-1": "10.1.10.1/24",
    "2-2": "25",
    "2-3": "Security Console",
    "3-0": "New York Printers",
    "3-1": "10.1.20.0/24",
    "3-2": "56",
    "3-3": "Security Console",
    "4-1": "172.16.0.0/22",
    "4-0": "New York DMZ",
    "4-2": "30",
    "4-3": "Scan Engine 1",
    "5-0": "Madrid Sales",
    "5-1": "10.2.0.0/22",
    "5-2": "65",
    "5-3": "Scan Engine 2",
    "6-0": "Madrid Development",
    "6-1": "10.2.10.0/23",
    "6-2": "130",
    "6-3": "Scan Engine 2",
    "7-0": "Madrid Printers",
    "7-1": "10.2.20.0/24",
    "7-2": "35",
    "7-3": "Scan Engine 2",
    "8-0": "Madrid DMZ",
    "8-1": "172.16.10.0/24",
    "8-2": "15",
    "8-3": "Scan Engine 3"
  },
  "cols": 4,
  "rows": 9
}
[/block]
An optimal configuration, seen in the following table, incorporates the principal of physical separation. Scan times will be even shorter, and reporting will be even more focused.
[block:parameters]
{
  "data": {
    "h-0": "Site name",
    "h-1": "Address space",
    "h-2": "Number of assets",
    "0-3": "Security Console",
    "h-3": "Component",
    "0-0": "New York Sales 1st Floor",
    "0-1": "10.1.1.0/24",
    "0-2": "84",
    "1-0": "New York Sales 2nd Floor",
    "1-1": "10.1.2.0/24",
    "1-2": "85",
    "1-3": "Security Console",
    "2-0": "New York Sales 3rd Floor",
    "2-1": "10.1.3.0/24",
    "2-2": "85",
    "2-3": "Security Console",
    "3-0": "New York IT",
    "3-1": "10.1.10.0/25",
    "3-2": "25",
    "3-3": "Security Console",
    "4-0": "New York Administration",
    "4-1": "10.1.10.128/25",
    "4-2": "25",
    "4-3": "Security Console",
    "5-0": "New York Printers Building 1",
    "5-1": "10.1.20.0/25",
    "5-2": "28",
    "5-3": "Security Console",
    "6-0": "New York Printers Building 2",
    "6-1": "10.1.20.128/25",
    "6-2": "28",
    "6-3": "Security Console",
    "7-0": "New York DMZ",
    "7-1": "172.16.0.0/22",
    "7-2": "30",
    "7-3": "Scan Engine 1",
    "8-0": "Madrid Sales Office 1",
    "8-1": "10.2.1.0/24",
    "8-2": "31",
    "8-3": "Scan Engine 2",
    "9-0": "Madrid Sales Office 2",
    "9-1": "10.2.2.0/24",
    "9-2": "31",
    "9-3": "Scan Engine 2",
    "10-0": "Madrid Sales Office 3",
    "10-1": "10.2.3.0/24",
    "10-2": "33",
    "10-3": "Scan Engine 2",
    "11-0": "Madrid Development Floor 2",
    "11-1": "10.2.10.0/24",
    "11-2": "65",
    "11-3": "Scan Engine 2",
    "12-0": "Madrid Development Floor 3",
    "12-1": "10.2.11.0/24",
    "12-2": "65",
    "12-3": "Scan Engine 2",
    "13-0": "Madrid Printers Building 3",
    "13-1": "10.2.20.0/24",
    "13-2": "35",
    "13-3": "Scan Engine 2",
    "14-0": "Madrid DMZ",
    "14-1": "172.16.10.0/24",
    "14-2": "15",
    "14-3": "Scan Engine 3"
  },
  "cols": 4,
  "rows": 15
}
[/block]