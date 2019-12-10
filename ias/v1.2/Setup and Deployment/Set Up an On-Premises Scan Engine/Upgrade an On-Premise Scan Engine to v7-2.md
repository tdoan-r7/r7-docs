---
title: "Upgrade an On-Premise Scan Engine to v7.2"
excerpt: ""
---
The <<product>> cloud scan engines were upgraded to version 7.2.041 on the 10th of December, 2018. Users with on-premise scan engines will also need to upgrade to the latest version, since the 7.2 version stream is incompatible with the older 7.0 versions. This article will help you upgrade your on-premise scan engines.
[block:callout]
{
  "type": "warning",
  "title": "Note",
  "body": "The engine upgrade process requires you to remove certain registry keys from the system. Before starting the upgrade process, please ensure that you are authorized to modify the system registry."
}
[/block]
You can upgrade an on-premise scan engine using the following steps:
1. [Uninstall](doc:uninstall-an-on-premise-scan-engine) the old scan engine by running the uninstaller in the InsightAppSec folder.
2. Open the registry editor tool `regedit` and remove the following registry subkeys if they exist on your system:
    * `HKEY_LOCAL_MACHINE\SOFTWARE\WOW6432Node\Rapid 7\AppSpider`
    * `HKEY_LOCAL_MACHINE\SOFTWARE\WOW6432Node\Rapid 7\AppSpider 7`
    * `HKEY_LOCAL_MACHINE\SOFTWARE\WOW6432Node\Rapid 7\InsightAppSec`
3. Visit [InsightAppSec](https://insight.rapid7.com) in your browser and open the **Settings > Manage Scan Engines** screen. 
4. Locate the entry for the old scan engine and click on the **Name**. The "Set Up New Scan Engine" panel will appear. 
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/09357c3-set_up_new_scan_engine.png",
        "set up new scan engine.png",
        1166,
        1448,
        "#4e5964"
      ]
    }
  ]
}
[/block]
5. Click the **Download Engine Installer** button to download the engine installer to the system. 
6. Click the **Regenerate Key** button to create an API key for the new engine. Copy this API key since you will need it during engine installation.
7. [Run the installer](doc:setting-up-an-on-premise-scan-engine#section-step-5-run-the-installer) and follow the prompts. After the installer performs the system checks, it'll prompt you for an API key, which will be used to validate your organization and verify that there is a scan engine ready to be paired. You'll need to provide the API key you copied earlier.
8. When the installation completes, refresh the "Manage Scan Engines" page. Your engine should now show the status "Available".

You must perform these steps for every scan engine in the "Manage Scan Engines" table.