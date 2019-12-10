---
title: "Scan Engine Pools"
excerpt: ""
---
[block:callout]
{
  "type": "warning",
  "title": "NOTE",
  "body": "You must be licensed to use Scan Engine pools to create and apply them in your site configurations. Contact your Customer Success Manager to learn more about gaining access to Scan Engine pools."
}
[/block]
Properly licensed InsightVM customers can take advantage of a Scan Engine pooling capability that balances the load of a single scan across several of your distributed Scan Engines.  Scan Engine pools are useful when you need to optimize scans for significantly large sites.

This article explains how to create and configure Scan Engine pools.

# Requirements

Scan Engine pools have the following requirements:

* Your product license must support Scan Engine pooling.
* Scan Engine pools can only be composed of your distributed Scan Engines.  The following engine types are not usable in Scan Engine pools:
 * Local Scan Engine
 * Rapid7 Hosted Scan Engine
 * Pre-Authorized AWS Scan Engine
* You can add any distributed Scan Engine to a pool, regardless of its connectivity status.
However, Scan Engines that are not currently “Active” will not contribute to scan load balancing.  Verify that all Scan Engines in your pool are “Active” to ensure maximum scanning optimization.

# Create a Scan Engine Pool

You can create a Scan Engine pool within a site configuration or through the **Administration** page.

## Create a Scan Engine Pool in a Site Configuration

To create a new Scan Engine pool in a site configuration:

1. In a new or existing site configuration, click the **Engines** tab.
 * You can create a new site by expanding the **Create** dropdown next to the left navigation menu, or access an existing site by clicking its edit icon in the “Sites” table of the **Home** page.
2. Click the **Create Engine Pool** subtab.
3. Name your Scan Engine pool.
4. In the “Scan Engines” table, select each available Scan Engine that you want to include in the pool.
5. Click **Save** when finished.

Your new Scan Engine pool is now available for use in your site configuration.  Return to the **Select Scan Engine** subtab to select your new pool in the “Scan Engines & Pools” table.

## Create a Scan Engine Pool through Administration

To create a new Scan Engine pool through the **Administration** page:

1. Browse to and click on the **Administration** tab in your left navigation menu.
2. In the “Scan Options” section, click **manage** next to “Engines”.
3. In the “Scan Engine Pools” section, click **New Engine Pool**.
4. Name your Scan Engine pool.
5. In the “Scan Engines” table, select each available Scan Engine that you want to include in the pool.
6. Click **Save** when finished.

Your new Scan Engine pool now appears in the “Scan Engine Pools” table of the Scan Engine management page.