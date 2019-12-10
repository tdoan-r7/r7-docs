---
title: "Adding assets to sites"
excerpt: ""
---
An asset is a single device on a network that the application discovers during a scan. In order to perform a scan on a site, you must assign assets to it.

* If you want to add or remove assets to an existing site, click that site's **Edit** icon in the _Sites_ table on the _Home_ page.
* If you want to add assets while creating a new site, click the **Create site** button on the _Home_ page.
[block:callout]
{
  "type": "info",
  "body": "Not all sites can be edited for target assets.  For example, sites created through dynamic discovery connections are assigned assets based on third-party integrations.  See [Managing dynamic discovery of assets](doc:managing-dynamic-discovery-of-assets) for more information.",
  "title": "TIP"
}
[/block]
Click the **Assets** tab in the _Site Configuration_. 

You can either manually input your assets or asset groups, or specify a connection that discovers assets.
[block:callout]
{
  "type": "warning",
  "body": "Switching between **Name/Address** and **Connections** methods will delete any unsaved assets that have been included for scanning. Also, refreshing your browser will remove unsaved assets."
}
[/block]

[block:callout]
{
  "type": "info",
  "body": "After you save a site, you cannot change the method for specifying assets. For example, if you specify assets with a discovery connection and then save the site, you can not manually add IP addresses or host names afterward."
}
[/block]
## Specifying assets by Names/Addresses

Use this method to create a site that scans a manually specified collection of assets or asset groups. Such sites work best for scanning environments that have non-virtual assets and do not often change. You can specify individual assets, ranges, asset groups, or a mixture.

## Adding individual assets or ranges

Use this method to specify individual assets or ranges of assets. You can use only this method, or also add asset groups to the same site.

To add assets:

1. Click the **Names/Addresses** button.
2. Enter host names, IP addresses, or ranges in the _Assets_ text box in the _Include_ section. To expand the text box, hover over the right corner and select the pencil icon. This allows you to edit or remove multiple assets at a time.  Use any of the following notations Each target can be separated by either typing a comma or **Enter** after each asset or range:


 * 10.0.0.1
 * 10.0.0.1 - 10.0.0.255
 * 10.0.0.0/24
 * 2001:db8::1
 * 2001:db8::0 - 2001:db8::ffff
 * 2001:db8::/112
 * 2001:db8:85a3:0:0:8a2e:370:7330/124
 * www.example.com


   IPv6 addresses can be fully compressed, partially uncompressed, or uncompressed. The following are equivalent:


 * 2001:db8::1
 * 2001:db8:0:0:0:0:0:1
 * 2001:0db8:0000:0000:0000:0000:0000:0001


   If you use CIDR notation for IPv4 addresses (x.x.x.x/24) the Network Identifier (.0) and Network Broadcast Address (.255) will be ignored, and the entire network is scanned.


 * 10.0.0.0/24 will become 10.0.0.1 - 10.0.0.254
 * 10.0.0.0/16 will become 10.0.0.1 - 10.0.255.254


You also can import a comma- or new-line-delimited ASCII-text file that lists IP address and host names of assets you want to scan by clicking **Choose File** or **Browse**, depending on your browser.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/ddeba51-s_nx_site_config_add_assets.jpg",
        "s_nx_site_config_add_assets.jpg",
        1839,
        686,
        "#212c3b"
      ],
      "caption": "Specifying assets by names or IP addresses"
    }
  ]
}
[/block]
If you don't want to scan certain assets, enter their names or addresses in the _Exclude_ pane. You may, for example, want to avoid scanning a specific asset within an IP address range either because it is unnecessary to scan, as with a printer, or it may require a different template or scan window than other assets in the range. The same format notations apply.

3. Configure any other site settings as desired.
4. Click **Save** or **Save & Scan** in the _Site Configuration_, depending on your preference.


**Tip:**  For a list of your assets that you can copy to your clipboard, click ![Alt](https://files.readme.io/0b92a62-i_nx_text_box.jpg "Text box icon")next to the **Browse** button.

## Adding asset groups

Use this method to scan one or more asset groups that you have previously created based on logical groupings. You can also combine the asset groups with individually specified assets or a range, as described above. You can either scan all the assets with the same Scan Engine or pool, or scan them each with the Scan Engine that was most recently used to scan the asset. To learn more, see the [Scan Engines](doc:selecting-a-scan-engine-for-a-site) page.

To add asset groups:

1. Click the **Names/Addresses** button.
In the _Asset Groups_ text box in the _Include_ section, begin typing the name of the asset group. As you type, matching suggestions will populate automatically. Select the asset group.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/5a8b77d-s_nx_adding_asset_group_to_site.jpg",
        "s_nx_adding_asset_group_to_site.jpg",
        1839,
        1057,
        "#202b3a"
      ],
      "caption": "Adding an asset group to a site"
    }
  ]
}
[/block]
If you don't want to scan certain assets, enter their names or addresses in the _Exclude_ pane. You may, for example, want to avoid scanning a specific asset within an IP address range either because it is unnecessary to scan, as with a printer, or it may require a different template or scan window than other assets in the range. The same format notations apply.

3. Configure any other site settings as desired.
4. Click **Save** or **Save & Scan** in the _Site Configuration_, depending on your preference.

## Adding assets by connection

Use this method to create a site in which the Security Console discovers assets via a connection with a server that manages those assets. Asset membership in a site created this way is subject to change under any of the following conditions:

* the discovery connection changes
* filter criteria for asset discovery change
* assets are added to or removed from the environment managed by the connection server

Such sites are ideal for scanning Amazon Web Services (AWS) and virtual assets managed by VMware vCenter or ESX/ESXi. Asset membership in a site is subject to change if the discovery connection changes or if filter criteria for asset discovery change.

For information on different types of discovery connections and best practices see [Managing dynamic discovery of assets](doc:managing-dynamic-discovery-of-assets).