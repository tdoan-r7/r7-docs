---
title: "Configure Email Notifications"
excerpt: ""
---
This feature provides email notification functionality for a limited number of events within InsightAppSec. Specifically, users are notified by email if the following events occur:
  * A scan has failed
  * A scan is awaiting bootstrap authentication
  * An on-premises engine has gone offline

The currently implemented security levels in InsightAppSec apply to notifications:
  * Admins receive all emails, where opted in
  * Users with access to an app receive all emails specific to that app where opted in
  * Users without access to an app do not receive emails from that app regardless of whether they are opted in

Customers can enable or disable these email notifications by making changes in the notification preferences screen. Each user of InsightAppSec can set their own preferences, which are accessible by clicking on their profile icon in the upper right of the application header.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/02ff1af-Screen_Shot_2019-02-03_at_5.19.48_PM.png",
        "Screen Shot 2019-02-03 at 5.19.48 PM.png",
        1474,
        940,
        "#404d59"
      ]
    }
  ]
}
[/block]
# Failed Scan
You might run scans at times of low user activity such as evenings or weekends. Email notifications of failed scans inform you of any issues with the scan without the need 
Recipients: All users who have access to the app in which the scan runs. Users with no access to the app do not receive an email.
# Scan Awaiting Bootstrap
A scan may take several hours and may need bootstrap authentication at several locations. The user can log out of InsightAppSec while the scan is running and is notified by email when authentication is required. The email contains a direct link to the running scan.
Recipients: All users who have access to the containing app and all users with this email notification enabled.
# Engine Offline
This scenario may have serious knock-on effects for scheduled scanning. Users are emailed when this occurs so that they can troubleshoot the problem. All users who have this option enabled are notified that the engine is offline, regardless of their level of access.
Recipients: All users who have this email notification enabled. Offline engines are not app specific.