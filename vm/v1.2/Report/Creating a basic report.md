---
title: "Creating a basic report"
excerpt: ""
---
Creating a basic report involves the following steps:

* Selecting a report template and format (see [Starting a new report configuration](doc:creating-a-basic-report#section-starting-a-new-report-configuration))
* [Selecting assets to report on](doc:creating-a-basic-report#section-selecting-assets-to-report-on)
* [Filtering report scope with vulnerabilities](doc:creating-a-basic-report#section-filtering-report-scope-with-vulnerabilities) (optional)
* [Configuring report frequency](doc:creating-a-basic-report#section-configuring-report-frequency) (optional)

There are additional configuration steps for the following types of reports:

* Export see [Entering CyberScope information](doc:creating-a-basic-report#section-entering-cyberscope-information) 
* [Configuring an XCCDF report](doc:creating-a-basic-report#section-configuring-an-xccdf-report) 
* [Configuring an ARF report](doc:creating-a-basic-report#section-configuring-an-asset-reporting-format-arf-export) 
* Database Export see [Distributing, sharing, and exporting reports](doc:distributing-sharing-and-exporting-reports)
* Baseline reports see [Selecting a scan as a baseline](doc:creating-a-basic-report#section-selecting-a-scan-as-a-baseline)
* Risk trend reports see [Working with risk trends in reports](doc:working-with-risk-trends-in-reports)

After you complete a basic report configuration, you will have the option to configure additional properties, such as those for distributing the report.

You will have the options to either save and run the report, or just to save it for future use. For example, if you have a saved report and want to run it one time with an additional site in it, you could add the site, save and run, return it to the original configuration, and then just save. See [Viewing, editing, and running reports](doc:viewing-editing-and-running-reports).

##Starting a new report configuration

1. Click the **Reports** icon.
OR
Click the **Create** tab at the top of the page and then select _Report_ from the drop-down list.
The Security Console displays the _Create a report_ panel.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/296e068-s_Configure_a_report_tab.jpg",
        "s_Configure_a_report_tab.jpg",
        1010,
        525,
        "#e0e4e6"
      ],
      "caption": "The Create a report panel"
    }
  ]
}
[/block]
2. Enter a name for the new report. The name must be unique in the application.
3. Select a time zone for the report. This setting defaults to the local Security Console time zone, but allows for the time localization of generated reports.
4. (_Optional_) Enter a search term, or a few letters of the template you are looking for, in the **Search templates** field to see all available templates that contain that keyword or phrase. For example, enter pci and the display will change to display only PCI templates.
> Search results are dependent on the template type, either **Document** or **Export** templates. If you are unsure which template type you require, make sure you select **All** to search all available templates.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/35b7577-s_search_pci_reports.jpg",
        "s_search_pci_reports.jpg",
        1007,
        385,
        "#467690"
      ],
      "caption": "Search report templates"
    }
  ]
}
[/block]

[block:callout]
{
  "type": "info",
  "body": "Resetting the **Search templates** field by clicking the close X displays all templates in alphabetical order."
}
[/block]
5. Select a template type:
 * _Document_ templates are designed for section-based, human-readable reports that contain asset and vulnerability information. Some of the formats available for this template type—Text, PDF, RTF, and HTML—are convenient for sharing information to be read by stakeholders in your organization, such as executives or security team members tasked with performing remediation.
 * _Export_ templates are designed for integrating scan information into external systems. The formats available for this type include various XML formats, Database Export, and CSV. For more information, see [Working with report formats](doc:working-with-report-formats).
6. Click **Close** on the **Search templates** field to reset the search or enter a new term.

The Security Console displays template thumbnail images that you can browse, depending on the template type you selected. If you selected the _All_ option, you will be able to browse all available templates. Click the scroll arrows on the left and the right to browse the templates.

You can roll over the name of any template to view a description.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/b37c5ee-s_report_config_rollover_tempalte_name.jpg",
        "s_report_config_rollover_tempalte_name.jpg",
        1004,
        514,
        "#456d83"
      ],
      "caption": "Selecting a report template"
    }
  ]
}
[/block]
You also can click the **Preview** icon in the lower right corner of any thumbnail (highlighted in the preceding screen shot) to enlarge and click through a preview of template. This can be helpful to see what kind of sections or information the template provides.

