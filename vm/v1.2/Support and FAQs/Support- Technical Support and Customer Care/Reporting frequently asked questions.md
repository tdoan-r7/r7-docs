---
title: "Reporting frequently asked questions"
excerpt: ""
---
This page concerns generating and reading reports.

## How are the XML report export options different?

Four XML report export options are available in InsightVM. You will see these options in the _General_ page of the Report Configuration wizard. They appear in a dropdown list with other export options. The formats differ in content, structure, and purpose:

* _XML Export_, also known as "raw XML," contains all possible data from a scan with minimal structure. Its contents must be parsed so that other systems can use its information.
* _Nexpose&trade;Simple XML_ is also a "raw XML" format. It is ideal for integration of scan data with the Metasploit vulnerability exploit framework. It contains a subset of the data available in the XML Export format:
hosts scanned
vulnerabilities found on those hosts
services scanned
vulnerabilities found in those services

* _SCAP Compatible XML_ is also a "raw XML" format that includes Common Platform Enumeration (CPE) names for fingerprinted platforms. This format supports compliance with Security Content Automation Protocol (SCAP) criteria for an Unauthenticated Scanner product.
* _XML_ arranges data in clearly organized, human-readable XML and is ideal for exporting to other document formats.
* _Qualys* XML Export_ is intended for integration with the Qualys reporting framework.

_ *Qualys is a trademark of Qualys, Inc._

## How does the Baseline Comparison report work?

A Baseline Comparison report displays data from the most recent scan and compares it to data from a preceding scan that you designate as a baseline. You have to have run more than one scan in order to create a Baseline Comparison report. When you are creating or modifying a report, go to the _General_ page of the configuration wizard. Select the Baseline Comparison report template. Go to the _Baseline_ page and select one of the options to designate as a baseline. You can use either the first scan ever run, the most recent preceding scan, or a scan from a particular date.

## How do I export report data to Microsoft Excel in Internet Explorer 7?

Add the URL of your InsightVM Security Console Web interface to your Internet Explorer 7 Trusted Sites. You will find the _Trusted Sites_ tab under _Tools_ | _Internet Options_ | _Security_. While you're in the _Trusted Sites_ dialog box, click the **Custom level...** button. Scroll to the section labeled _Initialize and script ActiveX controls not marked safe for scripting_. Select the **Prompt** option button.

You should see the green check marked labeled "Trusted Sites" displayed in the lower right hand of Internet Explorer window when you have the InsightVM site running in the browser. If so, the Excel Export feature will work.

## What are the result codes in CSV Export reports?

Each code corresponds to results of a vulnerability check:
* ve (vulnerable, exploited): The check was positive as indicated by asset-specific vulnerability tests. Vulnerabilities with this result appear in the CSV report if the Vulnerabilities found result type was selected in the report configuration.
* vv (vulnerable, version check): A check was positive because the version of the scanned service or application is associated with known vulnerabilities.
* vp (vulnerable, potential): The check for a potential vulnerability was positive.
* ee (excluded, exploited): A check for an exploitable vulnerability was excluded.
* ev (excluded, version check): A check for a vulnerability that can be identified because the version of the scanned service or application is associated with known vulnerabilities was excluded.
* ep (excluded, potential): A check for a potential vulnerability was excluded.
* nv (not vulnerable): InsightVM did not find the target application or service to be vulnerable.
* uk (unknown): InsightVM was unable to determine whether the scanned service or application is vulnerable.
* sd (skipped because of DoS settings): InsightVM skipped the check because it involves Denial of * Service settings.
* sv (skipped because of inapplicable version): InsightVM skipped the check because the version of the target service or application is not associated with the given vulnerability.
* er (error during check): InsightVM encountered an error during the check.
* ds (skipped, disabled): A check was not performed because it was disabled in the scan template.
* ov (overridden, version check): A check for a vulnerability that would ordinarily be positive because the version of the target service or application is associated with known vulnerabilities was negative due to information from other checks.
* nt (no tests): There were no checks to perform.