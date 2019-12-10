---
title: "Manage Goals and SLAs"
excerpt: ""
---
After you create a goal, it appears in the **Goals** tab. Click the **Goals** icon in the left navigation to see the **Goals** tab and the [**Recommended Goals**](#section-recommended-goals) tab.  

#View All Goals
The Goals tab contains a list of your organization’s goals. You’ll also see [high-level details](#section-goals-overview) of each goal.   

##Roles Required
Anyone within your organization can view any of the goals on the **Goals** tab if they are: 
* A Nexpose global administrator who has an Insight Platform account
* A Nexpose non-global administrator on a Nexpose security console who is a site administrator and also has an Insight Platform account
* A user whose Insight account was created by the Insight Platform Administrator 
[block:callout]
{
  "type": "danger",
  "title": "Warning - Goal Editing and Deletion by Other Users",
  "body": "If anyone in your organization fits into the [“Roles Required”](#section-roles-required) list above, they can view, edit, or delete any goal, regardless if they created them or not."
}
[/block]
##View Goals Overview
High-level goal information indicating progress of your organization’s goals appears in the horizontal bar at the top of the screen: 
* Goal number - Total number of goals that have been created 
* Goal status - Number of goals by status
* You can filter the goals table by status by clicking it.
   * Green - Compliant/On Track
   * Yellow - At Risk
   * Red - Not Compliant/Not Met
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/81a2a35-Screen_Shot_2019-10-28_at_4.53.32_PM.png",
        "Screen Shot 2019-10-28 at 4.53.32 PM.png",
        1585,
        103,
        "#4a5966"
      ]
    }
  ]
}
[/block]
##View Individual Goal Overview
Information about individual goals include the following and can be sorted: 
* Assets/Vulnerabilities - Number of assets or vulnerabilities that affect a goal
* Status - Denotes the goal’s state by dot color 

This will vary based on goal type. 
[block:parameters]
{
  "data": {
    "0-1": "Green Dot",
    "1-0": "Time Bound",
    "2-0": "Continuous",
    "3-0": "SLAs",
    "1-1": "Compliant",
    "2-1": "Compliant",
    "3-1": "Compliant (if asset-based) \n\nRemediated (if vulnerability-based)",
    "0-2": "Orange Dot",
    "1-2": "N/A",
    "2-2": "N/A",
    "3-2": "In Grace Period",
    "0-3": "Red Dot",
    "1-3": "Not Compliant",
    "3-3": "Not Compliant/\nPast Due",
    "2-3": "Not Compliant"
  },
  "cols": 4,
  "rows": 4
}
[/block]
* **Goal type** - Denotes if the goal is time bound, SLA, or continuous 
* **Time Remaining** - Denotes how much time is left before the goal is completed 
* **Created On** - Date the goal was created
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/e124754-new_columns.jpg",
        "new_columns.jpg",
        1570,
        173,
        "#3a454f"
      ]
    }
  ]
}
[/block]
To customize the order of your goals table, click **Manage Columns** next to the search box. You can choose which columns you want to see and reorder the columns in the table by dragging the headers in the order you want. 

##Edit, Copy, and Delete
Individual goal rows will show additional icons on mouseover towards the right side of your screen.
[block:parameters]
{
  "data": {
    "0-0": "Pencil",
    "1-0": "Stack",
    "2-0": "Trash can",
    "0-1": "Click to open your goal in the wizard and make any necessary changes. Note that users in the [“Roles Required”](#section-roles-required) list mentioned earlier can view, edit, or delete any goal, regardless if they created them or not.",
    "1-1": "Click here to copy your goal.",
    "2-1": "Click here to delete your goal. Deletions must be confirmed before they go through."
  },
  "cols": 2,
  "rows": 3
}
[/block]
#View Goals Details
Click the name link of any goal in your table to see more information about it. While the layout of information is the same for all goals, the data populating the fields can vary based on goal type, scope, and query. We highlight those differences in this section. 

