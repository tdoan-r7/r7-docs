---
title: "Configuring custom report templates"
excerpt: ""
---
The application includes a variety of built-in templates for creating reports. These templates organize and emphasize asset and vulnerability data in different ways to provide multiple looks at the state of your environment’s security. Each template includes a specific set of information sections.

If you are new to the application, you will find built-in templates especially convenient for creating reports. To learn about built-in report templates and the information they include, see [Report templates and sections](doc:report-templates-and-sections).

As you become more experienced with the application and want to tailor reports to your unique informational needs, you may find it useful to create or upload custom report templates.

##Fine-tuning information with custom report templates

Creating custom report templates enables you to include as much, or as little, scan information in your reports as your needs dictate. For example, if you want a report that lists assets organized by risk level, a custom report might be the best solution. This template would include only the Discovered System Information section. If you want a report that only lists vulnerabilities, you may create a document template with the Discovered Vulnerabilities section or create a data export template with vulnerability-related attributes.

You can also upload a custom report template that has been created by Rapid7 at your request to suit your specific needs. For example, custom report templates can be designed to provide high-level information presented in a dashboard format with charts for quick reference that include asset or vulnerability information that can be tailored to your requirements. Contact your account representative for information about having custom report templates designed for your needs. Templates that have been created for you will be provided to you.

After you create or upload a custom report template, it appears in the list of available templates on the _Template_ section of the _Create a report_ panel.

You must have permission to create a custom report template. To find out if you do, consult your Global Administrator. To create a custom report template, take the following steps:

1. Click the **Reports** icon in the Web interface.
OR
Click the **Create** tab at the top of the page and then select _Report_ from the drop-down list.
2. Click _Manage report templates_.
The _Manage report templates_ panel appears.
3. Click **New**.
The Security Console displays the _Create a New Report Template_ panel.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/2e2d30a-s_Create_a_new_report_template.jpg",
        "s_Create_a_new_report_template.jpg",
        1438,
        843,
        "#273042"
      ],
      "caption": "The Create a New Report Template panel"
    }
  ]
}
[/block]
##Editing report template settings

