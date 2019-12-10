---
title: "Planning for capacity requirements"
excerpt: ""
---
Capacity planning is the process of determining the resources needed by an application over time by identifying current usage trends and analyzing growth patterns. As usage grows, the main challenge is to ensure that system performance is consistent over long periods of time and the system has enough resources to handle the capacity for future needs. This document gives detailed information on the capacity usage patterns of the application based on intended usage, so that you can plan, analyze, and address capacity issues and allocate resources as needed to support your expected use.

The approach is first to analyze the current capacity under certain conditions such as numbers of assets, number of scans performed, and the frequency and number of reports that are generated and then to plan for future capacity needs. Tests were completed with a wide variety of individual assets in order to accurately capture the impact that different types of assets have on scan time, network utilization, and disk usage. The results of these tests were then used to create formulas that you can use to predict capacity needs for various usage scenarios. These formulas were then tested with real-world scanning scenarios to get repeatable, empirical measurements of disk usage, scan duration, and network utilization.

If you are an administrator, use the capacity planning guidelines to answer the following questions:

* [What size console do I need for my deployment?](doc:planning-for-capacity-requirements#section-what-size-console-do-i-need-for-my-deployment-)
* [How long will it take to scan an average asset?](doc:planning-for-capacity-requirements#section-how-long-will-it-take-to-scan-an-average-asset-)
* [How does network latency affect scan duration?](doc:planning-for-capacity-requirements#section-how-does-network-latency-affect-scan-duration-)
* [How much disk space will I need on my console?](doc:planning-for-capacity-requirements#section-how-much-disk-space-will-i-need-on-my-console-)
* [How many assets can a Scan Engine handle?](doc:planning-for-capacity-requirements#section-how-many-assets-can-a-scan-engine-handle-)
* [How long will it take to scan X assets with Y engines?](doc:planning-for-capacity-requirements#section-how-long-will-it-take-to-scan-x-assets-with-y-engines-)
* [How many engines do I need to scan X assets in Y hours?](doc:planning-for-capacity-requirements#section-how-many-engines-do-i-need-to-scan-x-assets-in-y-hours-)
* [How much network bandwidth will be used when scanning?](doc:planning-for-capacity-requirements#section-how-much-network-bandwidth-will-be-used-when-scanning-)
* [How can I tune the application for maximum scanning throughout?](doc:planning-for-capacity-requirements#section-how-can-i-tune-the-application-for-maximum-scanning-throughout-)

## What size console do I need for my deployment?

Below are some general guidelines on the size of the console needed for deployment based on your scanning needs. The table shows recommended console sizes when scanning weekly. The specifications provided are based on Rapid7’s pre-built hardware appliances, which can also serve as recommendations when not using the pre-built appliances from Rapid7:
[block:parameters]
{
  "data": {
    "h-0": "Number of Assets",
    "h-1": "Recommended",
    "h-2": "Specifications",
    "0-0": "< 5,000",
    "0-1": "R7-1000 Entry Level Appliance",
    "0-2": "* 16GB RAM\n* Intel Xeon E5-2603 v3 1.6 Ghz (6 cores)\n* 2 x 1TB 7200 SATA (1TB software RAID-1)\n* 1 U HP DL120 Gen9",
    "1-0": "5,000 – 20,000",
    "1-1": "R7-3000 Mid-tier appliance",
    "1-2": "* 64GB RAM\n* 2 x Intel Xeon Processor E5-2609 v3 1.90 GHz (6 cores) \n* 8x 500GB 7200 SATA (2TB hardware RAID-10)\n* 2 U HP DL380 Gen9",
    "2-0": "20,000 – 150,000",
    "2-1": "R7-5000 Enterprise",
    "2-2": "* 128GB RAM\n* 2 x Intel Xeon Processor E5-2609 v3 1.90 GHz (6 cores) \n* 16 x 500GB 7200 SATA (4TB hardware RAID-10)\n* 2 U HP DL380 Gen9",
    "3-0": "150,000 – 400,000",
    "3-1": "R7-5000x Enterprise Plus",
    "3-2": "* 256GB RAM\n* 2 x Intel Xeon Processor E5-2609 v3 1.90 GHz (6 cores)\n* 16 x 1TB 7200 SATA (8TB hardware RAID-10)\n* 2 U HP DL380 Gen9",
    "4-0": ">400,000",
    "4-1": "Multiple Enterprise or Enterprise Plus consoles",
    "4-2": "* Rapid7 will help size and architect your deployment based on your scanning needs."
  },
  "cols": 3,
  "rows": 5
}
[/block]
## How long will it take to scan an average asset?

Scan duration will vary based on operating system installed, responsiveness of the asset, open ports, applications installed, services running, and patch levels. These variables, in addition to scan configuration and network conditions, affect the scan duration and disk usage needs.

Below is a summary of average scan duration and disk usage when using the Full Audit template across a /20 network range where ~1,000 assets are alive. We will use these values in later calculations when determining total scan duration based on number of assets, engines and threads.

| Type of scan | Vulns per asset | Average Asset Scan Duration | Average Asset Disk Usage |
| - -- | - -- | - -- | - -- |
| Unauthenticated | 18 | 3.5 minutes (range 12 s – 29 min) | 37 KB |
| Authenticated | 307 | 7.4 minutes (range 12 s – 38 min) | 422 KB |

The test results indicate that authenticated scanning can take about twice as long as unauthenticated scanning due to the increase in the amount of local software that is assessed when having access to the asset.

## How does network latency affect scan duration?

Scan duration may vary based on network latency. The graph below shows the scan time for two sample assets when scanned for vulnerabilities (no policy checks were run) with credentials under different network latencies. In the capacity planning testing it was observed that network latencies of 100 ms increased scan times by 15-25% and network latencies of 300 ms increased scan times by around 35% for the assets tested. Actual impact may vary depending on the asset being scanned and the scan settings.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/4edf01e-c_scan_duration_with_latency.jpg",
        "c_scan_duration_with_latency.jpg",
        669,
        411,
        "#537ba8"
      ]
    }
  ]
}
[/block]
## How much disk space will I need on my console?

We will use the following values for “Average Asset Disk Usage” that we collected earlier. Authenticated scanning will consume about 10 times the disk that unauthenticated scanning will consume. This is because authenticated scanning will evaluate vulnerabilities in local software packages and file shares that unauthenticated scanning will not evaluate.
[block:parameters]
{
  "data": {
    "h-0": "Type of Scan",
    "h-1": "Vulns Per Asset",
    "h-2": "Average Asset Scan Duration",
    "h-3": "Average Asset Disk Usage",
    "0-0": "Unauthenticated",
    "0-1": "18",
    "0-2": "3.5 minutes",
    "0-3": "37 KB",
    "1-0": "Authenticated",
    "1-1": "307",
    "1-2": "7.4 minutes (range 12 s – 38 min)",
    "1-3": "422 KB"
  },
  "cols": 4,
  "rows": 2
}
[/block]
Reports that summarize trends or remediation information use much less disk space than those reports and export formats that export all asset and vulnerability information. Therefore, to determine disk usage by reporting, a CSV export of all fields across the ~1,000 assets tested was created in order to calculate the disk usage per asset that was consumed for authenticated and unauthenticated scans. This would represent retrieving all data out of the system after every scan.
[block:parameters]
{
  "data": {
    "h-0": "Type of Scan",
    "h-1": "Average Vulns",
    "h-2": "Report Template",
    "h-3": "Average Asset Disk Usage",
    "0-0": "Unauthenticated",
    "0-1": "18",
    "0-2": "CSV Export – All Fields",
    "0-3": "52 KB",
    "1-0": "Authenticated",
    "1-1": "307",
    "1-2": "CSV Export – All Fields",
    "1-3": "703 KB"
  },
  "cols": 4,
  "rows": 2
}
[/block]
Here is the formula to calculate the total disk usage based on number of scans, number of reports, and the number of assets scanned and reported:

_Total Disk SpaceRequired_
= (_K x NumberOfAssets x NumberOfScans_)
+ (_L x NumberOfAssets x NumberOfScans x NumberOfReportsGenerated_)
+ _M_

where K = disk usage of one scan of one asset, L = disk usage of for reporting on an asset, and M = the base install of the application. The values can be pulled from our test data for authenticated and unauthenticated scans:
[block:parameters]
{
  "data": {
    "h-0": "Parameter",
    "h-1": "Unauthenticated Scan",
    "h-2": "Authenticated Scan",
    "0-0": "K",
    "0-1": "37 KB",
    "0-2": "422 KB",
    "1-0": "L",
    "1-1": "52 KB",
    "1-2": "703 KB",
    "2-0": "M",
    "2-1": "2,500 MB",
    "2-2": "2,500 MB"
  },
  "cols": 3,
  "rows": 3
}
[/block]
Now we can calculate the total disk usage over time. Total disk space required for unauthenticated scanning of 10,000 assets weekly for one year and generating two reports, CSV Export of all fields and a _Top Remediations with Details_ report, every week:

= (0.037 x 10,000 x 52) + (0.052 x 10,000 x 2 x 52) + 2,500 MB

= **75,820 MB (~76 GB)**

The following chart illustrates disk usage over time for reporting and **unauthenticated** scanning 10,000 assets weekly and generating two reports per scan:
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/6a99c29-c_disk_usage_unauth_scanning_reporting_10000_assets.jpg",
        "c_disk_usage_unauth_scanning_reporting_10000_assets.jpg",
        689,
        373,
        "#ccd5e4"
      ]
    }
  ]
}
[/block]
Total disk space required for **authenticated** scanning of 10,000 assets weekly for one year and generating two reports, _CSV Export_ and _Remediation Plan_, every week:

= (.422 x 10,000 x 52) + (.703 x 10,000 x 2 x 52) + 2,500 MB

= **953,060 MB (~.95 TB)**
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/025adff-c_disk_usage_auth_scanning_reporting_10000_assets.jpg",
        "c_disk_usage_auth_scanning_reporting_10000_assets.jpg",
        695,
        392,
        "#ccd5e3"
      ]
    }
  ]
}
[/block]
In order to ensure the proper disk capacity, set the proper data retention policy by reading the "Setting data retention preferences" section.

