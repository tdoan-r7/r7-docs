---
title: "Define your goals"
excerpt: ""
---
Knowing in advance what security-related goals you want to fulfill will help you design the most
efficient and effective deployment for your organization.

####Know your business case to know your goals
If you have not yet defined your goals for your deployment, or if you are having difficulty doing so,
start by looking at your business model and your technical environment to identify your security
needs.

Consider factors such as network topology, technical resources (hardware and bandwidth),
human resources (security team members and other stake holders), time, and budget.

####How big is your enterprise?
How many networks, subnetworks, and assets does your enterprise encompass?

The size of your enterprise is a major factor in determining how many Scan Engines you deploy.

####What is the geography of your enterprise?
In how many physical locations is your network deployed? Where are these locations? Are they
thousands or tens of thousands of miles away from each other, or across town from each other,
or right next to each other? Where are firewalls and DMZs located?

These factors will affect how and where you deploy Scan Engines and how you configure your
sites.

####How is your network segmented?
What is the range of IP addresses and subnets within your enterprise?

Network segmentation is a factor in Scan Engine deployment and site planning.

####How do you want to view an asset in multiple sites?
Assets are scanned in logical groupings called sites. For more information about attaching assets
to sites, see the topic [Best practices for adding assets](doc:best-practices-for-adding-assets).
Depending on your needs, you may want to scan the same asset in multiple sites. For example,
an asset may belong to one site because of it's geographical location and another because it is
part of a PCI audit.

If you plan to have assets in multiple sites, consider whether you want to _link_ instances of each
asset in different sites so that it is regarded as the same entity throughout your deployment, or treat each instance as a unique entity. For more information about these options, see [Linking assets across sites](doc:linking-assets-across-sites).

####What is your asset inventory?
What kinds of assets are you using? What are their functions? What operating systems,
applications, and services are running on them? Which assets are physical hardware, and which
are virtual? Where are these different assets located relative to firewalls and DMZs? What are
your hidden network components that support other assets, such as VPN servers, LDAP
servers, routers, switches, proxy servers, and firewalls? Does your asset inventory change
infrequently? Or will today's spreadsheet listing all of your assets be out of date in a month?

#####Asset inventory influences site planning and scan template selection.
Does your asset inventory include laptops that employees take home? Laptops open up a whole
new set of security issues that render firewalls useless. With laptops, your organization is
essentially accepting external devices within your security perimeter. Network administrators
sometimes unwittingly create back doors into the network by enabling users to connect laptops or
home systems to a virtual private network (VPN).

Additionally, laptop users working remotely can innocently create vulnerabilities in many different
ways, such as by surfing the Web without company-imposed controls or plugging in personal
USB storage devices.

An asset inventory that includes laptops may require you to create a special site that you scan
during business hours, when laptops are connected to your local network. Also consider using
the Adpative Security feature to scan laptops as they come online.

####One possible environment: “Example, Inc.”
As you answer the preceding questions, you may find it helpful to create a table. The following
table lists network and asset information for a company called “Example, Inc.”
[block:parameters]
{
  "data": {
    "h-0": "Network segment",
    "h-1": "Address space",
    "h-2": "Number of assets",
    "h-3": "Location",
    "h-4": "Asset function",
    "0-0": "New York Sales",
    "0-1": "10.1.0.0/22",
    "0-2": "254",
    "0-3": "Building 1: Floors 1-3",
    "0-4": "Work stations",
    "1-0": "New York\nIT/Administration",
    "1-1": "10.1.10.0/23",
    "1-2": "50",
    "1-3": "Building 2: Floor 2",
    "1-4": "Work stations\nServers",
    "2-0": "New York printers",
    "2-1": "10.1.20.0/24",
    "2-2": "56",
    "2-3": "Buildings 1 & 2",
    "2-4": "Printers",
    "3-0": "New York DMZ",
    "3-1": "172.16.0.0/22",
    "3-2": "30",
    "3-3": "Co-location facility",
    "3-4": "Web server\nMail server",
    "4-0": "Madrid sales",
    "4-1": "10.2.0.0/22",
    "4-2": "65",
    "4-3": "Building 3: Floor 1",
    "4-4": "Work stations",
    "5-0": "Madrid development",
    "5-1": "10.2.10.0/23",
    "5-2": "130",
    "5-3": "Building 3: Floors 2 & 3",
    "5-4": "Work stations\nServers",
    "6-0": "Madrid printers",
    "6-1": "10.2.20.0/24",
    "6-2": "35",
    "6-3": "Building 3: Floors 1-3",
    "6-4": "Printers",
    "7-0": "Madrid DMZ",
    "7-1": "172.16.10.0/24",
    "7-2": "15",
    "7-3": "Building 3: dark room",
    "7-4": "File server"
  },
  "cols": 5,
  "rows": 8
}
[/block]
####What are the “hot spots” in your enterprise?
What assets contain sensitive data? What assets are on the perimeter of your network? Do you
have Web, e-mail, or proxy servers running outside of firewalls?

Areas of specific concern may warrant Scan Engine placement. Also, you may use certain scan
templates for certain types of high-risk assets. For example, a Web Audit scan template is most
appropriate for Web servers.

####What are your resources?
How much local-area network (LAN) and wide-area network (WAN) bandwidth do you have?
What is your security budget? How much time do you have to run scans, and when can you run
these scans without disrupting business activity?

