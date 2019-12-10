---
title: "Applying RealContext with tags"
excerpt: ""
---
When tracking assets in your organization, you may want to identify, group, and report on them according to how they impact your business.

For example, you have a server with sensitive financial data and a number of workstations in your accounting office located in Cleveland, Ohio. The accounting department recently added three new staff members. Their workstations have just come online and will require a number of security patches right away. You want to assign the security-related maintenance of these accounting assets to different IT administrators: A SQL and Linux expert is responsible for the server, and a Windows administrator handles the workstations. You want to make these administrators aware that these assets have high priority.

These assets are of significant importance to your organization. If they were attacked, your business operations could be disrupted or even halted. The loss or corruption of their data could be catastrophic.

The scan data distinguishes these assets by their IP addresses, vulnerability counts, risk scores, and installed operating systems and services. It does not isolate them according to the unique business conditions described in the preceding scenario.

Using a feature called _RealContext_, you can apply _tags_ to these assets to do just that. Your can tag all of these accounting assets with a _Cleveland_ location and a _Very High_ criticality level. You can tag your accounting server with a label, _Financials_, and assign it an owner named _Chris_, who is a Linux administrator with SQL expertise. You can assign your Windows workstations to a Windows administrator owner named _Brett_. And you can tag the new workstations with the label _First-quarter hires_. Then, you can create dynamic asset groups based on these tags and send reports on the tagged assets to Chris and Brett, so that they know that the workstation assets should be prioritized for remediation. For information on using tag-related search filters to create dynamic asset groups, see [Performing filtered asset searches](doc:performing-filtered-asset-searches).

You also can use tags as filters for report scope. See [Creating a basic report](doc:creating-a-basic-report).

##Types of tags

You can use several built-in tags:

* You can tag and track assets according to their geographic or physical _Locations_, such as data centers.
* You can associate assets with _Owners_, such as members of your IT or security team, who are in charge of administering them.
* You can apply levels of _Criticality_ to assets to indicate their importance to your business or the negative impact resulting from an attack on them. A criticality level can be _Very Low_, _Low_, _Medium_, _High_, or _Very High_. Additionally, you can apply numeric values to criticality levels and use the numbers as multipliers that impact risk score. For more information, see [Adjusting risk with criticality](doc:adjusting-risk-with-criticality)
.
You can also create custom tags that allow you to isolate and track assets according to any context that might be meaningful to you. For example, you could tag certain assets _PCI_, _Web site back-end_, or _consultant laptops_.

##Tagging assets, sites, and asset groups

You can tag an asset individually on the details page for that asset. You also can tag a site or an asset group, which would apply the tag to all member assets. The tagging workflow is identical, regardless of where you tag an asset:

1. If you are creating or editing a site: Go to the _General_ page of the _Site Configuration_ panel, and select **Add tags**.
If you are creating or editing a static asset group: Go to the _General_ page of the _Asset Group Configuration_ panel, and select **Add tags**.
If you are creating or editing a dynamic asset group: In the _Configuration_ panel for the asset group, select **Add tags**.
If you have just run a filtered asset search: To tag all of the search results, select **Add tags**, which appears above the search results table on the _Filtered Asset Search_ page.

The section for configuring tags expands.

2. Select a tag type.
3. If you select _Custom Tag_, _Location_, or _Owner_, type a new tag name to create a new tag. To add multiple names, type one name, press ENTER, type the next, press ENTER, and repeat as often as desired.
OR
To apply an previously created tag, start typing the name of the tag until the rest of the name fills in the text box.
If you are creating a new custom tag, select a color in which the tag name will appear. All built-in tags have preset colors.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/b681d36-s_nx_dag_add_custom_tags.jpg",
        "s_nx_dag_add_custom_tags.jpg",
        1443,
        458,
        "#dee2e5"
      ],
      "caption": "Creating a custom tag"
    }
  ]
}
[/block]
If you select Criticality, select a criticality level from the drop-down list.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/99a1f67-s_nx_dag_add_criticality_tag.jpg",
        "s_nx_dag_add_criticality_tag.jpg",
        615,
        187,
        "#dde6eb"
      ],
      "caption": "Applying a criticality level"
    }
  ]
}
[/block]
4. Click **Add**.
5. If you are creating or editing a site or asset group, click **Save** to save the configuration changes.

###Importing assets into a tag using CSV

To simplify the management of tags across a large number of assets, you can apply a tag to a set of assets using a CSV text file that contains a list of hostnames and/or IP addresses and ranges.

To import assets into tags using CSV:

1. Click the *Home* icon.
2. In the **Asset Tags** area, select an asset tag. The asset tag page appears.
3. In the **Assets** area, click **Add Assets From File**. The **Add Assets From File** window appears.
4. Click **Choose File**, and then select the appropriate text file. Each line in the file should contain only one hostname or IP address.
5. Select an option:


 * Click **Override Tag** if you want to replace all of the current assets. This function does not affect asset criteria. 
 * Click **Append to Tag** to add new assets to the current assets.