## How many assets can a Scan Engine handle?

Real world scanning throughput will depend on the network conditions, the average asset scan times, and scheduling. If a given engine is handling concurrent scans, keep in mind that the number of threads will also increase. For example, if an 8 GB engine is assigned to two sites and scanning 1,000 assets in each site with a scan template that scans 100 assets concurrently, then the concurrent assets would effectively be 200 and you probably want to change the schedule or increase the memory or reduce the number of concurrent assets. Note that the number of concurrent assets to scan is set on the _Scan Template Configuration_ page using the **Maximum assets scanned simultaneously per Scan Engine** option on the _General_ tab. To learn more, see the [Tune](doc:tune) section.

The following table provides general guidelines on how many assets a given scan engine can scan in a day based on general guidelines.
[block:parameters]
{
  "data": {
    "h-0": "Engine Memory",
    "h-1": "Engine Cores",
    "h-2": "Concurrent Assets",
    "h-3": "Unauthenticated",
    "h-4": "Authenticated",
    "0-0": "8 GB",
    "0-1": "4",
    "0-2": "100",
    "0-3": "0-10,000 per day",
    "0-4": "0-5,000 per day",
    "1-0": "16 GB",
    "1-1": "8",
    "1-2": "200",
    "1-3": "10,000 - 20,000 per day",
    "1-4": "5,000 – 10,000 per day",
    "2-0": "32 GB",
    "2-1": "8",
    "2-2": "400",
    "2-3": "20,000 - 40,000 per day",
    "2-4": "10,000 – 20,000 per day"
  },
  "cols": 5,
  "rows": 3
}
[/block]
## How long will it take to scan X assets with Y engines?

