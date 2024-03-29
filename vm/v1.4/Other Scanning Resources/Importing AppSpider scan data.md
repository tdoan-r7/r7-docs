---
title: "Importing AppSpider scan data"
excerpt: ""
---
If you use Rapid7 AppSpider to scan your Web applications, you can import AppSpider data with InsightVM scan data and reports. This allows you to view security information about your Web assets side-by-side with your other network assets for more comprehensive assessment and prioritization.

The process involves importing an AppSpider-generated file of scan results, _VulnerabilitiesSummary.xml_, into a InsightVM site. Afterward, you view and report on that data as you would with data from a InsightVM scan.

If you import the XML file on a recurring basis, you will build a cumulative scan history in InsightVM about the referenced assets. This allows you to track trends related to those assets as you would with any assets scanned in InsightVM.
[block:callout]
{
  "type": "info",
  "body": "This import process works with AppSpider versions 6.4.122 or later."
}
[/block]
To import AppSpider data, take the following steps:

1. Create a site if you want a dedicated site to include AppSpider data exclusively. See [Creating and editing sites](doc:creating-and-editing-sites).
Since you are creating the site to contain AppSpider scan results, you do not need to set up scan credentials. You will need to include at least one asset, which is a requirement for creating a site. However, it will not be necessary to scan this asset.
If you want to include AppSpider results in an existing site with assets scanned by InsightVM, skip this step.
2. Download the VulnerabilitiesSummary.xml file, generated by AppSpider, to the computer that you are using to access the InsightVM Web interface.
3. In the _Sites_ table, select the name of the site that you want to use for AppSpider.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/512c180-s_nx_appspider_click_site.png",
        "s_nx_appspider_click_site.png",
        2036,
        826,
        "#eff5f6"
      ],
      "caption": "Selecting the site for importing AppSpider data"
    }
  ]
}
[/block]
4. In the _Site Summary_ table for that site, click the hypertext link labeled **Import AppSpider Assessment**.
5. Click the button that appears, labeled **Choose File**. Find the VulnerabilitiesSummary.xml on your local computer and click **Open** in Windows Explorer.
The file name appears, followed by an **Import** button.
6. Click Import.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/e31eaca-s_nx_appspider_import.png",
        "s_nx_appspider_import.png",
        2002,
        918,
        "#ecf2f2"
      ],
      "caption": "Importing the VulnerabilitiesSummary.xml file"
    }
  ]
}
[/block]
The imported data appears in the _Assets_ table on your site page. You can work with imported assets as you would with any scanned by InsightVM: View detailed information about them, tag them, and include them in asset groups, and reports.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/b92f7ed-s_nx_appspider_imported_asset.png",
        "s_nx_appspider_imported_asset.png",
        1994,
        1478,
        "#ecf1f2"
      ],
      "caption": "An asset scanned by AppSpider"
    }
  ]
}
[/block]

[block:callout]
{
  "type": "info",
  "body": "Although you can include imported assets in dynamic assets groups, the data about these imported assets is not subject to change with InsightVM scans. Data about imported assets only changes with subsequent imports of AppSpider data."
}
[/block]