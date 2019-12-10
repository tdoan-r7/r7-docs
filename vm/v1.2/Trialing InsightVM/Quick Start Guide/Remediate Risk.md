---
title: "Remediate Risk"
excerpt: ""
---
# What is Risk?

Risk is a calculation of vulnerability exploitability on your assets.  While the method of calculation can vary, you should strive to keep your overall risk as low as possible.  After you’ve taken a look at what vulnerabilities are affecting your assets, you need a way to delegate and assign the task of remediation.  To this end, InsightVM has Remediation Workflow.

# What is Remediation Workflow?

Remediation Workflow is InsightVM’s security task tracking and management system.  Use this feature to create remediation projects, integrate with ticketing services, and automatically assign remediation tasks to members of your security team.  See [Remediation Workflow](doc:remediation-workflow) to learn more about its capabilities.

# Create a remediation project

Create a remediation project to address the vulnerabilities found on your assets.  See [Creating a Remediation Project](doc:remediation-workflow#section-creating-a-remediation-project) to learn how.
[block:callout]
{
  "type": "info",
  "title": "NOTE",
  "body": "The following ticketing integration and automation steps are only necessary if your organization uses an external ticketing solution.\n\nIf you do not currently use a ticketing solution, feel free to skip these steps."
}
[/block]
# Configure a ticketing integration (optional)

InsightVM features integration support for ticketing systems like JIRA and ServiceNow.  See [Ticketing Integration for Remediation Workflow Projects](doc:ticketing-integration-for-remediation-workflow-projects) for instructions on how to connect to these systems.

# Enable automated ticketing (optional)

Remediation projects already eliminate the need to distribute dense and lengthy reports to your security teams.  Why not do away with manual ticket creation as well?  Configure any of your existing ticketing connections to create and assign tickets automatically based on the criteria you specify.  See [Enabling Automated Ticketing for Remediation Projects](doc:ticketing-integration-for-remediation-workflow-projects#section-enabling-automated-ticketing-for-remediation-projects) for instructions.

# Create a remediation dashboard

The **Projects** tab isn’t the only place to view your ongoing remediation tasks.  Using the skills you learned in the last milestone, create a new dashboard dedicated to monitoring some different metrics of Remediation Workflow.  Give these particular cards a try:

* Remediators Requiring Assistance
* Top Remediated Vulnerabilities
* Top Remediators
[block:callout]
{
  "type": "success",
  "title": "Milestone complete!",
  "body": "Your team is on the job!  You should now have at least one remediation project that you can monitor going forward.  If you have access to a ticketing service like JIRA or ServiceNow, you should have a connection configured for one of those as well.\n\nLet’s move on to a newer type of asset being used in modern networks today.  It’s time to [Assess Containers](doc:assess-containers).\n\nReady to buy?  See our [Next Steps](doc:next-steps) page."
}
[/block]