When you see the see the desired template, click the thumbnail. It becomes highlighted and displays a _Selected_ label in the top, right corner.

7. Select a format for the report. Formats not only affect how reports appear and are consumed, but they also can have some influence on what information appears in reports. For more information, see [Working with report formats](doc:working-with-report-formats).
**Tip:** See [descriptions of all available report templates](doc:report-templates-and-sections) to help you select the best template for your needs.

If you are using the _PCI Attestation of Compliance_ or _PCI Executive Summary_ template, or a custom template made with sections from either of these templates, you can only use the RTF format. These two templates require ASVs to fill in certain sections manually.

8. (Optional) Select the language for your report: Click **Advanced Settings**, select **Language**, and choose an output language from the drop-down list.
To change the default language of reports, click your user name in the upper-right corner, select User **Preferences**, and select a language from the drop-down list. The newly selected default will apply to reports that you create after making this change. Reports created prior to the change retain their original language, unless you update them in the report configuration.
9. If you are using the CyberScope XML Export format, enter the names for the component, bureau, and enclave in the appropriate fields. For more information see [Entering CyberScope information](doc:creating-a-basic-report#section-entering-cyberscope-information). Otherwise, continue with specifying the scope of your report.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/043b450-s_cyberScope_section.jpg",
        "s_cyberScope_section.jpg",
        995,
        516,
        "#466f85"
      ],
      "caption": "Configuring a CyberScope XML Export report"
    }
  ]
}
[/block]
##Entering CyberScope information

When configuring a CyberScope XML Export report, you must enter additional information, as indicated in the _CyberScope Automated Data Feeds Submission Manual_ published by the U.S. Office of Management and Budget. The information identifies the entity submitting the data:

* **Component** refers to a reporting component such as _Department of Justice, Department of Transportation, or National Institute of Standards and Technology_.
* **Bureau** refers to a component-bureau, an individual Federal Information Security Management Act (FISMA) reporting entity under the component. For example, a bureau under Department of Justice might be _Justice Management Division or Federal Bureau of Investigation_.
* **Enclave** refers to an enclave under the component or bureau. For example, an enclave under Department of Justice might be _United States Mint_. Agency administrators and agency points of contact are responsible for creating enclaves within CyberScope.

Consult the _CyberScope Automated Data Feeds Submission Manual_ for more information.

You must enter information in all three fields.

##Configuring an XCCDF report

If you are creating one of the XCCDF reports, and you have selected one of the XCCDF formatted templates on the _Create a report_ panel take the following steps:
[block:callout]
{
  "type": "info",
  "body": "You cannot filter vulnerabilities by category if you are creating an XCCDF or CyberScope XML report."
}
[/block]
1. Select an XCCDF report template on the _Create a report_ panel.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/3f265cd-s_xccdf_report.jpg",
        "s_xccdf_report.jpg",
        1008,
        514,
        "#496d82"
      ],
      "caption": "Select an XCCDF formatted report template"
    }
  ]
}
[/block]
2. Select the policy results to include from the drop-down list.
The **Policies** option only appears when you select one of the XCCDF formats in the _Template_ section of the _Create a report_ panel.
3. Enter a name in the **Organization** field.
4. Proceed with asset selection. Asset selection is only available with the XCCDF Human Readable CSV Export.
[block:callout]
{
  "type": "info",
  "body": "As described in Selecting Policy Manager checks, the major policy groups regularly release updated policy checks. The XCCDF report template will only generate reports that include the updated policy. To be able to run a report of this type on a scan that includes a policy that just changed, re-run the scan."
}
[/block]
##Configuring an Asset Reporting Format (ARF) export

Use the Asset Reporting Format (ARF) export template to submit policy or benchmark scan results to the U.S. government in compliance with Security Content Automation Protocol (SCAP) 1.2 requirements. To do so, take the following steps:
[block:callout]
{
  "type": "info",
  "body": "To run ARF reports you must first run scans that have been configured to save SCAP data. See [Selecting Policy Manager checks](doc:selecting-policy-manager-checks) for more information."
}
[/block]
1. Select the ARF report template on the _Create a report_ panel.
2. Enter a name for the report in the **Name** field.
3. Select the site, assets, or asset groups to include from _Scope_ section.
4. Specify other advanced options for the report, such as report access, file storage, and distribution list settings.
5. Click **Run the report**.
The report appears on the _View reports_ page.

