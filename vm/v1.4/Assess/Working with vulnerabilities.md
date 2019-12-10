---
title: "Working with vulnerabilities"
excerpt: ""
---
Analyzing the vulnerabilities discovered in scans is a critical step in improving your security posture. By examining the frequency, affected assets, risk level, exploitability and other characteristics of a vulnerability, you can prioritize its remediation and manage your security resources effectively.

Every vulnerability discovered in the scanning process is added to vulnerability database. This extensive, full-text, searchable database also stores information on patches, downloadable fixes, and reference content about security weaknesses. The application keeps the database current through a subscription service that maintains and updates vulnerability definitions and links. It contacts this service for new information every six hours.

The database has been certified to be compatible with the MITRE Corporation’s Common Vulnerabilities and Exposures (CVE) index, which standardizes the names of vulnerabilities across diverse security products and vendors. The index rates vulnerabilities according to MITRE’s Common Vulnerabilities Scoring System (CVSS) Version 2 and Version 3, if it is available.

An application algorithm computes the CVSS score based on ease of exploit, remote execution capability, credentialed access requirement, and other criteria. The score, which ranges from 1.0 to 10.0, is used in Payment Card Industry (PCI) compliance testing. For more information about CVSS scoring, go to the FIRST Web site [https://www.first.org/cvss/](https://www.first.org/cvss/).

##Viewing active vulnerabilities

Viewing vulnerabilities and their risk scores helps you to prioritize remediation projects. You also can find out which vulnerabilities have exploits available, enabling you to verify those vulnerabilities. See [Using Exploit Exposure](doc:using-exploit-exposure).

Click the **Vulnerabilities** icon that appears on every page of the console interface.

The Security Console displays the _Vulnerabilities_ page, which lists all the vulnerabilities for assets that the currently logged-on user is authorized to see, depending on that user’s permissions. Since Global Administrators have access to all assets in your organization, they will see all the vulnerabilities in the database.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/f74dda9-s_nx_vulnerabilities_page.jpg",
        "s_nx_vulnerabilities_page.jpg",
        1981,
        1439,
        "#edf0f1"
      ],
      "caption": "The Vulnerabilities page"
    }
  ]
}
[/block]
The charts on the _Vulnerabilities_ page display your vulnerabilities by CVSS score and exploitable skill levels. The _CVSS Score chart_ displays how many of your vulnerabilities fall into each of the CVSS score ranges. This score is based on access complexity, required authentication, and impact on data. The score ranges from 1 to 10, with 10 being the worst, so you should prioritize the vulnerabilities with the higher numbers.

The _Exploitable Vulnerabilities by Skill Level_ chart shows you your vulnerabilities categorized by the level of skill required to exploit them. The most easily exploitable vulnerabilities present the greatest threat, since there will be more people who possess the necessary skills, so you should prioritize remediating the Novice-level ones and work your way up to Expert.

You can change the sorting criteria by clicking any of the column headings in the _Vulnerability Listing_ table.

The _Title_ column lists the name of each vulnerability.

Two columns indicate whether each vulnerability exposes your assets to malware attacks or exploits. Sorting entries according to either of these criteria helps you to determine at a glance which vulnerabilities may require immediate attention because they increase the likelihood of compromise.

