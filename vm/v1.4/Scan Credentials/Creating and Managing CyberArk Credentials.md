---
title: "Creating and Managing CyberArk Credentials"
excerpt: ""
---
Credentialed scanning enables you to obtain deeper visibility into your environment by allowing you to access assets on your network to gather information you may not be able to otherwise access. The CyberArk integration enables you to easily run credentialed scans and dynamically assign credentials for authentication to multiple sites by leveraging the CyberArk Vault technology. It allows you to globally manage your privileged accounts without having to provide them directly through the Security Console.

Configuring a credentialed scan with CyberArk as the authentication source is nearly identical to configuring any other type of credentialed scan. Like other credentialed scans, you can set up shared scan credentials to use across multiple sites or credentials that can only be used by a specific site. When the scan runs, a request is made to CyberArk for the credentials that are needed to access the target assets, and CyberArk will provide the requested credentials so that the scan can authenticate to and assess those assets.
[block:callout]
{
  "type": "info",
  "title": "TIP",
  "body": "In the context of this CyberArk credential lookup feature, the \"target assets\" described previously are the assets you have specified in your site configuration using the following methods:\n\n* By IP address\n* By IP address range\n* By hostname\n* By asset group"
}
[/block]
The following sections will help you understand how you can set up CyberArk as an authentication source for credentialed scans.

## Supported Services

CyberArk is a supported authentication source for the following services:

* Microsoft Windows/Samba (SMB/CIFS)
* Secure Shell (SSH)
* Secure Shell (SSH) Public Key
* IBM AS/400

When you add any of these credential types, CyberArk will be available to configure as a credential management source.

You can utilize privilege escalation for SSH, SSH Public Key, for both shared credentials and Site level credentials, when CyberArk is selected for Credential Management.

You can use the Test Credential function to test the escalated credentials.

## Before You Can Add CyberArk as an Authentication Source

Before you can add CyberArk as an authentication source, you'll need to:

* **Register your Security Console with CyberArk** - Any machine that requests passwords must be defined in the CyberArk vault as an application. Registering your Security Console enables the provider to assign an AppID to the console and retrieve passwords for it.
* **Install the CyberArk Application Identity Manager** - The Application Identity Manager, or AIM, must be installed on the same machine as your InsightVM instance.
* **Define the "User DN" field in CyberArk** - Make sure that you fill out the "User DN" field in CyberArk for the account that you want to use for scanning.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/f99d55a-cyberark_userdn_field.png",
        "cyberark_userdn_field.png",
        979,
        685,
        "#f6f4f4"
      ]
    }
  ]
}
[/block]
For help with any of these prerequisites, please visit the CyberArk documentation or contact their support team.

## Understanding CyberArk Vault Options

Adding CyberArk as the authentication source for credentialed scans is a simple process. You can set up CyberArk to provide shared scan credentials to use across multiple sites or credentials that are site-specific. Regardless of the scope of the credential you create, the options that are available for creating them will be the same.

The following table provides descriptions for all the CyberArk Vault options:
[block:parameters]
{
  "data": {
    "h-0": "Option",
    "h-1": "Description",
    "0-0": "AppID",
    "0-1": "The AppID that has been authorized to provide to access to CyberArk and retrieve credentials. This option is required.",
    "1-0": "Lookup Type",
    "1-1": "The method that is used to choose credentials from the vault. You can choose between Static Binding or Dynamic Binding.",
    "2-0": "Lookup Attributes",
    "2-1": "Lookup attributes allow you to specify criteria for the credentials that will be retrieved. You can create a lookup using a combination of the following attributes: the asset’s IP address, Object name, username, Policy ID, and custom attributes.",
    "3-0": "Lookup Location",
    "3-1": "The location you want to use to search for credentials in the Vault. You can search through all safes or specify a safe and folder you want to search.",
    "4-0": "Safe",
    "4-1": "The ID of the CyberArk safe that contains the credentials for the assets that will be scanned.",
    "5-0": "Folder",
    "5-1": "The ID of the CyberArk folder that contains the credentials for the assets that will be scanned. The default folder is Root.",
    "6-0": "Domain",
    "6-1": "An optional domain name for the user account. If enabled, this domain can also be used to authenticate to applicable assets during scans."
  },
  "cols": 2,
  "rows": 7
}
[/block]
## Looking Up Credentials in the CyberArk Vault

