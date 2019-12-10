---
title: "Scan Configuration"
excerpt: ""
---
A scan configuration, or scan config, is a group of settings you can use to scan a particular app. By creating a scan config, you can save a particular configuration of options, and use it to scan that app with those options again and again.

You can create multiple scan configs per app in order to address different needs. For example, you might want to scan your app weekly with the default attack template, and monthly with the SQL Injection and XSS template.

This section discusses the available options within a scan config.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/fd498e7-Scan_Config_Wizard.png",
        "Scan Config Wizard.png",
        3642,
        1330,
        "#47555d"
      ],
      "caption": "Scan Config Wizard"
    }
  ]
}
[/block]
## Info

In the **Info** section, you can specify a name and description for the scan config. Choose a name that suggests what options the config includes in order to remind yourself and others of the purpose of that config.

## Scan Scope 

In the **Scan Scope** section, you can add URLs to scan in addition to those configured in the app itself. You can also restrict certain URLs from being attacked or crawled.

In the **Scan URLs** subsection, you can add URLs that you want to scan with this config, in addition to those already specified in the app itself.

The URLs specified for the entire app appear in the *App URLs* listing. These are inherited into all scan configs created under that app. The inheritance relates to the seed URLs used when scanning. Seed URLs dictate what URLs are used as the base for a scan. Any scans on an app will use the app level URLs as seed URLs. 

In the *Scan Config URLs* listing, you can add more seed URLs that only apply to this config. You can choose a protocol (HTTP or HTTPS), subdomain (such as www or api), and sub-pages. You can add one URL at a time, or select the **Bulk Add URLs** option and paste or type in a list of URLs.

In the **Crawling Restrictions** subsection, you can restrict what will be crawled in scans run on this config. 
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/2df3ef1-Crawling_Restrictions.png",
        "Crawling Restrictions.png",
        1600,
        1272,
        "#4c5d65"
      ],
      "caption": "Restrict what will be crawled in scans using Crawling Restrictions"
    }
  ]
}
[/block]
The *Max links to crawl* setting allows you to limit the number, and thereby potentially the scope, of URLs to crawl.  The scan engine works in two phases: first crawling and then attacking. During the crawling phase, the seed URLs (a combination of app level URLs and scan config URLs) are used as starting points for an algorithm that requests the content at each URL and then interrogates the response for additional URLs, which are then recursively used for the same process, i.e. “crawling.” This occurs until the total number of URLs discovered reaches the *Max links to crawl* setting. Some resources, such as .js, and .css (an autoload resource needed to properly populate the web page in a browser), may be requested even after the max links limit has been reached.

The *Stay on port* setting forces the scan to crawl only URLs which are defined as using the same port(s) as those specified in the seed URLs.

The crawling restrictions are automatically generated for App URL constraints. The default is domain and subdomain level. To view the auto generated constraints, expand the *App URL Constraints* section.

You can also specify additional constraints. You can use literals, wildcards, or regular expressions to formulate the specific constraints to apply. 

Examples:
1. Wildcard:
Include
http://www.example.com/folder/*
Expected behavior - includes all files within folder in the scan scope.

2. Regular expression:
Include
http://www.example.com/folder/.*
Expected behavior - includes all files within folder in the scan scope.

3. Regular expression:
Exclude
http://www.example.com/.*action=delete
Expected behavior - excludes all pages that have the action delete parameter, for example
http://www.example.com/folder/test.html?action=delete

Note: In some cases, with regular expressions, it may be more effective to provide character classes rather than shortcuts.
Examples:
 * `[ ]+` rather than `\s+`
 * escape / : \/ 

The **Attack Restrictions** subsection is similar to Crawling Restrictions, but also allows you to specify a *Blacklist Regex* which can help you blacklist parameters from getting attacked. The benefit of this field is that the setting can be applied to every URL in the application. 
Example:
 * `id|action|date`
Blacklists the parameters *id*, *action*, and *date* from getting attacked on any URL included in that scan.

##Authentication

This panel allows you to set the authentication settings for the scan.

Form Authentication and Session Hijacking methods are expanded by default. HTTP Authentication, OAuth, and Advanced settings options are disabled by default.

The Form Authentication method contains the following settings:

* *Site requires Form authentication* checkbox - This enables form authentication; you should type in a username and password.
* *SSO* - This is required if a single sign-on solution has a login page outside of the domain restrictions set up in the scan.
* *Site requires HTTP authentication* checkbox - you may enable HTTP authentication and enter a username and password to use the previously entered Form credentials.
* The *Redirect to SSO* setting contains the *Allow initial redirect to SSO (no forms used)* checkbox.
* The *Session Hijacking* setting contains the *Session Hijacking* checkbox and *Utilize Captured Session Cookie* link. The link opens Session settings with the following fields:
  * *Session Cookie* text field.
  * *Lock cookie values for duration of scan* checkbox.
  *  *Apply to all cookies* checkbox.
  * Action buttons are Ok and Cancel.

Advanced settings contains:
  * *Configure SSL certificate* link - opens SSL configuration window where user may configure the SSL certificate
  * *Logged IN Regex* text field
  * *Assume Good login* checkbox - This prevents InsightAppSec from checking to see if the login appears to work. Occasionally, these checks can invalidate the user account.

##Attack Templates

[Attack templates](doc:concepts#section-attack-template) are pre-configured sets of attacks and performance options. The **Attack Templates** tab lets you select a built-in (default) or custom attack template for your scan. 

Some examples of the default scan templates are:
* Crawl only - Deselects all [attack modules](doc:attack-modules).
* Passive analysis - Enables only passive analysis [modules](doc:attack-modules).
* Default - Enables all active and passive analysis [modules](doc:attack-modules).

You can manage existing attack templates and create new templates from the **Administration** page. 

##Schedule

The **Schedule** section lets you schedule periodic scans by specifying the frequency and the date and time for the first scan to begin. You can also schedule [blackouts](doc:concepts#section-blackout) for times when there is heavy user traffic on your application. Blackouts can be one-time or recurring, and you can configure the start and end times for a blackout.

## Custom Options

The **Proxy** subsection allows you to configure an HTTP or HTTPS proxy that you might want to use to relay your scan requests to your App. If your proxy server requires authentication, you can also save your credentials here.

The **Performance** subsection allows you to tune the balance between efficiency and thoroughness of scanning. The performance parameters will also depend on the hardware and network capabilities of your application server. Some examples of editable parameters are *Number of URL Retry Attempts*, *Min Delay Between Requests (ms)*, and *Maximum Bandwidth (KB/s)*. 

There are also some flags that can be switched *On* or *Off* based on your scan preferences:
* Close connection after every request - You should turn this on if your application has not been programmed to handle HTTP pipelining.
* Sequential scan - Enabling this option will ensure that InsightAppSec tries all attacks selected in your scan configuration on one link before moving to the next one.
* Operation log - The operation log details the actions taken by InsightAppSec (e.g. crawling a link, making a specific attack, etc.).
* Traffic log - The traffic log details the request response traffic. This is very helpful if debugging is required. These logs can become very large with longer scans.

The **HTTP Headers** subsection allows you to enter some commonly used headers such as *Accept* and *Content-type*. There is also an area for you to enter other custom headers in the format `header-name=header-value`. Each new header in this box should be added in a new line.