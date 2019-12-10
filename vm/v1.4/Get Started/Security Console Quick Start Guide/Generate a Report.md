---
title: "Generate a Report"
excerpt: ""
---
Now that you’ve [created and scanned your first site](doc:create-and-scan-a-site), it’s time to generate your first report that will detail the findings.

# Reports Translate Your Scan Results Into Actionable Insights

The Security Console features a wealth of different report templates, all of which are designed to turn scan data into meaningful and actionable information.  You can apply these reports to a variety of business needs, including providing remediation plans to your security team and documenting organizational policy compliance efforts.

InsightVM categorizes each report template according to one of the following groups:

* **Document** - Report templates in this category are generated for readability with several file formats to choose from, such as PDF and RTF, and contextualize your scan data with a variety of visual aids, color-coded graphs, and tables.  Choose from over 30 different templates geared toward specific use cases and organizational needs.
* **Export** - Depending on the selected template, reports in this category are formatted in either XML, CSV, or exported to a compliant database of your choosing.  Several report templates in this category are designed to detail policy compliance and satisfy organizational audit requirements.  In particular, you can use the SQL Query Export report to create highly customizable reports based on queries of the Security Console database.
[block:callout]
{
  "type": "info",
  "title": "TIP",
  "body": "You can learn more about available report templates on the [Report templates and sections](doc:report-templates-and-sections) page."
}
[/block]
# Objective

For the purpose of this guide, you will generate a **Top Remediations with Details** report scoped to the scan results of the site you created previously.

The **Top Remediations with Details** report template is an excellent choice for this exercise given its focus and level of detail.  This report lists the 25 remediations that, when implemented, stand to reduce the greatest risk currently affecting your specified scope of assets.  It also includes easy-to-read remediation instructions for all 25 solutions.  As a result, it is a clearly defined report that is easy to follow and completing its remediation tasks will make an immediate impact on asset security.

# Generate Your First Report

From the **Home** page of your Security Console, click the **Reports** tab in your left navigation menu.  The Security Console displays the report configuration screen, which is composed of three clickable tabs for creating new reports, viewing saved reports, and managing existing report templates.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/8df3d81-securityconsole_create_a_report.png",
        "securityconsole_create_a_report.png",
        1050,
        911,
        "#eceff0"
      ]
    }
  ]
}
[/block]
To create your first report:

1. Click the **Create a report** tab.
2. Give your report a name.
 * Report names often indicate the asset scope and the report template in use. This ensures that the report is easily recognizable in the **View report** tab after the report is saved.
3. If desired, adjust the time zone that will be stamped on the report by making a selection in the provided dropdown list.
 * The Security Console chooses the default time zone according to what is detected on its host machine.
4. Under “Template”, make sure that the **Document** tab is selected.
5. Browse to and select the **Top Remediations with Details** report template.
6. Next to “File format”, make sure **PDF** is selected.
 * RTF and HTML formats are also available for this report template, but Rapid7 recommends the PDF format for readability and portability.
7. Next to “Scope”, click **Select Scan**.  A site selection window displays.
8. Find the site you created previously and click its corresponding radio button to select it.  Click **Select Scan** when ready.
9. From the “Select Scan” window, select the most recent scan for this site and click **OK**.
10. Next to “Frequency”, make sure **Do not run a recurring report** is selected.
 * Recurring reports are a great idea for production scanning environments.  That being said, you only need a single report for this exercise.
11. Review your report configuration and verify that everything is correct.  Click **Save & Run the Report** when ready.
 * This option both saves your report configuration and generates the report in a single click.

# View Your Report

After you save and generate your first report, the Security Console takes you directly to the **View reports** tab.  Your report appears at the top of the list and indicates that generation is in progress.

When your report finishes generating, click the report name link to open it.

## How to Read This Report

As explained previously, the **Top Remediations with Details** report lists the top 25 solutions that encompass the biggest risk impact according to your specified report scope.  Now that you have this report ready, take a look at the suggested remediations.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/5eb5fdc-top25withdetails_headermetrics.png",
        "top25withdetails_headermetrics.png",
        724,
        243,
        "#c2af8e"
      ]
    }
  ]
}
[/block]
The first page includes a header with several notable metrics, the most important of which is the “Will Remediate” section.  As long as you complete all the remediation tasks suggested by the report, your asset stands to reduce its overall vulnerabilities and associated risk by the percentages shown.

The remediations table follows the header.  Each remediation is listed in brief, along with its vulnerability count and total risk.  Additional pages of this report detail each of these solutions further and provide you with specific remediation steps.

With this information at hand, you can immediately improve the security of your asset.

# Manage Your Report

If you return to the **View reports** tab, you can also hover your mouse over the report entry to access additional options:

* **Run** - Regenerates the report according to its saved configuration.
* **Edit** - Takes you to the report configuration, where you can make any changes as needed.
* **Copy** - Copies the report configuration as a separate entry on the reports list.
* **Delete** - Deletes the report configuration and any generated report history attached to it.
* **History** - Displays a report generation history table.  You can access an individual report instance by clicking one of the date links shown in this window.
[block:callout]
{
  "type": "success",
  "title": "You’re ready to take action!",
  "body": "Now that you have your report, your remediation team will know exactly what needs to be fixed and how to fix it.  While this exercise does provide extensive value, keep in mind that this is just the tip of the iceberg when it comes to reporting in InsightVM."
}
[/block]