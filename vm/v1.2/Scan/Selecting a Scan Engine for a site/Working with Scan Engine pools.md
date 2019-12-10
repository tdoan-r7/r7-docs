---
title: "Working with Scan Engine pools"
excerpt: ""
---
You can improve the speed of your scans for large numbers of assets in a single site by pooling your Scan Engines. With pooling, the work it takes to scan one large site is split across multiple engines to maximize pool utilization.
[block:callout]
{
  "type": "info",
  "body": "To verify that you are licensed for Scan Engine pooling, see [Finding out what features your license supports](doc:finding-out-what-features-your-license-supports)."
}
[/block]
###Creating Scan Engine pools

You can add a Scan Engine while you're configuring a site:

* If you are adding an engine pool while configuring a new site, click the **Create site** button on the _Home_ page.
* If you are adding a new engine pool to an existing site, click that site's **Edit** icon in the _Sites_ table on the Home page.
1. In the Site Configuration, click Engines.
2. Click **Create Engine Pool**.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/c1d0bdd-s_nx_scan_engine_pool_config.jpg",
        "s_nx_scan_engine_pool_config.jpg",
        1969,
        778,
        "#202b3a"
      ],
      "caption": "Creating a Scan Engine Pool"
    }
  ]
}
[/block]
3. Enter a unique name to help you remember the pool.
4. Select the engines you want to include in the pool.
5. Click **Save**. Your new pool will appear on the _Scan Engines & Pools_ table, which you can view by clicking the **Select Scan Engine** tab.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/02a264d-s_nx_select_scan_engine.jpg",
        "s_nx_select_scan_engine.jpg",
        1822,
        841,
        "#212b3b"
      ],
      "caption": "The Scan Engines & Pools table"
    }
  ]
}
[/block]
If you are a Global Administrator, you can also create pools using the **Administration** tab:

1. Click the **Administration** icon.
2. Select **Scan Engine Pools** under _Scan Options_.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/b50bf98-s_nx_admin_scan_engine_pools.jpg",
        "s_nx_admin_scan_engine_pools.jpg",
        1963,
        579,
        "#e9eaee"
      ],
      "caption": "Creating a pool outside of the Site Configuration,via the Administration tab"
    }
  ]
}
[/block]
The _Scan Engine Pool Configuration_ page displays all of the engines that you have available (hosted and local engines cannot be used and won't appear), the number of pools they are in, the number of sites associated, and their status.
[block:callout]
{
  "type": "warning",
  "body": "Only engines with an active status will be effective in your pool. If your engine appears with an unknown or pending authorization status it can be added to a pool, but will not contribute to load balancing. For instructions on how to pair Scan Engines with the Security Console, see [Configuring distributed Scan Engines](doc:configuring-distributed-scan-engines)."
}
[/block]
3. Enter a unique name to help you remember pool.
4. Select the engines you want to include in the pool.
5. Click **Save**. Your new pool will appear listed on the _Scan Engines_ page.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/721a8e1-s_nx_scan_engines_w_pools.jpg",
        "s_nx_scan_engines_w_pools.jpg",
        1927,
        1140,
        "#f1f4f4"
      ],
      "caption": "Scan Engine page with pools"
    }
  ]
}
[/block]

[block:callout]
{
  "type": "info",
  "body": "For additional information on optimal deployment settings for Scan Engine pooling, see the section titled _Deploying Scan Engine Pools_ in the administrator's guide."
}
[/block]
###Site optimization for pooling

You may already have the application configured to match single Scan Engines to individual sites. If you decide to start using pooling, you may not achieve optimal results by simply moving those engines into a pool.

For optimal results, you can make the following adjustments to your site configuration:

* Create a few larger sites with more assets rather than many small sites with fewer assets. Scan Engines allocate memory for each site which it is currently scanning. Having fewer sites prevents resource contention and ensures that more memory is available for each scan.
[block:callout]
{
  "type": "warning",
  "body": "If you do create a large site to replace your smaller ones, you will lose any data from pre-aggregated sites once you delete them."
}
[/block]
* Schedule scans to run successively rather than concurrently.
* If you are going to run overlapping scans, stagger their start times as much as possible. This will prevent queued scan tasks from causing delays.

**Tip:** You can make scans complete more quickly by increasing the scan threads used. If the engine is already at capacity utilization, you can add more RAM to increase the amount of threads. For more information on tuning scan performance see [Tuning performance with simultaneous scan tasks](doc:configuring-custom-scan-templates#section-tuning-performance-with-simultaneous-scan-tasks).