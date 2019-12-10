---
title: "Setting up the application and getting started"
excerpt: ""
---
Once you’ve mapped out your Scan Engine deployment, you’re more than halfway to planning your installation. The next step is to decide how you want to install the main components—the Security Console and Scan Engines.

##Understanding deployment options
InsightVM components are available in two versions. The hardware/software Appliance is a plug-and-play device that contains the components of a Security Console and a Scan Engine. When you purchase an Appliance, it can be configured to run as a Scan Engine or as a Security Console with a local Scan Engine.

In some ways, an Appliance is a simpler solution than the software-only version of the product, which requires you to allocate your own resources to meet system requirements. When you install InsightVM software on a given host, your options —as with the Appliance—include running the application as a just a Scan Engine or as a Security Console and Scan Engine.

###Installation scenarios—which one are you?
The different ways to install InsightVM address different business scenarios and production environments. You may find one of these to be similar to yours.

####Small business, internal network
The owner of a single, small retail store has a network of 50 or 60 work stations and needs to ensure that they are PCI compliant. The assets include registers, computers for performing merchandise look-ups, and file and data servers. They are all located in the same building. A software-only Security Console/Scan Engine on a single server is sufficient for this scenario.

####Mid-size company with some remote locations
A company has a central office and two remote locations. The headquarters and one of the other locations have only a handful of assets between them. The other remote location has 300 assets. Network bandwidth is mediocre, but adequate. It definitely makes sense to dedicate a Scan Engine to the 300-asset location. The rest of the environment can be supported by a Security Console and Scan Engine on the same host. Due to bandwidth limitations, it is advisable to scan this network during off-hours.

####Global enterprise with multiple, large remote locations
A company headquartered in the United States has locations all over the world. Each location has a large number of assets. Each remote location has one or more dedicated Scan Engines. One bank of Scan Engines at the U.S. office covers local scanning and provides emergency backup for the remote Scan Engines. In this situation, it is advisable not to use the Scan Engine that shares the host with the Security Console, since the Security Console has to manage numerous Scan Engines and a great deal of data.

##Where to put the Security Console
Unlike Scan Engines, the Security Console is not restricted in its performance by its location on the network. Engines can be set to initiate outbound connections with the Console or to have the console initiate those connections in order to initiate scans. When a Security Console sends packets through an opening in a firewall, the packets originate from “inside” the firewall and travel to Scan Engines “outside.” You can install the Security Console wherever it is convenient for you.

One Security Console is typically sufficient to support an entire enterprise, assuming that the Security Console is not sharing host resources with a Scan Engine. If you notice that the Security Console’s performance is slower than usual, and if this change coincides with a dramatic increase in scan volume, you may want to consider adding a second Security Console.

Configuring the environment involves pairing each installed Scan Engine with a Security Console. 

##A deployment plan for Example, Inc.
Let’s return to the environment table for Example, Inc.
[block:parameters]
{
  "data": {
    "h-0": "Network segment",
    "h-1": "Address space",
    "h-2": "No. of assets",
    "h-3": "Location",
    "h-4": "Asset funciton",
    "0-0": "New York Sales",
    "0-1": "10.1.0.0/22",
    "0-2": "254",
    "0-3": "Building 1: Floors 1-3",
    "0-4": "Work stations",
    "1-0": "New York IT/Administration",
    "1-1": "10.1.10.0/23",
    "1-2": "50",
    "1-3": "Building 2: Floor 2",
    "1-4": "Work stations\nServers",
    "2-0": "New York printers",
    "2-1": "10.1.20.0/24",
    "2-2": "56",
    "2-3": "Buildings 1 & 2",
    "2-4": "Printers",
    "3-0": "New York DMZ",
    "3-1": "172.16.0.0/22",
    "3-2": "30",
    "3-3": "Co-location facility",
    "3-4": "Web server\nMail server",
    "4-0": "Madrid sales",
    "4-1": "10.2.0.0/22",
    "4-2": "65",
    "4-3": "Building 3: Floor 1",
    "4-4": "Work stations",
    "5-0": "Madrid development",
    "5-1": "10.2.10.0/23",
    "5-2": "130",
    "5-3": "Building 3: Floors 2 & 3",
    "5-4": "Work stations\nServers",
    "6-0": "Madrid printers",
    "6-1": "10.2.20.0/24",
    "6-2": "35",
    "6-3": "Building 3: Floors 1-3",
    "6-4": "Printers",
    "7-0": "Madrid DMZ",
    "7-1": "172.16.10.0/24",
    "7-2": "15",
    "7-3": "Building 3: dark room",
    "7-4": "File server"
  },
  "cols": 5,
  "rows": 8
}
[/block]
A best-practices deployment plan might look like this:

The eight groups collectively contain a total of 635 assets. Example, Inc., could purchase a fixed-number license for 635 licenses, but it would be wiser to purchase a discovery for the total address space. It is always a best practice to scan all assets in an environment according to standards such as PCI, ISO 27002, or ISO 27001. This practice reflects the hacker approach of viewing any asset as a possible attack point.

Example, Inc., should distribute InsightVM components throughout its four physical locations:

* Building 1
* Building 2
* Building 3
* Co-Location facility

The IT or security team should evaluate each of the LAN/WAN connections between these locations for quality and bandwidth availability. The team also should audit these pipes for devices that may prevent successful scanning, such as firewalls, ACLs, IPS, or IDS.

Finally the team must address any logical separations, like firewalls and ACLs, which may prevent access.

The best place for the Security Console is in New York because the bulk of the assets are there, not to mention IT and administration groups.

Assuming acceptable service quality between the New York buildings, the only additional infrastructure would be a Scan Engine inside the Co-Location facility.

Example, Inc., should install at least one Scan Engine in the Madrid location, since latency and bandwidth utilization are concerns over a WAN link.

Finally, it’s not a bad idea to add one more Scan Engine for the Madrid DMZ to bypass any firewall issues.

The following table reflects this plan.
[block:parameters]
{
  "data": {
    "h-0": "Asset",
    "h-1": "Location",
    "0-0": "Security Console",
    "0-1": "New York: Building 2",
    "1-0": "Scan Engine #1",
    "1-1": "New York: Co-Location Facility",
    "2-0": "Scan Engine #2",
    "2-1": "Madrid: Building 3",
    "3-0": "Scan Engine #3",
    "3-1": "Madrid: dark room"
  },
  "cols": 2,
  "rows": 5
}
[/block]
###Your deployment checklist
When you are ready to install, configure, and run InsightVM, it’s a good idea follow a general sequence. Certain tasks are dependent on others being completed.

You will find yourself repeating some of these steps:
* install components
* log onto the Security Console Web interface
* configure Scan Engines, and pair them with the Security Console
* create dynamic discovery connections to pull assets from VMWare, AWS, DHCP, etc.
* create one or more sites
* assign each site to a Scan Engine
* select a scan template for each site
* schedule scans
* create user accounts, and assign site-related roles and permissions to these accounts
* run scans
* configure and run reports
* create asset groups to view reports and asset data
* create user accounts, and assign asset-group-related roles and permissions to these accounts
* assign remediation tickets to users
* re-run scans to verify remediation
* perform maintenance tasks