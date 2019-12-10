---
title: "Site creation scenarios"
excerpt: ""
---
This section discusses "recipes" for sites to suit common needs. By selecting an appropriate template, assets, and configuration options, you can customize your site to suit specific goals.

## Default settings

The default scan template is Full Audit without Web Spider.

This scan template gives you thorough vulnerability checks on the majority of non-Web assets. It runs faster than the scan template with the Web spider.

To check thoroughly for vulnerabilities, you should specify credentials. See [Configuring scan credentials](doc:configuring-scan-credentials) for more information.

As you establish your vulnerability scanning practice, you can create additional sites with various scan templates and change your Scan Engine from the default as needed for your network configuration.

## Find out what you have: Discovery scan

**Summary:** The first step in checking for vulnerabilities is to make sure you are checking all the assets in your organization. You can find basic information about the assets in your organization by conducting a discovery scan. The application includes a built-in scan template for a discovery scan.

If there is an asset you do not know about that can be exploited, attackers can use that to bypass the Virtual Private Network (VPN) and corporate firewall, and launch attacks from within the local network. If you are new to your role, you might not already be aware of every asset you are responsible for securing. In any case, new assets are frequently added. You can conduct discovery scans to find and learn more about those assets, in preparation for developing an ongoing scanning program.

Your discovery scan may vary depending on your organization’s network configuration.We recommend conducting a discovery scan on as wide a range of IP addresses as possible, in case your organization has items outside the typical range. Therefore, for the initial discovery scan, we recommend initially checking the entire private IPv4 address space (10.0.0.0/8, 172.16.0.0/12 and 192.168.0.0/16) as well as all of the public IP addresses owned or controlled by the organization. Doing so will help you find the largest possible number of hosts. We recommend this certainly for organizations who actually make use of all the private address space, but also for organizations with smaller networks, in order to make sure they find everything they can.
[block:callout]
{
  "type": "info",
  "body": "Scanning so many assets could take some time. To estimate how long the scans will take, see the _Planning for capacity requirements_ section of the administrator's guide. In addition, a discovery scan can set off alerts through your system administration or antivirus programs; you may want to advise users before scanning."
}
[/block]
To conduct the initial discovery scan in InsightVM:

1. Create a new static site (see [Adding assets to sites](doc:adding-assets-to-sites)), including the following settings:
   * When specifying the included assets, specify a range in Classless Inter-Domain Routing (CIDR) notation. See [http://en.wikipedia.org/wiki/Classless_Inter-Domain_Routing](http://en.wikipedia.org/wiki/Classless_Inter-Domain_Routing). This notation allows you to specify a large group of machines in a concise syntax. As mentioned above, a best practice at this point is to scan all IP addresses controlled by the organization, as well as each of the private IP address ranges.
   * Select the **Discovery Scan** scan template.
   * Do not specify credentials. They are not needed for determining the presence of the machine on the network.
2. Run a scan on this site.
* Examine the results of the scan in comparison to what you know about your network. Look for and address any anomalies. For example:
   * **Ports incorrectly showing as active**: If the discovery scan shows every single port as active, it is likely that this result is not showing the actual network configuration, but is being affected by something else such as a piece of security equipment (for example, intrusion detection software, intrusion protection software, or a load balancer). Determine what is causing the unexpected result and make changes so that you can get accurate scan information. For example, if a firewall is causing the inaccurate results, whitelist InsightVM on the firewall.
   * **Ports incorrectly showing as inactive**: You may find areas of the network where you were not able to scan. For instance, there may be an address you know about that was not found on the discovery scan. Check whether the omission was due to a firewall or logical routing issue. If so, configure an additional Scan Engine on the other side of the barrier and scan those assets.

## Get an outside view of your environment

**Summary:** In addition to conducting thorough scans of your network, we recommend to use a Scan Engine outside your network to check what can be found. Once you have a Scan Engine ready, you can add it in the _Site Configuration_.

If you have external IP addresses, you can check on what someone could access from outside. You can set up a Scan Engine outside your network perimeter and see what it can find. If you would like to get an "external" view of your firewall, perform a scan from an engine that is external to the organization and treated the same as other external machines. You may want to consider using a Rapid7 hosted engine.

We recommend the following configurations:

   * Do not use credentials for these external scans.
   * Do not whitelist the source IP address.
   * You may need to exempt the engine from certain active/adaptive intrusion prevention technologies (e.g., Web Application Firewall, Unknown Unicast and Muticast Flood Control, intrusion prevention systems, Dynamic Firewall Blacklisting).
   * Use the Full Audit with Web Spider scan template or a similar custom template.
   * Scan the entirety of your organization’s assigned public address space, not just the systems you believe to be alive or accessible.
   * Scan at least monthly, or as frequently as feasible given change control and duration of scans.
   * Always combine external scanning with internal authenticated scanning as described above, because firewall rules screen access to certain vulnerabilities, services, and hosts.

We recommend the following prioritization for remediation:

   * One of the most dangerous types of vulnerabilities is one that could let an unauthenticated external user log on, such as an exposed Telnet port. Make it an urgent priority to remediate such vulnerabilities.
   * Otherwise, begin addressing the results by reducing the attack surface:
      * Take down or block access to hosts that do not need to be public.
      * Use firewall rules to restrict access to as many services and hosts as possible.
      * Address the remaining external-facing vulnerabilities based on CVSSv2 or CVSSv3 score and prevalence.

## Zero-day vulnerabilities

In the case of newly announced, high risk vulnerabilities, you may want to scan for just that specific vulnerability, in order to find out as quickly as possible which of your assets are affected.

You can create a custom scan template that checks just for specific vulnerabilities, and scan your sites with this special template. You can use the Common Vulnerabilities and Exposures Identifier (CVE-ID) to focus only on checks for that vulnerability.

To scan for specific vulnerabilities:

1. Typically, the best practice is to create a new scan template by copying an existing one. The best one to copy will vary depending on the nature of the vulnerability, but Full Audit with Web Spider or Full Audit without Web Spider are usually good starting points. For more information on scan templates, see [Scan templates](doc:scan-templates).
2. Ensure the **Vulnerabilities** option is selected, and that the **Web Spidering** option is selected if relevant. Clear the **Policies** option to focus the template on the checks specific to this vulnerability.
3. Edit the scan template name and description so you will be able to recognize later that the template is customized for this purpose.
4. Go to the _Vulnerability Checks_ page. First, you will disable all checks, check categories, and check types so that you can focus on scanning exclusively for items related to this issue.
5. Expand the _By Category_ section and click **Remove categories**.
6. Select the check box for the top row (_Vulnerability Category_), which will auto-select the check boxes for all categories. Then click Save. Note that 0 categories are now enabled.
7. Expand the _By Individual Check_ section and click **Add checks**.
8. Enter or paste the relevant CVE-ID in the _Search Criteria_ box and click **Search**. Select the check box for the top row (Vulnerability Check), which will auto-select the check boxes for all types. Then click _Save_.
9. Repeat step 7 for any additional CVE-IDs associated with the issue.
10. Save the scan template.
11. Create or edit a site to include:
   * the new custom scan template
   * credentials for the authenticated vulnerability checks
12. Start scanning.

## Assets in multiple locations

If you have assets in multiple locations, there are several factors to take into consideration:

   * You can apply tags to indicate the locations of the assets. See [Applying RealContext with tags](doc:applying-realcontext-with-tags) . You can then create reports based in these tags so you can assess the risk of your assets by location. See [Selecting assets to report on](doc:creating-a-basic-report#section-selecting-assets-to-report-on).
   * It is a good practice to create sites and associate them with scan engines in a way that makes the most of your network configuration. For example, if you have assets in Houston and Singapore, you probably will be better off placing Scan Engines in both locations and creating a site for each, rather than trying to scan all the assets with a scan engine in just one of the locations.

## Large numbers of assets

To scan large numbers of assets, you may want to take advantage of Scan Engine pooling. A Scan Engine pool can help with load balancing and serve as backup if one Scan Engine fails. To learn more about configuring Scan Engine pools, see [Working with Scan Engine pools](doc:working-with-scan-engine-pools).

## Amazon Web Services

To scan Amazon Web Services (AWS) virtual assets, you need to perform some preparation in your AWS environment and create a discovery connection specific to this type of assets. To learn more, see [Preparing for Dynamic Discovery in an AWS environment](doc:discovering-amazon-web-services-instances).

## VMWare

To scan VMWare virtual assets, you will need to perform some preparation steps in the target VMWare environment, and then create a discovery connection specific to this type of assets. To learn more, see [Preparing the target VMware environment for Dynamic Discovery](doc:discovering-virtual-machines-managed-by-vmware-vcenter-or-esxesxi).

## Internal PCI compliance scans

If your systems process, store, or transmit credit card holder data, you may be using InsightVM to comply with the Payment Card Industry (PCI) Security Standards Council Data Security Standards (DSS). The PCI internal audit scan template is designed to help you conduct your internal assessments as required in the DSS.

To learn more about PCI DSS 3.0, visit [our resource page](https://www.rapid7.com/solutions/compliance/pci-dss/).

The following is an outline of a suggested process to use with InsightVM to help with your internal PCI scans. (For more information on how to use any of the features in the application, see the Help or User’s Guide.)

1. As described in PCI DSS 3.0 section 6.1, you need to create a process to identify security vulnerabilities. To do so create one or more sites in InsightVM using the following configurations:
   a. Enter your organization information as required for PCI-specific reports in the _Organization_ section of the _Info & Security_ tab of the _Site Configuration_.
   b. Include the assets you need to scan for PCI compliance. (Generally these hosts will comprise your Cardholder Data environment or “CDE”).
   c. Use the _PCI internal audit_ scan template.
   d. Specify credentials for the scan. (These credentials should have privileges to read the registry, file, and package management aspects of target systems).
2. As indicated in the PCI Data Security Standard requirements 11.2.1 and 11.2.3, you need to create and examine reports to verify that you have scanned for and remediated vulnerabilities. You should also keep copies of these reports to prove your compliance with the PCI DSS.
   a. Create a new report as indicated in [Creating a basic report](doc:creating-a-basic-report). You will most likely want to use the _PCI Executive Summary_ and _PCI Vulnerability Details_ reports. Follow this process for each of those templates. Specify the following settings:
      i. For the **Scope** of the report, specify the assets you are scanning for PCI.
      ii. In the advanced settings, under **Distribution**, specify the e-mail sender address and the recipients of the report.
3. Mitigate the vulnerabilities. The description of a vulnerability contains remediation steps.
4. Re-scan to verify that your mitigations have successfully resolved the findings
   a. If compensating controls are used, it may be necessary to use exception handling to eliminate the associated findings. (It may not be possible for automated tools to detect your compensating control even if it is effective in mitigating associated risk.)
5. Continue to scan and mitigate. You will need to scan internally quarterly until you have remediated all high-risk vulnerabilities, as defined in sections 6.1 and 11.2.1 of the PCI DSS. You will also need to scan after major changes, as defined in section 11.2.3. The acceptable timeframes for applying remediations are outlined in section 6.2.

## Policy benchmarks

The application includes built-in scan templates that can be used for policy benchmarking. These include CIS, DISA, and USGCB. Each of these templates contains a bundle of policies to be used for different platforms; only the ones that apply are evaluated. Of the three, CIS contains support for the widest variety of platforms. For more information on these templates, see [Scan templates](doc:scan-templates).

All policy scan templates require a username and password pair used to gain access to assets such as desktop and server machines. Typically this account will have the privileges of an administrator or root user. For more on credentials, see [Configuring scan credentials](doc:configuring-scan-credentials).

The CIS scan template includes policy checks specific to databases, and requires a username and password for database access.