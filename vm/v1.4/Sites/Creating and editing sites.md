---
title: "Creating and editing sites"
excerpt: ""
---
In this section you will learn how to create and configure sites. If you are a new user, you will learn how to create your first basic site. Experienced users can find information on more advanced practices and configurations.

Topics include:

* [Getting started: Info & Security](doc:creating-and-editing-sites#section-getting-started-info-security)
* [Adding assets to sites](doc:adding-assets-to-sites)
* [Configuring scan credentials](doc:configuring-scan-credentials)
* [Configuring scan authentication on target Web applications](doc:configuring-scan-authentication-on-target-web-applications)
* [Selecting a scan template](doc:selecting-a-scan-template) 
* [Scan Engines](doc:selecting-a-scan-engine-for-a-site)
* [Setting up scan alerts](doc:setting-up-scan-alerts)
* [Scheduling scans](doc:scheduling-scans) 
* [Site creation scenarios](doc:site-creation-scenarios)
* [Managing dynamic discovery of assets](doc:managing-dynamic-discovery-of-assets) 
[block:callout]
{
  "type": "info",
  "body": "Not all of the procedures described are required for every kind of site. The site name is the only required field when saving a site.",
  "title": "TIP"
}
[/block]
If you want to edit an existing site, click that site's **Edit** icon in the _Sites_ table on the _Home_ page.

If you want to create a new site, click the **Create** tab at the top of the page and then select _Site_ from the drop-down list.
OR
Click the **Create Site** button at the bottom of the _Sites_ table.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/3c38b9f-s_new_static_site_edit.jpg",
        "s_new_static_site_edit.jpg",
        2126,
        1512,
        "#f0f4f5"
      ],
      "caption": "Starting to create or edit a site"
    }
  ]
}
[/block]
Click the tabs in the _Site Configuration_ to configure various aspects of your site and scans:

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/ecf146a-nexpose_site_config_anatomy.jpg",
        "nexpose_site_config_anatomy.jpg",
        1239,
        522,
        "#313b44"
      ]
    }
  ]
}
[/block]
## Getting started: Info & Security

The **Save** button is enabled as soon as you give the site a name.  The **Save & Scan** button will become available after you have specified at least one target asset.

1. On the _Site Configuration – Info & Security_ tab, type a name for your site.
   **Tip:** You may want to name your site based on how the assets within that site are grouped. For example, you could name them based on their locations, operating systems, or the types of assets, such as those that need to be audited for compliance.
2. Type a brief description of the site.
3. Select a level of importance from the drop-down list:
   * The _Very Low_ setting reduces the risk index to 1/3 of its initial value.
   * The _Low_ setting reduces the risk index to 2/3 of its initial value.
   * _High_ and _Very High_ settings increase the risk index to twice and 3 times its initial value respectively.
   * A _Normal_ setting does not change the risk index.
   The importance level corresponds to a risk factor used to calculate a risk index for each site. See [Adjusting risk with criticality](doc:adjusting-risk-with-criticality).
5. Add business context tags to the site. Any tag you add to a site will apply to all of the member assets. For more information and instructions, see [Applying RealContext with tags](doc:applying-realcontext-with-tags).
6. Click **Organization** to enter your company information. These fields are used in PCI reports.

For more information on managing user access, see [Giving users access to a site](doc:giving-users-access-to-a-site).