The selected tag is applied to all valid assets.

##Applying business context with dynamic asset filters

Another way to apply tags is by specifying criteria for which tags can be dynamically applied. This allows you to apply business context based on filters without having to create new sites or groups. It also allows you to add new criteria for which assets should have the tags as you think of them, rather than at the time you first tag assets. For example, you may have searched for all your assets meeting certain Payment Card Industry (PCI) criteria and applied the _High_ criticality level. Later, you decide you also want to filter for the Windows operating system. You can apply the additional filter on the page for the _High_ criticality level itself.

To apply business context with dynamic asset filters:

1. Click the name of any tag to go to the details page for that tag.
2. Click **Add Tag Criteria**.
3. Select the search filters. The available filters are the same as those available in the asset search filters. See [Performing filtered asset searches](doc:performing-filtered-asset-searches). There are some restrictions on which filters you can use with criticality tags. See [Filter restrictions for criticality tags](doc:applying-realcontext-with-tags#section-filter-restrictions-for-criticality-tags).
4. Select **Search**.
5. Select **Save**.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/0bd10b0-s_nx_add_tag_criteria.jpg",
        "s_nx_add_tag_criteria.jpg",
        288,
        430,
        "#dee3e5"
      ],
      "caption": "You can add criteria for when a tag will be dynamically applied"
    }
  ]
}
[/block]
To view existing business context for a tag:

* On the details page for that tag, select **View Tag Criteria**.

To edit, add new, or remove dynamic asset filters for a tag:
1. Click the name of any tag to go to the details page for that tag.
2. Click **Edit Tag Criteria**.
3. Edit or add the search filters. The available filters are the same as those available in the asset search filters. See [Performing filtered asset searches](doc:performing-filtered-asset-searches). There are some restrictions on which filters you can use with criticality tags. See [Filter restrictions for criticality tags](doc:applying-realcontext-with-tags#section-filter-restrictions-for-criticality-tags).
4. Select **Search**.
5. Select **Save**.

To remove all criteria for a tag:
* On the details page for that tag, select **Clear Tag Criteria**.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/9cd7071-s_nx_edit_asset_filter.jpg",
        "s_nx_edit_asset_filter.jpg",
        1428,
        448,
        "#dbe1e5"
      ],
      "caption": "You can take different actions to view or modify rules for tags"
    }
  ]
}
[/block]
##Filter restrictions for criticality tags

Certain filters are restricted for criticality tags, in order to prevent [circular references](doc:applying-realcontext-with-tags#section-avoiding-circular-references-when-tagging-asset-groups) . These restrictions apply to criticality tags applied through [tag criteria](doc::applying-realcontext-with-tags#section-tagging-assets-sites-and-asset-groups), and to those added through dynamic asset groups. See [Performing filtered asset searches](doc:performing-filtered-asset-searches).

The following filters cannot be used with criticality tags:
* Asset risk score
* User-added criticality level
* User-added custom tag
* User-added tag (location)
* User-added tag (owner)

##Removing and deleting tags

If a tag no longer accurately reflects the business context of an asset, you can remove it from that asset. To do so, click the **x** button next to the tag name. If the tag name is longer than one line, mouse over the ampersand below the name to expand it and then click the **x** button. Removing a tag is not the same as deleting it.

If you tag a site or an asset group, all of the member assets will "inherit" that tag. You cannot remove an inherited tag at the individual asset level. Instead, you will need to edit the site or asset group in which the tag was applied and remove it there.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/383d8b9-s_nx_dag_expand_delete_custom_tag.jpg",
        "s_nx_dag_expand_delete_custom_tag.jpg",
        409,
        193,
        "#f7f8f7"
      ],
      "caption": "Removing a custom tag."
    }
  ]
}
[/block]
If a tag no longer has any business relevance at all, you can delete it completely.
[block:callout]
{
  "type": "info",
  "body": "You cannot delete a criticality tag."
}
[/block]
To delete a tag, go to the _Tags_ page:

Click the name of any tag to go to the details page for that tag. Then click the **View All Tags** breadcrumb.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/1efc2b8-s_nx_tag_page_tags_highlighted.jpg",
        "s_nx_tag_page_tags_highlighted.jpg",
        1488,
        262,
        "#dae1e4"
      ],
      "caption": "Viewing the details page of a tag"
    }
  ]
}
[/block]
OR

Click the **Assets** icon, then click the number of tags listed for _Tagged Assets_, even if that number is zero.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/9dd5308-s_nx_home_tags.jpg",
        "s_nx_home_tags.jpg",
        330,
        86,
        "#dedfe0"
      ]
    }
  ]
}
[/block]
Go to the _Asset Tag Listing_ table of the _Tags_ page. Select the check box for any tag you want to delete. To select all displayed tags, select the check box in the top row. Then, click **Delete**.

