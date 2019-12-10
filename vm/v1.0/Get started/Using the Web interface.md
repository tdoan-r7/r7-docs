---
title: "Using the Web interface"
excerpt: ""
---
This section includes the following topics to help you access and navigate the Security Console Web interface.

##Activating and updating on private networks

If your Security Console is not connected to the Internet, you can find directions on updating and activating on private networks. See [Managing versions, updates, and licenses](doc:managing-versions-updates-and-licenses).

##Logging on

The Security Console Web interface supports the following browsers:
* Google Chrome (latest) (RECOMMENDED)
* Mozilla Firefox (latest)
* Mozilla Firefox ESR (latest)
* Microsoft Internet Explorer 11

If you received a license key via email, use the following steps to log on. You will enter the license key during this procedure. You can copy the key from the e-mail and paste it into the text box; or you can enter it with or without hyphens. Whether you choose to include or omit hyphens, do so consistently for all four sets of numerals.

If you do not have a license key, click the link to request one. Doing so will open a page on the Rapid7 Web site, where you can register to receive a key by e-mail. After you receive the license key, log on to the Security Console interface again and follow this procedure.

If you are a first-time user and have not yet activated your license, you will need the license key that was sent to you to activate your license after you log on.

To log on to the Security Console take the following steps:
1. Start a Web browser.
If you are running the browser on the same computer as the console, go to the following URL: ```https://localhost:3780```
Indicate HTTPS protocol and to specify port 3780.
If you are running the browser on a separate computer, substitute ```localhost``` with the correct host name or IP address.
Your browser displays the _Logon_ window.
[block:callout]
{
  "type": "info",
  "body": "If there is a usage conflict for port 3780, you can specify another available port in the `nsc.xml` file located at `/opt/rapid7/nexpose/nsc/conf/`. You also can switch the port after you log on. See the topic Changing the Security Console Web server default settings."
}
[/block]
2. Enter your user name and password that you specified during installation.
User names and passwords are case-sensitive and non-recoverable.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/6682b4c-s_logging_on.jpg",
        "s_logging_on.jpg",
        473,
        336,
        "#dadfe4"
      ],
      "caption": "Logon window"
    }
  ]
}
[/block]
3. Click the **Logon** icon.
If you are a first-time user and have not yet activated your license, the Security Console displays an activation dialog box. Follow the instructions to enter your license key.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/cfbfd23-s_search_start_2013Q1.jpg",
        "s_search_start_2013Q1.jpg",
        619,
        66,
        "#242424"
      ],
      "caption": "Activate License window"
    }
  ]
}
[/block]

[block:callout]
{
  "type": "info",
  "body": "If the Security Console displays a warning that authentication services are unavailable, and your network uses an external authentication source, have your Global Administrator verify that the source is online and correctly configured. See [Using external sources for user authentication](doc:managing-users-and-authentication#section-using-external-sources-for-user-authentication)."
}
[/block]
4. Click **Activate** to complete this step.
5. Click the **Home** icon to view the Security Console _Home_ page.
6. Click the **Help** icon on any page of the Web interface for information on how to use the application.

The first time you log on, you will see the _News_ page, which lists all updates and improvements in the installed system, including new vulnerability checks. If you do not wish to see this page every time you log on after an update, clear the check box for automatically displaying this page after every login. You can view the _News_ page by clicking the **News** link that appears under the **Help** icon dropdown. The **Help** icon can be found near the top right corner of every page of the console interface.

##Enabling Two Factor Authentication

For organizations that want additional security upon login, the product supports Two Factor Authentication. Two Factor Authentication requires the use of a time-based one-time password application such as Google Authenticator.

Two Factor Authentication can only be enabled by a Global Administrator on the _Security Console_.