For each discovered vulnerability that has at least one malware kit (also known as an _exploit kit_) associated with it, the console displays a malware exposure icon ![Alt](https://files.readme.io/8067dd3-i_malware.jpg). If you click the icon, the console displays the _Threat Listing_ pop-up window that lists all the malware kits that attackers can use to write and deploy malicious code for attacking your environment through the vulnerability. You can generate a comma-separated values (CSV) file of the malware kit list to share with others in your organization. Click the **Export to CSV** icon ![Alt](https://files.readme.io/9243f42-i_csvexport.jpg). Depending on your browser settings, you will see a pop-up window with options to save the file or open it in a compatible program.

You can also click the **Exploits** tab in the pop-up window to view published exploits for the vulnerability.

In the context of the application a _published_ exploit is one that has been developed in Metasploit or listed in the Exploit Database [www.exploit-db.com](https://www.exploit-db.com).

For each discovered vulnerability with an associated exploit the console displays a exploit icon. If you click this icon the console displays the _Threat Listing_ pop-up window that lists descriptions about all available exploits, their required skill levels, and their online sources. The Exploit Database ![Alt](https://files.readme.io/03c46ce-i_db_exploit.jpg) is an archive of exploits and vulnerable software. If a Metasploit exploit is available, the console displays the ![Alt](https://files.readme.io/60ba5d8-Ch_Working_with_vulnerabilities00001.jpg)™ icon and a link to a Metasploit module that provides detailed exploit information and resources.

There are three levels of exploit skill: _Novice_, _Intermediate_, and _Expert_. These map to Metasploit's seven-level exploit ranking. For more information, see the Metasploit Framework page [https://github.com/rapid7/metasploit-framework/wiki](https://github.com/rapid7/metasploit-framework/wiki).

* _Novice_ maps to _Great_ through _Excellent_.
* _Intermediate_ maps to _Normal_ through _Good_.
* _Expert_ maps to _Manual_ through _Low_ through _Average_.

You can generate a comma-separated values (CSV) file of the exploit list and related data to share with others in your organization. Click the **Export to CSV** icon ![Alt](https://files.readme.io/9243f42-i_csvexport.jpg). Depending on your browser settings, you will see a pop-up window with options to save the file or open it in a compatible program.

You can also click the **Malware** tab in the pop-up window to view any malware kits that attackers can use to write and deploy malicious code for attacking your environment through the vulnerability.

The _CVSS Score_ column lists the score for each vulnerability. By default, the score shown will be derived from the CVSS Version 3 scale, as long as data exists for it.  If not, a Version 2 score will be shown.  On mouseover, scores will show the vector currently being used to produce the value.  All CVSS Version 3 scores are prefixed with **CVSS:3.0** for ease of recognition.

The score link itself will also open the **CVSS Details** window on mouse-click.  This window contains additional information about each metric being applied to the vector currently in use.  Should data exist for CVSS Version 3, you will have multiple version tabs to choose from.

The _Published On_ column lists the date when information about each vulnerability became available.

The _Risk_ column lists the risk score that the application calculates, indicating the potential danger that each vulnerability poses to an attacker exploits it. The application provides two risk scoring models, which you can configure. See _Selecting a model for calculating risk scores_ in the _administrator's guide_. The risk model you select controls the scores that appear in the _Risk_ column. To learn more about risk scores and how they are calculated, see the [PCI, CVSS, and risk scoring FAQs](doc:pci-cvss-risk-scoring-frequently-asked-questions), which you can access in the _[Support](doc:support-technical-support-and-customer-care)_ page.

The application assigns each vulnerability a severity level, which is listed in the _Severity_ column. The three severity levels—Critical, Severe, and Moderate—reflect how much risk a given vulnerability poses to your network security. The application uses CVSS scores to rate severity. See the [PCI, CVSS, and risk scoring FAQs](doc:pci-cvss-risk-scoring-frequently-asked-questions), which you can access in the _[Support](doc:support-technical-support-and-customer-care)_ page.
[block:callout]
{
  "type": "warning",
  "body": "The severity ranking in the _Severity_ column is not related to the severity score in PCI reports."
}
[/block]
1 to 3 = Moderate

4 to 7 = Severe

8 to 10 = Critical

The _Instances_ column lists the total number of instances of that vulnerability in your site. If you click the link for the vulnerability name, you can view which specific assets are affected by the vulnerability. See [Viewing vulnerability details](doc:working-with-vulnerabilities#section-viewing-vulnerability-details).

You can click the icon in the _Exclude_ column for any listed vulnerability to exclude that vulnerability from a report.

An administrative change to your network, such as new credentials, may change the level of access that an asset permits during its next scan. If the application previously discovered certain vulnerabilities because an asset permitted greater access, that vulnerability data will no longer be available due to diminished access. This may result in a lower number of reported vulnerabilities, even if no remediation has occurred. Using baseline comparison reports to list differences between scans may yield incorrect results or provide more information than necessary because of these changes. Make sure that your assets permit the highest level of access required for the scans you are running to prevent these problems.

The _Solution_ column links to the recommended solution to remediate the vulnerability. The pill icon represents the status of the solution. In most cases, one best solution will have been identified, and clicking the pill icon will take you directly to the recommended solution. Occasionally, there may be more than one possible best solution, depending on your environment. In this case, the icon will change appearance and clicking it will take you to a list of the potential solutions. Below are the potential states of the solutions:

[block:parameters]
{
  "data": {
    "h-0": "Icon",
    "h-1": "Meaning",
    "0-1": "The application was able to identify a single best solution for this vulnerability on this asset.",
    "1-1": "The application identified multiple potential best solutions. A human judgment call is needed to identify the best solution for your environment.",
    "2-1": "Error state. This should appear rarely, but can occur in certain situations, such as if the vulnerability was deprecated, or the console has been decommissioned and is not taking updates.",
    "0-0": "![Alt](https://files.readme.io/a9d0445-i_solution-pill.png)",
    "1-0": "![Alt](https://files.readme.io/088e51d-i_solution-pill-alert.png)",
    "2-0": "![Alt](https://files.readme.io/f35f1c9-i_solution-pill-x.png)"
  },
  "cols": 2,
  "rows": 3
}
[/block]
The _Vulnerability Categories_ and _Vulnerability Check Types_ tables list all categories and check types that the Application _can_ scan for. Your scan template configuration settings determine which categories or check types the application _will_ scan for. To determine if your environment has a vulnerability belonging to one of the listed checks or types, click the appropriate link. The Security Console displays a page listing all pertinent vulnerabilities. Click the link for any vulnerability to see its detail page, which lists any affected assets.

##Filtering your view of vulnerabilities

Your scans may discover hundreds, or even thousands, of vulnerabilities, depending on the size of your scan environment. A high number of vulnerabilities displayed in the _Vulnerability Listing_ table may make it difficult to assess and prioritize security issues. By filtering your view of vulnerabilities, you can reduce the sheer number of those displayed, and restrict the view to vulnerabilities that affect certain assets. For example, a Security Manager may only want to see vulnerabilities that affect assets in sites or asset groups that he or she manages. Or you can restrict the view to vulnerabilities that pose a greater threat to your organization, such as those with higher risk scores or CVSS rankings.
[block:callout]
{
  "type": "info",
  "body": "The _CVSSv3 score_ filter works with the same operators described above.  All operators **except _is not_** will limit results to vulnerabilities with Version 3 data."
}
[/block]
###Working with filters and operators in vulnerability displays

Filtering your view of vulnerabilities involves selecting one or more filters, which are criteria for displaying specific vulnerabilities. For each filter you then select an operator, which controls how the filter is applied.

_Site name_ is a filter for vulnerabilities that affect assets in specific sites. It works with the following operators:

* The _is_ operator displays a drop-down list of site names. Click a name to display vulnerabilities that affect assets in that site. Using the **SHIFT** key, you can select multiple names.
* The _is not_ operator displays a drop-down list of site names. Click a name to filter out vulnerabilities that affect assets in that site, so that they are not displayed. Using the **SHIFT** key, you can select multiple names.

_Asset group name_ is a filter for vulnerabilities that affect assets in specific asset groups. It works with the following operators:

* The _is_ operator displays a drop-down list of asset group names. Click a name to display vulnerabilities that affect assets in that asset group. Using the **SHIFT** key, you can select multiple names.
* The _is not_ operator displays a drop-down list of asset group names. Click a name to filter out vulnerabilities that affect assets in that asset group, so that they are not displayed. Using the **SHIFT** key, you can select multiple names.

_CVE ID_ is a filter for vulnerabilities based on the CVE ID. The CVE identifiers (IDs) are unique, common identifiers for publicly known information security vulnerabilities. For more information, see [https://cve.mitre.org/cve/identifiers/index.html](https://cve.mitre.org/cve/identifiers/index.html). The filter applies a search string to the CVE IDs, so that the search returns vulnerabilities that meet the specified criteria. It works with the following operators:

* _is_ returns all vulnerabilities whose names match the search string exactly.
* _is not_ returns all vulnerabilities whose names do not match the search string.
* _contains_ returns all vulnerabilities whose names contain the search string anywhere in the name.
* _does not contain_ returns all vulnerabilities whose names do not contain the search string.

After you select an operator, you type a search string for the CVE ID in the blank field.

_CVSS score_ is a filter for vulnerabilities with specific CVSS rankings. It works with the following operators:

* The _is_ operator displays all vulnerabilities that have a specified CVSS score.
* The _is not_ operator displays all vulnerabilities that do not have a specified CVSS score.
* The _is in the range of_ operator displays all vulnerabilities that fall within the range of two specified CVSS scores and include the high and low scores in the range.
* The _is higher than_ operator displays all vulnerabilities that have a CVSS score higher than a specified score.
* The _is lower than_ operator displays all vulnerabilities that have a CVSS score lower than a specified score.

After you select an operator, enter a score in the blank field. If you select the range operator, you would enter a low score and a high score to create the range. Acceptable values include any numeral from 0.0 to 10. You can only enter one digit to the right of the decimal. If you enter more than one digit, the score is automatically rounded up. For example, if you enter a score of 2.25, the score is automatically rounded up to 2.3.

_Risk score_ is a filter for vulnerabilities with certain risk scores. It works with the following operators:

* The _is_ operator displays all vulnerabilities that have a specified risk score.
* The _is not_ operator displays all vulnerabilities that do not have a specified risk score.
* The _is in the range of_ operator displays all vulnerabilities that fall within the range of two specified risk scores and include the high and low scores in the range.
* The _is higher than_ operator displays all vulnerabilities that have a risk score higher than a specified score.
* The _is lower than_ operator displays all vulnerabilities that have a risk score lower than a specified score.

After you select an operator, enter a score in the blank field. If you select the range operator, you would type a low score and a high score to create the range. Keep in mind your currently selected risk strategy when searching for assets based on risk scores. For example, if the currently selected strategy is Real Risk, you will not find assets with scores higher than 1,000. [Learn about different risk score strategies](doc:working-with-risk-strategies-to-analyze-threats#section-comparing-risk-strategies). Refer to the risk scores in your vulnerability and asset tables for guidance.

_Vulnerability category_ is a filter that lets you search for vulnerabilities based on the categories that have been flagged on them during scans. Lists of vulnerability categories can be found in the scan template configuration or the report configuration.

The filter applies a search string to vulnerability categories, so that the search returns a list of vulnerabilities that either are or are not in categories that match that search string. It works with the following operators:

* _contains_ returns all vulnerabilities whose category contains the search string. You can use an asterisk (*) as a wildcard character.
* _does not contain_ returns all vulnerabilities that do not have a vulnerability whose category contains the search string. You can use an asterisk (*) as a wildcard character.
* _is_ returns all vulnerabilities whose category matches the search string exactly.
* _is not_ returns all vulnerabilities that do not have a vulnerability whose category matches the exact search string.
* _starts with_ returns all vulnerabilities whose categories begin with the same characters as the search string.
* _ends with_ returns all vulnerabilities whose categories end with the same characters as the search string.

After you select an operator, you type a search string for the vulnerability category in the blank field.

_Vulnerability title_ is a filter that lets you search vulnerabilities based on their titles.The filter applies a search string to vulnerability titles, so that the search returns a list of assets that either have or do not have the specified string in their titles. It works with the following operators:

* _contains_ returns all vulnerabilities whose name contains the search string. You can use an asterisk (*) as a wildcard character.
* _does not contain_ returns all vulnerabilities whose name does not contain the search string. You can use an asterisk (*) as a wildcard character.
* _is_ returns all vulnerabilities whose name matches the search string exactly.
* _is not_ returns all vulnerabilties whose names do not match the exact search string.
* _starts with_ returns all vulnerabilities whose names begin with the same characters as the search string.
* _ends with_ returns all vulnerabilities whose names end with the same characters as the search string.

After you select an operator, you type a search string for the vulnerability name in the blank field.
[block:callout]
{
  "type": "info",
  "body": "You can only use each filter once. For example, you cannot select the _Site name_ filter twice. If you want to specify more than one site name or asset name in the display criteria, use the **SHIFT** key to select multiple names when configuring the filter."
}
[/block]
##Applying vulnerability display filters

To apply vulnerability display filters, take the following steps:

1. Click the **Vulnerabilities** tab of the Security Console Web interface.
The Security Console displays the _Vulnerabilities_ page.
2. In the _Vulnerability Listing_ table, expand the section to **Apply Filters**.
3. Select a filter from the drop-down list.
4. Select an operator for the filter.
5. Enter or select a value based on the operator.
6. Use the + button to add filters. Repeat the steps for selecting the filter, operator, and value. Use the - button to remove filters.
7. Click **Filter**.
The Security Console displays vulnerabilities that meet _all_ filter criteria in the table.

Currently, filters do not change the number of displayed instances for each vulnerability.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/9c97fcf-s_nx_vulnlisting_filter.jpg",
        "s_nx_vulnlisting_filter.jpg",
        1440,
        585,
        "#f3f5f5"
      ],
      "caption": "Filtering the display of vulnerabilities"
    }
  ]
}
[/block]
**Tip:** You can export the filtered view of vulnerabilities as a comma-separated values (CSV) file to share with members of your security team. To do so, click the **Export to CSV** link at the bottom of the _Vulnerability Listing_ table.

##Viewing vulnerability details

Click the link for any vulnerability listed on the _Vulnerabilities_ page to view information about it. The Security Console displays a page for that vulnerability.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/766546d-s_vuln_details.jpg",
        "s_vuln_details.jpg",
        1503,
        2383,
        "#f6f8f8"
      ],
      "caption": "The page for a specific vulnerability"
    }
  ]
}
[/block]
At the top of the page is a header containing details about the vulnerability. These include a description of the vulnerability, its severity level and CVSS version ratings, the date that information about the vulnerability was made publicly available, CVSS and risk scores, vulnerability categories, Common Vulnerabilities and Exposures (CVEs), if available, and the most recent date that Rapid7 modified information about the vulnerability, such as its remediation steps, CVSS and risk scores, vulnerability categories, and Common Vulnerabilities and Exposures (CVEs), if available.

