---
title: "Sites and assets frequently asked questions"
excerpt: ""
---
This page concerns setting up sites and asset groups.

## I am seeing the error message "Exceeded licensed number of devices" when I try to start a scan.

Review how many IP addresses are listed in _all_ of your sites. InsightVM counts all addresses, not just those for hosts found to be "live," against the IP address limit in your license. This is especially important to remember when you define IP address ranges as scan targets. To reduce the number of counted assets, remove all data related to old assets wherever that data appears in the Web interface. To ensure that you are removing all references to that asset, run a search on the IP address or host name.

## How many IP addresses I can include in a site?

The total number of IP addresses you can scan depends on the type of InsightVM License you purchased. If you own a license based on a fixed number of IP addresses, keep in mind that this reflects the entire number of IP addresses in your environment. It does not reflect how many IP addresses are for live assets only. So, if you create a site with a large IP address range, intending to only scan some of the IPs within that range, you may see an error message indicating that you cannot scan that range or that you have exceeded the scope of your license. If this occurs, break down your site into multiple sites with smaller IP address ranges. You may also want to consider purchasing a discovery license, which does not impose this limit.

## What's the difference between a site and an asset group?

A site is a physical group of assets assembled for a scan by a specific, dedicated scan engine. The grouping principle may be something meaningful to you, such as a common geographic location or a range of IP addresses. Or, you may organize a site for a specific type of scan. An asset group is a logical collection of assets to which specified users have access in order to view data about these assets. These users are typically in charge of monitoring these assets and reporting or remediating any vulnerabilties that InsightVM discovers on them.

## How do I know if the credentials that I specified during site configuration are working during my scan?

A: Go to the page for any asset listed in the InsightVM Security Console Web interface. See the _Device Fingerprints_ pane. Each item in the table is displayed with a certainty ranking, which indicates the level of certainty with which InsightVM fingerprinted that item. If the certainty level is 1.0, then an operating-system-level credential was successfully applied. If you do see the _Device Fingerprints_ pane, you can make it appear by clicking the **Customize Dashboard** link at the top of any page of the interface.

## Why aren't the alerts I set up during site creation working?

If you are not receiving scan-related alerts after setting them up during site creation, go to the Alerting page of the configuration wizard and verify that any alerts you created are listed. If they are not, then you didn't save them them after creating them. You have to save save a new alert after creating it in the _New Alert_ dialog box. Then, you have to save the site configuration change, by clicking the **Save** button on any page of the wizard.

Also, make sure that when you create an alert, you select the appropriate notification method that you wanted.