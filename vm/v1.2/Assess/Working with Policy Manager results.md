---
title: "Working with Policy Manager results"
excerpt: ""
---
If you work for a U.S. government agency, a vendor that transacts business with the government, or a company with strict configuration security policies, you may be running scans to verify that your assets comply with the following security standards:

* United States Government Configuration Baseline (USGCB)
* Center for Internet Security (CIS)
* Federal Desktop Core Configuration (FDCC)

After running Policy Manager scans, you can view the following information:

* The overall rate of compliance for assets in your environment.
* Asset compliance on a per-policy and per-rule basis.
* Methods for exporting policy scan data to CSV.

# Policy Manager topics

* [Distinguishing between Policy Manager and standard policies](doc:working-with-policy-manager-results#section-distinguishing-between-policy-manager-and-standard-policies)
* [Getting an overview of Policy Manager results](doc:working-with-policy-manager-results#section-getting-an-overview-of-policy-manager-results)
* [Viewing policy details](doc:working-with-policy-manager-results#section-viewing-policy-details)
* [Searching within a policy](doc:working-with-policy-manager-results#section-searching-within-a-policy)
* [CSV exports](doc:working-with-policy-manager-results#section-csv-exports)

# Distinguishing between Policy Manager and standard policies
[block:callout]
{
  "type": "warning",
  "title": "NOTE",
  "body": "You can only view policy test results for assets to which you have access. This is true for Policy Manager and standard policies."
}
[/block]
The Policy Manager is a license-enabled feature that includes the following policy checks:

* USGCB 2.0 policies (only available with a license that enables USGCB scanning)
* USGCB 1.0 policies (only available with a license that enables USGCB scanning)
* Center for Internet Security (CIS) benchmarks (only available with a license that enables CIS scanning)
* FDCC policies (only available with a license that enables FDCC scanning)
* Custom policies that are based on USGCB or FDCC policies or CIS benchmarks (only available with a license that enables custom policy scanning)

Standard policies are available with all licenses and include the following:

* Oracle policy
* Lotus Domino policy
* Windows Group policy
* AS/400 policy
* CIFS/SMB Account policy

# Getting an overview of Policy Manager results

Click the **Policies** tab on the Security Console menu.  The “Policies” page contains a table of policies based on your level of access, along with the following metrics:

* Total policy count (clickable tab)
* Scanned policy count (clickable tab)
* Number of policies with increased or decreased compliance
* Overall compliance percentage
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/7a1b7cf-policy_landing_page.png",
        "policy_landing_page.png",
        1904,
        983,
        "#c5c8cc"
      ]
    }
  ]
}
[/block]

[block:callout]
{
  "type": "info",
  "title": "TIP",
  "body": "Depending on your level of access, the total policy count view may be too long to browse comfortably.  Click the **Scanned Policies** tab to filter out rows with no scan data."
}
[/block]
The “Policies” table has the following columns:

* Policy Name
* Category
* Source
* Assets Passed
* Assets Failed
* Rule Compliance (percentage)
* Compliance Trend (percentage)
[block:callout]
{
  "type": "warning",
  "title": "Policy compliance depends on Rule compliance",
  "body": "Each policy consists of specific rules, and each asset is tested against those rules.  An asset must pass **all** rule checks to be considered compliant to that policy."
}
[/block]
## Viewing scanned assets

You can toggle the “Policies” page between individual policy data and asset data from the following dropdown:
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/d669d23-policy_asset_view_toggle.png",
        "policy_asset_view_toggle.png",
        601,
        449,
        "#8f979e"
      ]
    }
  ]
}
[/block]
The “Scanned Assets” table contains similar information and functionality to the “Policies” table, but from the viewpoint of individual assets.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/fe8b5dd-scanned_asset_view.png",
        "scanned_asset_view.png",
        1904,
        983,
        "#c9cdcf"
      ]
    }
  ]
}
[/block]
# Viewing policy details

You can view policy details in two ways:

* Click any “Policy Name” link to open the detail page for that policy.  The screen will show a “Policy Breakdown” table and a “Summary Information” window.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/ec9c372-Policy_details.png",
        "Policy_details.png",
        1903,
        983,
        "#c7c6c8"
      ]
    }
  ]
}
[/block]
* Alternatively, click anywhere on a policy row to open the “Summary Information” drawer.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/b393c6d-Policy_drawer.png",
        "Policy_drawer.png",
        1903,
        982,
        "#c3c6c9"
      ]
    }
  ]
}
[/block]

[block:callout]
{
  "type": "info",
  "title": "TIP",
  "body": "Policy Manager check results are also viewable from asset detail pages.  See [Viewing the details about an asset](doc:locating-assets#section-viewing-the-details-about-an-asset) for more information."
}
[/block]
## Policy Breakdown
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/05c2e10-policy_groups.png",
        "policy_groups.png",
        1903,
        982,
        "#c7cacd"
      ]
    }
  ]
}
[/block]
While both interfaces feature lists of individual policy rules and scanned assets, the “Policy Breakdown” table provides this information at the most granular level.
[block:callout]
{
  "type": "info",
  "title": "TIP",
  "body": "The \"Summary Information\" window displays different tabs depending on the type of row you select in the \"Policy Breakdown\" table."
}
[/block]
### Policy Groups

