---
title: "Live Licensing"
excerpt: ""
---
The application will only store assessment data for your assets up to the licensed maximum.  For the benefit of awareness, the Security Console tracks license usage information and will display alerts when your assessed asset count nears the currently allotted asset limit.  Assets assessed by agents are also factored into this total.  This feature will allow you to plan ahead when it comes to determining what license requirements are suitable for your organization.

Your organization’s license determines the number of assets that can be assessed for vulnerabilities or policy compliance for storage in the console.  Your license **does not** limit the number of assets that can be **discovered** on your network.

# Access to license usage data

Only global administrators can view the extent of an organization’s license limit in full detail.  Non-admin user access is limited to overall and discovered asset counts, as well as license limit banner notifications.
[block:callout]
{
  "type": "warning",
  "title": "NOTE",
  "body": "The permissions of the current user role will determine overall and discovered asset count visibility.  A user with access to only a subset of their organization’s assets will be limited to the totals of that subset."
}
[/block]

[block:parameters]
{
  "data": {
    "h-1": "Global administrator",
    "h-2": "Non-admin user",
    "0-0": "_Overall asset count_",
    "1-0": "_Discovered asset count_",
    "2-0": "_License usage bar_",
    "3-0": "_License details_",
    "4-0": "_90% usage notification_",
    "5-0": "_100% usage notification_",
    "6-0": "_110% usage notification_",
    "0-1": "Viewable",
    "0-2": "Viewable",
    "1-1": "Viewable",
    "1-2": "Viewable",
    "2-1": "Viewable",
    "3-1": "Viewable",
    "4-1": "Viewable",
    "5-1": "Viewable",
    "6-1": "Viewable",
    "4-2": "Viewable",
    "5-2": "Viewable",
    "6-2": "Viewable",
    "2-2": "Unavailable",
    "3-2": "Unavailable"
  },
  "cols": 3,
  "rows": 7
}
[/block]
# What counts as an asset?

The application is licensed for _unique assessed assets_.  An asset is considered _assessed_ when its vulnerability or policy assessment data is stored in the Security Console.  The application uses correlation heuristics to determine whether an asset is unique based on the following factors:
* Universally Unique Identifier (UUID)
* Media Access Control (MAC) address(es)
* Hostname(s)
* IP address(es)

Assets identified and successfully correlated are only counted **once**.  A single asset that has been assessed by both an agent and a credentialed scan will not be double-counted as a result.
[block:callout]
{
  "type": "info",
  "body": "To correlate agent assets with unauthenticated scans, contact Rapid7 Support."
}
[/block]
## Assets in AWS and Microsoft Azure

Each instance or virtual machine within these environments counts as **one** asset until it is terminated.  Rapid7’s unique cloud connections with AWS and Azure facilitate the immediate removal of these terminated assets from your license count as soon as they are decommissioned.  Discovery connections for these environments automatically know when an asset has been decommissioned.  As a result, stale assets will not count toward your license limit as you continue to scan your network.

## Containers

For containers, each host counts as **one** asset.  A single host running multiple containers will still count as **one** asset.  Your license count will not be affected by assessments run on a per-image basis, or by data used for this assessment.

# Viewing your asset count
[block:callout]
{
  "type": "info",
  "title": "REMINDER",
  "body": "Data concerning an organization’s license limit is only available to global administrators."
}
[/block]
## Assets page

Click the **Assets** tab in the Security Console.  Your organization’s license usage will be shown in the form of a progress bar located below the overall asset count.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/7f5a9d7-Assets_page_license_usage.png",
        "Assets_page_license_usage.png",
        1918,
        671,
        "#e9cecc"
      ]
    }
  ]
}
[/block]
## Administration page

Click the **Administration** tab in the Security Console.  In the “Global and Console Settings” frame, click **Administer**.  The “Security Console Configuration” screen will be shown.

Click the **Licensing** tab on this page to view your organization’s license details.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/3a59cd1-Administration_page_license_usage.png",
        "Administration_page_license_usage.png",
        1917,
        752,
        "#2d353f"
      ]
    }
  ]
}
[/block]
# License usage notifications
[block:callout]
{
  "type": "info",
  "title": "NOTE",
  "body": "These notifications will appear for both admin and non-admin users."
}
[/block]
## 90% usage

The Security Console will display an orange notification when licensed assets exceed 90% of the allotted maximum.

## 100% usage

The Security Console will display a red notification when licensed assets exceed 100% of the allotted maximum.  In the event that your licensed assets exceed the license limit, you will be allowed _temporary_ flexibility to scan above your license limit in order to remain secure.

## 110% usage

The Security Console will display a red notification banner when licensed assets exceed 110% of the allotted maximum.
[block:callout]
{
  "type": "warning",
  "body": "This banner **cannot be dismissed**.  It will stop appearing only after your licensed asset count is brought within your license limit."
}
[/block]
If no action is taken toward increasing your license at this stage, further scans may trigger **automatic enforcement**.

## Automatic enforcement

Automatic enforcement may take place if you continue to scan assets after exceeding 110% of your allotted maximum.  Should automatic enforcement occur, new scan data **will not be retained**.  In order to avoid the potential loss of new scan data, clean up duplicate or stale assets in your Security Console or contact your Rapid7 CSM to increase your license.

Automatic enforcement will deactivate after your asset count is brought within your licensed maximum (this can be done by removing assets or increasing the limit of your license).  New scan data will be saved as usual once this has been resolved.
[block:callout]
{
  "type": "danger",
  "body": "Scan data that was not saved during automatic enforcement **will not** be available after your asset count is brought within your license limit.  Scan data that is collected during that time is not recoverable."
}
[/block]