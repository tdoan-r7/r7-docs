---
title: "AWS Security Hub"
excerpt: ""
---
Amazon Web Services (AWS) Security Hub features an integration with Rapid7 InsightVM. Configure this integration to utilize the following benefits: 

  * View and manage security findings collected by Rapid7 in the AWS environment and your InsightVM console
  * Quickly identify high priorities, get guidance to resolve these issues, respond to issues, and identify critical security trends in a single place

# Pricing Model
During the preview period, AWS Security Hub is temporarily free, with access to all features at an unlimited scale. For more pricing details, refer to [AWS Security Hub's pricing plans](https://aws.amazon.com/security-hub/pricing/).

# Before You Start
Please confirm that you meet the requirements for both AWS Security Hub and InsightVM. 

## AWS Subscription
Since AWS Security Hub gathers security findings from AWS services, you must subscribe to at least one of the services below: 
  * Amazon GuardDuty
  * Amazon Inspector
  * Amazon Macie
[block:callout]
{
  "type": "info",
  "title": "NOTE",
  "body": "If you do not have an account to one of the AWS services mentioned above, you cannot access AWS Security Hub."
}
[/block]
## AWS Security Hub Supported Regions
In addition to subscribing to one or more of the above AWS services, you must be located in an AWS Security Hub supported region. Check [this list](https://docs.aws.amazon.com/securityhub/latest/userguide/securityhub-regions.html) to confirm AWS Security Hub availability. 
[block:callout]
{
  "type": "info",
  "title": "NOTE",
  "body": "AWS Security Hub must be enabled in the same AWS region as your InsightVM instance in order for the integration to work."
}
[/block]
## InsightVM Integration Requirements
After confirming you meet the AWS requirements, ensure you meet either one of the InsightVM requirements below:  

  * Agent 2.1 or later is deployed in AWS
  * You use AWS Discovery Connection v2 (console version v6.5.43 or later, released on 11/28/18)

## Enable and Set Up AWS Security Hub 
After confirming you meet the AWS Security Hub requirements, access your free [AWS Security Hub preview](https://aws.amazon.com/security-hub/) and follow the instructions to opt into InsightVM via the providers’ page in the Security Hub console. You can also refer to [Setting Up AWS Security Hub](https://docs.aws.amazon.com/securityhub/latest/userguide/securityhub-settingup.html) in the user guide. 

## Enable AWS Security Hub in InsightVM
After enabling AWS Security Hub, you must integrate InsightVM. To do this, follow these steps: 
1. In your InsightVM console, click **Management** in the left nav.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/4635db3-Screen_Shot_2018-12-20_at_5.42.06_PM.png",
        "Screen Shot 2018-12-20 at 5.42.06 PM.png",
        184,
        297,
        "#3d4047"
      ]
    }
  ]
}
[/block]
2. Under Asset Data, navigate to AWS Security Hub and click **Add**.  
3. Slide toggle to the right to enable AWS Security Hub.
4. Click **Save**.
5. **Close** the panel. 
[block:image]
{
  "images": [
    {
      "image": []
    }
  ]
}
[/block]

[block:callout]
{
  "type": "info",
  "title": "NOTE",
  "body": "You can only add one instance of Security Hub in your InsightVM console."
}
[/block]
# Get Started with AWS Security Hub
Visit these AWS Security Hub resources to learn more:
  * [AWS Security Hub](https://aws.amazon.com/security-hub/) website
  * [AWS Security Hub User Guide](https://docs.aws.amazon.com/securityhub/latest/userguide/what-is-securityhub.html) 

This article will refer to the [AWS Security Hub User Guide](https://docs.aws.amazon.com/securityhub/latest/userguide/what-is-securityhub.html).

## Concepts and Terminology 
To make the most of AWS Security Hub, it is helpful to learn the key concepts listed below: 

  * **Finding** - A security issue that is collected by AWS Security Hub. It can be discovered by AWS or a third-party service, like Rapid7. 
  * **Insight** - A group of related findings defined by an aggregation statement and optional filters. An insight identifies high priority items.
  * **Standards** - A predefined group of rules based on security industry and AWS best practices which is used to measure compliance.  

For more information, refer to [AWS Security Hub Terminology and Concepts](https://docs.aws.amazon.com/securityhub/latest/userguide/securityhub-concepts.html). 

# Work in AWS Security Hub
There are several ways to see and prioritize security issues. The Security Hub dashboard shows a snapshot of your insights prioritized by severity. You can also build and designate a “my favorites” insight group that contains AWS and partner insights. 

## View InsightVM Data in Security Hub
After setting up AWS Security Hub and enabling InsightVM in the Security Console, configure Security Hub to display view your findings. To do so, follow these steps: 

1. Login to AWS Security Hub.
2. Click **Findings** in the left navigation.
3. In the search box, type "Company name EQUALS 'Rapid7.'"
4. Click **Apply**. 
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/681f20f-image_6.png",
        "image (6).png",
        977,
        286,
        "#f4f3f2"
      ]
    }
  ]
}
[/block]