To enable Two Factor Authentication:
1. As a Global Administrator, go to the **Administration** tab.
2. Click the **Administer** link in the _Global and Console Settings_ section.
3. Select **Enable two factor authentication**.
[block:callout]
{
  "type": "info",
  "body": "The Security Console's Two Factor Authentication is not currently compatible with Active Directory (LDAP) and Kerberos authentication methods."
}
[/block]

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/96d520a-2FA1.png",
        "2FA1.png",
        1390,
        688,
        "#1c2733"
      ]
    }
  ]
}
[/block]
The next step is to generate a token for each user. The users can generate their own tokens, or you can generate tokens for them that they then change. In either case, you should communicate with them about the upcoming changes.

###Method 1: Tokens created by users

Once Two Factor Authentication is enabled, when a user logs on, they will see a field where they can enter an access code. For the first time, they should log in without specifying an access code.

Once the user logs in, they can generate a token in the _User Preferences_ page.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/603074e-s_nx_sidebar_menu_print_export.jpg",
        "s_nx_sidebar_menu_print_export.jpg",
        1899,
        442,
        "#e6e7eb"
      ]
    }
  ]
}
[/block]
The user should then open their time-based one-time password application such as Google Authenticator. They should enter the token as the key in the password application. The password application will then generate a new code that should be used as the user’s access code when logging in.

A Global Administrator can check whether users have completed the Two Factor Authentication on the _Manage Users_ page. The _Manage Users_ page can be reached by going to the _Administration_ tab and clicking the **Manage** link in the _Users_ section. A new field, **Two Factor Authentication Enabled**, will appear in the table and let the administrator know which users have enabled this feature.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/d550543-2FA4.png",
        "2FA4.png",
        1078,
        291,
        "#edf3f3"
      ]
    }
  ]
}
[/block]
If the user doesn’t create a token, they will still be able to log in without an access code. In this case, you may need to take steps to enforce enablement.

###Method 2: Generating tokens for users

You can enforce that all users log in with a token by disabling the accounts of any users who have not completed the process, or by creating tokens for them and emailing them their tokens.

To disable users:
1. Go to the _Manage users_ page by going to the **Administration** tab and clicking the **Manage** link in the Users section.
2. Select the checkbox next to each user for whom the Two Factor Authentication Enabled column shows No.
3. Select **Disable users**.

To generate a token for a user:
1. Go to the _Manage users_ page by going to the **Administration** tab and clicking the **Manage** link in the _Users_ section.
2. Select **Edit** for that user.
3. Generate a token for that user.
4. Provide the user with the token.
5. Once the user logs in with their access code, they can change their token if they would like in the _User preferences_ page.

##Navigating the Security Console Web interface

The Security Console includes a Web-based user interface for configuring and operating the application. Familiarizing yourself with the interface will help you to find and use its features quickly.

When you log on to the to the _Home_ page for the first time, you see place holders for information, but no information in them. After installation, the only information in the database is the account of the default Global Administrator and the product license.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/81d687b-s_nx_home_new.jpg",
        "s_nx_home_new.jpg",
        2242,
        1526,
        "#eef3f4"
      ],
      "caption": "The Home page as it appears in a new installation"
    }
  ]
}
[/block]

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/bd0b435-s_nx_home_with_data.jpg",
        "s_nx_home_with_data.jpg",
        700,
        380,
        "#1f2a37"
      ],
      "caption": "The Home page as it appears with scan data"
    }
  ]
}
[/block]
The _Home_ page shows sites, asset groups, tickets, and statistics about your network that are based on scan data. If you are a Global Administrator, you can view and edit site and asset group information, and run scans for your entire network on this page.

The _Home_ page also displays a chart that shows trends of risk score and number of assets over time. The growth in assets over time is an increase in your surface area (total number of assets). As you add assets to your environment your level of risk can increase because the more assets you have, the more potential there is for vulnerabilities.

