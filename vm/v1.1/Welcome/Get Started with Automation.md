---
title: "Get Started with Automation"
excerpt: ""
---
Automation allows you to reduce the number of manual security tasks that you have to perform. To efficiently streamline your security processes, you can leverage Automation features that are available in InsightVM. These features allow you to automate tasks like containing vulnerable assets, patching vulnerabilities, and remediating risks.

To get started with Automation, you’ll need to complete the following tasks:

[Task 1: Install and Activate the Insight Orchestrator](doc:get-started-with-automation#section-task-1-install-and-activate-the-insight-orchestrator) 
[Task 2: Add Connections for Your Third-Party Tools](doc:get-started-with-automation#section-task-2-add-connections-for-your-third-party-tools) 
[Task 3: Specify the Scope for Automation Triggers](doc:get-started-with-automation#section-task-3-specify-the-scope-for-automation-triggers) 
[Task 4: Build Automation Workflows](doc:get-started-with-automation#section-task-4-build-automation-workflows) 

# Task 1: Install and Activate the Insight Orchestrator 

In order to connect InsightVM to the products, services, and tools you use in your environment, you’ll need to set up and activate the Insight Orchestrator. It is a component installed on your network that gives InsightVM the access it needs to automate security processes. You must have an orchestrator if you want to take advantage of the Automation Workflows available in InsightVM. 

Ready to get started? 

[Learn how to set up and activate the Insight Orchestrator. 
](https://insightconnect.help.rapid7.com/v1.0.0/docs/install-and-activate-the-orchestrator)

# Task 2: Add Connections for Your Third-Party Tools

InsightVM includes several out-of-the-box Workflow Templates built for third-party tools that you can leverage for your security needs. In order to use these templates, you’ll need to set up  Automation Connections. A connection comprises the credentials and required parameters, such as the application URL, that InsightVM needs to access and authenticate to a third-party tool. 

The out-of-the-box templates currently support the following third-party integrations: 

  * Microsoft SCCM
  * IBM BigFix
  * Cb Response
  * Palo Alto PAN-OS
  * Cisco ISE

Want to automatically patch a vulnerability with IBM BigFix? You’ll need to add a connection. 

[Learn how to add connections to your tools.](doc:workflows#section-connections) 

# Task 3: Specify the Scope for Automation Triggers
An Automation Trigger automatically invokes a Workflow based on a defined set of criteria. When you set up an Automation Workflow or Notification in InsightVM, you will need to select a trigger and define its scope using our specialized query language. A trigger can be any environmental or behavioral event that you want to use as the catalyst to start the Workflow. For example, if you want to receive notifications when certain assets are updated, you’ll need to build a query that matches those assets and the event type.  

Ready to scope your triggers?

[Learn how to use our query language.](doc:query-filter-guide) 

# Task 4: Build Automation Workflows
You can use Automation Workflows to do things like automate endpoint containment or patch a vulnerability. Workflows will automatically kick off when there is something happens in your environment that requires you to take action. Want to automatically patch a vulnerability? You can use the IBM BigFix Workflow. 

[Learn how to build Automation Workflows.](doc:workflows)