---
title: "Objective 1: Set the stage"
excerpt: ""
---
This article explains how to get started with InsightAppSec using a **free trial** account. After you receive your free trial confirmation email, you can sign in to InsightAppSec at https://insight.rapid7.com. 

During the free trial, you can scan one personal domain or Rapid7’s demo domains (http://www.webscantest.com/ and http://hackazon.webscantest.com/). You will see these options when you first sign in to InsightAppSec. 
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/86e6edc-Screen_Shot_2019-11-25_at_2.44.22_PM.png",
        "Screen Shot 2019-11-25 at 2.44.22 PM.png",
        1372,
        1138,
        "#444f58"
      ]
    }
  ]
}
[/block]
Scanning Rapid7’s pre-configured demo applications can help you explore the capabilities of InsightAppSec, while scanning your own domain helps you ensure that InsightAppSec is the right security tool for your technology stack. After you make your decision, consult the appropriate help section to:
  * [Scan your own domain](#section-scan-your-own-domain)
  * [Scan a demo domain](#section-scan-a-demo-domain)

# Scan Your Own Domain
You can scan one personal domain with a free trial account. Before you begin the scan, ensure that you meet the prerequisites in the next section. 

## Before You Begin
Before you can scan your own domain, you’ll need to validate your ownership of the domain. This requires you to add a custom-generated meta tag to your application’s root path. Ensure that you have access to modify the source code of web pages in the application you are going to scan. 

During an InsightAppSec scan, your web application may experience a high amount of incoming network traffic. Some firewalls may block attack traffic and prevent InsightAppSec from testing your application for vulnerabilities. In such cases, you must [whitelist the IP addresses](doc:whitelist-cloud-engine-ips) of the InsightAppSec cloud engines to scan your web applications.

## Scan Your Web Application
To scan your application:
1. On the welcome page, click the **Scan my Domain** button.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/bf3eb99-Screen_Shot_2019-12-01_at_8.45.01_PM.png",
        "Screen Shot 2019-12-01 at 8.45.01 PM.png",
        598,
        802,
        "#47525d"
      ]
    }
  ]
}
[/block]
2. When the "Set up target domain" wizard appears, enter the URL of the domain you would like to scan and press the **Enter** key. Be sure to select the right protocol for the URL, such as `http` or `https`.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/5956e2e-IAS-scan_my_domain-verify.png",
        "IAS-scan my domain-verify.png",
        1276,
        1122,
        "#4b555f"
      ]
    }
  ]
}
[/block]
3. You’ll now see a custom generated meta tag that you must place the `<head>` tag in the HTML code of your application’s index page. The index page is the page that appears by default (for example: index.html or default.aspx) at the URL you are testing. 
Click the **Copy** button to copy the meta tag to your clipboard. Insert the meta tag in the index page and redeploy your web application.
4. Click the **Verify** button. The InsightAppSec engine will access your web page and check for the presence of the meta tag. If the tag is found, the **Verify** button will say “Verified” in green and the **Run Scan** button will become clickable. 
5. Click the **Run Scan** button to start the scan. InsightAppSec will now provision a scan engine and initialize your scan. This process may take a few minutes. 
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/b37541c-Screen_Shot_2019-12-01_at_8.56.39_PM.png",
        "Screen Shot 2019-12-01 at 8.56.39 PM.png",
        1114,
        674,
        "#2d373e"
      ]
    }
  ]
}
[/block]
After your scan starts, InsightAppSec will take you to the [Scan Overview](scan-your-app#section-monitor-active-scans) page where you can monitor the scan's progress.
[block:callout]
{
  "type": "info",
  "title": "Note",
  "body": "During the free trial, InsightAppSec will scan your web application for [passive attack modules](doc:concepts#section-passive-attack-module) by default. After you become familiar with InsightAppSec, you can customize your scans to test for all attacks. We will learn how to customize scans in a subsequent lesson of this quick start guide."
}
[/block]
# Scan a Demo Domain
To scan a Rapid7 pre-configured vulnerable web application:
1. On the welcome page, click the **Scan a Demo Domain** button.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/3a9a00c-Screen_Shot_2019-12-01_at_9.03.07_PM.png",
        "Screen Shot 2019-12-01 at 9.03.07 PM.png",
        620,
        852,
        "#495560"
      ]
    }
  ]
}
[/block]
2. You will receive the option to scan either a basic site (http://www.webscantest.com/) or an ecommerce site (http://hackazon.webscantest.com/). Both of these websites are owned by Rapid7 and have been deliberately made vulnerable to test the features of your Dynamic Analysis Security Testing (DAST) tool. 
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/0df4f60-Screen_Shot_2019-12-01_at_9.16.33_PM.png",
        "Screen Shot 2019-12-01 at 9.16.33 PM.png",
        1304,
        968,
        "#3f4a53"
      ]
    }
  ]
}
[/block]
Select one of the sites and click the **Run Scan** button. InsightAppSec will now provision a scan engine and initialize your scan. This process may take a few minutes.

After your scan starts, InsightAppSec will take you to the [Scan Overview](doc:scan-your-app#section-monitor-active-scans) page where you can monitor the scan’s progress.