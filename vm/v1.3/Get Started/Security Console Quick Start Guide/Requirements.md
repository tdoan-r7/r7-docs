---
title: "Requirements"
excerpt: ""
---
Before starting the installation process, make sure the Security Console’s host machine meets the following requirements.

# System

Check our [System Requirements](https://www.rapid7.com/products/insightvm/system-requirements/) page for details.  Note the supported operating systems and browsers in particular.  Also, you can run the Security Console and Scan Engine on a virtualized instance of any of our supported operating systems as long as they meet the system requirements.

Rapid7 recommends deployments with Ubuntu Linux.
[block:callout]
{
  "type": "info",
  "title": "Look familiar?",
  "body": "If you’re arriving here from the [basic deployment plan](doc:basic-deployment-plan), you’ll notice that we already considered some of this information."
}
[/block]
# Networking

The following network requirements must be configured to use the Security Console:

## Host IP address

The IP address of your host machine must be statically assigned.  You will use this address to access the Security Console’s web interface.

## Ports

The Security Console communicates through these ports in order to perform the following tasks:
[block:parameters]
{
  "data": {
    "h-0": "Port",
    "h-1": "Task",
    "h-2": "Direction",
    "h-3": "Destination",
    "0-1": "Web interface access to the Security Console",
    "1-1": "Management of scan activity on Scan Engines and the retrieval of scan data",
    "2-1": "Download S/MIME validated content and feature updates",
    "3-1": "Upload of PGP-encrypted diagnostic information",
    "0-2": "Inbound",
    "1-2": "Outbound",
    "2-2": "Outbound",
    "3-2": "Outbound",
    "0-3": "Security Console",
    "1-3": "Scan Engine",
    "2-3": "updates.rapid7.com",
    "3-3": "support.rapid7.com",
    "0-0": "3780 (HTTPS protocol)",
    "1-0": "40814",
    "2-0": "80",
    "3-0": "443"
  },
  "cols": 4,
  "rows": 4
}
[/block]

[block:callout]
{
  "type": "info",
  "title": "Don’t forget to opt into the Insight platform!",
  "body": "InsightVM’s platform-only features like Dashboards and Remediation Projects require some additional connectivity in order to function properly.  See our [communications page](https://insightvm.help.rapid7.com/docs/configure-communications-with-the-insight-platform) for detailed platform connectivity requirements."
}
[/block]
# Programs and services

Several programs and services must be disabled for the Security Console to function.  In general, the following services may interfere with network scanning and may also prevent checks from loading or executing:

* Anti-virus / malware detectors
* Intrusion Detection Systems (IDS)
* Personal firewalls
* Executable blocking products
* SELinux
[block:callout]
{
  "type": "success",
  "title": "Do you have what InsightVM needs?",
  "body": "You should now understand all the requirements for the Security Console and where you need to make any necessary adjustments.  When you’re ready, let’s download an installer."
}
[/block]