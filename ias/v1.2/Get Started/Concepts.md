---
title: "Concepts"
excerpt: ""
---
# Apps

An app is a section of your site that you want to scan  and manage as a piece. You can specify multiple URLs to be included in an app that will apply across all scan configurations. Use the **+** button to add the URL, and you will then see it appear in the URLs list on the *Add URLs* tab.  
Creating an app is a key starting point for performing other actions in the application.

# Scan Configuration

A scan configuration is a group of settings you can use to scan an app, or certain URLs within an app, for vulnerabilities. You can create multiple scan configs in order to suit different needs at different times.

# Scan Status

The Scan Status field helps you track active scans through various phases which can be described as follows: 
  * **Pending** - The scan has been kicked off by the console but the engine has not started scanning.
  * **Running** - The engine is actively scanning your application.
  * **Scanned** - The engine has finished scanning your application, and is now processing the results.
  * **Processed** - InsightAppSec has processed the scan results and is now generating scan reports.
  * **Complete** - Your app scan has completed successfully and the results are ready for you.
  * **Paused** - The scan has been paused.
  * **Blacked Out** - Your scan overlapped with a Blackout period scheduled in the calendar. If your scan had not started, it will begin after the blackout period is over. If the scan was active, it will be paused. 
  * **Failed** - Your scan could not be completed successfully. Please check the Event Log and the Platform Event Log for more information. 

# Domain

A Domain is a website located on a certain port. Domain is identified by the name or IP address of website, its protocol and port. For instance, the following domains are different -
`https://localhost` and `http://localhost` because they have different protocols: HTTP and HTTPS. Also, the following domains are different - `http://localhost:8080` and `http://localhost:80` because they have different ports: 8080 and 80.

# Blackout

A blackout is a period of time when all scanning activities for a host are stopped. You can assign a blackout to a specific app, or create a Global blackout which stops all scanning activities on all your apps. 

# Attack template

An attack template is set in a scan configuration and determines which types of attacks will be run against your app during a scan. You can select from several preconfigured attack templates or create your own.

# Active Attack Module

An active attack module attempts to alter your application by running attacks for well-known vulnerabilities (e.g. inserting SQL in forms).

# Passive Attack Module

A passive attack module attempts to gain information about your environment by examining your application (e.g. looking for passwords stored in clear text).

# Macros

Macros are recordings of some action that cannot be otherwise automated, such as logging in on certain types of pages. You can store a macro in your scan configuration in order to perform these actions. Since InsightAppSec runs on the Rapid7 platform, you will need to use an extension for Google Chrome to record and deploy macros.

# Vulnerabilities

Vulnerabilities are aspects of your app that can make it vulnerable to attackers. For example, malformed SQL code can make your app vulnerable to SQL injection attacks. The application reports on the details of a vulnerability so you can learn how to remediate it and improve the security of your application.

The vulnerabilities page in the application displays the latest data from your most recent scans.

The vulnerability details displayed in InsightAppSec display information such as the vulnerability age and severity that you can use to determine the priority of the vulnerability. You can also dig deeper to view the request and response that the application used to determine the vulnerability was present.

# Remediations

A remediation is an action you or your application development team make to resolve a vulnerability. When the update is made and you scan again, the application should no longer show as vulnerable to that particular attack.