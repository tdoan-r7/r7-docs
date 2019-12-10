---
title: "Deleting sites"
excerpt: ""
---
To manage disk space and ensure data integrity of scan results, administrators can delete unused sites. By removing unused sites, inactive results do not distort scan results and risk posture in reports. 
[block:callout]
{
  "type": "warning",
  "title": "NOTE",
  "body": "Assets must belong to at least one site in order to appear in reports. Deleting a unique asset from its site or deleting the site entirely will effectively delete the asset data from the database.\n\nSee the [Site-level controls](doc:linking-assets-across-sites#section-site-level-controls) for more information."
}
[/block]
In addition, unused sites count against your license and can prevent the addition of new sites. Regular site maintenance helps to manage your license so that you can create new sites.
[block:callout]
{
  "type": "info",
  "body": "To delete a site, you must have access to the site and have _Manage Sites_ permission. The **Delete** button is hidden if you do not have permission."
}
[/block]
To delete a site:

1. Access the _Sites_ panel:
   * Click the **Assets** icon and then click on the number of sites at the top.
[block:callout]
{
  "type": "info",
  "body": "You cannot delete a site that is being scanned. You receive this message “Scans are still in progress. If you want to delete this site, stop all scans first”."
}
[/block]
   The _Sites_ panel displays the sites that you can access based on your permissions.

2. Click the ![Alt](https://files.readme.io/1b18ce6-i_Delete.jpg) **Delete** button to remove a site.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/4356df2-s_nx_delete_site_from_listing.jpg",
        "s_nx_delete_site_from_listing.jpg",
        2201,
        837,
        "#eff5f6"
      ],
      "caption": "Deleting a site from the Sites panel"
    }
  ]
}
[/block]
All reports, scan templates, and scan engines are disassociated. All assets in the deleted site will also be deleted unless they are a member of at least one other site.  Scan results are deleted. If the delete process is interrupted, then partially deleted sites will be automatically cleared.
[block:callout]
{
  "type": "warning",
  "title": "NOTE",
  "body": "The Rapid7 Insight Agent site **cannot** be deleted."
}
[/block]