##View Individual Goal Overview
The “Goal Overview” section shows details of your goal. Click the pencil icon to edit your goal. This launches the goal wizard so you can edit your "Manage Goal" details.
[block:callout]
{
  "type": "info",
  "title": "Note - Goal Editing Capability",
  "body": "You can only edit a goal by changing its name, description, or dashboard assignment. We do not support editing the scope or conditions at this time. If you want to edit the scope or conditions, you need to create a new goal."
}
[/block]

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/f0c1c1c-Goal_Overview.png",
        "Goal Overview.png",
        1537,
        520,
        "#494e58"
      ]
    }
  ]
}
[/block]
A. **Goal Overview** - This section contains general information about the goal, which includes: 
* **Type** - Goal type ([time bound](doc:goals-and-slas#section-time-bound-goals), [continuous](doc:goals-and-slas#section-continuous-goals), or [SLA](doc:goals-and-slas#section-slas))
* **Description** - Description of the goal (if you wrote one while creating your goal)
* **Due On** - Date you want your goal met (only applies to [time bound](doc:goals-and-slas#section-time-bound-goals) goal) 
* **Created On** - Date you made your goal 
* **Last Updated** - The last time the goal was updated with new data.
* **Criteria** - Conditions the goal must meet
* **Asset Filter** - Query used to narrow asset scope down
* **Vulnerability Filter** - Query used to narrow vulnerability scope

B. **Status bar** - This section contains the number of affected assets or vulnerabilities, the number of assets or vulnerabilities that are compliant, in grace period (applies only to SLAs,) and not compliant or past due (applies only to [SLAs](doc:goals-and-slas#section-slas)), deadline (applies only to [Time Bound](doc:goals-and-slas#section-time-bound-goals)), and goal status. 
* Met (applies to [Time Bound](doc:goals-and-slas#section-time-bound-goals))
* Compliant (applies to [Continuous](doc:goals-and-slas#section-continuous-goals) and [SLAs](doc:goals-and-slas##section-slas))
* Not Compliant (applies to [Continuous](doc:goals-and-slas#section-continuous-goals) and [SLAs](doc:goals-and-slas##section-slas))

C. **Data visualization** - The visualization varies based on goal type: 

* **[Continuous](doc:goals-and-slas#section-continuous-goals)** - Gauge depicts the percentage of assets in compliance 
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/e91bd06-Screen_Shot_2019-11-18_at_8.30.08_PM.png",
        "Screen Shot 2019-11-18 at 8.30.08 PM.png",
        1200,
        435,
        "#45535f"
      ],
      "caption": "Continuous Example"
    }
  ]
}
[/block]
* **[Time Bound](doc:goals-and-slas#section-time-bound-goals)** - Graph with dates along the x-axis, starting from the date you created the goal 
The dotted line shows the percentage of assets that you want to meet to accomplish your goal, while the solid blue line shows the actual percentage. So, if your solid line is above the dotted line, you are successfully meeting your goal, while a solid line below indicates that some work needs to be done. The vertical line represents your due date.   
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/d378617-Screen_Shot_2019-11-15_at_11.45.26_AM.png",
        "Screen Shot 2019-11-15 at 11.45.26 AM.png",
        955,
        348,
        "#445669"
      ],
      "caption": "Time Bound Example"
    }
  ]
}
[/block]
* **[SLAs](doc:goals-and-slas#section-slas)** -  Graph with dates along the x-axis, starting from the date you created the goal 
The y-axis measures either the percentage or total number of assets in scope that you want to meet your goal’s criteria. The thin blue line shows the percentage on the left y-axis, while the thicker gray line shows the total number of assets on the right y-axis.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/c656ab2-Screen_Shot_2019-11-15_at_12.05.55_PM.png",
        "Screen Shot 2019-11-15 at 12.05.55 PM.png",
        1126,
        330,
        "#434f5a"
      ],
      "caption": "SLA Example"
    }
  ]
}
[/block]

[block:callout]
{
  "type": "info",
  "title": "Note - Scan-based Data Points",
  "body": "When you first create an SLA, you might not see trending data or a horizontal line immediately. This is because these data points are based on your scan settings. It might take several scans to map data points, especially if scans are spaced apart."
}
[/block]
##SLA Detail Overview
The information in SLAs vary from [Time Bound](doc:goals-and-slas#section-time-bound-goals) or [Continuous](doc:goals-and-slas#section-continuous-goals) goals, which we'll explain in this section. 

Click the name link of any SLA in your "Goals" table to see details about it. You can see detailed data surrounding your assets or vulnerabilities by selecting **Assets** or **Vulnerabilities** from the menu dropdown on the table below the visualization. 


Here’s a breakdown of the information that appears: 

A. **Goal Overview** - Similar to the "Goal Overview" mentioned earlier, click the pencil icon to open the goal wizard if you need to make any edits. 

B. **Status bar** - Key performance indicators (KPIs) 
When you click on a KPI and scroll down, you see a table that lists the assets or vulnerabilities in that particular category. 

a. **Compliant** or **Remediated** - This can vary, depending on the type of SLA you made:
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;i. If you made an asset-based SLA, it will display **Compliant**, which is the number of assets that have been remediated within the time window since their discovery. 
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;ii. If you made a vulnerability-based SLA, it will show **Remediated**, which is the number of vulnerabilities that have been remediated within the time window since their discovery.  
b. **In grace period** - Indicates the number of assets that have not been remediated yet, but are within the time window since their discovery
c. **Past due** - Indicates the number of assets that have not been remediated yet and are outside the time window since their discovery
[block:callout]
{
  "type": "info",
  "title": "Note - KPIs Filter Your Assets or Vulnerabilities Table",
  "body": "Click a status to view the data related to that KPI. You can then export to CSV."
}
[/block]

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/92a803b-Screen_Shot_2019-11-15_at_1.35.58_PM.png",
        "Screen Shot 2019-11-15 at 1.35.58 PM.png",
        1233,
        488,
        "#46505a"
      ]
    }
  ]
}
[/block]
C. **SLAs Data Visualization** - See the SLAs visualization explanation above. 
D. **Assets and Vulnerabilities Data Table** - As mentioned earlier, select **Assets** or **Vulnerabilities** from the menu dropdown on the table to see detailed data surrounding your assets or vulnerabilities.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/638162a-Screen_Shot_2019-11-18_at_7.57.49_PM.png",
        "Screen Shot 2019-11-18 at 7.57.49 PM.png",
        1204,
        136,
        "#3b434d"
      ]
    }
  ]
}
[/block]

