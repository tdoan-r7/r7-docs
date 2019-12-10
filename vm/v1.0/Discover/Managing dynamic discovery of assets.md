---
title: "Managing dynamic discovery of assets"
excerpt: ""
---
## What is Dynamic Discovery, and why use it?

It may not be unusual for your organization’s assets to fluctuate in number, type, and state, on a fairly regular basis. As staff numbers grow or recede, so does the number of workstations. Servers go online and out of commission. Employees who are traveling or working from home plug into the network at various times using virtual private networks (VPNs).

This fluidity underscores the importance of having a dynamic asset inventory. Relying on a manually maintained spreadsheet is risky. There will always be assets on the network that are not on the list. And, if they’re not on the list, they're not being managed. Result: added risk.

One way to manage a "dynamic inventory," is to run discovery scans on a regular basis. See [Configuring asset discovery](doc:configuring-asset-discovery). This approach is limited because scan provides a snapshot of your asset inventory at the time of the scan. Another approach, Dynamic Discovery, allows you to discover and track assets without running a scan. It involves initiating a connection with a server or API that manages an asset environment, such as one for virtual machines, and then receiving periodic updates about changes in that environment. This approach has several benefits:

* As long as the discovery connection is active, the application periodically discovers assets "in the background," without manual intervention on your part.
* You can create dynamic sites that update automatically based on dynamic asset discovery. See [Configuring a site using a Dynamic Discovery connection](doc:configuring-a-site-using-a-dynamic-discovery-connection). Whenever you scan these sites, you are scanning the most current set of assets.
* You can concentrate scanning resources for vulnerability checks instead of running discovery scans.

## Verifying that your license enables relevant features

The following types of Discovery Connections require the Dynamic Discovery option:

* Amazon Web Services
* DHCP log servers, VMware servers
* McAfee ePolicy Orchestrator and Data Exchange Layer
* Project Sonar, see [Working with Project Sonar](doc:working-with-project-sonar) for more information

For McAfee Data Exchange Layer connections, your license must also enable the Adaptive Security option.

For ActiveSync connections that allow you to discover mobile devices, your license must enable the Mobile option.

To verify that your license enables Virtual Discovery:

1. Click the **Administration** icon.
The Security Console displays the _Administration_ page.

2. Click the **Manage** link for _Security Console_.
The Security Console displays the _Security Console Configuration_ panel.

3. Click the **Licensing** link.
The Security Console displays the _Licensing_ page.

4. See if the _Dynamic Discovery_ or _Mobile_ feature is checked, depending on your needs.