##Selecting assets to report on

1. Click **Select sites, assets, asset groups, or tags** in the Scope section of the _Create a report_ panel. The tags filter is available for all report templates except Audit Report, Baseline Comparison, Executive overview, Database export and XCCDF Human Readable CSV Export.
2. To use only the most recent scan data in your report, select **Use the last scan data only** check box. Otherwise, the report will include all historical scan data in the report.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/7e9111e-s_nx_select_report_scope.jpg",
        "s_nx_select_report_scope.jpg",
        1230,
        308,
        "#2c2c3c"
      ],
      "caption": "Select Report Scope panel"
    }
  ]
}
[/block]
**Tip:** The asset selection options are not mutually exclusive. You can combine selections of sites, asset groups, and individual assets.

3. Select _Sites_, _Asset Groups_, _Assets_, or _Tags_ from the drop-down list.
4. If you selected _Sites_, _Asset Groups_,  or _Tags_, click the check box for any displayed site or asset group to select it. You also can click the check box in the top row to select all options.
If you selected _Assets_, the Security Console displays search filters. Select a filter, an operator, and then a value.

For example, if you want to report on assets running Windows operating systems, select the operating system filter and the _contains_ operator. Then enter _Windows_ in the text field.

To add more filters to the search, click the + icon and configure your new filter.

Select an option to match any or all of the specified filters. Matching any filters typically returns a larger set of results. Matching all filters typically returns a smaller set of results because multiple criteria make the search more specific.

Click the check box for any displayed asset to select it. You also can click the check box in the top row to select all options.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/56335bd-s_select_report_scope_assets.jpg",
        "s_select_report_scope_assets.jpg",
        1688,
        819,
        "#272f3d"
      ],
      "caption": "Selecting assets to report on"
    }
  ]
}
[/block]
5. Click **OK** to save your settings and return the _Create a report_ panel. The selections are referenced in the _Scope_ section.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/a3f46e6-s_nx_select_report_scope_section.jpg",
        "s_nx_select_report_scope_section.jpg",
        659,
        160,
        "#dadadb"
      ],
      "caption": "The Scope section"
    }
  ]
}
[/block]
##Filtering report scope with vulnerabilities

Filtering vulnerabilities means including or excluding specific vulnerabilities in a report. Doing so makes the report scope more focused, allowing stakeholders in your organization to see security-related information that is most important to them. For example, a chief security officer may only want to see critical vulnerabilities when assessing risk. Or you may want to filter out potential vulnerabilities from a CSV export report that you deliver to your remediation team.

You can also filter vulnerabilities based on category to improve your organization’s remediation process. For example, a security administrator can filter vulnerabilities to make a report specific to a team or to a risk that requires attention. The security administrator can create reports that contain information about a specific type of vulnerability or vulnerabilities in a specific list of categories.

Reports can also be created to exclude a type of vulnerability or a list of categories. For example, if there is an Adobe Acrobat vulnerability in your environment that is addressed with a scheduled patching process, you can run a report that contains all vulnerabilities except those Adobe Acrobat vulnerabilities. This provides a report that is easier to read as unnecessary information has been filtered out.
[block:callout]
{
  "type": "info",
  "body": "You can manage vulnerability filters through the API. See the API guide for more information."
}
[/block]
Organizations that have distributed IT departments may need to disseminate vulnerability reports to multiple teams or departments. For the information in those reports to be the most effective, the information should be specific for the team receiving it. For example, a security administrator can produce remediation reports for the Oracle database team that only include vulnerabilities that affect the Oracle database. These streamlined reports will enable the team to more effectively prioritize their remediation efforts.

A security administrator can filter by vulnerability category to create reports that indicate how widespread a vulnerability is in an environment, or which assets have vulnerabilities that are not being addressed during patching. The security administrator can also include a list of historical vulnerabilities on an asset after a scan template has been edited. These reports can be used to monitor compliance status and to ensure that remediation efforts are effective.

The following document report template sections can include filtered vulnerability information:

* Discovered Vulnerabilities
* Discovered Services
* Index of Vulnerabilities
* Remediation Plan
* Vulnerability Exceptions
* Vulnerability Report Card Across Network
* Vulnerability Report Card by Node
* Vulnerability Test Errors

Therefore, report templates that contain these sections can include filtered vulnerability information. See [Fine-tuning information with custom report templates](doc:configuring-custom-report-templates#section-fine-tuning-information-with-custom-report-templates).

The following export templates can include filtered vulnerability information:

* Basic Vulnerability Check Results (CSV)
* Nexpose™ Simple XML Export
* QualysGuard™ Compatible XML Export
* SCAP Compatible XML Export
* XML Export
* XML Export 2.0

Vulnerability filtering is not supported in the following report templates:

* Cyberscope XML Export
* XCCDF XML
* XCCDF CSV
* Database Export

To filter vulnerability information, take the following steps:

1. Click **Filter report scope based on vulnerabilities** on the _Scope_ section of the _Create a report_ panel.
Options appear for vulnerability filters.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/5a85b56-s_select_vuln_filters.jpg",
        "s_select_vuln_filters.jpg",
        684,
        277,
        "#273245"
      ],
      "caption": "Select Vulnerability Filters section"
    }
  ]
}
[/block]
Certain templates allow you to include only validated vulnerabilities in reports: Basic Vulnerability Check Results (CSV), XML Export, XML Export 2.0, Top 10 Assets by Vulnerabilities, Top 10 Assets by Vulnerability Risk, Top Remediations, Top Remediations with Details, and Vulnerability Trends. Learn more about [Working with validated vulnerabilities](doc:working-with-vulnerabilities#section-working-with-validated-vulnerabilities).
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/b999eb2-s_select_vuln_filters_validated.jpg",
        "s_select_vuln_filters_validated.jpg",
        765,
        419,
        "#e8eeed"
      ],
      "caption": "Select Vulnerability Filters section with option to include only validated vulnerabilities"
    }
  ]
}
[/block]
2. To filter vulnerabilities by severity level, select the **Critical vulnerabilities** or **Critical and severe vulnerabilities** option. Otherwise, select **All severities**.
These are not PCI severity levels or CVSS scores. They map to numeric severity rankings that are assigned by the application and displayed in the _Vulnerability Listing_ table of the _Vulnerabilities_ page. Scores range from 1 to 10: 
1-3=_Moderate_; 4-7=_Severe_; and 8-10=_Critical_.
3. If you selected a CSV report template, you have the option to filter vulnerability result types. To include all vulnerability check results (positive and negative), select the **Vulnerable and non-vulnerable** option next to _Results_.
If you want to include only positive check results, select the **Vulnerable** option.

You can filter positive results based on how they were determined by selecting any of the check boxes for result types:

* **Vulnerabilities found:** Vulnerabilities were flagged because asset-specific vulnerability tests produced positive results. Vulnerabilities with this result type appear with the ve (vulnerable exploited) result code in CSV reports.
* **Vulnerabilities found:** Vulnerabilities were flagged because asset-specific vulnerability tests produced positive results. Vulnerabilities with this result type appear with the ve (vulnerable exploited) result code in CSV reports.
* **Vulnerabilities found:** Vulnerabilities were flagged because asset-specific vulnerability tests produced positive results. Vulnerabilities with this result type appear with the ve (vulnerable exploited) result code in CSV reports.


4. If you want to include or exclude specific vulnerability categories, select the appropriate option button in the _Categories_ section.
If you choose to include all categories, skip the following step.