Each point of data on the chart represents a week. The darker blue line and measurements on the left show how much your risk score has increased or decreased over time. The lighter blue line displays the number of assets.
[block:callout]
{
  "type": "info",
  "body": "This interactive chart shows a default of a year’s worth of data when available; if you have been using the application for a shorter historical period, the chart will adjust to show only the months applicable."
}
[/block]
The following are some additional ways to interact with charts:
* In the search filter at the top left of the chart, you can enter a name of a site or asset group to narrow the results that appear in the chart pane to only show data for that specific site or group.
* Click and drag to select a smaller, specific timeframe and view specific details. Select the **Reset/Zoom** button to reset the view to the previous settings.
* Hover your mouse over a point of data to show the date, the risk score, and the number of assets for the data point.
* Select the sidebar menu icon on the top left of the chart window to export and print a chart image.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/03cb9b6-s_nx_sidebar_menu_print_export.jpg",
        "s_nx_sidebar_menu_print_export.jpg",
        1899,
        442,
        "#e6e7eb"
      ],
      "caption": "Print or export the chart from the sidebar menu"
    }
  ]
}
[/block]
On the _Site Listing_ pane, you can click controls to view and edit site information, run scans, and start to create a new site, depending on your role and permissions.

Information for any currently running scan appears in the pane labeled _Current Scan Listings for All Sites_.

On the _Ticket Listing_ pane, you can click controls to view information about tickets and assets for which those tickets are assigned.

On the _Asset Group Listing_ pane, you can click controls to view and edit information about asset groups, and start to create a new asset group.

A menu appears on the left side of the _Home_ page, as well as every page of the Security Console. Mouse over the icons to see their labels, and use these icons to navigate to the main pages for each area.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/043f3dd-s_home_toolbar.jpg",
        "s_home_toolbar.jpg",
        530,
        506,
        "#313941"
      ],
      "caption": "Icon menu"
    }
  ]
}
[/block]
The _Home_ page links to the initial page you land on in the Security Console.

The _Assets_ page links to pages for viewing assets organized by different groupings, such as the sites they belong to or the operating systems running on them.

The _Vulnerabilities_ page lists all discovered vulnerabilities.

The _Policies_ page lists policy compliance results for all assets that have been tested for compliance.

The _Reports_ page lists all generated reports and provides controls for editing and creating report templates.

The _Tickets_ page lists remediation tickets and their status.

The _Administration_ page is the starting point for all management activities, such as creating and editing user accounts, asset groups, and scan and report templates. Only Global Administrators see this icon.

###Selecting your language

Some features of the application are supported in multiple languages. You have the option to set your user preferences to view Help in the language of your choosing. You can also run Reports in multiple languages, giving you the ability to share your security data across multi-lingual teams.

To select your language, click your user name in the upper-right corner and select **User Preferences**. This will take you to the _User Configuration_ panel. Here you can select your language for Help and Reports from the corresponding drop down lists.

When selecting a language for Help, be sure to clear your cache and refresh your browser after setting the language to view Help in your selection.

Setting your report language from the _User Configuration_ panel will determine the default language of any new reports generated through the _Create Report Configuration_ panel. Report configurations that you have created prior to changing the language in the user preferences will remain in their original language. When creating a new report, you can also change the selected language by going to the **Advanced Settings** section of the _Create a report_ page. See the topic [Creating a basic report](doc:creating-a-basic-report).

###Using icons and other controls

