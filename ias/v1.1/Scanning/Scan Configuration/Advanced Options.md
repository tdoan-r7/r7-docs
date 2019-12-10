---
title: "Advanced Options"
excerpt: ""
---
The Advanced Options screen enables you to minutely configure your scan template and provides a number of options not available in other screens. This article describes the configuration options and their use cases. The options are categorized as "Scalar", which are options that have a single value (e.g. MaxDatabaseSize), or "Lists", which can have a list of values (e.g. BlackListExtensionList). 

## ScanConfig's Scalar Values
[block:parameters]
{
  "data": {
    "h-0": "Property",
    "h-1": "Description",
    "h-2": "test2",
    "0-0": "Name",
    "0-1": "The name of the scan configuration. This parameter is mandatory. It cannot have an empty string.",
    "0-2": "test5",
    "1-0": "PauseOnRecoverableError",
    "1-1": "This flag controls the behavior of the scanner when it encounters a recoverable error. A recoverable error is an error that often can be corrected by the user. The following are some examples of errors that a user may correct:\n  * Re-login problem\n  * Out of disk space\n  * Out of memory\n\nIt is desirable to pause the scan (as opposed to stopping it) in case of a recoverable error and give the user a chance to correct the problem and continue the scan.  \n\nValues:\n  * **Enabled** - Scan will pause on a recoverable error\n  * **Disabled** - Scan will fail on a recoverable error\n\nDefault value: **Enabled**",
    "3-0": "MaxDatabaseSize",
    "4-0": "MaxTrafficFiles",
    "3-1": "The maximum size in bytes of the jet database scan data file after which the scan is stopped.\n\nDefault value: 1073741824 bytes (1 GB)",
    "4-1": "The maximum number of traffic files the scanner will keep. The scanner removes old traffic files (FIFO) after number of traffic file reaches the number specified in this parameter. A value of '0' means unlimited traffic files will be retained. \n\nDefault value: 0",
    "2-1": "This field specifies which browser component should be used by the scan.\n\nValues:\n  * **Internet Explorer** - Internet Explorer Web Browser Control will be used to execute Javascript\n  * **Chrome** - The Chrome Web Browser will be used to execute Javascript\n\nDefault value: **Internet Explorer** ",
    "2-0": "JavaScriptEngine"
  },
  "cols": 2,
  "rows": 5
}
[/block]
## JavaScriptEngine
[block:parameters]
{
  "data": {
    "h-0": "Property",
    "h-1": "Description",
    "0-0": "JavaScriptEngine"
  },
  "cols": 2,
  "rows": 1
}
[/block]
## DomainNameList
[block:parameters]
{
  "data": {
    "h-0": "Property",
    "h-1": "Description",
    "0-0": "Value"
  },
  "cols": 2,
  "rows": 1
}
[/block]
## CrawlConfig's Scalar Values
[block:parameters]
{
  "data": {
    "h-0": "Property",
    "h-1": "Value",
    "0-0": "MaxDomain",
    "1-0": "MaxCrawlResults",
    "2-0": "MaxPerWebSiteCrawlResults",
    "3-0": "MaxPerDirCrawlResults",
    "4-0": "MaxPerLinkCrawlResults",
    "5-0": "MaxPerNormalizedLinkCrawlResult",
    "6-0": "MaxPerDirChildNodes",
    "7-0": "MaxBlackListExtCrawlResults",
    "8-0": "MaxAttackFeedbackLinksCount",
    "9-0": "MaxPerFileNameCrawlResults",
    "10-0": "RecursionDepth",
    "11-0": "MaxDirDepth",
    "12-0": "DiscoveryDepth",
    "13-0": "UrlRepetitionTolerance",
    "14-0": "SequenceRepetitionTolerance",
    "15-0": "MaxReportedImages",
    "16-0": "MaxReportedLinks",
    "17-0": "MaxReportedComments",
    "18-0": "MaxReportedScripts",
    "19-0": "MaxReportedEmails",
    "20-0": "MaxReportedForms",
    "21-0": "MaxBrowserPageWaitTimeout",
    "22-0": "MaxBrowserWaitTillRequestTimeout",
    "23-0": "MaxBrowserDOMDepth",
    "24-0": "MaxBrowserEventsPerLink",
    "25-0": "MaxBrowserEventsPerCrawlResult",
    "26-0": "MaxBrowserEventsPerDOM",
    "27-0": "MaxBrowserNoNewResourceDOMCount",
    "28-0": "NotInsertedLinkCountThreshold",
    "29-0": "MaxCookiesFromJavascript",
    "30-0": "MaxCookiesSameNameFromJavascript",
    "31-0": "CrawlPrioritization",
    "32-0": "FileNotFoundRegex",
    "33-0": "ServerErrorRegex",
    "34-0": "InvalidURLRegexAttack",
    "35-0": "InvalidURLRegexCrawl",
    "36-0": "LockCookies",
    "37-0": "CaseSensitivity",
    "38-0": "SaveReferences",
    "39-0": "UseBrowser",
    "40-0": "ShowBrowser",
    "41-0": "StayOnPort",
    "42-0": "RestrictToMacro",
    "43-0": "RestrictToManualCrawling",
    "44-0": "RestrictToSeedList",
    "45-0": "RestrictToWebService",
    "46-0": "RestrictToSelenium",
    "47-0": "RestrictToSwagger",
    "48-0": "ImportCookiesFromTraffic",
    "49-0": "PageEqualThreshhold",
    "50-0": "PageSimilarThreshhold",
    "51-0": "ExperimentalCrawling",
    "52-0": "Flash",
    "53-0": "EnableAdvancedParsers",
    "54-0": "SearchForUrls",
    "55-0": "CookieCommaSeparator",
    "56-0": "MaxWebResourcesOverhead",
    "0-1": "Maximum number of domains that InsightAppSec will crawl. \nDomain is a host name and protocol (https://www.live.com) in the URL. For instance, windows.microsoft.com and www.microsoft.com are different domains. If InsightAppSec finds a URL with an explicit IP address that matches a host name in another URL (for instance http://localhost/page.html and http://127.0.0.1/page.html), InsightAppSec will consider those as two different domains. Also, the protocol is a part of the domain name, and, as a result, https://localhost and http://localhost are two different domains.\n\nDefault value: 100",
    "1-1": "The maximum number of web resources that InsightAppSec is allowed to retrieve from the server during the scan. A web resource is identified by a unique combination of a URL and a parameter (Query, POST). After that number is reached, crawling is stopped.\n\nDefault value: 5000",
    "2-1": "Maximum number web resource crawler is allowed to crawl per domain. \n\nDefault value: -1 (unlimited)",
    "3-1": "Maximum number of web resources in any directory the crawler is allowed to retrieve.\n\nDefault value: 500",
    "4-1": "Maximum number of web resources for a given link the crawler is allowed to retrieve. A Link is a URL with all the parameters. This option limits how many resources that have the same URL but different variations of POST parameters can be crawled\n\nDefault value: 50",
    "5-1": "Maximum number of resources the crawler is allowed to request for a given normalized link. Normalized link is a URL without parameter values.\n\nDefault value: 100",
    "6-1": "Maximum number of child nodes in the directory the crawler is allowed to crawl. Child node is a directory or a file. This parameter does not count grand children.\nThis parameter includes Crawl Results and sub-directories. The crawler will stop crawling new resources in a directory if one of the limits specified in MaxPerDirCrawlResult or MaxPerDirChildNodes is reached for that directory. This implies that the value of MaxPerDirCrawlResult should be greater or equal to the value of MaxPerDirChildNodes.\n\nDefault value: 300",
    "7-1": "Number of resources that have blacklisted based on extension the crawler is allowed to retrieve. Even if the resource should be blacklisted based on extension, InsightAppSec will still crawl a small number of those resources the number of resources specified in this parameter. This value is per domain.\n\nDefault value: 100",
    "8-1": "Maximum number of new links discovered in attack traffic the crawler will insert in the queue.\nCrawler monitors traffic of attack modules and tries to find new links in the traffic. This parameter specified maximum number of new Web Resource found in the responses received by attack modules. Some attack requests result is responses that contain some of the attack payload or invalid links. \n\nConsider this example: It is very common for website to return a reference to a URL that could help user to solve the problem. That reference often include the description of the problem. For instance, if the attack set the following request:\nGET /users/userinfo?userid=alert(‘111’), the response to the attack could have the following statement (and a new link):\n\nInvalid parameter to the request /users/userinfo?userid=alert(‘111’)\n<a href=”/mgmt/reporterror.php=Invalid parameter URL: /users/userinfo?userid=alert(‘111’)”>Report error</a>\n\nClearly, every attack would result in new Web Resource ‘/mgmt/reporterror.php’ with different parameter values. While it make sense to analyze that web resource once, it does not make to analyze all of those web resources. \nInsightAppSec tries automatically detect those invalid links and avoid crawling them;  this configuration parameter is a safety net in case invalid link detection algorithm fails. \n\nDefault value: 300",
    "9-1": "Maximum number of Web Resources with the same file name the crawler is allowed to analyze. \nDuring counting number of resources, only file name of the URL is considered and path is ignored). For instance the following two URLs are considered to have the same File Name\n\nhttp://mysite/customers/get_address.php?id=23\nhttp://mysite/suppliers/get_address.php?id=78,\n\nbecause the filename is the same for both URLs.\n\nDefault value: 250",
    "10-1": "Maximum repetition that InsightAppSec will tolerate in URL. This parameter defines how many times a part of a URL can be repeated. For instance, in the example below, if the recursion depth is set to 2, URL #1 will be crawled, while the URL #2 will be ignored because its recursion depth is 3.\nURL 1:  www.site.com/dir1/dir2/dir1/dir2/file.txt\nURL 2: www.site.com/dir1/dir2/dir1/dir2/dir1/dir2/file.txt\n\nDefault value: 2",
    "11-1": "Maximum number of directories InsightAppSec will look into. URLs that have more directories in their path than the value of this parameters will be ignored. For instance, URL www.site.com/dir1/dir2/dir3/file.html will be ignored if MaxDirDepth parameter is set to value smaller than 3. \n\nDefault value: 10",
    "12-1": "Maximum discovery depth that InsightAppSec can go into the site. Discovery depth of a URL is the number of steps (URL navigations) it is required for the user to discover the link.\n\nDefault value: -1 (Unlimited)",
    "13-1": "Maximum number of identical normalized URLs InsightAppSec is allowed to crawl. Normalized URL is the URL without query parameter values.\n\nDefault value: 25",
    "14-1": "Maximum number of similar sequences that InsightAppSec will try to follow.\n\nDefault value: 5",
    "15-1": "Maximum number of discovered Image links that InsightAppSec should store in the database.\n\nDefault value: 500",
    "16-1": "This parameter defines maximum number of discovered Web Resources that InsightAppSec should store in the database in addition to Web Resources that will be crawled by the crawler. \nThe crawler almost always sees more links that it will crawl. Often it discovers many times more links that it will crawl. Many Web Resources are ignored because one or more crawler limitation. This parameter describes how many Web Resources will be store in the database on top of the Web Resources  that were be crawled. While Web Resources take significantly less space in the database then Crawl Results, they still take some space, so it is recommended to keep this number below the value specified in parameter MaxCrawlResults.\n\nDefault value: 2500",
    "17-1": "Maximum number of discovered HTML comments that InsightAppSec should store in the database.\n\nDefault value: 500",
    "18-1": "Maximum number of discovered SCRIPTs that InsightAppSec should store in the database.\n\nDefault value: 500",
    "19-1": "Maximum number of discovered Email addresses that InsightAppSec should store in the database.\n\nDefault value: 500",
    "20-1": "Maximum number of discovered forms that InsightAppSec should store in the database.\n\nDefault value: 500",
    "21-1": "Maximum time InsightAppSec should wait for the Browser component to load the page and perform all operations.\n\nDefault value: 60000 ms (60 seconds)",
    "22-1": "Maximum time InsightAppSec should wait for the javascript on the page to send an AJAX request to the server after firing an event (for example, 'onclick' or 'onmouseover').\n\nDefault value: 4000 ms (4 seconds)",
    "23-1": "Maximum depth of DOMs that InsightAppSec should try to analyze within an HTML page. DOM depth is minimum number of user actions (events) that are required to reach that DOM from the initial DOM of the page.\n\nDefault value: 4",
    "24-1": "Maximum number of javascript events InsightAppSec should fire per one link. A link is a URL without a query parameter and the fragment.\n\nDefault value: 200",
    "25-1": "Maximum number of javascript events InsightAppSec should fire per one web resource.\n\nDefault value: 100",
    "26-1": "Maximum number of javascript events InsightAppSec should fire per one DOM view.\n\nDefault value: 100",
    "27-1": "",
    "28-1": "Maximum number of ignored links that should be reported in the User Log\nInsightAppSec reports ignored links in the User Log so that the user could easily notice that some URLs were unintentionally ignored and correct the problem by modifying scan configuration settings. In most cases if scan is configured incorrectly, first several ignored URLs show the problem.\n\nNote that only important messages should be reported in User Log. InsightAppSec ignores many links during crawling (for instance, out-of-domain links), on an average site the number of ignore links can be in thousands. To avoid cluttering User Log, it is recommended to keep this number low.\n\nDefault value: 2",
    "31-1": "This parameter defines the algorithm that will be used to crawl the site.\n\nValues:\n  * **FIFO**\n  * **Smart**\n  * **DirBreadthFirst**\n  * **FoundBreadthFirst**\n  * **FoundDepthFirst**\n  * **Juicy**\n  * **LoginFormDiscovery**\n  * **Login**\n\nDefault value: Smart\n",
    "32-1": "Regular Expression that is used by InsightAppSec to identify custom 404 responses (File not found).\n\nDefault value: (page|resource) (you requested )?(was not|cannot be) found|Page not found|404(.0)? - ((File (or directory )?not found)|(Not Found))|HTTP Status 404|404 Not Found",
    "33-1": "Regular Expression that is used by InsightAppSec to identify error responses from the web server.\n\nDefault value: Empty",
    "34-1": "Regular Expression that identifies URLs that comes from attack traffic as Invalid so that InsightAppSec does not attack an invalid URL.\n\nDefault value: ['\\\"\\\\(\\\\)<>]|\\\\d([-+]|%2[bd])\\\\d|repeat\\\\(|alert\\\\(|/x\\\\w{7}\\\\.txt|window.location|%20(AND|OR)%20|%3cscript|(ping|echo)%20|javascript(%3a|:)|%0d%0a",
    "35-1": "Regular Expression that identifies a URL that was discovered during crawling as Invalid so that InsightAppSec does not crawl and analyze an invalid URL.\n\nDefault value: (([ ]|%20)(MOD|ASC|DESC)([ ]|%20)|(<|%3c)(a|div|script|style|iframe|img|svg)|[?&=]x[a-z0-9]{7}$|C=N;O=D|\\\\?C=M)|(ping|echo)%20|javascript(%3a|:)|%0d%0ax",
    "36-1": "Flags that tells InsightAppSec whether it should preserve the value of the cookies supplied by the user in the Scan Configuration even if the web server requested to change the cookie.\n\nValues:\n  * **Enabled** - Lock cookie values\n  * **Disabled** - Do not lock cookie values\n\nDefault value: Enabled",
    "37-1": "This parameter tells InsightAppSec how to treat URLs of the web site. The website can have either a case sensitive or a case insensitive file system on the back end.\n\nValues:\n  * **AutoDetect**\n  * **CaseSensitive**\n  * **CaseInsensitive** \n\nDefault value: CaseSensitive",
    "38-1": "This parameter controls whether the crawler should store cross-references in the database. Note that storing references significantly increases the size of the database, and it is advised not to enable this feature.\n\nValues:\n  * **Enabled** - Store cross-references\n  * **Disabled** - Do not store cross-references\n\nDefault value: Disabled",
    "39-1": "Flag that tells the crawler to use browser to execute javascript event handlers. This flag only affect using browser for crawling. It has no affect on using browser for Macros, Sequences or attacks.\n\nValues:\n  * **Enabled** - Use browser\n  * **Disabled** - Do not use browser\n\nDefault value: Enabled",
    "40-1": "Flag that tells the crawler to show browser window during traversing web site's pages. \n\nThis flag was designed to be used to debug various crawling problems. It is advised to disable this feature for regular scans. \n\nIf this feature enabled, it is recommended to make the scan Single-Threaded. This way, only one browser window will be shown at any given moment.\n\nValues: \n  * **Enabled** - Show browser\n  * **Disabled** - Do not show browser\n \nDefault value: Disabled",
    "41-1": "Flag that tells the crawler to not deviate from the port of original seed URLs. This implies that all seed URLs should be on the same port if that option is enabled.\n\nValues:\n  * **Enabled** - The crawler should stay on port\n  * **Disabled** - The crawler can request URLs from other ports\n\nDefault: Disabled (the crawler can request URLs from other ports)",
    "42-1": "This flag forces InsightAppSec to not crawl any links other than the requests sent during macro execution.\n\nValues:\nEnabled - Crawler should not try to discover new links.\nDisabled - Crawler can discover new links\n\nDefault value: Disabled",
    "56-1": "This flags tells InsightAppSec how many links it can add to the crawl queue over the value specified in MaxCrawlResults parameter. Those extra links provide the Crawler with ability to pick more promising links to crawl. Without that parameter, the crawler would stop looking for new links once the queue is full.\nNote that even if those extra resources are added to the queue, the crawler will stop crawling once it reached the crawled number of links specified in the MaxCrawlResult option.\n\nDefault value: 1000",
    "54-1": "This flags tells InsightAppSec whether it should try to find URLs in places other than HTML structure: comments, javascript text, etc.\nFor example, consider the following HTML page with an HTML comment block:\n\n```\n<a href=”/admin/show_users.php”>Show Users</a><br>\n<!-- \n  Do not forget that we need to remove ‘/admin/rebootserver.php’ when we are done debugging\n- -->\n<a href=”/admin/server_info.php”>Server Information</a>\n```\n\nIf this flag is set to ‘1’, InsightAppSec will find URL ‘/admin/rebootserver.php’. If the flag is set to ‘0’, InsightAppSec won’t find/analyze/attack that URL.\n\nValues:\n  * **Enabled** - Should look for URLs in non-standard locations\n  * **Disabled** - Should not look for URLs in non-standard locations\n\nDefault value: Enabled",
    "53-1": "Internal parameter. The value provided in the scan configuration file is overwritten",
    "52-1": "This flags tells InsightAppSec whether it should analyze Flash files.\n\nValues:\n  * **Enabled** - Should analyze Flash files\n  * **Disabled** - Should not analyze Flash files\n\nDefault value: Enabled",
    "50-1": "This parameter sets the minimum value of the similarity coefficient above which two pages are considered to have same structure.\nThis parameter was introduced to deal with pages that return logically equivalent responses. For example, the shopping cart’s checkout page with a sweater in the shopping cart will look very similar to the page with a scarf in the shopping cart. This parameter helps InsightAppSec to understand what pages are similar. Several attacks and the analyzer use analysis for page similarity.\n\nThis parameter controls a proprietary algorithm that determines similarity of the pages. The more similar the pages are, the higher is their similarity coefficient. Two responses with with similarity coefficient above the value of the parameter are considered by InsightAppSec to be similar. It is recommended to not change the value of this parameter. \n\nDefault value: 0.80",
    "49-1": "This parameter sets the minimum value of the similarity coefficient above which two pages are considered to be identical.\n\nThis parameter was introduced to deal with randomness in the responses. Some pages always have advertisement frames that website randomly inserts in the responses. This parameter allows InsightAppSec to ignore that random content.\n\nThis parameter controls a proprietary algorithm that determines similarity of the pages. The more similar the pages are, the higher is their similarity coefficient. Two responses with with similarity coefficient above the value of the parameter are considered by InsightAppSec to be identical. This information is used in several components in InsightAppSec: when comparing responses with custom 404 response, to determine whether that response is seen too often and can be ignored, etc. It is recommended to not change the value of this parameter. \n\nDefault value: 0.95",
    "48-1": "This flag controls what InsightAppSec does with cookies that it finds in the imported traffic.",
    "46-1": "This flag forces InsightAppSec to not crawl any links other than requests performed during execution of Selenium scripts. \n\nValues:\nEnabled - Crawler should not try to discover new links.\nDisabled - Crawler can discover new links\n\nDefault value: Disabled",
    "45-1": "This flag forces InsightAppSec to not crawl any links other than the web service requests. \n\nValues:\nEnabled - Crawler should not try to discover new links.\nDisabled - Crawler can discover new links\n\nDefault value: Disabled",
    "44-1": "This flag forces InsightAppSec to not crawl any links other than the seed links provided in the scan configuration. \n\nValues:\nEnabled - Crawler should not try to discover new links.\nDisabled - Crawler can discover new links\n\nDefault value: Disabled",
    "43-1": "This flag forces InsightAppSec to not crawl any links other than the requests imported from proxy logs.\n\nIf Enabled, InsightAppSec will analyzed/attacked only the requests that it imported from the proxy logs. If imported responses contain other links, those links will not be crawler/analyzed/attacked. So, if the imported traffic has five requests, only five requests will be analyzed/attacked.\n\nValues:\nEnabled - Crawler should not try to discover new links.\nDisabled - Crawler can discover new links\n\nDefault value: Disabled"
  },
  "cols": 2,
  "rows": 57
}
[/block]

