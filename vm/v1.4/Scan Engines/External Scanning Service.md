---
title: "External Scanning Service"
excerpt: ""
---
[block:callout]
{
  "type": "warning",
  "title": "NOTE - Shared Hosted Scan Engine End-Of-Sale",
  "body": "As of November 18th, 2019, Rapid7 is no longer selling access to **shared** hosted Scan Engines."
}
[/block]
Rapid7 offers access to Scan Engines provisioned through our External Scanning Service in cases where you want to avoid deploying distributed Scan Engines on your own resources.  If your organization is licensed for the External Scanning Service, you must pair the provisioned Scan Engine with your Security Console before you can use it.
[block:callout]
{
  "type": "info",
  "title": "TIP",
  "body": "If you’re not yet licensed for the External Scanning Service, contact your Customer Success Manager to learn more about adding the service to your account."
}
[/block]
The External Scanning Service pairing procedure is different from those required by [distributed Scan Engines](doc:configuring-distributed-scan-engines) since deployment and configuration is done for you. However, [Rapid7 Support](https://www.rapid7.com/for-customers/) must authorize an external Scan Engine before you can scan with it.

This article explains how to provide [Rapid7 Support](https://www.rapid7.com/for-customers/) with the information needed to authorize your external Scan Engine.

# Send Rapid7 Support Your Console Address Information

After you purchase access to an external Scan Engine, you need to add the engine to your “Scan Engines” table.  Finally, [Rapid7 Support](https://www.rapid7.com/for-customers/) needs the IP address of your Security Console in order to authorize the engine for use in your environment.

**To add your engine and send your console address information to Rapid7 Support:**

1. In your Security Console, browse to and click on the **Administration** tab in your left navigation menu.
2. In the “Scan Options” section, click **manage** next to “Engines”.
3. In the “Scan Engines” table, click **New Engine**.
[block:callout]
{
  "type": "info",
  "title": "I already have an engine named “Rapid7 Hosted Scan Engine”.  Should I use that one?",
  "body": "In most cases, no. The “Rapid7 Hosted Scan Engine” entry that comes pre-configured with your Security Console refers to a **shared** hosted Scan Engine that Rapid7 no longer sells.\n\nIf you already scan with a shared hosted Scan Engine, you can continue to do so."
}
[/block]
4. In the “Scan Engine Configuration” page, give your external Scan Engine a name.
 * For easy identification, you can call this engine “Rapid7 External Scanning Service”.
5. Enter the IP address of your engine host provided by Rapid7 as the engine address.
6. Leave the port number as the default of 40814.  Click **Save** when finished.
7. Back in the “Scan Engines” table, locate the engine you just added and click the icon in the “Refresh” column.
8. An error message displays:

```
Cannot refresh scan engine (<Your engine name here>): Unauthorized console connection from: <IP ADDRESS>
```

[block:callout]
{
  "type": "info",
  "title": "Why am I seeing an error?",
  "body": "Don’t be alarmed!  This particular error message is expected and is part of the authorization procedure for external Scan Engines."
}
[/block]

[block:callout]
{
  "type": "warning",
  "title": "What if I’m seeing a different error?",
  "body": "If refreshing your external Scan Engine produces a different error than the one shown here, then continue with the next steps as usual.  [Rapid7 Support](https://www.rapid7.com/for-customers/) needs to see your error message in order to troubleshoot the issue.\n\nIn most cases, errors other than the one expected here are usually due to connectivity issues between your Security Console and the external Scan Engine.\n\nNote that your firewall rules must allow your Security Console to reach the external Scan Engine address shown in step 5 on port 40814.  The use of a proxy to reach your external Scan Engine is not supported."
}
[/block]
9. Write down or take a screenshot of the IP address shown in this error message.
10. Open a case in the [Customer Portal](https://www.rapid7.com/for-customers/) and indicate that you need an external Scan Engine authorized.  Provide (or attach) the error message that includes your console IP address in the case details.

# Maintenance Periods

Rapid7 performs regular maintenance of all External Scanning Service engines and other managed services. This maintenance period takes place every first Wednesday of the month from 10:00 AM EST to 2:00 PM EST. During this period, the following services will be unavailable:

* InsightVM External Scanning Service Scan Engines
* InsightVM Managed Services and PCI/ASV Scanning
[block:callout]
{
  "type": "warning",
  "title": "NOTE",
  "body": "Consider this maintenance period before configuring scan schedules that use external Scan Engines."
}
[/block]
From a statistical standpoint, Wednesday is the lowest usage weekday for External Scanning Service engines compared to the heavier scanning periods that take place on weekends during non-business hours. Based on this data, we have chosen this maintenance period in order to best provide a seamless customer experience while maintaining the level of quality and services that you expect.

If you have concerns about this schedule, or if you would like additional information or recommendations, please reach out to [Rapid7 Support](https://www.rapid7.com/for-customers/).