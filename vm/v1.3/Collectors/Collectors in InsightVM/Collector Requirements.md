---
title: "Collector Requirements"
excerpt: ""
---
Before installing a Collector, verify that your intended host machine and network meet the following requirements.

# General Requirements and Recommendations

Consider the following before choosing a Collector host:

* **DO NOT** install a Collector on a host that already runs a Security Console or Scan Engine.
 * Security Consoles and Scan Engines will not function properly if a Collector is present on the same host.
* Only install one Collector per machine, whether physical or virtual.
 * Additionally, Rapid7 recommends that the host be entirely dedicated to the Collector’s use to maximize resource availability.
* Your Collector host must be configured with a Fully Qualified Domain Name (FQDN).

# Hardware Requirements and Recommendations

You can install a Collector on a network server or virtual machine that meets the following minimum hardware requirements:

* 2 CPU cores
* 8 GB RAM
* 60 GB available disk space

For optimal performance, Rapid7 recommends the following hardware specifications:
[block:parameters]
{
  "data": {
    "h-0": "Collector Size",
    "h-1": "Number of Agents",
    "h-2": "Recommended CPU Cores",
    "h-3": "Recommended RAM",
    "h-4": "Recommended Disk Space*",
    "0-0": "Small",
    "0-1": "Up to 500",
    "0-2": "4",
    "0-3": "8 GB",
    "0-4": "60 GB",
    "1-0": "Medium",
    "1-1": "Up to 2,400",
    "1-2": "4",
    "1-3": "8 GB",
    "1-4": "80 GB",
    "2-0": "Large",
    "2-1": "Up to 600 per CPU core**",
    "2-2": "4+",
    "2-3": "16 GB",
    "2-4": "100 GB"
  },
  "cols": 5,
  "rows": 3
}
[/block]

[block:callout]
{
  "type": "info",
  "title": "* Disk Space",
  "body": "In cases where a connection to the Insight platform is interrupted or lost, the Collector will hold data in the form of logs written to the disk until a connection can be reestablished.\n\nThe more disk space a Collector has, the longer it can operate without a connection to the Insight platform."
}
[/block]

[block:callout]
{
  "type": "warning",
  "title": "** CPU Cores",
  "body": "The Collector can only be responsible for 600 agents per CPU core.  Mutlicore CPUs are recommended for taking on additional agents per Collector.\n\nIf your Collector CPU usage stays consistently above 40% under normal load, consider deploying an additional Collector."
}
[/block]
# Supported Operating Systems

Your Collector host must run one of the following 64-bit operating systems:

* Ubuntu 11.04 - 17.04
* Ubuntu Linux 10.04 LTS
* Debian 7.0 - 8.2
* CentOS 5.2 - 7.3
* Oracle Enterprise Linux (OEL) 5.2 - 7.3
* Fedora 17 - 25
* SUSE Linux Enterprise Server (SLES) 11 -12
* SUSE Linux Enterprise Desktop (SLED) 11 -12
* openSUSE LEAP (42.1 - 42.2)
* Amazon Linux
* Red Hat Enterprise Linux (RHEL) 5.2 - 7.3
* Microsoft Windows Server 2016
* Microsoft Windows Server 2012 R2
* Microsoft Windows Server 2008 R2
* Windows 7 and newer

# Supported Browsers

You need to access your InsightVM web interface in order to retrieve the installer and complete the activation process.  To do so, use either of the following supported web browsers:

* Mozilla Firefox (latest stable version)
* Google Chrome (latest stable version)

# Networking Requirements

The Collector communicates with your deployed agents and the Insight platform through the following TCP ports, all of which must be whitelisted for the designated target:
[block:parameters]
{
  "data": {
    "h-0": "Data Type",
    "h-1": "Direction",
    "h-2": "Destination",
    "h-3": "Port",
    "0-0": "All relevant agent data to the platform",
    "0-1": "Outbound",
    "0-2": "All endpoint URLs ending with `*.endpoint.ingress.rapid7.com`",
    "0-3": "443",
    "1-0": "Agent communication to Collector",
    "1-1": "Inbound",
    "1-2": "Rapid7 Collector",
    "2-2": "Rapid7 Collector",
    "3-2": "Rapid7 Collector",
    "1-3": "5508",
    "2-0": "Agent update requests to Collector",
    "2-1": "Inbound",
    "2-3": "6608",
    "3-0": "Agent file upload to Collector",
    "3-1": "Inbound",
    "3-3": "8037"
  },
  "cols": 4,
  "rows": 4
}
[/block]

[block:callout]
{
  "type": "warning",
  "title": "NOTE - Additional Connectivity Required",
  "body": "This InsightVM use case also requires additional connectivity as noted in the “Data Upload” section on this [platform communications page](doc:configure-communications-with-the-insight-platform)."
}
[/block]