[block:callout]
{
  "type": "info",
  "title": "NOTE",
  "body": "“Rapid7” is case-sensitive."
}
[/block]
After completing this process, you can view your InsightVM findings. Security Hub provides the following information:

  * The **Summary** page is a dashboard that provides a high-level overview and visualizations of your findings in Security Hub.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/05276fd-Summary.png",
        "Summary.png",
        1919,
        1055,
        "#e4e9ec"
      ]
    }
  ]
}
[/block]
  * The **Investigate** page lists insights, which are aggregated groups of findings. You can filter your findings by adding a query and can prioritize your remediation efforts by severity, title, status, or “last seen.” 
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/fe908f5-Investigate.png",
        "Investigate.png",
        1917,
        1055,
        "#ebecee"
      ]
    }
  ]
}
[/block]
  * Clicking on an individual finding shows more detail in a new pane.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/91be4fc-Google_Chrome.png",
        "Google_Chrome.png",
        1921,
        1028,
        "#efeff0"
      ]
    }
  ]
}
[/block]
## Use Managed and Custom Insights
AWS Security Hub provides managed insights, which are non-editable or deletable templates that help you identify security risks. If you need to create a template that is unique to your AWS environment and usage, create a custom insight. For more information, see [Insights in AWS Security Hub](https://docs.aws.amazon.com/securityhub/latest/userguide/securityhub-insights.html) in the User Guide. 

## Manage Security Hub Findings
To help you manage your security hub findings, you can apply filters to prioritize, organize, or archive them. For more information, see [Findings in AWS Security Hub](https://docs.aws.amazon.com/securityhub/latest/userguide/securityhub-findings.html) in the User Guide. 

## Manage AWS Accounts in AWS Security Hub
You can invite and enable multiple accounts to AWS Security Hub. When other accounts accept your invitation, your AWS Security Hub becomes the master account. The associated accounts become member accounts. For more information, see [Managing AWS Accounts in AWS Security Hub](https://docs.aws.amazon.com/securityhub/latest/userguide/securityhub-accounts.html) in the User Guide. 

## Disable AWS Security Hub
To disable AWS Security Hub, you will need to remove both connections from: 
  * InsightVM 
  * AWS Security Hub

### Disable InsightVM
You can either disable or delete the Security Hub from the InsightVM console. Follow these steps to disable: 
1. In your InsightVM console, click **Management** in the left nav.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/47395cf-Screen_Shot_2018-12-20_at_5.42.06_PM.png",
        "Screen Shot 2018-12-20 at 5.42.06 PM.png",
        184,
        297,
        "#3d4047"
      ]
    }
  ]
}
[/block]
2. Under Asset Data, click **AWS Security Hub**.  
3. Click **Edit**. 
4. Slide toggle to left to disable AWS Security Hub.
5. Click **Save**.
6. **Close** the panel. 

To delete the Security Hub, follow these steps: 
1. Follow steps 1 - 2 above. 
2. Click **Delete**. 
3. **Close** the panel. 

### Disable AWS Security Hub
After disabling InsightVM, disable AWS Security Hub. Do so in the Security Hub console or via the DisableSecurityHub API operation. If you disable Security Hub, your existing findings, insights, and configuration are lost permanently, including your master account and its associated accounts. 
[block:callout]
{
  "type": "info",
  "body": "Save existing findings by exporting them before disabling Security Hub.",
  "title": "NOTE"
}
[/block]
However, you can save your existing findings, by exporting them before disabling Security Hub. For more information, see [Disabling AWS Security Hub](https://docs.aws.amazon.com/securityhub/latest/userguide/securityhub-disable.html) in the User Guide. 

# AWS Security Hub Support
If you don’t see any findings in Security Hub and you have met the following conditions, contact [Rapid7 support](https://www.rapid7.com/for-customers/): 

  * Enabled InsightVM findings in AWS Security Hub
  * Deployed an agent in AWS
  * Enabled AWS Security Hub in the InsightVM console

For any other AWS Security Hub issues, contact [AWS](https://aws.amazon.com/contact-us/).