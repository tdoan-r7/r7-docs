---
title: "Working with scan templates and tuning scan performance"
excerpt: ""
---
You may want to improve scan performance. You may want to make scans faster or more accurate. Or you may want scans to use fewer network resources. The following section provides best practices for scan tuning and instructions for working with scan templates.

Tuning scans is a sensitive process. If you change one setting to attain a certain performance boost, you may find another aspect of performance diminished. Before you tweak any scan templates, it is important for you to know two things:

* What are your goals or priorities for tuning scans?
* What aspects of scan performance are you willing to compromise on?

Identify your goals and how they’re related to the performance “triangle.” See [Keep the “triangle” in mind when you tune](doc:working-with-scan-templates-and-tuning-scan-performance#section-keep-the-triangle-in-mind-when-you-tune). Doing so will help you look at scan template configuration in the more meaningful context of your environment. Make sure to familiarize yourself with scan template elements before changing any settings.

Also, keep in mind that tuning scan performance requires some experimentation, finesse, and familiarity with how the application works. Most importantly, you need to understand your unique network environment.

This introductory section talks about why you would tune scan performance and how different built-in scan templates address different scanning needs:

* [Defining your goals for tuning](doc:working-with-scan-templates-and-tuning-scan-performance#section-defining-your-goals-for-tuning)
* [The primary tuning tool: the scan template](doc:working-with-scan-templates-and-tuning-scan-performance#section-the-primary-tuning-tool-the-scan-template)

See also the appendix that compares all of our built-in scan templates and their use cases:

* [Scan templates](doc:scan-templates)

Familiarizing yourself with built-in templates is helpful for customizing your own templates. You can create a custom template that incorporates many of the desirable settings of a built-in template and just customize a few settings vs. creating a new template from scratch.

To create a custom scan template, go to the following section:

* [Configuring custom scan templates](doc:configuring-custom-scan-templates)

If you need to export your scan templates in preparation for migrating your installation to a new host, go to the following section:

* [Exporting your scan templates](doc:working-with-scan-templates-and-tuning-scan-performance#section-exporting-your-scan-templates)

##Defining your goals for tuning

Before you tune scan performance, make sure you know why you’re doing it. What do you want to change? What do you need it to do better? Do you need scans to run more quickly? Do you need scans to be more accurate? Do you want to reduce resource overhead?

The following sections address these questions in detail.

##You need to finish scanning more quickly

Your goal may be to increase overall scan speed, as in the following scenarios:

* Actual scan-time windows are widening and conflicting with your scan blackout periods. Your organization may schedule scans for non-business hours, but scans may still be in progress when employees in your organization need to use workstations, servers, or other network resources.
* A particular type of scan, such as for a site with 300 Windows workstations, is taking an especially long time with no end in sight. This could be a “scan hang” issue rather than simply a slow scan.
[block:callout]
{
  "type": "info",
  "body": "If a scan is taking an extraordinarily long time to finish, terminate the scan and contact Technical Support."
}
[/block]
* You need to be able to schedule more scans within the same time window.
* Policy or compliance rules have become more stringent for your organization, requiring you to perform “deeper” authenticated scans, but you don't have additional time to do this.
* You have to scan more assets in the same amount of time.
* You have to scan the same number of assets in less time.
* You have to scan _more_ assets in _less_ time.

##You need to reduce consumption of network or system resources

Your goal may be to lower the hit on resources, as in the following scenarios:
* Your scans are taking up too much bandwidth and interfering with network performance for other important business processes.
* The computers that host your Scan Engines are maxing out their memory if they scan a certain number of ports.
* The security console runs out of memory if you perform too many simultaneous scans.

##You need more accurate scan data

Scans may not be giving you enough information, as in the following scenarios:
* Scans are missing assets.
* Scans are missing services.
* The application is reporting too many false positives or false negatives.
* Vulnerability checks are not occurring at a sufficient depth.

##Keep the “triangle” in mind when you tune

Any tuning adjustment that you make to scan settings will affect one or more main performance categories.
These categories reflect the general goals for tuning discussed in the preceding section:
* accuracy
* resources
* time

These three performance categories are interdependent. It is helpful to visualize them as a triangle.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/e1c0cda-d_nx_prf_tri.jpg",
        "d_nx_prf_tri.jpg",
        234,
        229,
        "#cad3e3"
      ]
    }
  ]
}
[/block]
If you lengthen one side of the triangle—that is, if you favor one performance category—you will shorten at least one of the other two sides. It is unrealistic to expect a tuning adjustment to lengthen all three sides of the triangle. However, you often can lengthen two of the three sides.

