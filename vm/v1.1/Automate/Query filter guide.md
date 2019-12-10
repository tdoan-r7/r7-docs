---
title: "Query filter guide"
excerpt: ""
---
# Overview

Several program features rely on asset and vulnerability filtering in order to refine presented data or determine the scope of projects and triggers.  To this end, InsightVM offers its own query language that you can use to filter your data in as broad or specific terms as you need.  This guide explains the query filter building process.

Query filters are used with the following InsightVM features:

* Dashboard [cards](doc:cards)
* Remediation [projects](doc:remediation-workflow)
* [Automation](doc:automation) triggers

## Query layout
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/f0917e1-query_filter_figure.png",
        "query_filter_figure.png",
        1976,
        214,
        "#949399"
      ]
    }
  ]
}
[/block]
1. **Query Dictionary**
 * Click the **?** icon next to the query bar to open the Query Dictionary.  This table lists all available parameters for your selected category, along with descriptions and data types.  The Query Dictionary is sortable by column and searchable by parameter name.
2. **Query field**
 * Enter your query filter here.  Create your filter step by step through selection of suggested parameters and operators, or type your filter by hand.
3. **Remove query**
 * If you need to start over, click this icon to clear all content in the query field.
4. **Apply**
 * If you’re satisfied with your query, click **Apply** to filter your selected data category.

## Operators

The following operators are available for use when building query filters.
[block:callout]
{
  "type": "warning",
  "title": "NOTE",
  "body": "The list of usable operators shown will depend on which parameter you have selected beforehand."
}
[/block]

[block:parameters]
{
  "data": {
    "h-0": "Operator",
    "h-1": "Description",
    "0-0": "=",
    "0-1": "Equal To. Returns all records that equal the specified value.",
    "1-0": "!=",
    "1-1": "Not Equal To. Returns all records that are not equal to the specified value.",
    "2-0": "\\>",
    "2-1": "Greater Than. Returns all records that are greater than the specified value.",
    "4-0": "<",
    "4-1": "Less Than. Returns all records that are less than the specified value.",
    "5-0": "<=",
    "5-1": "Less Than or Equal To. Returns all records that are less than or equal to the specified value.",
    "3-0": "\\>=",
    "3-1": "Greater Than or Equal To. Returns all records that are greater than or equal to the specified value.",
    "6-0": "CONTAINS",
    "6-1": "Returns all records that contain the specified string.",
    "7-0": "STARTS WITH",
    "7-1": "Returns all records that start with the specified string.",
    "8-0": "ENDS WITH",
    "8-1": "Returns all records that end with the specified string.",
    "9-0": "LIKE",
    "9-1": "Works as a normal regular expression search as opposed to SQL regular expression search.",
    "10-0": "IS NULL",
    "10-1": "Returns all records whose specified value is NULL (contains the NULL value).",
    "11-0": "IS NOT NULL",
    "11-1": "Returns all records whose specified value is not NULL (does not contain the NULL value).",
    "12-0": "AND",
    "12-1": "The AND operator returns values when both conditions are true.",
    "13-0": "OR",
    "13-1": "The OR operator returns values when one of the conditions is true.",
    "14-0": "<=>",
    "14-1": "Used with parameters of the “Object” type.\n\nBuild a single query that specifies all desired sub-parameter matches that are contained within the main object parameter.",
    "15-0": "~>",
    "15-1": "Used with parameters of the “Object” type.\n\nThis operator will return the best match found among an object’s sub-parameters."
  },
  "cols": 2,
  "rows": 16
}
[/block]
## Data categories

Query filters are used to refine one of two data groups:

* Assets
* Vulnerabilities

As a result, all query parameters are either asset-based or vulnerability-based.  One or both of these parameter groups may be available, depending on the type of filter being applied.

# Build a query filter

1. Click the query field to get started.
 * InsightVM will suggest a short list of available parameters.  These suggestions will change as you type characters into the field.
 * Open the Query Dictionary for a full list of available parameters.
2. Select your first parameter.
 * Click or type the parameter name in full to complete your selection.
 * A list of available operators will display once your selection is complete.
3. Select an operator.
 * InsightVM will suggest applicable values if they are available, depending on the parameter.
 * Integer operators generally rely entirely on user input.
 * String operators will provide you with a set of double quotes where you can enter your string value.
 * Operators selected for “Date” parameters will display a calendar tool with clickable days.
4. If desired, refine your query with an “AND” or “OR” operator.
 * These operators allow you to specify multiple conditions.
 * Repeat steps 2 and 3 to complete these additional conditions.
5. Verify that your query is valid.
 * The status indicator will change from red to green once a valid query has been detected.
 * The **Apply** button will activate for valid queries only.
6. Click **Apply**.