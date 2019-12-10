---
title: "Ticketing Integration for Remediation Workflow Projects"
excerpt: ""
---
Remediation Projects integrate with popular ticketing systems so that security teams can automate the creation and assignment of work items based on pre-configured rules.

# Why integrate Projects with Ticketing?

Many security teams manage remediation efforts by generating CSV or PDF reports spanning hundreds of pages and spend a lot of time breaking down exposures into actionable work items. The Automated Ticketing feature simplifies this process while providing the following advantages:

* You can create targeted and precise tickets automatically with assignment rules that can be reused across projects.
* You can customize ticketing templates to include as much security context as you need.
* You can use the Projects page to provide a central location to manage and track your remediation projects. 
* You always have a clear picture of the progress of remediation work because solution statuses in Projects are updated from the ticketing system. 
* Your remediation teams can continue to use their existing tools and processes.

# Managing ticketing integration in Remediation Workflow
Ticketing Integration has two parts: 
* Creating connection settings to your preferred ticketing server, and matching each remediation status in InsightVM to a project status in your ticketing program. 
* Configuring a ticketing template for your project, which lets you select the ticketing project for automated ticketing, draft a template of the ticket generated from your Remediation Project, and then create rules for assigning automatically generated tickets to your team members.

You can create new ticket connections, edit existing connections, and enable/disable connections. 

# Enabling Automated Ticketing for Remediation Projects

The **Projects** tab shows the list of Remediation Projects you have set up for your environment. If a project has automated ticketing enabled, the Ticketing column will show the ![Alt](https://files.readme.io/23e17c9-rw_ticketing_enabled_icon.png) icon.

If you wish to enable automated ticketing on a project, you must go to the _Edit Project_ screen and click on the _Configure_ checkbox near the bottom of the page. This will reveal a list of ticketing templates that you have already configured, and you can select one for your project.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/53f49c7-rw_edit_remediation_project.png",
        "rw_edit_remediation_project.png",
        800,
        576,
        "#444c5b"
      ]
    }
  ]
}
[/block]
You can disable the ticketing configuration at any time. No new tickets will be generated for the Remediation Workflow project while the ticketing connection is disabled. You can also re-enable the ticketing connection later.