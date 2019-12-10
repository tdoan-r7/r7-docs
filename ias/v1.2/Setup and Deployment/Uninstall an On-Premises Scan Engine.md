---
title: "Uninstall an On-Premises Scan Engine"
excerpt: ""
---
To remove an on-premise Scan Engine, you must perform the following steps:
1. Run the InsightAppSec Uninstaller
2. Delete the Engine from the Manage On-Premise Engines screen

# Run the InsightAppSec Uninstaller
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
# Delete the Engine from the Manage On-Premise Engines screen
To delete a Scan Engine from InsightAppSec:
1. Go to **Settings > Manage On-Premise Engines** from the left navigation.
2. Select the **Engines** tab.
3. Select the Scan Engine to be deleted in the “On-Premise Engines” table by checking the box in the first column.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/e89bff3-Delete_On_prem_engine_in_UI.png",
        "Delete On prem engine in UI.png",
        477,
        318,
        "#36414c"
      ]
    }
  ]
}
[/block]
4. Click the **Delete** button that has the icon of a trash can on it. 
5. A confirmation screen will pop up to warn that this process cannot be undone. Click the **Delete** button on this screen.
6. Optionally, select the **Engine Groups** tab and delete the engine group for this engine.
[block:callout]
{
  "type": "danger",
  "title": "Note",
  "body": "Existing scan configs that use a deleted engine group will switch back to the **default** engine group and all their in-progress scans will be canceled."
}
[/block]