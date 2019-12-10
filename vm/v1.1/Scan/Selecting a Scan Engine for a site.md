---
title: "Selecting a Scan Engine for a site"
excerpt: ""
---
A Scan Engine is one of the components that a site must have. It discovers assets during scans and checks them for vulnerabilities or policy compliance. Scan Engines are controlled by the Security Console, which integrates their data into the database for display and reporting.

If you have deployed distributed Scan Engines or engine pools,  or you are using InsightVM hosted Scan Engines, you will have a choice of engines or pools for this site. Otherwise, your only option is the local Scan Engine that was installed with the Security Console. It is also the default selection.

For more information about Scan Engine options:

* [Configuring distributed Scan Engines](doc:configuring-distributed-scan-engines) 
* [Working with Scan Engine pools](doc:working-with-scan-engine-pools) 

To change the Scan Engine selection:

 * If you are adding an engine while configuring a new site, click the **Create site** button on the _Home_ page.
 * If you are adding a new engine option to an existing site, click that site's **Edit** icon in the _Sites_ table on the _Home_ page.
1. Click the **Engines** tab of the _Site Configuration_.
2. If you are scanning an asset group, select the desired option for scanning assets. See [Determining how to scan each asset when scanning asset groups](doc:selecting-a-scan-engine-for-a-site#section-determining-how-to-scan-each-asset-when-scanning-asset-groups).
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/e74e15d-s_nx_select_scan_engine.jpg",
        "s_nx_select_scan_engine.jpg",
        1822,
        841,
        "#212b3b"
      ],
      "caption": "Selecting a Scan Engine or pool"
    }
  ]
}
[/block]
**Tip:**  If you have many engines or pools you can make it easier to find the one you want by entering part of its name in the **Filter** text box.

> 3. Configure other site settings as desired.
> 4. Click **Save** or **Save & Scan**, depending on your preference.

###Determining how to scan each asset when scanning asset groups

When scanning asset groups, you have the option to use the same Scan Engine or Scan Engine Pool to scan all the assets in a site, or to scan each asset with the Scan Engine that was previously used. The best choice depends on your network configuration: for example, if your assets are geographically dispersed, you may want to use the most recent Scan Engine for each asset so they will be more likely to be scanned by a Scan Engine in the same location.

To determine which Scan Engine to use for each asset:

1. In the _Site Configuration_, go to the **Engines** tab.
2. If you want to scan all the assets with the same Scan Engine or Scan Engine Pool, select _Engine_ selected below.

OR

Select _Engine most recently used for that asset_. This may result in different assets being scanned by different Scan Engines.
  **Note:** Although this option appears in any site configuration, it only applies when scanning asset groups.

3. Select a Scan Engine or Scan Engine Pool from the list.
**Note:**  Even if you chose to scan with the engine most recently used for this asset, this setting will still be used for any asset that has never been scanned before. Therefore, you should make a choice no matter which option you chose above.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/2d9256f-s_nx_multi-engine_config.jpg",
        "s_nx_multi-engine_config.jpg",
        1822,
        841,
        "#212b3b"
      ],
      "caption": "Choosing to scan with the most recently used engine for each asset"
    }
  ]
}
[/block]
If you select the option to scan with the engine most recently used for that asset, the _Scans_ page may display multiple Scan Engines in the _Current Scans_ table and the _Past Scans_ table.

####Viewing Scan Engine Status

On the page for a scan, you can view the _Scan Engines Status_ table. To learn more, see [Running a manual scan](doc:running-a-manual-scan).