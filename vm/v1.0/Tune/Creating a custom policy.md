---
title: "Creating a custom policy"
excerpt: ""
---
[block:callout]
{
  "type": "warning",
  "body": "To edit policies you must have the Policy Editor license. Contact your account representative if you want to add this feature."
}
[/block]
You create a custom policy by editing copies of built-in configuration policies or other custom policies. A policy consists of rules that may be organized within groups or sub-groups. You edit a custom policy to fit the requirements of your environment by changing the values required for compliance.

You can create a custom policy and then periodically check the settings to improve scan results or adapt to changing organizational requirements.

For example, you need a different way to present vulnerability data to show compliance percentages to your auditors. You create a custom policy to track one vulnerability to measure the risks over time and show improvements. Or you show what percentage of computers are compliant for a specific vulnerability.

There are two policy types:
* Built-in policies are installed with the application (Policy Manager configuration policies based on USGCB, FDCC, or CIS). These policies are not editable.
Policy Manager is a license-enabled scanning feature that performs checks for compliance with United States Government Configuration Baseline (USGCB) policies, Center for Internet Security (CIS) benchmarks, and Federal Desktop Core Configuration (FDCC) policies.
* Custom policies are editable copies of built-in policies. You can make copies of a custom policy if you need custom policies with similar changes, such as policies for different locations.

You can determine which policies are editable (custom) on the _Policy Listing_ table on the _Policies_ page. The Source column displays which policies are built-in and custom. The **Copy**, **Edit** and **Delete** buttons display for only custom policies for users with Manage Policies permission.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/c15e8ac-s_policy_editor_source_column.jpg",
        "s_policy_editor_source_column.jpg",
        1278,
        678,
        "#f1f5f5"
      ],
      "caption": "Policy — viewing the policy source column"
    }
  ]
}
[/block]
##Editing policies during a scan

You can edit policies during a scan without affecting your results. While you modify policies, manual or scheduled scans that are in process or paused scans that are resumed use the policy configuration settings in effect when the scan initially launched. Changes saved to a custom policy are applied during the next scheduled scan or a subsequent manual scan.

If your session times out when you try to save a policy, reestablish a session and then save your changes to the policy.

##Editing a policy
[block:callout]
{
  "type": "warning",
  "body": "To edit policies, you need Manage Policies permissions. Contact your administrator about your user permissions."
}
[/block]
The following section demonstrates how to edit the different items in a custom policy. You can edit the following items:

* custom policy—customize name and description
* groups—customize name and description
* rules—customize name and description and modify the values for checks

To create an editable policy, complete these steps:
1. Click **Copy** next to a built-in or custom policy.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/02dfc6d-s_policy_editor_copy.jpg",
        "s_policy_editor_copy.jpg",
        1276,
        612,
        "#f3f6f6"
      ],
      "caption": "Policy — copying a built-in policy"
    }
  ]
}
[/block]
The application creates a copy of the policy.

2. You can modify the Name to identify which policies are customized for your organization. For example, add your organization name or abbreviation, such as _XYZ Org -USGCB 1.2.1.0 - Windows 7 Firewall_.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/35e72a7-s_policy_editor_copy_result.jpg",
        "s_policy_editor_copy_result.jpg",
        1282,
        641,
        "#e6edee"
      ],
      "caption": "Policy — creating a custom policy"
    }
  ]
}
[/block]
3. (Optional) You can modify the _Description_ to explain what settings are applied in the custom policy using this policy.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/8743733-s_policy_editor_edit_policy_title.jpg",
        "s_policy_editor_edit_policy_title.jpg",
        547,
        253,
        "#e8eced"
      ],
      "caption": "Policy Editor — editing custom policy name and description"
    }
  ]
}
[/block]
4. Click **Save**.

##Viewing policy hierarchy

