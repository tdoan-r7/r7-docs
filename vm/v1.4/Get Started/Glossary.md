---
title: "Glossary"
excerpt: ""
---
###API (application programming interface)

An API is a function that a developer can integrate with another software application by using program calls. The term _API_ also refers to one of two sets of XML APIs, each with its own included operations: API v1.1 and Extended API v1.2. To learn about each API, see the API documentation, which you can download from [Support: Technical Support and Customer Care](doc:support-technical-support-and-customer-care).

###Appliance

An Appliance is a set of InsightVM components shipped as a dedicated hardware/software unit. Appliance configurations include a Security Console/Scan Engine combination and an Scan Engine-only version.

###Asset

An asset is a single device on a network that the application discovers during a scan. In the Web interface and API, an asset may also be referred to as a _device_. See [Managed asset](doc:glossary#section-managed-asset) and [Unmanaged asset](doc:glossary#section-unmanaged-asset). An asset’s data has been integrated into the scan database, so it can be listed in sites and asset groups. In this regard, it differs from a _node_. See [Node](doc:glossary#section-node).

###Asset group

An asset group is a logical collection of managed assets to which specific members have access for creating or viewing reports or tracking remediation tickets. An asset group may contain assets that belong to multiple sites or other asset groups. An asset group is either static or dynamic. An asset group is not a site. See [Site](doc:glossary#section-site), [Dynamic asset group](doc:glossary#section-dynamic-asset-group), and [Static asset group](doc:glossary#section-static-asset-group).

###Asset Owner

Asset Owner is one of the preset roles. A user with this role can view data about discovered assets, run manual scans, and create and run reports in accessible sites and asset groups.

###Asset Report Format (ARF)

The Asset Report Format is an XML-based report template that provides asset information based on connection type, host name, and IP address. This template is required for submitting reports of policy scan results to the U.S. government for SCAP certification.

###Asset search filter

An asset search filter is a set of criteria with which a user can refine a search for assets to include in a dynamic asset group. An asset search filter is different from a [Dynamic Discovery filter](doc:glossary#section-dynamic-discovery-filter).

###Authentication

Authentication is the process of a security application verifying the logon credentials of a client or user that is attempting to gain access. By default the application authenticates users with an internal process, but you can configure it to authenticate users with an external LDAP or Kerberos source.

###Average risk

Average risk is a setting in risk trend report configuration. It is based on a calculation of your risk scores on assets over a report date range. For example, average risk gives you an overview of how vulnerable your assets might be to exploits whether it’s high or low or unchanged. Some assets have higher risk scores than others. Calculating the average score provides a high-level view of how vulnerable your assets might be to exploits.

###Benchmark

In the context of scanning for FDCC policy compliance, a benchmark is a combination of policies that share the same source data. Each policy in the Policy Manager contains some or all of the rules that are contained within its respective benchmark. See [Federal Desktop Core Configuration (FDCC)](doc:glossary#section-federal-desktop-core-configuration-fdcc-) and [United States Government Configuration Baseline (USGCB)](doc:glossary#section-united-states-government-configuration-baseline-usgcb-).

###Breadth

Breadth refers to the total number of assets within the scope of a scan.

###Category

In the context of scanning for FDCC policy compliance, a category is a grouping of policies in the Policy Manager configuration for a scan template. A policy’s category is based on its source, purpose, and other criteria. See [Policy Manager](doc:glossary#section-policy-manager), [Federal Desktop Core Configuration (FDCC)](doc:glossary#section-federal-desktop-core-configuration-fdcc-), and [United States Government Configuration Baseline (USGCB)](doc:glossary#section-united-states-government-configuration-baseline-usgcb-).

###Check type

A check type is a specific kind of check to be run during a scan. Examples: The Unsafe check type includes aggressive vulnerability testing methods that could result in Denial of Service on target assets; the Policy check type is used for verifying compliance with policies. The check type setting is used in scan template configurations to refine the scope of a scan.

###Center for Internet Security (CIS)

Center for Internet Security (CIS) is a not-for-profit organization that improves global security posture by providing a valued and trusted environment for bridging the public and private sectors. CIS serves a leadership role in the shaping of key security policies and decisions at the national and international levels. The Policy Manager provides checks for compliance with CIS benchmarks including technical control rules and values for hardening network devices, operating systems, and middleware and software applications. Performing these checks requires a license that enables the Policy Manager feature and CIS scanning. See [Policy Manager](doc:glossary#section-policy-manager).

###Command console

The command console is a page in the Security Console Web interface for entering commands to run certain operations. When you use this tool, you can see real-time diagnostics and a behind-the-scenes view of Security Console activity. To access the command console page, click the **Run Security Console commands** link next to the _Troubleshooting_ item on the _Administration_ page.

###Common Configuration Enumeration (CCE)

Common Configuration Enumeration (CCE) is a standard for assigning unique identifiers known as CCEs to configuration controls to allow consistent identification of these controls in different environments. CCE is implemented as part of its compliance with SCAP criteria for an Unauthenticated Scanner product.

###Common Platform Enumeration (CPE)

Common Platform Enumeration (CPE) is a method for identifying operating systems and software applications. Its naming scheme is based on the generic syntax for Uniform Resource Identifiers (URI). CCE is implemented as part of its compliance with SCAP criteria for an Unauthenticated Scanner product.

###Common Vulnerabilities and Exposures (CVE)

The Common Vulnerabilities and Exposures (CVE) standard prescribes how the application should identify vulnerabilities, making it easier for security products to exchange vulnerability data. CVE is implemented as part of its compliance with SCAP criteria for an Unauthenticated Scanner product.

###Common Vulnerability Scoring System (CVSS)

Common Vulnerability Scoring System (CVSS) is an open framework for calculating vulnerability risk scores. CVSS is implemented as part of its compliance with SCAP criteria for an Unauthenticated Scanner product.

###Compliance

Compliance is the condition of meeting standards specified by a government or respected industry entity. The application tests assets for compliance with a number of different security standards, such as those mandated by the Payment Card Industry (PCI) and those defined by the National Institute of Standards and Technology (NIST) for Federal Desktop Core Configuration (FDCC).

###Continuous scan

A continuous scan starts over from the beginning if it completes its coverage of site assets within its scheduled window. This is a site configuration setting.

###Coverage

Coverage indicates the scope of vulnerability checks. A coverage improvement listed on the News page for a release indicates that vulnerability checks have been added or existing checks have been improved for accuracy or other criteria.

###Criticality

Criticality is a value that you can apply to an asset with a RealContext tag to indicate its importance to your business. Criticality levels range from _Very Low_ to _Very High_. You can use applied criticality levels to alter asset risk scores. See _Criticality-adjusted risk_ below.

###Criticality-adjusted risk

or

###Context-driven risk

Criticality-adjusted risk is a process for assigning numbers to criticality levels and using those numbers to multiply risk scores.

###Custom tag

With a custom tag you can identify assets by according to any criteria that might be meaningful to your business.

###Depth

Depth indicates how thorough or comprehensive a scan will be. Depth refers to level to which the application will probe an individual asset for system information and vulnerabilities.

###Discovery (scan phase)

Discovery is the first phase of a scan, in which the application finds potential scan targets on a network. Discovery as a scan phase is different from [Dynamic Discovery](doc:glossary#section-dynamic-discovery).

###Document report template

Document templates are designed for human-readable reports that contain asset and vulnerability information. Some of the formats available for this template type—Text, PDF, RTF, and HTML—are convenient for sharing information to be read by stakeholders in your organization, such as executives or security team members tasked with performing remediation.

###Dynamic asset group

A dynamic asset group contains scanned assets that meet a specific set of search criteria. You define these criteria with asset search filters, such as IP address range or operating systems. The list of assets in a dynamic group is subject to change with every scan or when vulnerability exceptions are created. In this regard, a dynamic asset group differs from a static asset group. See [Asset group](doc:glossary#section-asset-group) and [Static asset group](doc:glossary#section-static-asset-group).

###Dynamic Discovery

Dynamic Discovery is a process by which the application automatically discovers assets through a connection with a server that manages these assets. You can refine or limit asset discovery with criteria filters. Dynamic discovery is different from [Discovery (scan phase)](doc:glossary#section-discovery-scan-phase-).

###Dynamic Discovery filter

A Dynamic Discovery filter is a set of criteria refining or limiting Dynamic Discovery results. This type of filter is different from an [Asset search filter](doc:glossary#section-asset-search-filter).

###Dynamic Scan Pool

The Dynamic Scan Pool feature allows you to use Scan Engine pools to enhance the consistency of your scan coverage. A Scan Engine pool is a group of shared Scan Engines that can be bound to a site so that the load is distributed evenly across the shared Scan Engines. You can configure scan pools using the Extended API v1.2.

###Dynamic site

A dynamic site is a collection of assets that are targeted for scanning and that have been discovered through vAsset discovery. Asset membership in a dynamic site is subject to change if the discovery connection changes or if filter criteria for asset discovery change. See [Static site](doc:glossary#section-static-site), [Site](doc:glossary#section-site), and [Dynamic Discovery](doc:glossary#section-dynamic-discovery).

###Exploit

An exploit is an attempt to penetrate a network or gain access to a computer through a security flaw, or vulnerability. Malicious exploits can result in system disruptions or theft of data. Penetration testers use benign exploits only to verify that vulnerabilities exist. The Metasploit product is a tool for performing benign exploits. See [Metasploit](doc:glossary#section-metasploit) and [Published exploit](doc:glossary#section-published-exploit).

###Export report template

Export templates are designed for integrating scan information into external systems. The formats available for this type include various XML formats, Database Export, and CSV.

###Exposure

An exposure is a vulnerability, especially one that makes an asset susceptible to attack via malware or a known exploit.

###Extensible Configuration Checklist Description Format (XCCDF)

As defined by the National Institute of Standards and Technology (NIST), Extensible Configuration Checklist Description Format (XCCDF) “is a specification language for writing security checklists, benchmarks, and related documents. An XCCDF document represents a structured collection of security configuration rules for some set of target systems. The specification is designed to support information interchange, document generation, organizational and situational tailoring, automated compliance testing, and compliance scoring.” Policy Manager checks for FDCC policy compliance are written in this format.

###False positive

A false positive is an instance in which the application flags a vulnerability that doesn’t exist. A false negative is an instance in which the application fails to flag a vulnerability that does exist.

###Federal Desktop Core Configuration (FDCC)

The Federal Desktop Core Configuration (FDCC) is a grouping of configuration security settings recommended by the National Institute of Standards and Technology (NIST) for computers that are connected directly to the network of a United States government agency. The Policy Manager provides checks for compliance with these policies in scan templates. Performing these checks requires a license that enables the Policy Manager feature and FDCC scanning.

###Fingerprinting

Fingerprinting is a method of identifying the operating system of a scan target or detecting a specific version of an application.

###Global Administrator

Global Administrator is one of the preset roles. A user with this role can perform all operations that are available in the application and they have access to all sites and asset groups.

###Host

A host is a physical or virtual server that provides computing resources to a guest virtual machine. In a high-availability virtual environment, a host may also be referred to as a node. The term node has a different context in the application. See [Node](doc:glossary#section-node).

###Latency

Latency is the delay interval between the time when a computer sends data over a network and another computer receives it. Low latency means short delays.

###Locations tag

With a _Locations_ tag you can identify assets by their physical or geographic locations.

###Malware

Malware is software designed to disrupt or deny a target systems’s operation, steal or compromise data, gain unauthorized access to resources, or perform other similar types of abuse. The application can determine if a vulnerability renders an asset susceptible to malware attacks.

###Malware kit

Also known as an exploit kit, a malware kit is a software bundle that makes it easy for malicious parties to write and deploy code for attacking target systems through vulnerabilities.

###Managed asset

A managed asset is a network device that has been discovered during a scan and added to a site’s target list, either automatically or manually. Only managed assets can be checked for vulnerabilities and tracked over time. Once an asset becomes a managed asset, it counts against the maximum number of assets that can be scanned, according to your license.

###Manual scan

A manual scan is one that you start at any time, even if it is scheduled to run automatically at other times. Synonyms include _ad-hoc scan_ and _unscheduled scan_.

###Metasploit

Metasploit is a product that performs benign exploits to verify vulnerabilities. See [Exploit](doc:glossary#section-exploit).

###MITRE

The MITRE Corporation is a body that defines standards for enumerating security-related concepts and languages for security development initiatives. Examples of MITRE-defined enumerations include Common Configuration Enumeration (CCE) and Common Vulnerability Enumeration (CVE). Examples of MITRE-defined languages include Open Vulnerability and Assessment Language (OVAL). A number of MITRE standards are implemented, especially in verification of FDCC compliance.

###National Institute of Standards and Technology (NIST)

National Institute of Standards and Technology (NIST) is a non-regulatory federal agency within the U.S. Department of Commerce. The agency mandates and manages a number of security initiatives, including Security Content Automation Protocol (SCAP). See [Security Content Automation Protocol (SCAP)](doc:glossary#section-security-content-automation-protocol-scap-).

###Node

A node is a device on a network that the application discovers during a scan. After the application integrates its data into the scan database, the device is regarded as an asset that can be listed in sites and asset groups. See [Asset](doc:glossary#section-asset).

###Open Vulnerability and Assessment Language (OVAL)

Open Vulnerability and Assessment Language (OVAL) is a development standard for gathering and sharing security-related data, such as FDCC policy checks. In compliance with an FDCC requirement, each OVAL file that the application imports during configuration policy checks is available for download from the _SCAP_ page in the Security Console Web interface.

###Override

An override is a change made by a user to the result of a check for compliance with a configuration policy rule. For example, a user may override a Fail result with a Pass result.

###Payment Card Industry (PCI)

The Payment Card Industry (PCI) is a council that manages and enforces the PCI Data Security Standard for all merchants who perform credit card transactions. The application includes a scan template and report templates that are used by Approved Scanning Vendors (ASVs) in official merchant audits for PCI compliance.

###Permission

A permission is the ability to perform one or more specific operations. Some permissions only apply to sites or asset groups to which an assigned user has access. Others are not subject to this kind of access.

###Policy

A policy is a set of primarily security-related configuration guidelines for a computer, operating system, software application, or database. Two general types of polices are identified in the application for scanning purposes: Policy Manager policies and standard policies. The application's Policy Manager (a license-enabled feature) scans assets to verify compliance with policies encompassed in the United States Government Configuration Baseline (USGCB), the Federal Desktop Core Configuration (FDCC), Center for Internet Security (CIS), and Defense Information Systems Agency (DISA) standards and benchmarks, as well as user-configured custom policies based on these policies. See [Policy Manager](doc:glossary#section-policy-manager), [Federal Desktop Core Configuration (FDCC)](doc:glossary#section-federal-desktop-core-configuration-fdcc-), [United States Government Configuration Baseline (USGCB)](doc:glossary#section-united-states-government-configuration-baseline-usgcb-). The application also scans assets to verify compliance with standard policies. See [Scan](doc:glossary#section-scan) and [Standard policy](doc:glossary#section-standard-policy).

###Policy Manager

Policy Manager is a license-enabled scanning feature that performs checks for compliance with Federal Desktop Core Configuration (FDCC), United States Government Configuration Baseline (USGCB), and other configuration policies. Policy Manager results appear on the _Policies_ page, which you can access by clicking the **Policies** icon in the Web interface. They also appear in the _Policy Listing_ table for any asset that was scanned with Policy Manager checks. Policy Manager policies are different from standard policies, which can be scanned with a basic license. See [Policy](doc:glossary#section-policy) and [Standard policy](doc:glossary#section-standard-policy).

###Policy Result

In the context of FDCC policy scanning, a result is a state of compliance or non-compliance with a rule or policy. Possible results include _Pass_, _Fail_, or _Not Applicable_.

###Policy Rule

A rule is one of a set of specific guidelines that make up an FDCC configuration policy. See [Federal Desktop Core Configuration (FDCC)](doc:glossary#section-federal-desktop-core-configuration-fdcc-), [United States Government Configuration Baseline (USGCB)](doc:glossary#section-united-states-government-configuration-baseline-usgcb-), and [Policy](doc:glossary#section-policy).

###Potential vulnerability

A potential vulnerability is one of three positive vulnerability check result types. The application reports a potential vulnerability during a scan under two conditions: First, potential vulnerability checks are enabled in the template for the scan. Second, the application determines that a target is running a vulnerable software version but it is unable to verify that a patch or other type of remediation has been applied. For example, an asset is running version 1.1.1 of a database. The vendor publishes a security advisory indicating that version 1.1.1 is vulnerable. Although a patch is installed on the asset, the version remains 1.1.1. In this case, if the application is running checks for potential vulnerabilities, it can only flag the host asset as being potentially vulnerable. The code for a potential vulnerability in XML and CSV reports is vp (vulnerable, potential). For other positive result types, see [Vulnerability check](doc:glossary#section-vulnerability-check).

###Published exploit

In the context of the application, a published exploit is one that has been developed in Metasploit or listed in the Exploit Database. See [Exploit](doc:glossary#section-exploit).

###RealContext

RealContext is a feature that enables you to tag assets according to how they affect your business. You can use tags to specify the criticality, location, or ownership. You can also use custom tags to identify assets according any criteria that is meaningful to your organization.

###Real Risk strategy

Real Risk is one of the built-in strategies for assessing and analyzing risk. It is also the recommended strategy because it applies unique exploit and malware exposure metrics for each vulnerability to Common Vulnerability Scoring System (CVSS) base metrics for likelihood (access vector, access complexity, and authentication requirements) and impact to affected assets (confidentiality, integrity, and availability). See [Risk strategy](doc:glossary#section-real-risk-strategy).

###Report template

Each report is based on a template, whether it is one of the templates that is included with the product or a customized template created for your organization. See [Document report template](doc:glossary#section-document-report-template) and [Export report template](doc:glossary#section-export-report-template).

###Risk

In the context of vulnerability assessment, risk reflects the likelihood that a network or computer environment will be compromised, and it characterizes the anticipated consequences of the compromise, including theft or corruption of data and disruption to service. Implicitly, risk also reflects the potential damage to a compromised entity’s financial well-being and reputation.

###Risk score

A risk score is a rating that the application calculates for every asset and vulnerability. The score indicates the potential danger posed to network and business security in the event of a malicious exploit. You can configure the application to rate risk according to one of several built-in risk strategies, or you can create custom risk strategies.

###Risk strategy

A risk strategy is a method for calculating vulnerability risk scores. Each strategy emphasizes certain risk factors and perspectives. Four built-in strategies are available: [Real Risk strategy](doc:glossary#section-real-risk-strategy), [TemporalPlus risk strategy](doc:glossary#section-temporalplus-risk-strategy), [Temporal risk strategy](doc:glossary#section-temporal-risk-strategy), and [Weighted risk strategy](doc:glossary#section-weighted-risk-strategy). You can also create custom risk strategies.

###Risk trend

A risk trend graph illustrates a long-term view of your assets’ probability and potential impact of compromise that may change over time. Risk trends can be based on average or total risk scores. The highest-risk graphs in your report demonstrate the biggest contributors to your risk on the site, group, or asset level. Tracking risk trends helps you assess threats to your organization’s standings in these areas and determine if your vulnerability management efforts are satisfactorily maintaining risk at acceptable levels or reducing risk over time. See [Average risk](doc:glossary#section-average-risk) and [Total risk](doc:glossary#section-total-risk).

###Role

A role is a set of permissions. Five preset roles are available. You also can create custom roles by manually selecting permissions. See [Asset Owner](doc:glossary#section-asset-owner), [Security Manager](doc:glossary#section-security-manager), [Global Administrator](doc:glossary#section-global-administrator), [Site Owner](doc:glossary#section-site-owner), and [User](doc:glossary#section-user).

###Scan

A scan is a process by which the application discovers network assets and checks them for vulnerabilities. See [Exploit](doc:glossary#section-exploit) and [Vulnerability check](doc:glossary#section-vulnerability-check).

###Scan credentials

Scan credentials are the user name and password that the application submits to target assets for authentication to gain access and perform deep checks. Many different authentication mechanisms are supported for a wide variety of platforms. See [Shared scan credentials](doc:glossary#section-shared-scan-credentials) and [Site-specific scan credentials](doc:glossary#section-site-specific-scan-credentials).

###Scan Engine

The Scan Engine is one of two major application components. It performs asset discovery and vulnerability detection operations. Scan engines can be _distributed_ within or outside a firewall for varied coverage. Each installation of the Security Console also includes a local engine, which can be used for scans within the console’s network perimeter.

###Scan template

A scan template is a set of parameters for defining how assets are scanned. Various preset scan templates are available for different scanning scenarios. You also can create custom scan templates. Parameters of scan templates include the following:
* methods for discovering assets and services
* types of vulnerability checks, including safe and unsafe
* Web application scanning properties
* verification of compliance with policies and standards for various platforms

###Scheduled scan

A scheduled scan starts automatically at predetermined points in time. The scheduling of a scan is an optional setting in site configuration. It is also possible to start any scan manually at any time.

###Security Console

The Security Console is one of two major application components. It controls Scan Engines and retrieves scan data from them. It also controls all operations and provides a Web-based user interface.

###Security Content Automation Protocol (SCAP)

Security Content Automation Protocol (SCAP) is a collection of standards for expressing and manipulating security data. It is mandated by the U.S. government and maintained by the National Institute of Standards and Technology (NIST). The application complies with SCAP criteria for an Unauthenticated Scanner product.

###Security Manager

Security Manager is one of the preset roles. A user with this role can configure and run scans, create reports, and view asset data in accessible sites and asset groups.

###Shared scan credentials

One of two types of credentials that can be used for authenticating scans, shared scan credentials are created by Global Administrators or users with the Manage Site permission. Shared credentials can be applied to multiple assets in any number of sites. See [Site-specific scan credentials](doc:glossary#section-site-specific-scan-credentials).

###Site

A site is a collection of assets that are targeted for a scan. Each site is associated with a list of target assets, a scan template, one or more Scan Engines, and other scan-related settings. See [Dynamic site](doc:glossary#section-dynamic-site) and [Static site](doc:glossary#section-static-site). A site is not an asset group. See [Asset group](doc:glossary#section-asset-group).

###Site-specific scan credentials

One of two types of credentials that can be used for authenticating scans, a set of single-instance credentials is created for an individual site configuration and can only be used in that site. See [Scan credentials](doc:glossary#section-scan-credentials) and [Shared scan credentials](doc:glossary#section-shared-scan-credentials).

###Site Owner

Site Owner is one of the preset roles. A user with this role can configure and run scans, create reports, and view asset data in accessible sites.

###Standard policy

A standard policy is one of several that the application can scan with a basic license, unlike with a Policy Manager policy. Standard policy scanning is available to verify certain configuration settings on Oracle, Lotus Domino, AS/400, Unix, and Windows systems. Standard policies are displayed in scan templates when you include policies in the scope of a scan. Standard policy scan results appear in the _Advanced Policy Listing_ table for any asset that was scanned for compliance with these policies. See [Policy](doc:glossary#section-policy).

###Static asset group

A static asset group contains assets that meet a set of criteria that you define according to your organization's needs. Unlike with a dynamic asset group, the list of assets in a static group does not change unless you alter it manually. See [Dynamic asset group](doc:glossary#section-dynamic-asset-group).

###Static site

A static site is a collection of assets that are targeted for scanning and that have been manually selected. Asset membership in a static site does not change unless a user changes the asset list in the site configuration. For more information, see [Dynamic site](doc:glossary#section-dynamic-site) and [Site](doc:glossary#section-site).

###Temporal risk strategy

One of the built-in risk strategies, Temporal indicates how time continuously increases likelihood of compromise. The calculation applies the age of each vulnerability, based on its date of public disclosure, as a multiplier of CVSS base metrics for likelihood (access vector, access complexity, and authentication requirements) and asset impact (confidentiality, integrity, and availability). Temporal risk scores will be lower than TemporalPlus scores because Temporal limits the risk contribution of partial impact vectors. See [Risk strategy](doc:glossary#section-risk-strategy).

###TemporalPlus risk strategy

One of the built-in risk strategies, TemporalPlus provides a more granular analysis of vulnerability impact, while indicating how time continuously increases likelihood of compromise. It applies a vulnerability's age as a multiplier of CVSS base metrics for likelihood (access vector, access complexity, and authentication requirements) and asset impact (confidentiality, integrity, and availability). TemporalPlus risk scores will be higher than Temporal scores because TemporalPlus expands the risk contribution of partial impact vectors. See [Risk strategy](doc:glossary#section-risk-strategy).

###Total risk

Total risk is a setting in risk trend report configuration. It is an aggregated score of vulnerabilities on assets over a specified period.

###United States Government Configuration Baseline (USGCB)

The United States Government Configuration Baseline (USGCB) is an initiative to create security configuration baselines for information technology products deployed across U.S. government agencies. USGCB evolved from FDCC, which it replaces as the configuration security mandate in the U.S. government. The Policy Manager provides checks for Microsoft Windows 7, Windows 7 Firewall, and Internet Explorer for compliance with USGCB baselines. Performing these checks requires a license that enables the Policy Manager feature and USGCB scanning. See [Policy Manager](doc:glossary#section-policy-manager) and [Federal Desktop Core Configuration (FDCC)](doc:glossary#section-federal-desktop-core-configuration-fdcc-).

###Unmanaged asset

An unmanaged asset is a device that has been discovered during a scan but not correlated against a managed asset or added to a site’s target list. The application is designed to provide sufficient information about unmanaged assets so that you can decide whether to manage them. An unmanaged asset does not count against the maximum number of assets that can be scanned according to your license.

###Unsafe check

An unsafe check is a test for a vulnerability that can cause a denial of service on a target system. Be aware that the check itself can cause a denial of service, as well. It is recommended that you only perform unsafe checks on test systems that are not in production.

###Update

An update is a released set of changes to the application. By default, two types of updates are automatically downloaded and applied:

_Content_ updates include new checks for vulnerabilities, patch verification, and security policy compliance. Content updates always occur automatically when they are available.

_Product_ updates include performance improvements, bug fixes, and new product features. Unlike content updates, it is possible to disable automatic product updates and update the product manually.

###User

User is one of the preset roles. An individual with this role can view asset data and run reports in accessible sites and asset groups.

###Validated vulnerability

A validated vulnerability is a vulnerability that has had its existence proven by an integrated Metasploit exploit. See [Exploit](doc:glossary#section-exploit).

###Vulnerable version

Vulnerable version is one of three positive vulnerability check result types. The application reports a vulnerable version during a scan if it determines that a target is running a vulnerable software version and it can verify that a patch or other type of remediation has not been applied. The code for a vulnerable version in XML and CSV reports is vv (vulnerable, version check). For other positive result types, see [Vulnerability check](doc:glossary#section-vulnerability-check).

###Vulnerability

A vulnerability is a security flaw in a network or computer.

###Vulnerability category

A vulnerability category is a set of vulnerability checks with shared criteria. For example, the Adobe category includes checks for vulnerabilities that affect Adobe applications. There are also categories for specific Adobe products, such as _Air_, _Flash_, and _Acrobat/Reader_. Vulnerability check categories are used to refine scope in scan templates. Vulnerability check results can also be filtered according category for refining the scope of reports. Categories that are named for manufacturers, such as _Microsoft_, can serve as supersets of categories that are named for their products. For example, if you filter by the _Microsoft_ category, you inherently include all Microsoft product categories, such as _Microsoft Path_ and _Microsoft Windows_. This applies to other “company” categories, such as _Adobe_, _Apple_, and _Mozilla_.

###Vulnerability check

A vulnerability check is a series of operations that are performed to determine whether a security flaw exists on a target asset. Check results are either negative (no vulnerability found) or positive. A positive result is qualified one of three ways: See [Vulnerability found](doc:glossary#section-vulnerability-found), [Vulnerable version](doc:glossary#section-vulnerable-version), and [Potential vulnerability](doc:glossary#section-potential-vulnerability). You can see positive check result types in XML or CSV export reports. Also, in a site configuration, you can set up alerts for when a scan reports different positive results types.

###Vulnerability exception

A vulnerability exception is the removal of a vulnerability from a report and from any asset listing table. Excluded vulnerabilities also are not considered in the computation of risk scores.

###Vulnerability found

Vulnerability found is one of three positive vulnerability check result types. The application reports a vulnerability found during a scan if it verified the flaw with asset-specific vulnerability tests, such as an exploit. The code for a vulnerability found in XML and CSV reports is ve (vulnerable, exploited). For other positive result types, see [Vulnerability check](doc:glossary#section-vulnerability-check).

###Weighted risk strategy

One of the built-in risk strategies, Weighted is based primarily on asset data and vulnerability types, and it takes into account the level of importance, or weight, that you assign to a site when you configure it. See [Risk strategy](doc:glossary#section-risk-strategy).