Scan duration depends on number of assets to be scanned, the average asset scan duration, the number of Scan Engines being used, and the number of scan threads used on the scan template. Scan duration decreases as the number of Scan Engines and number of scan threads increases for a fixed number of assets. There is some additional overhead to adding engines due to the remote communication required to retrieve the result; however, adding scan engines is the best way to horizontally scale up the scanning ability to larger numbers of assets in shorter periods of time.

The following formula calculates estimated scan duration based on number of assets, average scan time per asset, number of scan threads and number of scan engines. Note that the network configuration is also an important factor in number of scan engines needed. For example, if assets are spread across 4 VLANS without connectivity between them, one scan engine will be required per VLAN to be able to scan assets in that VLAN.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/6985a46-equation_scan_x_assets_with_y_engines_time.PNG",
        "equation_scan_x_assets_with_y_engines_time.PNG",
        467,
        148,
        "#133d66"
      ]
    }
  ]
}
[/block]
The _1.2_ value above represents the overhead of integrating scan results into the console. The _.85_ represents the overhead of managing additional scan engines. Both values are conservative estimates and may vary based on the console’s specifications and configuration. The lower bound on both of these formulas will always be the longest asset scan duration. For example, if there is one asset that takes thirty minutes to scan then the total scan time for all assets will never be less than thirty minutes.

