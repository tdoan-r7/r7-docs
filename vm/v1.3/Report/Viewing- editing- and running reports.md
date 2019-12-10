---
title: "Viewing, editing, and running reports"
excerpt: ""
---
You may need to view, edit, or run existing report configurations for various reasons:

* On occasion, you may need to run an automatically recurring report immediately. For example, you have configured a recurring report on Microsoft Windows vulnerabilities. Microsoft releases an unscheduled security bulletin about an Internet Explorer vulnerability. You apply the patch for that flaw and run a verification scan. You will want to run the report to demonstrate that the vulnerability has been resolved by the patch.
* You may need to change a report configuration. For example, you may need add assets to your report scope as new workstations come online.

The application lists all report configurations in a table, where you can view run or edit them, or view the histories of when they were run in the past.
[block:callout]
{
  "type": "info",
  "body": "On the _View Reports_ panel, you can start a new report configuration by clicking the **New** button."
}
[/block]
To view existing report configurations, take the following steps.

1. Click the **Reports** icon that appears on every page of the Web interface. The Security Console displays the _Reports_ page.
2. Click the **View reports** panel to see all the reports of which you have ownership. A Global Administrator can see all reports.

A table list reports by name and most recent report generation date. You can sort reports by either criteria by clicking the column heading. Report names are unique in the application.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/8a2edfd-s_Report_page_view_report_history.jpg",
        "s_Report_page_view_report_history.jpg",
        1782,
        652,
        "#dce2e5"
      ],
      "caption": "The View Reports panel"
    }
  ]
}
[/block]
To edit or run a listed report, hover over the row for that report, and click the tool icon that appears.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/13a70a5-s_report_tools.jpg",
        "s_report_tools.jpg",
        1778,
        654,
        "#dce4e8"
      ],
      "caption": "Accessing report tools"
    }
  ]
}
[/block]
* To run a report, click **Run**.
Every time the application writes a new instance of a report, it changes the date in the _Most Recent Report_ column. You can click the link for that date to view the most recent instance of the report.
* You also change a report configuration by clicking **Edit**.
* Or you can copy a configuration by clicking **Copy** on the tools drop-down menu for the report. Copying a template allows you to create a modified version that incorporates some the original template’s attributes. It is a quick way to create a new report configuration that will have properties similar to those of another.

For example, you may have a report that only includes Windows vulnerabilities for a given set of assets. You may still want to create another report for those assets, focusing only on Adobe vulnerabilities. Copying the report configuration would make the most sense if no other attributes are to be changed.

Whether you click **Edit** or **Copy**, the Security Console displays the **Configure a Report** panel for that configuration. See [Creating a basic report](doc:creating-a-basic-report).

* To view all instances of a report that have been run, click **History** in the tools drop-down menu for that report. You can also see the history for a report that has previously run at least once by clicking the report name, which is a hyperlink. If a report name is not a hyperlink, it is because an instance of the report has not yet run successfully. By reviewing the history, you can see any instances of the report that failed.
* Clicking **Delete** will remove the report configuration and all generated instances from the application database.

#Delete a Running Report
**To delete a running report:**
1. Select **Reports** from the left hand menu.
2. To the left of the report, hover your mouse to reveal the "Settings" icon.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/5f4fbfa-2.png",
        "2.png",
        512,
        126,
        "#e0e8ed"
      ]
    }
  ]
}
[/block]
3. Select the **History** option.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/7441e88-1.png",
        "1.png",
        1600,
        155,
        "#f8f9fb"
      ]
    }
  ]
}
[/block]
4. Click the **Trash** icon to delete the running report.

#Stop a Report from Generating
You can stop a running report from completing by doing the following:
1. On the left hand menu, select the **Reports** page.
2. Select the **View Reports** option.
3. Hover over the desired report to reveal the options.
4. Click on the **Settings** gear icon on the left and click the **History** option.
5. Click on the **trash** icon on the right to stop the report from generating.