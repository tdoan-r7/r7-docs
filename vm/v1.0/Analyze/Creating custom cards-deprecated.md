---
title: "Creating custom cards-deprecated"
excerpt: ""
---
Custom cards let you display analytics that meet your needs. You accomplish this by creating filters using a simple query language. Once a filter is created, you can save it to use it as needed and to use it as a starting point to create other related filters.

##Adding cards

Perform the following steps to add cards to the dashboard.

1. Click the **+ ADD CARD** button.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/9871d27-add-card-button.PNG",
        "add-card-button.PNG",
        94,
        30,
        "#0494d4"
      ],
      "caption": "Add card button"
    }
  ]
}
[/block]
2. The **Add a Card** screen displays.
3. The left panel displays card categories to make it easier to find the cards that you want to display. The default displays all cards.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/0dabc0d-cards-categories.PNG",
        "cards-categories.PNG",
        240,
        193,
        "#3c4552"
      ],
      "caption": "Card categories"
    }
  ]
}
[/block]
4. Click the checkbox to the left of its name to select that card. Repeat to add as many cards as necessary. 
[block:callout]
{
  "type": "warning",
  "body": "You need to click the ADD button before switching categories. Card selections are not saved when you choose another card category."
}
[/block]
5. The number of selected cards displays in the top right-hand corner.
6. Click the **ADD** button to add the selected cards.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/6ce5bd5-add-card-screen-annotated.PNG",
        "add-card-screen-annotated.PNG",
        566,
        375,
        "#3c4553"
      ],
      "caption": "Add a card screen - annotated"
    }
  ]
}
[/block]
7. The cards display at the top of the dashboard.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/8b9dd5c-added-cards.PNG",
        "added-cards.PNG",
        567,
        309,
        "#434c5a"
      ],
      "caption": "Cards added to dashboard"
    }
  ]
}
[/block]
##Duplicating a card

A card may display analytics that are similar to what you need. Instead of creating the card from scratch, you can duplicate the card and then edit it as needed.

Perform the following steps to duplicate a card.
1. Hover your cursor over the title of the card that you want to duplicate. The **Duplicate Card** icon displays.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/81be85d-duplicate-card.png",
        "duplicate-card.png",
        125,
        73,
        "#424e59"
      ],
      "caption": "Duplicate card icon"
    }
  ]
}
[/block]
2. Click the **Duplicate Card** icon.
3. The card is duplicated.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/a70d044-duplicate-cards-on-dashboard.PNG",
        "duplicate-cards-on-dashboard.PNG",
        478,
        263,
        "#434c5b"
      ],
      "caption": "Duplicate cards"
    }
  ]
}
[/block]
##Deleting a card

Perform the following steps to delete a card.

1. Hover your cursor over the title of the card that you want to delete. The **Delete Card** icon displays.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/d2a593e-delete-card.png",
        "delete-card.png",
        114,
        100,
        "#45515c"
      ],
      "caption": "Delete card icon"
    }
  ]
}
[/block]
2. Click the **Delete Card** icon.
3. Click the **DELETE** button.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/1e4a278-delete-card-prompt.PNG",
        "delete-card-prompt.PNG",
        239,
        100,
        "#4c5c66"
      ],
      "caption": "Delete button"
    }
  ]
}
[/block]
##Working with filters

###Creating a filter to find a specific operating system

Filters allow you to refine the data that cards display. Nexpose's filter builder makes it easy to build queries without worrying about making syntax errors.

Perform the following steps to build a filter that finds a specific operating system.