Here is an example of using 100 threads to scan 10,000 assets with an average asset scan duration of 3.5 minutes:

= (1.2 x 3.5 min x 10,000)/100 = 420 minutes = 7 hours

The total time to perform an authenticated scan of 10,000 assets with one Scan Engine would be the following:

= (1.2 x 3.5 min x 10,000)/(.85 x 4 x 100)= 123 minutes = ~2 hours

This chart shows the effect on scan duration when using different amounts of threads and engines. As you can see, increasing thread count per engine is more effective than adding engines. However, each engine can only handle a certain amount of threads before memory or CPU contention becomes a bottleneck and adding more threads or engines does not help significantly. Therefore, you should maximize the number of threads per engine before scaling out to multiple engines in order to have the most impact on scan duration.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/ac6ab3b-c_scan_duration_unauth.jpg",
        "c_scan_duration_unauth.jpg",
        669,
        437,
        "#d9dde3"
      ]
    }
  ]
}
[/block]

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/98fcafb-c_scan_duration_auth.jpg",
        "c_scan_duration_auth.jpg",
        672,
        401,
        "#dcdfe4"
      ]
    }
  ]
}
[/block]
## How many engines do I need to scan X assets in Y hours?

The same formula can be used to calculate number of Scan Engines needed as well. For example, if 10,000 assets need to be scanned in 4 hours then the following will calculate the number of engines needed:
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/6bd071e-equation_scan_x_assets_with_y_engines_number.PNG",
        "equation_scan_x_assets_with_y_engines_number.PNG",
        403,
        46,
        "#17446c"
      ]
    }
  ]
}
[/block]
For unauthenticated scanning with 100 threads with average asset scan time of 3.5 minutes:

= (1.2 x 3.5 min x 10,000)/(.85 x 100 x 240) = **~2 engines required**

For authenticated scanning with 100 threads we change the average asset scan time to 7.4 minutes:

= (1.2 x 7.4 min x 10,000)/(.85 x 100 x 240) = **~4 engines required**

Please note that the number of engines required may be determined by the scan templates used and the accessibility of scan targets within the network topology. The formula above is to be used for guidance in determining the number of engines needed for sheer throughput and assumes the engines have access to all the assets being scanned and that assets can be equally distributed across sites.

## How much network bandwidth will be used when scanning?

