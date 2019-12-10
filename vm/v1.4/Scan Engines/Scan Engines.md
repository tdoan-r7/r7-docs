---
title: "Scan Engines"
excerpt: ""
---
Scan Engines are the workhorses of the scanning process and operate solely at the discretion of the Security Console.  They are responsible for discovering assets during a scan, checking them for vulnerabilities, and assessing their level of policy compliance (if your selected scan template is configured to do so).  Although Scan Engines serve as data collectors, they only temporarily store this data on their respective host machines.  Instead, the Security Console integrates Scan Engine data into the PostgreSQL database for you to see and report on.  This is why [Scan Engine host machine storage requirements](https://www.rapid7.com/products/insightvm/system-requirements/) are far lower than what the Security Console requires.

This article covers the following topics:

* [Scan Engine Types](doc:selecting-a-scan-engine-for-a-site#section-scan-engine-types)
* [Scan Engines in Site Configurations](doc:selecting-a-scan-engine-for-a-site#section-scan-engines-in-site-configurations)
* [Scan Engine Management](doc:selecting-a-scan-engine-for-a-site#section-scan-engine-management)

# Scan Engine Types

The Security Console can use multiple Scan Engines of various types that are designed to meet the configuration needs and scanning demands of your network.

## Local Scan Engine

All installations of the Security Console include a local Scan Engine so that you can start scanning immediately after your initial deployment.  While convenient, the local Scan Engine is best suited for very small scale deployments and trial experiences of the product.
[block:callout]
{
  "type": "warning",
  "title": "NOTE",
  "body": "Rapid7 does not recommend relying on the local Scan Engine in most cases.  If you intend to deploy a production scanning environment on any scale, [distributed Scan Engines](doc:selecting-a-scan-engine-for-a-site#section-distributed-scan-engine) are the way to go."
}
[/block]
## Distributed Scan Engine

Distributed Scan Engines are the most widely used engine type and are essential for any production scanning deployment.  Unlike the local variety, you install distributed Scan Engines on separate host machines from the console itself.  As a result, they can make use of more processing resources for scanning tasks and you can efficiently distribute them depending on the geographic spread of your assets.  You can also configure each distributed Scan Engine to communicate with the Security Console in a way that accommodates the presence of any firewalls on your network.
[block:callout]
{
  "type": "info",
  "title": "Planning a production deployment?  Use distributed Scan Engines!",
  "body": "See the following Help pages to learn more about Scan Engine communication configurations and for instructions on how to deploy:\n\n* [Scan Engine Communication Methods](doc:scan-engine-communication-methods)\n* [Distributed Scan Engines](doc:configuring-distributed-scan-engines)"
}
[/block]
## External Scanning Service

If you rather not deploy a Scan Engine on your own resources, Rapid7 offers access to Scan Engines provisioned through our External Scanning Service that are dedicated to your organization.  These external Scan Engines are also useful for determining what attackers can see on your external assets that are accessible to the internet.

If you are already licensed for the External Scanning Service, see the [External Scanning Service](doc:pairing-a-hosted-scan-engine) page for instructions on how to complete the pairing to your Security Console.

## Scan Engine Pool

If your product license supports engine pooling, you can group multiple distributed Scan Engines together in order to improve site scanning speed.

See the [Scan Engine Pools](doc:working-with-scan-engine-pools) page for instructions on creating and using Scan Engine pools in your environment.

## Pre-Authorized Scan Engine

Currently available specifically for those customers with Amazon Web Services (AWS) infrastructure, this Scan Engine type is pre-authorized for use by AWS and allows you to scan your EC2 instances for vulnerabilities as you would with your traditional assets.

See the [Pre-Authorized AWS Scan Engines](doc:insightvm-scan-engine-pre-authorized-ami) page for requirements and deployment instructions.

# Scan Engines in Site Configurations

All sites must specify at least one Scan Engine or engine pool for use during a scan.  You can view and select from all your individual and pooled Scan Engines on the **Engines** tab of any open site configuration.
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
## Asset Scanning Options

The “Scan each asset with” section above the Scan Engine list includes the following options:

* **Engine selected below** - This is the default method.  Enable this option to scan all targets in your site with your selected Scan Engine or engine pool.
* **Engine most recently used for that asset** - If your site configuration specifies one or more pre-configured asset groups as scan targets, you can enable this option to scan the asset group members based on their engine history.  When enabled, each asset group member is scanned by whichever engine scanned it last.  This can improve scan efficiency if your targeted asset group includes geographically dispersed assets.
[block:callout]
{
  "type": "info",
  "title": "TIP",
  "body": "If you enable the **Engine most recently used for that asset** option, your selected Scan Engine will ultimately be responsible for scanning any individual asset group member that does not yet have a scan history."
}
[/block]

[block:callout]
{
  "type": "warning",
  "title": "NOTE",
  "body": "Although the **Engine most recently used for that asset option** is available in all site configurations, it only applies to and affects the assets in your included asset groups."
}
[/block]
# Scan Engine Management

You can view, create, edit, update, and check the status of your Scan Engines from the engine management screen.  To access this view, click the **Administration** tab in your left navigation menu.  In the “Scan Options” section, click **manage** next to “Engines”.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/3d5f21a-admin_scanengine_manage.png",
        "admin_scanengine_manage.png",
        626,
        203,
        "#cfd2d5"
      ]
    }
  ]
}
[/block]
The Scan Engine management screen lists all your added Scan Engines and displays relevant information like connection status, communication direction, and version information.  You can also add new engines, [configure engine pools](doc:working-with-scan-engine-pools), and [adjust the communication direction](doc:scan-engine-communication-methods) of your existing engines from this screen.
[block:callout]
{
  "type": "info",
  "title": "TIP",
  "body": "The Scan Engine management screen’s **Refresh** function is the final step for pairing a Scan Engine to the Security Console.  Consult the Help page that corresponds to your Scan Engine type for instructions on how to complete these pairing procedures."
}
[/block]