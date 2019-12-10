---
title: "Remediation Workflow"
excerpt: ""
---
Remediation Workflow is a feature that allows teams to coordinate on the progress of remediation initiatives. It provides visibility into the responsibilities of security and IT teams, so that they can easily track and measure the progress of remediation work.

* [Benefits of Remediation Workflow](doc:remediation-workflow#section-benefits-of-remediation-workflow)
* [Remediation Workflow Concepts](doc:remediation-workflow#section-remediation-workflow-concepts)
* [Creating a Remediation Project](doc:remediation-workflow#section-creating-a-remediation-project)
* [Viewing a Remediation Project](doc:remediation-workflow#section-viewing-a-remediation-project)
* [Remediation statuses](doc:remediation-workflow#section-remediation-statuses)
* [Automated ticketing for Remediation Projects](doc:remediation-workflow#section-automated-ticketing-for-remediation-projects)

# Benefits of Remediation Workflow

Remediation Workflow makes it simpler to prioritize, drive, and track remediation progress by showing you the true state of the remediation. Project metrics are automatically updated as vulnerabilities are found not to exist any more, so that you can fully visualize the achievements of your remediation teams.

With Remediation Workflow, you can:

* Communicate relevant context and prioritizations to the right people.
* Track the progress of remediation projects.
* Identify the remediation work that teams are working on at a glance.
* Automatically identify, assign, and monitor remediation progress.

# Remediation Workflow Concepts

* **Remediation project** - A remediation project is a group of solutions for vulnerabilities that need to be remediated on a specific set of assets within a certain time frame. When you create a remediation project, the Security Console applies an algorithm to identify solutions and aggregates the risk by solution to determine the remediation actions that will reduce the most risk.
* **Project owner** - A project owner has the ability to create a project, identify the assets and/or vulnerabilities that are contained in the project, and assign the project to other users.
* **Project assignee** - A project assignee is typically a remediation team member. Assignees review the solution steps and execute remediation for the specified assets and update the status of the solutions.

# Creating a Remediation Project

Open the **Projects** tab in your navigation menu.  On the “Remediation Projects” screen, click **Create a Project** to start the project creation wizard.
[block:callout]
{
  "type": "info",
  "title": "TIP",
  "body": "You can also start the project creation wizard from the expanded view of applicable cards.  See [Cards](doc:cards) to learn more."
}
[/block]
1. Provide your project with some basic information.
 * Ensure that your project name and description is purposeful and clear for your intended assignees.
2. Specify the project scope.
 * Determine whether your project will be **Static** or **Dynamic**.
 * Add query filters to define the project solution scope.  See [Advanced filter options](doc:advanced-filter-options) to learn how to build these filters.
 * Preview the included asset and vulnerability records by expanding the **\>** symbol next to each filter type.
[block:callout]
{
  "type": "warning",
  "title": "NOTE",
  "body": "You must apply both an asset and vulnerability filter to advance to the assignment step in the wizard."
}
[/block]

[block:callout]
{
  "type": "info",
  "title": "What are the differences between static and dynamic projects?",
  "body": "Static projects will not adjust their contents after the project is initially created.  Their qualifying data, based on your filters, will remain the same throughout the life of the project.  Static projects are commonly used for addressing specific asset and vulnerability groups.\n\nDynamic projects will automatically add and remove solutions as conditions change in your network, or if you decide to adjust the filters in use.  Dynamic projects are commonly used for ongoing maintenance, such as the remediation of any assets that surpass a certain level of risk."
}
[/block]
3. Assign the project to members of your security team.
 * Expand the assignment dropdown to select one or more InsightVM users that will work on this project.
 * If desired, check the permission box to allow users without InsightVM credentials to access the project via email.
 * Determine what level of access your assignee(s) will have to the project details.
4. Set a due date for the project.
[block:callout]
{
  "type": "warning",
  "title": "Automated ticketing configuration",
  "body": "The following step will only appear in your project creation wizard if you have a configured ticketing integration already available for use.\n\nSee [Ticketing Integration for Remediation Workflow Projects](doc:ticketing-integration-for-remediation-workflow-projects) to learn how to configure a new ticketing integration."
}
[/block]
5. Select one of your pre-configured ticketing systems to create, assign, and track remediation progress.

**Save and Complete** the wizard when finished.

# Viewing a Remediation Project

Click the **Projects** tab in the left navigation bar to access a list of remediation projects.  You also have the option to view a list of projects immediately after creating a new project.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/b31c811-projects_page.png",
        "projects_page.png",
        1918,
        983,
        "#3c4852"
      ]
    }
  ]
}
[/block]
Each row represents an individual remediation project. Click on a project row to view expanded summary, solution, asset, and vulnerability information.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/e1ccf00-projects_overview_details.png",
        "projects_overview_details.png",
        1920,
        983,
        "#3f4953"
      ]
    }
  ]
}
[/block]
Click any project name to open it.  The “Solutions” view will show overview details such as owner information, remediation steps, assets affected, and assignee information.  Individual solutions can also be expanded to show additional details.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/0e57573-solutions_overview_details.png",
        "solutions_overview_details.png",
        1919,
        982,
        "#3e4954"
      ]
    }
  ]
}
[/block]

[block:callout]
{
  "type": "info",
  "body": "Only Global Administrators can create, edit, and close projects. Anyone who is not a Global Administrator can view projects that they have been assigned."
}
[/block]
## Exporting Project and Solution data to CSV

Column data in both the **Projects** and **Solutions** pages can be exported to a CSV file.

To run an export:

1. Select all desired projects or solutions by enabling their respective checkboxes.
2. Expand the export dropdown and click **Export to CSV**.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/f30a8ad-projects_export.png",
        "projects_export.png",
        701,
        623,
        "#3e4650"
      ]
    }
  ]
}
[/block]

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/1bf2d62-solutions_export.png",
        "solutions_export.png",
        1116,
        613,
        "#404851"
      ]
    }
  ]
}
[/block]
Asset and vulnerability data can also be exported from the solution drawer:

1. Click the desired solution row to open the drawer.
2. Select the **Vulnerability** or **Asset** tab.
3. Enable the checkbox of each desired row.
4. Expand the export dropdown and click **Export to CSV**.
[block:callout]
{
  "type": "info",
  "body": "Assets listed in the solution drawer can be filtered by the following statuses:\n\n* All\n* Remediated\n* Unresolved"
}
[/block]

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/0d052bf-solution_drawer_export.png",
        "solution_drawer_export.png",
        1500,
        853,
        "#434e59"
      ]
    }
  ]
}
[/block]
# Remediation statuses
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/f8e3111-remediation_workflow_state_machine.jpg",
        "remediation_workflow_state_machine.jpg",
        8298,
        6688,
        "#3b424a"
      ]
    }
  ]
}
[/block]
# Automated ticketing for Remediation Projects

You can make your remediation projects more effective by automatically assigning work items to the team members responsible for mitigating exposures. For more information, see [Ticketing Integration for Remediation Workflow Projects](doc:ticketing-integration-for-remediation-workflow-projects).