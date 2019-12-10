---
title: "Working with report formats"
excerpt: ""
---
The choice of a format is important in report creation. Formats not only affect how reports appear and are consumed, but they also can have some influence on what information appears in reports.

##Working with human-readable formats

Several formats make report data easy to distribute, open, and read immediately:

* _PDF_ can be opened and viewed in Adobe Reader.
* _HTML_ can be opened and viewed in a Web browser.
* _RTF_ can be opened, viewed, and edited in Microsoft Word. This format is preferable if you need to edit or annotate the report.
* _Text_ can be opened, viewed, and edited in any text editing program.
[block:callout]
{
  "type": "info",
  "body": "If you wish to generate PDF reports with Asian-language characters, make sure that UTF-8 fonts are properly installed on your host computer. PDF reports with UTF-8 fonts tend to be slightly larger in file size."
}
[/block]
If you are using one of the three report templates mandated for PCI scans as of September 1, 2010 (_Attestation of Compliance_, _PCI Executive Summary_, or _Vulnerability Details_), or a custom template made with sections from these templates, you can only use the RTF format. These three templates require ASVs to fill in certain sections manually.

##Working with XML formats
[block:callout]
{
  "type": "info",
  "body": "For information about XML export attributes, see [Export template attributes](doc:report-templates-and-sections#section-export-template-attributes). That section describes similar attributes in the CSV export template, some of which have slightly different names."
}
[/block]
Various XML formats make it possible to integrate reports with third-party systems.

* _Asset Report Format (ARF)_ provides asset information based on connection type, host name, and IP address. This template is required for submitting reports of policy scan results to the U.S. government for SCAP certification.
* _XML Export_, also known as “raw XML,” contains a comprehensive set of scan data with minimal structure. Its contents must be parsed so that other systems can use its information.
* _XML Export 2.0_ is similar to _XML Export_, but contains additional attributes:
   * Asset Risk	
   * Exploit Title	
   * Site Name
   * Exploit IDs	
   * Malware Kit Name(s)	
   * Site Importance
   * Exploit Skill Needed	
   * PCI Compliance Status	
   * Vulnerability Risk
   * Exploit Source Link	
   * Scan ID	
   * Vulnerability Since
   * Exploit Type	
   * Scan Template	 
* _InsightVM TM  Simple XML is also a “raw XML” format. It is ideal for integration of scan data with the Metasploit vulnerability exploit framework. It contains a subset of the data available in the XML Export format:_
   * hosts scanned
   * vulnerabilities found on those hosts
   * services scanned
   * vulnerabilities found in those services
* _SCAP Compatible XML_ is also a “raw XML” format that includes Common Platform Enumeration (CPE) names for fingerprinted platforms. This format supports compliance with Security Content Automation Protocol (SCAP) criteria for an Unauthenticated Scanner product.
* _XML_ arranges data in clearly organized, human-readable XML and is ideal for exporting to other document formats.
* _XCCDF Results XML Report_ provides information about compliance tests for individual USGCB or FDCC configuration policy rules. Each report is dedicated to one rule. The XML output includes details about the rule itself followed by data about the scan results. If any results were overridden, the output identifies the most recent override as of the time the report was run. See [Policy rule overrides](doc:policy-rule-overrides).
* _CyberScope XML Export_ organizes scan data for submission to the CyberScope application. Certain entities are required by the U.S. Office of Management and Budget to submit CyberScope-formatted data as part of a monthly program of reporting threats.
* _Qualys* XML Export_ is intended for integration with the Qualys reporting framework.
_*Qualys is a trademark of Qualys, Inc._

XML Export 2.0 contains the most information. In fact, it contains all the information captured during a scan. Its schema can be downloaded from the Support page in Help. Use it to help you understand how the data is organized and how you can customize it for your own needs.

##Working with CSV export

You can open a _CSV_ (comma separated value) report in Microsoft Excel. It is a powerful and versatile format. Not only does it contain a significantly greater amount of scan information than is available in report templates, but you can easily use macros and other Excel tools to manipulate this data and provide multiple views of it. Two CSV formats are available:

