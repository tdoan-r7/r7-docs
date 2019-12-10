---
title: "Scheduling scans"
excerpt: ""
---
Depending on your security policies and routines, you may schedule certain scans to run on a monthly basis, such as patch verification checks, or on an annual basis, such as certain compliance checks. It's a good practice to run discovery scans and vulnerability checks more often—perhaps every week or two weeks, or even several times a week, depending on the importance or risk level of these assets.

### Best practices for scheduling scans

Scheduling scans requires care. Generally, it’s a good idea to scan during off-hours, when more bandwidth is free and work disruption is less likely. On the other hand, your workstations may automatically power down at night, or employees may take laptops home. In this case, you may need to scan those assets during office hours. Make sure to alert staff of an imminent scan, as it may tax network bandwidth or appear as an attack.

If you plan to run scans at night, find out if backup jobs are running, as these can eat up a lot of bandwidth.

Your primary consideration in scheduling a scan is the scan window: How long will the scan take?

Many factors can affect scan times:

* A scan with an Exhaustive template will take longer than one with a Full Audit template for the same number of assets. An Exhaustive template includes more ports in the scope of a scan.
* A scan with a high number of services to be discovered will take additional time.
* Checking for patch verification or policy compliance is time-intensive because of logon challenges on the target assets.
* A site with a high number of assets will take longer to scan.
* A site with more live assets will take longer to scan than a site with fewer live assets.
* Network latency and loading can lengthen scan times.
* Scanning Web sites presents a whole subset of variables. A big, complex directory structure or a high number of pages can take a lot of time.

If you schedule a scan to run on a repeating basis, note that a future scheduled scan job will not start until the preceding scheduled scan job has completed. If the preceding job has not completed by the time the next job is scheduled to start, an error message appears in the scan log. To verify that a scan has completed, view its status. See [Running a manual scan](doc:running-a-manual-scan).

[block:callout]
{
  "type": "warning",
  "body": "You cannot save a site configuration with overlapping schedules. Make sure any given scan time doesn't even partially conflict with that of another."
}
[/block]
### Scheduling scans to run with different templates

By alternating scan templates in a site, you can check the same set of assets for different needs. For example, you may schedule a recurring scan to run on a fairly routine basis with a template that is specifically tuned for the assets in a particular site. Then you can schedule a monthly scan to run with a special template for verifying Microsoft patches that have been applied after Patch Tuesday. Or you can schedule a monthly or quarterly scan with an internal PCI template to monitor compliance.

### Steps for scheduling a scan

* If you want to set a schedule for an existing site, click that site's **Edit** icon in the _Sites_ table on the _Home_ page.
* If you want to set a schedule while creating a new site, click the **Create site** button on the _Home_ page, or click the **Create** tab at the top of the page and then select _Site_ from the drop-down list.


1. Click the **Schedules** tab of the _Site Configuration_.
2. Click **Create Schedule**.
3. Optionally, you can add a **Name** for the schedule. Since you can use different scan templates and Scan Engines, you can use the name to help yourself and other users keep track of the specific configuration of this schedule.
4. Select the check box labeled **Enable schedule**. The Security Console displays options for a start date and time, maximum scan duration in minutes, and frequency of repetition.
5. Enter a start date in mm/dd/yyyy format, or select a date from the calendar that appears when you click inside the text box.
6. Enter a start time in HH:MM format, and select AM or PM.
7. Select a template for the scheduled scan. See [Scheduling scans to run with different templates](doc:scheduling-scans#section-scheduling-scans-to-run-with-different-templates) for more information.
[block:callout]
{
  "type": "info",
  "body": "If you created the site through the integration with VMware NSX, you cannot use multiple scan templates because the Full Audit is automatically assigned as part of the integration process. See [Integrating NSX network virtualizations with scans](doc:integrating-nsx-network-virtualizations-with-scans)."
}
[/block]
8. Select a Scan Engine for the scheduled scan. This allows you to create your schedules in a way that lets you take advantage of what you know about the availability and performance of your Scan Engines at particular times.
9. Optionally, you can specify a subset of assets to scan. To do so, select the checkbox. Note that these assets must always be among those already included in the site. Including assets or groups here means _only_ the included assets will be scanned in this schedule. This field is required once you choose to scan a subset of assets at all. Excluding assets or groups means those assets will be excluded from the scan in this schedule, in addition to any existing inclusions configured on the site.
[block:callout]
{
  "type": "warning",
  "title": "NOTE",
  "body": "Subset scanning criteria **must** be aligned with how the site is defined.\n\nSites defined by asset group (or groups) can **only** specify _Included Groups_ and _Excluded Groups_ as subset criteria.  Accordingly, sites defined by IP address (or range) can **only** specify _Included_ and _Excluded_ as subset criteria, and only if the specified assets fall within the range defined by the site.\n\nSubset field types cannot be mixed."
}
[/block]
10. If you want to set a maximum duration, enter a numeral for the number of minutes the scan can run. When the scan reaches the duration limit, it will pause. If you don't enter a value, the scan will simply run until it completes.
11. Select an option for what you want the scan to do after reaches the duration limit:
If you select the option to continue where the scan left off, the paused scan will continue at the next scheduled start time.
If you select the option to restart the paused scan from the beginning, the paused scan will stop and then start from the beginning at the next scheduled start time.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/8aaa79a-s_nx_site_config_schedule_scan.jpg",
        "s_nx_site_config_schedule_scan.jpg",
        1000,
        812,
        "#e9e9ea"
      ],
      "caption": "Scheduling a recurring scan"
    }
  ]
}
[/block]
12. To make it a recurring scan, select an option from the **Frequency** dropdown.  Select **Other…** for additional customization options.
13. Click **Save**.
The newly scheduled scan appears in the _Scan Schedules_ table, which you can access by clicking **Manage Schedules**.

**Tip:** You can edit a schedule by clicking its hyperlink in the table.

### Selecting a schedules for a site

You may want to suspend a scheduled scan. For example, a particular set of assets may be undergoing maintenance at a time when a scan is scheduled. You can enable and disable schedules as your needs dictate.

1. Click **Manage Schedules** in the _Schedules_ tab of the _Site Configuration_.
2. Select a check box to enable a schedule, and clear a check box to disable it.
3. Configure any other site settings as desired.
4. Click **Save & Scan** or **Save** depending on your needs.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/9b023e5-s_nx_site_config_select_schedules.jpg",
        "s_nx_site_config_select_schedules.jpg",
        2235,
        712,
        "#1f2a3a"
      ],
      "caption": "Enabling and disabling schedules"
    }
  ]
}
[/block]