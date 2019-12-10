---
title: "Objective 3: Extract Insights"
excerpt: ""
---
Having run your first scan, you can now [examine the vulnerabilities](doc:work-with-vulnerabilities) discovered by InsightAppSec. There are three ways to check your vulnerabilities - at the Organization level, the App level, or the Scan level. If you visit the Scan Results page, you will be able to view the vulnerabilities found in the scan using the Live Vulnerability View. You can try the two built-in filters to learn about vulnerability filtering, or create your own.
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
Clicking on any vulnerability will open a panel with details such as the affected URL, HTTP Method (GET or POST), attack type, and attack value. You can also compare the response of a normal request against a malicious request to your app. Consult the documentation regarding [working with vulnerabilities](doc:work-with-vulnerabilities) for more details.