As the application scans assets over the network, a considerable amount of network resources may be consumed. The amount of network bandwidth used is directly proportional to number of devices being scanned simultaneously, the type of assets being scanned, and the scan template settings. This section provides capacity guidelines of network utilization when assets over the network were being scanned so that administrators can adjust their scan windows and scan template settings to not affect other critical network traffic or affect accuracy of scan results.

The following graph represents the network utilization with different number of assets in one site, keeping number of scan threads constant (20) number of scan ports constant (20) and performing unauthenticated scans:
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/0d3c561-c_network_utilization.jpg",
        "c_network_utilization.jpg",
        663,
        338,
        "#858189"
      ]
    }
  ]
}
[/block]
The network utilization would remain constant after a certain number of assets, because the upper bound is determined by the total number of scan threads defined in the scan template.

The more simultaneous scans are performed the more network bandwidth would be consumed up to a certain point. The below graph shows the network bandwidth consumption in two different scan scenarios performed on fixed number of assets

- _Scenario 1:_ One site - 20 Threads configured - Unauthenticated Scan
- _Scenario 2:_ Two Sites - 20 Threads configured (each) - Unauthenticated Scan
- _Scenario 3:_ Three Sites - 20 Threads configured (each) - Unauthenticated Scan

The following graph shows the comparative network utilization based on these three scenarios:
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/881be6d-c_network_utilization_additional_sites.jpg",
        "c_network_utilization_additional_sites.jpg",
        572,
        310,
        "#b9595a"
      ]
    }
  ]
}
[/block]
When simultaneous scans are performed with additional sites, scan duration would come down but at the expense of in network bandwidth and CPU utilization.

_Peak Network Bandwidth (Mbps)_ = 0.4_x No.OfAssetsScanned Simultaneously_
_AverageNetwork Bandwidth (Mbps)_ = 0.45_x PeakNetworkBandwidth_

## How can I tune the application for maximum scanning throughput?

### Tuning the database server for maximum performance

The application comes with a PostgreSQL database server installed which can be tuned for better performance based on the amount of RAM available to the console host. Tuning PostgreSQL will improve integration times which will reduce overall scan duration. See [Tuned PostgreSQL settings](doc:configuring-maximum-performance-in-an-enterprise-environment#section-tuned-postgresql-settings) for more information on how to tune the database.

### Tuning scan templates for maximum performance

Scan templates have a wide variety of options which can be adjusted to deliver greater throughput when scanning. One of the most effective tuning options is to increase the number of scan threads from the default value by setting **Maximum assets scanned simultaneously per Scan Engine** on the _General_ tab of the _Scan Template Configuration_ page. When scanning assets that have a lot of open services, increase the value of **Maximum scan processes simultaneously used on each asset** to decrease scan duration. To decrease the duration spent during asset discovery, increase the minimum value for **Packets-per-Second Rate** on the _Discovery Performance_ tab of the scan template. Increasing the minimum can greatly improve discovery performance and comes at the cost of additional bandwidth usage so be aware of the demands on the network when increasing this value.

See [Scan templates](doc:scan-templates) for information on how to tune templates for maximum performance.

### Scaling with multiple Scan Engines

As seen by the _Scan Engine performance_ section, multiple engines can provide greater throughput for scanning and enables deployments to horizontally scale to large numbers of assets. Before scaling to multiple engines, increase the number of threads used in order to maximize the hardware resources available on each engine. Since the console is responsible for generating reports, integrating scan results, and serving up content for end users, it is highly recommended to delegate scanning to remote engines when scanning more than a few hundred assets.

### Scaling with multiple Security Consoles

Multiple consoles can also be deployed in situations where regional areas have their own scanning and reporting needs. Adding additional consoles enabled horizontal scaling of the reporting, user interface, and integration resources. For more information, see [Where to put the Security Console](doc:setting-up-the-application-and-getting-started#section-where-to-put-the-security-console).