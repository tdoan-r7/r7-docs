---
title: "Scan your App"
excerpt: ""
---
Once you are familiar with InsightAppSec and have a good understanding of the topology of your application, you can start targeting various sections of your application to search for vulnerabilities. It is recommended to start with the "All modules" [attack template](doc:attack-templates) which covers all modules and provides maximum coverage. This will give you a broad understanding of the security posture of your app, and you can subsequently shape your scans using the various options available in the [Scan Config](doc:scan-configuration) wizard.

##Monitor active scans

In order to scan an app, go to the "All Apps" screen and click on the app you would like to scan. On the App Overview page, click the **Scan Now** button on the top right hand side of the screen, and select the scan config you wish to use. 
You will see a message about the scan starting successfully, with a link to the Scan Overview page. The Scan Overview page is structured differently based on whether the scan is in progress or completed. If the scan is in progress, the page shows the "Scan Status" view which has two tabs:
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/e8be8f7-Screen_Shot_2018-03-19_at_7.52.42_AM.png",
        "Screen Shot 2018-03-19 at 7.52.42 AM.png",
        3716,
        1782,
        "#3e4953"
      ]
    }
  ]
}
[/block]
* Vulnerabilities per attack - This tab is useful for a live snapshot of the vulnerabilities being discovered on your app. 
* Event Log - The Event log lists in real time, the actions taken by the InsightAppSec console as part of the scan, and can help you detect authentication or access failures early in the scan. For example, imagine you have an app that takes a few hours to scan and is scheduled to be scanned after business hours. You can follow the scan log at the beginning of the scan to ensure that InsightAppSec can correctly access your app, and that the scan results will be useful to your team the next day.

##View Scan Results
When the scan is completed, the Scan Overview page uses the Scan Results layout. The KPIs are displayed at the top while the scan information and the Vulnerabilities table is displayed below.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/34fa563-Screen_Shot_2018-03-19_at_8.28.16_AM.png",
        "Screen Shot 2018-03-19 at 8.28.16 AM.png",
        3678,
        1656,
        "#45505a"
      ]
    }
  ]
}
[/block]
Click on any vulnerability in the table to view attack details and remediation ideas. More guidance on analysing vulnerabilities is available in the [Work with Vulnerabilities](doc:work-with-vulnerabilities)  help article. You can also use this page to [export vulnerabilities to JIRA](doc:ticketing-integration) and to [generate reports](doc:generate-reports).

## Monitor Scanning Activity across Apps

The Scanning Activity screen provides an overview of the app scanning activity in your portfolio. You can use this screen to quickly learn about the status of active scans as well as the high-level results (vulnerability count, risk level) of past scans. You can use the date range filter to focus on scans that occurred between a certain time period, and use the scan activity chart to learn about scanning trends in your portfolio. 
If you are interested in scan results for a specific app, you can click on the app name in the Scanning Activity table, or visit the Apps tab. You can also click on a scan name to bring up individual scan details. 
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/7138728-Screenshot-2017-11-21_InsightAppSec.png",
        "Screenshot-2017-11-21 InsightAppSec.png",
        1855,
        957,
        "#39444c"
      ],
      "caption": "The Scanning Activity screen provides an overview of past and active scans"
    }
  ]
}
[/block]