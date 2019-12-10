---
title: "IBM BigFix - Automation-Assisted Patching"
excerpt: ""
---
This article details the **Automation-Assisted Patching with IBM BigFix** workflow offered with the **Automation** feature in InsightVM.
[block:callout]
{
  "type": "warning",
  "title": "REMINDER",
  "body": "InsightVM automation workflows require an installed and activated [orchestrator](doc:workflows#section-insight-orchestrator) in order to communicate with your external tools.\n\nIf you still need to deploy an orchestrator, see the [orchestrator help page](https://insightconnect.help.rapid7.com/docs/install-and-activate-the-orchestrator) for installation instructions."
}
[/block]
This content covers the following topics:

* [Goal](doc:ibm-bigfix-automation-assisted-patching#section-goal)
* [How it Works](doc:ibm-bigfix-automation-assisted-patching#section-how-it-works)
* [Limitations](doc:ibm-bigfix-automation-assisted-patching#section-limitations)
* [Workflow Process In-Depth](doc:ibm-bigfix-automation-assisted-patching#section-workflow-process-in-depth)
* [InsightVM Workflow Configuration Instructions](doc:ibm-bigfix-automation-assisted-patching#section-insightvm-workflow-configuration-instructions)
* [Troubleshoot](doc:ibm-bigfix-automation-assisted-patching#section-troubleshoot)
* [Resources](doc:ibm-bigfix-automation-assisted-patching#section-resources)

# Goal

This workflow is designed for InsightVM users who want to leverage their IBM BigFix tool to ease the vulnerability management process with automation assistance.

# How it Works

This workflow consumes vulnerability and asset information from InsightVM in order to form queries that check BigFix for relevant patches (known as “fixlets” in BigFix) and assets. If matching fixlets and assets are found, the workflow will prompt the user to decide on one of the two following options:

* Deploy the relevant fixlets immediately using a Multiple Action Group
* Package the fixlets into a Baseline for deployment at a later time

## Trigger Behavior

Workflow triggers respond when the Insight platform receives new vulnerability assessment data from your environment. In other words, newly configured workflows will not initiate based on the current state of your network, even if that current state falls within the trigger scope you have defined.

In this context, workflow triggers respond to the data uploads that consist of completed vulnerability scans initiated by your Security Console and completed vulnerability assessments reported by your Insight Agents. The Insight platform checks the trigger conditions associated with your workflows when these data uploads take place and initiates the workflows that qualify.
[block:callout]
{
  "type": "warning",
  "title": "NOTE",
  "body": "If you experience delays or stops in trigger events, it could be due to platform communication issues. Check the [Configure communications with the Insight platform](doc:configure-communications-with-the-insight-platform) page to verify that your whitelist settings are correct."
}
[/block]
# Limitations

This workflow operates under the following limitations:

* The workflow does not bulk process patches to send to BigFix on an interval.
 * As previously described in the [trigger behavior](doc:ibm-bigfix-automation-assisted-patching#section-trigger-behavior), the workflow only sends new vulnerabilities and assets to BigFix in the event of a trigger.
* The workflow can only implement patches based off content available in BigFix.
 * Vulnerabilities identified by InsightVM that have no relevant patch in BigFix will result in no action being taken.
* Assets included in the workflow scope in InsightVM must also correlate to available assets in BigFix.
 * If InsightVM includes assets that BigFix is not aware of, no action will be taken for those assets.
* Assets identified as vulnerable by InsightVM must also be identified as vulnerable by BigFix or no action will be taken.

# Workflow Process In-Depth

This workflow proceeds through the following steps in order to meet its goal:

1. [Trigger the Workflow Based on Asset and Vulnerability Filters](doc:ibm-bigfix-automation-assisted-patching#section-trigger-the-workflow-based-on-asset-and-vulnerability-filters)
2. [Convert Trigger Data into a Relevance String](doc:ibm-bigfix-automation-assisted-patching#section-convert-trigger-data-into-a-relevance-string)
3. [Query BigFix with Relevance String](doc:ibm-bigfix-automation-assisted-patching#section-query-bigfix-with-relevance-string)
4. [Human Decision Options When Fixlets Are Found](doc:ibm-bigfix-automation-assisted-patching#section-human-decision-options-when-fixlets-are-found)
 * [Immediate Deployment](doc:ibm-bigfix-automation-assisted-patching#section-immediate-deployment)
 * [Baseline for Later Deployment](doc:ibm-bigfix-automation-assisted-patching#section-baseline-for-later-deployment)

## Trigger the Workflow Based on Asset and Vulnerability Filters

The asset and vulnerability filters you configure during the workflow wizard serve together as the trigger for initiating the workflow. When qualifying data is detected on a state change, InsightVM packages this trigger data into an artifact. This artifact includes general information about the trigger data, such as descriptions, timestamps, and asset data.

## Convert Trigger Data into a Relevance String

The workflow then passes the asset and vulnerability data from your trigger to a BigFix action that converts it into a Relevance string.
[block:callout]
{
  "type": "info",
  "title": "What is a “Relevance” string?",
  "body": "“Relevance” is the name of the proprietary language that BigFix uses to determine if an asset requires one or more fixlets in order to stay in compliance.  InsightVM workflow trigger data must be converted to a string in the Relevance language in order for BigFix to process it."
}
[/block]
This Relevance string directs BigFix to focus on the assets and vulnerabilities provided by the InsightVM workflow trigger scope you have defined.

## Query BigFix with Relevance String

After the workflow converts the trigger data into a Relevance string that BigFix can read, the workflow then queries BigFix for any applicable fixlets that correspond to the CVE codes associated with the vulnerabilities included in the workflow trigger:

* If fixlets **are found**, the workflow prompts the user to choose to deploy the fixlets immediately, or package them in a Baseline for later deployment.
* If fixlets **are not found**, the workflow creates an artifact to note this.
[block:callout]
{
  "type": "warning",
  "title": "NOTE",
  "body": "The workflow terminates if no applicable fixlets are found."
}
[/block]
## Human Decision Options When Fixlets Are Found

If the workflow finds applicable fixlets in BigFix, the user is prompted to make one of the following decisions.

### Immediate Deployment

If the user decides to immediately deploy the fixlets to included assets, the workflow creates a Multiple Action Group in BigFix with the name `Rapid7 InsightVM: AutoPatch ActionGroup`.  BigFix will deploy the fixlets on your target assets at this time.

### Baseline for Later Deployment

If the user decides to delay the deployment of the fixlets, the workflow creates a Baseline in BigFix with the name `Rapid7 InsightVM: AutoPatch Baseline: <InsightVM Event>.<timestamp>`. Your BigFix administrator can use this Baseline to deploy the fixlets at a later time.

# InsightVM Workflow Configuration Instructions

To configure a new workflow using the **Automation-Assisted Patching with IBM BigFix** template in InsightVM, follow these steps:

1. [Configure the Workflow Trigger](doc:ibm-bigfix-automation-assisted-patching#section-configure-the-workflow-trigger)
2. [Select or Configure a Connection](doc:ibm-bigfix-automation-assisted-patching#section-select-or-configure-a-connection)
3. [Name and Activate Your Workflow](doc:ibm-bigfix-automation-assisted-patching#section-name-and-activate-your-workflow)

## Configure the Workflow Trigger

First, you need to configure the trigger conditions that will initiate the workflow.

**To start the wizard and configure your workflow trigger:**

1. In InsightVM, click the **Automation** tab on your left navigation menu.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/c234c27-insightvm_leftmenu_automation.png",
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
 * The **Automation-Assisted Patching with IBM BigFix** template requires this trigger type.
5. **Apply** an asset filter and a vulnerability filter to refine the scope of your trigger.  Click **Continue** when ready.
 * These filters determine what assets the workflow sends to BigFix and what vulnerabilities on those assets need to be remediated.
6. Select the **Automation-Assisted Patching with IBM BigFix** workflow template from the dropdown list.  A preview of all individual workflow steps will appear.  Click **Continue** at the bottom of this step list when ready.

## Select or Configure a Connection

Next, you need to select an existing connection to your BigFix tool, or configure a new one for the workflow to use.

**To create a new connection:**

1. Select **New Connection** from the dropdown list.  The connection creation form appears.
2. Give your new connection a name.  You will be able to select this connection in future workflow wizards.
3. Select the [orchestrator](https://insightconnect.help.rapid7.com/docs/orchestrator) that has access to your BigFix tool from the dropdown list.
4. Select an existing credential associated with your BigFix tool from the dropdown list, or click **Create New Credential** to configure a new one.
 * In the context of InsightVM automation workflows, a “credential” is a username and password pair for an account that you would use to access your BigFix software.
[block:callout]
{
  "type": "warning",
  "title": "NOTE - Credential account requirements",
  "body": "To run this workflow, your credential account must have administrator privileges and read/write access on the BigFix software.  Specifically, the account must have the following permissions:\n\n* Can Create Actions\n* Can Send Refresh to Multiple Computers\n* Can Submit Queries\n* Custom Content\n* Post-Action Behavior\n* Action Script Commands\n* Can Use REST API"
}
[/block]
5. In the “URL” field, enter the full hostname URL for the server that hosts the BigFix software.
6. In the “SSL Verify” field, select **true** or **false** from the dropdown list.
 * Although **true** is the preferred option here, you may select **false** if you use a self-signed certificate.
7. Click **Save Connection** when finished.
8. With your connection selected, click **Continue**.

## Name and Activate Your Workflow

Now that you’ve configured your workflow trigger and connection, give your workflow a name so that you can identify it in your “Workflows” table.  Click **Activate** to complete the workflow wizard.
[block:callout]
{
  "type": "success",
  "title": "Your workflow is ready!",
  "body": "You should now have successfully configured a workflow with the **Automation-Assisted Patching with IBM BigFix** template."
}
[/block]
# Troubleshoot

See the [IBM BigFix](https://insightconnect.help.rapid7.com/docs/troubleshoot-a-failed-job#section-ibm-bigfix) section of the [Troubleshoot a Failed Job Help page](https://insightconnect.help.rapid7.com/docs/troubleshoot-a-failed-job) for a common troubleshooting scenario and solution.

# Resources

* IBM BigFix documentation - https://www.ibm.com/support/knowledgecenter/SS6MER_9.5.0/com.ibm.bigfix.patch.doc/welcome/BigFix_Patch_welcome.html