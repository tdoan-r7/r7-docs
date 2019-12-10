---
title: "Report templates and sections"
excerpt: ""
---
Use this appendix to help you select the right built-in report template for your needs. You can also learn about the individual sections or data fields that make up report templates, which is helpful for creating custom templates.

##Built-in report templates and included sections

Creating custom document templates enables you to include as much, or as little, information in your reports as your needs dictate. For example, if you want a report that only lists all assets organized by risk level, a custom report might be the best solution. This template would include only the section. Or, if you want a report that only lists vulnerabilities, create a template with the section.

Configuring a document report template involves selecting the sections to be included in the template. Each report template in the following section lists all sections available for each of the document report templates, including those that appear in built-in report templates and those that you can include in a customized template. You may find that a given built-in template contains all the sections that you require in a particular report, making it unnecessary to create a custom template. 

###Asset Report Format (ARF)

The Asset Report Format (ARF) XML template organizes data for submission of policy and benchmark scan results to the U.S. Government for SCAP 1.2 compliance.

###Audit Report

Of all the built-in templates, the Audit is the most comprehensive in scope. You can use it to provide a detailed look at the state of security in your environment.
* The Audit Report template provides a great deal of granular information about discovered assets:
* host names and IP addresses
* discovered services, including ports, protocols, and general security issues
* risk scores, depending on the scoring algorithm selected by the administrator
* users and asset groups associated with the assets
* discovered databases*
* discovered files and directories*
* results of policy evaluations performed*
* spidered Web sites*

It also provides a great deal of vulnerability information:
* affected assets
* vulnerability descriptions
* severity levels
* references and links to important information sources, such as security advisories
* general solution information

Additionally, the Audit Report template includes charts with general statistics on discovered vulnerabilities and severity levels.

>To gather this “deep” information the application must have logon credentials for the target assets. An Audit Report based on a non-credentialed scan will not include this information. Also, it must have policy testing enabled in the scan template configuration.

