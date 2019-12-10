---
title: "Set Up an On-Premise Scan Engine"
excerpt: ""
---
InsightAppSec uses a cloud-based engine to test applications that have been deployed to the public domain and are accessible from the internet. For applications that are not accessible from the internet, you can set up an on-premise scan engine. The on-premise scan engine will scan the applications that the cloud engines cannot reach and will send the data back to InsightAppSec. This allows you to easily scan your internal applications without publicly exposing them or making major modifications to your internal environment. 

To facilitate communication between InsightAppSec and an on-premise engine, the installation process includes an agent, which regularly checks to see if there are jobs for the scan engine to perform, such as running a scan or updating the engine. 

To set up an on-premise engine, check your [system requirements](doc:setting-up-an-on-premise-scan-engine#section-system-requirements) and follow the steps below.

## System Requirements

Before you can set up a scan engine, you must verify the following:

* The machine you're installing the engine on meets the hardware, operating system, and browser requirements. 
* The machine you're installing the engine on can reach InsightAppSec at:
  * https://us.appsec.insight.rapid7.com if your platform account is hosted in the United States.
  * https://eu.appsec.insight.rapid7.com if your platform account is hosted in the EU.
  * https://ca.appsec.insight.rapid7.com if your platform account is hosted in Canada.
  * https://au.appsec.insight.rapid7.com if your platform account is hosted in Australia.
* If the system is behind a firewall that restricts access to the internet, you'll need to add the domain to the firewall's whitelist. 
* You are a platform or product administrator.  

### Hardware Requirements
* 6GB of RAM
* 50GB of disk space
* 4 CPU cores (recommended)
* 1 network interface

### Supported Operating Systems 
Windows NT versions 6.1-10.0, which includes:
* Windows Server 2008 R2 
* Windows 7
* Windows 8
* Windows Server 2012
* Windows 8.1
* Windows Server 2012 R2
* Windows Server 2016   
* Windows 10 

[block:callout]
{
  "type": "info",
  "title": "Note",
  "body": "You will not be able to install the on-premise engine on versions of Windows older than 6.1. The installation may work on newer versions of Windows, but you will receive a warning that it will not be officially supported by Rapid7."
}
[/block]
### Browser Requirements
* Internet Explorer 11 or higher

## Step 1: Download the Installer

1. Log in to http://insight.rapid7.com/ and go to InsightAppSec. 
2. From InsightAppSec, go to **Settings > Manage Scan Engines**.
3. Click **Set Up New Scan Engine**. 
4. From the "Setup New Scan Engine" panel, download the installer.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/d28bc59-download.jpg",
        "download.jpg",
        596,
        808,
        "#444d5c"
      ]
    }
  ]
}
[/block]
## Step 2: Copy the API Key

The API Key is used to validate that your organization has access to InsightAppSec and there is a scan engine that is ready to be paired. 

Copy the API key shown in step 3 from the "Setup New Scan Engine" panel. You'll need to have the API key available when you run the installer.  
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/75fe73c-api.jpg",
        "api.jpg",
        596,
        808,
        "#454d5c"
      ]
    }
  ]
}
[/block]
## Step 3: Name the Engine

This step is straightforward: enter a name for the scan engine. 
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/39e3d69-scan-engine-name.jpg",
        "scan-engine-name.jpg",
        601,
        812,
        "#444d5c"
      ]
    }
  ]
}
[/block]

[block:callout]
{
  "type": "info",
  "body": "You can reuse names for scan engines. The API key will act as the unique key for the scan engine. However, to help you easily identify a scan engine, you should give it a descriptive, unique name.",
  "title": "Note"
}
[/block]
## Step 4: Prepare the Engine for Pairing

After you copy the API key and name the scan engine, you're ready to  pair it. During the pairing process, the new scan engine waits for the on-premise engine to come online so that they can be paired.

Click **Pair Now** at the bottom of the "Setup New Scan Engine" panel. 
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/18f2f76-pair-now.jpg",
        "pair-now.jpg",
        601,
        812,
        "#444d5c"
      ]
    }
  ]
}
[/block]
A new scan engine will be added to the "Manage Scan Engines" page with a status of "Status Unknown."
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/95f5a99-status-unknown.jpg",
        "status-unknown.jpg",
        1356,
        381,
        "#3b434f"
      ]
    }
  ]
}
[/block]
## Step 5: Run the Installer

The installer provides step-by-step instructions, so you just need to run the installer and follow the prompts.

During installation, the installer verifies that the system meets the minimum requirements and validates that the engine can connect with the Insight platform. If it cannot reach the Insight Platform, you can configure a proxy for the installer to use. 

After the installer performs the system checks, it'll prompt you for an API key, which will be used to validate your organization and verify that there is a scan engine ready to be prepared. You'll need to provide the API key you copied earlier. 

When the installation completes, you'll need to go back to the "Manage Scan Engines" page in InsightAppSec. 

## Step 6: Refresh Manage Scan Engines page

When the installation completes, the status of the new on-premise engine changes from "Status Unknown" to "Idle," which indicates that it has successfully paired and is ready for tasks. You'll need to refresh the page to see the status change. 

## Step 7: Use the New Scan Engine

The scan engine is now set up. You're ready to start using the scan engine. 

To get started, you can select the scan engine for new scan configs or you can update existing scan configs to use the new scan engine. 

To update your existing scan configs, go to Apps > Scan config > Engines. You can choose the new scan engine from the list of on premise scan engines. 

Once you have selected an on-premise scan engine for a scan config, the agent will regularly contact InsightAppSec to see if there are tasks, such as scans or engine updates, that need to be performed. 

## Step 8: Scan Your Apps

You're all done! You're now ready to scan your apps.