---
title: "Activating Your Console on the Insight Platform"
excerpt: ""
---
The Rapid7 Insight platform provides data collection, visibility, analytics, and automation to establish a shared point of view between security, IT operations, and DevOps. Our cloud platform delivers one-click access to Rapid7’s vulnerability management, application testing, incident detection and response, phishing analysis and simulation, and log management solutions. 

You can learn more about the Insight platform in the following articles:

* [https://www.rapid7.com/products/insight-platform/](https://www.rapid7.com/products/insight-platform/)
* [https://www.rapid7.com/trust](https://www.rapid7.com/trust)

[block:callout]
{
  "type": "warning",
  "title": "Whitelist requirements",
  "body": "You may need to configure whitelisting for outbound traffic in order to upload data to the Insight platform.  See [Configure communications with the Insight platform](doc:configure-communications-with-the-insight-platform) for details."
}
[/block]
# Benefits

InsightVM license holders can opt in to take advantage of capabilities available only in the Rapid7 Insight platform.

## Dashboards

With Dashboards, you can build customizable, drag-and-drop interfaces so you can continuously monitor your security environment from a compact, informative space. For more information, see [Dashboards Help Page](doc:dashboards).

## Insight Agents

Insight Agents assess vulnerabilities on cloud-based and on-prem assets by collecting data and relaying them back to the Insight platform for analysis. To learn more, see our [Insight Agent Help Pages](https://insightagent.help.rapid7.com/docs/). 

## Containers

The Containers interface allows you to monitor risk assessment for all images that are running containers in your environment, as well as sort your images in a variety of ways. To learn more, see our [Containers Help Page](doc:working-with-containers). 

## Projects
The Remediation Workflow is an InsightVM feature that creates, assigns, monitors, and automates ticketing for remediation projects. A remediation project is a group of solutions for vulnerabilities that need to be remediated on a specific set of assets within a certain time frame. 

To learn more, see our [Remediation Workflow Help Pages](doc:remediation-workflow). 

The **Dashboard**, **Projects**, **Containers**, and **Management** interfaces are only accessible to organizations that have activated their Security Console on the Insight platform.

# Security Console Activation Requirements 

These are the requirements needed to activate the Security Console: 
1. You are on InsightVM Security Console version 6.5.29 or later.
2. InsightVM Security Console cannot have access to Dashboards or other cloud capabilities. The console cannot be connected  on the Insight platform prior to InsightVM Security Console version 6.5.29. 
3. An Insight platform account is needed to activate your Security Console. 
  a. If you don’t remember if you have an account or forgotten your credentials, [contact Rapid7 Technical Support](https://www.rapid7.com/contact/). 
[block:callout]
{
  "type": "warning",
  "title": "NOTE",
  "body": "An Insight platform account is different from your Security Console login."
}
[/block]

[block:callout]
{
  "type": "info",
  "title": "TIP",
  "body": "If you already have access to Dashboards or other InsightVM cloud capabilities, no further action is required."
}
[/block]
# Networking

You may need to configure whitelisting for outbound traffic in order to upload data to the Insight platform. See [Configure communications with the Insight platform](docs/configure-communications-with-the-insight-platform) for details.

# How to Activate InsightVM on the Insight Platform
[block:callout]
{
  "type": "danger",
  "title": "IMPORTANT",
  "body": "Before starting this procedure, ensure the Security Console’s host machine has the correct time. If the time setting on the host machine is incorrect, it may interfere with your ability to access InsightVM’s cloud features.\n\nWe recommend syncing your Security Console’s host machine with an NTP server.\n\nFor Virtual Appliance deployments, see our [FAQ section](https://kb.help.rapid7.com/docs/insightvm-and-nexpose-virtual-appliance-guide#section-how-do-i-set-the-system-time-) to learn how to set the system time."
}
[/block]
If you don’t already have a Rapid7 Insight platform account, you will need to create one so you can access InsightVM’s cloud capabilities.

##Activation wizard

Run the wizard to complete the activation process.  You can trigger the activation wizard by clicking any of the following icons in the left navigation menu:

* **Dashboard**
* **Projects**
* **Containers**
* **Management**
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/a5d7344-wizard_access.png",
        "wizard_access.png",
        201,
        552,
        "#40424a"
      ]
    }
  ]
}
[/block]

[block:callout]
{
  "type": "info",
  "title": "TIP",
  "body": "If the wizard is not triggered and you are redirected to your InsightVM dashboard, you already have access to the Insight platform and do not need to take further action."
}
[/block]
Alternatively, you can run the wizard manually: 

1. From your left navigation menu, go to **Administration**. 
2. Under “Global and Console Settings,” click **Administer**. 
3. Click the **Insight Platform** tab.
4. Click **Activate Console**.

After triggering the wizard, select the appropriate option. 
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/54eda93-activation_wizard_noaccount.png",
        "activation_wizard_noaccount.png",
        599,
        621,
        "#5f6a73"
      ]
    }
  ]
}
[/block]
Follow the steps in the wizard, which will prompt you to create a Rapid7 Insight platform account or use your existing account to activate your Security Console on the Insight platform. 

### Create Your Insight Account

If you needed to create a new Rapid7 Insight platform account, you will be guided through the steps of setting up your account password and security questions. If you already have an Insight platform account, skip ahead to [Activate the Security Console](doc:activating-your-console-on-the-insight-platform#section-activate-the-security-console).

### Activate the Security Console

Follow these steps to use your existing Rapid7 Insight platform account to activate InsightVM on the Insight platform:

1. Sign in to your Rapid7 Insight platform account at [insight.rapid7.com](https://insight.rapid7.com/login).
2. If this is your only product with Rapid7, skip to step 3. 
  a. If you are not sent directly to your platform home page, open the app switcher located next to your current product logo in the upper-left of your screen and select “My Account”. 
  b. If you have other Rapid7 products, open the InsightVM tile. If the InsightVM tile is not present, add it manually from the “More Products & Services” section by clicking the Pair Console button.  


[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/cac68d2-modal_almost-there_2.png",
        "modal_almost-there_2.png",
        1040,
        584,
        "#dbdfe0"
      ]
    }
  ]
}
[/block]
3. Copy the pairing key.
4. Back in your Security Console, click **Enter Pairing Key**, which is found in the banner below the upper navigation menu.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/9fb951e-banner.png",
        "banner.png",
        840,
        98,
        "#3c5867"
      ]
    }
  ]
}
[/block]
5. On the next screen, enter your pairing key in the field. Click **Activate Console**. 
6. You will see a notification that confirms your pairing was successful. 
[block:callout]
{
  "type": "info",
  "title": "NOTE",
  "body": "You can also access the banner by following these steps:\n\n1. In the left navigation menu, go to **Administration**. \n2. Under “Global and Console Settings,” click **Administer**. \n3. Click the **Insight Platform** tab.\n4. Click **Activate Console**."
}
[/block]
It may take a few moments for the connection to complete. Once completed, the page will refresh and your Security Console will now be able to communicate with the Insight platform. Dashboards, remediation workflow, and container assessment features will be available for use.

# How to Deactivate Your Console from the Insight Platform

If you need to deactivate your Security Console from the Rapid7 Insight platform, follow these steps: 

1. From your left navigation menu, go to **Administration**. 
2. Under “Global and Console Settings,” click **Administer**. 
3. Click the **Insight Platform** tab.
4. Click **Deactivate Console**.