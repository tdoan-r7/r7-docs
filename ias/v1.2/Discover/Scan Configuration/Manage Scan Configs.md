---
title: "Manage Scan Configs"
excerpt: ""
---
You can perform operations like copying and deleting your scan configurations from the “Scan Configs” screen of an app. 

#Copy Scan Config
You spend a considerable amount of time refining scan configs to ensure scans have the desired coverage, have the correct auth credentials, and run as quickly as possible. Once you have done this, you may want to scan the targets with a different attack module, or scan a different area of your web application with the same settings. 

InsightAppSec allows you to create a copy of an existing scan config and reuse the settings with minor modifications. 
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/916df68-Copy_Scan_Config.png",
        "Copy Scan Config.png",
        1680,
        562,
        "#3d4a55"
      ]
    }
  ]
}
[/block]
To copy a scan config:
1. Navigate to **All Apps** and select the app you wish to scan.
2. On the app screen, select the **Scan Configs** tab.
3. In the “Scan Configs” table, select the row with the scan config you want to copy, then click the **Copy scan config** button. 
4. The “Copy Scan Config” screen will appear. The “Scan Config Name” will default to the name of the original scan config with “ (Copy)” added to the name. Modify this name if you like.
5. Optionally add a description with the purpose of this scan config.
6. Click the **Save Copy** button. The new scan config will appear in the “Scan Configs” table.

#Delete Scan Config
You may want to delete scan configs if the associated target has been removed or the web application settings have drastically changed.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/a71a1ed-Delete_Scan_Config.png",
        "Delete Scan Config.png",
        1690,
        580,
        "#3f4c57"
      ]
    }
  ]
}
[/block]
To delete a scan config:
1. Go to **All Apps** and select the app with the obsolete scan config.
2. On the app screen, select the **Scan Configs** tab.
3. In the “Scan Configs” table, select the row with the scan config you want to delete, then click the **Delete scan config** button. 
4. You will see a warning that the delete process cannot be undone. If you are certain about deleting the scan config, click the **Delete** button. The scan config will disappear from the “Scan Configs” table.