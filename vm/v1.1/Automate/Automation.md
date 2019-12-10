---
title: "Automation"
excerpt: ""
---
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/580369b-leftnav_automationtab.png",
        "leftnav_automationtab.png",
        180,
        308,
        "#313941"
      ]
    }
  ]
}
[/block]
# Overview

As a platform-enabled InsightVM customer, you can take advantage of multiple Automation features that allow you to eliminate most of the manual tasks involved in addressing security needs in your environment.  These capabilities include both internal InsightVM functions and external tool orchestration via Workflows.

InsightVM offers the following configurable Automation options:

## Notifications

Contained entirely within InsightVM, configure [Notifications](doc:notifications) to alert both internal and external team members to detected changes affecting your assets.  Choose between communication methods such as email and text messaging to keep your team informed.

## Workflows
[block:callout]
{
  "type": "warning",
  "title": "REQUIRED",
  "body": "You must install and activate an Insight Orchestrator to run Workflows.  See our [orchestrator help page](https://insightconnect.help.rapid7.com/docs/install-and-activate-the-orchestrator) for instructions."
}
[/block]
Driven by the Insight Orchestrator, configure [Workflows](doc:workflows) to eliminate the significant lag time and tasking normally associated with asset containment and remediation.  InsightVM includes several ready-made Workflows built for industry-leading third party solutions (such as Automation-assisted patching with IBM BigFix and Microsoft SCCM) that you can use to quickly address emerging security needs.

# Understanding triggers

Before you get started with your first Automation, it’s important to understand how and when they decide to run.  All InsightVM Automations are designed to run on triggers.  Automation triggers are made of query filters applied to your assets and the vulnerabilities found therein.  These filters can be as broad or focussed as you require, and proper use will help you get the most out of Automation in InsightVM.

Check out our [Query filter guide](doc:query-filter-guide) to learn how to build Automation triggers effectively.

# Take a quick tour of the Automation page

Click the **Automation** tab on your navigation menu.  Before we dive in to each Automation type in detail, feel free to familiarize yourself with the landing page and the information it holds.

## History

Your Automation page opens to this view by default.  The **History** tab is a consolidated view of all the trigger instances for each of your configured Automations, regardless of type.

## Filters

The “Filters” panel holds several filter options, including raw search, date range, and status selectors.  Apply one or combine several for an increasingly granular view of your trigger instances.

## History table

All historical trigger instances for your Automations are listed here, sortable by several columns.  Click any of these records to view the particular detail page for that trigger instance.

## **Manage Connections** button

The Workflow Automation type relies on established Connections to your third party solutions in order to execute successfully.  Click **Manage Connections** to navigate to, create, and check the status of your configured Connections.

Check out the [Workflows](doc:workflows) page for instructions on how to configure your connections.

## **+ New Automation** button

Click **+ New Automation** to start the Automation creation wizard.  Automations of all types are created this way.  Be sure to read our individual Automation pages for instructions on using the wizard in each scenario.