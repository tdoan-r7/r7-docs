---
title: "Configuring Web spidering"
excerpt: ""
---
InsightVM can spider Web sites to discover their directory structures, default directories, the files and applications on their servers, broken links, inaccessible links, and other information.

The application then analyzes this data for evidence of security flaws, such as SQL injection, cross-site scripting (CSS/XSS), backup script files, readable CGI scripts, insecure password use, and other issues resulting from software defects or configuration errors.

Some built-in scan templates use the Web spider by default:
* Web audit
* HIPAA compliance
* Internet DMZ audit
* Payment Card Industry (PCI) audit
* Full audit

You can adjust the settings in these templates. You can also configure Web spidering settings in a custom template. The spider examines links within each Web page to determine which pages have been scanned. In many Web sites, pages that are yet to be scanned will show a base URL, followed by a parameter directed-link, in the address bar.

For example, in the address www.exampleinc.com/index.html?id=6, the ?id=6 parameter probably refers to the content that should be delivered to the browser. If you enable the setting to include query strings, the spider will check the full string www.exampleinc.com/index.html?id=6 against all URL pages that have been already retrieved to see whether this page has been analyzed.

If you do not enable the setting, the spider will only check the base URL without the ?id=6 parameter.

To gain access to a Web site for scanning, the application makes itself appear to the Web server application as a popular Web browser. It does this by sending the server a Web page request as a browser would. The request includes pieces of information called headers. One of the headers, called User-Agent, defines the characteristics of a user’s browser, such as its version number and the Web application technologies it supports. User-Agent represents the application to the Web site as a specific browser, because some Web sites will refuse HTTP requests from browsers that they do not support. The default User-Agent string represents the application to the target Web site as Internet Explorer 7.

##Configuration steps and options for Web spidering

Configure general Web spider settings:
1. Go to the _Web Spidering_ page of the _Scan Template Configuration_ panel.
2. Select the check box to enable Web spidering.
[block:callout]
{
  "type": "warning",
  "body": "Including query strings with Web spidering check box causes the spider to make many more requests to the Web server. This will increase overall scan time and possibly affect the Web server's performance for legitimate users."
}
[/block]
3. Select the appropriate check box to include query strings when spidering if desired.
4. If you want the spider to test for persistent cross-site scripting during a single scan, select the check box for that option.
This test helps to reduce the risk of dangerous attacks via malicious code stored on Web servers. Enabling it may increase Web spider scan times.
[block:callout]
{
  "type": "warning",
  "body": "Changing the default user agent setting may alter the content that the application receives from the Web site."
}
[/block]
5. If you want to change the default value in the **Browser ID (User-Agent)** field enter a new value.
If you are unsure of what to enter for the User-Agent string, consult your Web site developer.
6. Select the option to check the use of common user names and passwords if desired. The application reports the use of these credentials as a vulnerability. It is an insecure practice because attackers can easily guess them. With this setting enabled, the application attempts to log onto Web applications by submitting common user names and passwords to discovered authentication forms. Multiple logon attempts may cause authentication services to lock out accounts with these credentials.

_(Optional)_ Enable the Web spider to check for the use of weak credentials:

As the Web spider discovers logon forms during a scan, it can determine if any of these forms accept commonly used user names or passwords, which would make them vulnerable to automated attacks that exploit this practice. To perform the check, the Web spider attempts to log on through these forms with commonly used credentials. Any successful attempt counts as a vulnerability.
[block:callout]
{
  "type": "warning",
  "body": "This check may cause authentication services with certain security policies to lock out accounts with these commonly used credentials."
}
[/block]
1. Go the _Weak Credential Checking_ area on the Web spidering configuration page, and select the check box labeled **Check use of common user names and passwords**.

Configure Web spider performance settings:
1. Enter a maximum number of foreign hosts to resolve, or leave the default value of 100.
This option sets the maximum number of unique host names that the spider may resolve. This function adds substantial time to the spidering process, especially with large Web sites, because of frequent cross-link checking involved. The acceptable host range is 1 to 500.

