---
title: "Executive Report"
excerpt: ""
---
#Overview
Designed with executives in mind, the Executive Report provides a monthly curated assessment of your organization’s vulnerability management program. If you are a Global Administrator, you will be able to access the Executive Report via the in-product InsightVM link. If you don’t have the correct credentials or role, you will not be able to access the report. An Executive Report for the previous month will be available on the seventh of every month. 

The Executive Report allows you to easily see your remediation efforts in one place so that you can compare data from current and previous reporting periods. For now, the report period is one month. There are also high-level graphs to provide visibility and insight from the previous 12 months, so you can assess monthly trends over the course of the year. 

The report includes easy-to-read visuals, graphs, and explanations. 

##Data Analysis

The Executive Report is divided into several sections: 
  * Environment Overview
  * Program Improvements
  * Cloud
  * Location Tag
  * Owners Tag
  * Criticality Tag

##Environment Overview 

The “Environment Overview” provides a high-level view of data from new and existing assets, new vulnerabilities, and new remediation projects. 

Here is a deeper look at the sections in the “Environment Overview”: 

  * Assets
  * Vulnerabilities
  * Remediation

###Assets
The “Assets” section gives you an overview of your assets data over the course of one month. 

Here’s what’s covered in the “Assets” section: 
  * **Total Assessed Assets** -  Shows the number of assets that were scanned for vulnerabilities. 
  * **Risk Score** - Measures the difficulty needed to fix a vulnerability or asset. The Executive Report defines risk score as the total overall score for known assets and their vulnerabilities. Ideally, risk scores should decline as time passes and can help you prioritize vulnerabilities and assets. For more information, see our [PCI, CVSS, & Risk Scoring](doc:pci-cvss-risk-scoring-frequently-asked-questions) help documentation.  
  * The **Assessed Assets vs Risk Over Time** chart -  Shows trends of your total risk score over the past 12 months, while compared to the total number of assessed assets over the same time period.  Showing the assessed assets provides context to noticeable changes in risk from month to month. For example, an increase in risk may be caused by more asset assessments, not an increase in risk per asset.
  * **New Assets** -  Represents the number of assets that are new in your environment during the reporting period. 
  * **Assessment Ratio** - Shows the percentage of assessed total assets compared to unaccessed assets within the reporting period. To create the percentage, it compares the number of assets that were scanned for vulnerabilities to the number of assets that were not scanned for vulnerabilities.  
  * **New Software** - Represents the number of new software applications in your environment.
  * **New Services** - Represents the number of new services in your environment.
  * The **“Discovered Assets”** chart - Shows the percentage of assets that were scanned for vulnerabilities, or assessed assets, against the number of assets that were scanned for vulnerabilities in your known environment within the report period. This chart tells you how many unscanned assets exist, but it does not tell you what vulnerabilities exist on these assets, which is why these particular assets are called blind spots. 
  * The “**Assessment Counts of Assets**” visualization - Shows a cluster of circles with a number inside each one, which indicates the number of assets in an assessment. The size of the circle represents the number of times those assets were assessed during the reporting period. For example, the number of assets inside the biggest circle indicates that specific number of assets were assessed the most. The number of assets in the smallest circle indicates that those number of assets were assessed the least. 

In addition, you’ll also see the average number of assessments for the reporting period. 

###Vulnerabilities
The “Vulnerabilities”  section provides an overall view of your vulnerabilities data over the course of the report period. You can use this data to understand the scale and effectiveness of your security assessment operations. 

Here’s what’s covered in the “Vulnerabilities” section: 
  * **Total Vulnerabilities** is the number of vulnerabilities that were scanned during the report period. 
  * **Critical Vulnerabilities** shows the percentage of critical vulnerabilities in proportion to your total number of vulnerabilities.
  * The **Vulnerabilities and Risk Over Time** graph shows trends of your total risk score over the past 12 months, while compared to the total number of targeted and known vulnerabilities over the same time period. Showing targeted and known vulnerabilities provides context to noticeable changes in risk from month to month. For example, a spike in Risk Score indicates a spike in Vulnerabilities, Targeted Vulnerabilities, or both.
  * **New Vulnerabilities** is the number of vulnerabilities that are new in your environment. 
  * **New Targeted Vulnerabilities** is the number of targeted vulnerabilities that are new in your environment. A targeted vulnerability is a vulnerability actively being targeted by attackers, based on Rapid7’s threat intelligence research. 
  * **New Risk** is the total number of new risks in your environment. 
  * **New Vulnerabilities by Criticality** shows the percentage of new vulnerabilities organized by risk level. The three states are critical, severe, and moderate. 
  * **Vulnerability Criticality** shows the percentage of total vulnerabilities organized by risk level. The three states are critical, severe, and moderate. 
  * **Available Exploits** is the number of exploits in your environment.   
  * **Available Malware Kits** is the number of malware kits in your environment. A malware kit, or exploit kit, is a tool that makes it easier for attackers to write and deploy malicious code to attack targets through associated vulnerabilities. 

