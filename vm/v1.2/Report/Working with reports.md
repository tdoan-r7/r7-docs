---
title: "Working with reports"
excerpt: ""
---
You may want any number of people in your organization to view asset and vulnerability data without actually logging on to the Security Console. For example, a chief information security officer (CISO) may need to see statistics about your overall risk trends over time. Or members of your security team may need to see the most critical vulnerabilities for sensitive assets so that they can prioritize remediation projects. It may be unnecessary or undesirable for these stakeholders to access the application itself. By generating reports, you can distribute critical information to the people who need it via e-mail or integration of exported formats such as XML, CSV, or database formats.

Reports provide many, varied ways to look at scan data, from business-centric perspectives to detailed technical assessments. You can learn everything you need to know about vulnerabilities and how to remediate them, or you can just list the services are running on your network assets.

You can create a report on a site, but reports are not tied to sites. You can parse assets in a report any number of ways, including all of your scanned enterprise assets, or just one.
[block:callout]
{
  "type": "info",
  "body": "For information about other tools related to compliance with Policy Manager policies, see _What are your compliance requirements?_, which you can download from the _Support_ page in Help."
}
[/block]
If you are verifying compliance with PCI, you will use the following report templates in the audit 
process:

* Attestation of Compliance
* PCI Executive Summary
* Vulnerability Details

If you are verifying compliance with United States Government Configuration Baseline (USGCB) or Federal Desktop Core Configuration (FDCC) policies, you can use the following report formats to capture results data:

* XCCDF Human Readable CSV Report
* XCCDF Results XML Report
[block:callout]
{
  "type": "info",
  "body": "You also can click the top row check box to select all requests and then approve or reject them in one step."
}
[/block]
You can also generate an XML export reports that can be consumed by the CyberScope application to fulfill the U.S. Government’s Federal Information Security Management Act (FISMA) reporting requirements.

Reports are primarily how your asset group members view asset data. Therefore, it’s a best practice to organize reports according to the needs of asset group members. If you have an asset group for Windows 2008 servers, create a report that only lists those assets, and include a section on policy compliance.

Creating reports is very similar to creating scan jobs. It’s a simple process involving a configuration panel. You select or customize a report template, select an output format, and choose assets for inclusion. You also have to decide what information to include about these assets, when to run the reports, and how to distribute them.

All panels have the same navigation scheme. You can either use the navigation buttons in the upper-right corner of each panel page to progress through each page of the panel, or you can click a page link listed on the left column of each panel page to go directly to that page.
[block:callout]
{
  "type": "info",
  "body": "Parameters labeled in red denote required parameters on all panel pages."
}
[/block]
To save configuration changes, click **Save** that appears on every page. To discard changes, click **Cancel**.