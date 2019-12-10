---
title: "Objective 4: Create and Assign Remediation Projects"
excerpt: ""
---
Now that you’ve established a Goal for your organization, it’s time to create and assign the remediation tasks required to achieve it..  Remediation Workflow, the security task tracking and management system in InsightVM, is the feature that makes this possible.  In short, if Goals define the standard that your security environment should reach, Remediation Workflow is how you get there.

Use Remediation Workflow to create remediation projects, integrate with ticketing services, and automatically assign these projects to members of your security team.  Remediation Workflow also uses the same [query language](doc:query-filter-guide) that you’ve used in previous objectives.

# Create a Remediation Project

Based on the target defined in your goal, create a remediation project to address the vulnerabilities found on your assets.  See the [Remediation Workflow](doc:remediation-workflow) page to learn how.

# Build a Remediation Dashboard

Aside from the **Projects** tab, you can monitor your ongoing remediation projects with specialized cards on your dashboard.  Build a custom dashboard just for Remediation Workflow monitoring using the skills you learned from the previous objective.  Give these particular cards a try:

* Remediators Requiring Assistance
* Top Remediated Vulnerabilities
* Top Remediators
[block:callout]
{
  "type": "info",
  "title": "NOTE",
  "body": "The following ticketing integration and automation steps are only necessary if your organization uses an external ticketing solution.\n\nIf you do not currently use a ticketing solution, you can skip these steps."
}
[/block]
# Configure a Ticketing Integration (Optional)

InsightVM features integration support for ticketing systems like JIRA and ServiceNow.  See [Ticketing Integration for Remediation Workflow Projects](doc:ticketing-integration-for-remediation-workflow-projects) for instructions on how to connect to these systems.

# Enable Automated Ticketing (Optional)

Remediation projects already eliminate the need to distribute dense and lengthy reports to your security teams.  Enable automated ticketing to do away with the need for manual ticket creation as well.  Configure any of your existing ticketing connections to create and assign tickets automatically based on the criteria you specify.  See the [Enable Automated Ticketing for Remediation Projects](doc:ticketing-integration-for-remediation-workflow-projects#section-enabling-automated-ticketing-for-remediation-projects) section to learn how.
[block:callout]
{
  "type": "success",
  "title": "Your team is on the job!",
  "body": "You should now have at least one remediation project that you can monitor going forward.  If you have access to a ticketing service like JIRA or ServiceNow, you should have a connection configured for one of those as well.\n\nFor your next objective, let’s talk about a newer type of asset being used in modern networks today.  It’s time to assess your containers."
}
[/block]