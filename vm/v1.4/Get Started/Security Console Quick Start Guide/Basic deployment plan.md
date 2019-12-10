---
title: "Basic deployment plan"
excerpt: ""
---
Proper resource allocation is a critical step towards maximizing the value and effectiveness of your deployment. With all deployments, big or small, it is important to have a plan in place so you can properly scale your resources according to your environment size and network topology.

This guide is intended for initial deployments, so this plan will make use of the local Scan Engine included with your Security Console installation. 

Your basic deployment will provide for the following:

* Scanning of up to a maximum of 1000 assets on your local network
* Adequate storage for scan data, reports, and database backups
[block:callout]
{
  "type": "info",
  "title": "Enterprise and production-level deployments",
  "body": "While the local Scan Engine is sufficient for trial purposes, it is not recommended that you rely on the local Scan Engine alone for production deployments.\n\nIf you’re looking for production deployment guidelines beyond the scope of this article, the following resources are available:\n\n* [Planning for Capacity Requirements](doc:planning-for-capacity-requirements)\n* [Configuring maximum performance in an enterprise environment](doc:configuring-maximum-performance-in-an-enterprise-environment)\n* [Distributed Scan Engines](doc:configuring-distributed-scan-engines)"
}
[/block]
# Components

Your InsightVM installation has the following components:

  * **Security Console** - This is the component you’ll use to create sites, run scans, generate reports, and much more.  The Security Console is accessed via a web-based user interface through any of our supported browsers.
  * **PostgreSQL database** - The embedded PostgreSQL databases stores all the asset scan data and is used for generating reports.
  * **Local Scan Engine** - Scan Engines are responsible for performing scan jobs on your assets.  Your installation includes a local Scan Engine that you can use for trial purposes like this one.  Note that Scan Engines only store scan data temporarily before sending it back to the  Security Console for integration and long-term storage.

# Host requirements

It is important to choose the right location to host the Security Console both in terms of accessibility to the assets you want to scan and network resource availability.

Ideally, locate your host machine in your network where there is high bandwidth and low latency.  Both can impact scan efficiency.
[block:callout]
{
  "type": "info",
  "title": "Take note of these guidelines!",
  "body": "While general [system requirements](doc:requirements) will be covered later, keep the following recommendations in mind when you ultimately decide where to install the Security Console."
}
[/block]
## Memory

The integration of scan data from Scan Engines can be memory-intensive depending on how many assets are being scanned at once.

For this basic deployment, we recommend that your host machine have a minimum of **16GB** of RAM.

## Disk space

Proper disk space allocation for the database is essential.  The biggest storage impact on your host machine will come from scans, reports, and database backups.  Scan data alone can have varying levels of storage impact depending on your configuration, including scan frequency and whether or not you are authenticating to the target assets.
[block:callout]
{
  "type": "warning",
  "title": "NOTE",
  "body": "Authenticated scans require roughly ten times the disk space of unauthenticated scans."
}
[/block]
For this basic deployment, your host machine must have a minimum of **100GB** of free storage space in order to accommodate your future scan data and reports.  At least **1TB** of free storage space is recommended for small-scale deployments.

Consider this example deployment situation:

Scanning 1000 assets on a monthly basis with authentication, generating a single report, and storing the data for one year will take **76GB** of storage.

### Don’t underestimate your storage needs

When preparing your deployment plan, it is important to be mindful of how your network and security needs could change over time.  Storage allocation should take additional assets, increased frequency, and potential backups (to name a few) into account so that you’re prepared when those events take place.

If you find yourself making a decision between two numbers, go for the larger one.
[block:callout]
{
  "type": "success",
  "title": "You’re ready to deploy!",
  "body": "Now that you have your deployment plan, let’s briefly go over what the Security Console can do for you."
}
[/block]