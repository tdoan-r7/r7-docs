---
title: "Cloud Configuration Assessment Interface Guide"
excerpt: ""
---
[block:callout]
{
  "type": "info",
  "body": "A feature that is in \"preview\" has made enough progress to be suitable for customer use, albeit still in active development.\n\nInsightVM customers can take advantage of this preview offering to provide early feedback and usage data that will shape the final version of Cloud Configuration Assessment when it becomes Generally Available (GA).\n\nLike other preview features, the Cloud Configuration Assessment preview may not yet have all the functionality planned for the GA version and may only be accessible from cloud-enabled pages in InsightVM (such as the **Dashboard** tab).  Using this preview will not affect your production data.\n\nYou can provide your feedback on the Cloud Configuration Assessment preview by completing the following survey:\n\nhttps://www.surveygizmo.com/s3/4936396/VM-Cloud-Configuration-Assessment-Survey\n\nThe following features are not yet available in the preview, but are planned for GA:\n* Ability to group rules into benchmarks",
  "title": "NOTE: Cloud Configuration Assessment is currently available in \"preview\" form"
}
[/block]
After you [configure a connection](doc:cloud-configuration-assessment-overview#section-supported-iaas-providers) to your Infrastructure-as-a-Service (IaaS) providers, you can use the Cloud Configuration Assessment interface to read your assessment results, examine support materials, and learn how to address your non-compliant resources.

This article covers the following topics:

* [Interface Overview](doc:cloud-configuration-assessment-interface-guide#section-interface-overview)
* [Filter Capabilities](doc:cloud-configuration-assessment-interface-guide#section-filter-capabilities)
* [How to Read Assessment Results](doc:cloud-configuration-assessment-interface-guide#section-how-to-read-assessment-results)
* [Rule Exceptions](doc:cloud-configuration-assessment-interface-guide#section-rule-exceptions)
* [Connection Management](doc:cloud-configuration-assessment-interface-guide#section-connection-management)

# Interface Overview

The Cloud Configuration Assessment interface is organized according to the following tabs:

* [Findings View](doc:cloud-configuration-assessment-interface-guide#section-findings-view)
* [Resources View](doc:cloud-configuration-assessment-interface-guide#section-resources-view)
* [Rules View](doc:cloud-configuration-assessment-interface-guide#section-rules-view)
* [Exceptions View](doc:cloud-configuration-assessment-interface-guide#section-exceptions-view)

## Findings View

Click the **Findings** tab to view your total findings and a corresponding filterable table.  Remember that “findings” in Cloud Configuration Assessment are individual instances of a specific rule check across your IaaS resources.  You can have multiple findings of the same rule with varying results as each finding is attached to a specific resource.

### Table Data

Table rows for your individual findings contain the following data columns:

* **Service** - The IaaS service or app responsible for deploying your resource.
* **Rule** - The service-tailored rule that was applied to your resource.
* **Resource** - The individual instance of a service that was checked for rule compliance.
* **Status** - The result of the rule check, which can be either a “Pass” or “Fail” value.
* **Severity** - The security impact for the rule if the resource is non-compliant.
* **Account** - The name of the connection that yielded this finding. This is the same name that you * provided when you originally configured the connection.
* **Region** - The data region where your resource is located.
* **Actions** - This column contains additional functions if the finding is in the “Fail” state:
 * Click the **information** icon to examine the rule check result of this finding in detail. The “Finding Details” screen includes the proof of the failing rule check and the remediation procedure that will correct it.
 * Click the **cancel** icon to [configure an exception](doc:cloud-configuration-assessment-interface-guide#section-how-to-configure-an-exception) for the rule associated with this particular finding.

### Severity Scale

All rules in Cloud Configuration Assessment are ranked according to Rapid7’s severity scale.  These rankings are similar to those that apply to vulnerabilities tracked by other InsightVM features, but some variation exists to meet the Cloud Configuration Assessment use case.  

For ease of recognition, findings in the “Fail” state display their severity rankings by color as well.

Cloud Configuration Assessment rules can have one of the following severity rankings:

* Critical
* Severe
* Moderate
* Low
* Info
[block:callout]
{
  "type": "info",
  "title": "What is the “Info” ranking?",
  "body": "Some Cloud Configuration Assessment rules are ranked as “Info” in lieu of standard severity rankings.  Rules with “Info” ranks may not have a security impact at present, but should be addressed nonetheless.  For example, resources that are unused or have certificates approaching expiration will be ranked with the “Info” tag."
}
[/block]
## Resources View

Click the **Resources** tab to view all your different IaaS services and their corresponding number of deployed instances discovered by your configured connections.  Your total number of detected services is located in parentheses in the “Services” table.

The “Services” table contains the following columns:

* **Type** - The name of the service or app in use.
* **Regions** - The number of regions where instances of this service are found.
* **Accounts** - The number of connections that yielded the instances of this service.
* **Resources** - The number of individual deployed instances of this service.
* **Details** - The instance breakdown of this service by category.

## Rules View

Click the **Rules** tab to view all the Cloud Configuration Assessment rules that apply to your detected IaaS services.

The “Rules” table contains the following columns:

* **Type** - The name of the service or app for which the rule is tailored.
* **Name** - The formal name of the rule.
* **Passed** - The number of resources that are compliant with this rule.
* **Failed** - The number of resources that are not compliant with this rule.
* **Status** - The overall compliance for this rule.
[block:callout]
{
  "type": "info",
  "title": "TIP",
  "body": "In order for a rule to be considered as passing, 100% of your applicable resources must be compliant with the rule.  If even one of your resources fails the rule check, the rule itself is considered as failing."
}
[/block]
* **Severity** - Indicates the security impact for the rule if the resource is non-compliant.
* **Created** - Indicates when the rule was originally published.
* **Last Modified** - Indicates when the rule was last changed.
* **Actions** - This column contains an additional function if the rule is in the “Fail” state. Click the **cancel** icon to [configure an exception](doc:cloud-configuration-assessment-interface-guide#section-how-to-configure-an-exception) for this rule.

You can also limit the displayed rules based on their status by clicking the **Passed Rules** and **Failed Rules** counters in the upper right corner of the table.

## Exceptions View

An “exception” in Cloud Configuration Assessment is a rule you have elected not to factor into your overall assessment results.  Whether or not you configure exceptions is ultimately up to you and what you feel is best for your organization.

Click the **Exceptions** tab to view all of your configured rule exceptions, including the scope of the affected resources for each.
[block:callout]
{
  "type": "info",
  "title": "TIP",
  "body": "See the [Rule Exceptions](doc:cloud-configuration-assessment-interface-guide#section-rule-exceptions) section of this article for exception configuration instructions."
}
[/block]
# Filter Capabilities

To help you consume assessment data in a context that is meaningful to you, the **Findings** tab contains highly customizable filtering capabilities based on a variety of criteria.  Since your findings can number in the tens of thousands relative to the size of your organization, learning to effectively filter your results is crucial.

For a first lesson on creating meaningful filters, see the [Practical Filtering Exercise](doc:cloud-configuration-assessment-interface-guide#section-practical-filtering-exercise) subsection of this article.

## Filter Application Methods

You can apply one or more filters in the following ways based on your preference:

* [By Category Checkbox](doc:cloud-configuration-assessment-interface-guide#section-by-category-checkbox)
* [By Table Cell](doc:cloud-configuration-assessment-interface-guide#section-by-table-cell)

### By Category Checkbox

The “Filter Results” panel on the left side of the screen contains a series of accordion-style menus that correspond to the data shown in the findings table.  Click any accordion to expand its contents.  In an effort to keep these objects manageable, note that only one accordion can be open at a time.

Each accordion contains a series of clickable checkboxes for each detected value of that category, along with a number in parentheses indicating how many findings currently apply.  These checkboxes are automatically listed in descending order by the number of findings that apply to each.
[block:callout]
{
  "type": "warning",
  "title": "NOTE",
  "body": "The finding counters next to your filter checkboxes are designed to reflect the table records that are currently displayed.  As a result, checking any filter box changes the finding counters throughout your accordions when the filter successfully applies."
}
[/block]
Check any of these boxes to apply a filter to your findings table.  A loading icon next to the “Filter Results” panel title indicates that filter application is in progress.

### By Table Cell

You can also quickly apply inclusion and exclusion filters based on the value of an individual table cell.  Applicable table cells display two magnifying glass icons on mouseover: one with a **plus (+)** symbol, and one with a **minus (-)** symbol.  These functions do the following:

* Click the **plus (+)** magnifying glass to apply an **inclusion** filter based on this category value.  Your table will only display findings that match this value.
* Click the **minus (-)** magnifying glass to apply an **exclusion** filter based on this category value.  Your table will display all findings except those that match this value.

## Manage and Adjust Applied Filters

You can manage and adjust your applied filters in multiple ways:

* [Filter Pills](doc:cloud-configuration-assessment-interface-guide#section-filter-pills)
* [Clear and Reset](doc:cloud-configuration-assessment-interface-guide#section-clear-and-reset)

### Filter Pills

Whether you apply a filter using an accordion checkbox or directly from a table cell, your applied filters appear as “pills” just below the overall findings counter.  You can use these pills to adjust your applied filters when necessary.

Each pill displays a magnifying glass indicating whether it is an inclusion or exclusion filter, along with the category and value being filtered.  Hover your mouse over a pill to reveal additional options:

* Check (or uncheck) the box on the left side of the pill to toggle the filter on or off.
 * This is useful when you need to momentarily disable a filter you intend to use again without deleting it entirely.
* Click the **plus (+)** or **minus (-)** magnifying glasses to switch the state of the filter between inclusive and exclusive.
* Click the **X** icon to delete the filter entirely.

### Clear and Reset

In the “Filter Results” panel, click **Clear** on any accordion with active filters to remove them from your findings table.

To remove your applied filters and return the findings table to the default state, click **Reset** next to the “Filter Results” panel title.
[block:callout]
{
  "type": "info",
  "title": "What is the “default” state?",
  "body": "The default state of the findings table includes a “Status: Fail” filter so that only failed findings are shown initially."
}
[/block]
## Practical Filtering Exercise

The following exercise demonstrates a common use case of filtering in Cloud Configuration Assessment and will give you a solid foundation to build meaningful filters in the future.

### Identify Your Severe and Critical Resources

Consider the following example scenario:

An organization that subscribes to AWS has a large number of Elastic Compute Cloud (EC2) instances running in support of their business.  The security team considers these EC2 instances (particularly those in the US East region) a top priority and needs to quickly identify noncompliant resources.  In order to make the most effective use of their time, the security team has decided to limit their findings table to failing checks with a severity of “Severe” or higher.

**To construct a filter that meets this use case:**

1. On the **Findings** tab, click **Reset** next to “Filter Results” so you can start from the default state.
2. Next, you need to isolate all your EC2 instances.  Click the **Service** accordion to expand it and check the **EC2** box.  This applies an inclusion filter for all findings that apply to the EC2 service type.
3. Given this example scenario, you now need to further limit the findings table by severity.  Click the **Severity** accordion to expand it and check the **Severe** and **Critical** boxes.

The findings table should now contain only those records that match failed rule checks of “Severe” and “Critical” severities against detected EC2 instances.  Remember that this security team considers EC2 instances in the US East region their highest priority, so now it’s time to refine our table data further.
4. Click the **Region** accordion to expand it and check the **US East** box of your choice.

As you continue to refine table data into more manageable sizes, you improve the quality of actionable information.  This security team will be better equipped to address this subset of noncompliant resources based on their priorities as opposed to sifting through tens of thousands of findings in order to decide what to fix.

# How to Read Assessment Results

You can read your assessment results in several ways depending on which avenue of approach you want to use.  The following approach methods group assessment results based on individual [rules](doc:cloud-configuration-assessment-interface-guide#section-by-rule), [resources](doc:cloud-configuration-assessment-interface-guide#section-by-resource), and [findings](doc:cloud-configuration-assessment-interface-guide#section-by-finding-filter).

## By Rule

**To read assessment results based on individual rules:**

1. In your Cloud Configuration Assessment interface, click the **Rules** tab.
2. Browse to the desired rule and click the corresponding link in the “Name” column. The rule detail page displays.

The table view defaults to any and all applicable resources that have failed this particular rule check.

3. If desired, you can switch to see only passing resources by clicking the **Passed Resources** counter in the upper right corner of the rule detail page.
4. To view both passing and failing resources together, click the **rule name** link in the upper left of the table view.

### Rule Description

Rule detail pages include a written description of the rule just above the resource table.  These descriptions explain the justification for the rule and provide additional details when necessary.

### Rule Summary Panel

Rule detail pages also contain a collapsable “Summary” panel located on the left side of the page.  This panel tells you more about the service for which the rule applies and its original publishing date.

Browse the items listed under the “Links” section of this panel to reference available support material for this particular rule.

## By Resource

**To read assessment results based on individual resources:**

1. In your Cloud Configuration Assessment interface, click the **Resources** tab.
2. In the “Services” table, browse to the service category that you want to examine.  Click one of the links in the “Details” column to bring up a list of applicable resources.
[block:callout]
{
  "type": "info",
  "title": "TIP",
  "body": "The formatting of the resulting resource table depends on the category of the service you selected.  Some services have additional columns with information relevant to that service."
}
[/block]
3. Click the link of any resource to open it. The resource detail view displays.

The table view defaults to any and all applicable rule checks that have failed this particular resource.

4. If desired, you can switch to see only passing rules by clicking the **Passed Rules** counter in the upper right corner of the resource detail page.
5. To view both passing and failing rules together, click the **Findings** counter in the upper left of the table view.
6. If you have configured any rule exceptions, click the **Excepted Rules** counter to view them.
[block:callout]
{
  "type": "warning",
  "title": "NOTE",
  "body": "As you will learn in the [Rule Exceptions](doc:cloud-configuration-assessment-interface-guide#section-rule-exceptions) section, you can tailor a rule exception to be global, finding specific, or custom scope specific.  For this reason, do not assume that the exceptions shown for a specific resource are also excepted across the rest of your Cloud Configuration Assessment environment."
}
[/block]
### Resource Summary Panel

Like their rule detail counterparts, resource detail pages also contain a collapsable “Summary” panel located on the left side of the page.  Check this panel for information and attributes specific to the service type of the resource.

## By Finding Filter

You can also navigate to both rule and resource detail pages by [filtering your findings table](doc:cloud-configuration-assessment-interface-guide#section-filter-capabilities).  To review this method, check out the [practical filtering exercise](doc:cloud-configuration-assessment-interface-guide#section-practical-filtering-exercise) for a quick lesson.

# Rule Exceptions

An “exception” in Cloud Configuration Assessment is a designation that you apply to a rule in the “Fail” state to prevent affected findings from counting against your assessment results.
[block:callout]
{
  "type": "info",
  "title": "TIP - Exceptions have an independent state",
  "body": "Findings affected by exceptions are not treated as either passing or failing.  Rather, they assume a separate status that is independent of passing and failing metrics."
}
[/block]
The reasons for configuring a rule exception can vary widely, but determining what rules should and should not apply to your environment is ultimately at your discretion.

## Exception Characteristics

Exceptions in Cloud Configuration Assessment have the following characteristics:

* You can only configure exceptions for rules with at least one finding in the “Fail” state.
* Exceptions can only apply to a specific finding, the entire rule, or a custom scope of findings.
* After you configure an exception, affected findings assume a status of “Excepted” and are indicated by a white dot.
 * The “Excepted” status is considered neither passing nor failing and is tracked independently of your assessment results.
* If desired, you can specify an expiration date for the exception.
* For documentation purposes, you must select a reason for an exception and provide a supplemental comment for justification.

## How to Configure an Exception

You can configure exceptions in several ways:

* [Except an Individual Finding](doc:cloud-configuration-assessment-interface-guide#section-except-an-individual-finding)
* [Except an Entire Rule](doc:cloud-configuration-assessment-interface-guide#section-except-an-entire-rule)
* [Except a Custom Scope of Findings](doc:cloud-configuration-assessment-interface-guide#section-except-a-custom-scope-of-findings)

### Except an Individual Finding

**To configure an exception for an individual finding:**

1. In the **Findings** view, browse to the table row of your desired finding that has a “Fail” status.
2. Hover your mouse cursor over the “Actions” column of this table row.  Click the **cancel** icon that appears. The “Create Exception” window displays. 
3. The **Exclude this finding only** radio button will already be selected.
4. If desired, set an expiration time.
5. Select a reason for the exception from the dropdown list.
6. Provide justification for the exception in the “Comment” field.
7. Click **Submit** when finished.

### Except an Entire Rule

**To configure an exception for an entire rule:**

1. In the **Rules** view, browse to the table row of your desired rule that has a “Fail” status.
2. Hover your mouse cursor over the “Actions” column of this table row.  Click the **cancel** icon that appears. The “Create Exception” window displays.
3. The **Exclude this Rule** radio button will already be selected.
4. If desired, set an expiration time.
5. Select a reason for the exception from the dropdown list.
6. Provide justification for the exception in the “Comment” field.
7. Examine the figures under “Potential Exception Impact” to verify how many findings, regions, and accounts will be affected by this exception.
8. Click **Submit** when finished.

### Except a Custom Scope of Findings

**To configure an exception based on a custom scope of findings:**

1. In the **Findings** or **Rules** views, browse to the table row of your desired finding or rule that has a “Fail” status.
2. Hover your mouse cursor over the “Actions” column of this table row.  Click the **cancel** icon that appears. The “Create Exception” window displays.
3. Select the **Custom Scope** radio button.
4. You can specify a custom scope of findings based on the following categories:
 * Accounts
 * Regions
 * Tags
5. If desired, you can also specify individual resources in the “Resource ID” field.
6. If desired, set an expiration time.
7. Select a reason for the exception from the dropdown list.
8. Provide justification for the exception in the “Comment” field.
9. Examine the figures under “Potential Exception Impact” to verify how many findings, regions, and accounts will be affected by this exception.
10. Click **Submit** when finished.

## Manage Existing Exceptions

Click the **Exceptions** tab to view all your currently active rule exceptions.  If you want to delete an exception, hover your mouse cursor over the “Actions” column for the desired table row and click the **trash** icon.

# Connection Management

To manage your existing connections to your IaaS providers or to add new ones, click the **Add/Manage Connections** button in the upper right corner of the Cloud Configuration Assessment landing page.

After clicking **Add/Manage Connections**, InsightVM navigates to the **Management** tab on your left navigation menu.

**To manage existing connections:**

1. On the **Connections** tab, browse to the “Cloud Infrastructure” section.  Your current number of connections is indicated in parentheses.
2. Click **Cloud Infrastructure (#)** under “Connections” to view your current connection list.  Green check marks indicate that the connection is currently active.
3. Click **Edit** or **Delete** to manage any of these connections as needed.

**To add a new connection:**

1. On the **Connections** tab, browse to the “Cloud Infrastructure” section.
2. Click **Add** next to the supported IaaS provider of your choice to open the connection setup drawer.

## Supported IaaS Provider Connection Guides

See the following pages for instructions on how to configure connections to supported IaaS providers:

* [Amazon Web Services](doc:aws-connect-to-cloud-configuration-assessment)