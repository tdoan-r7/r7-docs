---
title: "Common Use Cases"
excerpt: ""
---
## Creating your App

[Apps](doc:concepts#section-apps) are a way to group your targets together, which in turn allows you to tune scans consistently for all targets in a single grouping, to group results into one place, and to track improvements over time. Start by clicking the **Add App** button on the *All Apps* screen which will reveal the *Add App Wizard*. You can use this wizard to set App-level configurations such as base URLs and users.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/423c170-Add_app_wizard.png",
        "Add app wizard.png",
        1598,
        1358,
        "#44535c"
      ],
      "caption": "Choose target URLs from a set of whitelisted domains"
    }
  ]
}
[/block]
On the Target URLs step, use the **+** button to add individual URLs, or click on the **Bulk Add URLs** link to add multiple URLs, e.g. to copy a list of URLs from an external document.  
From the Users step, you can assign users to a particular App. 
Completing the wizard takes to the home page inside the App, where your next step is to create a [Scan Configuration](doc:scan-configuration).

## Running your first scan

Before you start scanning specific sections of your app for vulnerabilities, it is useful to understand the topology of your app and make an inventory of all the web pages in it. The 'Crawl Only' scan template available by default in the [Scan Configuration](doc:scan-configuration) can help you achieve this. You can can either run an unauthenticated crawl scan to discover all the public facing resources of your app, or an authenticated scan to list all the internal as well as external resources. Clicking the **Crawl Map** button on the Scan page reveals the topology of the app discovered through the scan. 

## Following the Event Log

When scanning your application, you can follow the Event Log by clicking the button on the Scan page. The Event log lists in real time, the actions taken by the InsightAppSec console as part of the scan, and can help you detect authentication or access failures early in the scan. 
For example, imagine you have an app that takes a few hours to scan and is scheduled to be scanned after business hours. You can follow the scan log at the beginning of the scan to ensure that InsightAppSec can correctly access your app, and that the scan results will be useful to your team the next day.

## Finding Vulnerabilities

Once you are familiar with the tool and have a good understanding of the topology of your application, you can start targeting various sections of your application to search for vulnerabilities. It is recommended to start with the Default scan template which covers all modules and provides maximum coverage. This will give you a broad understanding of the security posture of your app, and you can subsequently shape your scans using the various options available in the [Scan Config](doc:scan-configuration) wizard.

## Analysing Vulnerabilities

InsightAppSec allows you to view your vulnerabilities at the Organization level, the App level, or the Scan level. The organizational view can be seen by clicking on the **All Vulnerabilities** tab on the left navigation bar. If you are viewing a specific app, the **Vulns** tab will show you all the vulnerabilities for that app, while clicking on a scan from the **Scans** tab will show you all the vulnerabilities found in that particular scan. 
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/c2f70b5-Scan_level_vulns.png",
        "Scan level vulns.png",
        3448,
        338,
        "#45515b"
      ],
      "caption": "Analyzing Scan level vulnerabilities from the Scans tab"
    }
  ]
}
[/block]
You can choose any of these views based on how your security team likes to analyse and address issues. You can also use the Filtering capability to focus on certain vulnerabilities, for example, high severity vulnerabilities in your *Banking* app. 
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/89fa7c7-Filtering_vulnerabilities.png",
        "Filtering vulnerabilities.png",
        3520,
        1060,
        "#4c5b66"
      ],
      "caption": "Filtering high severity SQL vulnerabilities"
    }
  ]
}
[/block]
## Monitoring Scanning Activity

The Scanning Activity tab provides an overview of the app scanning activity in your portfolio. You can use this screen to quickly learn about the status of active scans as well as the high-level results (vulnerability count, risk level) of past scans. You can use the date range filter to focus on scans that occurred between a certain time period, and use the scan activity chart to learn about scanning trends in your portfolio. 
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
The Scanning Activity screen allows you to track active scans through various phases, which can be described as follows:

  * **Pending** - The scan has been kicked off by the console but the engine has not started scanning.
  * **Running** - The engine is actively scanning your application.
  * **Scanned** - The engine has finished scanning your application, and is now processing the results.
  * **Processed** - InsightAppSec has processed the scan results and is now generating scan reports.
  * **Complete** - Your app scan has completed successfully and the results are ready for you.
  * **Paused** - The scan has been paused.
  * **Blacked Out** - Your scan overlapped with a Blackout period scheduled in the calendar. If your scan had not started, it will begin after the blackout period is over. If the scan was active, it will be paused. 
  * **Failed** - Your scan could not be completed successfully. Please check the Event Log and the Platform Event Log for more information. 

## Sharing action items with your team

InsightAppSec allows you to export vulnerability reports in the CSV or PDF formats. The export feature respects any filtering applied to your vulnerabilities table. You can choose the format and level of detail visible in the reports based on your audience. For example, your developers may like a CSV report so they can import the vulnerabilities into their bug tracking system and follow the progress of the remediation projects. On the other hand, organizational leadership may be more interested in the overall trend of vulnerabilities for which a high-level PDF report would be more useful.