2. Enter the amount of time, in milliseconds, in the **Spider response timeout** field to wait for a response from a target Web server. You can enter a value from 1 to 3600000 ms (1 hour). The default value is 120000 ms (2 minutes). The Web spider will retry the request based on the value specified in the **Maximum retries for spider requests** field.
3. Type a number in the field labeled **Maximum directory levels to spider** to set a directory depth limit for Web spidering.
Limiting directory depth can save significant time, especially with large sites. For unlimited directory traversal, type 0 in the field. The default value is 6.
[block:callout]
{
  "type": "info",
  "body": "If you run recurring scheduled scans with a time limit, portions of the target site may remain unscanned at the end of the time limit. Subsequent scans will not resume where the Web spider left off, so it is possible that the target Web site may never be scanned in its entirety."
}
[/block]
4. Type a number in the **Maximum spidering time (minutes)** field to set a maximum number of minutes for scanning each Web site.
A time limit prevents scans from taking longer than allotted time windows for scan jobs, especially with large target Web sites. If you leave the default value of 0, no time limit is applied. The acceptable range is 1 to 500.
5. Type a number in the **Maximum pages to spider** field to limit the number of pages that the spider requests.
This is a time-saving measure for large sites. The acceptable range is 1 to 1,000,000 pages.
[block:callout]
{
  "type": "info",
  "body": "If you set both a time limit and a page limit, the Web spider will stop scanning the target Web site when the first limit is reached."
}
[/block]
6. Enter the number of time to retry a request after a failure in the **Maximum retries for spider requests** field. Enter a value from 0 to 100. A value of 0 means do not retry a failed request. The default value is 2 retries.

Configure Web spider settings related to regular expressions:
1. Enter a regular expression for sensitive data field names, or leave the default string.
The application reports field names that are designated to be sensitive as vulnerabilities: _Form action submits sensitive data in the clear_. Any matches to the regular expression will be considered sensitive data field names.
2. Enter a regular expression for sensitive content. The application reports as vulnerabilities strings that are designated to be sensitive. If you leave the field blank, it does not search for sensitive strings.

Configure Web spider settings related to directory paths:
1. Select the check box to instruct the spider to adhere to standards set forth in the _robots.txt_ protocol.
_Robots.txt_ is a convention that prevents spiders and other Web robots from accessing all or part of Web site that are otherwise publicly viewable.
[block:callout]
{
  "type": "info",
  "body": "Scan coverage of any included bootstrap paths is subject to time and page limits that you set in the Web spider configuration. If the scan reaches your specified time or page limit before scanning bootstrap paths, it will not scan those paths."
}
[/block]
2. Enter the base URL paths for applications that are not linked from the main Web site URLs in the **Bootstrap paths** field if you want the spider to include those URLS.
Example: /myapp. Separate multiple entries with commas. If you leave the field blank, the spider does not include bootstrap paths in the scan.
3. Enter the base URL paths to exclude in the **Excluded paths** field. Separate multiple entries with commas.
If you specify excluded paths, the application does not attempt to spider those URLs or discovery any vulnerabilities or files associated with them. If you leave the field blank, the spider does not exclude any paths from the scan.

Configure any other scan template settings as desired. When you have finished configuring the scan template, click **Save**.

#Web Spidering Restrictions
If you are experiencing abnormal behavior from your printers while scanning them, uncheck the "Don't scan printers, multiple-use devices, or print servers" during the configuration process.


#Fine-tuning Web spidering

The Web spider crawls Web servers to determine the complete layout of Web sites. It is a thorough process, which makes it valuable for protecting Web sites. Most Web application vulnerability tests are dependent on Web spidering.

InsightVM uses spider data to evaluate custom Web applications for common problems such as SQL injection, cross-site scripting (CSS/XSS), backup script files, readable CGI scripts, insecure use of passwords, and many other issues resulting from custom software defects or incorrect configurations.

By default, the Web spider crawls a site using three threads and a per-request delay of 20 ms. The amount of traffic that this generates depends on the amount of discovered, linked site content. If you’re running the application on a multiple-processor system, increase the number of spider threads to three per processor.

A complete Web spider scan will take slightly less than 90 seconds against a responsive server hosting 500 pages, assuming the target asset can serve one page on average per 150 ms. A scan against the same server hosting 10,000 pages would take approximately 28 minutes.

When you configure a scan template for Web spidering, enter the maximum number of directories, or depth, as well as the maximum number of pages to crawl per Web site. These values can limit the amount of time that Web spidering takes. By default, the spider ignores cross-site links and stays only on the end point it is scanning.

If your asset inventory doesn’t include Web sites, be sure to turn this feature off. It can be very time consuming.