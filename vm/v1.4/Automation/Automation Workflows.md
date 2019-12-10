---
title: "Automation Workflows"
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

This page will introduce the standard Workflow Templates included with InsightVM, go over system requirements, and help you manage your Workflows through the dedicated **Workflows** view.

* [Included Workflow Templates](doc:workflows#section-included-workflow-templates)
* [Requirements](doc:workflows#section-requirements)
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
    "0-1": "* [Automation-assisted patching](doc:ibm-bigfix-automation-assisted-patching)",
    "2-1": "* Asset quarantine\n* Reverse asset quarantine",
    "3-0": "Cisco ISE",
    "3-1": "* Asset quarantine\n* Reverse asset quarantine",
    "1-0": "Microsoft SCCM",
    "1-1": "* [Automation-assisted patching](doc:microsoft-sccm-automation-assisted-patching)",
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
  "body": "You must configure all new connections in the [Workflow wizard](doc:workflows#section-workflow-wizard).  See our dedicated InsightVM workflow guides to learn how to configure connections for each supported tool:\n\n* [Microsoft SCCM - Automation-Assisted Patching](doc:microsoft-sccm-automation-assisted-patching)\n* [IBM BigFix - Automation-Assisted Patching](doc:ibm-bigfix-automation-assisted-patching)"
}
[/block]
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