## CrawlConfig's Lists 

| **Property**                        | **Description**                                                                                                                                                                                     |
| - - --------------------------------- | - - ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| SeedUrlList                         | List of seed URLs from which InsightAppSec should start the scan.                                                                                                                                       |
| ScopeConstraintList                 | This parameter contains rules that specify what URLs InsightAppSec should crawl                                                                                                                         |
| BlackListExtensionList              | List of extensions that the crawler is not allowed to crawl. See parameter *MaxBlackListExtCrawlResults* for the details.                                                                           |
| GrayListExtensionList               | List of extensions that the crawler is not allowed to crawl if Web Resource with the specified extensions do not have query parameters. See parameter *MaxBlackListExtCrawlResults* for the details |
| BinaryExtensionList                 | List of file extensions that usually files with binary content have                                                                                                                                 |
| TextExtensionList                   | List of file extensions that usually files with text content have                                                                                                                                   |
| BinaryContentTypeList               | List of content types that identify files with binary content                                                                                                                                       |
| HTMLContentTypeList                 | List of content types that identify HTML content                                                                                                                                                    |
| TextContentTypeList                 | List of content types that identify text content                                                                                                                                                    |
| XMLContentTypeList                  | List of content types that identify XML content                                                                                                                                                     |
| BrowserDownloadWhitelistList        | List of URLs that browser should always download (for example, javascript files)                                                                                                                    |
| BrowserDoNotDownloadExtentionList   | List of file extensions that should not be downloaded even if they were requested by the browser                                                                                                    |
| BrowserDoNotDownloadContentTypeList | List of content type of files that should not be downloaded even if they were requested by the browser                                                                                              |
| LockedCookieList                    | List of cookie names that should not change value for the duration of the scan                                                                                                                      |

