---
title: "Setting up scan alerts"
excerpt: ""
---
When a scan is in progress, you may want to know as soon as possible if certain things happen. For example, you may want to know when the scan finds a severe or critical vulnerability or if the scan stops unexpectedly. You can have the application alert you about scan events that are particularly important to you.

This feature is not a required part of the site configuration, but it's a convenient way to keep track of your scan when you don't have access to the Security Console Web interface or are simply not checking activity on the console.
[block:callout]
{
  "type": "info",
  "body": "Alerts are sent in cleartext and are not encrypted."
}
[/block]
If you want to add an alert for an existing site, click that site's **Edit** icon in the _Sites_ table on the _Home_ page.

If you want to add an alert while creating a new site, click the **Create site** button on the _Home_ page.
OR
Click the **Create** tab at the top of the page and then select _Site_ from the drop-down list.

To set up alerts:

1. Click the **Alerts** tab of the _Site Configuration_.
2. Click **Create alert**.
The _New Alert_ form appears.
3. The **Enable** check box is selected by default to ensure that an alert is generated. You can clear the check box at any time to disable the alert if you prefer not to receive that alert temporarily without having to delete it.
4. Enter a name for the alert.
5. Enter a value in the _Maximum Alerts to Send_ field if you want to limit the number of this type of alert that you receive during the scan.
6. Select the check boxes for types of events that you want to generate alerts for.
For example, if you select **Paused** and **Resumed**, an alert is generated every time the application pauses or resumes a scan.
7. Select a severity level for vulnerabilities that you want to generate alerts for. For information about severity levels, see [Viewing active vulnerabilities](doc:working-with-vulnerabilities#section-viewing-active-vulnerabilities) .
8. Select the **Confirmed**, **Unconfirmed**, and **Potential** check boxes to receive those alerts.
[block:callout]
{
  "type": "info",
  "body": "If a vulnerability can be verified, a “confirmed” vulnerability is reported. If the system is unable to verify a vulnerability known to be associated with that asset, it reports an “unconfirmed” or “potential” vulnerability. The difference between these latter two classifications is the level of probability. Unconfirmed vulnerabilities are more likely to exist than potential ones, based on the asset’s profile."
}
[/block]
9. Select a notification method from the drop-down box. Alerts can be sent via SMTP e-mail, SNMP message, or Syslog message. Your selection will control which additional fields appear below this box.
[block:callout]
{
  "type": "warning",
  "title": "Specifying multiple recipients with SMTP",
  "body": "The _Recipient E-mail Addresses_ field can accommodate multiple entries.  Validation requirements are as follows:\n\n* At least one recipient must be specified.\n* Each recipient must be a valid e-mail address.\n* Multiple recipients must be delimited by either a comma or a new line."
}
[/block]

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/bee7411-scan_alert_multiple_recipients.png",
        "scan_alert_multiple_recipients.png",
        1849,
        918,
        "#a0a6ab"
      ],
      "caption": "Creating an alert"
    }
  ]
}
[/block]

[block:callout]
{
  "type": "info",
  "body": "Alerts work best when they are targeted and setting multiple can feel overwhelming."
}
[/block]