These considerations will affect which scan templates you use, how you tune your scans, and
when you schedule scans to run. See the Discover section in the user’s guide for information on
setting up sites and scans.

####What exactly are the security risks to your organization?
How easy is it for attackers to penetrate your network remotely? Are there multiple logon
challenges in place to slow them down? How difficult is it for attackers to exploit vulnerabilities in
your enterprise? What are the risks to data confidentiality? To data integrity? To data availability?
The triad of confidentiality, integrity, and availability (CIA) is a good metric by which to quantify
and categorize risks in your organization.

Confidentiality is the prevention of data disclosure to unauthorized individuals or systems. What
happens if an attacker steals customer credit card data? What if a trojan provides hacker access
to your company’s confidential product specifications, business plans, and other intellectual
property?

Integrity is the assurance that data is authentic and complete. It is the prevention of unauthorized
data modification. What happens when a virus wipes out records in your payroll database?
Availability refers to data or services being accessible when needed. How will a denial-of-service
hack of your Web server affect your ability to market your products or services? What happens if
a network attack takes down your phones? Will it cripple your sales team?

If your organization has not attempted to quantify or categorize risks, you can use reports to
provide some guidelines. The algorithm that produces a risk score for each scanned asset
calculates the score based on CIA factors.

Other risks have direct business or legal implications. What dangers does an attack pose to your
organization’s reputation? Will a breach drive away customers? Is there a possibility of getting
sued or fined?

Knowing how your enterprise is at risk can help you set priorities for deploying Scan Engines,
creating sites, and scheduling scans.

The application provides powerful tools for helping you to analyze and track risk so you prioritize
remediation and monitor security trends in your environment over time. See the topics Working
with risk strategies to analyze threats and Working with risk trends in reports in the user’s guide.

####What are your compliance requirements?
Many organizations have a specific reason for acquiring InsightVM: they have to comply with a
specific set of security requirements imposed by the government or by a private-sector entity that
regulates their industry.

Health care providers must protect the confidentiality of patient data as required by the Health
Insurance Portability and Accountability Act (HIPAA).

Many companies, especially those in the financial sector, are subject to security criteria specified
in the Sarbanes-Oxley Act (SOX).

U.S. government organizations and vendors who transact business with the government must
comply with Federal Desktop Core Configuration (FDCC) policies for their Microsoft Windows
systems.

Merchants, who perform credit and debit card transactions, must ensure that their networks
comply with Payment Card Industry (PCI) security standards.

The application provides a number of compliance tools, such as built-in scan templates that help
you verify compliance with these standards. For a list of scan templates and their specifications,
see [Where to find SCAP update information and OVAL files](doc:scap-compliance#section-where-to-find-scap-update-information-and-oval-files).

For official PCI scans the application provides additional tools, including PCI-sanctioned reports,
Web interface features for PCI-specific site configuration and vulnerability exception
management, and expanded application program interface (API) functionality for managing
report distribution. For more information, see the _ASV Guide_, which you can request from
Technical Support.

####Verifying compliance with configuration standards
The application provides several tools to assess configuration against various established
standards:
* a built-in United States Government Configuration Baseline (USGCB) scan template that
includes Policy Manger checks for compliance with USGCB configuration policies (see [Scan templates](doc:scan-templates).)
* a built-in Federal Desktop Core Configuration (FDCC) scan template that includes Policy
Manger checks for compliance with FDCC configuration policies (see [Scan templates](doc:scan-templates).)
* a built-in Center for Internet Security (CIS) scan template that includes Policy Manger checks
for compliance with CIS configuration benchmarks (see [Scan templates](doc:scan-templates).)
* Web interface tools for tracking and overriding policy test results.
* XML and CSV reports for disseminating policy test result data. (See [Creating a basic report](doc:creating-a-basic-report).)
* Web interface tools for viewing SCAP data and working with OVAL files (see [Where to find SCAP update information and OVAL files](doc:scap-compliance#section-where-to-find-scap-update-information-and-oval-files).)

These tools require a license that enables the Policy Manager and policy scanning for the specific
desired standards.

#####What are your goals beyond compliance?
Compliance goals may help you to define your deployment strategy, but it’s important to think
beyond compliance alone to ensure security. For example, protecting a core set of network
assets, such as credit card data servers in the case of PCI compliance, is important; but it may not
be enough to keep your network secure—not even secure enough to pass a PCI audit.

Attackers will use any convenient point of entry to compromise networks. An attacker may exploit
an Internet Explorer vulnerability that makes it possible to install a malicious program on an
employee's computer when that employee browses the Web. The malware may be a remote
execution program with which the hacker can access more sensitive network assets, including
those defined as being critical for compliance.

Compliance, in and of itself, is not synonymous with security. On the other hand, a well
implemented, comprehensive security plan will include among its benefits a greater likelihood of
compliance.

####Who is your security team?
Are you a one-person company or IT department? Are you the head of a team of 20 people, each
with specific security-related tasks? Who in your organization needs to see asset/security data,
and at what level of technical detail? Who’s in charge of remediating vulnerabilities? What are the
security considerations that affect who will see what information? For example, is it necessary to
prevent a security analyst in your Chicago branch from seeing data that pertains to your
Singapore branch?

These considerations will dictate how you set up asset groups, define roles and permissions,
assign remediation tickets, and distribute reports. See [Managing users and authentication](doc:managing-users-and-authentication).