The _Policy Configuration_ panel displays the groups and rules in item order for the selected policy. By opening the groups, you drill down to an individual group or rule in a policy.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/8203c10-s_policy_editor_view_hierarchy.jpg",
        "s_policy_editor_view_hierarchy.jpg",
        1390,
        564,
        "#e9eeed"
      ],
      "caption": "Policy — viewing the policy hierarchy"
    }
  ]
}
[/block]
To view policy hierarchy for password rules, complete these steps:

1. Click **View** on the _Policy Listing_ table to display the policy configuration.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/f741ed6-s_policy_editor_click_view.jpg",
        "s_policy_editor_click_view.jpg",
        1395,
        496,
        "#f4f6f7"
      ],
      "caption": "Policy — clicking **View** to display the policy"
    }
  ]
}
[/block]
2. Click the icon to expand groups or rules to display details on the _Policy Configuration_ panel.
Use the policy _Find_ box to locate a specific rule. See [Using policy find](doc:creating-a-custom-policy#section-using-policy-find).
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/3b28ec7-s_policy_editor_view_hierarchy.jpg",
        "s_policy_editor_view_hierarchy.jpg",
        1390,
        564,
        "#e9eeed"
      ],
      "caption": "Policy — viewing the policy hierarchy"
    }
  ]
}
[/block]
3. Select an item (rule or group) in the policy tree (hierarchy) to display the detail in the right panel.
For example, your organization has specific requirements for password compliance. Select the Password Complexity rule to view the checks used during a scan to verify password compliance. If your organization policy does not enforce strong passwords then you can change the value to Disabled.

##Using policy find

Use the policy find to quickly locate the policy item that you want to modify.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/8fd9fa0-S_Policy_Search.jpg",
        "S_Policy_Search.jpg",
        389,
        208,
        "#e6e2da"
      ],
      "caption": "Policy — typing search criteria"
    }
  ]
}
[/block]
For example, type IPv6 to locate all policy items with that criteria. Click the **Up** ![Alt](https://files.readme.io/719f681-i_Up.jpg) and **Down** ![Alt](https://files.readme.io/d8216a2-i_Down.jpg) arrows to display the next or previous instance of IPv6 found by the policy find.

To find an item in a policy, complete these steps:

1. Type a word or phrase in the policy _Find_ box.
For example, type password.
As you type, the application searches then highlights all matches in the policy hierarchy.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/4e33d83-s_policy_editor_search_results.jpg",
        "s_policy_editor_search_results.jpg",
        1016,
        410,
        "#ecebe5"
      ],
      "caption": "Policy — browsing find results"
    }
  ]
}
[/block]
2. Click the **Up** ![Alt](https://files.readme.io/719f681-i_Up.jpg) and **Down** ![Alt](https://files.readme.io/d8216a2-i_Down.jpg) arrows to move to the next or previous items that match the find criteria.
3. (Optional) Refine your criteria if you receive too many results. For example, replace password with password age.
4. To clear the find results, click **Clear** ![Alt](https://files.readme.io/8bab1ba-i_Clear.jpg).

##Editing policy groups

You modify the group _Name and Description_ to change the description of items that you customized. The policy find uses this text to locate items in the policy hierarchy. See [Using policy find](doc:creating-a-custom-policy#section-using-policy-find).
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/dfe3316-s_policy_editor_edit_metadata.jpg",
        "s_policy_editor_edit_metadata.jpg",
        513,
        208,
        "#e9edec"
      ],
      "caption": "Policy — editing group name or description"
    }
  ]
}
[/block]
You select a group in the policy hierarchy to display the details. You can modify this text to identify which groups contain modified (custom) rules and add a description of what type of changes.

##Editing policy rules

You can modify policy rules to get different scan results. You select a rule in the Policy Configuration hierarchy to see the list of editable checks and values related to that rule.

To edit a rule value, complete these steps:

