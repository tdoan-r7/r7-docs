---
title: "Working with risk strategies to analyze threats"
excerpt: ""
---
One of the biggest challenges to keeping your environment secure is prioritizing remediation of vulnerabilities. If InsightVM discovers hundreds or even thousands of vulnerabilities with each scan, how do you determine which vulnerabilities or assets to address first?

Each vulnerability has a number of characteristics that indicate how easy it is to exploit and what an attacker can do to your environment after performing an exploit. These characteristics make up the vulnerability’s risk to your organization.

Every asset also has risk associated with it, based on how sensitive it is to your organization’s security. For example, if a database that contains credit card numbers is compromised, the damage to your organization will be significantly greater than if a printer server is compromised.

The application provides several strategies for calculating risk. Each strategy emphasizes certain characteristics, allowing you to analyze risk according to your organization’s unique security needs or objectives. You can also create custom strategies and integrate them with the application.

After you select a risk strategy you can use it in the following ways:

* Sort how vulnerabilities appear in Web interface tables according to risk. By sorting vulnerabilities you can make a quick visual determination as to which vulnerabilities need your immediate attention and which are less critical.
* View risk trends over time in reports, which allows you to track progress in your remediation effort or determine whether risk is increasing or decreasing over time in different segments of your network.

Working with risk strategies involves the following activities:

