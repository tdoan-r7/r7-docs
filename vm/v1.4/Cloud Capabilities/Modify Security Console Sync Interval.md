---
title: "Modify Security Console Sync Interval"
excerpt: ""
---
InsightVM customers that have [activated their Security Console on the Insight platform](doc:activating-your-console-on-the-insight-platform) can modify how frequently the console synchronizes with the data stored in the cloud.

# Console and Platform Synchronization Explained

For use with InsightVM, each Insight Agent you have deployed in your organization reports vulnerability data to the Insight platform [every six hours](https://insightagent.help.rapid7.com/docs/data-collected).  Each agent follows its own schedule based on the time it was initially installed.  As a result, the rate at which the platform receives new vulnerability data depends on whether you deployed the agent across your organization individually per asset, all at once, or a combination of both.

By contrast, your Security Console synchronizes with all vulnerability data housed on the Insight platform according to an adjustable hourly interval schedule.

The interval value affects the overall number of agent data packages that are retrieved each sync:

* Shorter intervals direct the Security Console to sync more frequently, but the number of data downloads per sync will be lower given that not all agents will have reported new data during that window.
* Longer intervals functionally allow for a broader window for agents to report new data to the platform.  Interval values configured in this way do not require the Security Console to sync as often, but each sync will have to download a larger number of agent data packages.
[block:callout]
{
  "type": "info",
  "title": "TIP",
  "body": "We recommend that you evaluate the timing of how your deployed agents report to the Insight platform in order to select an interval value that is most effective for your organization."
}
[/block]
# How to Modify the Interval Value
[block:callout]
{
  "type": "warning",
  "title": "REMINDER",
  "body": "Your Security Console must already be [activated on the Insight platform](doc:activating-your-console-on-the-insight-platform) to access this feature."
}
[/block]
**To modify the Security Console synchronization interval:**

1. In your Security Console, click the **Administration** tab in your left navigation menu.
2. In the “Global and Console Settings” section, click **Administer** next to the “Console” label.
3. On the “Security Console Configuration” page, click the **Insight Platform** tab.
4. Next to the “Insight Platform Sync Interval” field, modify the value as desired.
 * Interval options range from 1 to 12 in whole hours.
5. Click **Save** in the upper right corner of the page to save the changes to your Security Console configuration.