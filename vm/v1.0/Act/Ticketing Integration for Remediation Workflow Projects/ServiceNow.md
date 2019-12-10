---
title: "ServiceNow"
excerpt: ""
---
# ServiceNow integration requirements

The integration with ServiceNow currently requires the URL of a ServiceNow server that accepts inbound communication from the Rapid7 Insight Platform and an account with the following roles:

* admin
**OR**
* itil_admin
* itil
* mid_server
* report_admin
* personalize_choices

The minimum roles above will allow you to create a connection, but you must be aware of other fields required to create a ticket. If the account does not have access to a required field, you may not be able to save field mappings correctly.
[block:callout]
{
  "type": "warning",
  "title": "NOTE",
  "body": "If your ServiceNow instance is configured with an IP whitelist, see [Configure communications with the Insight platform](doc:configure-communications-with-the-insight-platform) for current Insight whitelist IPs."
}
[/block]
## Configuring Access Control rules

You may need to modify role privileges within ServiceNow for your ticketing connection to function properly.  Open your ServiceNow interface to start this procedure.
[block:callout]
{
  "type": "warning",
  "title": "REQUIRED",
  "body": "You must be a System Administrator with modification privileges to make these changes.  Check the user settings dropdown to verify your access before proceeding."
}
[/block]
1. On your navigation menu, click the **All Applications** tab.
2. Browse to **System Security** and expand it.
3. Click **Access Control (ACL)**.
4. On the "Access Controls" page, check that the following records are in place:
[block:callout]
{
  "type": "warning",
  "title": "NOTE",
  "body": "Make sure all the following Access Controls are enabled as “Active”."
}
[/block]

[block:parameters]
{
  "data": {
    "h-0": "Access Control name",
    "h-1": "Operation",
    "h-2": "Field",
    "h-3": "Value",
    "0-0": "incident",
    "0-1": "create",
    "0-2": "N/A",
    "0-3": "N/A",
    "1-0": "incident",
    "1-1": "read",
    "1-2": "\"Requires role\"",
    "1-3": "\"itil\" role is specified",
    "2-0": "incident",
    "2-1": "read",
    "2-2": "\"Script\"",
    "2-3": "Script contains the following:"
  },
  "cols": 4,
  "rows": 3
}
[/block]
```
current.opened_by == gs.getUserID() || current.caller_id == gs.getUserID() || current.watch_list.indexOf(gs.getUserID()) > -1;
```
[block:parameters]
{
  "data": {
    "0-0": "incident",
    "0-1": "write",
    "0-2": "\"Requires role\"",
    "0-3": "\"itil\" role is specified",
    "1-0": "sys_choice",
    "1-1": "read",
    "1-2": "\"Requires role\"",
    "1-3": "\"personalize_choices\" role is specified",
    "h-0": "Access Control name",
    "h-1": "Operation",
    "h-2": "Field",
    "h-3": "Value"
  },
  "cols": 4,
  "rows": 2
}
[/block]

[block:callout]
{
  "type": "warning",
  "title": "NOTE",
  "body": "You should have access to all Create Read Update Delete (CRUD) operations by default if you have the “personalize_choices” role."
}
[/block]

[block:parameters]
{
  "data": {
    "0-0": "sys_user",
    "0-1": "read",
    "0-2": "N/A",
    "0-3": "N/A",
    "1-0": "sys_user_group",
    "1-1": "read",
    "1-2": "N/A",
    "1-3": "N/A",
    "2-0": "sys_user_has_role",
    "2-1": "read",
    "2-2": "\"Requires role\"",
    "2-3": "\"itil\" role is specified",
    "h-0": "Access Control name",
    "h-1": "Operation",
    "h-2": "Field",
    "h-3": "Value"
  },
  "cols": 4,
  "rows": 3
}
[/block]
# Creating a new ServiceNow ticketing connection in Remediation Workflow
[block:callout]
{
  "type": "info",
  "body": "ServiceNow integration does not require the ServiceNow Vulnerability Response module."
}
[/block]
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
3. On the **Settings** > **Connections** view, click the _ServiceNow_ ticketing option in the ticketing area.
4. On the **Connection Settings** page, enter the URL of your ServiceNow server and the credentials to an account with the required permissions.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/ab886b7-Ticketing_servicenow_ConnectionSettings1.png",
        "Ticketing_servicenow_ConnectionSettings1.png",
        755,
        395,
        "#444d5c"
      ]
    }
  ]
}
[/block]
5. Click **Solution Status Mapping** to map one or more JIRA issues statuses to one of the following  Remediation Project statuses: 
   * **Awaiting Verification** - The remediator has taken action to mitigate the vulnerability and is now awaiting verification, the vulnerability no longer exists, or the remediation failed.
   * **Will Not Fix** - The item cannot be remediated.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/70349ec-ticketing_serviceNow_solution_status.JPG",
        "ticketing_serviceNow_solution_status.JPG",
        786,
        265,
        "#424a59"
      ]
    }
  ]
}
[/block]

[block:callout]
{
  "type": "warning",
  "title": "NOTE",
  "body": "Changing the status of a ServiceNow ticket can change the status of a remediation solution, but changing the solution status will not change a ServiceNow ticket's status. The integration will add a comment to the ticket to notify the ticket owner of the updated state."
}
[/block]
 6. Click **Configurations**, and then click **New Configuration**. The ticketing template wizard opens to the **Ticketing Connection** page. The ticketing template wizard has three pages:

Complete the **Ticketing Connection** page to select the ServiceNow project for automated ticketing and the type of work item that you want to create, e.g Task.  The available **Issue Types** are based on the Project Name that you select. Click **Next** to continue to the **Ticketing Project and Field Mapping** page.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/0d0e5aa-ticketing_service_now_ticketing_connection.JPG",
        "ticketing_service_now_ticketing_connection.JPG",
        751,
        315,
        "#434b5a"
      ]
    }
  ]
}
[/block]
Complete the **Ticketing Project and Field Mapping** page to draft a template of the ticket that you generate from your Remediation Project. You can configure how concise or detailed you want the summary and description to be with variables for information, such as a solution name ($SOL_NAME), asset list ($ASSET_NAME_LIST), and other data related to your vulnerability scans. Click the **Syntax Help** button to open a dictionary that lists all of the supported placeholders. Click **Next** to continue to the **Assignment Rules** page.

Complete the **Assignment Rules** page to create rules for assigning automatically generated tickets to your team based on factors like the ownership of assets and the expertise of the assignees. The list of rules ordered by **preference**.  Every ticket is assigned based on the first rule whose asset filter conditions are satisfied. If no rule is matched, the incident is assigned to the _Default Assignee_. Click on the **+New Rule** button to create additional rules.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/057c8db-rw_sn_asset_filter_suggestions.PNG",
        "rw_sn_asset_filter_suggestions.PNG",
        951,
        391,
        "#444d5c"
      ]
    }
  ]
}
[/block]
7. When you are done creating all of the necessary rules, click **Save** and exit from the ticketing wizard.

##Editing a ticketing connection for Remediation Projects
To edit a ticketing connection:
1. Click the **Management** tab.
2. Click **Edit** for the ticketing connection that you want to edit.
3. Edit the **Connection Settings**, **Solution Status**, and **Configuration** pages as necessary.