1. Enter a name and description for the new template on the _General_ section of the _Create a New Report Template_ panel.
[block:callout]
{
  "type": "info",
  "body": "If you are a Global Administrator, you can find out if your license enables a specific feature. Click the **Administration** tab and then the **Manage** link for the Security Console. In the _Security Console Configuration_ panel, click the **Licensing** link."
}
[/block]
2. Select the template type from the **Template type** drop-down list:
    * With a _Document_ template you will generate section-based, human-readable reports that contain asset and vulnerability information. Some of the formats available for this template type—Text, PDF, RTF, and HTML—are convenient for sharing information to be read by stakeholders in your organization, such as executives or security team members tasked with performing remediation.
    * With an _export_ template, the format is identified in the template name, either comma-separated-value (CSV) or XML files. CSV format is useful for integrating check results into spreadsheets, that you can share with stakeholders in your organization. Because the output is CSV, you can further manipulate the data using pivot tables or other spreadsheet features. See [Using Excel pivot tables to create custom reports from a CSV file](doc:working-with-report-formats#section-using-excel-pivot-tables-to-create-custom-reports-from-a-CSV-file). To use this template type, you must have the _Customizable CSV_ export featured enabled. If it is not, contact your account representative for license options. 
**Note:** Discovery scan results are not exportable in CSV format.
    * With the _Upload a template file_ option you can select a template file from a library. You will select the file to upload in the _Content_ section of the _Create a New Report Template_ panel.
[block:callout]
{
  "type": "warning",
  "body": "The Vulnerability details setting only affects document report templates. It does not affect data export templates."
}
[/block]
3. Select a level of vulnerability details from the drop-down list in the _Content_ section of the _Create a New Report Template_ panel.
Vulnerability details filter the amount of information included in document report templates:
   * _None_ excludes all vulnerability-related data.
   * _Minimal (title and risk metrics)_ excludes vulnerability solutions.
   * _Complete except for solutions_ includes basic information about vulnerabilities, such as title, severity level, CVSS score, and date published.
   * _Complete_ includes all vulnerability-related data.
4. Select your display preference:
   * _Display asset names only_
   * _Display asset names and IP addresses_
5. Select the sections to include in your template and click **Add**. See [Report templates and sections](doc:report-templates-and-sections).
Set the order for the sections to appear by clicking the up or down arrows.
6. (_Optional_) Click **Remove** to take sections out of the report.
7. (_Optional_) Add the _Cover Page_ section to include a cover page, logo, scan date, report date, and headers and footers. See [Adding a custom logo to your report](doc:configuring-custom-report-templates#section-adding-a-custom-logo-to-your-report) for information on file formats and directory location for adding a custom logo.
8. (_Optional_) Clear the check boxes to _Include scan data_ and _Include report date_ if you do not want the information in your report.
9. (_Optional_) Add the _Baseline Comparison_ section to select the scan date to use as a baseline. See [Selecting a scan as a baseline](doc:creating-a-basic-report#section-selecting-a-scan-as-a-baseline) for information about designating a scan as a baseline.
10. (Optional) Add the _Executive Summary_ section to enter an introduction to begin the report.
11. Click **Save**.

##Creating a custom report template based on an existing template
[block:callout]
{
  "type": "warning",
  "title": "NOTE",
  "body": "Only certain legacy reports templates can be copied for customization purposes.  Newer report templates do not support this feature."
}
[/block]
You can create a new custom report template based on a legacy template or existing custom report template. This allows you to take advantage of some of a template's useful features without having to recreate them as you tailor a template to your needs.

To create a custom template based on an existing template, take the following steps:

1. Click the **Reports** icon in the Web interface.
2. Click **Manage report templates**.
The _Manage report_ templates panel appears.
3. From the table, select a template that you want to base a new template on.
OR
If you have a large number of templates and don't want to scroll through all of them, start typing the name of a template in the _Find a report template_ text box. The Security Console displays any matches. The search is not case-sensitive.
4. Hover over the tool icon of the desired template. If it is a legacy built-in template, you will have the option to copy and then edit it. If it is a custom template, you can edit it directly unless you prefer to edit a copy. Select an option.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/23ba75e-s_nx_report_copy_template.jpg",
        "s_nx_report_copy_template.jpg",
        1373,
        743,
        "#e7ecee"
      ],
      "caption": "Selecting a report template to edit"
    }
  ]
}
[/block]
The Security Console displays the **Create a New Report Template** panel.

5. Edit settings as described in [Editing report template settings](doc:configuring-custom-report-templates#section-editing-report-template-settings). If you are editing a copy of a template, give the template a new name.
6. Click **Save**.
The new template appears in the template table.

##Adding a custom logo to your report

By default, a document report cover page includes a generic title, the name of the report, the date of the scan that provided the data for the report, and the date that the report was generated. It also may include the Rapid7 logo or no logo at all, depending on the report template. See [Cover Page](doc:report-templates-and-sections#section-cover-page). You can easily customize a cover page to include your own title and logo.
[block:callout]
{
  "type": "warning",
  "body": "Logos can be JPEG and PNG logo formats."
}
[/block]
To display your own logo on the cover page:

1. Copy the logo file to the designated directory of your installation.
   * In Windows: C:\Program Files\[installation_directory]\shared\reportImages\custom\silo\default.
2. Go to the _Cover Page Settings_ section of the _Create a New Report Template_ panel.
3. Enter the name of the file for your own logo, preceded by the word “image:” in the **Add logo** field.
Example: image:file_name.png. Do not insert a space between the word “image:” and the file name.
4. Enter a title in the **Add title** field.
5. Click **Save**.
6. Restart the Security Console. _Make sure to restart before you attempt to create a report with the custom logo_.