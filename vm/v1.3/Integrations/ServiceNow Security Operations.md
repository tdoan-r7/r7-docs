---
title: "ServiceNow Security Operations"
excerpt: ""
---
#Overview

To help streamline vulnerability remediation, this API integration processes and prioritizes vulnerabilities by incorporating InsightVM data into ServiceNow Security Operations dashboards and analytics. 

##Integration Overview

Here’s a high-level overview of how this integration works: 

1. InsightVM scans the environment to assess risk within organizational systems and processes the vulnerability data.
2.  ServiceNow Security Operations (SecOps) periodically queries InsightVM for the latest vulnerabilities. 
3.  ServiceNow creates remediation tickets for vulnerabilities and closes tickets that have been fixed.
4.  With the next query of InsightVM, ServiceNow checks closed tickets for successful remediation. 

With ServiceNow integrated, you can:
  * Import Rapid7 InsightVM scan data directly into ServiceNow Security Operations.
  * Gain more context and visibility into individual vulnerabilities and overall risk. 
  * Reduce exposure time through data-centric collaboration between IT Operations and Security.
  * Maximize output while minimizing effort through an automated and closed-loop workflow.
  * Deploy easily by accessing the Rapid7 integration for Security Operations in the ServiceNow Marketplace.

#Whitelist Platform Traffic

The integration uses the following hostnames to communicate with the Insight platform:

[block:parameters]
{
  "data": {
    "h-0": "Region",
    "h-1": "Hostname",
    "0-0": "United States",
    "1-0": "Europe",
    "2-0": "Canada",
    "3-0": "Japan",
    "4-0": "Australia",
    "4-1": "au.api.insight.rapid7.com",
    "3-1": "ap.api.insight.rapid7.com",
    "2-1": "ca.api.insight.rapid7.com",
    "1-1": "eu.api.insight.rapid7.com",
    "0-1": "us.api.insight.rapid7.com"
  },
  "cols": 2,
  "rows": 5
}
[/block]
In order for ServiceNow to transmit data, you must configure your network to allow traffic to the corresponding hostname of your designated InsightVM region.
[block:callout]
{
  "type": "info",
  "title": "NOTE",
  "body": "The region you chose for your integration must match the region that has been selected previously in InsightVM. If you select an incorrect region, data will not populate."
}
[/block]
#Install and Configure

Complete the following steps to configure your ServiceNow SecOps integration:
1. Generate a Rapid7 API key.
2. Install and configure the SecOps integration.

##Generate a Rapid7 API Key

Complete the following steps to configure your ServiceNow SecOps integration: 

To use the SecOps integration, you need a Rapid7 API key, which you generate from the Rapid7 Insight platform.

In order to access the Rapid7 platform, you will need a Rapid7 Insight platform account, which is different from your InsightVM Rapid7 Security Console account.

Here's how to get a Rapid7 Insight platform account: 
*  If you are an InsightIDR, InsightAppSec, InsightOps, or InsightConnect customer, you already have a Rapid7 Insight platform account. You can link your existing InsightVM Security Console to the Rapid7 Insight platform account you created with your other Rapid7 product by following the instructions here:
https://insightvm.help.rapid7.com/docs/activating-your-console-on-the-insight-platform
*  If you are already using the cloud capabilities of InsightVM and don’t have a Rapid7 Insight platform account, contact the [Rapid7 Technical Support team](https://rapid7support.force.com/customers/login) to request one. 

Follow these steps to generate the Rapid7 API key: 

1. Go to [https://insight.rapid7.com/platform#/ ](https://insight.rapid7.com/platform#/ )
2. Log in to your Rapid7 Insight platform account.  
3. Go to [API Keys](https://insight.rapid7.com/platform#/apiKeyManagement). 
4. Under **User Key**, click on the **New User Key** button. 
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/cec994c-Screen_Shot_2019-03-14_at_11.09.41_AM.png",
        "Screen Shot 2019-03-14 at 11.09.41 AM.png",
        2686,
        686,
        "#eef0f2"
      ]
    }
  ]
}
[/block]
5. In the “Organization” dropdown menu, select your InsightVM organization name.
6. Enter a name for your key in the field. 
7. Click **Generate**. 
8. Copy and save the provided API Key.
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
  "body": "This is the only time you will be able to see the API key, so store it in a safe place. If you misplace your API key, you can always generate a new one."
}
[/block]
9. Click Done. 
10. Your new API key will display in the “User Key” table.

##Install and Configure the ServiceNow API Integration

Before starting, confirm that you meet [ServiceNow system requirements](https://store.servicenow.com/sn_appstore_store.do#!/store/application/8a2aa078e7330300809a268b03f6a988/6.2.0) and that the appropriate regions are whitelisted. After generating your API key, follow these steps to install and configure the ServiceNow integration:

1. Log into your ServiceNow application.
2. Go to “Rapid7 Vulnerability Integration” in the left navigation and select **Configuration**.  
3. Next to “Integration Type,” select “InsightVM” from the dropdown menu. 
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/47f0617-Screen_Shot_2019-03-15_at_1.06.18_PM.png",
        "Screen Shot 2019-03-15 at 1.06.18 PM.png",
        1932,
        555,
        "#c4cbcc"
      ]
    }
  ]
}
[/block]
4. In the “Server URL” field, select the desired region.
5. In the “API Key” field, input the API key collected from the Insight platform.
6. Click **Test credentials** and check the “Validation Status” field to confirm the integration. If valid, **Save**. If invalid, confirm that the required whitelisting is in place and the API key was copied correctly, then repeat Steps 4 - 6 again.

InsightVM data will now appear in ServiceNow to help manage your remediation efforts.