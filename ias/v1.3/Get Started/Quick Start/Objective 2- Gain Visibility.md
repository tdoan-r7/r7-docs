---
title: "Objective 2: Gain Visibility"
excerpt: ""
---
Now that we have created an app, we are ready to scan it. InsightAppSec enables you to minutely control the scope and thoroughness of your scan based on your requirements. These controls are available under the [Scan Configs](doc:scan-configuration) section of your app. 

##Scan an App
1. In the "All Apps" page, click on the name of your app.
2. Select the **Scan Configs** tab. 
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/924f53a-Screen_Shot_2018-04-16_at_7.38.16_AM.png",
        "Screen Shot 2018-04-16 at 7.38.16 AM.png",
        1878,
        854,
        "#3b454c"
      ]
    }
  ]
}
[/block]
3. If you are scanning a Rapid7 app, you will find a pre-built scan config called "recommended-*<name of app>*". Click the scan button in the last column to begin scanning. 
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/2727401-Screen_Shot_2018-03-16_at_2.48.43_AM.png",
        "Screen Shot 2018-03-16 at 2.48.43 AM.png",
        1460,
        676,
        "#44525e"
      ]
    }
  ]
}
[/block]
If you are scanning your own application, click the **Create New Scan Config** button. The Scan Configuration wizard will appear. Refer to the articles in the [Scan Configuration](doc:scan-configuration) section for details about this wizard.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/a35ce31-Screen_Shot_2018-03-19_at_6.20.25_AM.png",
        "Screen Shot 2018-03-19 at 6.20.25 AM.png",
        3718,
        1438,
        "#47525a"
      ]
    }
  ]
}
[/block]
  i. Provide a name and description for the scan configuration. 
  ii. Set the [Scan Scope](doc:scan-scope) which includes settings like the maximum number of pages to crawl, URLs to include or exclude from the scan, as well as parameters to include or exclude from the scan. If you are testing the tool on a customer facing application, it would be useful to either use a low number of links to crawl or restrict your testing to a small subsection of the site using wildcards. 
  iii. Add your [authentication credentials](doc:authentication) if certain parts of the app are visible only after logging in.
  iv. Select an [attack template](doc:attack-templates). For the first scan, we recommend using the "Crawl Only" template to make an inventory of the publicly visible resources on your web application. You can then focus on a smaller subsection of the app to run more comprehensive tests such as the "All modules" template.
  v. Click the **Save** button to save the template. You can then create [Schedules and Blackouts](doc:schedules-and-blackouts) to control the timing of scans around other activity in your network.
  vi. Click the **Scan Now** button on the top right corner of the screen and choose your newly created scan configuration.

##Monitor scan activity

The App Overview page lists all the scans for any app. Clicking on a Scan name will take you to the Scan Overview page. When the scan is in progress, this page displays a live count of discovered vulnerabilities, and on scan completion it provides a list of all the vulnerabilities discovered in the scan. Take a look at the [scanning](doc:scan-your-app) help guide to learn more.