* [Changing your risk strategy and recalculating past scan data](doc:working-with-risk-strategies-to-analyze-threats#section-changing-your-risk-strategy-and-recalculating-past-scan-data)
* [Using custom risk strategies](doc:working-with-risk-strategies-to-analyze-threats#section-using-custom-risk-strategies)
* [Changing the appearance order of risk strategies](doc:working-with-risk-strategies-to-analyze-threats#section-changing-the-appearance-order-of-risk-strategies)

##Comparing risk strategies

Each risk strategy is based on a formula in which factors such as likelihood of compromise, impact of compromise, and asset importance are calculated. Each formula produces a different range of numeric values. For example, the Real Risk strategy produces a maximum score of 1,000, while the Temporal strategy has no upper bounds, with some high-risk vulnerability scores reaching the hundred thousands. This is important to keep in mind if you apply different risk strategies to different segments of scan data. See [Changing your risk strategy and recalculating past scan data](doc:working-with-risk-strategies-to-analyze-threats#section-changing-your-risk-strategy-and-recalculating-past-scan-data).

Many of the available risk strategies use the same factors in assessing risk, each strategy evaluating and aggregating the relevant factors in different ways. The common risk factors are grouped into three categories: vulnerability impact, initial exploit difficulty, and threat exposure. The factors that comprise vulnerability impact and initial exploit difficulty are the six base metrics employed in Version 2 of the Common Vulnerability Scoring System (CVSS).

* Vulnerability impact is a measure of what can be compromised on an asset when attacking it through the vulnerability, and the degree of that compromise. Impact is comprised of three factors:
   * _Confidentiality impact_ indicates the disclosure of data to unauthorized individuals or systems.
   * _Integrity impact_ indicates unauthorized data modification.
   * _Availability impact_ indicates loss of access to an asset's data.
* Initial exploit difficulty is a measure of likelihood of a successful attack through the vulnerability, and is comprised of three factors:
   * _Access vector_ indicates how close an attacker needs to be to an asset in order to exploit the vulnerability. If the attacker must have local access, the risk level is low. Lesser required proximity maps to higher risk.
   * _Access complexity_ is the likelihood of exploit based on the ease or difficulty of perpetrating the exploit, both in terms of the skill required and the circumstances which must exist in order for the exploit to be feasible. Lower access complexity maps to higher risk.
   * _Authentication_ requirement is the likelihood of exploit based on the number of times an attacker must authenticate in order to exploit the vulnerability. Fewer required authentications map to higher risk.
* Threat exposure includes three variables:
   * _Vulnerability age_ is a measure of how long the security community has known about the vulnerability. The longer a vulnerability has been known to exist, the more likely that the threat community has devised a means of exploiting it and the more likely an asset will encounter an attack that targets the vulnerability. Older vulnerability age maps to higher risk.
   * _Exploit exposure_ is the rank of the highest-ranked exploit for a vulnerability, according to the Metasploit Framework. This ranking measures how easily and consistently a known exploit can compromise a vulnerable asset. Higher exploit exposure maps to higher risk.
   * _Malware exposure_ is a measure of the prevalence of any malware kits, also known as exploit kits, associated with a vulnerability. Developers create such kits to make it easier for attackers to write and deploy malicious code for attacking targets through the associated vulnerabilities.

Review the summary of each model before making a selection.

##Real Risk strategy

This strategy is recommended because you can use it to prioritize remediation for vulnerabilities for which exploits or malware kits have been developed. A security hole that exposes your environment to an unsophisticated exploit or an infection developed with a widely accessible malware kit is likely to require your immediate attention. The Real Risk algorithm applies unique exploit and malware exposure metrics for each vulnerability to CVSS base metrics for likelihood and impact.
[block:callout]
{
  "type": "info",
  "body": "Real Risk is computed using CVSSv2 metrics."
}
[/block]
Specifically, the model computes a maximum impact between 0 and 1,000 based on the confidentiality impact, integrity impact, and availability impact of the vulnerability. The impact is multiplied by a likelihood factor that is a fraction always less than 1. The likelihood factor has an initial value that is based on the vulnerability's initial exploit difficulty metrics from CVSS: access vector, access complexity, and authentication requirement. The likelihood is modified by threat exposure: likelihood matures with the vulnerability's age, growing ever closer to 1 over time. The rate at which the likelihood matures over time is based on exploit exposure and malware exposure. A vulnerability's risk will never mature beyond the maximum impact dictated by its CVSS impact metrics.

The Real Risk strategy can be summarized as base impact, modified by initial likelihood of compromise, modified by maturity of threat exposure over time. The highest possible Real Risk score is 1,000.

##TemporalPlus strategy

Like the Temporal strategy, TemporalPlus emphasizes the length of time that the vulnerability has been known to exist. However, it provides a more granular analysis of vulnerability impact by expanding the risk contribution of partial impact vectors.

The TemporalPlus risk strategy aggregates proximity-based impact of the vulnerability, using confidentiality impact, integrity impact, and availability impact in conjunction with access vector. The impact is tempered by an aggregation of the exploit difficulty metrics, which are access complexity and authentication requirement. The risk then grows over time with the vulnerability age.

The TemporalPlus strategy has no upper bounds. Some high-risk vulnerability scores reaching the hundred thousands.

This strategy distinguishes risk associated with vulnerabilities with “partial” impact values from risk associated with vulnerabilities with “none” impact values for the same vectors. This is especially important to keep in mind if you switch to TemporalPlus from the Temporal strategy, which treats them equally. Making this switch will increase the risk scores for many vulnerabilities already detected in your environment.

##Temporal strategy

This strategy emphasizes the length of time that the vulnerability has been known to exist, so it could be useful for prioritizing older vulnerabilities for remediation. Older vulnerabilities are regarded as likelier to be exploited because attackers have known about them for a longer period of time. Also, the longer a vulnerability has been in an existence, the greater the chance that less commonly known exploits exist.

The Temporal risk strategy aggregates proximity-based impact of the vulnerability, using confidentiality impact, integrity impact, and availability impact in conjunction with access vector. The impact is tempered by dividing by an aggregation of the exploit difficulty metrics, which are access complexity and authentication requirement. The risk then grows over time with the vulnerability age.

The Temporal strategy has no upper bounds. Some high-risk vulnerability scores reach the hundred thousands.

##Weighted strategy

The Weighted strategy can be useful if you assign levels of importance to sites or if you want to assess risk associated with services running on target assets. The strategy is based primarily on site importance, asset data, and vulnerability types, and it emphasizes the following factors:
* vulnerability severity, which is the number—ranging from 1 to 10—that the application calculates for each vulnerability
* number of vulnerability instances
* number and types of services on the asset; for example, a database has higher business value
* the level of importance, or weight, that you assign to a site when you configure it; see [Configuring a site using a Dynamic Discovery connection](doc:managing-dynamic-discovery-of-assets#section-configuring-a-site-using-a-dynamic-discovery-connection) or [Getting started: Info & Security](doc:creating-and-editing-sites#section-getting-started-info-security).
* Weighted risk scores scale with the number of vulnerabilities. A higher number of vulnerabilities on an asset means a higher risk score. The score is expressed in single- or double-digit numbers with decimals.

##PCI ASV 2.0 Risk strategy

The PCI ASV 2.0 Risk strategy applies a score based on the Payment Card Industry Data Security Standard (PCI DSS) Version 2.0 to every discovered vulnerability. The scale ranges from 1 (lowest severity) to 5 (highest severity). With this model, Approved Scan Vendors (ASVs) and other users can assess risk from a PCI perspective by sorting vulnerabilities based on PCI 2.0 scores and viewing these scores in PCI reports. Also, the five-point severity scale provides a simple way for your organization to assess risk at a glance.

##Changing your risk strategy and recalculating past scan data

You may choose to change the current risk strategy to get a different perspective on the risk in your environment. Because making this change could cause future scans to show risk scores that are significantly different from those of past scans, you also have the option to recalculate risk scores for past scan data.

Doing so provides continuity in risk tracking over time. If you are creating reports with risk trend charts, you can recalculate scores for a specific scan date range to make those scores consistent with scores for future scans. This ensures continuity in your risk trend reporting.

For example, you may change your risk strategy from Temporal to Real Risk on December 1 to do exposure-based risk analysis. You may want to demonstrate to management in your organization that investment in resources for remediation at the end of the first quarter of the year has had a positive impact on risk mitigation. So, when you select Real Risk as your strategy, you will want to calculate Real Risk scores for all scan data since April 1.

Calculation time varies. Depending on the amount of scan data that is being recalculated, the process may take hours. You cannot cancel a recalculation that is in progress.
[block:callout]
{
  "type": "info",
  "body": "You can perform regular activities, such as scanning and reporting while a recalculation is in progress. However, if you run a report that incorporates risk scores during a recalculation, the scores may appear to be inconsistent. The report may incorporate scores from the previously used risk strategy as well as from the newly selected one."
}
[/block]
To change your risk strategy and recalculate past scan data, take the following steps:

Go to the _Risk Strategies_ page.
1. Click the **Administration** icon in the Security Console Web interface.
The console displays the _Administration_ page.
2. Click **Manage** for _Global Settings_.
The Security Console displays the _Global Settings_ panel.
3. Click **Risk Strategy** in the left navigation pane.
The Security Console displays the _Risk Strategies_ page

Select a new risk strategy.
1. Click the arrow for any risk strategy on the _Risk Strategies_ page to view information about it.
Information includes a description of the strategy and its calculated factors, the strategy’s source (built-in or custom), and how long it has been in use if it is the currently selected strategy.
2. Click the radio button for the desired risk strategy.
3. Select **Do not recalculate** if you do not want to recalculate scores for past scan data.
4. Click **Save**. You can ignore the following steps.

(_Optional_) View risk strategy usage history.

This allows you to see how different risk strategies have been applied to all of your scan data. This information can help you decide exactly how much scan data you need to recalculate to prevent gaps in consistency for risk trends. It also is useful for determining why segments of risk trend data appear inconsistent.

1. Click **Usage history** on the _Risk Strategies_ page.
2. Click the **Current Usage** tab in the _Risk Strategy Usage_ box to view all the risk strategies that are currently applied to your entire scan data set.
Note the _Status_ column, which indicates whether any calculations did not complete successfully. This could help you troubleshoot inconsistent sections in your risk trend data by running the calculations again.
3. Click the _Change Audit_ tab to view every modification of risk strategy usage in the history of your installation.
The table in this section lists every instance that a different risk strategy was applied, the affected date range, and the user who made the change. This information may also be useful for troubleshooting risk trend inconsistencies or for other purposes.
4. (Optional) Click the **Export to CSV** icon to export the change audit information to CSV format, which you can use in a spreadsheet for internal purposes.

Recalculate risk scores for past scan data.
1. Click the radio button for the date range of scan data that you want to recalculate. If you select **Entire history**, the scores for all of your data since your first scan will be recalculated.
2. Click **Save**.
The console displays a box indicating the percentage of recalculation completed.

##Using custom risk strategies

You may want to calculate risk scores with a custom strategy that analyzes risk from perspectives that are very specific to your organization’s security goals. You can create a custom strategy and use it in InsightVM.

Each risk strategy is an XML document. It requires the _RiskModel_ element, which contains the id attribute, a unique internal identifier for the custom strategy.

_RiskModel_ contains the following required sub-elements.
* _name:_ This is the name of the strategy as it will appear in the Risk Strategies page of the Web interface. The datatype is xs:string.
* _description:_ This is the description of the strategy as it will appear in the Risk Strategies page of the Web interface. The datatype is xs:string.
[block:callout]
{
  "type": "info",
  "body": "The Rapid7 Professional Services Organization (PSO) offers custom risk scoring development. For more information, contact your account manager."
}
[/block]
* _VulnerabilityRiskStrategy_: This sub-element contains the mathematical formula for the strategy. It is recommended that you refer to the XML files of the built-in strategies as models for the structure and content of the VulnerabilityRiskStrategy sub-element.

A custom risk strategy XML file contains the following structure:
```
<?xml version="1.0" encoding="UTF-8" standalone="yes"?>
<RiskModel id="custom_risk_strategy">
   <name>Primary custom risk strategy</name>
   <description>
       This custom risk strategy emphasizes a number of important factors.
   </description>
   <VulnerabilityRiskStrategy>
       [formula]
   </VulnerabilityRiskStrategy>
</RiskModel>
```
[block:callout]
{
  "type": "info",
  "body": "Make sure that your custom strategy XML file is well-formed and contains all required elements to ensure that the application performs as expected."
}
[/block]
To make a custom risk strategy available in InsightVM, take the following steps:
1. Copy your custom XML file into the directory
[installation_directory]/shared/riskStrategies/custom/global.
2. Restart the Security Console.

The custom strategy appears at the top of the list on the _Risk Strategies_ page.

##Setting the appearance order for a risk strategy

To set the order for a risk strategy, add the optional order sub-element with a number greater than 0 specified, as in the following example. Specifying a 0 would cause the strategy to appear last.
```
<?xml version="1.0" encoding="UTF-8" standalone="yes"?>
<RiskModel id="janes_risk_strategy">
   <name>Jane’s custom risk strategy</name>
   <description>
        Jane’s custom risk strategy emphasizes factors important to Jane.
   </description>
   <order>1</order>
   <VulnerabilityRiskStrategy>
       [formula]
   </VulnerabilityRiskStrategy>
</RiskModel>
```
To set the appearance order:
1. Open the desired risk strategy XML file, which appears in one of the following directories:
   * for a custom strategy: [installation_directory]/shared/riskStrategies/custom/global
   * for a built-in strategy: [installation_directory]/shared/riskStrategies/builtin
2. Add the _order_ sub-element with a specified numeral to the file, as in the preceding example.
3. Save and close the file.
4. Restart the Security Console.

##Changing the appearance order of risk strategies

You can change the order of how risk strategies are listed on the _Risk Strategies_ page. This could be useful if you have many strategies listed and you want the most frequently used ones listed near the top. To change the order, you assign an order number to each individual strategy using the optional order element in the risk strategy’s XML file. This is a sub-element of the _RiskModel_ element. See [Using custom risk strategies](doc:working-with-risk-strategies-to-analyze-threats#section-using-custom-risk-strategies).

For example: Three people in your organization create custom risk strategies: _Jane’s Risk Strategy_, _Tim’s Risk Strategy_, and _Terry’s Risk Strategy_. You can assign each strategy an order number. You can also assign order numbers to built-in risk strategies.

A resulting order of appearance might be the following:
* _Jane’s Risk Strategy_ (1)
* _Tim’s Risk Strategy_ (2)
* _Terry’s Risk Strategy_ (3)
* Real Risk (4)
* TemporalPlus (5)
* Temporal (6)
* Weighted (7)
[block:callout]
{
  "type": "info",
  "body": "The order of built-in strategies will be reset to the default order with every product update."
}
[/block]
Custom strategies always appear above built-in strategies. So, if you assign the same number to a custom strategy and a built-in strategy, or even if you assign a lower number to a built-in strategy, custom strategies always appear first.

If you do not assign a number to a risk strategy, it will appear at the bottom in its respective group (custom or built-in). In the following sample order, one custom strategy and two built-in strategies are numbered 1.

One custom strategy and one built-in strategy are not numbered:
* _Jane’s Risk Strategy_ (1)
* _Tim’s Risk Strategy_ (2)
* _Terry’s Risk Strategy_ (no number assigned)
* Weighted (1)
* Real Risk (1)
* TemporalPlus (2)
* Temporal (no number assigned)

Note that a custom strategy, _Tim’s_, has a higher number than two numbered, built-in strategies; yet it appears above them.

##Understanding how risk scoring works with scans

An asset goes through several phases of scanning before it has a status of _completed_ for that scan. An asset that has not gone through all the required scan phases has a status of _in progress_. InsightVM only calculates risk scores based on data from assets with _completed_ scan status.

If a scan pauses or stops, The application does not use results from assets that do not have _completed_ status for the computation of risk scores. For example: 10 assets are scanned in parallel. Seven have _completed_ scan status; three do not. The scan is stopped. Risk is calculated based on the results for the seven assets with _completed_ status. For the three _in progress_ assets, it uses data from the last completed scan.

To determine scan status consult the scan log. See [Viewing the scan log](doc:running-a-manual-scan#section-viewing-the-scan-log).