Throughout the Web interface, you can use various controls for navigation and administration.
[block:parameters]
{
  "data": {
    "h-0": "Control",
    "h-2": "Control",
    "h-1": "Description",
    "h-3": "Description",
    "0-1": "Minimize any pane so that only its title bar appears.",
    "0-3": "Add items to your dashboard.",
    "1-1": "Expand a minimized pane.",
    "1-3": "Copy a built-in report template to create a customized version.",
    "2-1": "Close a pane.",
    "2-3": "Edit properties for a site, report, or a user account.",
    "3-1": "Click to display a list of closed panes and open any of the listed panes.",
    "3-3": "View a preview of a report template.",
    "4-1": "Export data to a comma-separated value (CSV) file.",
    "4-3": "Delete a site, report, or user account.",
    "5-1": "Start a manual scan.",
    "5-3": "Exclude a vulnerability from a report.",
    "6-1": "Pause a scan.",
    "6-3": "View Help.\nView the Support page to search FAQ pages and contact Technical Support.\nView the _News_ page which lists all updates.",
    "7-1": "Resume a scan.",
    "7-2": "Product logo",
    "7-3": "Click the product logo in the upper-left area to return to the _Home_ page.",
    "8-1": "Stop a scan.",
    "8-2": "**User: <user name>** link",
    "8-3": "This link is the logged-on user name. Click it to open the User Configuration panel where you can edit account information such as the password and view site and asset group access. Only Global Administrators can change roles and permissions.",
    "9-1": "Initiate a filtered search for assets to create a dynamic asset group.",
    "9-2": "**Log Out** link",
    "9-3": "Log out of the Security Console interface. The _Logon_ box appears. For security reasons, the Security Console automatically logs out a user who has been inactive for 10 minutes.",
    "10-1": "Expand a drop-down list of options to create sites, asset groups, tags, or reports.",
    "0-0": "![Alt](https://files.readme.io/358c553-i_minimize.jpg)",
    "1-0": "![Alt](https://files.readme.io/346f9fa-i_maximize.jpg)",
    "0-2": "![Alt](https://files.readme.io/acbfa9d-i_dashboard.jpg)",
    "1-2": "![Alt](https://files.readme.io/80f2f45-i_copy.jpg)",
    "2-0": "![Alt](https://files.readme.io/336bbfb-i_close_pane.jpg)",
    "2-2": "![Alt](https://files.readme.io/1ac75d5-i_nx48_edit.png)",
    "3-0": "![Alt](https://files.readme.io/22b42a6-i_customize_dashboard.jpg)",
    "3-2": "![Alt](https://files.readme.io/ca8f5c6-i_nx48_pvureptemp.png)",
    "4-0": "![Alt](https://files.readme.io/9796c5c-i_csvexport.jpg)",
    "4-2": "![Alt](https://files.readme.io/193f8ca-i_nx_delete_icon.jpg)",
    "5-0": "![Alt](https://files.readme.io/828272f-i_nx_scan_on.jpg)",
    "5-2": "![Alt](https://files.readme.io/d02e339-i_nx48_exclude.png)",
    "6-0": "![Alt](https://files.readme.io/57de13c-i_nx_scan_pause.jpg)",
    "6-2": "![Alt](https://files.readme.io/68271a7-i_support_help_news.jpg)",
    "7-0": "![Alt](https://files.readme.io/43ed57a-i_nx_scan_resume.jpg)",
    "8-0": "![Alt](https://files.readme.io/a6f10e8-i_nx_scan_stop.jpg)",
    "9-0": "![Alt](https://files.readme.io/ae6fd84-i_asset_filtered_search.jpg)",
    "10-0": "![Alt](https://files.readme.io/895f882-i_nx_create.jpg)"
  },
  "cols": 4,
  "rows": 11
}
[/block]
##Using the search feature

With the powerful full-text search feature, you can search the database using a variety of criteria, such as the following:
* full or partial IP addresses
* asset names
* site names
* asset group names
* vulnerability titles
* vulnerability CVE IDs
* internal vulnerability IDs user-added tags
* criticality tags
* Common Configuration Enumerator (CCE) IDs
* operating system names

Access the **Search** box on any a page of the Security Console interface by clicking the magnifying glass icon near the top right of the page.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/69e4c41-s_nx_search_icon.png",
        "s_nx_search_icon.png",
        446,
        92,
        "#292b2f"
      ],
      "caption": "Clicking the Search icon"
    }
  ]
}
[/block]
Enter your search criteria into the **Search** box and then click the magnifying glass icon again. For example, if you want to search for discovered instances of the vulnerabilities that affect assets running ActiveX, enter _ActiveX_ or _activex_ in the **Search** text box. The search is not case-sensitive.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/46ddc26-s_search_start_2013Q1.jpg",
        "s_search_start_2013Q1.jpg",
        619,
        66,
        "#242424"
      ]
    }
  ]
}
[/block]
The application displays search results on the _Search_ page, which includes panes for different groupings of results. With the current example,

