---
title: "Uninstall an On-Premise Scan Engine"
excerpt: ""
---
To remove an on-premise scan engine:
1. Navigate to the **Rapid7 > InsightAppSec** folder, which is usually located at `Program Files\Rapid7\InsightAppSec`.
2. Right-click the `uninstall_InsightAppSec.exe` tool and select **Run as Administrator**.
3. Follow the steps of the uninstaller to remove the Scan Engine and all associated tools. 
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/2ade34c-Uninstall_Engine.png",
        "Uninstall Engine.png",
        1176,
        568,
        "#eff4f6"
      ]
    }
  ]
}
[/block]

[block:callout]
{
  "type": "danger",
  "title": "Note:",
  "body": "Do not use the Uninstall feature in the Windows **Control Panel > Programs and Features** screen to remove the scan engine. It will not remove certain related tools and your system will continue trying to connect with the Rapid7 platform. \n\nIf you have attempted to uninstall from the Programs and Features screen, contact Rapid7 Support."
}
[/block]