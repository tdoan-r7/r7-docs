---
title: "Enabling dashboards"
excerpt: ""
---
As an InsightVM Global Administrator, you have the ability to enable dashboard functionality for your organization. Dashboards are personalized views into your environment that allow users to explore all of your vulnerability management data in one place and can be customized to focus on the information each user cares about. Once the dashboard functionality is enabled, users can access it automatically from their InsightVM consoles: their InsightVM credentials will serve as a single sign-on. To learn more, see [Dashboards](doc:dashboards).

Dashboards are powered by the Rapid7 Insight platform. This means that when you enable dashboards, your organization's data will be synchronized to an AWS cloud instance. Rapid7 takes your security and privacy seriously, and has put measures into place to protect your data security. For more information, see [https://www.rapid7.com/trust/](https://www.rapid7.com/trust/). When enabling dashboards, you will be asked to confirm that you are agreeing to synchronize your organization's data to the cloud.

Your vulnerability and asset data will be synced to the Rapid7 Insight Platform after you activate Exposure Analytics. During the initial syncing, the historical data from the past six months is uploaded to the platform. The uploaded data, which includes your assets, vulnerabilities, and sites, is used to by your dashboards to analyze and monitor trends in your environment. For more information on the data transmitted, see [Data Transmitted to the Insight Platform](doc:enabling-dashboards#section-data-transmitted-to-the-insight-platform). After the initial syncing, your security data will be automatically uploaded to the platform as soon as it is collected and assessed in your InsightVM Security Console.

In order to successfully upload data to the platform, your InsightVM Security Console must be able to create a TCP connection with the following URLs:

* data.insight.rapid7.com
* s3.amazonaws.com
* s3-external-1.amazonaws.com
* exposure-analytics.insight.rapid7.com

If you selected **Europe** (Frankfurt) for the EA deployment, you'll need to whitelist the following URLs:
* eu.data.insight.rapid7.com
* eu.exposure-analytics.insight.rapid7.com
* s3.eu-central-1.amazonaws.com
* s3-eu-central-1.amazonaws.com

If you selected **Asia** (Northeast Asia) for the EA deployment, you'll need to whitelist the following URLS:
* ap.data.insight.rapid7.com
* ap.exposure-analytics.insight.rapid7.com
* s3.ap-northeast-1.amazonaws.com
* s3-ap-northeast-1.amazonaws.com

To enable access to InsightVM dashboards, several conditions must be in place:
* Your InsightVM instance must be licensed with an Enterprise or Ultimate license.

If the above conditions are met, and you are a Global Administrator, you will have the option to enable dashboard functionality. To do so:

1. In the InsightVM console, select the dashboard icon ![Alt](https://files.readme.io/0663c56-s_nx_dashboard_icon.jpg) from the left navigation menu.
2. A welcome screen appears.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/de42f0d-s_nx_dashboard_opt-in_welcome.jpg",
        "s_nx_dashboard_opt-in_welcome.jpg",
        1444,
        922,
        "#2d2f35"
      ]
    }
  ]
}
[/block]
3. Click **Next**.
4. The Exposure Analytics opt-in screen appears. This is where you confirm that you are ready to sync your organization's data to the cloud.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/a0b2265-s_nx_dashboard_opt-in_cloud.jpg",
        "s_nx_dashboard_opt-in_cloud.jpg",
        1844,
        1134,
        "#34363c"
      ]
    }
  ]
}
[/block]
5. To opt in, select **Yes, I am ready**.
[block:callout]
{
  "type": "info",
  "body": "If you select **Maybe later**, the next step will exit you from the dialog. See [Enabling or disabling dashboards from the Administration page](doc:enabling-dashboards#section-enabling-or-disabling-dashboards-from-the-administration-page) for how to enable the feature later when you are ready."
}
[/block]
6. Click **Next**.
7. The **Console name** screen appears.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/d6a53c7-s_nx_dashboard_opt-in_console.jpg",
        "s_nx_dashboard_opt-in_console.jpg",
        1856,
        1322,
        "#2e3035"
      ]
    }
  ]
}
[/block]
8. Specify a name to make it clear to users of the dashboard that the data they are seeing comes from this console.
9. Click **Next**.
10. The **Cloud Region** screen appears.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/ddcf686-s_nx_dashboard_opt-in_cloud_region.jpg",
        "s_nx_dashboard_opt-in_cloud_region.jpg",
        883,
        602,
        "#e3760b"
      ]
    }
  ]
}
[/block]
11. Select the AWS region where your data will be stored.
12. Click **Next**.
13. The main screen of the dashboards appears.

##Enabling or disabling dashboards from the Administration page

Another way to enable dashboards, or to disable them, is from the Administration page. This is how you can enable dashboards if you initially opted out in the process described above.

Disabling dashboards

To have access to this section, the following conditions must apply:
* Your InsightVM instance must be licensed with an Enterprise or Ultimate license.
* You must be a Global Administrator for your InsightVM installation.
* To learn more about this feature and activation, please visit [http://www.rapid7.com/nexpose-now](http://www.rapid7.com/nexpose-now).

To enable dashboards from the Administration page:
1. On the _Administration_ page, select **Administer** next to Console.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/52e2a69-s_nx_console_administer.jpg",
        "s_nx_console_administer.jpg",
        690,
        630,
        "#1e2733"
      ]
    }
  ]
}
[/block]
2. Select **Exposure Analytics** from the left menu.
3. Select **Use Exposure Analytics**.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/1e509f7-s_nx_ea_opt_in.jpg",
        "s_nx_ea_opt_in.jpg",
        1276,
        648,
        "#1a2633"
      ]
    }
  ]
}
[/block]
4. Click **Save**.
5. Select the dashboard icon ![Alt](https://files.readme.io/0663c56-s_nx_dashboard_icon.jpg) from the InsightVM left navigation menu.
6. Proceed according to the instructions above.

To disable dashboards from the Administration page:
1. On the _Administration_ page, select **Administer** next to Console.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/2623e72-s_nx_console_administer.jpg",
        "s_nx_console_administer.jpg",
        690,
        630,
        "#1e2733"
      ]
    }
  ]
}
[/block]
2. Select **Exposure Analytics** from the left menu.
3. Select **Do not use Exposure Analytics**.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/dc41052-s_nx_ea_opt_out.jpg",
        "s_nx_ea_opt_out.jpg",
        1278,
        628,
        "#1b2633"
      ]
    }
  ]
}
[/block]
4. A message appears indicating that all data will be removed from the cloud. Select **Disable Exposure Analytics**.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/53f390a-s_nx_ea_opt_out_msg.jpg",
        "s_nx_ea_opt_out_msg.jpg",
        414,
        212,
        "#ecf3f3"
      ]
    }
  ]
}
[/block]
5. Click **Save**.

If you have disabled dashboards, you will still be able to enable them again at a later date as long as the required conditions are still met. Similarly, the option to disable them will remain available once they are enabled.

##Data Transmitted to the Insight Platform

The following types of information are transmitted to the Insight platform:
* Asset information
* Asset groups
* Asset owners
* Vulnerabilities
* Vulnerability exceptions
* Tags
* Scan Engine information
* InsightVM Console information

InsightVM does not transmit user or service credentials of any kind to the Insight platform.