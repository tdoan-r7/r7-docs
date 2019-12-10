---
title: "Enabling Remote Registry Activation"
excerpt: ""
---
Remote Registry is a Windows service which allows a non-local user to read or make changes to the registry on your Windows system when they are authorized to do so. Users may configure a site to temporarily enable Remote Registry on all Windows devices as they are being scanned. This allows information to be retrieved from the registry and means Nexpose can collect more accurate data from the assets.

In the site configuration, a user will need to add credentials that have appropriate permissions on the target systems to read from the registry. Once the scan is complete, the Remote Registry service will be returned to its prior state. Only a Global Administrator or Administrator may enable the Remote Registry Activation.

To enable Remote Registry for a given site:

1. Navigate to the Site for which you would like to enable Remote Registry.
2. Click the **Edit Site** link.
3. Navigate to the _Template_ tab of the _Site Configuration_ page.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/b6987a4-RR1.png",
        "RR1.png",
        2880,
        1440,
        "#1f2a37"
      ]
    }
  ]
}
[/block]
4. Under the _Select Scan Template_ section, copy an existing template using the icons at the end of the table row (or edit a custom template).
5. In the new window showing the _Scan Template Configuration_ options, enable the check box marked **Allow Nexpose to enable Windows Services**.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/cf51675-rr2.png",
        "rr2.png",
        2878,
        1418,
        "#1d2733"
      ]
    }
  ]
}
[/block]
6. Read the warning and click the **Yes** button.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/6290171-rr3.png",
        "rr3.png",
        828,
        368,
        "#2b3942"
      ]
    }
  ]
}
[/block]
7. Click the **Save** button.

To disable Remote Registry for a site, an authorized user can update the template that is being used for a site in the site configuration or select a different scan template that does not have the option switched on.