A lookup allows you to match credentials based on a set of criteria. There are two types of lookups you can perform:

* **Static binding** - Obtains a single credential from the vault using the lookup attributes.
* **Dynamic binding** - Obtains credentials for each asset using the lookup attributes. This is useful when you don’t know the credentials that are needed for an asset and want to specify criteria to find the credentials you need during a scan.
[block:callout]
{
  "type": "info",
  "body": "If you are adding a credential dynamically, you should restrict it to sites that do not contain many non-CyberArk credentials. Otherwise, a CyberArk lookup will be performed on every target in the site, which would cause a large number of failed lookups. To prevent this from occurring, you can create a custom list of sites that can use the CyberArk credentials. From the Shared _Scan Credential Configuration_ page, go to the **Site Assignment** tab and select the **Create a custom list of sites that can use these credentials** option."
}
[/block]

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/e6450c8-8ebcddd-s_shared_credentials_custom_site_list.png",
        "8ebcddd-s_shared_credentials_custom_site_list.png",
        593,
        283,
        "#2d3440"
      ]
    }
  ]
}
[/block]
Along with the lookup type, you can use the lookup attributes to specify the criteria that identifies the credentials that can be used for an asset during a scan. You can query the CyberArk Vault using the following attributes:

* **Address** - The IP address or fully qualified domain name for the asset.
* **Object Name** - The name of the object that stores the credentials.
* **Username** - The username for the account that will be retrieved.
* **Policy ID** - The policy ID that is assigned to the credentials that will be retrieved.
* **Custom Attributes** - Custom attributes enable you to add a key and value from your CyberArk password object. The lookup attributes that are available in InsightVM cover the most common request parameters; however, if there are other parameters you want to request from your CyberArk password object, you can specify them using custom attributes.

## Adding Shared Scan Credentials for CyberArk

Shared scan credentials are managed globally in the Security Console and can be used by multiple sites. To configure shared credentials, you must be a Global Administrator role or have a role with Manage Site permissions.

1. Click the **Administration** tab.
2. On the _Administration_ page, click the **Create** link for _Shared Credentials_.
3. From the **General** tab, name the new credential set that will be used with CyberArk.
4. From the **Account** tab, select one of the following services: Microsoft Windows/Samba (SMB/CIFS), Secure Shell (SSH), or Secure Shell (SSH) Public Key. These services support CyberArk as an authentication source.
5. From the **Credential Management** dropdown, select CyberArk.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/339099c-s_cyberark_cred_mgmt_source.PNG",
        "s_cyberark_cred_mgmt_source.PNG",
        809,
        274,
        "#2e3641"
      ]
    }
  ]
}
[/block]
6. When the CyberArk options appear, you must provide the AppID, which will identify the application that is requesting the credentials.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/2603c40-s_cyberark_appid.PNG",
        "s_cyberark_appid.PNG",
        800,
        305,
        "#2d3540"
      ]
    }
  ]
}
[/block]
7. Additionally, you can provide lookup attributes and a lookup location if you want to configure the scan to retrieve credentials from specific safe or based on a specific set of criteria in CyberArk. Please see [Understanding CyberArk Vault Options](doc:creating-and-managing-cyberark-credentials#section-understanding-cyberark-vault-options) for more details.
 * It may be necessary to specify at least two lookup attributes for the connection to pull the proper credentials. For example, consider specifying both the "User Name" and the "Address" attributes when configuring your connection.

[block:callout]
{
  "type": "info",
  "title": "Using the Address lookup with a Domain",
  "body": "The preference between a fully qualified domain name and an IP address differs across CyberArk. In cases where either the domain name or IP address cannot be resolved, you can use the \"Address\" lookup attribute in conjunction with a specified domain to retrieve credentials. To do this, find the \"Lookup Attributes\" field, verify that \"Address\" is selected, and enter the  IP address or fully qualified domain for the asset.\n\nIf both the domain and address are valid, InsightVM will prefer the credentials associated with the domain."
}
[/block]

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/ee6fab2-CyberArk_Domain_field.png",
        "CyberArk_Domain_field.png",
        2490,
        1320,
        "#252d3c"
      ]
    }
  ]
}
[/block]
8. From the **Site Assignment** tab, you can choose to add these scan credentials to all existing and new sites or you can choose the set of sites that will have access to these credentials. The best practice is to use the **Create a custom list of sites that can use these credentials** option. This will allow you to control the sites that have access to the CyberArk credentials and prevent CyberArk lookups from being performed on every target in the site, which would cause a large number of failed lookups. You should reduce the scope of sites to the ones you know will contain targets that will return a CyberArk credential.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/b8a6221-s_shared_credentials_custom_site_list.PNG",
        "s_shared_credentials_custom_site_list.PNG",
        593,
        283,
        "#2d3440"
      ]
    }
  ]
}
[/block]
9. Save your changes.

