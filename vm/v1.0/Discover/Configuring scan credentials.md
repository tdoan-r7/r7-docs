---
title: "Configuring scan credentials"
excerpt: ""
---
Scanning with credentials allows you to gather information about your network and assets that you could not otherwise access. You can inspect assets for a wider range of vulnerabilities or security policy violations. Additionally, authenticated scans can check for software applications and packages and verify patches. When you scan a site with credentials, target assets in that site authenticate the Scan Engine as they would an authorized user.

Topics in this section explain how to set up and test credentials for a site as well as shared scan credentials, which you can use in multiple sites. Certain authentication options, such as SSH public key and LM/NTLM hash, require additional steps, which are covered in related topics. You can also learn best practices for getting the most out of credentials, such as expanding authentication with elevated permissions.

## Shared credentials vs. site-specific credentials

Two types of scan credentials can be created in the application, depending on the role or permissions of the user creating them:

* _Shared_ credentials can be used in multiple sites
* _Site-specific_ credentials can only be used in the site for in which they are configured

The range of actions that a user can perform with each type depends on the user’s role or permissions, as indicated in the following table:
[block:parameters]
{
  "data": {
    "h-0": "Credentials type",
    "h-1": "How it is created",
    "h-2": "Actions that can be performed by a Global Administrator or user with Manage Site permission",
    "h-3": "Actions that can be performed by a Site Owner",
    "0-0": "shared",
    "0-1": "A Global Administrator or user with the Manage Site permission creates it on the _Administration_ > _Shared Scan Credentials_ page.",
    "0-2": "Create, edit, delete, assign to a site, restrict to an asset. Enable or disable the use of the credentials in any site.",
    "0-3": "Enable or disable the use of the credentials in sites to which the Site Owner has access.",
    "1-0": "site-specific",
    "1-1": "A Global Administrator or Site Owner creates it in the configuration for a specific site.",
    "1-2": "Within a specific site to which the Site Owner has access: Create, edit, delete, enable or disable the use of the credentials in that site.",
    "1-3": "Within a specific site to which the Site Owner has access: Create, edit, delete, enable or disable the use of the credentials in that site."
  },
  "cols": 4,
  "rows": 2
}
[/block]
## Credentials and the expert system

The application uses an expert system at the core of its scanning technology in order to chain multiple actions together to get the best results when scanning. For example, if the application is able to use default configurations to get local access to an asset, then it will trigger additional actions using that access. The Nexpose Expert System paper outlines the benefits of this approach and can be found here: [Using an Expert System for Deeper Vulnerability Scanning](https://information.rapid7.com/using-an-expert-system-for-deeper-vulnerability-scanning.html). The effect of the expert system is that you may see scan results beyond those directly expected from the credentials you provided; for example, if some scan targets cannot be accessed with the specified credentials, but can be accessed with a default password, you will also see the results of those checks. This behavior is similar to the approach of a hacker and enables to find vulnerabilities that other scanners may not.