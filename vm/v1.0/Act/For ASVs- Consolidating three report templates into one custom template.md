---
title: "For ASVs: Consolidating three report templates into one custom template"
excerpt: ""
---
If you are an approved scan vendor (ASV), you must use the following PCI-mandated report templates for PCI scans as of September 1, 2010:

* Attestation of Compliance
* PCI Executive Summary
* Vulnerability Details

You may find it useful and convenient to combine multiple reports into one template. For example you can create a template that combines sections from the Executive Summary, Vulnerability Details, and Host Details templates into one report that you can present to the customer for the initial review. Afterward, when the post-scan phase is completed, you can create another template that includes the PCI Attestation of Compliance with the other two templates for final delivery of the complete report set.
[block:callout]
{
  "type": "info",
  "body": "PCI Attestation of Scan Compliance is one self-contained section."
}
[/block]
PCI Executive Summary includes the following sections:

* Cover Page
* Payment Card Industry (PCI) Scan Information
* Payment Card Industry (PCI) Component Compliance Summary
* Payment Card Industry (PCI) Vulnerabilities Noted
* Payment Card Industry (PCI) Special Notes

PCI Vulnerability Details includes the following sections:
* Cover Page
* Table of Contents
* Payment Card Industry (PCI) Scan Information
* Payment Card Industry (PCI) Vulnerability Details

PCI Host Detail contains the following sections:
* Table of Contents
* Payment Card Industry (PCI) Scan Information
* Payment Card Industry (PCI) Host Details

To consolidate reports into one custom template:
[block:callout]
{
  "type": "info",
  "body": "Due to PCI Council restrictions, section numbers of PCI reports are static and cannot change to reflect the section structure of a customized report. Therefore, a customized report that mixes PCI report sections with non-PCI report sections may have section numbers that appear out of sequence."
}
[/block]
1. Select the **Manage report templates** tab on the _Reports_ page.
2. Click **New** to create a new report template.
The console displays the _Create a New Report Template_ panel.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/cf24a3f-s_ASV_combined_report_template.jpg",
        "s_ASV_combined_report_template.jpg",
        1165,
        827,
        "#eaeeee"
      ],
      "caption": "Consolidated report template for ASVs."
    }
  ]
}
[/block]
3. Enter a name and description for your custom report on the _View Reports_ page.
The report name is unique.
4. Select the document template type from the drop-down list.
5. Select a level of vulnerability detail to be included in the report from the drop-down list.
6. Specify if you want to display **IP addresses** or **asset names and IP addresses** on the template.
7. Locate the PCI report sections and click **Add**.
[block:callout]
{
  "type": "warning",
  "body": "Do not use sections related to “legacy” reports. These are deprecated and no longer sanctioned by PCI as of September 1, 2010."
}
[/block]
8. Click **Save**.
The Security Console displays the _Manage report templates_ page with the new report template.
[block:callout]
{
  "type": "warning",
  "body": "If you use sections from PCI Executive Summary or PCI Attestation of Compliance templates, you will only be able to use the RTF format. If you attempt to select a different format, an error message is displayed."
}
[/block]