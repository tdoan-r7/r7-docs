---
title: "Advanced filter options"
excerpt: ""
---
Individual filter parameters can be viewed from the **Syntax Help / Query Dictionary** inside the expanded view of all dashboard cards.

To access this, add (or browse to) a dashboard card that you would like to query and click **Expand Card**.  Click the question mark icon located between the **Saved Query** dropdown and the filter field.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/f8b6991-Syntax_help_query_dictionary_icon.png",
        "Syntax_help_query_dictionary_icon.png",
        1600,
        821,
        "#3e4755"
      ]
    }
  ]
}
[/block]
The **Syntax Help / Query Dictionary** table will be shown.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/8d28c2f-Syntax_help_query_dictionary_table.png",
        "Syntax_help_query_dictionary_table.png",
        1600,
        821,
        "#3e4754"
      ]
    }
  ]
}
[/block]
## _Asset_ and _Vulnerability_ parameters

Query parameters are categorized as either **asset** based or **vulnerability** based.  The availability of certain parameters will depend on the type of card.

### Filtering asset cards

**Asset** based cards can only filter with parameters of the asset type.

### Filtering vulnerability cards

**Vulnerability** based cards have additional filtering functionality:

* Both asset and vulnerability parameter types are available.
* Both parameter types can be applied sequentially to form a double query.

When a filter of one parameter type is applied, you will be presented with the option of specifying a second filter of the remaining parameter type.  For example, the results of an asset based filter can be further refined by a vulnerability based filter, and vice versa.

You can apply a double query with the following steps:

1. Browse to any queryable vulnerability card and click **Expand Card \>**.
2. Specify an asset or vulnerability parameter filter in the query field, or select a saved query from the dropdown.
3. Click **Apply**.  The card will now show filtered data, and the **Add a filter** button will appear to the left of the query field.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/255478c-expanded_first_filter.png",
        "expanded_first_filter.png",
        1918,
        983,
        "#464d58"
      ]
    }
  ]
}
[/block]
4. Click **Add a filter**.  Query parameters of the unused filter type will now be available.
5. Specify your second filter and click **Apply**.  The card will now show data according to both filters.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/56a0e15-double_query.png",
        "double_query.png",
        1919,
        982,
        "#4b525c"
      ]
    }
  ]
}
[/block]
6. When finished, open the **Save** dropdown in the upper right corner of the screen.  You can elect to save the changes to the current card or make a copy.
7. If you have not yet named and saved your filters, do so now.  The filters’ visibility can be set to **Private** or **Public**.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/d7e770a-save_filters.png",
        "save_filters.png",
        692,
        357,
        "#59646e"
      ]
    }
  ]
}
[/block]
8. Click **OK** and **Close** the card.

Cards that have been saved with applied filters will continue to show adjusted data when collapsed to the dashboard view.  The filter symbol in the upper left corner of the collapsed card denotes that a filter is currently active.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/452fbc0-filtered_card_collapsed.png",
        "filtered_card_collapsed.png",
        404,
        528,
        "#54464e"
      ]
    }
  ]
}
[/block]
Applied filters that have been saved to the card will remain active until you remove them.

## Sorting by column

The query parameters can be sorted alphabetically according to their name, description, and type.  Click any of the column headers to toggle between ascending and descending order.

## Searching by parameter name

The search field in the upper right corner can take string values and return any matching parameter names.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/9da1d9c-Parameter_search.png",
        "Parameter_search.png",
        1919,
        615,
        "#3b4450"
      ]
    }
  ]
}
[/block]

[block:callout]
{
  "type": "info",
  "title": "NOTE",
  "body": "The search function only matches strings to the parameter **name**."
}
[/block]
## Managing saved filters

Your saved card filters can be viewed and sorted from the **Management** page.

Select the **Filters** tab below “Settings” to see a full list of all saved card filters.  Rows can be sorted by the following columns:

* Filter Name
* Filter Text
* Created On
* Modified On
* Owner

Enter keywords in the search field to narrow the filter list by Filter Name.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/ec421a2-manage_filters.png",
        "manage_filters.png",
        1917,
        983,
        "#3e4853"
      ]
    }
  ]
}
[/block]
Filters can be selected and deleted as necessary as long as you are the owner.
[block:callout]
{
  "type": "warning",
  "title": "NOTE",
  "body": "Deleting filters that are currently in use by cards will make the data unpresentable.  Cards that have been affected by filter deletion must be **reset** or **deleted entirely**."
}
[/block]
# Filter operators

See the [operators table](doc:query-filter-guide#section-operators) for a list of available operators and their corresponding descriptions.