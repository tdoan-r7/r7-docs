---
title: "Goals"
excerpt: ""
---
#Overview

In InsightVM, Goals is a feature that can help reduce overall risk and improve the security of your environment. Track your remediation efforts by identifying goals and defining metrics to measure against those goals. Goal cards can be added to dashboards to display progress at a glance. 

##Goal Types
There are two types of goals that can be created: 
  * Time bound
  * Continuous

###Time Bound
A time bound goal lets you specify metrics for assets or vulnerabilities and assign a target date so you can track your progress as your deadline approaches. 

Examples include:  
  * Remove 100% of Windows 7 desktops across the entire organization by January 14, 2020.
  * Reduce the number of exploitable vulnerabilities in Boston by 50% by December 2020.
  * Reduce the number of assets with critical vulnerabilities to less than 10% by June 15, 2022.

###Continuous
A continuous goal lets you monitor progress or criteria without a time limit, such as a rule or a key performance indicator. 

Examples include: 
  * All external facing assets must have a closed SSH port. 
  * All critical assets should have had a successful credential scan. 
  * Only 20% of MS vulnerabilities should be critical severity. 

#Create a Goal

To create a goal, follow these steps:   

1. In the left navigation, click the **Goals** icon.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/fc32866-Screen_Shot_2018-10-01_at_4.07.08_PM.png",
        "Screen Shot 2018-10-01 at 4.07.08 PM.png",
        56,
        247,
        "#433e44"
      ]
    }
  ]
}
[/block]
2. In the next screen, click **+ New Goal** in the upper right corner or at the bottom of the image. This action will launch the wizard to create a goal.  

In addition, you can create a goal from any dashboard by following these steps: 

1. In the left navigation, click the **Dashboard** icon.
2. In the upper right corner, click **+ Add Card**. 
3. In the pop-up window that appears, select **Goals** in the left column. 
4. Select your desired goal type by checking the appropriate box. 
5. Click **Add**. This action will add a goal card on your dashboard.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/d0977f8-Screen_Shot_2018-10-01_at_4.31.13_PM.png",
        "Screen Shot 2018-10-01 at 4.31.13 PM.png",
        848,
        668,
        "#4b5662"
      ]
    }
  ]
}
[/block]
6. Click **Create a Goal** to launch the wizard to create a new goal. 

After creating a new goal, you can add it to a card to any dashboard. See [Goal Cards](doc:goals-and-slas-cards) for more information.