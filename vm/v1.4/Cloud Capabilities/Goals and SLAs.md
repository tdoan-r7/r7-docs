---
title: "Goals and SLAs"
excerpt: ""
---
#Overview

Goals and SLAs is an InsightVM feature that helps you reduce overall risk and improve the security of your environment. You can track your remediation efforts by identifying goals and defining metrics to measure against those goals. To help you view your progress, you can add goal cards to dashboards. 

##Goal Types
A goal is a metric that you can use to evaluate your remediation efforts. You can build goals to track and measure progress against your vulnerability and asset data to help evaluate your organization’s overall security performance.

You can create three types of goals: 

  * [Time bound](#section-time-bound-goals)
  * [Continuous](#section-continuous-goals)
  * [Service Level Agreements (SLAs)](#section-slas)

###Time Bound Goals
A time bound goal lets you specify metrics based on a target date. It is a one-time goal with a set deadline and suited for data scopes that do not change. After you meet the goal, you most likely will not encounter it again after you achieve it.    

For example, let’s say you have 150 assets that use Windows 10, but that operating system will become obsolete by October 2025. Since you’ll need to upgrade those 150 assets before October, you can create a time bound goal to help you track the systems that need to be upgraded before that date. 

Examples include:  
  * Remove 100% of Windows 7 desktops across the entire organization by January 14, 2020.
  * Reduce the number of exploitable vulnerabilities in Boston by 50% by December 2020.
  * Reduce the number of assets with critical vulnerabilities to less than 10% by June 15, 2022.

###Continuous Goals
A continuous goal lets you monitor progress or criteria without a time limit, such as a rule or a key performance indicator. If you want to keep track of a recurring event or condition to ensure you’re compliant, use a continuous goal to monitor any new occurrences or status changes. A continuous goal helps you track repeatable events or conditions that can change with each scan or agent data collection.

For example, if you need to keep port 22 closed on all assets, you can create a continuous goal to monitor if any assets have an open port 22. 


Examples include: 
  * All external facing assets must have a closed SSH port. 
  * All critical assets should have had a successful credential scan. 
  * Only 20% of MS vulnerabilities should be critical severity. 

###SLAs
An SLA lets you track remediation over a dynamic time span as part of your organizational targets. An SLA monitors recurring events or conditions that can change with each scan, like a continuous goal, but under a designated time frame. This time frame starts on a rolling basis for each new vulnerability or asset discovered during scans or agent collection, so the SLA must be met or fixed for all instances within this designated time. 

For example, you can use an SLA to monitor critical vulnerabilities on production systems to ensure they are patched within seven days after they are discovered. Since new vulnerabilities are constantly being discovered, you can’t make a time bound or continuous goal, since systems should be patched and protected as soon as possible. 
 
Examples include: 
  * Remediate all critical vulnerabilities in production environments within three days of discovery.
  * Remediate all vulnerabilities that have a CVSS of 5 or greater on Windows Servers within 15 days of discovery.
  * Remediate all assets in Boston to achieve asset risk score to be less than 1000 within 10 days of discovery.


#Create a Goal or SLA

To create a goal or SLA, you will use a wizard to select your desired goal type, sort and define your data, establish the conditions you want to meet, and save. 

Refer to this chart to help determine if you want to build a goal or SLA:  
[block:parameters]
{
  "data": {
    "h-0": "Goal Type",
    "h-1": "Data Scope",
    "h-2": "Time Frame",
    "0-0": "Time Bound",
    "0-1": "Does not change",
    "0-2": "Specific end date",
    "1-0": "Continuous",
    "2-0": "SLA",
    "1-1": "Can change",
    "2-1": "Can change",
    "1-2": "Ongoing",
    "2-2": "Relative"
  },
  "cols": 3,
  "rows": 3
}
[/block]
The process for creating a goal is identical for goals and SLAs. To create a goal, you must first navigate to your goals page, which is where you can launch the goal creation wizard.   

There are two ways to access your goals page: 
  * From the InsightVM left menu
  * From the dashboard by clicking on “**View Goal Details**” link on a goal card.

##InsightVM Left Menu

To create a goal:   

1. Log into InsightVM. 
2. In the left navigation menu, click the **Goals** icon. 
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
3. When the “Goals and SLAs” page appears, click **+ New Goal** in the upper right corner. This action will launch the wizard to create a goal.  

##Dashboard

To create a goal card on your dashboard:   

1. Log into InsightVM. 
2. In the left navigation menu, click the **Dashboard** icon. 
3. When the “Default Dashboard” page appears, click **+ Add Card** in the upper right corner to launch the wizard to add a goal. 
[block:callout]
{
  "type": "info",
  "title": "Note - Goals and queries",
  "body": "Creating goals relies on [building queries to filter asset and vulnerability data](doc:query-filter-guide) to narrow your scope. For information on how to build queries, visit our [Query Filter Guide.](doc:query-filter-guide)"
}
[/block]
##Create a Goal
Here’s an overview of the steps:

1. Select Goal Type
2. Define Scope
3. Specify Criteria 
4. Manage Goal

###Select Goal Type
Select your desired goal type: [time bound](#section-time-bound-goals), [SLA](#section-slas), or [continuous]((#section-continuous-goals).

###Define Scope
To narrow down your data, [build a new query to filter asset and vulnerability data](doc:query-filter-guide) or use an existing one. At a minimum, you must add at least one asset filter, but you can add more by using “And” or “Or” to combine them. 
[block:callout]
{
  "type": "info",
  "title": "Tip - Narrow your data down",
  "body": "Adding a vulnerabilities filter is optional, but helps cut your data down even more for faster processing. You can add more filters if needed by using “And” or “Or.”"
}
[/block]

[block:callout]
{
  "type": "info",
  "title": "Note - Filters only affect scope here",
  "body": "Adding filters at this step only affects scope. You’ll add qualifiers in the next step, **Specify Criteria**. "
}
[/block]
###Specify Criteria 
Next, you’ll select the criteria to evaluate your data range which will formulate a target statement for you to measure against your data. 
 
###Manage Goal
In this last step, you’ll enter a name and description to identify your goal. You can also assign your goal to a dashboard for easy reference. Click **Finish**. 

After you create a goal, it will appear in the **Goals** tab so you can see a quick snapshot of goals created by you and your security team, as well as [manage your goals](doc:manage-goals-and-slas).  
[block:callout]
{
  "type": "info",
  "title": "Note - SLAs must initialize",
  "body": "After creating an SLA, an “Initializing” status might appear in the \"My Goals\" table for a few minutes if the system is analyzing a large data scope."
}
[/block]
#Add a Goal Card on the Dashboard
After creating a new goal, you can add it to a card to any dashboard. See our [Dashboard](docs/dashboards) help doc for more information. 

Follow these steps: 

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