###Remediation
The remediation overview can help you assess your organization’s efficiency in reducing risk during the report period. Prioritize your remediation efforts to address exploitable and targeted vulnerabilities, which pose the highest risk. 

Here’s what’s covered in the Remediation Overview: 
  * **Remediated Vulnerabilities** is the number of vulnerabilities that were remediated, or resolved, during the report period. 
  * **New Risk vs Remediated Risk** shows the ratio of new risk to remediated risk for this report period.
  * The “**Total Risk and Remediated Risk**” graph shows trend data for new and remediated risk over time. This indicates how efficient your InsightVM program is at addressing new vulnerabilities as they are found. 
  * **Remediated Vulnerabilities** shows the number of vulnerabilities that were remediated, or resolved, during the report period. It also shows the increase or decrease in remediated vulnerabilities from the previous reporting period. 
  * **Remediated Targeted Vulnerabilities** is the number of targeted vulnerabilities [anchor link to targeted vulns above] that were remediated during the report period. It also shows the increase or decrease in remediated vulnerabilities from the previous reporting period. 
  * **Remediated Risk** is the total number of remediated risks in your environment. It also shows the increase or decrease in remediated vulnerabilities from the previous reporting period.
  * **Remediated Vulnerabilities by Criticality** shows the percentage of remediated vulnerabilities organized by risk level. The three states are critical, severe, and moderate. 
  * **Average Remediation by Criticality** shows the average number of days it takes to remediate a criticality, which is organized by risk level. The three states are critical, severe, and moderate. 
  * **Remediated Exploits** is the number of remediated exploits in your environment.   
  * **Remediated Malware Kits** is the number of remediated malware kits in your environment. A malware kit is a tool that makes it easier for attackers to write and deploy malicious code to attack targets through associated vulnerabilities. 

##Program Improvements
The Program Improvements overview provides data about InsightVM’s Remediation Projects feature, tagged assets, and assets installed with Insight Agent. 

Here’s what’s covered in the Program Improvements overview: 
  * **New Remediation Projects** is the number of remediation projects that were opened during the reporting period. 
  * **Closed Remediation Projects** is the number of remediation projects that were closed during the reporting period.

[block:callout]
{
  "type": "info",
  "body": "The rate at which Remediation Projects open and close can indicate how efficient remediation efforts are.",
  "title": "NOTE"
}
[/block]
  * **Tagged Assets** is the number of assets that were tagged during the reporting period. The number of tagged assets from the previous reporting period, as well as the percent increase or decrease, is also shown. For more information on tags, see [Applying RealContext with tags](doc:applying-realcontext-with-tags). 
  * **Assets with Agents** is the number of assets installed with Insight Agent. The number of assets installed with Insight Agent from the previous reporting period and the percent increase or decrease is also shown. For more information, see our [Insight Agent](doc:using-the-agent-with-insightvm)  help documentation. 

##Location Tags
The Location Tags overview provides metrics about assets tagged by location.  

Here’s what’s covered in the Location Tags overview: 
  * **Location Tags** is the total number of assets designated with a location tag during the reporting period. 
  * The next metric shows the percentage of assets in your environment that are tagged by location.  
  * **Top Five Locations** shows the total number, percentage, and places that have the most assets tagged with location tags. 
  * **New Risk by Location** shows the top five places that have the newest assets with the highest risk score. These assets must all be tagged with a location tag. 
  * **Remediated Risk by Location** shows the top five places that have remediated the most risk. These assets must all be tagged with a location tag. 

##Owner Tags
The Owner Tags overview provides metrics about assets tagged by asset owner.  

Here’s what’s covered in the Owner Tags overview: 
  * **Owner Tags** is the total number of assets designated with an owner tag during the reporting period. 
  * The next metric shows the percentage of assets in your environment that is tagged by owner.  
  * **Top Five Owners** shows the total number, percentage, and places that have the most assets tagged with owner tags. 
  * **New Risk by Owner** shows the top five owners who have new assets with the highest risk score. These assets must all be tagged with an owner tag. 

##Criticality Tags
The Criticality Tags overview provides metrics about assets tagged by criticality. Assets can be tagged with a critical, severe, or moderate tag. 

Here’s what’s covered in the Criticality Tags overview: 
  * **Criticality Tags** is the total number of assets designated with a criticality tag during the reporting period. 
  * The next metric shows the percentage of assets in your environment that is tagged by criticality.  
Assets by Criticality Tag compares the number and percentage of assets tagged with a criticality tag to non-criticality tagged assets in your environment. 
  * **Top Five Criticalities** shows the total number, percentage, and risk level of vulnerabilities in this report period. These assets must all be tagged with a criticality tag. 
  * **Remediated Risk by Criticality** shows the number of resolved vulnerabilities that were tagged with a criticality tag.