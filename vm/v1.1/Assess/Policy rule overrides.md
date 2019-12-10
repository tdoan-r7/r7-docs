---
title: "Policy rule overrides"
excerpt: ""
---
You can override the result of a policy rule if you deem it necessary.  Requirements are as follows:

* You can only configure overrides per individual rule.  Policy rule groups cannot be overridden.
* You must provide a reason for the override to exist.
* You must have the proper permissions.
[block:callout]
{
  "type": "info",
  "title": "TIP",
  "body": "The following report templates include information on the most recent override per policy rule check:\n\n* XCCDF Human Readable CSV Export\n* XCCDF Results XML Export\n\nSee [Working with report formats](doc:working-with-report-formats) for more information."
}
[/block]
# Permissions

Users must be granted special permissions to submit, review, and delete policy rule override requests.  View and configure these permissions from any user’s “User Configuration” screen:

1. On your Security Console menu, click the **Administration** tab.
2. In the “Users” window, click **manage** next to “user accounts”.
3. Click the icon under “Edit” for your desired user, or click the **New User** button.
4. On the “User Configuration” screen, click the **Roles** tab.
5. Browse to the “Vulnerability Exception and Policy Override Permissions” section.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/a61301d-administration_userconfiguration_roles_override.png",
        "administration_userconfiguration_roles_override.png",
        939,
        195,
        "#c7dce3"
      ]
    }
  ]
}
[/block]
Permissions will be enabled or disabled depending on the selected user role.  Define a custom role to manually add or remove permissions as you see fit.

# Create an override

Create policy rule overrides starting from both the “Policies” and “Scanned Assets” views:
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/7fde8d0-policy_asset_view_toggle.png",
        "policy_asset_view_toggle.png",
        601,
        449,
        "#8f979e"
      ]
    }
  ]
}
[/block]
## Override scope

The starting point of a policy rule override configuration will determine if the scope of the override is adjustable.

* Starting from the “Policies” view restricts override scope to “All assets”.
* Starting from the “Scanned Assets” view provides the following scope options:
 * All assets
 * This asset only
 * This asset until the next scan
[block:callout]
{
  "type": "info",
  "title": "TIP",
  "body": "Consider whether you will need override scope options before starting the configuration."
}
[/block]
## Select a policy rule

After opening a desired policy or scanned asset to its detail page, expand individual policy groups until a rule is selected.  The **Create Policy Override** button will activate.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/5d9f9e3-policies_policydetails_overridebutton.png",
        "policies_policydetails_overridebutton.png",
        631,
        529,
        "#d4d6d9"
      ]
    }
  ]
}
[/block]
Click the **Create Policy Override** button.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/f1605d1-policies_scannedassets_createpolicyoverride.png",
        "policies_scannedassets_createpolicyoverride.png",
        1192,
        1022,
        "#dfe3e7"
      ]
    }
  ]
}
[/block]
1. If necessary, select the scope for the override.
2. Specify how the override will change the result of the rule check.
3. Provide a detailed reason for the override to exist.
[block:callout]
{
  "type": "info",
  "title": "TIP",
  "body": "All overrides and their reasons are incorporated, along with the policy check results, into the documentation that the U.S. government reviews in the certification process."
}
[/block]
4. Submit the form when finished.  If you already have the necessary permissions, you can click the **Submit and Approve** button to enable the override without going through the review process.

# Managing override requests

You can review pending override requests from the “Configuration Policy Overrides” window.

1. On your Security Console menu, click the **Administration** tab.
2. In the “Exceptions and Overrides” window, click **Review**.
3. Browse to the “Configuration Policy Overrides” window.
4. Select any pending policy override(s) for review or deletion.
 * The “Review Policy Overrides” window contains options for approving and rejecting submitted overrides.  If desired, you can also specify an expiration date.

# Viewing override history

You can view policy override history by examining completed scans of assets.

1. In the “Sites” window of your Security Console **Home** tab, open the site responsible for scanning the asset(s) you want to review.
2. In the “Site Scan Summary” window, click the **View Scan History** button.
3. In the “Past Scans” window, open your desired scan.
4. In the “Completed Assets” window, browse to and open the asset you want to check.
5. In the “Policies” window, open a policy.
6. Open any desired policy rule.  The policy rule details page will show a history of overrides if any exist.