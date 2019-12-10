---
title: "Notifications"
excerpt: ""
---
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/258c88d-automation_notificationtab.png",
        "automation_notificationtab.png",
        506,
        109,
        "#2f3840"
      ]
    }
  ]
}
[/block]
Automations of the Notification type can provide your security team with instant updates on detected changes affecting your network’s assets and their vulnerabilities.

This page will guide you through the Notification creation wizard and will detail the management of your Notifications through the dedicated **Notifications** view.

* [Notification wizard](doc:notifications#section-notification-wizard)
* [Management](doc:notifications#section-management)
* [Notification details](doc:notifications#section-notification-details)
* [Recipient preferences](doc:notifications#section-recipient-preferences)

# Notification wizard

To create a Notification:

1. Navigate to the **Automation** tab on your left menu.
2. On the “Automation” page, click the **Notifications** tab.
3. In the upper right corner, click **+ New Automation**.
 * If you don’t have any Notifications yet, this button will also be available from the center of your screen.
4. On the first step of the wizard, select the **Notification** Automation type and click **Continue**.
5. Select a trigger type for your Notification.  All Automations trigger on assets or vulnerabilities affecting those assets.
6. Apply a filter for your selected trigger type.  See the [Query filter guide](doc:query-filter-guide) for instructions and operator descriptions.
 * You can preview your filter results by expanding the trigger type dropdown list.  Click the **\>** next to your filter results number to open it.
[block:callout]
{
  "type": "warning",
  "title": "The Vulnerability trigger type requires two filters",
  "body": "If you select **Vulnerability** as your trigger type, you must apply both an asset filter and a vulnerability filter.  Automations that respond to vulnerability changes have to know what subset of assets are being considered."
}
[/block]
7. Review your configured trigger for accuracy.  Click **Continue** when ready.
8. Click the pencil icon to change the name of your Notification to something your security team will recognize.
9. Select a Notification method.
 * You can choose between an email distribution or text messaging via SMS.
[block:callout]
{
  "type": "warning",
  "title": "NOTE",
  "body": "Given the character limitations of SMS messages, Notifications configured with the SMS delivery method will only contain summarized content.\n\nIf you receive an SMS Notification, browse to its corresponding [“Notification Details”](doc:notifications#section-notification-details) page to download its full contents."
}
[/block]
10. Specify who will receive the Notification.
 * You can customize an email distribution with both internal and external addresses in the provided field.
11. Specify a Notification time and interval.
12. Click **Continue** when finished.

Your configured Notification will now appear in the “Notifications” table.

# Management

You can manage your configured Notifications from the dedicated **Notifications** tab on the “Automation” page.

## Filters

Similarly to the consolidated **History** tab, the **Notifications** tab view includes its own filtering capability tailored for Notification traits.

## "Notifications" table

All your configured Notifications are listed here, sortable by several columns.  Any filters you have applied will affect the entries shown on this table.

### Status

You can quickly enable or disable your configured Notifications using the sliders in the “Status” column.  The Notification is considered active when the slider is in the green position.

### Edit, Copy, and Delete

Individual Notification rows will show additional icons towards the right side of your screen.
[block:parameters]
{
  "data": {
    "0-0": "Pencil",
    "0-1": "Click here to open your Notification in the wizard and make any necessary changes.",
    "h-0": "Icon",
    "h-1": "Function",
    "1-0": "Trash can",
    "1-1": "Click here to delete your Notification.  Deletions must be confirmed before they go through."
  },
  "cols": 2,
  "rows": 2
}
[/block]
# Notification details

Click the name link of any Notification on the table to see the “Notification Details” page.  This view displays general information based on the Notification’s configuration.

## “Notification History” table

This table will keep a record of every trigger instance of your Notification, and will include data on whether it succeeded or failed, when it started, and a failure reason, if applicable.

Applicable filters on the “Notification Details” page are tailored for these table traits.

### CSV export

Notification data is retrieved in CSV format.  Download CSV exports of individual trigger instances to see their asset and vulnerability information in detail.

Click **Export to CSV** under the “Events” column to create an export for that trigger instance.
[block:callout]
{
  "type": "warning",
  "title": "NOTE",
  "body": "Your historical Notification trigger instances will expire after 30 days."
}
[/block]
# Recipient preferences

Recipients of email Notifications can adjust their subscription directly from the email itself.

1. Open any Notification email and click **Unsubscribe from this Notification** at the bottom of the page.
2. On the “Email preferences” page, check the box next to the Notification name if you wish to unsubscribe.
3. Click **Update**.

Alternatively, you can elect to unsubscribe from all email communication from insight_noreply@rapid7.com.  Click **Unsubscribe** to do so.
[block:callout]
{
  "type": "danger",
  "title": "WARNING",
  "body": "Unsubscribing from all email communication will prevent you from receiving any newly configured Notifications in the future.\n\nIf you choose to unsubscribe, make sure you communicate this to your Automation administrator."
}
[/block]