Below these items is a table listing each affected asset, port, and the site on which a scan reported the vulnerability. You can click on the link for the device name or address to view all of its vulnerabilities. . You also can click the site link to view information about the site.

The _Port_ column in the _Affected Assets_ table lists the port that the application used to contact the affected service or software during the scan. The _Status_ column lists a _Vulnerable_ status for an asset if the application confirmed the vulnerability. It lists a _Vulnerable Version_ status if the application only detected that the asset is running a version of a particular program that is known to have the vulnerability.

The _Proof_ column lists the method that the application used to detect the vulnerability on each asset. It uses exploitation methods typically associated with hackers, inspecting registry keys, banners, software version numbers, and other indicators of susceptibility.

The _Exploits_ table lists descriptions of available exploits and their online sources. The Exploit Database is an archive of exploits and vulnerable software. If a Metasploit exploit is available, the console displays the ![Alt](https://files.readme.io/60ba5d8-Ch_Working_with_vulnerabilities00001.jpg)™ icon and a link to a Metasploit module that provides detailed exploit information and resources.

The _Malware_ table lists any malware kit that attackers can use to write and deploy malicious code for attacking your environment through the vulnerability. This table is not displayed if there is no known malware for the vulnerability.

The _References_ table, which appears below the _Affects_ pane, lists links to Web sites that provide comprehensive information about the vulnerability.

At the very bottom of the page is the _Remediations_ pane, which lists remediation steps and links for downloading patches and fixes. This pane includes two tabs:

* Vulnerability rollup solutions: All the solutions with the highest supersedence for this particular vulnerability (that is, the most recent and broad of the available solutions).
* Vulnerability solutions: The full list of available solutions for the vulnerability with no determination as to which has the highest supersedence.

When you view the vulnerabilities page for an asset, there will be additional tabs that categorize the vulnerabilities by relevance to that asset.

If you wish to query the database for a specific vulnerability, and you know its name, type all or part of the name in the **Search** box that appears on every page of the console interface, and click the magnifying glass icon. The console displays a page of search results organized by different categories, including vulnerabilities.

##Working with validated vulnerabilities

There are many ways to sort and prioritize vulnerabilities for remediation. One way is to give higher priority to vulnerabilities that have been validated, or proven definitively to exist. The application uses a number of methods to flag vulnerabilities during scans, such as fingerprinting software versions known to be vulnerable. These methods provide varying degrees of certainty that a vulnerability exists. You can increase your certainty that a vulnerability exists by exploiting it, which involves deploying code that penetrates your network or gains access to a computer through that specific vulnerability.

As discussed in the topic [Viewing active vulnerabilities](doc:working-with-vulnerabilities#section-viewing-active-vulnerabilities), any vulnerability that has a published exploit associated with it is marked with a Metasploit or Exploit Database icon. You can integrate Rapid7 Metasploit as a tool for validating vulnerabilities discovered in scans and then have InsightVM indicate that these vulnerabilities have been validated on specific assets.
[block:callout]
{
  "type": "info",
  "body": "Metasploit is the only exploit application that the vulnerability validation feature supports. See a [tutorial](https://metasploit.help.rapid7.com/docs/validating-a-vulnerability) for performing vulnerability validation with Metasploit."
}
[/block]
To work in InsightVM with vulnerabilities that have been validated with Metasploit, take the following steps:

1. After performing exploits in Metasploit, click the **Assets** tab of the InsightVMSecurity Console Web interface.
2. Locate an asset that you would like to see validated vulnerabilities for. See [Locating and working with assets](doc:locating-assets) .
3. Double-click the asset's name or IP address.
The Security Console displays the details page for the asset.

View the _Exploits_ column ![Alt](https://files.readme.io/926cfb3-i_nx_exploits.jpg) in the _Vulnerabilities_ table.

4. If a vulnerability has been validated with an exploit via a Metasploit module, the column displays the ![Alt](https://files.readme.io/5ef1d16-i_nx_metasploit_validated.jpg) icon.
5. To sort the vulnerabilities according to whether they have been validated, click the title row in the _Exploits_ column.
As seen in the following screen shot, the descending sort order for this column is 1) vulnerabilities that _have_ been validated with a Metasploit exploit, 2) vulnerabilities that _can be_ validated with a Metasploit exploit, 3) vulnerabilities that _have been_ validated with an Exploit database exploit, 4) vulnerabilities that _can be_ validated with an Exploit database exploit.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/b48d299-s_nx_asset_details_exposures.jpg",
        "s_nx_asset_details_exposures.jpg",
        1497,
        923,
        "#f4f6f6"
      ],
      "caption": "The asset details page with the Exposures legend highlighted"
    }
  ]
}
[/block]