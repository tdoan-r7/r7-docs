---
title: "Creating reports based on SQL queries"
excerpt: ""
---
You can run SQL queries directly against the reporting data model and then output the results in a comma-separated value (CSV) format. This gives you the flexibility to access and share asset and vulnerability data that is specific to the needs of your security team. Leveraging the capabilities of CSV format, you can create pivot tables, charts, and graphs to manipulate the query output for effective presentation.

##Prerequisites

To use the SQL Query Export feature, you will need a working knowledge of SQL, including writing queries and understanding data types.

You will also benefit from an [Understanding the reporting data model: Overview and query design](doc:understanding-the-reporting-data-model-overview-and-query-design), which maps database elements to business processes in your environments.

##Defining a query and running a report

1. Click the **Reports** icon in the Security Console Web interface.
OR
Click the **Create** tab at the top of the page and then select _Site_ from the drop-down list.
2. On the _Create a report_ page, select the **Export** option and then select the -SQL Query Export_ template from the carousel.
The Security Console displays a box for defining a query and a drop-down list for selecting a data model version. Currently, versions 1.2.0 and 1.1.0 are available. It is the current version and covers all functionality available in preceding versions.
3. _Optional:_ If you want to focus the query on specific assets, click the control to **Select Sites, Assets, or Asset Groups**, and make your selections. If you do not select specific assets, the query results will be based on all assets in your scan history.
4. _Optional:_ If you want to limit the query results with vulnerability filters, click the control to **Filter report scope based on vulnerabilities**, and make your selections.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/1c84ca0-s_nx_sql_start_define.jpg",
        "s_nx_sql_start_define.jpg",
        987,
        889,
        "#e9eeef"
      ],
      "caption": "Selecting the SQL Query Export template"
    }
  ]
}
[/block]
5. Click the text box for defining the query.
The Security Console displays a page for defining a query, with a text box that you can edit.
6. In this text box, enter the query.
**Tip:** Click the **Help** icon to view a list of sample queries. You can select any listed query to use it for the report.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/90e1b38-s_nx_sql_define_csh.jpg",
        "s_nx_sql_define_csh.jpg",
        1212,
        424,
        "#e8eeef"
      ],
      "caption": "Viewing a list of sample queries that you can use"
    }
  ]
}
[/block]
7. Click the **Validate** button to view and correct any errors with your query. The validation process completes quickly.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/ef54984-s_nx_sql_define_validate.jpg",
        "s_nx_sql_define_validate.jpg",
        1206,
        344,
        "#e4e7e7"
      ],
      "caption": "Viewing the message for a validated query"
    }
  ]
}
[/block]
8. Click the **Preview** button to verify that the query output reflects what you want to include in the report. The time required to run a preview depends on the amount of data and the complexity of the query.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/71e47ef-s_nx_sql_define_preview.jpg",
        "s_nx_sql_define_preview.jpg",
        1211,
        851,
        "#f3f5f4"
      ],
      "caption": "Viewing a preview of the query output"
    }
  ]
}
[/block]
9. If necessary, edit the query based on the validation or preview results. Otherwise, click the **Done** button to save the query and run a report.
[block:callout]
{
  "type": "info",
  "body": "If you click **Cancel**, you will not save the query."
}
[/block]
The Security Console displays the _Create a report_ page with the query displayed for reference.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/222bb37-s_nx_sql_run_report.jpg",
        "s_nx_sql_run_report.jpg",
        1019,
        501,
        "#eeedec"
      ],
      "caption": "Running the SQL query report"
    }
  ]
}
[/block]
10. Click **Save & run the report** or **Save the report**, depending on what you want to do.
11. For example, if you have a saved report and want to run it one time with an additional site in it, you could add the site, save and run, return it to the original configuration, and then just save.
12. In either case, the saved SQL query export report appears on the _View reports_ page.