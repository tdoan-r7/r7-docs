---
title: "Pairing a hosted Scan Engine"
excerpt: ""
---
[block:callout]
{
  "type": "warning",
  "title": "NOTE",
  "body": "You must be licensed to use a hosted Scan Engine in order to pair one to your Security Console.  Contact your Customer Success Manager to learn more about gaining access to hosted Scan Engines."
}
[/block]
When an InsightVM Hosted Scan Engine isn’t properly paired to an InsightVM Console, you may see the following error:

    Cannot refresh scan engine <Scan Engine Name> Unauthorized console connection from <IP address of console>
[block:api-header]
{
  "type": "basic",
  "title": "Adding the Engine"
}
[/block]
To add an engine:
1. Go to **Administration** and click **manage** under Engines in the Scan Options section.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/f460fa6-Nexpose_Manage_ScanEngine.jpg",
        "Nexpose_Manage_ScanEngine.jpg",
        749,
        192,
        "#252d3c"
      ]
    }
  ]
}
[/block]
2. Click the refresh icon next to **Rapid7 Hosted Scan Engine**.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/eaad3c3-74ffd72-Nexpose_Admin_ScanEngine_refresh.jpg",
        "74ffd72-Nexpose_Admin_ScanEngine_refresh.jpg",
        1137,
        337,
        "#f2f5f5"
      ]
    }
  ]
}
[/block]
You will see the following message: 
```
Cannot refresh scan engine (Rapid7 Hosted Scan Engine): Unauthorized console connection from: <IP ADDRESS>
```

Take a screenshot of this message or make a note of the IP address for the next step.
[block:api-header]
{
  "title": "Authorizing the Console"
}
[/block]

Please send the screenshot or listed IP address from the previous section to [Rapid7 Support](https://help.rapid7.com/get-support.html) so we can complete the pairing of the Hosted Engine to your console.

If any message besides the "Cannot refresh scan engine <Scan Engine Name> Unauthorized console connection from <IP address of console>" error is presented, please provide a screenshot of that message.