# AttackerConfig Structure

## AttackerConfig 's Scalar Values
[block:parameters]
{
  "data": {
    "h-0": "Property",
    "h-1": "Description",
    "0-0": "ParametersToAttackBeforeLimitingAttacks",
    "1-0": "LinksToAttackBeforeLimitingAttacks",
    "2-0": "MaxSameNameParameterAttackPoints",
    "3-0": "MaxSameCookieParameterAttackPoints",
    "4-0": "MaxSameNameParameterAttackPointsPerLink",
    "5-0": "MaxParameterAttackPointsPerLink",
    "6-0": "MaxNormalizedSameNameParameterAttackPointsPerLink",
    "7-0": "ApplyGlobalFindingsSettings",
    "8-0": "ApplyCrawlerConstraints",
    "9-0": "MaxNumberOfScheduledPassiveAttacks",
    "10-0": "MinCookieLifetimeForAttacks",
    "11-0": "ExcludeLowConfidenceFindings",
    "2-1": "This parameter determines how many parameter values that have the same name (query or POST) InsightAppSec is going to attack. \n\nDefault value: 25",
    "3-1": "This parameter determines on how many pages a cookie can be attacked by InsightAppSec.\n\nDefault value: 15",
    "4-1": "This parameter determines how many parameter values that have the same name (query or POST) InsightAppSec is going to attack on links that have the same URL. \n\nDefault value: 2",
    "5-1": "This parameter determines how many parameters InsightAppSec is going to attack on URLs that have the same URL. \n\nDefault value: 50",
    "6-1": "This parameter determines how many parameters with the same normalized name InsightAppSec is going to attack on links that have the same URL. Normalized name is the name of the parameter without array index or any other indexing type. \nFor instance if a page has parameter params[1], params[2], params[3], all those parameters will have the same normalized name: params[]\n\nDefault value: 4"
  },
  "cols": 2,
  "rows": 12
}
[/block]

