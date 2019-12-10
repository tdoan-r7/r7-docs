---
title: "Set Up an On-Premises Scan Engine"
excerpt: ""
---
InsightAppSec uses a cloud-based engine to test applications that have been deployed to the public domain and are accessible from the internet. For applications that are not accessible from the internet, you can set up an on-premise scan engine. The on-premise scan engine will scan the applications that the cloud engines cannot reach and will send the data back to InsightAppSec. This allows you to easily scan your internal applications without publicly exposing them or making major modifications to your internal environment. 

To facilitate communication between InsightAppSec and an on-premise engine, the installation process includes an agent, which regularly checks to see if there are jobs for the scan engine to perform, such as running a scan or updating the engine. 

#Scan Engine Groups
On-premise scan engines are organized in InsightAppSec using scan engine groups. Scan engine groups are collections of scan engines with similar network configurations that can be used to scan a web application. When creating a [Scan Config](doc:scan-configuration), you can choose an on-premise scan engine group. During the scan, InsightAppSec will find the first available engine from the group and use it to scan your app. 

[block:callout]
{
  "type": "info",
  "title": "Note",
  "body": "Scan engines in the same group should all have similar infrastructure and network access so they can be interchangeably used to scan your application."
}
[/block]
##Create a Scan Engine Group
InsightAppSec has a built-in scan engine group called "Default". You can also create custom scan engine groups using the following steps:
1. Log in to http://insight.rapid7.com/ and go to InsightAppSec.
2. From InsightAppSec, go to Settings > Manage Engines.
3. Select the “Engine Groups” tab.
4. Click the **+** button in the first row of the “Engine Groups” table.
5. Add a name and description that would let you easily identify the purpose of this engine group and press “Enter.” 

You should now see your custom engine group in the table with zero engines assigned to it. You can proceed to install an on-premise scan engine and assign it to an engine group. 

#Set Up an On-Premise Scan Engine

To set up an on-premise engine, check your [system requirements](doc:setting-up-an-on-premise-scan-engine#section-system-requirements) and follow the steps below.

## System Requirements

Before you can set up a scan engine, you must verify the following:

* The machine you're installing the engine on meets the hardware, operating system, and browser requirements. 
* The machine you're installing the engine on can reach InsightAppSec at:
  * https://us.appsec.insight.rapid7.com and https://us.engines.appsec.insight.rapid7.com if your platform account is hosted in the United States.
  * https://eu.appsec.insight.rapid7.com and https://eu.engines.appsec.insight.rapid7.com if your platform account is hosted in the EU.
  * https://ca.appsec.insight.rapid7.com and https://ca.engines.appsec.insight.rapid7.com if your platform account is hosted in Canada.
  * https://au.appsec.insight.rapid7.com and https://au.engines.appsec.insight.rapid7.com if your platform account is hosted in Australia.
  * https://ap.appsec.insight.rapid7.com and https://ap.engines.appsec.insight.rapid7.com if your platform account is hosted in Japan.
* If the system is behind a firewall that restricts access to the internet, you'll need to add the domain to the firewall's whitelist. 
* You are a platform or product administrator.  

### Hardware Requirements
* 6GB of RAM
* 50GB of free disk space (after OS installation)
* 4 CPU cores (recommended)
* 1 network interface

### Supported Operating Systems 
The scan engine can be installed on 64-bit Windows NT versions 6.2-10.0, which includes:
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
  "body": "You will not be able to install the on-premise engine on versions of Windows older than 6.2. The installation may work on newer versions of Windows, but you will receive a warning that it will not be officially supported by Rapid7."
}
[/block]
### Software Requirements
* The latest version of 64-bit Java Runtime pre-installed on the system
* Internet Explorer 11 or higher

## Step 1: Download the Installer

1. Log in to http://insight.rapid7.com/ and go to InsightAppSec. 
2. From InsightAppSec, go to **Settings > Manage Engines**.
3. Click **Set Up New Engine**. 
4. From the "Set Up New Engine" panel, download the installer.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/da911c1-Screen_Shot_2019-03-07_at_4.32.17_PM.png",
        "Screen Shot 2019-03-07 at 4.32.17 PM.png",
        1298,
        1754,
        "#4f5b65"
      ]
    }
  ]
}
[/block]
## Step 2: Copy the API Key

The API Key is used to validate that your organization has access to InsightAppSec and an available scan engine is ready to be paired. 

Copy the API key shown in Step 3 from the "Setup New Engine" panel. You'll need to have the API key available when you run the installer.  
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/ce9eca7-Copy_API_Key.png",
        "Copy API Key.png",
        1298,
        1754,
        "#4f5b65"
      ]
    }
  ]
}
[/block]
## Step 3: Name the Engine

Next, enter a name for the scan engine. 
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/7152a80-Name_the_engine.png",
        "Name the engine.png",
        1300,
        1748,
        "#4f5b65"
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
## Step 4: Assign an Engine Group
If you have created a custom engine group, select it from the list of engine groups in Step 5. You can leave the engine group as “Default” for now, but you can change the engine group name later from the “Manage Engines” page.

## Step 5: Prepare the Engine for Pairing

After you copy the API key and name the scan engine, you're ready to  pair it. During the pairing process, the new scan engine waits for the on-premise engine to come online so that they can be paired.
Click **Save** at the bottom of the "Setup New Engine" panel. A new scan engine will be added to the "Manage Engines" page with a status of "Unavailable."
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/0465a57-Screen_Shot_2019-03-08_at_5.08.19_PM.png",
        "Screen Shot 2019-03-08 at 5.08.19 PM.png",
        2684,
        696,
        "#39444d"
      ]
    }
  ]
}
[/block]
## Step 6: Run the Installer

The installer provides step-by-step instructions, so you just need to run the installer and follow the prompts.

During installation, the installer verifies that the system meets the minimum requirements and validates that the engine can connect with the Insight platform. If it cannot reach the Insight Platform, you can configure a proxy for the installer to use. 

After the installer performs the system checks, it'll prompt you for an API key, which will be used to validate your organization and verify the presence of a pairable scan engine. You'll need to provide the API key you copied earlier.

When the installation completes, you'll need to go back to the "Manage Scan Engines" page in InsightAppSec. 

## Step 7: Refresh Manage Scan Engines page

After installation, the status of the new on-premise engine changes from "Unavailable" to "Available," which indicates that it has successfully paired and is ready for tasks. You'll need to refresh the page to see the status change. 

## Step 8: Use the New Scan Engine

The scan engine is now set up. You're ready to start using the scan engine. 
To get started, you can select the scan engine group for new scan configs or you can update existing scan configs to use the new scan engine group.
To update your existing scan configs, go to Apps > Scan Config > Engine Groups. You can choose the engine group for this new engine from the list of on premise scan engine groups.
Once you have selected an on-premise scan engine group for a scan config, the agent will regularly contact InsightAppSec to see if there are tasks, such as scans or engine updates, that need to be performed. 

## Step 9: Scan Your Apps

You're all done! You're now ready to scan your apps.