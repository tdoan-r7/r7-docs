---
title: "Query Builder"
excerpt: ""
---
[block:callout]
{
  "type": "info",
  "title": "NOTE: The Query Builder is currently available in \"preview\" form",
  "body": "A feature that is in \"preview\" has made enough progress to be suitable for customer use, albeit still in active development.\n\nInsightVM customers can take advantage of this preview to provide early feedback and usage data that will shape the final version of the Query Builder when it becomes Generally Available (GA).\n\nLike other preview features, the Query Builder may not yet have all the functionality planned for the GA version and may only be accessible from cloud-enabled pages in InsightVM, such as the Dashboard tab. Using this preview will not affect your production data.\n\nThe following features are not yet available in the preview, but are planned for GA:\n\n* Result table column customization\n* Additional table columns\n* Individual tabs for Software and Services data \n* Query filter inheritance in Asset and Vulnerability detail pages\n* Integration into Dashboard Cards and Remediation Projects"
}
[/block]
The Query Builder is a cloud-based feature that helps you distill asset and vulnerability data using custom-built queries. These queries are composed of “pills”, which are individual criteria that filter your data based on an array of unique parameters. These pills display and define the fields, operators, and values as the query is built. 

#Benefits of the Query Builder
The Query Builder allows you to query and analyze data without SQL knowledge third-party tools.  

You can use the Query Builder to:  
*  Quickly pivot between Asset and Vulnerability results using the same query. 
*  Perform faster queries than those conducted with the Security Console.
*  [Export data](#section-export-a-query) to a CSV file. 

#Access the Query Builder
To access the Query Builder, sign in to your Insight platform account and open your InsightVM product. In the upper right corner, click the icon with the magnifying glass next to the account icon. 
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/976387c-QB_icon.png",
        "QB_icon.png",
        284,
        59,
        "#282c34"
      ]
    }
  ]
}
[/block]
#Get to Know the Query Builder
Before building a query, let’s familiarize ourselves with the interface and learn some basic concepts. 

##Query Builder Layout 
Click **Add Criteria** to open the field selection interface.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/3fbe4f6-QB_map.jpg",
        "QB_map.jpg",
        2464,
        1004,
        "#4c5861"
      ]
    }
  ]
}
[/block]
A. Click **Suggested Fields** to display the most commonly used fields and their definitions. 
B. Click **Recent Fields** to display fields that you have recently used in other pills. 
C. Under Categories, you’ll see a list of field categories. Click a field category in the left panel to automatically scroll to the relevant fields in the second panel (denoted in this figure as **C-1**). You can also scroll through the fields manually. Each field definition is located to the right of its corresponding field label. 
[block:callout]
{
  "type": "info",
  "title": "TIP",
  "body": "Type a keyword in the search bar to quickly bring up fields that contain that keyword."
}
[/block]
D. Click the desired field to add it to your in-progress query (denoted in this figure as **D**). 
E. Next, select an operator from this panel. 
F. Finally, select a value from the available list in this panel or enter one manually. 
G. Click **Apply Criteria** to create the pill. 

Let’s take a closer look at the structure of the pill.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/135a274-Pill_Anatomy.png",
        "Pill Anatomy.png",
        462,
        117,
        "#434952"
      ]
    }
  ]
}
[/block]
A. **Filter checkbox** - Check this box to apply the contents of the pill to your data. If you uncheck the box, the pill will not apply to the data. 
B. **Field** - This is the attribute used to sort your data. 
C. **Operator** 
D. **Value **
E. **Criterion** - The entire contents of a pill. The criterion can be used by itself as a query, or used in conjunction with others to make a more targeted query. 
F. **“X”** - Removes the pill. 

#Create a Query 
You can create two types of queries with the Query Builder: 
* Single pill queries
* Multiple pill queries 

##Create a Single Pill Query
To create a single pill query, follow these steps: 

1. Click Add Criteria.
2. Select a category. 
3. Select a desired field from the field panel. 
4. Select an operator. 
5. Click Apply Criteria to complete your pill. 
6. Click Save to build your query. 

##Create a Multiple Pill Query
To build a more targeted query, you can build a query composed of several pills: 

1. After creating the first pill, **Add Criteria** and build another pill. 
2. Chose between **AND** or **OR** to join your queries together.  
[block:callout]
{
  "type": "info",
  "title": "NOTE",
  "body": "You can switch to **AND** or **OR** at any time, but your choice will apply to the rest of your query.  You cannot mix **AND** or **OR** pills together in the same query."
}
[/block]
3. Click **Save**.

#Save a Query
Upon clicking **Save**, a review screen will appear prompting you to enter a query name and set the visibility.

Select **Private** to limit those who can see, run, and save a copy of the query to one or more users of your choosing. Included users can edit the pills to generate new results, but they cannot save changes unless they save a new query. Use the dropdown to specify which users will have access to this query. 
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/283e75c-Screen_Shot_2019-04-05_at_3.12.28_PM.png",
        "Screen Shot 2019-04-05 at 3.12.28 PM.png",
        685,
        309,
        "#5a6168"
      ]
    }
  ]
}
[/block]
##Load a Saved Query
To load a previously saved query, follow these steps: 

1. Click the Load Query button in the upper right corner of the Query Builder interface.
2. Select the desired query. 

###Query Permissions
The current visibility permissions of the query will affect the way you can edit existing queries and save new copies:  
* If you are the query owner, you can edit the query and save as-is. 
* If a colleague shared the query with you, you must save your changes as a new query.  Click the following icon to save a query as a new copy: 
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/540ec10-Screen_Shot_2019-04-05_at_3.30.37_PM.png",
        "Screen Shot 2019-04-05 at 3.30.37 PM.png",
        145,
        60,
        "#4e5560"
      ]
    }
  ]
}
[/block]
#Export a Query 
For easy reporting, you can export query results as a CSV file. Click the **Export as CSV** button to download a CSV file with the contents of your currently applied query. 
[block:callout]
{
  "type": "info",
  "title": "Note - Epoch Dates Exported in CSV Files",
  "body": "Dates in CSV files exported from the Query Builder are in epoch format (in milliseconds). To convert these epoch dates into a standard date format, use the following formula in Google Sheets or Microsoft Excel:\n\n`=DATE(1970,1,1)+(K2/86400000)`\n\nSubstitute the example `K2` cell with the cell of the epoch data you want to convert."
}
[/block]
#Future Query Builder Features
As mentioned before, new functionality will be added to the Query Builder soon. 
Upcoming features include:

* Additional columns for solutions, software, and services
* Column customization functionality to help you find the information you’re looking for
* Quick pill application through inclusion/exclusion functions on individual table cells