1. Click the **Expand Card >** link on the **Assets by Operating System** card. A detailed view of information for this card displays.
2. Click the **Click to create new filter** field. A list of available parameters displays. In this example, parameters available for sites displays.
3. Click **asset.name**.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/b940611-asset-name.PNG",
        "asset-name.PNG",
        299,
        216,
        "#454b59"
      ],
      "caption": "List of operators"
    }
  ]
}
[/block]
4. Click the **=** operator.
5. Enter _Ubuntu_ between the single quotes.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/f86e92b-asset-name-ubuntu.PNG",
        "asset-name-ubuntu.PNG",
        174,
        39,
        "#444b54"
      ],
      "caption": "Parameter with value"
    }
  ]
}
[/block]
6. Click the **save filter** icon (down arrow) to save the filter.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/645e440-save-filter-icon.PNG",
        "save-filter-icon.PNG",
        23,
        27,
        "#5c646c"
      ],
      "caption": "Save filter icon"
    }
  ]
}
[/block]
7. The **Save Filter** dialog displays. Enter the name for the filter in the Name field.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/cfaebd4-save-query.png",
        "save-query.png",
        285,
        114,
        "#dee2e1"
      ],
      "caption": "Save Filter dialog"
    }
  ]
}
[/block]
8. Click the **SAVE** button.
9. The filter is saved and can be retrieved when needed.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/6f0f511-save-query.png",
        "save-query.png",
        285,
        114,
        "#dee2e1"
      ],
      "caption": "Save Filter list"
    }
  ]
}
[/block]

[block:callout]
{
  "type": "info",
  "body": "You will be unable to save a filter unless the syntax is correct. The filter must also have a name in order for it to be saved."
}
[/block]
##Filter operators

The following table lists and explains the operators that you can use to create filters.
[block:parameters]
{
  "data": {
    "h-0": "Operator",
    "h-1": "Explanation",
    "0-0": "=",
    "0-1": "Equals. Returns all records that equal the specified value.",
    "1-0": "!=",
    "1-1": "Not Equal To. Returns all records that are not equal to the specified value.",
    "2-0": ">",
    "2-1": "Greater Than. Returns all records that are greater than the specified value.",
    "3-0": "\\>=",
    "3-1": "Greater Than or Equal. Returns all records that are greater than or equal to the specified value.",
    "4-0": "<",
    "4-1": "Less Than. Returns all records that are less than the specified value.",
    "5-0": "<=",
    "5-1": "Less Than or Equal.",
    "6-0": "CONTAINS",
    "6-1": "Returns all records that contain the specified value.",
    "7-0": "STARTS WITH",
    "7-1": "Returns all records that start with the specified value.",
    "8-0": "ENDS WITH",
    "8-1": "Returns all records that end with the specified value.",
    "9-0": "LIKE",
    "9-1": "Works as a nornal regular expression search as opposed to an SQL regular expression search.",
    "10-0": "IS NULL",
    "10-1": "Returns all records whose specified value is NULL (contains the NULL value).",
    "11-0": "IS NOT NULL",
    "11-1": "Returns all records whose specified value is not NULL (does not contain the NULL value).",
    "12-0": "AND",
    "12-1": "The AND operator returns values when both conditions are true.",
    "13-0": "OR",
    "13-1": "The OR operator returns values when one of the conditions are true."
  },
  "cols": 2,
  "rows": 14
}
[/block]
##Accessing a saved filter

Perform the following steps to access a saved filter.
1. Select the saved filter from the **Saved Filter** dropdown menu.
2. The filter displays the records, if any, that match the filter.
[block:callout]
{
  "type": "info",
  "body": "You can create and save several filters from a card's expanded view, but you can only apply one saved filter to a card at a time."
}
[/block]
##Creating a filter to find vulnerabilities equal to or above a specific risk score

Perform the following steps to create a card that displays vulnerabilities above a specific risk score.

1. Click the **Expand Card >** link on the **Assets by Risk and Vulnerabilities** card. A detailed view of information for this card displays.
2. Click the **Click to create new filter** field. A list of available parameters displays. In this example, parameters available for sites displays.
3. Click **asset.riskScore**.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/238ef3f-asset-risk-score.PNG",
        "asset-risk-score.PNG",
        296,
        222,
        "#414c5b"
      ],
      "caption": "asset.riskScore and available operators"
    }
  ]
}
[/block]
4. Click the **>=** operator and enter the value 1.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/fa8b050-asset-risk-score-ge.PNG",
        "asset-risk-score-ge.PNG",
        135,
        30,
        "#dfe8d1"
      ],
      "caption": "asset.riskScore example"
    }
  ]
}
[/block]