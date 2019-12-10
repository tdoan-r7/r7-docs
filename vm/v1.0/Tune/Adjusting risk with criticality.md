---
title: "Adjusting risk with criticality"
excerpt: ""
---
The Risk Score Adjustment setting allows you to customize your assets’ risk score calculations according to the [business context](doc:applying-realcontext-with-tags) of the asset. For example, if you have set the Very High criticality level for assets belonging to your organization’s senior executives, you can configure the risk score adjustment so that those assets will have higher risk scores than they would have otherwise. You can specify modifiers for your user-applied criticality levels that will affect the asset risk score calculations for assets with those levels set.

Note that you must enable Risk Score Adjustment for the criticality levels to be taken into account in calculating the risk score; it is not set by default.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/fc27816-s_nx_risk_score_adjustment_checkbox.jpg",
        "s_nx_risk_score_adjustment_checkbox.jpg",
        588,
        112,
        "#e2e2e0"
      ],
      "caption": "Risk Score Adjustment must be manually enabled"
    }
  ]
}
[/block]
To enable and configure Risk Score Adjustment:
1. On the Administration page, in Global and Console Settings, click the **Manage** link for global settings.
2. In the Global Settings page, select **Risk Score Adjustment**.
3. Select **Adjust asset risk scores based on criticality**.
4. Change any of the modifiers for the listed criticality levels, per the constraints listed below.

Constraints:
* Each modifier must be greater than 0.
* You can specify up to two decimal places. For example, frequently-used modifiers are values such as .75 or .25.
* The numbers must correspond proportionately to the criticality levels. For example, the modifier for the High criticality level must be less than or equal to modifier for the Very High criticality level, and greater than or equal to the modifier for the Medium criticality level. The numbers can be equal to each other: For example, they can all be set to 1.

The default values are:
* Very High: 2
* High: 1.5
* Medium: 1
* Low: 0.75
* Very Low: 0.5
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/46a6a3f-s_nx_risk_score_modifiers.jpg",
        "s_nx_risk_score_modifiers.jpg",
        888,
        310,
        "#e0dfdd"
      ],
      "caption": "Adjust the multipliers for the criticality levels"
    }
  ]
}
[/block]
##Interaction with risk strategy

The [Risk Strategy](doc:working-with-risk-strategies-to-analyze-threats) and Risk Score Adjustment are independent factors that both affect the risk score.

To calculate the risk score for an individual asset, InsightVMuses the algorithm corresponding to the selected risk strategy. If Risk Score Adjustment is set and the asset has a criticality tag applied, the application then multiplies the risk score determined by the risk strategy by the modifier specified for that criticality tag.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/2afb579-s_nx_context-driven_risk_score_asset.jpg",
        "s_nx_context-driven_risk_score_asset.jpg",
        1110,
        221,
        "#f8f9f9"
      ],
      "caption": "Both the original and context-driven risk scores are displayed for an individual asset"
    }
  ]
}
[/block]
The risk score for a site or asset group is based upon the scores for the assets in that site or group. The calculation used to determine the risk for the entire site or group depends on the risk strategy. Note that even though it is possible to apply criticality through an asset group, the criticality actually gets applied to each asset and the total risk score for the group is calculated based upon the individual asset risk scores.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/91a63cd-s_nx_context-driven_risk_score_asset_group.jpg",
        "s_nx_context-driven_risk_score_asset_group.jpg",
        1144,
        123,
        "#e7eced"
      ],
      "caption": "The risk score for a site or asset-group is based on the context-driven risk scores of the assets in it."
    }
  ]
}
[/block]
##Viewing risk scores

If Risk Score Adjustment is enabled, nearly every risk score you see in your InsightVMinstallation will be the context-driven risk score that takes into account the risk strategy and the risk score adjustment. The one exception is the Original risk score available on the page for a selected asset. The Original risk score takes into account the risk strategy but not the risk score adjustment. Note that the values displayed are rounded to the nearest whole number, but the calculations are performed on more specific values. Therefore, the context-driven risk score shown may not be the exact product of the displayed original risk score and the multiplier.

When you first apply a criticality tag to an asset, the context-driven risk score on the page for that asset should update very quickly. There will be a slight delay in recalculating the risk scores for any sites or asset groups that include that asset.