When you are done, you’ll be able to select the credentials you’ve added for any site that has been granted access to them.

## Adding Site-Specific Credentials for CyberArk

Scan credentials can be site-specific, which means that they are restricted to a single site for use. To configure site-specific credentials, you must be a Global Administrator or Site Owner.

To add CyberArk as an authentication source:

1. Create or edit a site.
2. Go to the **Authentication** tab.
3. Go to the **Add Credentials** tab.
4. From the **General** tab, name the new credential set that will be used with CyberArk.
5. From the **Account** tab, select one of the following services: Microsoft Windows/Samba (SMB/CIFS), Secure Shell (SSH), or Secure Shell (SSH) Public Key. These services support CyberArk as an authentication source.
6. From the **Credential Management** dropdown, select CyberArk. 
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/b566fdd-s_cyberark_cred_mgmt_source2.PNG",
        "s_cyberark_cred_mgmt_source2.PNG",
        814,
        409,
        "#2e3844"
      ]
    }
  ]
}
[/block]
7. When the CyberArk options appear, you must provide the AppID, which will identify the application that is requesting the credentials.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/30e8b7e-s_cyberark_appid2.PNG",
        "s_cyberark_appid2.PNG",
        543,
        209,
        "#e2e6e2"
      ]
    }
  ]
}
[/block]
8. Additionally, you can provide lookup attributes and a lookup location if you want to configure the scan to retrieve credentials from a specific safe based on a specific set of criteria in CyberArk. Please see  [Understanding CyberArk Vault Options](doc:creating-and-managing-cyberark-credentials#section-understanding-cyberark-vault-options) for more details.
 * It may be necessary to specify at least two lookup attributes for the connection to pull the proper credentials. For example, consider specifying both the "User Name" and the "Address" attributes when configuring your connection.
[block:callout]
{
  "type": "info",
  "title": "Using the Address lookup with a Domain",
  "body": "The preference between a fully qualified domain name and an IP address differs across CyberArk. In cases where either the domain name or IP address cannot be resolved, you can use the \"Address\" lookup attribute in conjunction with a specified domain to retrieve credentials. To do this, find the \"Lookup Attributes\" field, verify that \"Address\" is selected, and enter the  IP address or fully qualified domain for the asset.\n\nIf both the domain and address are valid, InsightVM will prefer the credentials associated with the domain."
}
[/block]

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/ee6fab2-CyberArk_Domain_field.png",
        "CyberArk_Domain_field.png",
        2490,
        1320,
        "#252d3c"
      ]
    }
  ]
}
[/block]
9. Save your changes.

When you are done, the site you’ve added the credentials to will be able to use them for authenticated scans.