##Increasing time availability

Providing more time to run scans typically means making scans run faster. One use case is that of a company that holds auctions in various locations around the world. Its asset inventory is slightly over 1,000. This company cannot run scans while auctions are in progress because time-sensitive data must traverse the network at these times without interruptions. The fact that the company holds auctions in various time zones complicates scan scheduling. Scan windows are extremely tight. The company's best solution is to use a lot of bandwidth so that scan can finish as quickly as possible.

In this case it’s possible to reduce scan time without sacrificing accuracy. However, a high workload may tap resources to the point that the scanning mechanisms could become unstable. In this case, it may be necessary to reduce the level of accuracy by, for example, turning off credentialed scanning.

There are many various ways to increase scan speeds, including the following:

* Increase the number of assets that are scanned simultaneously. Be aware that this will tax RAM on Scan Engines and the Security Console.
* Allocate more scan threads. Doing so will impact network bandwidth.
* Use a less exhaustive scan template. Again, this will diminish the accuracy of the scan.
* Add Scan Engines, or position them in the network strategically. If you have one hour to scan 200 assets over low bandwidth, placing a Scan Engine on the same side of the firewall as those assets can speed up the process. When deploying a Scan Engine relative to target assets, choose a location that maximizes bandwidth and minimizes latency. For more information on Scan Engine placement, refer to the administrator’s guide.
[block:callout]
{
  "type": "warning",
  "body": "Deploying additional Scan Engines may lower bandwidth availability."
}
[/block]
##Increasing accuracy

Making scans more accurate means finding more security-related information.

There are many ways to this, each with its own “cost” according to the performance triangle:

Increase the number of discovered assets, services, or vulnerability checks. This will take more time.

“Deepen” scans with checks for policy compliance and hotfixes. These types of checks require credentials and can take considerably more time.

Scan assets more frequently. For example, peripheral network assets, such as Web servers or Virtual Private Network (VPN) concentrators, are more susceptible to attack because they are exposed to the Internet. It’s advisable to scan them often. Doing so will either require more bandwidth or more time. The time issue especially applies to Web sites, which can have deep file structures.

Be aware of license limits when scanning network services. When the application attempts to connect to a service, it appears to that service as another “client,” or user. The service may have a defined limit for how many simultaneous client connections it can support. If service has reached that client capacity when the application attempts a connection, the service will reject the attempt. This is often the case with telnet-based services. If the application cannot connect to a service to scan it, that service won’t be included in the scan data, which means lower scan accuracy.

##Increasing resource availability

Making more resources available primarily means reducing how much bandwidth a scan consumes. It can also involve lowering RAM use, especially on 32-bit operating systems.

Consider bandwidth availability in four major areas of your environment. Any one of or more of these can become bottlenecks:

* The computer that hosts the application can get bogged down processing responses from target assets.
* The network infrastructure that the application runs on, including firewalls and routers, can get bogged down with traffic.
* The network on which target assets run, including firewalls and routers, can get bogged down with traffic.
* The target assets can get bogged down processing requests from the application.

Of particular concern is the network on which target assets run, simply because some portion of total bandwidth is always in use for business purposes. This is especially true if you schedule scans to run during business hours, when workstations are running and laptops are plugged into the network. Bandwidth sharing also can be an issue during off hours, when backup processes are in progress.