_ActiveX_, results appear in the _Vulnerability Results_ table. At the bottom of each category pane, you can view the total number of results and change settings for how results are displayed.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/d9fe3f6-s_nx_search_for_partial.jpg",
        "s_nx_search_for_partial.jpg",
        250,
        61,
        "#b3b3b3"
      ],
      "caption": "Search results"
    }
  ]
}
[/block]
In the _Search Criteria_ pane, you can refine and repeat the search. You can change the search phrase and choose whether to allow partial word matches and to specify that all words in the phrase appear in each result. After refining the criteria, click the **Search Again** button.

###Using asterisks and avoiding _stop words_

When you run initial searches with partial strings in the _Search_ box that appears in the upper-right corner of most pages in the Web interface, results include all terms that even partially match those strings. It is not necessary to use an asterisk (*) on the initial search. For example, you can enter _Win_ to return results that include the word Windows, such as any Windows operating system. Or if you want to find all IP addresses in the 10.20 range, you can enter 10.20 in the Search text box.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/0311101-s_nx_search_for_partial.jpg",
        "s_nx_search_for_partial.jpg",
        250,
        61,
        "#b3b3b3"
      ]
    }
  ]
}
[/block]
If you want to modify the search after viewing the results, an asterisk is appended to the string in the _Search Criteria_ pane that appears with the results. If you leave the asterisk in, the modified search will still return partial matches. You can remove the asterisk if you want the next set of results to match the string exactly.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/99206d3-s_nx_modify_search.jpg",
        "s_nx_modify_search.jpg",
        1962,
        1409,
        "#f1f4f5"
      ],
      "caption": "Searching with a partial string"
    }
  ]
}
[/block]
If you precede a string with an asterisk, the search ignores the asterisk and returns results that match the string itself.

Certain words and individual characters, collectively known as _stop words_ return no results, even if you enter them with asterisks. For better performance, search mechanisms do not recognize stop words. Some stop words are single letters, such as _a_, _i_, _s_, and _t_. If you want to include one of these letters in a search string, add one or more letters to the string. Following is a list of stop words:
[block:parameters]
{
  "data": {
    "0-0": "a",
    "0-1": "about",
    "0-2": "above",
    "0-3": "after",
    "0-4": "again",
    "0-5": "against",
    "0-6": "all",
    "0-7": "am",
    "0-8": "an",
    "0-9": "and",
    "1-0": "any",
    "1-1": "are",
    "1-2": "as",
    "1-3": "at",
    "1-4": "be",
    "1-5": "because",
    "1-6": "been",
    "1-7": "being",
    "1-8": "below",
    "1-9": "before",
    "2-0": "between",
    "2-1": "both",
    "2-2": "but",
    "2-3": "by",
    "2-4": "can",
    "2-5": "did",
    "2-6": "do",
    "2-7": "doing",
    "2-8": "don",
    "2-9": "does",
    "3-0": "down",
    "3-1": "during",
    "3-2": "each",
    "3-3": "few",
    "3-4": "for",
    "3-5": "from",
    "3-6": "further",
    "3-7": "had",
    "3-8": "has",
    "3-9": "have",
    "4-0": "having",
    "4-1": "he",
    "4-2": "her",
    "4-3": "here",
    "4-4": "hers",
    "4-5": "herself",
    "4-6": "him",
    "4-7": "himself",
    "4-8": "his",
    "4-9": "how",
    "5-0": "i",
    "5-1": "if",
    "5-2": "in",
    "5-3": "into",
    "5-4": "it",
    "5-5": "is",
    "5-6": "its",
    "5-7": "itself",
    "5-8": "just",
    "5-9": "me",
    "6-0": "more",
    "6-1": "most",
    "6-2": "my",
    "6-3": "myself",
    "6-4": "no",
    "6-5": "nor",
    "6-6": "not",
    "6-7": "now",
    "6-8": "of",
    "6-9": "off",
    "7-0": "on",
    "7-1": "once",
    "7-2": "only",
    "7-3": "or",
    "7-4": "other",
    "7-5": "our",
    "7-6": "ours",
    "7-7": "ourselves",
    "7-8": "out",
    "7-9": "over",
    "8-0": "own",
    "8-1": "s",
    "8-2": "same",
    "8-3": "she",
    "8-4": "should",
    "8-5": "so",
    "8-6": "some",
    "8-7": "such",
    "8-8": "t",
    "8-9": "than",
    "9-0": "that",
    "9-1": "the",
    "9-2": "their",
    "9-3": "theirs",
    "9-4": "them",
    "9-5": "themselves",
    "9-6": "then",
    "9-7": "there",
    "9-8": "these",
    "9-9": "they",
    "10-0": "this",
    "10-1": "those",
    "10-2": "through",
    "10-3": "to",
    "10-4": "too",
    "10-5": "under",
    "10-6": "until",
    "10-7": "up",
    "10-8": "very",
    "10-9": "was",
    "11-0": "we",
    "11-1": "were",
    "11-2": "what",
    "11-3": "when",
    "11-4": "where",
    "11-5": "which",
    "11-6": "while",
    "11-7": "who",
    "11-8": "whom",
    "11-9": "why",
    "12-0": "will",
    "12-1": "with",
    "12-2": "you",
    "12-3": "your",
    "12-4": "yours",
    "12-5": "yourself",
    "12-6": "yourselves"
  },
  "cols": 10,
  "rows": 13
}
[/block]
##Accessing operations faster with the Administration page

