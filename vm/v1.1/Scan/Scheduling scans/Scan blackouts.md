---
title: "Scan blackouts"
excerpt: ""
---
Scan blackouts allow you to prevent scans from taking place during specified times when you need to keep the network available for other traffic. For example, if your company makes extensive backups on Fridays, you could create a recurring blackout period from 9 am to 9 pm every Friday to prevent scans from running at that time.

There are two types of scan blackouts:

* **Global blackouts** apply throughout your InsightVM workspace. Global blackouts are created and managed from the _Administration_ page. They can only be created and managed by Global Administrators.
* **Site-level blackouts** apply only for specific sites. They are created and managed from the _Site Configuration_. Site-level blackouts can be created and managed by Global Administrators or by Site Managers for that site.

During a blackout period, any scheduled scans will not start. If anyone tries to start a manual scan during a blackout period, they will see a message informing them of the blackout period. Global Administrators will have the option to scan anyway. Others will be unable to proceed with the scan.

If a scan is already in progress when a blackout period begins, the scan will be paused by the system for the duration of the blackout period. The scan will resume once the blackout period is over, in most cases. The exception is if a scheduled scan is paused by the system for a blackout and meets its maximum duration during the blackout period. In that case, the scan duration will take precedence and the blackout duration will not resume.
[block:callout]
{
  "type": "info",
  "body": "Each scan takes approximately 30 seconds to shut down, and the scans shut down sequentially. There will be network activity at the beginning of the blackout period while the scans shut down. If you are creating a blackout period because you cannot have network activity during a certain time period, set the blackout to begin earlier to allow for all the scans to shut down."
}
[/block]
## Creating a site-level blackout

As previously mentioned, in order to create a site-level blackout, you must be a Site Manager for that site, or a Global Administrator.

Before creating a new site-level blackout, you may want to review the existing site-level and global blackouts that may apply to this site. Doing so will help you avoid creating overlapping or conflicting blackouts.

To review existing blackouts that may affect a site:

1. In the _Site Configuration_, go to the **Schedule** tab.
2. In the left navigation, select **Manage Blackouts**.
3. Review the existing blackout periods. The page shows both site-level and global blackouts.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/b9d070b-s_nx_manage_site_blackouts.jpg",
        "s_nx_manage_site_blackouts.jpg",
        2239,
        825,
        "#1f2b3a"
      ],
      "caption": "Viewing existing blackouts that affect a site"
    }
  ]
}
[/block]
To create a site-level blackout:

1. In the _Site Configuration_, go to the **Schedule** tab.
2. In the left navigation, select **Create Blackout**.
3. Specify the desired settings: Start date and time, maximum duration, whether to repeat the blackout, and, if so, a repetition schedule. Select or clear the **Enable blackout** checkbox to determine whether the blackout will take effect.
4. Click **Save** on the _Create Blackout_ page.
5. Click **Save** on the _Site Configuration_.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/530c125-s_nx_create_site_blackout.jpg",
        "s_nx_create_site_blackout.jpg",
        2212,
        911,
        "#1f2a39"
      ],
      "caption": "Creating a site-level blackout"
    }
  ]
}
[/block]
## Managing site-level blackouts

In the _Site Configuration_, Site Managers and Global Administrators can edit site-level blackouts and view global blackouts.

**Note:** If you modify a blackout that is currently in effect, it will be stopped and any running scans will resume.

To manage site-level blackouts:

1. In the _Site Configuration_, go to the **Schedule** tab.
2. In the left navigation, select **Manage Blackouts**.
3. You can view the list of site-level and global blackouts.
   * To enable or disable a site-level blackout, select or clear the **Enable** check box. Global blackouts can only be edited on the **Administration** page by Global Administrators.
   * To edit a site-level blackout, click the start date. Edit the settings. Click **Save** on the _Create Blackout_ page and on the _Site Configuration_.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/5f40284-s_nx_manage_site_blackouts.jpg",
        "s_nx_manage_site_blackouts.jpg",
        2239,
        825,
        "#1f2b3a"
      ],
      "caption": "Managing site level blackouts"
    }
  ]
}
[/block]
## Creating a global blackout

Only Global Administrators can create global blackouts.

Before creating a global blackout, you may want to review the existing global blackouts in order to avoid creating a new one that overlaps or conflicts.

To review existing global blackouts:

1. Go to the _Administration_ page.
2. In _Scan Options_, go to _Global Blackouts_ and select **Manage**.
3. Review the existing global blackout periods.

To create a global blackout:
1. Go to the _Administration_ page.
2. In _Scan Options_, next to _Global Blackouts_, select **Create**.
3. Specify the desired settings: Start date and time, maximum duration, whether to repeat the blackout, and, if so, a repetition schedule. Select or clear the **Enable blackout** checkbox to determine whether the blackout will take effect.
4. Click **Save** on the _Create Blackout_ page.
5. Click _Save Global Blackouts_.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/1281851-s_nx_create_global_blackout.jpg",
        "s_nx_create_global_blackout.jpg",
        2227,
        685,
        "#1a2736"
      ],
      "caption": "Creating a global blackout"
    }
  ]
}
[/block]
## Managing global blackouts

Only Global Administrators can manage global blackouts.

**Note:** If you modify a blackout that is currently in effect, it will be stopped and any running scans will resume.

To manage existing global blackouts:
1. Go to the _Administration_ page.
2. In _Scan Options_, go to _Global Blackouts_ and select **Manage**.
3. Review the existing global blackout periods.

To enable or disable a global blackout:
1. Select or clear the *Enable* check box.
2. Site blackouts can be administered from the _Scan Configuration_ for that site.

To edit a global blackout:
1. Click the start date for the blackout you want to edit.
2. Edit the desired settings: Start date and time, maximum duration, whether to repeat the blackout, and, if so, a repetition schedule. Select or clear the **Enable blackout** checkbox to determine whether the blackout will take effect.
3. Click **Save** on the _Manage Blackouts_ page.
4. Click **Save Global Blackouts**.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/a4aa907-s_nx_manage_global_blackouts.jpg",
        "s_nx_manage_global_blackouts.jpg",
        2208,
        642,
        "#1a2736"
      ],
      "caption": "Managing global blackouts"
    }
  ]
}
[/block]