Rules within a policy are often categorized by type for organizational and export purposes into _Policy Groups_.  Expand any of these to show their individual rules.  When a policy group is selected, the “Summary Information” window contains tabs for its policy rules and scanned assets.
[block:callout]
{
  "type": "info",
  "title": "TIP",
  "body": "Some policies contain multi-layered groups.  Keep this in mind when selecting policy groups for export."
}
[/block]
### Policy Rules

All policies contain individual rules.  If you select a policy rule, the “Summary Information” window will feature the following tabs:

* **Rationale** - This tab contains a brief summary on why the rule exists and what type of vulnerability it can proactively guard against.
* **Remediation** - When data is available, this tab lists remediation steps to ensure compliance with the rule.
* **Scanned Assets** - This tab shows the rule’s scanned assets, the operating system of each asset, and whether the asset passed or failed.
* **Policy Controls** - When applicable, this tab lists policy controls for the selected rule.
[block:callout]
{
  "type": "warning",
  "title": "NOTE",
  "body": "If you inspect a policy rule via the “Scanned Assets” dropdown, the **Proof** tab will replace the **Scanned Assets** tab described previously in the “Summary Information” window.\n\nWhen an asset passes a rule check, the **Proof** tab details the reason for the pass."
}
[/block]
## “Unscored” and “not applicable” policy rules

Not all policy rules will factor into your compliance score.  See the following sections for details on how the Security Console handles these rules.

### Unscored rules

There may be rules within a policy that are considered “unscored”.  While these rules are still counted towards your overall rule total, their outcome will not be factored into your compliance percentage.
[block:callout]
{
  "type": "info",
  "title": "TIP",
  "body": "Unscored rules are denoted with an asterisk \\(\\*\\) appended to the rule title."
}
[/block]
### Not applicable rules

Not all policy rules will apply to your scanned assets, particularly if the rule only exists for a specific operating system that your target asset does not use.  By default, policy scan results will only show the number of applicable assets for the rule in question.

However, rules that are deemed “not applicable” will count as passing and be included in your compliance score if the following conditions are met:

* There must be at least one applicable rule in the same policy
* The applicable rule(s) must have a score of “Pass” or “Fail”
[block:callout]
{
  "type": "warning",
  "title": "NOTE",
  "body": "Policies that do not contain any applicable rules are not factored into your rule count or compliance score at all."
}
[/block]
You can view all assets that were scanned, regardless of applicability, from the **Scanned Assets** tab of the “Summary Information” drawer:

1. On the “Policies” screen, click the **Scanned Policies** tab.
2. Click the table row of the desired policy to open the “Summary Information”” drawer.
 * Alternatively, navigate to the “Policy Breakdown” table by clicking on the policy name link.
3. In the “Summary Information” drawer, click the **Scanned Assets** tab.
 * The **Scanned Assets** tab is also available when individual policy groups and rules are selected.
4. Adjust the filter from **Applicable assets only** to **All assets**.

# Searching within a policy

On the “Policies” table, check the box of **one** policy to enable the **View Policy** button.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/a35ca24-open_policy_button.png",
        "open_policy_button.png",
        703,
        424,
        "#c7cdd1"
      ]
    }
  ]
}
[/block]
Similarly to the “Policy Breakdown” table, the “Policy Configuration” screen shows policy groups and rules in directory form.  Use the text field to match specific keywords to policy groups and rules.  Highlight individual groups and rules to show additional details on the right side of the screen.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/e79c416-policy_keyword_search.png",
        "policy_keyword_search.png",
        1723,
        855,
        "#f7f5f4"
      ]
    }
  ]
}
[/block]

[block:callout]
{
  "type": "warning",
  "title": "NOTE",
  "body": "The “Description” and “Check” parameter fields for built-in policies are locked by default.  See [Creating a custom policy](doc:creating-a-custom-policy) for more information."
}
[/block]
# CSV exports

The “Policies” page features widespread support for exporting data to CSV.  Use the **Export to CSV** button to export any rows you specify to a CSV file.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/cc247fb-csv_button.png",
        "csv_button.png",
        497,
        350,
        "#b3bbc0"
      ]
    }
  ]
}
[/block]

[block:callout]
{
  "type": "info",
  "title": "TIP",
  "body": "By default, the **Export to CSV** button will export all records if individual rows are not checked."
}
[/block]
## Export types

The following screens/tabs support CSV exports:

* Main “Policies” table
* “Scanned Policies” filtered table (via **Scanned Policies** tab)
* “Scanned Assets” table (via dropdown)
* **Scanned Assets** tab (via “Summary Information” window or drawer)
* “Policy Breakdown” table (via policy detail screen)