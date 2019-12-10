---
title: "JIRA"
excerpt: ""
---
#JIRA integration requirements

The integration with JIRA currently requires the URL of a JIRA server that accepts inbound communication from the Rapid7 Insight Platform and an account with the following permissions:

* Browse projects
* View read-only workflow
* Assignable user
* Create issues
* Assign issues
* Edit issues
* Close issues
* Delete issues
* Modify reporter
* Set issue security
* Add comments

The minimum permissions above allow you to create a connection, but you must be aware of other fields required to create a ticket. If the account does not have access to a required field you may not be able to save field mappings correctly.
[block:callout]
{
  "type": "warning",
  "title": "NOTE",
  "body": "If your JIRA instance is configured with an IP whitelist, see [Configure communications with the Insight platform](doc:configure-communications-with-the-insight-platform) for current Insight whitelist IPs."
}
[/block]
# Creating a new JIRA ticketing connection in Remediation Workflow

1. Click the **Projects** tab.
2. On the **Remediation Projects** page, click **Add a ticketing connection**. 

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/b934bd9-new_ticketing_connection.png",
        "new_ticketing_connection.png",
        1918,
        467,
        "#3a444f"
      ]
    }
  ]
}
[/block]
3. On the **Settings** > **Connections** view, click the _Jira Software_ ticketing option in the ticketing area.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/b26e76d-ticketing_select_server.JPG",
        "ticketing_select_server.JPG",
        627,
        330,
        "#404856"
      ]
    }
  ]
}
[/block]
4. On the **Connection Settings** page, enter the URL of your JIRA server and the credentials to an account with the required permissions.
[block:callout]
{
  "type": "warning",
  "title": "NOTE",
  "body": "The email address associated with your JIRA account is NOT your JIRA username.  The “Username” field is intended for JIRA usernames only."
}
[/block]

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/9e7f9bc-ticketing_connection_settings1_1.png",
        "ticketing_connection_settings1 (1).png",
        1239,
        518,
        "#434d5b"
      ]
    }
  ]
}
[/block]
5. Click **Save**. 
6. Click **Solution Status Mapping** to map one or more JIRA issue statuses to one of the following  Remediation Project statuses: 
   * **Awaiting Verification** - The remediator has taken action to mitigate the vulnerability and is now awaiting verification, the vulnerability no longer exists, or the remediation failed.
   * **Will Not Fix** - The item cannot be remediated.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/7ffe553-ticketing_solution_status_mapping.JPG",
        "ticketing_solution_status_mapping.JPG",
        751,
        933,
        "#434c5c"
      ]
    }
  ]
}
[/block]

[block:callout]
{
  "type": "warning",
  "title": "NOTE",
  "body": "Changing the status of a JIRA ticket can change the status of a remediation solution, but changing the solution status will not change a JIRA ticket's status. The integration will add a comment to the ticket to notify the ticket owner of the updated state."
}
[/block]
7. Click **Save**. The ticketing template wizard opens to the **Ticketing Connection** page. The ticketing template wizard has three pages: 

Complete the **Ticketing Connection** page to select the JIRA project for automated ticketing and the type of work item that you want to create, e.g Task.  The available **Issue Types** are based on the Project Name that you select. Click **Next** to continue to the **Ticketing Project and Field Mapping** page.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/5ea8482-ticketing_ticketing_connection1.png",
        "ticketing_ticketing_connection1.png",
        720,
        356,
        "#434c54"
      ]
    }
  ]
}
[/block]
Complete the **Ticketing Project and Field Mapping** page to draft a template of the ticket that you generate from your Remediation Project. You can configure how concise or detailed you want the summary and description to be with variables for information, such as a solution name ($SOL_NAME), asset list ($ASSET_NAME_LIST), and other data related to your vulnerability scans. 
Click the **Syntax Help** button to open a dictionary that lists all of the supported placeholders. Click **Next** to continue to the **Assignment Rules** page.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/1446ccb-ticketing_project_and_field_mapping1.png",
        "ticketing project and field mapping1.png",
        1024,
        907,
        "#424b53"
      ]
    }
  ]
}
[/block]
Complete the **Assignment Rules** page to create rules for assigning automatically generated tickets to your team based on factors like the ownership of assets and expertise of the assignees. The list of rules is ordered by **preference**.  Every ticket is assigned based on the first rule whose asset filter conditions are satisfied. If no rule is matched, the incident is assigned to the _Default Assignee_. Click on the **+New Rule** button to create additional rules.  
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/5b9eb0c-ticketing_assignment_rules1.png",
        "ticketing_assignment_rules1.png",
        720,
        546,
        "#434c54"
      ]
    }
  ]
}
[/block]
8. When you are done creating all of the necessary rules, click **Save** to exit from the ticketing wizard. 

# Editing a ticketing connection for Remediation Projects
To edit a ticketing connection:
1. Click the **Management** tab.
2. Click **Edit** for the ticketing connection that you want to edit.
3. Edit the **Connection Settings**, **Solution Status**, and **Configuration** pages as necessary.