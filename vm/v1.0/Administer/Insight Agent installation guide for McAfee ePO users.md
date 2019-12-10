---
title: "Insight Agent installation guide for McAfee ePO users"
excerpt: ""
---
The McAfee ePolicy Orchestrator (ePO) can be used to simplify the task of installing the Rapid7 Insight Agent on a large number of machines in your network. This article outlines the steps involved in this installation.

##Prerequisites

We assume that you have already configured the McAfee ePolicy Orchestrator to monitor the Windows systems in your environment, and these target systems have the McAfee Agent installed.

You'll need to download the Rapid7 ePO extension from [http://download2.rapid7.com/download/NeXpose-v4/epo-extension/Rapid7Nexpose.zip](http://download2.rapid7.com/download/NeXpose-v4/epo-extension/Rapid7Nexpose.zip), the Rapid7 Manager plugin from [http://download2.rapid7.com/download/NeXpose-v4/epo-extension/R7AgentDeployment_0409.zip](http://download2.rapid7.com/download/NeXpose-v4/epo-extension/R7AgentDeployment_0409.zip), and the Insight Agent installer from the "Download agent" page in your application. These installer files should be accessible from the ePO server.

##Installation

The installation process consists of 3 parts:
* Installing the Rapid7 extension on the ePO server
* Installing the Rapid7 Manager plugin on the target systems
* Installing the Insight Agent on the target systems

These parts are outlined separately in the following sections.

###Installing the Rapid7 Extension

The Rapid7 ePO extension can be installed by obtaining the installation zip archive from Rapid7 support. The extension can be installed on ePO using the following steps –

1. From the main menu of ePO, click on **Extensions** under the _Software_ category.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/0219acd-Insight_Agent_installation.png",
        "Insight Agent installation.png",
        1440,
        860,
        "#e0e6ea"
      ]
    }
  ]
}
[/block]
2. The _Extensions_ screen appears. On this screen, click on the **Install Extension** button, and browse to the Rapid7.zip file location. Follow all the steps of the installation process.
3. After the installation is complete, you will return to the Extensions screen. Ensure that Rapid7 is visible in the list of extensions and the state is _Running_.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/1f205c1-Insight_Agent_installation_1.png",
        "Insight Agent installation_1.png",
        1102,
        277,
        "#fafafa"
      ]
    }
  ]
}
[/block]
###Installing the Rapid7 Manager plugin on target systems

The Rapid7 Manager coordinates communication between the Rapid7 extension and the Insight Agents on the target systems. It is also responsible for enforcing the policies related to Rapid7 on the target systems. The following steps are required for installing the Rapid7 Manager on your systems –

1. From the main menu, click on **Master Repository** under the _Software_ category.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/34cbcc3-Insight_Agent_installation_2.png",
        "Insight Agent installation_2.png",
        1440,
        860,
        "#eaf0f5"
      ]
    }
  ]
}
[/block]
2. On the Master Repository screen, click on the **Check In Package** button, and browse to the R7AgentDeployment zip file.
3. Ensure that the application _Rapid7 Manager_ appears in the package list in the Master Repository screen.
4. From the main menu, select **Client Task Catalog** under the _Policy_ category.
5. On the Client Task Catalog screen, select **Product Deployment** as the task type, and click on the **New Task** button.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/399bbf8-Insight_Agent_installation_3.png",
        "Insight Agent installation_3.png",
        1440,
        860,
        "#e9eff4"
      ]
    }
  ]
}
[/block]
6. In the client task creation wizard, set the product as **Rapid7 Manager** and the action as **Install**. Complete the rest of the fields in the installation wizard as per your preferences.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/13da81c-Insight_Agent_installation_4.png",
        "Insight Agent installation_4.png",
        1440,
        860,
        "#5fb9d5"
      ]
    }
  ]
}
[/block]
7. Now that the installation task is created, you can apply it to the systems in your network. For this, you will have to return to the main menu, and select **System Tree** under the _Systems_ category.
8. On the System Tree screen, select a system group and open the _Assigned Client Tasks_ tab. From the _Actions_ menu at the bottom of this tab, select **New Client Task Assignment**.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/8013362-Insight_Agent_installation_5.png",
        "Insight Agent installation_5.png",
        1440,
        860,
        "#e9eff3"
      ]
    }
  ]
}
[/block]
9. In the New Client Task Assignment wizard, select the **install Rapid7 Manager** task created in the previous step. Based on your selections, the final screen of the wizard should look something like this – 
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/34d3b22-Insight_Agent_installation_6.png",
        "Insight Agent installation_6.png",
        1440,
        860,
        "#5db5d3"
      ]
    }
  ]
}
[/block]
When this Client Task has been assigned to your systems, the Rapid7 Manager will be installed the next time ePO syncs up with those systems. By default, this sync-up process occurs once every hour.

###Installing the Insight Agent

The Rapid7 Manager is responsible for installing the Insight Agent on your systems. The following steps will help you configure the Agent installation –

1. From the main menu, click **Server Settings** under the _Configuration_ category.
2. In the Server Settings screen, select Rapid7 Settings. The right pane will have four text fields for agent-related configuration data – client.crt, config.json, client.key and cafile.pem. Complete these fields using the contents of similarly named files in the Insight Agent installation package. The contents of these files can be viewed by opening them in Notepad. 
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/d7c7807-Insight_Agent_installation_7.png",
        "Insight Agent installation_7.png",
        1440,
        860,
        "#e7e8e7"
      ]
    }
  ]
}
[/block]
3. Return to the main menu and click on **Policy Catalog** under the _Policy_ category. The Policy Catalog page will look like this – 
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/1b532dc-Insight_Agent_installation_8.png",
        "Insight Agent installation_8.png",
        1440,
        381,
        "#5aaac9"
      ]
    }
  ]
}
[/block]
4. On the Policy Catalog page, either duplicate the inbuilt nexpose _Default_ policy, or click **New Policy**.
5. On the policy configuration page, select the recommended option – **Don’t re-install the Rapid7 Insight Agent if already present**. Give this policy a suitable name like ‘install Rapid7 Insight Agent’. 
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/caaacd7-Insight_Agent_installation_9.png",
        "Insight Agent installation_9.png",
        990,
        362,
        "#5eb8d4"
      ]
    }
  ]
}
[/block]
6. Visit the System Tree screen through the main menu. On the System Tree screen, select a system group and open the _Assigned Policies_ tab. From the _Actions_ menu at the bottom of this tab, select **New Policy Assignment**.
7. In the Policy Assignment wizard, select **install Rapid7 Insight Agent** as the policy to be assigned. 
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/62cca8e-Insight_Agent_installation_10.png",
        "Insight Agent installation_10.png",
        1440,
        542,
        "#5fbad6"
      ]
    }
  ]
}
[/block]
When the Rapid7 Manager on your target system syncs up with the ePO server, it will be notified about the new policy assigned to the system. It will then download the configuration files from the ePO server and the Insight Agent hosted on the Rapid7 cloud platform.

You can confirm the installation of the Insight Agent on your target systems by visiting the path _Program Files > R7Agent_.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/6cbac02-Insight_Agent_installation_11.png",
        "Insight Agent installation_11.png",
        800,
        341,
        "#c3d2e2"
      ]
    }
  ]
}
[/block]