---
title: "Generate Reports"
excerpt: ""
---
InsightAppSec allows you to generate vulnerability reports so you can provide status updates to stakeholders within your organization. The Generate Report feature respects any filters applied to your vulnerabilities table and you can choose the format and level of detail in the reports based on your audience.

# Generate a Report
1. Select an App and a Scan for which you wish to generate a report. 
2. On the Scan overview page, click the **Generate Report** link in the upper right side of the screen.
[block:callout]
{
  "type": "info",
  "title": "Note",
  "body": "If you wish to report on only a subset of vulnerabilities, you can apply filters on the vulnerabilities table and select the checkboxes for the relevant vulnerabilities."
}
[/block]
The "Generate Report" panel appears.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/dd54274-Selection_138.png",
        "Selection_138.png",
        415,
        988,
        "#48545f"
      ]
    }
  ]
}
[/block]
3. Provide a name for this report. 
4. If you wish to include ignored vulnerabilities in this report, enable the **Include Ignored Vulnerabilities** switch. 
5. Select the report type followed by the report format from the "Report Types" list. 
6. Click the **Generate Report** button. 
  * If you selected an HTML report, it will auto-generate and open in a new tab. 
  * If you selected a PDF report, the "Generate Report" panel will close and you will see a message on-screen while the PDF report generates. When the report is ready, it will download in your browser.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/8bf8f58-Screen_Shot_2019-04-06_at_6.21.51_AM.png",
        "Screen Shot 2019-04-06 at 6.21.51 AM.png",
        492,
        95,
        "#206659"
      ]
    }
  ]
}
[/block]
#Report Types
## Compliance Reports
InsightAppSec can help you maintain compliance with industry standards such as PCI or GDPR by informing you of security gaps in your web applications. InsightAppSec has a built-in suite of compliance reports that correlate your vulnerabilities to known issues in compliance standards. Before generating a compliance report, we suggest scanning your entire app with the “All Modules” template so you have the most up-to-date vulnerability information around your app. 
[block:callout]
{
  "type": "warning",
  "body": "InsightAppSec reports are advisory only. If a report is generated showing no vulnerabilities, or low severity or safe vulnerabilities, this should not be taken as affirmation of compliance.",
  "title": "Note"
}
[/block]
### Payment Card Industry Report
The PCI Standard is mandated by payment card brands and administered by the Payment Card Industry Security Standards Council. The standard was created to increase controls around cardholder data to reduce credit card fraud. Due to the complexity of the standard, it can be difficult to translate data into actionable tasks that will help achieve compliance. To help reduce complexity, you can run the InsightAppSec PCI report. The report will help you prepare for an audit, an assessment, or a questionnaire around PCI compliance. Uncovering potential issues that will affect the outcome of any of these exercises allows you to take action and secure critical vulnerabilities on any assets that deal with payment card data.

The InsightAppSec PCI report checks online properties for issues such as insecure data collection forms, cookie presence, third-party links, cross-site-scripting vulnerabilities, and SQL-injection vulnerabilities. InsightAppSec uses this information to generate an automatic checklist of potential compliance issues. By taking advantage of this information, you can proactively filter and prioritize identified issues to ensure faster remediation of your organization's most critical regulatory compliance concerns.


###GDPR Report
General Data Protection Regulation (GDPR) compliance has been a legal requirement for all EU companies from the 25th of May, 2018. Organisations can be fined up to 4% of annual global turnover for breaching GDPR. A maximum fine of €20 million can be imposed for the most serious infringements such as not having sufficient customer consent to process data, or violating the core of Privacy by Design concepts. There is a tiered approach to fines. For example, a company can be fined 2% for not having their records in order (article 28), not notifying the supervising authority and data subject about a breach, or not conducting impact assessment. It is important to note that these rules apply to both controllers and processors – meaning ‘clouds’ are not exempt from GDPR enforcement.

InsightAppSec provides an advisory report showing how vulnerabilities in scanned targets might jeopardise your GPDR compliance and highlights which vulnerabilities need to be addressed.