## AttackerConfig's Lists
                                                                  
| Property                    | Description                                                                                                                                                                                                                                          |
| - - --------------------------------- | - - ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| ScopeConstraintList         | List of scope constraints that determines which URLs InsightAppSec can attack. Note that even if the that list is empty ,InsightAppSec will not attack URLs that do not comply with constraints specified for the crawler in CrawlConfig.ScopeConstraintList |
| DefaultDoNotAttackParamList | List of parameter names that InsightAppSec should not attack. This list should not be changed by the user. For convenience, user-defined parameters that should not be attacked are moved into a separate parameter: UserDoNotAttackParamList            |
| UserDoNotAttackParamList    | List of parameter that InsightAppSec should not attack.                                                                                                                                                                                                  |

## AnalyzerConfig's Scalar Values

[block:parameters]
{
  "data": {
    "h-0": "Property",
    "h-1": "Description",
    "0-0": "NotExistingFilePath",
    "1-0": "NotExistingDirPath",
    "2-0": "AppendToOriginalValue",
    "3-0": "ReplaceOriginalValue",
    "0-1": "This parameter defines the URL request that InsightAppSec sends to retrieve the response that the web server returns for a  non-existing file path. The value of that parameter is appended to the URL of the directory.\n\nDefault value: /aaaaaaaa.aaa",
    "1-1": "This parameter defines the URL request that InsightAppSec sends to retrieve the response that the web server returns for a non-existing directory path. The value of that parameter is appended to the URL of the directory.\n\nDefault value: /aaaaaaaa/"
  },
  "cols": 2,
  "rows": 4
}
[/block]
# AuthConfig Structure