1. Select a rule in the policy hierarchy.
The rule details display.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/2812a2c-s_policy_editor_edit_values.jpg",
        "s_policy_editor_edit_values.jpg",
        1206,
        547,
        "#edeee8"
      ],
      "caption": "Policy — selecting a rule"
    }
  ]
}
[/block]
(Optional) Customize the _Name_ and _Description_ for your organization. Text in the _Name_ is used by policy find. See [Using policy find](doc:creating-a-custom-policy#section-using-policy-find).
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/0f65914-s_policy_editor_edit_rule_metadata.jpg",
        "s_policy_editor_edit_rule_metadata.jpg",
        513,
        208,
        "#e9edec"
      ],
      "caption": "Policy — modifying rule values"
    }
  ]
}
[/block]
2. Modify the checks for the rule using the fields displayed.
Refer to the guidelines about what value to apply to get the correct result.
For example, disable the Use FIPS compliant algorithms for encryption, hashing and signing rule by typing ‘0’ in the text box.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/0479201-s_policy_editor_edit_checks3.jpg",
        "s_policy_editor_edit_checks3.jpg",
        510,
        136,
        "#e7ebf0"
      ],
      "caption": "Policy — disabling a rule"
    }
  ]
}
[/block]
For example, change the Behavior of the elevation prompt for administrators in Admin Approval Mode check by typing a value for the total seconds. The guidelines list the options for each value.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/73ddbe2-s_policy_editor_edit_checks5.jpg",
        "s_policy_editor_edit_checks5.jpg",
        512,
        209,
        "#edf1f1"
      ],
      "caption": "Policy — entering the value for a check option."
    }
  ]
}
[/block]
3. Repeat these steps to edit other rules in the policy.
4. Click **Save**.

##Enabling or disabling policy rules
[block:callout]
{
  "type": "warning",
  "body": "To enable or disable policy rules, you need Manage Policies permissions. Contact your administrator about your user permissions."
}
[/block]
You can enable or disable a group of rules or specific rules within a custom policy.

To enable or disable policy rules, complete these steps:
1. Select a policy in the hierarchy.
2. Click the **Edit** icon.
The **Policy Configuration** page displays. Green toggles indicate enabled rules and gray toggles indicate disabled rules.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/ead0199-enable_disable_rules.PNG",
        "enable_disable_rules.PNG",
        1496,
        624,
        "#e3ebe9"
      ],
      "caption": "Policy — enabling or disabling rules"
    }
  ]
}
[/block]
3. To disable rules, click on the associated green toggle; to enable rules, click on the associated gray toggle.
4. Click **Save**.
Changes become effective in the next scan.
[block:callout]
{
  "type": "warning",
  "body": "At least one rule must be enabled to save a policy."
}
[/block]
###Notes about enabling or disabling rules:
* Enabling or disabling rules will trigger compliance score recalculations.
* Disabled rules are not run as part of the policy scan and may result in a deletion of scan results.
* Overrides on disabled rules are inactive until the rule is enabled again. See [Working with Policy Manager results](doc:working-with-policy-manager-results) for information about overrides.
* Disabled rules are only visible on the **Policy Configuration** page.

##Deleting a policy
[block:callout]
{
  "type": "warning",
  "body": "To delete policies, you need Manage Policies permissions. Contact your administrator about your user permissions."
}
[/block]
You can remove custom policies that you no longer use. When you delete a policy, all scan data related to the policy is removed. The policy must be removed from scan templates and report configurations before deleting.

Click **Delete** for the custom policy that you want to remove.

If you try to delete a policy while running a scan, then a warning message displays indicating that the policy can not be deleted.

##Adding Custom Policies in Scan Templates
[block:callout]
{
  "type": "info",
  "body": "To perform policy checks in scans, make sure that your Scan Engines are updated to the August 8, 2012 release."
}
[/block]
You add custom policies to the scan templates to apply your modifications across your sites. The _Policy Manager_ list contains the custom policies.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/7d24351-s_policy_editor_enable_custom_policy.jpg",
        "s_policy_editor_enable_custom_policy.jpg",
        1264,
        871,
        "#202939"
      ],
      "caption": "Policy — enabling a custom policy in the scan template"
    }
  ]
}
[/block]
Click _Custom Policies_ to display the custom policies. Select the custom policies to add.