**Tip:** Categories that are named for manufacturers, such as Microsoft, can serve as supersets of categories that are named for their products. For example, if you filter by the Microsoft category, you inherently include all Microsoft product categories, such as Microsoft Path and Microsoft Windows. This applies to other "company" categories, such as Adobe, Apple, and Mozilla.To view the vulnerabilities in a category see [Configuration steps for vulnerability check settings](doc:selecting-vulnerability-checks#section-configuration-steps-for-vulnerability-check-settings).

5. If you choose to include or exclude specific categories, the Security Console displays a text box containing the words _Select categories_. You can select categories with two different methods:
   * Click the text box to display a window that lists all available categories. Scroll down the list and select the check box for each desired category. Each selection appears in a text field at the bottom of the window.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/7e8bc19-s_vuln_cat_filters_check.jpg",
        "s_vuln_cat_filters_check.jpg",
        607,
        382,
        "#e6e7e7"
      ],
      "caption": "Selecting vulnerability categories by clicking check boxes"
    }
  ]
}
[/block]
* Click the text box to display a window that lists all available categories. Enter part or all a category name in the **Filter:** text box, and select the categories from the list that appears. If you enter a name that applies to multiple categories, all those categories appear. For example, you type _Adobe_ or _ado_, several Adobe categories appear. As you select categories, they appear in the text field at the bottom of the window.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/d34226e-s_vuln_cat_filters_textbox.jpg",
        "s_vuln_cat_filters_textbox.jpg",
        614,
        383,
        "#e7e8e8"
      ],
      "caption": "Filter by category list"
    }
  ]
}
[/block]
If you use either or both methods, all your selections appear in a field at the bottom of the selection window. When the list includes all desired categories, click outside of the window to return to the _Scope_ page. The selected categories appear in the text box.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/83ed8e8-s_select_vuln_filters_categories_selected.jpg",
        "s_select_vuln_filters_categories_selected.jpg",
        760,
        458,
        "#293549"
      ],
      "caption": "Selected vulnerability categories appear in the Scope section"
    }
  ]
}
[/block]

[block:callout]
{
  "type": "info",
  "body": "Existing reports will include all vulnerabilities unless you edit them to filter by vulnerability category."
}
[/block]
6. Click the **OK** button to save scope selections.

##Configuring report frequency

You can run the completed report immediately on a one-time basis, configure it to run after every scan, or schedule it to run on a repeating basis. The third option is useful if you have an asset group containing assets that are assigned to many different sites, each with a different scan template. Since these assets will be scanned frequently, it makes sense to run recurring reports automatically.

To configure report frequency, take the following steps:

1. Go to the _Create a report_ panel. 
2. Click **Configure advanced settings...**
3. Click **Frequency**.
4. Select a frequency option from the drop-down list:
 * Select **Do not run a recurring report** to generate a report immediately, on a one-time basis.
 * Select **Run a recurring report after each scan** to generate a report every time a scan is completed on the assets defined in the report scope.
 * Select **Run a recurring report on a repeated schedule** if you wish to schedule reports for regular time intervals.
If you selected either of the first two options, ignore the following steps.
If you selected the scheduling option, the Security Console displays controls for configuring a schedule.
5. Enter a start date using the mm/dd/yyyy format.
OR
Select the date from the calendar widget.
6. Enter an hour and minute for the start time, and click the **Up** or **Down** arrow to select _AM_ or _PM_.
7. Enter a value in the field labeled **Repeat every** and select a time unit from the drop-down list to set a time interval for repeating the report.
If you select _months on the specified date_, the report will run every month on the selected calendar date. For example, if you schedule a report to run on October 15, the report will run on October 15 every month.
If you select _months on the specified day of the month_, the report will run every month on the same ordinal weekday. For example, if you schedule the first report to run on October 15, which is the third Monday of the month, the report will run every third Monday of the month.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/076549b-s_schedule_reports.jpg",
        "s_schedule_reports.jpg",
        786,
        159,
        "#dcdbda"
      ],
      "caption": "Creating a report schedule"
    }
  ]
}
[/block]
##Best practices for scheduling reports

The frequency with which you schedule and distribute reports depends your business needs and security policies. You may want to run quarterly executive reports. You may want to run monthly vulnerability reports to anticipate the release of Microsoft hotfix patches. Compliance programs, such as PCI, impose their own schedules.

The amount of time required to generate a report depends on the number of included live IP addresses the number of included vulnerabilities—if vulnerabilities are being included—and the level of details in the report template. Generating a PDF report for 100-plus hosts with 2500-plus vulnerabilities takes fewer than 10 seconds.

The application can generate reports simultaneously, with each report request spawning a new thread. Technically, there is no limit on the number supported concurrent reports. This means that you can schedule reports to run simultaneously as needed. Note that generating a large number of concurrent reports—20 or more—can take significantly more time than usual.

##Best practices for using remediation plan templates

The remediation plan templates provide information for assessing the highest impact remediation solutions. You can use the Remediation Display settings to specify the number of solutions you want to see in a report. The default is 25 solutions, but you can set the number from 1 to 1000 as you require. Keep in mind that if the number is too high you may have a report with an unwieldy level of data and too low you may miss some important solutions for your assets.

