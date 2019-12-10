---
title: "Running the Linux uninstaller"
excerpt: ""
---
Each copy of InsightVM must be installed from scratch. This means that if you already have it installed on your system, you must uninstall it before you install the new copy you downloaded.
[block:callout]
{
  "type": "danger",
  "body": "To prevent a loss of sites, configurations, reports, and other data, make sure you back up all of your data before you begin the procedure."
}
[/block]
Uninstalling completely removes all components. It also deletes sites, configurations, reports, and any scan data on discovered assets, nodes, and vulnerabilities.

To uninstall the application, take these steps:
1. Run: ```$ cd [installation directory]/.install4j```
```install4j``` is a hidden directory. To list hidden directories, run: ```ls -a```.
2. Run: ```$./uninstall```