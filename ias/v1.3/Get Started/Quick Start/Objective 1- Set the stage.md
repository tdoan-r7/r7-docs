---
title: "Objective 1: Set the stage"
excerpt: ""
---
An [App](doc:concepts#section-apps) in InsightAppSec is a section of your site that you want to scan and manage. Apps allow you to tune scans consistently for several targets in a single grouping, group scan results into one place, and track improvements over time. 

When you log in to InsightAppSec for the first time, you can choose to scan your own domain or a pre-configured Rapid7 app. Scanning pre-configured vulnerable apps can help you explore the capabilities of InsightAppSec, while scanning your own domain helps you ensure that InsightAppSec is the right security tool for your technology stack. Before you can start scanning your own application, you’ll need to validate your application’s domain. This requires adding a custom-generated meta tag to your application’s root path. Trial users can scan one verified domain.

## Add an app with your own domain

1. On the first time welcome page, select the **Scan my own domain** option. 
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/be713f0-Appsec1.png",
        "Appsec1.png",
        975,
        627,
        "#37414a"
      ]
    }
  ]
}
[/block]
2. When the "Add New App" wizard appears, enter a name and description for your new app and click the **Target Domains** button.
3. Enter the URL of the domain you would like to scan. Be sure to include the protocol for the URL, such as http or https.
4. Click the **Save** button to add the domain to this app. Next, click the **Users** button to proceed to the next screen.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/02167d1-Screen_Shot_2018-03-19_at_5.31.01_AM.png",
        "Screen Shot 2018-03-19 at 5.31.01 AM.png",
        1518,
        1228,
        "#4c5a65"
      ]
    }
  ]
}
[/block]
5. On the "Users" tab of the wizard, select the users you want to access this app. Click the **Add New App** button.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/4187eea-Screen_Shot_2018-03-16_at_8.26.20_PM.png",
        "Screen Shot 2018-03-16 at 8.26.20 PM.png",
        1512,
        1536,
        "#4b5863"
      ]
    }
  ]
}
[/block]
6. You’ll now be asked to validate the domain. You will need to add a custom-generated meta tag below the < head > tag in the HTML code of your application’s base directory index page. The index page is the page that appears by default (e.g. index.html, default.aspx) at the URL you are testing. 
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/aa17975-Appsec-2.png",
        "Appsec-2.png",
        975,
        621,
        "#364049"
      ]
    }
  ]
}
[/block]
7. After you have added the meta tag to the index page, click the **Verify URL** button to finish adding your app. 

## Add a Rapid7 app

1. On the first time welcome page, select the **Scan a Rapid7 domain** option.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/d9560cd-Screen_Shot_2018-03-16_at_8.07.48_PM.png",
        "Screen Shot 2018-03-16 at 8.07.48 PM.png",
        1510,
        1232,
        "#4f5e69"
      ]
    }
  ]
}
[/block]
2. When the Add New App wizard appears, select the app you would like to scan and click the **Users** button.  
3. On the "Users" tab of the wizard, select the users you want to access this app.. Click the Add New App button to finish adding your App. 

After your app has been added, you will be taken to the "Scan Config" page, where you can configure your scanning preferences for your application.