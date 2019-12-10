---
title: "Using regular expressions"
excerpt: ""
---
A regular expression, also known as a “regex,” is a text string used for searching for a piece of information or a message that an application will display in a given situation. Regex notation patterns can include letters, numbers, and special characters, such as dots, question marks, plus signs, parentheses, and asterisks. These patterns instruct a search application not only what string to search for, but how to search for it.

Regular expressions are useful in configuring scan activities:
* searching for file names on local drives; see [How the file name search works with regex](doc:using-regular-expressions#section-how-the-file-name-search-works-with-regex)
* searching for certain results of logon attempts to Telnet servers; see [Configuring scans of Telnet servers](doc:configuring-scans-of-various-types-of-servers#section-configuring-scans-of-telnet-servers)
* determining if a logon attempt to a Web server is successful; see [How to use regular expressions when logging on to a Web site](doc:using-regular-expressions#section-how-to-use-regular-expressions-when-logging-on-to-a-web-site)

##General notes about creating a regex

A regex can be a simple pattern consisting of characters for which you want to find a direct match. For example, the pattern _nap_ matches character combinations in strings only when exactly the characters _n_, _a_, and _p_ occur together and in that exact sequence. A search on this pattern would return matches with strings such as _snap_ and _synapse_. In both cases the match is with the substring _nap_. There is no match in the string an _aperture_ because it does not contain the substring _nap_.

When a search requires a result other than a direct match, such as one or more n's or white space, the pattern requires special characters. For example, the pattern _ab*c_ matches any character combination in which a single _a_ is followed by 0 or more _bs_ and then immediately followed by _c_. The asterisk indicates 0 or more occurrences of the preceding character. In the string _cbbabbbbcdebc_, the pattern matches the substring _abbbbc_.

The asterisk is one example of how you can use a special character to modify a search. You can create various types of search parameters using other single and combined special characters.

##How the file name search works with regex

InsightVM searches for matching files by comparing the search string against the entire directory path and file name. See [Configuring file searches on target systems](doc:configuring-file-searches-on-target-systems). Files and directories appear in the results table if they have any greedy matches against the search pattern. If you don't include regex anchors, such ^ and $, the search can result in multiple matches. Refer to the following examples to further understand how the search algorithm works with regular expressions. Note that the search matches are in **bold** typeface.

With search pattern _.*xls_

* the following search input,
C$/Documents and Settings/user/My Documents/patientData.xls
results in one match:
C$/Documents and Settings/user/My Documents/patientData.xls
* the following search input,
C$/Documents and Settings/user/My Documents/patientData.doc
results in no matches
*the following search input,
C$/Documents and Settings/user/My Documents/xls/patientData.xls
results in one match:
C$/Documents and Settings/user/My Documents/xls/patientData.xls
* the following search input,
C$/Documents and Settings/user/My Documents/xls/patientData.doc
results in one match:
C$/Documents and Settings/user/My Documents/xls/patientData.doc

With search pattern^.*xls$:
* the following search input,
C$/Documents and Settings/user/My Documents/patientData.xls
results in one match:
C$/Documents and Settings/user/My Documents/patientData.xls
* the following search input,
C$/Documents and Settings/user/My Documents/patientData.docresults in no matches

##How to use regular expressions when logging on to a Web site

When InsightVM makes a successful attempt to log on to a Web application, the Web server returns an HTML page that a user typically sees after a successful logon. If the logon attempt fails, the Web server returns an HTML page with a failure message, such as “Invalid password.”

Configuring the application to log on to a Web application with an HTML form or HTTP headers involves specifying a regex for the failure message. During the logon process, it attempts to match the regex against the HTML page with the failure message. If there is a match, the application recognizes that the attempt failed. It then displays a failure notification in the scan logs and in the Security Console Web interface. If there is no match, the application recognizes that the attempt was successful and proceeds with the scan.