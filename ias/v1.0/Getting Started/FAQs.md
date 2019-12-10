---
title: "FAQs"
excerpt: "Common scenarios and how to handle them"
---
## How do I test different types of protocols separately (such as HTTP and HTTPS)

Create one app. Create multiple scan configurations associated with that app,  but using different protocols (for example, one using HTTP and one using HTTPS). This way you can scan the different variations separately but still track them as part of the same app.

## How do I test for a specific category of vulnerabilities (such as SQL injection attacks)

Create one app. Create multiple scan configurations associated with that app. On one of them you can create a custom attack template that addresses the specific types of vulnerabilities you want to find. 

## How do I manage access to InsightAppSec and to specific apps within it.

Select the administration menu from the left navigation. 

Under User Accounts, you can create and manage users and permissions.

##  How do I view details of a vulnerability

Select the line in the table in which the vulnerabilty appears. A drawer panel will slide out on the right side of the screen containing details about the vulnerability, including information about the specific attack vectors. You also have the option to change items such as the severity and status.