**Tip:** If you want to see which assets are associated with the tag before deleting it, click the tag name to view its details page. This could be helpful in case you want to apply a different tag to those assets.

##Changing the criticality of an asset

Over time, the criticality of an asset may change. For example, a laptop may initially be used by a temporary worker and not contain sensitive data, which would indicate low criticality. That laptop may later be used by a senior executive and contain sensitive data, which would merit a higher criticality level.

Your options for changing an asset's criticality level depend on where the original criticality level was initially applied and where you are changing it:

* If you apply a criticality level to a site and then change the criticality of a member asset, you can only increase the criticality level. For example, if you apply a criticality level of _Medium_ to a site and then change the criticality level of an individual member asset, you can only change the level to _High_ or _Very High_.
* If you apply a criticality level to an asset group, and if any asset has had a criticality level applied elsewhere (in sites, other asset groups, or individually), the asset will retain the highest-applied criticality level. For example, an asset named *Server_1* belongs to a site named _Boston_ with a criticality level of _Medium_. A criticality level of _Very High_ is later applied to Server_1 individually. If you apply a _High_ criticality level to a new asset group that includes Server_1, it will retain the _Very High_ criticality level.
* If you apply a criticality level to an asset group, and if any asset has had a criticality level applied elsewhere (in sites, other asset groups, or individually), the asset will retain the highest-applied criticality level. For example, an asset named *Server_1* belongs to a site named _Boston_ with a criticality level of _Medium_. A criticality level of _Very High_ is later applied to Server_1 individually. If you apply a _High_ criticality level to a new asset group that includes Server_1, it will retain the _Very High_ criticality level.
* If you apply a criticality level to an individual asset, you can later change the criticality to any desired level.

##Creating tags without applying them

You can create tags without immediately applying them to assets. This could be helpful if, for example, you want to establish a convention for how tag names are written.

1. Click the **Assets** icon, then click the number of tags listed for _Tagged Assets_, even if that number is zero.
OR
Click the **Create** tab at the top of the page and then select _Tags_ from the drop-down list.
2. Click **Add tags** and add any tags as described in [Tagging assets, sites, and asset groups](doc:applying-realcontext-with-tags#section-tagging-assets-sites-and-asset-groups).

##Avoiding "circular references" when tagging asset groups

You may apply the same tag to an asset as well as an asset group that contains it. For example, you might want to create a group based on assets tagged with a certain location or owner. This may occasionally lead to a circular reference loop in which tags refer to themselves instead of the assets or groups to which they were originally applied. This could prevent you from getting useful context from the tags.

The following example shows how a circular reference can occur with with location and custom tags:

1. A first user tags a number of assets with the location _Cleveland_.
2. The user creates a dynamic asset group called _Midwest office_ with search results based on assets tagged _Cleveland_.
3. The user applies a custom tag named _Accounting_ to the _Midwest office_ asset group because all the assets in the group are used by the accounting team.
4. A second user, who is not aware of the _Midwest office_ dynamic asset group or the _Cleveland_ tag, creates a new dynamic asset group named _Financial_ with search results based on the _Accounting_ tag.
5. That user tags the _Financial_ group with _Cleveland_, expecting that all assets in the group will inherit the tag. But because the assets were tagged _Cleveland_ by the first user, the _Cleveland_ tag now refers to itself in a potentially infinite loop.

The following example shows how a circular reference can occur with criticality:

1. You create a dynamic asset group _Priorities_ for all assets that have an original risk score of less than 1,000. One of these assets is named *Server_1*.
2. You tag this group with a _Very High_ criticality level, so that every asset in the group inherits the tag.
3. Your Security Console has been configured to double the risk score of assets with a _Very High_ criticality level. See [Adjusting risk with criticality](doc:adjusting-risk-with-criticality).
4. *Server_1* has its risk score doubled, which causes it to no longer meet the filter criteria of _Priorities_. Therefore, it is removed from _Priorities_.
5. Since *Server_1* no longer inherits the _Very High_ criticality level applied to _Priorities_, it reverts to its original risk score, which is lower than 1,000.
6. *Server_1* now once again meets the criteria for membership in _Priorities_, so it once again inherits the _Very High_ criticality level applied to the asset group. This, again, causes its risk score to double, so that it no longer meets the criteria for membership in _Priorities_. This is a circular reference loop.

The best way to prevent circular references is to look at the Tags page to see what tags have been created. Then go to the details page for a tag that you are considering using and to see which assets, sites, and asset groups it is applied to. This is especially helpful if you have multiple Security Console users and high numbers of tags and asset groups. To access to the details page for a tag, simply click the tag name.