Two related bandwidth metrics to keep an eye on are the number of data packets exchanged during the scan, and the correlating firewall states. If the application sends too many packets per second (pps), especially during the service discovery and vulnerability check phases of a scan, it can exceed a firewall’s capacity to track connection states. The danger here is that the firewall will start dropping request packets, or the response packets from target assets, resulting in false negatives. So, taxing bandwidth can trigger a drop in accuracy.

There is no formula to determine how much bandwidth should be used. You have to know how much bandwidth your enterprise uses on average, as well as the maximum amount of bandwidth it can handle. You also have to monitor how much bandwidth the application consumes and then adjust the level accordingly.

For example, if your network can handle a maximum of 10,000 pps without service disruptions, and your normal business processes average about 3,000 pps at any given time, your goal is to have the application work within a window of 7,000 pps.

The primary scan template settings for controlling bandwidth are scan threads and maximum simultaneous ports scanned.

The cost of conserving bandwidth typically is time.

For example, a company operates full-service truck stops in one region of the United States. Its security team scans multiple remote locations from a central office. Bandwidth is considerably low due to the types of network connections. Because the number of assets in each location is lower than 25, adding remote Scan Engines is not a very efficient solution. A viable solution in this situation is to reduce the number of scan threads to between two and five, which is well below the default value of 10.

There are various other ways to increase resource availability, including the following:

* Reduce the number of target assets, services, or vulnerability checks. The cost is accuracy.
* Reduce the number of assets that are scanned simultaneously. The cost is time.
* Perform less exhaustive scans. Doing so primarily reduces scan times, but it also frees up threads.

##The primary tuning tool: the scan template

Scan templates contain a variety of parameters for defining how assets are scanned. Most tuning procedures involve editing scan template settings.

The built-in scan templates are designed for different use cases, such as PCI compliance, Microsoft Hotfix patch verification, Supervisory Control And Data Acquisition (SCADA) equipment audits, and Web site scans. You can find detailed information about scan templates in the section titled [Scan templates](doc:scan-templates). This section includes use cases and settings for each scan template.

##Templates are best practices
[block:callout]
{
  "type": "info",
  "body": "Until you are familiar with technical concepts related to scanning, such as port discovery and packet delays, it is recommended that you use built-in templates."
}
[/block]
You can use built-in templates without altering them, or create custom templates based on built-in templates. You also can create new custom templates. If you opt for customization, keep in mind that built-in scan templates are themselves best practices. Not only do built-in templates address specific use cases, but they also reflect the delicate balance of factors in the performance triangle: time, resources, and accuracy.

You will notice that if you select the option to create a new template, many basic configuration settings have built-in values. It is recommended that you do not change these values unless you have a thorough working knowledge of what they are for. Use particular caution when changing any of these built-in values.

If you customize a template based on a built-in template, you may not need to change every single scan setting. You may, for example, only need to change a thread number or a range of ports and leave all other settings untouched.

For these reasons, it’s a good idea to perform any customizations based on built-in templates. Start by familiarizing yourself with built-in scan templates and understanding what they have in common and how they differ. The following section is a comparison of four sample templates.

##Understanding configurable phases of scanning

Understanding the phases of scanning is helpful in understanding how scan templates are structured.

Each scan occurs in three phases:
* asset discovery
* service discovery
* vulnerability checks
[block:callout]
{
  "type": "info",
  "body": "The discovery phase in scanning is a different concept than that of asset discovery, which is a method for finding potential scan targets in your environment."
}
[/block]
During the _asset discovery_ phase, a Scan Engine sends out simple packets at high speed to target IP addresses in order to verify that network assets are live. You can configure timing intervals for these communication attempts, as well as other parameters, on the _Asset Discovery_ and _Discovery Performance_ pages of the _Scan Template Configuration_ panel.

