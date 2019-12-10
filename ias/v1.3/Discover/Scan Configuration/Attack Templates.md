---
title: "Attack Templates"
excerpt: ""
---
[Attack templates](doc:concepts#section-attack-template) are pre-configured sets of attacks and performance options. InsightAppSec comes with a set of pre-built default attack templates based on common requirements of application security professionals. Click on the "View Details" button beside the name of any template to examine the attacks and configurations included with that template. 
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/7907921-Screen_Shot_2018-03-18_at_11.58.33_PM.png",
        "Screen Shot 2018-03-18 at 11.58.33 PM.png",
        3548,
        1738,
        "#43505a"
      ]
    }
  ]
}
[/block]
## Default attack templates
The default attack templates are as follows:
* All modules - Enables all [attack modules](doc:attack-modules). This template provides the most comprehensive coverage of vulnerabilities but also requires the most resources. If possible, you should host you application locally when using this attack template so that it does not affect the performance of customer-facing websites. 
* Crawl only - Deselects all attack modules. This template is useful to understand the topology of your app and make an inventory of all the web pages in it. You can can either run an unauthenticated crawl scan to discover all the public facing resources of your app, or an authenticated scan to list all the internal as well as external resources. Clicking the Crawl Map button on the Scan page reveals the topology of the app discovered through the scan. 
* OWASP 2013 - Enables attacks related to the most critical web application security risks listed in the [OWASP 2013](https://www.owasp.org/index.php/Top_10_2013-Top_10) report. 
* Passive analysis - Enables only [passive analysis modules](doc:concepts#section-passive-attack-module).
* SQL Injection - Includes all [SQL Injection](https://www.owasp.org/index.php/SQL_Injection) related attacks.
* XSS - Enables all attacks related to [Cross-site Scripting](https://www.owasp.org/index.php/Cross-site_Scripting_%28XSS%29). 
* SQL Injection and XSS - In many real-life scenarios, attackers use a combination of SQL Injection and Cross-site scripting vulnerabilities to gather sensitive data from your application. This template gives you an overall picture of such vulnerabilities in your application. 

You can manage existing attack templates and create new templates from the **Administration** page.