AuthConfig data structure describes parameters required for
authentication.

## AuthConfig's Scalar Values
[block:parameters]
{
  "data": {
    "h-0": "Property",
    "h-1": "Description",
    "0-0": "Type",
    "1-0": "HttpAuth",
    "2-0": "OAuth",
    "3-0": "ReloginAfterSessionLoss",
    "4-0": "LogoutDetection",
    "5-0": "UserAssistance",
    "6-0": "AssumeSuccessfulLogin",
    "7-0": "VerifyNotLoggedin",
    "8-0": "PostponeLoginAction",
    "9-0": "CreateNonAuthenticatedSession",
    "10-0": "TreatFailedReloginAsError",
    "11-0": "RestartProxyBeforeRelogin",
    "12-0": "BlacklistSinglePasswordForms",
    "13-0": "BlacklistMultiPasswordForms",
    "14-0": "ResetCookies",
    "15-0": "AccountType",
    "16-0": "UsernameForm",
    "17-0": "PasswordForm",
    "18-0": "UsernameHttp",
    "19-0": "PasswordHttp",
    "20-0": "AutoLogonSecurity",
    "21-0": "LoginLinkRegex",
    "22-0": "LoggedInRegex",
    "23-0": "LoggedInHeaderRegex",
    "24-0": "SessionLossRegex",
    "25-0": "SessionLossHeaderRegex",
    "26-0": "LogoutLinkRegex",
    "27-0": "LogoutPostBodyRegex",
    "28-0": "CanaryPage",
    "29-0": "SessionLossOnCanaryPageRegex",
    "30-0": "FormSubmissionScript",
    "31-0": "SessionCookieRegex",
    "32-0": "SessionCookieLifespan",
    "33-0": "URLSessionTokenRegex",
    "34-0": "PostSessionTokenRegex",
    "35-0": "ResponseBodyTokenRegex",
    "36-0": "HTTPHeaderWithTokenReplacement",
    "37-0": "DiscoveryMaxLinks",
    "38-0": "LoginMaxLinks",
    "39-0": "DiscoveryDepth",
    "40-0": "LoginDepth",
    "41-0": "MaxMacroReloginAttempts",
    "42-0": "DiscoveryPrioritization",
    "43-0": "LoginPrioritization",
    "44-0": "BootstrapDelay",
    "45-0": "SeedLink",
    "46-0": "DiscoverLoginForm",
    "47-0": "UseBrowserFormLogin",
    "48-0": "PingFrequency",
    "49-0": "PingURL",
    "0-1": "This parameter defines the type of authentication that will be used by InsightAppSec.\n\nValues:\n  * **None** - No authentication\n  * **Form** - Form-based automatic authentication\n  * **Macro** - Macro is used to authenticate the user. The macro should be specified in parameter 'MacroFile'\n  * **SessionTakeover** - The user will provide session cookies\n  * **SSORedirect**\n  * **Bootstrap**\n\nDefault value: None",
    "1-1": "Flag that tells that InsightAppSec should use HTTP username and password from the config to login to site that use HTTP authentication (Basic, NTLM, Kerberos, etc)\n\nValues:\n  * **Enabled** - Should use HTTP authentication credentials\n  * **Disabled** - Should not use HTTP authentication credentials \n\nDefault value: **Disabled** ",
    "3-1": "Flag that specifies whether InsightAppSec should re-login after it detected session loss.\n\nValues:\n  * **Enabled** - Should re-login\n  * **Disabled** - Should not re-login \n\nDefault value: **Enabled**",
    "4-1": "Flag that specifies whether InsightAppSec should try to detect whether it lost the session.\n\nValues:\n  * **Enabled** - Should detect session loss\n  * **Disabled** - Should not detect session loss\n\nDefault value: **Enabled**",
    "6-1": "Flag that defines whether InsightAppSec should check if the user was logged in using the regular expression in parameter LoggedInRegex or it can just assume that the user was logged in.\nThis parameter is often used in conjunction with macro login when the user can see in the browser that InsightAppSec logged in and does not want to craft a regular expression that detects a logged in state.\n\nValues:\n  * **Enabled** - Assume that the user was logged in.\n  * **Disabled** - Use regular expression to detect whether the user was logged in.\n\nDefault value: **Disabled**",
    "7-1": "This flag defines whether InsightAppSec should verify that the session is not logged in before trying to re-login. If the session was logged in and that flag is set, InsightAppSec will not try to re-login.\nIf during scanning a false positive logout was detected on one of the responses , InsightAppSec will try to re-login into session that is perfectly valid. This parameter configures how InsightAppSec behaves in this situations. If the value of the parameter is set to 'Enabled', InsightAppSec first check whether the user is already login, prior to starting login process. If it is set to ‘Disabled’, InsightAppSec will reset session \nValues:\n  * **Enabled** - InsightAppSec will verify whether the session was logged in.\n  * **Disabled** - InsightAppSec will verify whether the session was not logged in\n\nDefault value: **Enabled**",
    "8-1": "Flag that tells InsightAppSec whether it should postpone crawling the link if the is defined in the action attribute of the login form\n\nValues:\n  * **Enabled** - InsightAppSec will postpone crawling of the action link.\n  * **Disabled** - InsightAppSec will crawl the action link.\n\nDefault value: **Enabled**",
    "9-1": "Flag that determines whether InsightAppSec should create a non-authenticated session along with the authenticated session. This flag should only be set if the user provided authentication information in the scan configuration: login macro, username and password for form authentication, etc.\n\nValues:\n  * **Enabled** - Create non-authenticated session.\n  * **Disabled** - Do not create non-authenticated session\n\nDefault value: **Disabled**",
    "10-1": "The flag that tells InsightAppSec what to do when it fails to re-login the user. If that flag is set, then the scan will stop if relogin is failed. If the flag is not set then InsightAppSec continues with the scan with the logged out session. Note that the initial login is always treated as an error. \n\nValues:\n  * **Enabled** - Consider re-login failure as an error.\n  * **Disabled** - Do not treat re-login failure as an error and continue with the scan.\n\nDefault value: **Enabled**",
    "12-1": "This flag determines whether the crawler should send requests from forms that have one password field.\n\nValues:\n  * **Enabled** - Do not crawl forms with one password field\n  * **Disabled** - Allowed to crawl forms with one password field\n\nDefault value: **Disabled**",
    "13-1": "This flag determines whether the crawler should send requests from forms that have two password fields.\n\nValues:\n  * **Enabled** - Do not crawl forms with two password fields\n  * **Disabled** - Allowed to crawl forms with two password fields\n\nDefault value: **Enabled**",
    "14-1": "This flag tells InsightAppSec whether it should reset all cookies before every re-login.\n\nValues:\n  * **Enabled** - Reset all cookies.\n  * **Disabled** - Do not reset cookies that were in the session before re-login\n\nDefault value: **Enabled**",
    "43-1": "This parameter determines the algorithm the crawler should use after the submission of login form to find the page would indicate a logged in state. (e.g. “Welcome back to acme.com Bob”)\nIt is not recommended to change the value from this parameter from the one selected by InsightAppSec by default.\n\nValues:\n  * **FIFO**\n  * **Smart**\n  * **DirBreadthFirst**\n  * **FoundBreadthFirst**\n  * **FoundDepthFirst**\n  * **Juicy**\n  * **LoginFormDiscovery**\n  * **Login**\n\nDefault value: **Login**",
    "42-1": "This parameter determines the algorithm the login form discovery crawler should use.\nIt is not recommended to change the value from this parameter from the one selected by InsightAppSec by default.\n\nValues:\n  * **FIFO**\n  * **Smart**\n  * **DirBreadthFirst**\n  * **FoundBreadthFirst**\n  * **FoundDepthFirst**\n  * **Juicy**\n  * **LoginFormDiscovery**\n  * **Login**\n\nDefault value: **LoginFormDiscovery**",
    "41-1": "Maximum number of times InsightAppSec should try to re-login. Note that this parameter is not used for initial login, which is performed only once.\n\nDefault value: 3",
    "40-1": "This parameter determines how deep into the web site the crawler should go after the submitting login form in search of the page that can determine a logged in state. The depth of a link is the minimum number of links (steps) that the user should visit to discover this links starting from the page with the login form\n\nDefault value: 10",
    "39-1": "This parameter determines how deep into the web site the crawler should go in search of the login form. The depth of a link is the minimum number of links (steps) that the user should visit to discover this link.\n\nDefault value: 10",
    "38-1": "This parameter defines the maximum number of links that the login component can crawl after submitting a login form while it is looking for the page that indicates that the user session was logged in.\n\nDefault value: 50",
    "37-1": "This parameter defines maximum number links that the login component can crawl in search for a login form\n\nDefault value: 200",
    "32-1": "This parameter determines the maximum lifespan of the cookie below which the cookie is considered a session cookie.\n\nDefault value: 32 (days)",
    "31-1": "This parameter contains the regular expression that InsightAppSec uses to determine whether a cookie is a session cookie. The regular expression is applied to the cookie’s name only.\n\nDefault value: \\\\b(CFID|CFTOKEN|SESSION|JSESSIONID|ASPSESSIONID[A-Z0-9]+|PHPSESSID|ASP[.]NET_SessionId)\\\\b",
    "29-1": "Defines the regular expression that InsightAppSec uses to determine whether a request with POST data can cause session logout. This helps InsightAppSec to stay logged in by not clicking on or requesting  logout links.\nNote that this parameter should be used in conjunction with parameter CanaryPage.\n\nDefault value: None",
    "28-1": "Defines the URL that InsightAppSec will periodically request to determine whether the session was lost.\nNote that this parameter should be used in conjunction with parameter SessionLossOnCanaryPageRegex.\n\nDefault value: None",
    "27-1": "Defines the regular expression that InsightAppSec uses to determine whether a request with POST data can cause session logout. This helps InsightAppSec to stay logged in by not clicking on or requesting  logout links.\n\nDefault value: (sign|log|time)[ -]?(in|on|out|off)",
    "26-1": "Defines the regular expression that InsightAppSec uses to determine whether a link is a logout link. This helps InsightAppSec to stay logged in by not clicking on or requesting  logout links.\n\nDefault value: (sign|log|time)[ -]?(in|on|out|off)|password",
    "25-1": "Defines the regular expression that InsightAppSec uses to determine whether the user was logged out. This regex is only applied to HTTP response body.\nInsightAppSec applies that regex to all responses (as opposed to regular expression in SessionLossOnCanaryPageRegex).\n\nDefault value: please (re)?login|have been logged out|session has expired",
    "24-1": "Defines the regular expression that InsightAppSec uses to determine whether the user was logged out. This regex is only applied to HTTP response body.\nInsightAppSec applies that regex to all responses (as opposed to regular expression in SessionLossOnCanaryPageRegex).\n\nDefault value: please (re)?login|have been logged out|session has expired",
    "22-1": "Defines the regular expression that InsightAppSec uses to determine whether the user was logged in as a result of login macro execution or login form submission or any other type of supported authentication.\n\nDefault value: (sign|log)[ -]?(out|off)",
    "21-1": "Defines the regular expression that InsightAppSec uses to determine whether a link is a login link (link used in login process)\n\nDefault value: ((log|sign)[ -]?(in|on))|auth",
    "20-1": "This parameter defines the scope for which InsightAppSec should use Windows user identity for Integrated Windows Authentication. \n\nValues:\n  * **AutoLogonSecurityLow** - An authenticated log on using the default credentials is performed for all requests\n  * **AutoLogonSecurityMedium** - An authenticated log on using the default credentials is performed only for requests on the local Intranet\n  * **AutoLogonSecurityHigh** - Default credentials are not used. Note that this flag takes effect only if you specify the server by the actual machine name. It will not take effect, if you specify the server by \"localhost\" or IP address.\n\nDefault value: **AutoLogonSecurityMedium**",
    "19-1": "The user password that will be used for HTTP authentication (Basic, NTLM or Kerberos)\n\nDefault value: None",
    "18-1": "The user name that will be used for HTTP authentication (Basic, NTLM or Kerberos). Note that for NTLM authentication with domain, the format of username should be <domain>/<username>. \n\nDefault value: None",
    "17-1": "The user password that will be used for form authentication. This parameter is only used if parameter Type is set to ‘Form’.\n\nDefault value: None",
    "16-1": "The user name that will be used for form authentication. This parameter is only used if parameter Type is set to ‘Form’.\n\nDefault value: None"
  },
  "cols": 2,
  "rows": 50
}
[/block]
## AuthConfig's Objects

| **Property** | **Description**                                                                                                        |
| - - ---------- | - - -------------------------------------------------------------------------------------------------------------------- |
| MacroFile    | Macro file that will be used for authentication. Note that this parameter is used only if Type value is set to 'Macro' |

## AuthConfig's Lists 

| **Property**        | **Description**                                                                                                                                                                                         |
| - - ----------------- | - - ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| ScopeConstraintList | List of scope constraints for the login crawler that determine which part of the site the login crawler is allowed to crawl. Note that this parameter is only used when the Type value is set to 'Form' |