[block:callout]
{
  "type": "info",
  "body": "When you first create an SLA, you might not see trending data or a horizontal line immediately. This is because these data points are based on your scan settings. It might take several scans to map data points, especially if scans are spaced apart.",
  "title": "Note"
}
[/block]
###Export to CSV
There are multiple ways to customize your data for CSV export: 

* Check the box next to the **Export to CSV** button to select all the rows in the table below that shows assets or vulnerabilities. You can select or deselect individual rows if you don’t want to include them in the export file.
* Select rows individually. In this example, the first and third row will be exported as a CSV file. 
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/badfc53-Screen_Shot_2019-11-11_at_12.46.34_PM.png",
        "Screen Shot 2019-11-11 at 12.46.34 PM.png",
        1181,
        199,
        "#3f4d59"
      ]
    }
  ]
}
[/block]
* Select a KPI to display relevant data in the data table. 
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/64638c3-Screen_Shot_2019-11-11_at_1.01.45_PM.png",
        "Screen Shot 2019-11-11 at 1.01.45 PM.png",
        1198,
        92,
        "#555e6a"
      ]
    }
  ]
}
[/block]
After you’ve identified what data you want to export, click **Export to CSV** to download. 

###Data Details Table
You’ll find these details to help you take action: 
* **Due date** - Applies to assets and vulnerabilities. This is when the grace period ends.
* **Discovery date** - Changes based on if you’re looking at vulnerabilities or assets. 
  * **Vulnerabilities** - The discovery date of the vulnerabilities.
  * **Assets** - The time when an asset that does not meet the criteria is discovered.

##Recommended Goals
Select **Recommended Goals** to see goals that will enhance your security operations. Selecting a card will pre-configure the query field of the goal wizard, but you can finetune the parameters to meet your organization’s needs.