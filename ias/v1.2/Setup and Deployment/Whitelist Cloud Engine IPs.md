---
title: "Whitelist Cloud Engine IPs"
excerpt: ""
---
Some firewalls may block attack traffic and prevent InsightAppSec from testing your application for vulnerabilities. In such cases, you must whitelist the IP addresses of the InsightAppSec cloud engines to scan your web applications. The following table provides the IP addresses of the InsightAppSec engines based on the region where your platform account is hosted. When you log in to InsightAppSec, the region is the first sub-domain in the URL. For example, if the url is `https://us.appsec.insight.rapid7.com` then your region is US. 
Consult the following table to determine which IPs must be whitelisted according to your region.
[block:parameters]
{
  "data": {
    "h-0": "Region",
    "h-1": "IPs to Whitelist",
    "0-1": "34.205.208.125\n34.192.183.106\n34.224.19.93\n34.227.121.223\n45.79.136.181",
    "0-0": "US",
    "1-0": "EU",
    "1-1": "35.158.144.37\n35.156.166.245\n172.104.153.232",
    "2-1": "52.60.149.201\n52.60.191.46\n172.104.11.18",
    "2-0": "CA",
    "3-1": "52.63.190.180\n52.62.83.29\n139.162.25.220",
    "3-0": "AU",
    "4-1": "172.104.83.134\n52.68.0.155\n54.64.21.140",
    "4-0": "AP/Tokyo"
  },
  "cols": 2,
  "rows": 5
}
[/block]