You can also specify the criteria for sorting data in your report. Solutions can be sorted by _Affected asset_, _Risk score_, _Remediated vulnerabilities_, _Remediated vulnerabilities with known exploits_, and _Remediated vulnerabilities with malware kits_.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/166c568-s_remediation_display_settings.jpg",
        "s_remediation_display_settings.jpg",
        577,
        280,
        "#0e8dcb"
      ],
      "caption": "Remediation display settings"
    }
  ]
}
[/block]
##Best practices for using the Vulnerability Trends report template

The Vulnerability Trends template provides information about how vulnerabilities in your environment have changed have changed over time. You can configure the time range for the report to see if you are improving your security posture and where you can make improvements. To ensure readability of the report and clarity of the charts there is a limit of 15 data points that can be included in the report. The time range you set controls the number of data points that appear in the report. For example, you can set your date range for a weekly interval for a two-month period, and you will have eight data points in your report.
[block:callout]
{
  "type": "warning",
  "body": "Ensure you schedule adequate time to run this report template because of the large amount of data that it aggregates. Each data point is the equivalent of a complete report. It may take a long time to complete."
}
[/block]
To configure the time range of the report, use the following procedure:

1. Click **Configure advanced settings...**
2. Select **Vulnerability Trend Date Range**.
3. Select from pre-set ranges of **Past 1 year**, **Past 6 months**, **Past 3 months**, **Past 1 month**, or **Custom range**.
To set a custom range, enter a start date, end date, and specify the interval, either days, months, or years.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/9e95871-s_vulnerability_trend_timeperiod.jpg",
        "s_vulnerability_trend_timeperiod.jpg",
        523,
        84,
        "#e8eae6"
      ],
      "caption": "Vulnerability trend date range"
    }
  ]
}
[/block]
4. Configure other settings that you require for the report.
5. Click **Save & run the report** or **Save the report**, depending on what you want to do.

##Saving or running the newly configured report

After you complete a basic report configuration, you will have the option to configure additional properties, such as those for distributing the report. You can access those properties by clicking **Configure advanced settings...**

If you have configured the report to run in the future, either by selecting **Run a recurring report after every scan** or **Run a recurring report in a schedule** in the _Frequency_ section (see [Configuring report frequency](doc:creating-a-basic-report#section-configuring-report-frequency), you can save the report configuration by clicking Save the report or run it once immediately by clicking Save & run the report. Even if you configure the report to run automatically with one of the frequency settings, you can run the report manually any time you want if the need arises. See [Viewing, editing, and running reports](doc:viewing-editing-and-running-reports).

If you configured the report to run immediately on a one-time basis, you will also see buttons allowing you to either save and run the report, or just to save it. See [Viewing, editing, and running reports](doc:viewing-editing-and-running-reports) .
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/6612d5f-s_nx_report_save_run.jpg",
        "s_nx_report_save_run.jpg",
        683,
        163,
        "#0c92d0"
      ],
      "caption": "Saving or saving and running a one-time report"
    }
  ]
}
[/block]
##Selecting a scan as a baseline

Designating an earlier scan as a baseline for comparison against future scans allows you to track changes in your network. Possible changes between scans include newly discovered assets, services and vulnerabilities; assets and services that are no longer available; and vulnerabilities that were mitigated or remediated.

You must select the _Baseline Comparison_ report template in order to be able to define a baseline. See [Starting a new report configuration](doc:creating-a-basic-report#section-starting-a-new-report-configuration).

1. Go to the _Create a report_ panel. 
2. Click **Configure advanced settings...**
3. Click **Baseline Scan selection**.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/545141e-s_report_baseline_scan.jpg",
        "s_report_baseline_scan.jpg",
        587,
        88,
        "#e4e6e2"
      ],
      "caption": "Baseline scan selection"
    }
  ]
}
[/block]
4. Click **Use first scan**, **Use previous scan**, or **Use scan from a specific date** to specify which scan to use as the baseline scan.
5. Click the calendar icon to select a date if you chose **Use scan from a specific date**.
6. Click **Save & run the report** or **Save the report**, depending on what you want to do.