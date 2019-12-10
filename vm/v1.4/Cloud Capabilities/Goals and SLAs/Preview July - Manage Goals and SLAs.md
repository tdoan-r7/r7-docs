---
title: "Preview July - Manage Goals and SLAs"
excerpt: ""
---
#Overview
You can manage your goals on the **Goals** tab. Additionally, you can select the **Recommended Goals** tab, which pre-configures the goal wizard with metrics that can help you successfully enhance your security operations. 

##Goals
Select **Goals** to see a table of all configured goals and relevant data in sortable columns. 

##Edit, Copy, and Delete
Individual goal rows will show additional icons on mouseover towards the right side of your screen.
[block:parameters]
{
  "data": {
    "0-0": "Pencil",
    "1-0": "Stack",
    "2-0": "Trash can",
    "0-1": "Click here to open your goal in the wizard and make any necessary changes.",
    "1-1": "Click here to copy your goal.",
    "2-1": "Click here to delete your goal. Deletions must be confirmed before they go through."
  },
  "cols": 2,
  "rows": 3
}
[/block]
##Goals Detail Overview
Click the name link of any goal in your table to see the “Goal Details” page. You can see detailed data surrounding your assets or vulnerabilities by selecting **Assets** or **Vulnerabilities** from the menu dropdown. 

Here's a breakdown of the information you'll find: 

1. **Goal Overview** - Shows general information about the goal. Click the edit icon to open the goal wizard if you need to make any changes to your goal. 
2. **Goal status bar** - Shows the status of your goal, which can be on track, at risk, or missed. It also shows the number of assets that are compliant or not compliant. 
3. **Data visualization** - If the goal is continuous, you will see a gauge. If your goal is time bound, you will see a graph. 
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/c2e06ee-Screen_Shot_2019-05-11_at_4.07.13_PM.png",
        "Screen Shot 2019-05-11 at 4.07.13 PM.png",
        3110,
        910,
        "#48535e"
      ]
    }
  ]
}
[/block]
##SLA Detail Overview
Click the name link of any SLA in your table to see details about it. You can see detailed data surrounding your assets or vulnerabilities by selecting **Assets** or **Vulnerabilities** from the menu dropdown. 

Here’s a breakdown of the information you’ll find: 

1. **Goal Overview** - Shows general information about the goal. Click the pencil icon to start the goal wizard to edit your goal.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/8f799d9-Screen_Shot_2019-05-10_at_11.14.47_AM.png",
        "Screen Shot 2019-05-10 at 11.14.47 AM.png",
        698,
        840,
        "#4a545e"
      ]
    }
  ]
}
[/block]

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/acef39e-preview_SLA.gif",
        "preview_SLA.gif",
        2848,
        1638,
        "#3f4a54"
      ]
    }
  ]
}
[/block]
2. **Status bar** - Shows key performance indicators (KPIs). When you click on a KPI and scroll down, you will see a table that lists the assets or vulnerabilities in that particular category. 
3. **Compliant** or **Remediated** - This can vary, depending on the type of SLA you made:
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;i. **Compliant** - If you made an asset-based SLA, it will display “Compliant,” which is the number of assets that have been &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;remediated within the time window since their discovery. 
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;ii. **Remediated** - If you made a vulnerability-based SLA, it will show “Remediated,” which is the number of vulnerabilities that &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;have been remediated within the time window since their discovery.  
4. **In grace period** - Indicates the number of assets that have not been remediated yet, but are within the time window since their discovery.
5. **Past due** - Indicates the number of assets that have not been remediated yet and are outside the time window since their discovery.
6. **Data visualization** - You will see two charts with a horizontal line. The line starts when you first create the SLA. If your SLA is vulnerability-based, both charts will display vulnerability instances. if your SLA is asset-based, both charts will display asset data.
      &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;i. The top chart shows a horizontal line that represents the percentage of assets or vulnerability instances that are compliant.  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;ii. The bottom chart shows a horizontal line that indicates the spikes or drops in compliance percentage that might occur when &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;adding new assets or vulnerabilities. 
[block:callout]
{
  "type": "info",
  "body": "When you first create an SLA, you might not see trending data or a horizontal line immediately. This is because these data points are based on your scan settings. It might take several scans to map data points, especially if scans are spaced apart.",
  "title": "Note"
}
[/block]
##Recommended Goals
Select **Recommended Goals** to see goals that will enhance your security operations. Selecting a card will pre-configure the query field of the goal wizard, but you can finetune the parameters to meet your organization’s needs.