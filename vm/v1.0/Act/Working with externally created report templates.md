---
title: "Working with externally created report templates"
excerpt: ""
---
The application provides built-in report templates and the ability to create custom templates based on those built-in templates. Beyond these options, you may want to use compatible templates that have been created outside of the application for your specific business needs.

See [Fine-tuning information with custom report templates](doc:configuring-custom-report-templates#section-fine-tuning-information-with-custom-report-templates) for information about requesting custom report templates.

Making one of these externally created templates available in the Security Console involves two actions:

1. downloading the template to the workstation that you use to access the Security Console
2. uploading the template to the Security Console using the _Reports_ configuration panel
[block:callout]
{
  "type": "warning",
  "body": "Your license must enable custom reporting for the template upload option to be available. Also, externally created custom template files must be approved by Rapid7 and archived in the .JAR format."
}
[/block]
After you have downloaded a template archive, take the following steps:

1. Click the **Reports** icon in the Security Console Web interface.
OR
Click the **Create** tab at the top of the page and then select _Report_ from the drop-down list.
2. Click _Manage report templates_.
The _Manage report templates_ panel appears.
3. Click **New**.
The Security Console displays the _Create a New Report Template_ panel.
4. Enter a name and description for the new template on the _General_ section of the _Create a New Report Template_ panel.
5. Select _Upload a template file_ from the **Template type** drop-down list.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/16eb2d7-s_reports_upload_a_template.jpg",
        "s_reports_upload_a_template.jpg",
        969,
        419,
        "#e9eeef"
      ],
      "caption": "Upload a report template file"
    }
  ]
}
[/block]
6. Click **Browse** in the **Select file** field to display a directory for you to search for custom templates.
7. Select the report template file and click **Open**.
The report template file appears in the _Select file_ field in the _Content_ section.
**Note:** Contact Technical Support if you see errors during the upload process.
8. Click **Save**.
The custom report template file will now appear in the list of available report templates on the _Manage report templates_ panel.