Note that the Audit Report template is different from the PCI Audit template. See [PCI Audit (legacy)](doc:report-templates-and-sections#section-pci-audit-legacy-).

The Audit report template includes the following sections:
* Cover Page
* Discovered Databases
* Discovered Files and Directories
* Discovered Services
* Discovered System Information
* Discovered Users and Groups
* Discovered Vulnerabilities
* Executive Summary
* Policy Evaluation
* Spidered Web Site Structure
* Vulnerability Report Card by Node

###Baseline Comparison

You can use the Baseline Comparison to observe security-related trends or to assess the results of a scan as compared with the results of a previous scan that you are using as a baseline, as in the following examples.
* You may use the first scan that you performed on a site as a baseline. Being the first scan, it may have revealed a high number of vulnerabilities that you subsequently remediated. Comparing current scan results to those of the first scan will help you determine how effective your remediation work has been.
* You may use a scan that revealed an especially low number of vulnerabilities as a benchmark of good security “health”.
* You may use the last scan preceding the current one to verify whether a certain patch removed a vulnerability in that scan.

Trending information indicates changes discovered during the scan, such as the following:
* new assets and services
* assets or services that are no longer running since the last scan
* new vulnerabilities
* previously discovered vulnerabilities did not appear in the most current scan

Trending information is useful in gauging the progress of remediation efforts or observing environmental changes over time. For trending to be accurate and meaningful, make sure that the compared scans occurred under identical conditions:
* the same site was scanned
* the same scan template was used
* if the baseline scan was performed with credentials, the recent scan was performed with the same credentials.

The Baseline Comparison report template includes the following sections:
* Cover Page
* Executive Summary

###Executive Overview

You can use the Executive Overview template to provide a high-level snapshot of security data. It includes general summaries and charts of statistical data related to discovered vulnerabilities and assets.

Note that the Executive Overview template is different from the _PCI Executive Overview_. See [PCI Executive Overview (legacy)](doc:report-templates-and-sections#section-pci-executive-overview-legacy-).

The Executive Overview template includes the following sections:
* Baseline Comparison
* Cover Page
* Executive Summary
* Risk Trends

###Highest Risk Vulnerabilities

The Highest Risk Vulnerabilities template lists the top 10 discovered vulnerabilities according to risk level. This template is useful for targeting the biggest threats to security as priorities for remediation.

Each vulnerability is listed with risk and CVSS scores, as well references and links to important information sources.

The Highest Risk Vulnerabilities report template includes the following sections:
* Cover Page
* Highest Risk Vulnerability Details
* Table of Contents

###Newly Discovered Assets

With this template you can view assets that were discovered in scans within a specified time period. It is useful for tracking changes to your asset inventory. In addition to general information about each asset, the report lists risk scores and indicates whether assets have vulnerabilities with associated exploits or malware kits.

###PCI Attestation of Compliance

This is one of three PCI-mandated report templates to be used by ASVs for PCI scans as of September 1, 2010.

The PCI Attestation of Compliance is a single page that serves as a cover sheet for the completed PCI report set.

In the top left area of the page is a form for entering the customer’s contact information. If the ASV added scan customer organization information in the site configuration on which the scan data is based, the form will be auto-populated with that information. See _Including organization information in a site in the user's guide or Help_. In the top right area is a form with auto-populated fields for the ASV’s information.

The Scan Status section lists a high-level summary of the scan, including whether the overall result is a Pass or Fail, some statistics about what the scan found, the date the scan was completed, and scan expiration date, which is the date after which the results are no longer valid.

In this section, the ASV must note the number of components left out of the scope of the scan.

Two separate statements appear at the bottom. The first is for the customer to attest that the scan was properly scoped and that the scan result only applies to external vulnerability scan requirement of PCI Data Security Standard (DSS). It includes the attestation date, and an indicated area to fill in the customer’s name.

The second statement is for the ASV to attest that the scan was properly conducted, QA-tested, and reviewed. It includes the following auto-populated information:
* attestation date for scan customer
* ASV name*
* certificate number*
* ASV reviewer name* (the individual who conducted the scan and review process)
To support auto-population of these fields*, you must enter create appropriate settings in the oem.xml configuration file. See The _ASV guide_, which you can request from Technical Support.

The PCI Attestation report template includes the following section:
* Asset and Vulnerabilities Compliance Overview

###PCI Audit (legacy)

This is one of two reports no longer used by ASVs in PCI scans as of September 1, 2010. It provides detailed scan results, ranking each discovered vulnerability according to its Common Vulnerability Scoring System (CVSS) ranking.

Note that the _PCI_ Audit template is different from the Audit Report template. See [Audit Report](doc:report-templates-and-sections#section-audit-report).

The PCI Audit (Legacy) report template includes the following sections:
* Cover Page
* Payment Card Industry (PCI) Scanned Hosts/Networks
* Payment Card Industry (PCI) Vulnerability Details
* Payment Card Industry (PCI) Vulnerability Synopsis
* Table of Contents
* Vulnerability Exceptions

###PCI Executive Overview (legacy)

This is one of two reports no longer used by ASVs in PCI scans as of September 1, 2010. It provides high-level scan information.

Note that the _PCI Executive Overview_ template is different from the template _PCI Executive Summary_. See [PCI Executive Summary](doc:report-templates-and-sections#section-pci-executive-summary).

The PCI Executive Overview (Legacy) report template includes the following sections:
* Cover Page
* Payment Card Industry (PCI) Executive Summary
* Table of Contents

###PCI Executive Summary

This is one of three PCI-mandated report templates to be used by ASVs for PCI scans as of September 1, 2010.

The PCI Executive Summary begins with a _Scan Information_ section, which lists the dates that the scan was completed and on which it expires. This section includes the auto-populated ASV name and an area to fill in the customer’s company name. If the ASV added scan customer organization information in the site configuration on which the scan data is based, the customer’s company name will be auto-populated. See [Getting started: Info & Security](doc:creating-and-editing-sites#section-getting-started-info-security).

The _Component Compliance Summary_ section lists each scanned IP address with a Pass or Fail result.

The _Asset and Vulnerabilities Compliance Overview_ section includes charts that provide compliance statistics at a glance.

The _Vulnerabilities Noted for each IP Address_ section includes a table listing each discovered vulnerability with a set of attributes including PCI severity, CVSS score, and whether the vulnerability passes or fails the scan. The assets are sorted by IP address. If the ASV marked a vulnerability for exception in the application, the exception is indicated here. The column labeled _Exceptions, False Positives, or Compensating Controls_ field in the PCI Executive Summary report is auto-populated with the user name of the individual who excluded a given vulnerability.

In the concluding section, _Special Notes_, ASVs must disclose the presence of any software that may pose a risk due to insecure implementation, rather than an exploitable vulnerability. The notes should include the following information:
* the IP address of the affected asset
* the note statement, written according to PCIco (see the PCI ASV Program Guide v1.2)
* information about the issue such as name or location of the affected software
* the customer’s declaration of secure implementation or description of action taken to either remove the software or secure it
Any instance of remote access software or directory browsing is automatically noted. ASVs must add any information pertaining to point-of-sale terminals and absence of synchronization between load balancers. ASVs must obtain and insert customer declarations or description of action taken for each special note before officially releasing the Attestation of Compliance.

The PCI Executive Overview report template includes the following sections:
* Payment Card Industry (PCI) Component Compliance Summary
* Payment Card Industry (PCI) Scan Information
* Payment Card Industry (PCI) Special Notes
* Payment Card Industry (PCI) Vulnerabilities Noted (sub-sectioned into High, Medium, and Small)

###PCI Host Details

This template provides detailed, sorted scan information about each asset, or host, covered in a PCI scan. This perspective allows a scanned merchant to consume, understand, and address all the PCI-related issues on an asset-by-asset basis. For example, it may be helpful to note that a non-PCI-compliant asset may have a number of vulnerabilities specifically related to its operating system or a particular network communication service running on it.

The PCI Host Details report template includes the following sections:
* Payment Card Industry (PCI) Host Details
* Table of Contents

###PCI Vulnerability Details

This is one of three PCI-mandated report templates to be used by ASVs for PCI scans as of September 1, 2010.

The PCI Vulnerability Details report begins with a _Scan Information_ section, which lists the dates that the scan was completed and on which it expires. This section includes the auto-populated ASV name and an area to fill in the customer's company name.
[block:callout]
{
  "type": "info",
  "body": "The PCI Vulnerability Details report takes into account approved vulnerability exceptions to determine compliance status for each vulnerability instance."
}
[/block]
The _Vulnerability Details_ section includes statistics and descriptions for each discovered vulnerability, including affected IP address, Common Vulnerability Enumeration (CVE) identifier, CVSS score, PCI severity, and whether the vulnerability passes or fails the scan. Vulnerabilities are grouped by severity level, and within grouping vulnerabilities are listed according to CVSS score.

The PCI Vulnerability Details report template includes the following sections:
* Payment Card Industry (PCI) Scan Information
* Payment Card Industry (PCI) Vulnerability Details
* Table of Contents

###Policy Evaluation

The Policy Evaluation displays the results of policy evaluations performed during scans.

The application must have proper logon credentials in the site configuration and policy testing enabled in the scan template configuration. See _Establishing scan credentials and Modifying and creating scan templates_ in the _administrator's guide_.

Note that this template provides a subset of the information in the Audit Report template.

The Policy Evaluation report template includes the following sections:

* Cover Page
* Policy Evaluation

###Remediation Plan

The Remediation Plan template provides detailed remediation instructions for each discovered vulnerability. Note that the report may provide solutions for a number of scenarios in addition to the one that specifically applies to the affected target asset.

The Remediation Plan report template includes the following sections:
* Cover Page
* Discovered System Information
* Remediation Plan
* Risk Assessment

###Report Card

The Report Card template is useful for finding out whether, and how, vulnerabilities have been verified. The template lists information about the test that InsightVM performed for each vulnerability on each asset. Possible test results include the following:
* not vulnerable
* not vulnerable version
* exploited

For any vulnerability that has been excluded from reports, the test result will be the reason for the exclusion, such as _acceptable risk_.

The template also includes detailed information about each vulnerability.

The Report Card report template includes the following sections:
* Cover Page
* Index of Vulnerabilities
* Vulnerability Report Card by Node

###Top 10 Assets by Vulnerability Risk
[block:callout]
{
  "type": "info",
  "body": "The Top 10 Assets by Vulnerability Risk and Top 10 Assets by Vulnerabilities report templates do not contain individual sections that can be applied to custom report templates."
}
[/block]
The Top 10 Assets by Vulnerability Risk lists the 10 assets with the highest risk scores. For more information about ranking, see [Viewing active vulnerabilities](doc:working-with-vulnerabilities#section-viewing-active-vulnerabilities).

This report is useful for prioritizing your remediation efforts by providing your remediation team with an overview of the assets in your environment that pose the greatest risk.

###Top 10 Assets by Vulnerabilities

The Top 10 Assets by Vulnerabilities report lists 10 the assets in your organization that have the most vulnerabilities. This report does not account for cumulative risk.

You can use this report to view the most vulnerable services to determine if services should be turned off to reduce risk. This report is also useful for prioritizing remediation efforts by listing the assets that have the most vulnerable services.

###Top Remediations

The Top Remediations template provides high-level information for assessing the highest impact remediation solutions. The template includes the percentage of total vulnerabilities resolved, the percentage of vulnerabilities with malware kits, the percentage of vulnerabilities with known exploits, and the number of assets affected when the top remediation solutions are applied.

This report presents the best solutions as determined by how recently they were released and how well they address the vulnerability on all the types of machines in your environment. To review all potential solutions for a given vulnerability, see the Remediations section on the details page for that vulnerability. To learn more, see [Working with vulnerabilities](doc:working-with-vulnerabilities).

The Top Remediations template includes information in the following areas:
* the number of vulnerabilities that will be remediated, including vulnerabilities with no exploits or malware that will be remediated
* vulnerabilities and total risk score associated with the solution
* the number of targeted vulnerabilities that have known exploits associated with them
* the number of targeted vulnerabilities with available malware kits
* the number of assets to be addressed by remediation
* the amount of risk that will be reduced by the remediations

###Top Remediations with Details

The Top Remediations with Details template provides expanded information for assessing remediation solutions and implementation steps. The template includes the percentage of total vulnerabilities resolved and the number of assets affected when remediation solutions are applied.

The Top Remediations with Details includes the information from the Top Rememdiations template with information in the following areas:
* remediation steps that need to be performed
* vulnerabilities and total risk score associated with the solution
* the assets that require the remediation steps

###Vulnerability Trends

The Vulnerability Trends template provides information about how vulnerabilities in your environment have changed, if your remediation efforts have succeeded, how assets have changed over time, how asset groups have been affected when compared to other asset groups, and how effective your asset scanning process is. To manage the readability and size of the report, when you configure the date range there is a limit of 15 data points that can be included on a chart. For example, you can set your date range for a weekly interval for a two-month period, and you will have eight data points in your report. You can configure the period of time for the report to see if you are improving your security posture and where you can make improvements.
[block:callout]
{
  "type": "warning",
  "body": "Ensure you schedule adequate time to run this report template because of the large amount of data that it aggregates. Each data point is the equivalent of a complete report. It may take a long time to complete."
}
[/block]
The Vulnerability Trends template provides charts and details in the following areas:

* assets scanned and vulnerabilities
* severity levels
* trend by vulnerability age
* vulnerabilities with malware or exploits

The Vulnerability Trends template helps you improve your remediation efforts by providing information about the number of assets included in a scan and if any have been excluded, if vulnerability exceptions have been applied or expired, and if there are new vulnerability definitions that have been added to the application. The Vulnerability Trends survey template differs from the vulnerability trend section in the Baseline report by providing information for more in-depth analysis regarding your security posture and remediation efforts provides.

##Document report sections

Some of the following documents report sections can have vulnerability filters applied to them. This means that specific vulnerabilities can be included or excluded in these sections based on the report Scope configuration. When the report is generated, sections with filtered vulnerabilities will be so identified. Document report templates that do not contain any of these sections do not contain filtered vulnerability data. The document report sections are listed in the sections below:

###Asset and Vulnerabilities Compliance Overview

This section includes charts that provide compliance statistics at a glance.

###Baseline Comparison

This section appears when you select the Baseline Report template. It provides a comparison of data between the most recent scan and the baseline, enumerating the following changes:
* discovered assets that did not appear in the baseline scan
* assets that were discovered in the baseline scan but not in the most recent scan
* discovered services that did not appear the baseline scan
* services that were discovered in the baseline scan but not in the most recent scan
* discovered vulnerabilities that did not appear in the baseline scan
* vulnerabilities that were discovered in the baseline scan but not in the most recent scan

Additionally, this section provides suggestions as to why changes in data may have occurred between the two scans. For example, newly discovered vulnerabilities may be attributable to the installation of vulnerable software that occurred after the baseline scan.

In generated reports, this section appears with the heading _Trend Analysis_.

###Cover Page

The _Cover Page_ includes the name of the site, the date of the scan, and the date that the report was generated. Other display options include a customized title and company logo.

###Discovered Databases

This section lists all databases discovered through a scan of database servers on the network.

For information to appear in this section, the scan on which the report is based must meet the following conditions:
* database server scanning must be enabled in the scan template
* the application must have correct database server logon credentials

###Discovered Files and Directories

This section lists files and directories discovered on scanned assets.

For information to appear in this section, the scan on which the report is based must meet the following conditions:
* file searching must be enabled in the scan template
* the application must have correct logon credentials

See [Configuring scan credentials](doc:configuring-scan-credentials) for information on configuring these settings.

###Discovered Services

This section lists all services running on the network, the IP addresses of the assets running each service, and the number of vulnerabilities discovered on each asset.

Vulnerability filters can be applied.

###Discovered System Information

This section lists the IP addresses, alias names, operating systems, and risk scores for scanned assets.

Discovered Users and Groups

This section provides information about all users and groups discovered on each node during the scan.
[block:callout]
{
  "type": "info",
  "body": "In generated reports, the Discovered Vulnerabilities section appears with the heading _Discovered and Potential Vulnerabilities_."
}
[/block]
###Discovered Vulnerabilities

This section lists all vulnerabilities discovered during the scan and identifies the affected assets and ports. It also lists the Common Vulnerabilities and Exposures (CVE) identifier for each vulnerability that has an available CVE identifier. Each vulnerability is classified by severity.

If you selected a _Medium_ technical detail level for your report template, the application provides a basic description of each vulnerability and a list of related reference documentation. If you selected a _High_ level of technical detail, it adds a narrative of how it found the vulnerability to the description, as well as remediation options. Use this section to help you understand and fix vulnerabilities.

This section does not distinguish between potential and confirmed vulnerabilities.

Vulnerability filters can be applied.

###Executive Summary

This section provides statistics and a high-level summation of the scan data, including numbers and types of network vulnerabilities.

###Highest Risk Vulnerability Details

This section lists highest risk vulnerabilities and includes their categories, risk scores, and their Common Vulnerability Scoring System (CVSS) Version 2 scores. The section also provides references for obtaining more information about each vulnerability.

###Index of Vulnerabilities

This section includes the following information about each discovered vulnerability:
* severity level
* Common Vulnerability Scoring System (CVSS) Version 2 rating
* category
* URLs for reference
* description
* solution steps

In generated reports, this section appears with the heading _Vulnerability Details_.

Vulnerability filters can be applied.

###Payment Card Industry (PCI) Component Compliance Summary

This section lists each scanned IP address with a Pass or Fail result.

###Payment Card Industry (PCI) Executive Summary

This section includes a statement as to whether a set of assets collectively passes or fails to comply with PCI security standards. It also lists each scanned asset and indicates whether that asset passes or fails to comply with the standards.

###Payment Card Industry (PCI) Host Details

This section lists information about each scanned asset, including its hosted operating system, names, PCI compliance status, and granular vulnerability information tailored for PCI scans.

###Payment Card Industry (PCI) Scan Information

This section includes name fields for the scan customer and approved scan vendor (ASV). The customer's name must be entered manually. If the ASV has configured the oem.xml file to auto-populate the name field, it will contain the ASV’s name. Otherwise, the ASV’s name must be entered manually as well. For more information, see the _ASV guide_, which you can request from Technical Support.

This section also includes the date the scan was completed and the scan expiration date, which is the last day that the scan results are valid from a PCI perspective.

###Payment Card Industry (PCI) Scanned Hosts/Networks

This section lists the range of scanned assets.
[block:callout]
{
  "type": "info",
  "body": "Any instance of remote access software or directory browsing is automatically noted."
}
[/block]
###Payment Card Industry (PCI) Special Notes

In this PCI report section, ASVs manually enter the notes about any scanned software that may pose a risk due to insecure implementation, rather than an exploitable vulnerability. The notes should include the following information:
* the IP address of the affected asset
* the note statement, written according to PCIco (see the _PCI ASV Program Guide v1.2_)
* the type of special note, which is one of four types specified by PCIco (see the _PCI ASV Program Guide v1.2_)
* the scan customer’s declaration of secure implementation or description of action taken to either remove the software or secure it

###Payment Card Industry (PCI) Vulnerabilities Noted for each IP Address

This section includes a table listing each discovered vulnerability with a set of attributes including PCI severity, CVSS score, and whether the vulnerability passes or fails the scan. The assets are sorted by IP address. If the ASV marked a vulnerability for exception, the exception is indicated here. The column labeled _Exceptions, False Positives, or Compensating Controls_ field in the PCI Executive Summary report is auto-populated with the user name of the individual who excluded a given vulnerability.
[block:callout]
{
  "type": "info",
  "body": "The PCI Vulnerability Details report takes into account approved vulnerability exceptions to determine compliance status for each vulnerability instance."
}
[/block]
###Payment Card Industry (PCI) Vulnerability Details

This section contains in-depth information about each vulnerability included in a PCI Audit report. It quantifies the vulnerability according to its severity level and its Common Vulnerability Scoring System (CVSS) Version 2 rating.

This latter number is used to determine whether the vulnerable assets in question comply with PCI security standards, according to the CVSS v2 metrics. Possible scores range from 1.0 to 10.0. A score of 4.0 or higher indicates failure to comply, with some exceptions. For more information about CVSS scoring or go to the FIRST Web site at [https://www.first.org/cvss/](https://www.first.org/cvss/).

###Payment Card Industry (PCI) Vulnerability Synopsis

This section lists vulnerabilities by categories, such as types of client applications and server-side software.

###Policy Evaluation

This sections lists the results of any policy evaluations, such as whether Microsoft security templates are in effect on scanned systems. Section contents include system settings, registry settings, registry ACLs, file ACLs, group membership, and account privileges.

###Remediation Plan

This section consolidates information about all vulnerabilities and provides a plan for remediation. The database of vulnerabilities feeds the _Remediation Plan_ section with information about patches and fixes, including Web links for downloading them. For each remediation, the database provides a time estimate. Use this section to research fixes, patches, work-arounds, and other remediation measures.

Vulnerability filters can be applied.

###Risk Assessment

This section ranks each node (asset) by its risk index score, which indicates the risk that asset poses to network security. An asset’s confirmed and unconfirmed vulnerabilities affect its risk score.

###Risk Trend

This section enables you to create graphs illustrating risk trends in reports in your Executive Summary. The reports can include your five highest risk sites, asset groups, assets, or you can select all assets in your report scope.

###Scanned Hosts and Networks

This section lists the assets that were scanned. If the IP addresses are consecutive, the console displays the list as a range.

###Table of Contents

This section lists the contents of the report.

###Trend Analysis

This section appears when you select the Baseline report template. It compares the vulnerabilities discovered in a scan against those discovered in a baseline scan. Use this section to gauge progress in reducing vulnerabilities improving network's security.

###Vulnerabilities by IP Address and PCI Severity Level

This section, which appears in PCI Audit reports, lists each vulnerability, indicating whether it has passed or failed in terms of meeting PCI compliance criteria. The section also includes remediation information.

###Vulnerability Details

The Vulnerability Details section includes statistics and descriptions for each discovered vulnerability, including affected IP address, Common Vulnerability Enumeration (CVE) identifier, CVSS score, PCI severity, and whether the vulnerability passes or fails the scan. Vulnerabilities are grouped by severity level, and within grouping vulnerabilities are listed according to CVSS score.

###Vulnerability Exception Activity

Use this template to view all vulnerability exceptions that were applied or requested within a specified time period. The report includes information about each exception or exception request, including the parties involved, statuses, and the reasons for the exceptions. This information is useful for examining your organization's vulnerability management practices.

###Vulnerability Exceptions

This section lists each vulnerability that has been excluded from report and the reason for each exclusion. You may not wish to see certain vulnerabilities listed with others, such as those to be targeted for remediation; but business policies may dictate that you list excluded vulnerabilities if only to indicate that they were excluded. A typical example is the PCI Audit report. Vulnerabilities of a certain severity level may result in an audit failure. They may be excluded for certain reasons, but the exclusions must be noted.

Do not confuse an excluded vulnerability with a disabled vulnerability check. An excluded vulnerability has been discovered by the application, which means the check was enabled.

Vulnerability filters can be applied.

###Vulnerability Report Card by Node

This section lists the results of vulnerability tests for each node (asset) in the network. Use this section to assess the vulnerability of each asset.

Vulnerability filters can be applied.

###Vulnerability Report Card Across Network

This section lists all tested vulnerabilities, and indicates how each node (asset) in the network responded when the application attempted to confirm a vulnerability on it. Use this section as an overview of the network's susceptibility to each vulnerability.

Vulnerability filters can be applied.

###Vulnerability Test Errors

This section displays vulnerabilities that were not confirmed due to unexpected failures. Use this section to anticipate or prevent system errors and to validate that scan parameters are set properly.

Vulnerability filters can be applied.

##Export template attributes

When creating a custom export template, you can select from a full set of vulnerability data attributes. The following table lists the name and description of each attribute that you can include.
[block:parameters]
{
  "data": {
    "h-0": "Attribute name",
    "h-1": "Description",
    "0-0": "Asset Alternate IPv4 Addresses",
    "0-1": "This is the set of alternate IPv4 addresses of the scanned asset.",
    "1-0": "Asset Alternate IPv6 Addresses",
    "1-1": "This is the set of alternate IPv6 addresses of the scanned asset.",
    "2-0": "Asset IP Address",
    "2-1": "This is the IP address of the scanned asset.",
    "3-0": "Asset MAC Addresses",
    "3-1": "These are the MAC addresses of the scanned asset. In the case of multi-homed assets, multiple MAC addresses are separated by commas. Example: 00:50:56:39:06:F5, 00:50:56:39:06:F6",
    "4-0": "Asset Names",
    "4-1": "These are the host names of the scanned asset. On the Assets page, asset names may be referred to as _aliases_.",
    "5-0": "Asset OS Family",
    "5-1": "This is the fingerprinted operating system family of the scanned asset. Only the family with the highest-certainty fingerprint is listed. Examples: Linux, Windows",
    "6-0": "Asset OS Name",
    "6-1": "This is the fingerprinted operating system of the scanned asset. Only the operating system with the highest-certainty fingerprint is listed.",
    "7-0": "Asset OS Version",
    "7-1": "This is the fingerprinted version number of the scanned asset’s operating system. Only the version with the highest-certainty fingerprint is listed.",
    "8-0": "Asset Risk Score",
    "8-1": "This is the overall risk score of the scanned asset when the vulnerability test was run. Note that this is different from the vulnerability risk score, which is the specific risk score associated with the vulnerability.",
    "9-0": "Exploit Count",
    "9-1": "This is the number of exploits associated with the vulnerability.",
    "10-0": "Exploit Minimum Skill",
    "10-1": "This is the minimum skill level required to exploit the vulnerability.",
    "11-0": "Exploit URLs",
    "11-1": "These are the URLs for all exploits as published by Metasploit or the Exploit Database.",
    "12-0": "Malware Kit Names",
    "12-1": "These are the malware kits associated with the vulnerability. Multiple kits are separated by commas.",
    "13-0": "Malware Kit Count",
    "13-1": "This is the number of malware kits associated with the vulnerability.",
    "14-0": "Scan ID",
    "14-1": "This is the ID for the scan during which the vulnerability test was performed as displayed in a site’s scan history. It is the last scan during which the asset was scanned. Different assets within the same site may point to different scan IDs as of individual asset scans (as opposed to site scans).",
    "15-0": "Scan Template",
    "15-1": "This is the name of the scan template currently applied to the scanned asset’s site. It may or may not be the template used for the scan during which the vulnerability was discovered, since a user could have changed the template since the scan was last run.",
    "16-0": "Service Name",
    "16-1": "This is the fingerprinted service type of the port on which the vulnerability was tested. \nExamples: HTTP, CIFS, SSHIn the case of operating system checks, the service name is listed as _System_.",
    "17-0": "Service Port",
    "17-1": "This is the port on which the vulnerability was found. For example, all HTTP-related vulnerabilities are mapped to the port on which the Web server was found.In the case of operating system checks, the port number is 0.",
    "18-0": "Service Product",
    "18-1": "This is the fingerprinted product that was running the scanned service on the port where the vulnerability was found.In the case of operating system checks, this column is blank.",
    "19-0": "Service Protocol",
    "19-1": "This is the network protocol of the scanned port. Examples: TCP, UDP",
    "20-0": "Site Importance",
    "20-1": "This is the site importance according to the current site configuration at the time of the CSV export. See [Creating and editing sites](doc:creating-and-editing-sites).",
    "21-0": "Site Name",
    "21-1": "This is the name of the site to which the scanned asset belongs.",
    "22-0": "Vulnerability Additional URLs",
    "22-1": "There are the URLs that provide information about the vulnerability in addition to those cited as Vulnerability Reference URLs. They appear in _References_ table of vulnerability details page, labeled as _URL_. Multiple URLs are separated by commas.",
    "23-0": "Vulnerability Age",
    "23-1": "This is the number of days since the vulnerability was first discovered on the scanned asset.",
    "24-0": "Vulnerability CVE IDs",
    "24-1": "These are the Common Vulnerabilities and Exposure (CVE) IDs associated with the vulnerability. If the vulnerability has multiple CVE IDs, the 10 most recent IDs are listed. For multiple values, each value is separated by a comma and space.",
    "25-0": "Vulnerability CVE URLs",
    "25-1": "This is the URL of the CVE’s entry in the National Institute of Standards and Technology (NIST) National Vulnerability Database (NVD). For multiple values, each value is separated by a comma and space.",
    "26-0": "Vulnerability CVSS Score",
    "26-1": "This is the vulnerability’s Common Vulnerability Scoring System (CVSS) score according to CVSS 2.0 specification.",
    "29-0": "Vulnerability CVSS Vector",
    "29-1": "This is the vulnerability’s Common Vulnerability Scoring System (CVSS) vector according to CVSS 2.0 specification.",
    "30-0": "Vulnerability Description",
    "30-1": "This is useful information about the vulnerability as displayed in the vulnerability details page. Descriptions can include a substantial amount of text. You may need to expand the column in the spreadsheet program for better reading. This value can include line breaks and appears in double quotation marks.",
    "31-0": "Vulnerability ID",
    "31-1": "This is the unique identifier for the vulnerability as assigned by InsightVM.",
    "32-0": "Vulnerability PCI Compliance Status",
    "32-1": "This is the PCI status if the asset is found to be vulnerable.If an asset is not found to be vulnerable, the PCI severity level is not calculated, and the value is Not Applicable.If an asset is found to be vulnerable, the PCI severity is calculated, and the value is either Pass or Fail.If the vulnerability instance on the asset is excluded, the value is Pass.",
    "33-0": "Vulnerability Proof",
    "33-1": "This is the method used to prove that the vulnerability exists or doesn’t exist as reported by Scan Engine. Proofs can include a substantial amount of text. You may need to expand the column in the spreadsheet program for better reading. This value can include line breaks and appears in double quotation marks.",
    "34-0": "Vulnerability Published Date",
    "34-1": "This is the date when information about the vulnerability was first released.",
    "35-0": "Vulnerability Reference IDs",
    "35-1": "These are reference identifiers of the vulnerability, typically assigned by vendors such as Microsoft, Apple, and Redhat or security groups such as Secunia; SysAdmin, Audit, Network, Security (SANS) Institute; Computer Emergency Readiness Team (CERT); and SecurityFocus.\nThese appear in the _References_ table of the vulnerability details page.\nThe format of this attribute is Source:Identifier. Multiple values are separated by commas and spaces.Example: BID:4241, CALDERA:CSSA-2002-012.0, CONECTIVA:CLA-2002:467, DEBIAN:DSA-119, MANDRAKE:MDKSA-2002:019, NETBSD:NetBSD-SA2002-004, OSVDB:730, REDHAT:RHSA-2002:043, SANS-02:U3, XF:openssh-channel-error(8383)",
    "36-0": "Vulnerability Reference URLs",
    "36-1": "These are reference URLs for information about the vulnerability. They appear in the _References_ table of the vulnerability details page. Multiple values separated by commas.Example: http://www.securityfocus.com/bid/29179, http://www.cert.org/advisories/TA08-137A.html, http://www.kb.cert.org/vuls/id/925211, http://www.debian.org/security/DSA-/DSA-1571, http://www.debian.org/security/DSA-/DSA-1576, http://secunia.com/advisories/30136/, http://secunia.com/advisories/30220/",
    "37-0": "Vulnerability Risk Score",
    "37-1": "This is the risk score assigned to the vulnerability. Note that this is different from the asset risk score, which is the overall risk score of the asset.",
    "38-0": "Vulnerable Since",
    "38-1": "This is the date when the vulnerability was first discovered on the scanned asset.",
    "39-0": "Vulnerability Solution",
    "39-1": "This is the solution for remediating the vulnerability. Currently, a solution is exported even if the vulnerability test result was negative. Solutions can include a substantial amount of text. You may need to expand the column in the spreadsheet program for better reading. This value can include line breaks and appears in double quotation marks.",
    "40-0": "Vulnerability Tags",
    "40-1": "These are tags assigned by InsightVM for the vulnerability.",
    "41-0": "Vulnerability Test Result Description",
    "41-1": "This is the word or phrase describing the vulnerability test result. See [Vulnerability result codes](doc:working-with-report-formats#section-vulnerability-result-codes).",
    "42-0": "Vulnerability Test Date",
    "42-1": "This is the date when the vulnerability test was run. It is the same as the last date that asset was scanned. \nFormat: mm/dd/YYYY",
    "43-0": "Vulnerability Test Result Code",
    "43-1": "This is the result code for the vulnerability test. See [Vulnerability result codes](doc:working-with-report-formats#section-vulnerability-result-codes).",
    "44-0": "Vulnerability Severity Level",
    "44-1": "This is the vulnerability’s numeric severity level assigned byInsightVM. Scores range from 1 to 10 and map to severity rankings in the Vulnerability Listing table of the Vulnerabilities page: 1-3=_Moderate_; 4-7=_Severe_; and 8-10=_Critical_. This is not the PCI severity level.",
    "45-0": "Vulnerability Title",
    "45-1": "This is the name of the vulnerability.",
    "27-0": "Vulnerability CVSSv3 Score",
    "27-1": "This is the vulnerability’s Common Vulnerability Scoring System (CVSS) score according to CVSS 3.0 specification.",
    "28-0": "Vulnerability CVSSv3 Vector",
    "28-1": "This is the vulnerability’s Common Vulnerability Scoring System (CVSS) vector according to CVSS 3.0 specification."
  },
  "cols": 2,
  "rows": 46
}
[/block]