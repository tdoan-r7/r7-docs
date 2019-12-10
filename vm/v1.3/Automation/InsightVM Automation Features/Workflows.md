---
title: "Workflows"
excerpt: ""
---
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/f0f5f95-automation_workflowtab.png",
        "automation_workflowtab.png",
        530,
        108,
        "#2f3740"
      ]
    }
  ]
}
[/block]
Automations of the Workflow type can eliminate most of the manual tasking involved in performing common network security procedures such as remediation and asset quarantine.

This page will introduce the standard Workflow Templates included with InsightVM, go over system requirements, guide you through the Workflow creation wizard, and help you manage your Workflows through the dedicated **Workflows** view.

* [Included Workflow Templates](doc:workflows#section-included-workflow-templates)
* [Requirements](doc:workflows#section-requirements)
* [Workflow wizard](doc:workflows#section-workflow-wizard)
* [Management](doc:workflows#section-management)
* [Workflow details](doc:workflows#section-workflow-details)

# Included Workflow Templates

InsightVM features built-in Workflow Templates for the following third-party tools:
[block:parameters]
{
  "data": {
    "h-0": "Tool",
    "h-1": "Available Workflow Templates",
    "0-0": "IBM BigFix",
    "2-0": "Carbon Black",
    "0-1": "* Automation-assisted patching",
    "2-1": "* Asset quarantine\n* Reverse asset quarantine",
    "3-0": "Cisco ISE",
    "3-1": "* Asset quarantine\n* Reverse asset quarantine",
    "1-0": "Microsoft SCCM",
    "1-1": "* Automation-assisted patching",
    "4-0": "Palo Alto PAN-OS",
    "4-1": "* Asset quarantine\n* Reverse asset quarantine"
  },
  "cols": 2,
  "rows": 5
}
[/block]
# Requirements

Since Workflows are designed to communicate with external tools, they require additional setup before they can be used.  You must install an Insight Orchestrator and configure Connections to your third-party software in order to run Workflows.

## Insight Orchestrator

The Insight Orchestrator serves as the driver of your Workflows.  It passes input and output between Workflow steps in order to provide external tools with the information they need to act on their own.  An orchestrator must be installed and activated before you can run your first Workflow.

InsightVM directs you to the following page if you need to install an orchestrator:
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/0d3c5c2-insightvm_orchestrator_download.png",
        "insightvm_orchestrator_download.png",
        1905,
        977,
        "#343c45"
      ]
    }
  ]
}
[/block]
See our [orchestrator help page](https://insightconnect.help.rapid7.com/docs/install-and-activate-the-orchestrator) for installation instructions.

## Connections
[block:callout]
{
  "type": "warning",
  "title": "REQUIRED",
  "body": "You must have an orchestrator installed and activated in order to configure a Connection."
}
[/block]
Workflows rely on configured Connections to your external tools in order for the orchestrator to communicate data between steps.  You must have a configured Connection to the third-party software that your Workflow plans to use.
[block:callout]
{
  "type": "info",
  "title": "Where do I configure Connections?",
  "body": "Connections are configured in the [Workflow wizard](doc:workflows#section-workflow-wizard).  Return to this procedure when the wizard prompts you to do so."
}
[/block]
When prompted, complete the following fields to configure a Connection:

1. Select the third-party tool meant for this Connection.
2. Select the orchestrator that will use this Connection.
3. Fill out the Connection parameters.
 * While required parameters will differ depending on your selected third-party software, they generally require a credential and a key for authentication purposes.
4. Enter the server URL of your third-party software.
5. Click **Save Connection** when finished.

Once saved, InsightVM will test your Connection to ensure it works properly.  If your Connection test fails, click **Edit Connection** to return to the Connection configuration and verify that all fields were filled out correctly.  You can also download the log file for troubleshooting purposes.

# Workflow wizard

To create a Workflow:

1. Navigate to the **Automation** tab on your left menu.
2. On the “Automation” page, click the **Workflows** tab.
3. In the upper right corner, click **+ New Automation**.
 * If you don’t have any Workflows yet, this button will be available from the center of your screen.
4. On the first step of the wizard, select the **Workflow** Automation type and click **Continue**.
5. Select a trigger type for your Workflow.  All Automations trigger on assets or vulnerabilities affecting those assets.
6. Apply a filter for your selected trigger type.  See the [Query filter guide](doc:query-filter-guide) for instructions and operator descriptions.
 * You can preview your filter results by expanding the trigger type dropdown list.  Click the **\>** next to your filter results number to open it.
[block:callout]
{
  "type": "warning",
  "title": "The Vulnerability trigger type requires two filters",
  "body": "If you select **Vulnerability** as your trigger type, you must apply both an asset filter and a vulnerability filter.  Automations that respond to vulnerability changes have to know what subset of assets are being considered."
}
[/block]
7. Review your configured trigger for accuracy.  Click **Continue** when ready.
8. Select a Workflow Template to use.
 * Templates included with InsightVM are [listed above](doc:workflows#section-included-workflow-templates).
 * Your selected Workflow Template will list all the steps involved in its execution.
9. Select a Connection.
 * If you have not yet [configured a Connection](doc:workflows#section-connections) for your chosen third-party software, you can do so now by clicking **Create New Connection** in the selection dropdown.
10. Confirm the scope of your trigger.
 * Your applied filters will be shown for your review before proceeding.
11. Click **Activate**.

Your configured Workflow will now appear in the “Workflows” table.

# Management

You can manage your configured Workflows from the dedicated **Workflows** tab on the “Automation” page.

## Filters

Similarly to the consolidated **History** tab, the **Workflow** tab view includes its own filtering capability tailored for Workflow traits.

## “Workflows” table

All your configured Workflows are listed here, sortable by several columns.  Any filters you have applied will affect the entries shown on this table.

### Status

You can quickly enable or disable your configured Workflows using the sliders in the “Status” column.  The Workflow is considered active when the slider is in the green position.

# Workflow details

Click the name link of any Workflow on your table to see the “Workflow Details” page.  This view displays general information based on the Workflow’s configuration.

## “Workflow History” table

This table will keep a record of every trigger instance of your Workflow and will include data on whether it succeeded, paused, or failed, and when it started and finished.

Applicable filters on the “Workflow Details” page are tailored for these table traits.