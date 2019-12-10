---
title: "Work with Vulnerabilities"
excerpt: ""
---
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
You can choose any of these views based on how your security team likes to analyse and address issues. 

##Filter vulnerabilities
You can also use the Filtering capability to focus on certain vulnerabilities, for example, high severity vulnerabilities in your banking app. InsightAppSec comes with two filters by default - High or Medium Severity vulnerabilities, and Unreviewed High Severity vulnerabilities.
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
A search filter allows you to choose the attributes of the assets that you are interested in. You can add multiple filters for more precise searches. A filter is made by comparing certain properties of vulnerabilities (e.g. severity, description) to a value or regular expression using one of the following operators:

* = (equals)
* != (does not equal)
* contains
* starts with
* ends with
* Like (regular expression)
* is null
* is not null

You can combine filters using the "AND" operator so that the search result set contains only the vulnerabilities that meet all of the criteria in all of the filters (leading to a smaller result set). Or you can combine filters using the "OR" operator so that the search result set contains vulnerabilities that meets any of the criteria in any given filter (leading to a larger result set).

A circle on the left side of the filters indicates whether the expression in the field is allowed or not. If the circle is red in colour, your filter is incomplete or incorrect. 

##Analyse vulnerabilities

Clicking on any vulnerability will display the vulnerability details in a panel on the right side of your screen. The top row in the panel displays general details about the vulnerability such as the name and severity of the underlying attack, the review status of the vulnerability and the time of its first and last appearance. You can also change the severity and status of the vulnerability from this area. You may wish to reduce the severity of a vulnerability if you have a compensating control for it, whereas you may wish to increase the severity if you feel that your industry is prone to attacks due to a certain vulnerability. For example, the "Sensitive Data Exposure" module has a severity rating of Low, but you may want to increase this if you work with a health care app which holds patient health information.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/acf4399-Screen_Shot_2018-03-18_at_8.55.31_PM.png",
        "Screen Shot 2018-03-18 at 8.55.31 PM.png",
        2240,
        2060,
        "#414d57"
      ]
    }
  ]
}
[/block]
The other sections of the vulnerability details panel are as follows:

###General
* App - Link to the app where the vulnerability was found.
* ID - A unique hexadecimal identifier for this instance of the vulnerability. 
* JIRA - An indicator of whether this instance of the vulnerability has been exported to JIRA or not. 
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/1cceeca-Screen_Shot_2018-03-19_at_10.05.20_AM.png",
        "Screen Shot 2018-03-19 at 10.05.20 AM.png",
        1386,
        324,
        "#45515b"
      ]
    }
  ]
}
[/block]
###Root Cause
* URL - The URL of the web resource where this vulnerability was found. 
* Parameter - the HTTP request parameter which was used for this attack.
* Method - The HTTP method, GET or POST, that was used to carry out this attack. 

###Attack Variances
InsightAppSec may attempt multiple variations of the same attack on a URL to ensure your security of your applications against a variety of attacks. For example, you may have protected your application against certain special characters in web forms, but not others. The Attack Variances section contains multiple tabs for each variation of an attack attempted by InsightAppSec.

In each Attack tab, you will find the following details:

* Description - Description of the variation of the attack being attempted.
* Original value - The original non malicious value of the parameter, which is used to observe normal behaviour of the app
* Attack value - A specially crafted value which is supposed to make the app behave abnormally
* Error - The error message from the application, or a description of the error encountered by the app
* Original traffic - A snapshot of the HTTP request sent to the app and the response received in the normal case
* Attack traffic - A snapshot of the HTTP request sent with the attack value in the parameter, and the resulting erroneous response

###Description
This section provides details about the vulnerability and recommendations on how to solve it. You will also find links to references from industry standard councils such as NIST, OWASP, DISA which you can use to gather more information about the vulnerability.

###Discovery history
This table shows a list of all the scans where this vulnerability has been found in your environment.