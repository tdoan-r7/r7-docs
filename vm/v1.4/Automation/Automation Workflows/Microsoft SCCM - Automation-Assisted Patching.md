---
title: "Microsoft SCCM - Automation-Assisted Patching"
excerpt: ""
---
This article details the **Automation-Assisted Patching with Microsoft SCCM** workflow offered with the **Automation** feature in InsightVM.
[block:callout]
{
  "type": "warning",
  "title": "REMINDER",
  "body": "InsightVM automation workflows require an installed and activated [orchestrator](doc:workflows#section-insight-orchestrator) in order to communicate with your external tools.\n\nIf you still need to deploy an orchestrator, see the [orchestrator help page](https://insightconnect.help.rapid7.com/docs/install-and-activate-the-orchestrator) for installation instructions."
}
[/block]
This content covers the following topics:

* [Goal](doc:microsoft-sccm-automation-assisted-patching#section-goal)
* [How it Works](doc:microsoft-sccm-automation-assisted-patching#section-how-it-works)
* [Limitations](doc:microsoft-sccm-automation-assisted-patching#section-limitations)
* [Workflow Process In-Depth](doc:microsoft-sccm-automation-assisted-patching#section-workflow-process-in-depth)
* [InsightVM Workflow Configuration Instructions](doc:microsoft-sccm-automation-assisted-patching#section-insightvm-workflow-configuration-instructions)
* [Troubleshoot](doc:microsoft-sccm-automation-assisted-patching#section-troubleshoot)
* [Resources](doc:microsoft-sccm-automation-assisted-patching#section-resources)

# Goal

This workflow is designed for InsightVM users who want to leverage their Microsoft System Center Configuration Manager (SCCM) tool to ease the vulnerability management process with automation assistance.

# How it Works

This workflow consumes vulnerability and asset information from InsightVM in order to form queries that check SCCM for relevant patches and assets. If the workflow finds matching patches and assets, it creates and stages a pair of SCCM entities (a Software Update Group and a Device Collection) that SCCM can deploy.

## Trigger Behavior

Workflow triggers respond when the Insight platform receives new vulnerability assessment data from your environment.  In other words, newly configured workflows will not initiate based on the current state of your network, even if that current state falls within the trigger scope you have defined.

In this context, workflow triggers respond to the data uploads that consist of completed vulnerability scans initiated by your Security Console and completed vulnerability assessments reported by your Insight Agents. The Insight platform checks the trigger conditions associated with your workflows when these data uploads take place and initiates the workflows that qualify.
[block:callout]
{
  "type": "warning",
  "title": "NOTE",
  "body": "If you experience delays or stops in trigger events, it could be due to platform communication issues.  Check the [Configure communications with the Insight platform](doc:configure-communications-with-the-insight-platform) page to verify that your whitelist settings are correct."
}
[/block]
# Limitations

This workflow operates under the following limitations:

* The workflow only supports Microsoft vulnerabilities and their respective patches.
* The workflow can only implement patches based off content available in SCCM.
 * InsightVM will not take action if identified vulnerabilities do not have a relevant patch in SCCM. 
* Assets included in the workflow scope in InsightVM must also correlate to available assets (referred to as “devices”) in SCCM.
 * If InsightVM includes assets that SCCM is not aware of, the workflow will not take action for those assets.
* Assets identified as vulnerable by InsightVM must also be identified as vulnerable by SCCM or the workflow will not take action.

# Workflow Process In-Depth

This workflow proceeds through the following steps in order to meet its goal:

1. [Trigger the Workflow Based on Asset and Vulnerability Filters](doc:microsoft-sccm-automation-assisted-patching#section-trigger-the-workflow-based-on-asset-and-vulnerability-filters)
2. [Query SCCM with Trigger Data](doc:microsoft-sccm-automation-assisted-patching#section-query-sccm-with-trigger-data)
3. [SCCM Stages Completed Software Update Group and Device Collection for Deployment](doc:microsoft-sccm-automation-assisted-patching#section-sccm-stages-completed-software-update-group-and-device-collection-for-deployment)

## Trigger the Workflow Based on Asset and Vulnerability Filters

The asset and vulnerability filters you configure during the workflow wizard serve together as the trigger for initiating the workflow. When qualifying data is detected on a state change, InsightVM packages this trigger data into an artifact. This artifact includes general information about the trigger data, such as descriptions, timestamps, and asset data.

## Query SCCM with Trigger Data

The workflow then queries SCCM to see if the workflow name you specified in the configuration wizard matches an existing Software Update Group name.
[block:callout]
{
  "type": "info",
  "title": "TIP",
  "body": "The workflow uses its own InsightVM name to find possible matches for both a Software Update Group and a Device Collection in SCCM.  For example, if you name your workflow “My Workflow” during the configuration wizard, the workflow looks for a Software Update Group and Device Collection of the same name.\n\nNote that both the Software Update Group and Device Collection do not need to already exist prior to the configuration for this workflow to complete successfully.  At this stage, if the workflow does not find a matching Software Update Group, it will create a new one for you."
}
[/block]
With either an existing or new Software Update Group in place, the workflow queries the SCCM server for software updates based on each Software Update ID associated with the vulnerabilities in the workflow trigger:

* If software updates **are found**, the workflow adds them to the Software Update Group and logs an artifact to reflect this.
* If software updates **are not found**, the workflow creates an artifact to note this.

The workflow then determines if the workflow name you specified in the configuration wizard matches an existing Device Collection in SCCM:

* If a matching Device Collection **exists**, the workflow queries SCCM for the asset hostnames included in the workflow trigger. The workflow adds matching SCCM hostnames that are not already part of the existing Device Collection and logs an artifact. If the hostname is not found in SCCM, the workflow creates an artifact to note this.
* If a matching Device Collection **does not exist**, the workflow creates a new Device Collection in SCCM based on the assets included in the workflow trigger. Just as before, the workflow adds matching SCCM hostnames to the new Device Collection and logs an artifact. If the hostname is not found in SCCM, the workflow creates an artifact to note this.

## SCCM Stages Completed Software Update Group and Device Collection for Deployment

The workflow completes when the Software Update Group and Device Collection are staged in SCCM.
[block:callout]
{
  "type": "warning",
  "title": "NOTE",
  "body": "The workflow does not deploy software updates itself.  SCCM is ultimately responsible for deploying software updates after the Software Update Group and Device Collection have been staged."
}
[/block]
# InsightVM Workflow Configuration Instructions

To configure a new workflow using the **Automation-Assisted Patching with Microsoft SCCM** template in InsightVM, follow these steps:

1. [Configure the Workflow Trigger](doc:microsoft-sccm-automation-assisted-patching#section-configure-the-workflow-trigger)
2. [Select or Configure a Connection](doc:microsoft-sccm-automation-assisted-patching#section-select-or-configure-a-connection)
3. [Name and Activate Your Workflow](doc:microsoft-sccm-automation-assisted-patching#section-name-and-activate-your-workflow)

## Configure the Workflow Trigger

First, you need to configure the trigger conditions that will initiate the workflow.

**To start the wizard and configure your workflow trigger:**

1. In InsightVM, click the **Automation** tab on your left navigation menu.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/1986786-insightvm_leftmenu_automation.png",
        "insightvm_leftmenu_automation.png",
        197,
        420,
        "#3a4149"
      ]
    }
  ]
}
[/block]
2. On the “Automation” page, click **+ New Automation** in the upper right corner. The automation configuration wizard appears.
3. Select **Workflow** and click **Continue**.
4. Click the **Vulnerability** trigger type radio button.
 * The **Automation-Assisted Patching with Microsoft SCCM** template requires this trigger type.
5. **Apply** an asset filter and a vulnerability filter to refine the scope of your trigger.  Click **Continue** when ready.
 * These filters determine what assets the workflow sends to SCCM and what vulnerabilities on those assets need to be remediated.
6. Select the **Automation-Assisted Patching with Microsoft SCCM** workflow template from the dropdown list.  A preview of all individual workflow steps will appear.  Click **Continue** at the bottom of this step list when ready.

## Select or Configure a Connection

Next, you need to select an existing connection to your SCCM tool, or configure a new one for the workflow to use.

**To create a new connection:**

1. Select **New Connection** from the dropdown list.  The connection creation form appears.
2. Give your new connection a name.  You will be able to select this connection in future workflow wizards.
3. Select the [orchestrator](https://insightconnect.help.rapid7.com/docs/orchestrator) that has access to your SCCM tool from the dropdown list.
4. Select an existing credential associated with your SCCM tool from the dropdown list, or click **Create New Credential** to configure a new one.
 * In the context of InsightVM automation workflows, a “credential” is a username and password pair for an account that you would use to access your SCCM software.
[block:callout]
{
  "type": "warning",
  "title": "NOTE - Credential account requirements",
  "body": "To run this workflow, your credential account must have administrator privileges and read/write access on the SCCM software."
}
[/block]
5. In the “Server IP” field, enter the IP address for the Windows server that hosts the SCCM software.
 * If you don’t know this address, open a command prompt on the Windows server and run `ipconfig`.  The address will appear next to `IPv4 Address`.
6. This workflow uses the Windows Remote Management (WinRM) protocol to communicate with your SCCM server.  In the "WinRM Port" field, enter a corresponding port number.
 * By default, WinRM listens on ports 5985 and 5986. InsightVM currently only supports port 5986 for HTTPS/TLS. 
[block:callout]
{
  "type": "info",
  "title": "TIP",
  "body": "Although this field is technically not required to save your connection, it defaults to port 5986 if left blank."
}
[/block]
7. In the “SCCM Path” field, enter the absolute path to the SCCM AdminConsole binaries.
 * By default, this path is `C:\Program Files (x86)\Microsoft Configuration Manager\AdminConsole\bin`, but note that this location can vary depending on how SCCM was originally installed.  Check with your SCCM administrator to confirm that your SCCM path is correct.
8. In the “Site Path” field, enter the site code of your SCCM server.
 * SCCM site codes are often composed of three characters. You can determine your site code by navigating to **Administration > Site Configuration > Sites** in your SCCM Admin Console.
9. Click **Save Connection** when finished.
With your connection selected, click **Continue**.

## Name and Activate Your Workflow

Now that you’ve configured your workflow trigger and connection, give your workflow a name so that you can identify it in your “Workflows” table.  Click **Activate** to complete the workflow wizard.
[block:callout]
{
  "type": "success",
  "title": "Your workflow is ready!",
  "body": "You should now have successfully configured a workflow with the **Automation-Assisted Patching with Microsoft SCCM** template."
}
[/block]
# Troubleshoot

See the [Troubleshoot Microsoft SCCM Connection](https://insightconnect.help.rapid7.com/docs/microsoft-sccm#section-troubleshoot-microsoft-sccm-connection) section of the [Microsoft SCCM InsightConnect Help page](https://insightconnect.help.rapid7.com/docs/microsoft-sccm) for common troubleshooting scenarios and solutions.

# Resources

* Microsoft SCCM documentation - https://docs.microsoft.com/en-us/sccm/core/understand/introduction