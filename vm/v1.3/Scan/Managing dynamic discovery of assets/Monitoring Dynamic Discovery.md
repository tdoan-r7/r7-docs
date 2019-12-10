---
title: "Monitoring Dynamic Discovery"
excerpt: ""
---
[block:callout]
{
  "type": "info",
  "body": "Assets discovered through McAfee ePolicy Orchestrator connections are not virtual and therefore appear in the regular Assets list."
}
[/block]
Since discovery is an ongoing process as long as the connection is active, you may find it useful to monitor events related to discovery. The _Discovery Statistics_ page includes several informative tables:

* _Assets_ lists the number of currently discovered virtual machines, hosts, data centers, and discovery connections. It also indicates how many virtual machines are online and offline.
* _Dynamic Site Statistics_ lists each dynamic site, the number of assets it contains, the number of scanned assets, and the connection through which discovery is initiated for the site’s assets.
* _Events_ lists every relevant change in the target discovery environment, such as virtual machines being powered on or off, renamed, or being added to or deleted from hosts.

Dynamic Discovery is not meant to enumerate the host types of virtual assets. The application categorizes each asset it discovers as a host type and uses this categorization as a filter in searches for creating dynamic asset groups. See [Performing filtered asset searches](doc:performing-filtered-asset-searches). Possible host types include _Virtual machine_ and _Hypervisor_. The only way to determine the host type of an asset is by performing a credentialed scan. So, any asset that you discover through Dynamic Discovery and do not scan with credentials will have an _Unknown_ host type, as displayed on the scan results page for that asset. Dynamic discovery only finds virtual assets, so dynamic sites will only contain virtual assets.
[block:callout]
{
  "type": "info",
  "body": "Listings in the _Events_ table reflect discovery over the preceding 30 days."
}
[/block]
To monitor Dynamic Discovery, take the following steps:
1. Click the **Administration** icon.
2. In the _Discovery Options_ area of the _Administration_ page, click the *View** link for _Events_.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/820dbef-s_nx_admin_discovery_statistics_AWS.jpg",
        "s_nx_admin_discovery_statistics_AWS.jpg",
        2054,
        1278,
        "#eef3f3"
      ],
      "caption": "Viewing discovery statistics"
    }
  ]
}
[/block]