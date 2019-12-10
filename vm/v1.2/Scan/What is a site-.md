---
title: "What is a site?"
excerpt: ""
---
A site is a collection of assets that are targeted for a scan. You must create a site in order to run a scan of your environment and find vulnerabilities.

A site consists of:

* target assets (optional)
* a scan template
* one or more Scan Engines
* other scan-related settings such as schedules or alerts

## Different ways to add assets to a site

You can specify target assets in several ways:

* by individual name, address, or range
* by asset group name
* through a dynamic discovery connection

Consider the fluidity of your scan target environment when deciding on your preferred method.
[block:callout]
{
  "type": "info",
  "body": "Target assets are **not required** when saving a site.  If necessary, you can determine how assets are added to your site by clicking on the **Assets** tab of the Site Configuration.",
  "title": "TIP"
}
[/block]
Specifying individual assets or ranges is a good choice for situations where the addresses of your assets are likely to remain stable.

Specifying asset groups allows you to scan based on logical groupings that you have previously created. In the case of scanning dynamic asset groups, you can scan based on whether assets meet certain criteria. For example, you can scan all assets whose operating system is Ubuntu. To learn more about asset groups, see [Working with asset groups](doc:working-with-asset-groups).

Adding assets through connection is ideal for a highly fluid target environment, such as a deployment of virtualized assets. It is not unusual for virtual machines to undergo continual changes, such as having different operating systems installed, being supported by different resource pools, or being turned on and off. Because asset membership in such a site is based on continual discovery of virtual assets, the asset list changes as the target environment changes, as reflected in the results of each scan.

You can change asset membership in a site that populates assets through a connection by changing the discovery connection or the criteria filters that determine which assets are discovered. See [Managing dynamic discovery of assets](doc:managing-dynamic-discovery-of-assets).

## How are sites different from asset groups?

Asset groups provide different ways for members of your organization to grant access to, view, scan, and report on asset information. You can create asset groups that contain assets across multiple sites. See [Working with asset groups](doc:working-with-asset-groups).

## Rapid7 Insight Agents Site

The Rapid7 Insight Agents Site is a special site that automatically contains all assets that have Rapid7 Insight Agents installed and running. This site [cannot be deleted or edited](doc:deleting-sites).