Upon locating the asset, the Scan Engine begins the service discovery phase, attempting to connect to various ports and to verify services for establishing valid connections. Because the application scans Web applications, databases, operating systems and network hardware, it has many opportunities for attempting access. You can configure attributes related to this phase on the _Service Discovery_ and _Discovery Performance_ pages of the _Scan Template Configuration_ panel.

During the third phase, known as the _vulnerability check_ phase, the application attempts to confirm vulnerabilities listed in the scan template. You can select which vulnerabilities to scan for in _Vulnerability Checking_ page of the _Scan Template Configuration_ panel.

Other configuration options include limiting the types of services that are scanned, searching for specific vulnerabilities, and adjusting network bandwidth usage.

In every phase of scanning, the application identifies as many details about the asset as possible through a set of methods called fingerprinting. By inspecting properties such as the specific bit settings in reserved areas of a buffer, the timing of a response, or a unique acknowledgment interchange, the application can identify indicators about the asset's hardware, operating system, and, perhaps, applications running under the system. A well-protected asset can mask its existence, its identity, and its components from a network scanner.

##Do you need to alter templates or just alter-nate them?

When you become familiar with the built-in scan templates, you may find that they meet different performance needs at different times.
[block:callout]
{
  "type": "info",
  "body": "Use your variety of report templates to parse your scan results in many useful ways. Scans are a resource investment, especially “deeper” scans. Reports help you to reap the biggest possible returns from that investment."
}
[/block]
You could, for example, schedule a Web audit to run on a weekly basis, or even more frequently, to monitor your Internet-facing assets. This is a faster scan and less of a drain on resources. You could also schedule a Microsoft hotfix scan on a monthly basis for patch verification. This scan requires credentials, so it takes longer. But the trade-off is that it doesn't have to occur as frequently. Finally, you could schedule an exhaustive scan on a quarterly basis do get a detailed, all-encompassing view of your environment. It will take time and bandwidth but, again, it's a less frequent scan that you can plan for in advance.
[block:callout]
{
  "type": "warning",
  "body": "If you change templates regularly, you will sacrifice the conveniences of scheduling scans to run at automatic intervals with the same template."
}
[/block]
Another way to maximize time and resources without compromising on accuracy is to alternate target assets. For example, instead of scanning all your workstations on a nightly basis, scan a third of them and then scan the other two thirds over the next 48 hours. Or, you could alternate target ports in a similar fashion.

##Quick tuning: What can you turn off?

Sometimes, tuning scan performance is a simple matter of turning off one or two settings in a template. The fewer things you check for, the less time or bandwidth you'll need to complete a scan. However, your scan will be less comprehensive, and so, less accurate.
[block:callout]
{
  "type": "warning",
  "body": "Credentialed checks are critical for accuracy, as they make it possible to perform “deep” system scans. Be absolutely certain that you don't need credentialed checks before you turn them off."
}
[/block]
If the scope of your scan does not include Web assets, disable Web-related vulnerability checks. If you don't have to verify hotfix patches, disable any hotfix checks. Turn off credentialed checks if you are not interested in running them. If you do run credentialed checks, make sure you are only running necessary ones.

An important note here is that you need to know exactly what's running on your network in order to know what to turn off. This is where discovery scans become so valuable. They provide you with a reliable, dynamic asset inventory. For example, if you learn, from a discovery scan, that you have no servers running Lotus Notes/Domino, you can exclude those policy checks from the scan.

## Exporting your scan templates
[block:callout]
{
  "type": "danger",
  "title": "IMPORTANT",
  "body": "Complete this step **before** migrating your installation to a new host."
}
[/block]
To export scan templates from the Security Console UI, copy the contents of the following directory:

```
/opt/rapid7/nexpose/shared/scanTemplates/custom/silo/default
```

Save the copied contents on your target machine so that it will be available for placement after your migration is complete.