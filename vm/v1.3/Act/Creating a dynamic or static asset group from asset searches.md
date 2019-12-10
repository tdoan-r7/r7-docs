---
title: "Creating a dynamic or static asset group from asset searches"
excerpt: ""
---
After you configure asset search filters as described in the preceding section, you can create an asset group based on the search results. Using the assets search is the only way to create a dynamic asset group. It is one of two ways to create a static asset group and is more ideal for environments with large numbers of assets. For a different approach, which involves manually selecting assets, see [Configuring a static asset group by manually selecting assets](doc:working-with-asset-groups#section-configuring-a-static-asset-group-by-manually-selecting-assets).
[block:callout]
{
  "type": "info",
  "body": "If you have permission to create asset groups, you can save asset search results as an asset group."
}
[/block]
1. After you configure asset search filters, click **Search**.
A table of assets that meet the filter criteria appears.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/c5ed6ad-s_nx_filtered_asset_search_results.jpg",
        "s_nx_filtered_asset_search_results.jpg",
        1433,
        384,
        "#f1f3f2"
      ],
      "caption": "Asset search results"
    }
  ]
}
[/block]
(Optional) Click the **Export to CSV** link at the bottom of the table to export the results to a comma-separated values (CSV) file that you can view and manipulate in a spreadsheet program.
[block:callout]
{
  "type": "warning",
  "body": "Only Global Administrators or users with the Manage Group Assets permission can create asset groups, so only these users can save Asset Filter search results."
}
[/block]
2. Click **Create Asset Group**.
Controls for creating an asset group appear.
3. Select either the **Dynamic** or **Static** option, depending on what kind of asset group you want to create. See [Comparing dynamic and static asset groups](doc:working-with-asset-groups#section-comparing-dynamic-and-static-asset-groups).
If you create a dynamic asset group, the asset list is subject to change with every scan. See [Using dynamic asset groups](doc:working-with-asset-groups#section-using-dynamic-asset-groups).
4. Enter a unique asset group name and description.
You must give users access to an asset group for them to be able view assets or perform asset-related operations, such as reporting, with assets in that group.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/516fe71-s_nx_creating_asset_group_from_filtered_search.jpg",
        "s_nx_creating_asset_group_from_filtered_search.jpg",
        1413,
        734,
        "#dee2e6"
      ],
      "caption": "Creating a new dynamic asset group"
    }
  ]
}
[/block]

[block:callout]
{
  "type": "warning",
  "body": "You must be a Global Administrator or have Manage Asset Group Access permission to add users to an asset group."
}
[/block]
5. Click **Add Users**. 
The _Add Users_ dialog box appears.
6. Select the check box for every user account that you want to add to the access list or select the check box in the top row to add all users.

##Changing asset membership in a dynamic asset group

You can change search criteria for membership in a dynamic asset group at any time.

To change criteria for a dynamic asset group:

1. Go to the _Assets :: Asset Groups_ page by one of the following routes:
Click the **Administration** icon to go to the _Administration_ page, and then click the **manage** link below _Groups_.

OR

Click the **Assets** icon to go to the _Assets_ page, and then click the blue number above _Asset Groups_.

2. Click **Edit** to find a dynamic asset group that you want to modify.
OR
Click the link for the name of the desired asset group.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/585760b-s_nx_edit_dynamic_asset_group.jpg",
        "s_nx_edit_dynamic_asset_group.jpg",
        1451,
        164,
        "#e9f2f5"
      ],
      "caption": "Starting to edit a dynamic asset group"
    }
  ]
}
[/block]
The console displays the page for that group.

3. Click **Edit Asset Group** or click **View Asset Filter** to review a summary of filter criteria.
Any of these approaches causes the application to display the **Filtered asset search** panel with the filters set for the most recent asset search.
4. Change the filters according to your preferences, and run a search. See [Configuring asset search filters](doc:performing-filtered-asset-searches#section-configuring-asset-search-filters) .
5. Click **Save**.