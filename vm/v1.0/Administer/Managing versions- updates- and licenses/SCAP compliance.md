---
title: "SCAP compliance"
excerpt: ""
---
InsightVM complies with Security Content Automation Protocol (SCAP) criteria for an Unauthenticated Scanner product. SCAP is a collection of standards for expressing and manipulating security data in standardized ways. It is mandated by the US government and maintained by the National Institute of Standards and Technology (NIST).

This appendix provides information about how the SCAP standards are implemented for an Unauthenticated Scanner:
* The **Common Platform Enumeration (CPE)** naming scheme, based on the generic syntax for Uniform Resource Identifiers (URI), is a method for identifying operating systems and software applications.
* The **Common Vulnerabilities and Exposures (CVE)** standard prescribes how the product should identify vulnerabilities, making it easier for security products to exchange vulnerability data.
* The **Common Vulnerability Scoring System (CVSS)** is an open frame work for calculating vulnerability risk scores.
* **Common Configuration Enumeration (CCE)** is a standard for assigning unique identifiers known as CCEs to configuration controls to allow consistent identification of these controls in different environments.

##How CPE is implemented

During scans, InsightVM utilizes its fingerprinting technology to recognize target platforms and applications. After completing scans and populating its scan database with newly acquired data, it applies CPE names to fingerprinted platforms and applications whenever corresponding CPE names are available.

Within the database, CPE names are continually kept up to date with changes to the National Institute of Standards (NIST) CPE dictionary. With every revision to the dictionary, the application maps newly available CPE names to application descriptions that previously did not have CPE names.

The Security Console Web interface displays CPE names in scan data tables. You can view these names in listings of assets, software, and operating systems, as well as on pages for specific assets. CPE names also appear in reports in the XML Export format.

##How CVE is implemented

When InsightVM populates its scan database with discovered vulnerabilities, it applies Common Vulnerabilities and Exposures (CVE) identifiers to these vulnerabilities whenever these identifiers are available.

You can view CVE identifiers on vulnerability detail pages in the Security Console Web interface. Each listed identifier is a hypertext link to the CVE online database at nvd.nist.gov, where you can find additional relevant information and links.

You can search for vulnerabilities in the application interface by using CVE identifiers as search criteria.

CVE identifiers also appear in the Discovered Vulnerabilities sections of reports.

The application uses the most up-to-date CVE listing from the CVE mailing list and changelog. Since the application always uses the most up-to-date CVE listing, it does not have to list CVE version numbers. The application updates its vulnerability definitions every six hours through a subscription service that maintains existing definitions and links and adds new ones continuously.

##How CVSS is implemented

For every vulnerability that it discovers, InsightVM computes a Common Vulnerability Scoring System (CVSS) Version 2 score. When data is available, a Version 3 score will be computed as well.  InsightVM will prefer the Version 3 score in the Vulnerability table view, if it exists. In the Security Console Web interface, each vulnerability is listed with its CVSS score. You can use this score, severity rankings, and risk scores based on either temporal or weighted scoring models—depending on your configuration preference—to prioritize vulnerability remediation tasks.

The application incorporates the CVSS score in the PCI Executive Summary and PCI Vulnerability Details reports, which provide detailed Payment Card Industry (PCI) compliance results. Each discovered vulnerability is ranked according to its CVSS score. Rapid7 is an Approved Scanning Vendor (ASV); and InsightVM is a Payment Card Industry (PCI)-sanctioned tool for conducting compliance audits. CVSS scores correspond to severity rankings, which ASVs use to determine which determine whether a given asset is compliant with PCI standards.

The application also includes the CVSS score in report sections that appear in various report templates. The _Highest Risk Vulnerability Details_ section lists highest risk vulnerabilities and includes their categories, risk scores, and their CVSS scores. The _Index of Vulnerabilities_ section includes the severity level and CVSS rating for each vulnerability.

The _PCI Vulnerability Details_ section contains in-depth information about each vulnerability included in a PCI Audit (legacy) report. It quantifies the vulnerability according to its severity level and its CVSS rating.

##How CCE is implemented

InsightVM  tests assets for compliance with configuration policies. It displays the results of compliance tests on the scan results page of every tested asset. The _Policy Listing_ table on this page displays every policy against which the asset was tested.

Every listed policy is a hyperlink to a page about that policy, which includes a table of its constituent rules. Each listed rule is a hyperlink to a page about that rule. The rule page includes detailed technical information about the rule and lists its CCE identifier.

CCE entries can be found via the search feature. See _Using the Search feature_ in the user’s guide.

##Where to find SCAP update information and OVAL files

InsightVM  automatically includes any new SCAP content with each content update. You can view SCAP update information on the _SCAP_ page, which you can access from the _Administration_ page in Security Console Web interface.

Four tables appear on the SCAP page:
* CPE Data
* CVE Data
* CVSS Data
* CCE Data

Each table lists the most recent content update that included new SCAP data and the most recent date that NIST generated new data.

On the SCAP page you also can view a list of Open Vulnerability and Assessment Language (OVAL) files that it has imported during configuration policy checks. In compliance with an FDCC requirement, each listed file name is a hyperlink that you can click to download the XML-structured check content.