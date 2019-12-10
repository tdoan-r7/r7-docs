---
title: "Viewing and working with cards"
excerpt: ""
---
Cards are integral components of your dashboard that present real-time data in a variety of styles, including graphs, tables, and charts.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/5e0ca4e-ViewingCards-Dashboard.png",
        "ViewingCards-Dashboard.png",
        2880,
        1294,
        "#3d4653"
      ]
    }
  ]
}
[/block]
* [Card data](doc:viewing-and-working-with-cards#section-card-data)
* [Card types](doc:viewing-and-working-with-cards#section-card-types)
* [Viewing cards](doc:viewing-and-working-with-cards#section-viewing-cards)

# Card Data

Cards provide analytics for the following areas:
* **Assets** - Devices on a network that InsightVM discovers during a scan.
* **Key Performance Indicators (KPI)** - Metrics used to define and measure progress towards organizational goals.
* **Risk** - The potential danger that each vulnerability poses to an attacker exploit.
* **Sites** - A collection of assets that are targeted for a scan.
* **Vulnerabilities** - Security flaws found in a network or computer.

# Card Types

A dashboard can contain instances of the following cards:
* **Table** - Displays multiple sets of data in a tabular format with sortable functionality.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/eb0695b-CardTypes-Table.png",
        "CardTypes-Table.png",
        1171,
        633,
        "#414a59"
      ]
    }
  ]
}
[/block]
* **Scatter** - Displays selected data plotted on a dual axis chart.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/6d92a5e-CardTypes-Scatter.png",
        "CardTypes-Scatter.png",
        1171,
        628,
        "#454e5e"
      ]
    }
  ]
}
[/block]
* **Pie** - Displays a pie chart divided into sectors that represent proportional values of the selected data.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/2696e12-Column-Hover.png",
        "Column-Hover.png",
        2880,
        1037,
        "#3b434f"
      ]
    }
  ]
}
[/block]
* **Solid gauge** - Displays a data value as a colored angle of an arc.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/1e05d5d-CardTypes-Gauge.png",
        "CardTypes-Gauge.png",
        574,
        629,
        "#454e5e"
      ]
    }
  ]
}
[/block]
* **Stacked area** - Displays cumulative totals using numbers or percentages over a period of time.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/addf21c-Screen_Shot_2017-12-14_at_1.30.15_PM.png",
        "Screen Shot 2017-12-14 at 1.30.15 PM.png",
        686,
        406,
        "#494d58"
      ]
    }
  ]
}
[/block]
* **Column** - Displays multiple sets of data, as vertical bars, that coordinate with the value axis.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/e2ffc4a-CardTypes-Column.png",
        "CardTypes-Column.png",
        1172,
        629,
        "#454e5e"
      ]
    }
  ]
}
[/block]
* **Number** - Displays a numeric value of the selected data.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/fe9c7db-CardTypes-Number.png",
        "CardTypes-Number.png",
        571,
        629,
        "#454e5e"
      ]
    }
  ]
}
[/block]
* **Timeline** - Displays a graph of the selected data over a period of time.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/4e3b003-CardTypes-Timeline.png",
        "CardTypes-Timeline.png",
        1171,
        629,
        "#454e5e"
      ]
    }
  ]
}
[/block]
* **Line** - Displays a chart with information as a series of data points
* **Tree map** - Displays hierarchical data by using nested rectangles.
* **Heat map** - Displays a table containing multiple sets of data, represented by colors instead of numerical values.

# Viewing cards

You can expand cards for a more granular view of your data. The information made available by the card and the way it is presented is dependent on the card data and card type.
1. To view an existing card, click **Expand Card >**.
[block:callout]
{
  "type": "info",
  "body": "The expand card feature is not available for all cards."
}
[/block]

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/0f5268b-ViewCards-ExpandCard.png",
        "ViewCards-ExpandCard.png",
        1167,
        49,
        "#444c5c"
      ]
    }
  ]
}
[/block]
The expanded card panel displays the following:

* **Close** button - Closes the expanded card panel.
* **Select a Saved Query** drop down menu - Allows you to select a previously created filter.
* **Save query** icon - Saves a newly created filter.
* **Click to create new filter** field - Allows you to create a filter to be used with the card. To learn more, see Advanced filter options.
* **Apply** button - Applies a newly created filter.
* **Data** table - Provides multiple sets of data in a tabular format.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/1af0b51-ExpandCard-ViewPanel.png",
        "ExpandCard-ViewPanel.png",
        2880,
        1426,
        "#3a434f"
      ]
    }
  ]
}
[/block]
* **Agent** status - Assets that have the Rapid7 Insight Agent installed will display a corresponding icon.  The icon will show status and versioning information on mouseover.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/871ff64-EA_agent_versioning.png",
        "EA_agent_versioning.png",
        1330,
        698,
        "#515c65"
      ]
    }
  ]
}
[/block]
* **Analytics** - Interactive graphs, tables, and charts with detailed information. Available for the following card types:

##Scatter

Hover your mouse over a data point for additional information.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/54bc805-Scatter-Hover.png",
        "Scatter-Hover.png",
        2880,
        1032,
        "#3b434f"
      ]
    }
  ]
}
[/block]
Click on a data point for detailed analysis.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/9956476-Pie-Click.png",
        "Pie-Click.png",
        2880,
        1070,
        "#3b424f"
      ]
    }
  ]
}
[/block]
##Pie

Hover your mouse over a segment for additional information.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/e23857e-Pie-Hover.png",
        "Pie-Hover.png",
        2880,
        1065,
        "#3b424f"
      ]
    }
  ]
}
[/block]
Click on a segment or select a numeric range for detailed analysis.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/cb41945-Pie-Click.png",
        "Pie-Click.png",
        2880,
        1070,
        "#3b424f"
      ]
    }
  ]
}
[/block]
##Solid gauge

Hover your mouse over a segment for additional information.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/b4d095d-Gauge-Hover.png",
        "Gauge-Hover.png",
        2880,
        1030,
        "#3b434f"
      ]
    }
  ]
}
[/block]
Click on a segment or select a numeric range for detailed analysis.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/c80b067-Gauge-Click.png",
        "Gauge-Click.png",
        2880,
        1085,
        "#3b4350"
      ]
    }
  ]
}
[/block]
##Table

Sort and view data using clickable headers.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/496be1d-Table-View.png",
        "Table-View.png",
        2880,
        1427,
        "#3a424f"
      ]
    }
  ]
}
[/block]
##Stacked area

Hover your mouse over a segment for additional information.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/61ae824-Screen_Shot_2017-12-15_at_9.42.24_AM.png",
        "Screen Shot 2017-12-15 at 9.42.24 AM.png",
        1844,
        483,
        "#4b4e5a"
      ]
    }
  ]
}
[/block]
##Column

Hover your mouse over a column for additional information.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/d8d4b72-Column-Hover.png",
        "Column-Hover.png",
        2880,
        1037,
        "#3b434f"
      ]
    }
  ]
}
[/block]
Click on a column for detailed analysis.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/2387c31-Column-Click.png",
        "Column-Click.png",
        2880,
        1065,
        "#3b4350"
      ]
    }
  ]
}
[/block]
##Number

Select an item from the drop-down menu to update the results.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/eca3cdc-Number-Select.png",
        "Number-Select.png",
        2880,
        1017,
        "#3a424e"
      ]
    }
  ]
}
[/block]