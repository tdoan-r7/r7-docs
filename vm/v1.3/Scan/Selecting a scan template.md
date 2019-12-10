---
title: "Selecting a scan template"
excerpt: ""
---
You may need to scan different types of assets for different types of purposes at different times. A scan **template** is a predefined set of scan attributes that you can select quickly rather than manually define properties, such as target assets, services, and vulnerabilities. For a list of scan templates and suggestions on when to use them, see [Scan templates](doc:scan-templates). InsightVM includes a variety of preconfigured scan templates to help you assess your vulnerabilities according to the best practices for a given need.

Using varied templates is a good idea, as you may want to look at your assets from different perspectives. The first time you scan a site, you might just do a discovery scan to find out what is running on your network. Then, you could run a vulnerability scan using the Full Audit template, which includes a broad and comprehensive range of checks. If you have assets that are about to go into production, it might be a good time to scan them with a Denial-of-Service template. Exposing them to unsafe checks is a good way to test their stability without affecting workflow in your business environment. You may also want to apply different templates to different types of assets; for instance, Web audit for Web servers and Web applications.

A Global Administrator can also customize scan templates or create new ones to suit your organization's particular needs. By creating sites of selected assets and applying the most relevant scan template, you can conduct scans that are specific to your needs. See [Configuring custom scan templates](doc:configuring-custom-scan-templates) for more information. Keep in mind that the scans must balance three critical performance factors: time, accuracy, and resources. If you customize a template to scan more quickly by adding threads, for example, you may pay a price in bandwidth.

## Selecting a scan template

If you want to change the scan template for an existing site, click that site's **Edit** icon in the Sites table on the Home page.

If you want to select the scan template while creating a new site, click the **Create site** button on the Home page.

**Note:** If you created the site through the integration with VMware NSX, you can change the scan template but it will not affect the type of scan or the scan results. See [Integrating NSX network virtualizations with scans](doc:integrating-nsx-network-virtualizations-with-scans).

###Selecting an existing scan template

1. In the _Site Configuration_, go to the _Templates_ tab.
2. Select an existing scan template from the table.
The default is _Full audit without Web Spider_. This is a good initial scan, because it provides full coverage of your assets and vulnerabilities, but runs faster than if Web spidering were included.
3. Save your changes.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/aac08bc-s_nx_scan_template_default.jpg",
        "s_nx_scan_template_default.jpg",
        1979,
        937,
        "#212c3b"
      ],
      "caption": "Default scan template selection"
    }
  ]
}
[/block]
###Creating a new scan template

1. Click the **Copy** icon next to the listed template you want to base the new one on, or click **Create Scan Template** to start from scratch.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/3ea94d4-s_nx_copy_scan_template.jpg",
        "s_nx_copy_scan_template.jpg",
        1986,
        952,
        "#222c3b"
      ],
      "caption": "Copying an existing scan template"
    }
  ]
}
[/block]

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/8420586-s_nx_create_scan_template.jpg",
        "s_nx_create_scan_template.jpg",
        1951,
        949,
        "#222c3b"
      ],
      "caption": "Creating a new scan template"
    }
  ]
}
[/block]
A new tab will open with the _Scan Template Configuration_.

2. Change the template as desired. See [Configuring custom scan templates](doc:configuring-custom-scan-templates) for more information.
3. Click **Save**.
4. Return to the tab with the _Scan Template Configuration_.
5. Click the **Refresh** icon at the top of the _Scan Templates_ table to make the new template appear.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/a53256c-s_nx_site_config_scan_template_refresh.jpg",
        "s_nx_site_config_scan_template_refresh.jpg",
        1979,
        937,
        "#212c3b"
      ],
      "caption": "Refreshing the Scan Templates table display"
    }
  ]
}
[/block]
6. Save your changes.