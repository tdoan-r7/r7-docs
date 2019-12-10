---
title: "Ticketing Integration"
excerpt: ""
---
Many security teams manage remediation efforts by generating CSV or PDF reports spanning hundreds of pages and spend a lot of time breaking down exposures into actionable work items. InsightAppSec integrates with JIRA Cloud so that security teams can automate the creation and assignment of work items based on pre-configured rules.

The automated ticketing feature simplifies this process while allowing you to:

  * Create targeted and precise tickets automatically with rules that can be reused across projects.
  * Customize ticketing templates to include as much security context as you need.
  * Let your remediation teams continue to use their existing tools and processes.

## Creating a JIRA ticketing connection 

1. Click on the **Administration** icon in the sidebar. 
2. On the *Administration* page, click on the **Add a new JIRA server** link under the *Integrations* panel.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/63de38a-Administration_Page.png",
        "Administration Page.png",
        902,
        360,
        "#454f5f"
      ],
      "caption": "Integrations panel in the Administration page"
    }
  ]
}
[/block]
3. In the *New JIRA Server Connection* form, enter a name for this new connection as well as the URL, username, and password of your JIRA cloud connection and press **Save**. 
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/e89d566-New_JIRA_server_connection.png",
        "New JIRA server connection.png",
        1030,
        1158,
        "#3e4654"
      ],
      "caption": "Enter your JIRA connection details"
    }
  ]
}
[/block]
4. You will see the *Project Configurations for InsightAppSec* screen where you can set up various *configurations* for your JIRA ticketing project. A configuration is a set of rules that InsightAppSec uses to determine the Type, Status, Priority, and contents of automatically generated tickets. 
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/10bbfb3-Project_Configurations.png",
        "Project Configurations.png",
        3520,
        626,
        "#3e4653"
      ],
      "caption": "Click on the New Configuration button"
    }
  ]
}
[/block]
Click on the *New Configuration* button. 
5. In the *Configuration* panel, provide a unique name for the configuration. Select the projects where you would like to apply this configuration, the JIRA Project Key, and the Issue Type (e.g. Task, Bug, Story). 
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/ef36a66-Project_Information.png",
        "Project Information.png",
        1294,
        1053,
        "#444c5c"
      ],
      "caption": "Enter the Project Information for the new configuration"
    }
  ]
}
[/block]

[block:callout]
{
  "type": "info",
  "body": "You can always edit the configuration in the future, but changing the Project Key or Issue type will reset all status and priority mappings.",
  "title": "Note"
}
[/block]
 6. Enter mappings for InsightAppSec statuses to JIRA statuses. For example, you may wish to show all 'Remediated' vulnerabilities in 'Done' state in JIRA.

7. Enter mappings for Priority.
8. In the Ticketing Template tab, set up what the Summary and Description in the ticket will say. You can use the special syntax to have terms from vulnerability description to be automatically added to the ticket.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/6689893-Ticketing_Template.png",
        "Ticketing Template.png",
        1300,
        2066,
        "#444d5d"
      ],
      "caption": "Use the predictive text to have terms from vulnerability description to be automatically added to your ticket"
    }
  ]
}
[/block]
When all the required fields are completed, the **Save** button will be enabled. Press the **Save** button to save your configuration. If you wish to edit an existing JIRA connection, you will also be able to do so from the *Integrations* panel on the *Administration* page. 

## Creating JIRA tickets based on InsightAppSec vulnerabilities
1. Visit the Scan Details page of any App for which you have set up a Project Configuration already, or the *All Vulnerabilities* page. 
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/beb5c43-Export_to_JIRA_button.png",
        "Export to JIRA button.png",
        3644,
        1440,
        "#3e4754"
      ]
    }
  ]
}
[/block]
2. Select the vulnerabilities that you wish to export and click on the **Export to JIRA** button.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/c3cc624-Screen_Shot_2017-11-25_at_6.24.13_PM.png",
        "Screen Shot 2017-11-25 at 6.24.13 PM.png",
        1542,
        520,
        "#434c5c"
      ]
    }
  ]
}
[/block]
Note that changes to vulnerabilities in InsightAppSec are not automatically reflected in JIRA, and need to be explicitly ported using the 'Export to JIRA' functionality.