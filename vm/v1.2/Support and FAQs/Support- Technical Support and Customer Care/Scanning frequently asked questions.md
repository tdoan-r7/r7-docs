---
title: "Scanning frequently asked questions"
excerpt: ""
---
This page concerns running scans and managing scan engines.

####How does InsightVM perform discovery scans?

Discovery scans occur in two sequential phases: device discovery and service discovery.

_Device, or asset discovery_

During this initial phase, InsightVM sends connection requests to target assets to verify that they are alive and available for scanning. InsightVM uses any of three methods to contact these assets:
* ICMP echo requests (also known as "pings")
* TCP packets
* UDP packets

_Service discovery_

InsightVM also uses different methods for performing TCP service discovery. It can send packets with the SYN flag, or SYN+RST, or SYN+FIN, or SYN+ECE. If it receives a SYN response, the port is open. If it receives an RST response, InsightVM considers the port closed.

You can configure which methods InsightVM uses for discovery scan phases. See [Configuring asset discovery](doc:configuring-asset-discovery) and [Configuring service discovery](doc:configuring-service-discovery). To learn more about how to optimize scanning, see [Working with scan templates and tuning scan performance](doc:working-with-scan-templates-and-tuning-scan-performance).

####What are the network and port requirements for InsightVM to function properly?

See [Requirements](doc:requirements) for console-specific port needs.

InsightVM Scan Engines contact target assets using TCP, UDP, and ICMP to perform scans. Scan engines do not initiate outbound communication with the InsightVM Security Console.

Ideally there should be no firewalls or similar devices between a scan engine and its target assets. See _the following topic_.

Scanning may also require some flexibility in security policies. For more information, see the _administrator's guide_. You can download this document from the [Support](doc:support-technical-support-and-customer-care) page.

####What changes do I need to make on my Windows firewall to allow InsightVM to scan accurately?

In a domain-joined environment, you must enable two group policy settings:
* Windows Firewall: Allow remote administration exception
* Windows Firewall: Allow file and print sharing exception

In a standalone environment, you must start Remote Registry to allow InsightVM to fingerprint remote scan targets accurately.
You must also enable two standard profile settings:
* Windows Firewall: Allow inbound file and printer sharing exception
* Windows Firewall: Allow inbound remote remote administration exception

Windows Vista requires additional steps:
* making sure the setting Prohibit use of Internet connection firewall on your DNS domain network has a "Disabled" or "Not configured" state
* turning off User Account Control

For detailed instructions on how to perform these steps, consult appropriate Microsoft documentation.

####When I run the Linux top command, why does it appear that InsightVM using all available memory even after the scan is complete?

The host that is running InsightVM uses all memory allocated to the Java Virtual Machine (JVM) for scanning and for any InsightVM system functions. This is important to keep in mind when using RAM to optimize scan performance. The allocated memory is not released unless InsightVM restarts. The top command is not a reliable way to monitor memory use in InsightVM.

####How do I create a scan template that checks for only one vulnerability?*

When you are creating or modifying a scan template, go the _Vulnerabilities_ page of the configuration wizard, and enable the vulnerability that you want InsightVM to check. When you enable a specific vulnerability check, you are disabling all other checks.

####What does it mean when I see the messages "Paused by System" and "Not enough memory to complete scan" during a scan?*

InsightVM pauses scans and stops report generation when the memory on the Security Console host server is dangerously low. This reduces the possibility of the server failing. However, it may cause the Security Console to stop scans or reporting activities before they are complete. If you are seeing these messages, then your host system is running low on memory.

To lower the likelihood of scans being paused for this reason, try running fewer simultaneous scans or lowering the number of scan threads allocated by your scan template.

If these changes do not help you complete your scans, contact [Rapid7 Technical Support](mailto:support@rapid7.com).

####Why are my scans hanging or causing printers to crash during vulnerability checks on printers?*

Printers are known to have HTTP services that may freeze scans or cause other unwanted results during scans. You can mitigate this problem with two steps:
1. Avoid using the Web spidering feature when performing vulnerability checks: Using device discovery data, find the names of HTTP daemons associated with printers. Enter these names in the field labeled "HTTP daemons to skip while spidering". This field is located on the Web spidering page of any Scan Template configuration wizard.
2. Scan printers separately: Create a site just for printers. Disable Web spidering in the template that you use for this site.

####Why can't I see incremental scan data for a current scan job?

By default, InsightVM only retrieves incremental results from a local scan engine, which runs on the same host as the InsightVM Security Console; and it displays the full set of scan results from a remote engine after the scan has been completed. You can configure InsightVM to retrieve incremental scan results from remote scan engines, including Rapid7 hosted engines. This control is available on the _Scan Engines_ page of the InsightVM Security Console configuration wizard.

####Why are my scan results showing all devices as "Alive" or all devices as "Dead"?

In security-conscious environments, it's not uncommon to have a firewall that provides SYN flood protection to prevent devices like InsightVM from performing accurate port scanning and host discovery. One way to mitigate this problem is to reduce port scanning speed in the scan template to avoid triggering the SYN flood protection. The drawback is that scanning will take much longer. If this works, then scanning will become much slower than expected. A better solution is to configure the firewall to "whitelist" InsightVM. This makes it possible for InsightVM to scan reliably at normal speeds.
[block:callout]
{
  "type": "info",
  "body": "This topic involves features that are only available in the Enterprise version of InsightVM."
}
[/block]