* _CSV Export_ includes comprehensive scan data
* _XCCDF Human Readable CSV Report_ provides test results on individual assets for compliance with individual USGCB or FDCC configuration policy rules. If any results were overridden, the output lists results based on the most recent overrides as of the time the output was generated. However, the output does not identify overrides as such or include the override history. See [Policy rule overrides](doc:policy-rule-overrides). 

The CSV Export format works only with the Basic Vulnerability Check Results template and any *Data*-type custom templates. See [Fine-tuning information with custom report templates](doc:configuring-custom-report-templates#section-fine-tuning-information-with-custom-report-templates).

##Using Excel pivot tables to create custom reports from a CSV file

The pivot table feature in Microsoft Excel allows you to process report data in many different ways, essentially creating multiple reports one exported CSV file. Following are instructions for using pivot tables. These instructions reflect Excel 2007. Other versions of Excel provide similar workflows.

If you have Microsoft Excel installed on the computer with which you are connecting to the Security Console, click the link for the CSV file on the _Reports_ page. This will start Microsoft Excel and open the file. If you do not have Excel installed on the computer with which you are connecting to the console, download the CSV file from the _Reports_ page, and transfer it to a computer that has Excel installed. Then, use the following procedure.

To create a custom report from a CSV file:

1. Start the process for creating a pivot table.
2. Select all the data.
3. Click the **Insert** tab, and then select the **PivotTable** icon.
The _Create Pivot Table_ dialog box, appears.
4. Click **OK** to accept the default settings.
Excel opens a new, blank sheet. To the right of this sheet is a bar with the title _PivotTable Field List_, which you will use to create reports. In the top pane of this bar is a list of fields that you can add to a report. Most of these fields re self-explanatory.

The **result-code** field provides the results of vulnerability checks. See [How vulnerability exceptions appear in XML and CSV formats](doc:working-with-report-formats#section-how-vulnerability-exceptions-appear-in-xml-and-csv-formats) for a list of result codes and their descriptions.

The **severity** field provides numeric severity ratings. The application assigns each vulnerability a severity level, which is listed in the Severity column. The three severity levels—Critical, Severe, and Moderate—reflect how much risk a given vulnerability poses to your network security. The application uses various factors to rate severity, including CVSS scores, vulnerability age and prevalence, and whether exploits are available.
[block:callout]
{
  "type": "info",
  "body": "The severity field is not related to the severity score in PCI reports.\n* 8 to 10 = Critical\n* 4 to 7 = Severe\n* 1 to 3 = Moderate"
}
[/block]
The next steps involve choosing fields for the type of report that you want to create, as in the three following examples.

**Example 1:** Creating a report that lists the five most numerous exploited vulnerabilities

1. Drag **result-code** to the _Report Filter_ pane.
2. Click drop-down arrow in column B to display result codes that you can include in the report.
3. Select the option for multiple items.
4. Select _ve_ for exploited vulnerabilities.
5. Click **OK**.
6. Drag **vuln-id** to the _Row Labels_ pane.
Row labels appear in column A.
7. Drag **vuln-id** to the _Values_ pane.
A count of vulnerability IDs appears in column B.
8. Click the drop-down arrow in column A to change the number of listed vulnerabilities to five.
9. Select Value Filters, and then Top 10...
10. Enter 5 in the Top 10 Filter dialog box and click **OK**.

The resulting report lists the five most numerous exploited vulnerabilities.

**Example 2:** Creating a report that lists required Microsoft hot-fixes for each asset

1. Drag result-code to the _Report Filter_ pane.
2. Click the drop-down arrow in column B of the sheet it to display result codes that you can include in the report.
3. Select the option for multiple items.
4. Select _ve_ for exploited vulnerabilities and _vv_ for vulnerable versions.
5. Click **OK**.
6. Drag **host** to the _Row Labels_ pane.
7. Drag **vuln-id** to the _Row Labels_ pane.
8. Click **vuln-id** once in the pane for choosing fields in the _PivotTable Field List_ bar.
9. Click the drop-down arrow that appears next to it and select **Label Filters**.
10. Select **Contains...** in the _Label Filter_ dialog box.
11. Enter the value windows-hotfix.
12. Click **OK**.

The resulting report lists required Microsoft hot-fixes for each asset.

**Example 3:** Creating a report that lists the most critical vulnerabilities and the systems that are at risk

1. Drag **result-code** to the _Report Filter_ pane.
2. Click the drop-down arrow that appears in column B to display result codes that you can include in the report.
3. Select the option for multiple items.
4. Select _ve_ for exploited vulnerabilities.
5. Click **OK**.
6. Drag **severity** to the _Report Filter_ pane.
Another of the sheet.
7. Click the drop-down arrow appears that column B to display ratings that you can include in the report.
8. Select the option for multiple items.
9. Select **8**, **9**, and **10**, for critical vulnerabilities.
10. Click **OK**.
11. Drag **vuln-titles** to the _Row Labels_ pane.
12. Drag **vuln-titles** to the _Values_ pane.
13. Click the drop-down arrow that appears in column A and select **Value Filters**.
14. Select **Top 10...** in the _Top 10 Filter_ dialog box, confirm that the value is 10.
15. Click **OK**.
16. Drag **host** to the _Column Labels_ pane.
17. Another of the sheet.
18. Click the drop-down arrow appears in column B and select **Label Filters**.
19. Select **Greater Than...** in the Label Filter dialog box, enter a value of 1.
20. Click **OK**.

The resulting report lists the most critical vulnerabilities and the assets that are at risk.

##How vulnerability exceptions appear in XML and CSV formats

Vulnerability exceptions can be important for the prioritization of remediation projects and for compliance audits. Report templates include a section dedicated to exceptions. See [Vulnerability Exceptions](doc:report-templates-and-sections#section-vulnerability-exceptions). In XML and CSV reports, exception information is also available.

_XML_: The vulnerability test status attribute will be set to one of the following values for vulnerabilities suppressed due to an exception:
```
exception-vulnerable-exploited - Exception suppressed exploited vulnerability
exception-vulnerable-version - Exception suppressed version-checked vulnerability
exception-vulnerable-potential - Exception suppressed potential vulnerability
```

_CSV_: The vulnerability result-code column will be set to one of the following values for vulnerabilities suppressed due to an exception.

##Vulnerability result codes

Each code corresponds to results of a vulnerability check:

* _ds_ (skipped, disabled): A check was not performed because it was disabled in the scan template.
* _ee_ (excluded, exploited): A check for an exploitable vulnerability was excluded.
* _ep_ (excluded, potential): A check for a potential vulnerability was excluded.
* -er_ (error during check): An error occurred during the vulnerability check.
* _ev_ (excluded, version check): A check was excluded. It is for a vulnerability that can be identified because the version of the scanned service or application is associated with known vulnerabilities.
* _nt_ (no tests): There were no checks to perform.
* _nv_ (not vulnerable): The check was negative.
* _ov_ (overridden, version check): A check for a vulnerability that would ordinarily be positive because the version of the target service or application is associated with known vulnerabilities was negative due to information from other checks.
* _sd_ (skipped because of DoS settings): sd (skipped because of DOS settings)—If unsafe checks were not enabled in the scan template, the application skipped the check because of the risk of causing denial of service (DOS). See [Configuration steps for vulnerability check settings](doc:selecting-vulnerability-checks#section-configuration-steps-for-vulnerability-check-settings).
* _sv_ (skipped because of inapplicable version): the application did not perform a check because the version of the scanned item is not included in the list of checks.
* _uk_ (unknown): An internal issue prevented the application from reporting a scan result.
* _ve_ (vulnerable, exploited): The check was positive as indicated by asset-specific vulnerability tests. Vulnerabilities with this result appear in the CSV report if the Vulnerabilities found result type was selected in the report configuration. See [Filtering report scope with vulnerabilities](doc:creating-a-basic-report#section-filtering-report-scope-with-vulnerabilities).
* _vp_ (vulnerable, potential): The check for a potential vulnerability was positive.
* -vv_ (vulnerable, version check): The check was positive. The version of the scanned service or software is associated with known vulnerabilities.

##Working with the database export format

You can output the _Database Export_ report format to Oracle, MySQL, and Microsoft SQL Server.

Like CSV and the XML formats, the Database Export format is fairly comprehensive in terms of the data it contains. It is not possible to configure what information is included in, or excluded from, the database export. Consider CSV or one of the XML formats as alternatives.

InsightVM provides a schema to help you understand what data is included in the report and how the data is arranged, which is helpful in helping you understand how to you can work with the data. You can request the database export schema from Technical Support.