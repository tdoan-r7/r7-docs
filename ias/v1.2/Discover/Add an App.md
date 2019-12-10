---
title: "Add an App"
excerpt: ""
---
[Apps](doc:concepts#section-apps) are a way to group your targets together, which in turn allow you to tune scans consistently for all targets in a single grouping, to group results into one place, and to track improvements over time. In order to scan a web application, you will have to create an App and add the URLs of your application to this app.
[block:callout]
{
  "type": "info",
  "title": "Note",
  "body": "During an InsightAppSec scan, your web application may experience a high amount of incoming network traffic. Some firewalls may block attack traffic and prevent InsightAppSec from testing your application for vulnerabilities. In such cases, you must [whitelist the IP addresses](doc:whitelist-cloud-engine-ips) of the InsightAppSec cloud engines to scan your web applications."
}
[/block]
# Add an App with the Add App Wizard
1. Go to **Settings > Manage Attack Targets** and ensure that the domain you wish to scan is in the “Target Domains” list and the entry for the target domain is enabled. 
[block:callout]
{
  "type": "info",
  "title": "Note",
  "body": "If you wish to scan multiple subdomains of a website, such as `mail.mysite.com` and `blog.mysite.com`, you need to add them individually to this list. The “Target Domains” list does not accept URLs with wildcards such as `*.mysite.com`."
}
[/block]

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/f667c55-Manage_attack_targets.png",
        "Manage attack targets.png",
        1708,
        1460,
        "#46515a"
      ]
    }
  ]
}
[/block]
2. Go to the “All Apps” screen and click the **Add App** button to start the “Add App Wizard”. Provide a name and optionally a description for this app on the “Details” screen.
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
3. On the "Target URLs" step, use the **+** button to add individual URLs, or click on the **Bulk Add URLs** link to add multiple URLs.  
4. From the "Users" step, you can assign users to a particular App. 

Completing the wizard takes you to the home page inside the App, where your next step is to create a [Scan Configuration](doc:scan-configuration).