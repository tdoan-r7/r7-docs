---
title: "Security Console port requirements"
excerpt: ""
---
The Security Console communicates through these ports using TCP in order to perform the following tasks:
[block:parameters]
{
  "data": {
    "h-0": "Task",
    "h-1": "Direction",
    "h-2": "Destination",
    "h-3": "Port",
    "0-0": "Management of scan activity on Scan Engines and the retrieval of scan data",
    "0-1": "Outbound",
    "0-2": "Scan Engine",
    "0-3": "40814",
    "1-0": "Download of content and feature updates from updates.rapid7.com",
    "1-1": "Outbound",
    "1-2": "Update server",
    "1-3": "80",
    "2-0": "Upload of PGP-encrypted diagnostic information to support.rapid7.com",
    "2-1": "Outbound",
    "2-2": "Support server",
    "2-3": "443",
    "3-0": "Web interface access to the Security Console",
    "3-1": "Inbound",
    "3-2": "Security Console",
    "3-3": "3780 (HTTPS request)"
  },
  "cols": 4,
  "rows": 4
}
[/block]

[block:callout]
{
  "type": "info",
  "title": "Looking for Insight platform communication requirements?",
  "body": "See [Configure communications with the Insight platform](doc:configure-communications-with-the-insight-platform) for additional whitelisting information."
}
[/block]