You can access a number of key Security Console operations quickly from the _Administration_ page. To go there, click the **Administration** icon. The page displays a panel of tiles that contain links to pages where you can perform any of the following operations to which you have access:
* managing user accounts
* managing asset groups
* reviewing requests for vulnerability exceptions and policy result overrides
* creating and managing Scan Engines
* managing shared scan credentials, which can be applied in multiple sites
* viewing the scan history for your installation
* managing scan templates
* managing different models, or strategies, for calculating risk scores
* managing various activities and settings controlled by the Security Console, such as license, * updates, and communication with Scan Engines
* managing settings and events related to discovery of virtual assets, which allows you to create dynamic sites
* viewing information related to Security Content Automation Protocol (SCAP) content
* maintaining and migrating the database
* troubleshooting the application
* using the command console to type commands
* managing data export settings for integration with third-party reporting systems

Tiles that contain operations that you do not have access to because of your role or license display a label that indicates this restriction.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/8c2f17a-s_nx_admin_5_8_limited_access.jpg",
        "s_nx_admin_5_8_limited_access.jpg",
        1991,
        1303,
        "#e8eeef"
      ],
      "caption": "Administration page"
    }
  ]
}
[/block]
After viewing the options, select an operation by clicking the link for that operation.

##Using configuration panels

The Security Console provides panels for configuration and administration tasks:
* creating and editing sites
* creating and editing user accounts
* creating and editing asset groups
* creating and editing scan templates
* creating and editing reports and report templates
* configuring Security Console settings
* troubleshooting and maintenance
[block:callout]
{
  "type": "info",
  "body": "Parameters labeled in red denote required parameters on all panel pages."
}
[/block]
##Extending Web interface sessions
[block:callout]
{
  "type": "info",
  "body": "You can change the length of the Web interface session. See [Changing the Security Console Web server default settings](doc:managing-the-security-console#section-changing-the-security-console-web-server-default-settings)."
}
[/block]
By default, an idle Web interface session times out after 10 minutes. When an idle session expires, the Security Console displays a logon window. To continue the session, simply log on again. You will not lose any unsaved work, such as configuration changes. However, if you choose to log out, you will lose unsaved work.

If a communication issue between your browser and the Security Console Web server prevents the session from refreshing, you will see an error message. If you have unsaved work, do not leave the page, refresh the page, or close the browser. Contact your Global Administrator.