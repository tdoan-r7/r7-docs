---
title: "Managing users and authentication"
excerpt: ""
---
Effective use of scan information depends on how your organization analyzes and distributes it, who gets to see it, and for what reason. Managing access to information in the application involves creating asset groups and assigning roles and permissions to users. This chapter provides best practices and instructions for managing users, roles, and permissions.

* [Mapping roles to your organization](doc:managing-users-and-authentication#section-mapping-roles-to-your-organization)
* [Configuring roles and permissions](doc:managing-users-and-authentication#section-configuring-roles-and-permissions)
* [Managing and creating user accounts](doc:managing-users-and-authentication#section-managing-and-creating-user-accounts)
* [Configure general user account attributes](doc:managing-users-and-authentication#section-configure-general-user-account-attributes)
* [Assign a role and permissions to a user](doc:managing-users-and-authentication#section-assign-a-role-and-permissions-to-a-user)
* [Give a user access to specific sites](doc:managing-users-and-authentication#section-give-a-user-access-to-specific-sites)
* [Give a user access to asset groups](doc:managing-users-and-authentication#section-give-a-user-access-to-asset-groups)
* [Using external sources for user authentication](doc:managing-users-and-authentication#section-using-external-sources-for-user-authentication)
* [Setting a password policy](doc:managing-users-and-authentication#section-setting-a-password-policy)

##Mapping roles to your organization

It is helpful to study how roles and permissions map to your organizational structure.
[block:callout]
{
  "type": "info",
  "body": "While a user authentication system is already included, you should integrate any supported external authentication service with the application to avoid managing multiple sets of user information.  The Security Console supports integrations with the following authentication sources:\n\n* Microsoft Active Directory\n* Kerberos\n* SAML 2.0\n\nSee [Using external sources for user authentication](doc:managing-users-and-authentication#section-using-external-sources-for-user-authentication) for instructions.",
  "title": "TIP"
}
[/block]
In a smaller company, one person may handle all security tasks. He or she will be a Global Administrator, initiating scans, reviewing reports, and performing remediation. Or there may be a small team of people sharing access privileges for the entire system. In either of these cases, it is unnecessary to create multiple roles, because all network assets can be included in one site, requiring a single Scan Engine.

Example, Inc. is a larger company. It has a wider, more complex network, spanning multiple physical locations and IP address segments. Each segment has its own dedicated support team managing security for that segment alone.

One or two global administrators are in charge of creating user accounts, maintaining the system, and generating high-level, executive reports on all company assets. They create sites for different segments of the network. They assign security managers, site administrators, and system administrators to run scans and distribute reports for these sites.

The Global Administrators also create various asset groups. Some will be focused on small subsets of assets. Non-administrative users in these groups will be in charge of remediating vulnerabilities and then generating reports after follow-up scans are run to verify that remediation was successful. Other asset groups will be more global, but less granular, in scope. The non-administrative users in these groups will be senior managers who view the executive reports to track progress in the company's vulnerability management program.

##Configuring roles and permissions

Whether you create a custom role or assign a preset role for an account depends on several questions: What tasks do you want that account holder to perform? What data should be visible to the user? What data should not be visible to the user.

For example, a manager of a security team that supports workstations may need to run scans on occasion and then distribute reports to team members to track critical vulnerabilities and prioritizing remediation tasks. This account may be a good candidate for an Asset Owner role with access to a site that only includes workstations and not other assets, such as database servers.
[block:callout]
{
  "type": "info",
  "body": "Keep in mind that, except for the Global Administrator role, the assigning of a custom or preset role is interdependent with access to site and asset groups."
}
[/block]
If you want to assign roles with very specific sets of permissions you can create custom roles. The following tables list and describe all permissions that are available. Some permissions require other permissions to be granted in order to be useful. For example, in order to be able to create reports, a user must also be able to view asset data in the reported-on site or asset group, to which the user must also be granted access.

The tables also indicate which roles include each permission. You may find that certain roles are granular or inclusive enough for a given account. A list of preset roles and the permissions they include follows the permissions tables. See [Give a user access to asset groups](doc:managing-users-and-authentication#section-give-a-user-access-to-asset-groups).

###Permissions tables

####Global permissions

These permissions automatically apply to all sites and asset groups and do not require additional, specified access.
[block:parameters]
{
  "data": {
    "h-0": "Permission",
    "h-1": "Description",
    "h-2": "Role",
    "0-0": "Manage Sites",
    "0-1": "Create, delete, and configure all attributes of sites, except for user access. Implicitly have access to all sites. Manage shared scan credentials. **Other affected permissions**: When you select this permission, all site permissions automatically become selected. See Site permissions.",
    "0-2": "[Global Administrator](doc:managing-users-and-authentication#section-global-administrator)",
    "1-0": "Manage Scan Templates",
    "1-1": "Create, delete, and configure all attributes of scan templates.",
    "1-2": "[Global Administrator](doc:managing-users-and-authentication#section-global-administrator)",
    "2-0": "Manage Report Templates",
    "2-1": "Create, delete, and configure all attributes of report templates.",
    "2-2": "[Global Administrator](doc:managing-users-and-authentication#section-global-administrator),\n[Security Manager and Site Owner](doc:managing-users-and-authentication#section-security-manager-and-site-owner),\n[Asset Owner](doc:managing-users-and-authentication#section-asset-owner), \n[User](doc:managing-users-and-authentication#section-user)",
    "3-0": "Manage Scan Engines",
    "3-1": "Create, delete, and configure all attributes of Scan Engines; pair Scan Engines with the Security Console.",
    "3-2": "[Global Administrator](doc:managing-users-and-authentication#section-global-administrator)",
    "4-0": "Manage Policies",
    "4-1": "Copy existing policies; edit and delete custom policies.",
    "4-2": "[Global Administrator](doc:managing-users-and-authentication#section-global-administrator)",
    "5-0": "Appear on Ticket and Report Lists",
    "5-1": "Appear on user lists in order to be assigned remediation tickets and view reports. \n\n**Prerequisite:** A user with this permission must also have asset viewing permission in any relevant site or asset group: View Site Asset Data;  View Group Asset Data ",
    "5-2": "[Global Administrator](doc:managing-users-and-authentication#section-global-administrator),\n[Security Manager and Site Owner](doc:managing-users-and-authentication#section-security-manager-and-site-owner),\n[Asset Owner](doc:managing-users-and-authentication#section-asset-owner), \n[User](doc:managing-users-and-authentication#section-user)",
    "6-0": "Configure Global Settings",
    "6-1": "Configure settings that are applied throughout the entire environment, such as risk scoring and exclusion of assets from all scans.",
    "6-2": "[Global Administrator](doc:managing-users-and-authentication#section-global-administrator)",
    "7-0": "Manage Tags",
    "7-1": "Create tags and configure their attributes. Delete tags except for built-in criticality tags. Implicitly have access to all sites.",
    "7-2": "[Global Administrator](doc:managing-users-and-authentication#section-global-administrator)"
  },
  "cols": 3,
  "rows": 8
}
[/block]
####Site permissions

These permissions only apply to sites to which a user has been granted access.
[block:parameters]
{
  "data": {
    "h-0": "Permission",
    "h-1": "Description",
    "h-2": "Role",
    "0-0": "View Site Asset Data",
    "0-1": "View discovered information about all assets in accessible sites, including IP addresses, installed software, and vulnerabilities.",
    "0-2": "[Global Administrator](doc:managing-users-and-authentication#section-global-administrator),\n[Security Manager and Site Owner](doc:managing-users-and-authentication#section-security-manager-and-site-owner),\n[Asset Owner](doc:managing-users-and-authentication#section-asset-owner), \n[User](doc:managing-users-and-authentication#section-user)",
    "1-0": "Specify Site Metadata",
    "1-1": "Enter site descriptions, importance ratings, and organization data.",
    "1-2": "[Global Administrator](doc:managing-users-and-authentication#section-global-administrator),\n[Security Manager and Site Owner](doc:managing-users-and-authentication#section-security-manager-and-site-owner)",
    "2-0": "Specify Scan Targets",
    "2-1": "Add or remove IP addresses, address ranges, and host names for site scans.",
    "2-2": "[Global Administrator](doc:managing-users-and-authentication#section-global-administrator)",
    "3-0": "Assign Scan Engine",
    "3-1": "Assign a Scan Engine to sites.",
    "3-2": "[Global Administrator](doc:managing-users-and-authentication#section-global-administrator)",
    "4-0": "Assign Scan Template",
    "4-1": "Assign a scan template to sites.",
    "4-2": "[Global Administrator](doc:managing-users-and-authentication#section-global-administrator),\n[Security Manager and Site Owner](doc:managing-users-and-authentication#section-security-manager-and-site-owner)",
    "5-0": "Manage Scan Alerts",
    "5-1": "Create, delete, and configure all attributes of alerts to notify users about scan-related events.",
    "5-2": "[Global Administrator](doc:managing-users-and-authentication#section-global-administrator),\n[Security Manager and Site Owner](doc:managing-users-and-authentication#section-security-manager-and-site-owner)",
    "6-0": "Manage Site Credentials",
    "6-1": "Provide logon credentials for deeper scanning capability on password-protected assets",
    "6-2": "[Global Administrator](doc:managing-users-and-authentication#section-global-administrator),\n[Security Manager and Site Owner](doc:managing-users-and-authentication#section-security-manager-and-site-owner)",
    "7-0": "Schedule Automatic Scans",
    "7-1": "Create and edit site scan schedules.",
    "7-2": "[Global Administrator](doc:managing-users-and-authentication#section-global-administrator),\n[Security Manager and Site Owner](doc:managing-users-and-authentication#section-security-manager-and-site-owner)",
    "8-0": "Start Unscheduled Scans",
    "8-1": "Manually start one-off scans of accessible sites (does not include ability to configure scan settings).",
    "8-2": "[Global Administrator](doc:managing-users-and-authentication#section-global-administrator),\n[Security Manager and Site Owner](doc:managing-users-and-authentication#section-security-manager-and-site-owner),\n[Asset Owner](doc:managing-users-and-authentication#section-asset-owner)",
    "9-0": "Purge Site Asset Data",
    "9-1": "Manually remove asset data from accessible sites.\n**\nPrerequisites:** A user with this permission must also have one of the following permissions: View Site Asset Data; View Group Asset Data",
    "9-2": "[Global Administrator](doc:managing-users-and-authentication#section-global-administrator)",
    "10-0": "Manage Site Access",
    "10-1": "Grant and remove user access to sites.",
    "10-2": "[Global Administrator](doc:managing-users-and-authentication#section-global-administrator)"
  },
  "cols": 3,
  "rows": 11
}
[/block]
####Asset Group permissions

These permissions only apply to asset groups to which a user has been granted access.
[block:parameters]
{
  "data": {
    "h-0": "Permission",
    "h-1": "Description",
    "h-2": "Role",
    "0-0": "Manage Dynamic Asset Groups",
    "0-1": "Create dynamic asset groups. Delete and configure all attributes of accessible dynamic asset groups except for user access. **Implicitly have access to all sites**. \n\n**Note:** A user with this permission has the ability to view all asset data in your organization.",
    "0-2": "[Global Administrator](doc:managing-users-and-authentication#section-global-administrator)",
    "1-0": "Manage Static Asset Groups",
    "1-1": "Create static asset groups. Delete and configure all attributes of accessible static asset groups except for user access. \n\n**Prerequisite:** A user with this permission must also have the following permissions and access to at least one site to effectively manage static asset groups: *Manage Group Assets; View Group Asset Data* ",
    "1-2": "[Global Administrator](doc:managing-users-and-authentication#section-global-administrator)",
    "2-0": "View Group Asset Data",
    "2-1": "View discovered information about all assets in accessible asset groups, including IP addresses, installed software, and vulnerabilities.",
    "2-2": "Global Administrator](doc:managing-users-and-authentication#section-global-administrator),\n[Security Manager and Site Owner](doc:managing-users-and-authentication#section-security-manager-and-site-owner),\n[Asset Owner](doc:managing-users-and-authentication#section-asset-owner), \n[User](doc:managing-users-and-authentication#section-user)",
    "3-0": "Manage Group Assets",
    "3-1": "Add and remove assets in static asset groups. \n\n**Note: **This permission does not include ability to delete underlying asset definitions or discovered asset data. **Prerequisite:** A user with this permission must also have of the following permission: View Group Asset Data",
    "3-2": "[Global Administrator](doc:managing-users-and-authentication#section-global-administrator)",
    "4-0": "Manage Asset Group Access",
    "4-1": "Grant and remove user access to asset groups.",
    "4-2": "[Global Administrator](doc:managing-users-and-authentication#section-global-administrator)"
  },
  "cols": 3,
  "rows": 5
}
[/block]
####Report permissions

The Create Reports permission only applies to assets to which a user has been granted access. Other report permissions are not subject to any kind of access.
[block:parameters]
{
  "data": {
    "h-0": "Permission",
    "h-1": "Description",
    "h-2": "Role",
    "0-0": "Create Reports",
    "0-1": "Create and own reports for accessible assets; configure all attributes of owned reports, except for user access. \n\n**Prerequisites:** A user with this permission must also have one of the following permissions: View Site Asset Data; View Group Asset Data ",
    "0-2": "[Global Administrator](doc:managing-users-and-authentication#section-global-administrator),\n[Security Manager and Site Owner](doc:managing-users-and-authentication#section-security-manager-and-site-owner),\n[Asset Owner](doc:managing-users-and-authentication#section-asset-owner), \n[User](doc:managing-users-and-authentication#section-user)",
    "1-0": "Use Restricted Report Sections",
    "1-1": "Create report templates with restricted sections; configure reports to use templates with restricted sections. \n\n**Prerequisites:** A user with this permission must also have one of the following permissions: Manage Report Templates",
    "1-2": "[Global Administrator](doc:managing-users-and-authentication#section-global-administrator)",
    "2-2": "[Global Administrator](doc:managing-users-and-authentication#section-global-administrator)",
    "2-0": "Manage Report Access",
    "2-1": "Grant and remove user access to owned reports."
  },
  "cols": 3,
  "rows": 3
}
[/block]
####Ticket permissions

These permissions only apply to assets to which a user has been granted access.
[block:parameters]
{
  "data": {
    "h-0": "Permission",
    "h-1": "Description",
    "h-2": "Role",
    "0-0": "Create Tickets",
    "0-1": "Create tickets for vulnerability remediation tasks. \n\n**Prerequisites: **A user with this permission must also have one of the following permissions: View Site Asset Data; View Group Asset Data",
    "0-2": "[Global Administrator](doc:managing-users-and-authentication#section-global-administrator),\n[Security Manager and Site Owner](doc:managing-users-and-authentication#section-security-manager-and-site-owner),\n[Asset Owner](doc:managing-users-and-authentication#section-asset-owner), \n[User](doc:managing-users-and-authentication#section-user)",
    "1-0": "Close Tickets",
    "1-1": "Close or delete tickets for vulnerability remediation tasks.\n\n**Prerequisites:** A user with this permission must also have one of the following permissions:View Site Asset Data; View Group Asset Data",
    "1-2": "[Global Administrator](doc:managing-users-and-authentication#section-global-administrator),\n[Security Manager and Site Owner](doc:managing-users-and-authentication#section-security-manager-and-site-owner),\n[Asset Owner](doc:managing-users-and-authentication#section-asset-owner), \n[User](doc:managing-users-and-authentication#section-user)"
  },
  "cols": 3,
  "rows": 2
}
[/block]
####Vulnerability exception permissions

These permissions only apply to sites or asset groups to which a user has been granted access.
[block:parameters]
{
  "data": {
    "h-0": "Permission",
    "h-1": "Description",
    "h-2": "Role",
    "0-0": "Submit Vulnerability Exceptions",
    "0-1": "Submit requests to exclude vulnerabilities from reports. \n**\nPrerequisites:** A user with this permission must also have one of the following permissions: View Site Asset Data; View Group Asset Data ",
    "0-2": "[Global Administrator](doc:managing-users-and-authentication#section-global-administrator),\n[Security Manager and Site Owner](doc:managing-users-and-authentication#section-security-manager-and-site-owner),\n[Asset Owner](doc:managing-users-and-authentication#section-asset-owner), \n[User](doc:managing-users-and-authentication#section-user)",
    "1-0": "Review Vulnerability Exceptions",
    "1-1": "Approve or reject requests to exclude vulnerabilities from reports.\n\n**Prerequisites:** A user with this permission must also have one of the following permissions: View Site Asset Data; View Group Asset Data ",
    "1-2": "[Global Administrator](doc:managing-users-and-authentication#section-global-administrator)",
    "2-2": "[Global Administrator](doc:managing-users-and-authentication#section-global-administrator)",
    "2-0": "Review Vulnerability Exceptions",
    "2-1": "Approve or reject requests to exclude vulnerabilities from reports.\n\n**Prerequisites:** A user with this permission must also have one of the following permissions: View Site Asset Data; View Group Asset Data",
    "3-0": "Delete Vulnerability Exceptions",
    "3-1": "Delete vulnerability exceptions and exception requests.\n\n**Prerequisites:** A user with this permission must also have one of the following permissions: View Site Asset Data; View Group Asset Data",
    "3-2": "[Global Administrator](doc:managing-users-and-authentication#section-global-administrator)"
  },
  "cols": 3,
  "rows": 4
}
[/block]
###List of roles

####Global Administrator

The Global Administrator role differs from all other preset roles in several ways. It is not subject to site or asset group access. It includes all permissions available to any other preset or custom role. It also includes permissions that are not available to custom roles:
* Manage all functions related to user accounts, roles, and permissions.
* Manage Dynamic Discovery connections that allow you to pull assets from systems such as VMWare, AWS, DHCP, and Infoblox.
* Manage configuration, maintenance, and diagnostic routines for the Security Console.
* Manage shared scan credentials.

####Security Manager and Site Owner

The Security Manager and Site Owner roles include the following permissions:

* [Manage Report Templates](doc:managing-users-and-authentication#section-global-permissions) 
* [Appear on Ticket and Report Lists](doc:managing-users-and-authentication#section-global-permissions) 
* [View Site Asset Data](doc:managing-users-and-authentication#section-site-permissions) 
* [Specify Site Metadata](doc:managing-users-and-authentication#section-site-permissions) 
* [Assign Scan Template](doc:managing-users-and-authentication#section-site-permissions) 
* [Manage Scan Alerts](doc:managing-users-and-authentication#section-site-permissions) 
* [Manage Site Credentials](doc:managing-users-and-authentication#section-site-permissions) 
* [Schedule Automatic Scans](doc:managing-users-and-authentication#section-site-permissions) 
* [Start Unscheduled Scans](doc:managing-users-and-authentication#section-site-permissions) 
* [View Group Asset Data](doc:managing-users-and-authentication#section-asset-group-permissions)   (Security Manager only)
* [Create Reports](doc:managing-users-and-authentication#section-report-permissions) 
* [Create Tickets](doc:managing-users-and-authentication#section-ticket-permissions) 

The only distinction between these two roles is the Security Manager’s ability to work in accessible sites _and_ assets groups. The Site Owner role, on the other hand, is confined to sites.

####Asset Owner

The Asset Owner role includes the following permissions in accessible sites and asset groups:

* [Manage Report Templates](doc:managing-users-and-authentication#section-global-permissions) 
* [Appear on Ticket and Report Lists](doc:managing-users-and-authentication#section-global-permissions)
* [View Site Asset Data](doc:managing-users-and-authentication#section-site-permissions)
* [Start Unscheduled Scans](doc:managing-users-and-authentication#section-site-permissions)
* [View Group Asset Data](doc:managing-users-and-authentication#section-asset-group-permissions)
* [Create Reports](doc:managing-users-and-authentication#section-report-permissions)

####User

Although “user” can refer generically to any owner of aInsightVM account, the name User, with an upper-case _U_, refers to one of the preset roles. It is the only role that does not include scanning permissions. It includes the following permissions in accessible sites and asset groups:

* [Manage Report Templates](doc:managing-users-and-authentication#section-global-permissions) 
* [Manage Policies](doc:managing-users-and-authentication#section-global-permissions) 
* [View Site Asset Data](doc:managing-users-and-authentication#section-site-permissions) 
* [View Group Asset Data](doc:managing-users-and-authentication#section-asset-group-permissions)  (Security Manager only)
* [Create Reports](doc:managing-users-and-authentication#section-report-permissions)
* [Create Tickets](doc:managing-users-and-authentication#section-ticket-permissions)

####ControlsInsight User

This role provides complete access to ControlsInsight with no access to Nexpose.

##Managing and creating user accounts

The **Users** links on the _Administration_ page provide access to pages for creating and managing user accounts. Click **manage** next to _Users_ to view the _Users_ page. On this page, you can view a list of all accounts within your organization. The last logon date and time is displayed for each account, giving you the ability to monitor usage and delete accounts that are no longer in use.

To edit a user account: 
1. Click **Edit** for any listed account, and change its attributes.
The application displays the _User Configuration_ panel. The process for editing an account is the same as the process for creating a new user account. See [Configure general user account attributes](doc:managing-users-and-authentication#section-configure-general-user-account-attributes).

To delete an account and reassign tickets or reports:
1. Click **Delete** for the account you want to remove.
A dialog box appears asking you to confirm that you want to delete the account.
2. Click **Yes** to delete the account.
If that account has been used to create a report, or if that account has been assigned a ticket, the application displays a dialog box prompting you to reassign or delete the report or ticket in question. You can choose delete a report or a ticket that concerns a closed issue or an old report that contains out-of-date information.

3. Select an account from the drop-down list to reassign tickets and reports to.
4. (_Optional_) Click **Delete tickets and reports** to remove these items from the database.
5. Click **OK** to complete the reassignment or deletion.

##Configure general user account attributes

You can specify attributes for general user accounts on the _User Configuration_ panel.

To configure user account attributes:
1. Click **New User** on the _Users_ page.
2. (_Optional_) Click **Create** next to _Users_ on the _Administration_ page. The Security Console displays the _General_ page of the _User Configuration_ panel.
3. Enter all requested user information in the text fields.
4. (_Optional_) Select the appropriate source from the drop-down list to authenticate the user with external sources.
Before you can create externally authenticated user accounts you must define external authentication sources. See [Using external sources for user authentication](doc:managing-users-and-authentication#section-using-external-sources-for-user-authentication).
5. Check the **Account enabled** check box.
You can later disable the account without deleting it by clicking the check box again to remove the check mark.
6. Click **Save** to save the new user information.

##Assign a role and permissions to a user

Assigning a role and permissions to a new user allows you to control that user’s access to Security Console functions.

To assign a role and permissions to a new user:
1. Go to the _Roles_ page.
2. Choose a role from the drop-down list.
When you select a role, the Security Console displays a brief description of that role.
If you choose one of the five default roles, the Security Console automatically selects the appropriate check boxes for that role.
If you choose **Custom Role**, select the check box for each permission that you wish to grant the user.
3. Click **Save** to save the new user information.

##Give a user access to specific sites

A Global Administrator automatically has access to all sites. A security manager, site administrator, system administrator, or nonadministrative user has access only to those sites granted by a global administrator.

To grant a user access to specific sites:
1. Go to the _Site Access_ page.
2. (_Optional_) Click the appropriate radio button to give the user access to all sites.
3. (_Optional_) Click the radio button for creating a custom list of accessible sites to give the user access to specific sites.
4. Click **Add Sites**.
5. The Security Console displays a box listing all sites within your organization.
6. Click the check box for each site that you want the user to access.
7. Click **Save**.
The new site appears on the _Site Access_ page.
8. Click **Save** to save the new user information.

##Give a user access to asset groups

A global administrator automatically has access to all asset groups. A site administrator user has no access to asset groups. A security manager, system administrator, or nonadministrative user has access only to those access groups granted by a global administrator.

To grant a user access to asset group:

1. Go to the _Asset Group Access_ page.
2. (_Optional_) Click the appropriate radio button to give the user access to all asset groups.
3. (_Optional_) Click the radio button for creating a custom list of accessible asset groups to give the user access to specific asset groups.
4. Click **Add Groups**.
The Security Console displays a box listing all asset groups within your organization.
5. Click the check box for each asset group that you want this user to access.
6. Click **Save**.
The new asset group appears on the _Asset Group Access_ page.
7. Click **Save** to save the new user information.

##Using external sources for user authentication

You can integrate the Security Console with external authentication sources. If you use one of these sources, leveraging your existing infrastructure will make it easier for you to manage user accounts.

The application provides single-sign-on external authentication with the following sources:

* **LDAP (including Microsoft Active Directory):** Active Directory (AD) is an LDAP-supportive Microsoft technology that automates centralized, secure management of an entire network's users, services, and resources.  See [Configuring LDAP authentication](doc:configuring-ldap-authentication) for instructions.
* **Kerberos:** Kerberos is a secure authentication method that validates user credentials with encrypted keys and provides access to network services through a “ticket” system.  See [Configuring Kerberos authentication](doc:configuring-kerberos-authentication) for instructions.
* **SAML 2.0:** Security Assertion Markup Language version 2.0 is an XML-based protocol that authenticates users by way of statement packages (known as assertions) communicated between identity and service providers.  See [Configuring SAML 2.0 authentication](doc:configuring-saml-20-authentication) for instructions.
[block:callout]
{
  "type": "info",
  "body": "The Security Console's Two Factor Authentication is not currently compatible with Active Directory (LDAP) and Kerberos authentication methods. For more information, see [Enabling Two Factor Authentication](doc:using-the-web-interface#section-enabling-two-factor-authentication)."
}
[/block]
The application also continues to support its two internal user account stores:

* XML file lists default “built-in” accounts. A Global Administrator can use a built-in account to log on to the application in maintenance mode to troubleshoot and restart the system when database failure or other issues prevent access for other users.
* Datastore lists standard user accounts, which are created by a global administrator.

##Setting a password policy

Global Administrators can customize the password policy in your InsightVM installation. One reason to do so is to configure it to correspond with your organization's particular password standards.
[block:callout]
{
  "type": "info",
  "body": "When you update a password policy, it will take effect for new users and when existing users change their passwords. Existing users will not be forced to change their passwords."
}
[/block]
To customize a password policy:

1. In the Security Console, go to the _Administration_ page.
2. Select **password policy**.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/42c3686-s_nx_password_policy_nav.jpg",
        "s_nx_password_policy_nav.jpg",
        1779,
        1304,
        "#252d3c"
      ],
      "caption": "Navigating to the password policy configuration"
    }
  ]
}
[/block]
3. Change the policy name.
4. Select the desired parameters for the password requirements.
[block:callout]
{
  "type": "info",
  "body": "If you do not want to enforce a maximum length, set the maximum length to 0."
}
[/block]

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/c9b4acc-s_nx_password_policy_config.jpg",
        "s_nx_password_policy_config.jpg",
        1821,
        885,
        "#1c2737"
      ],
      "caption": "Example: This policy is named Test Policy and enforces a minimum length of 8 characters, maximum length of 24 characters, at least one capital leter, at least one numeric value, and at least one special character."
    }
  ]
}
[/block]
5. Click **Save**.

Once the password policy is set, it will be enforced on the User Configuration page.

As a new password is typed in, the items on the list of requirements turn from red to green as the password requirements are met.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/17e75e7-s_nx_password_policy_enforce.jpg",
        "s_nx_password_policy_enforce.jpg",
        1842,
        871,
        "#1c2736"
      ],
      "caption": "As a user types a new password, the requirements on the list change from red to green as they are fulfilled."
    }
  ]
}
[/block]
If a user attempts to save a password that does not meet all the requirements, an error message will appear.