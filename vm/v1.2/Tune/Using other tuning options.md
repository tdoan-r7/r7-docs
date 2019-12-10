---
title: "Using other tuning options"
excerpt: ""
---
Beyond customizing scan templates, you can do other things to improve scan performance.

##Change Scan Engine deployment

Depending on bandwidth availability, adding Scan Engines can reduce scan time over all, and it can improve accuracy. Where you put Scan Engines is as important as how many you have. It’s helpful to place Scan Engines on both sides of network dividing points, such as firewalls. See the topic _Distribute Scan Engines strategically_ in the administrator's guide.

##Edit site configuration

Tailor your site configuration to support your performance goals. Try increasing the number of sites and making sites smaller. Try pairing sites with different scan templates. Adjust your scan schedule to avoid bandwidth conflicts.

##Increase resources

Resources fall into two main categories:
* Network bandwidth
* RAM and CPU capacity of hosts

If your organization has the means and ability, enhance network bandwidth. If not, find ways to reduce bandwidth conflicts when running scans.

Increasing the capacity of host computers is a little more straightforward. The _installation guide_ lists minimum system requirements for installation. Your system may meet those requirements, but if you want to bump up maximum number of scan threads, you may find your host system slowing down or becoming unstable. This usually indicates memory problems.

If increasing scan threads is critical to meeting your performance goals, consider installing the 64-bit version of InsightVM. A Scan Engine running on a 64-bit operating system can use as much RAM as the operating system supports, as opposed to a maximum of approximately 4 GB on 32-bit systems. The vertical scalability of 64-bit Scan Engines significantly increases the potential number simultaneous scans that InsightVM can run.

Always keep in mind that best practices for Scan Engine placement. See the topic _Distribute Scan Engines strategically_ in the administrator's guide. Bandwidth is also important to consider.

##Make your environment “scan-friendly”

Any well constructed network will have effective security mechanisms in place, such as firewalls. These devices will regard InsightVM as a hostile entity and attempt to prevent it from communicating with assets that they are designed to attack.

If you can find ways to make it easier for the application to coexist with your security infrastructure—without exposing your network to risk or violating security policies—you can enhance scan speed and accuracy.

For example, when scanning Windows XP workstations, you can take a few simple measures to improve performance:
* Make the application a part of the local domain.
* Give the application the proper domain credentials.
* Configure the XP firewall to allow it to connect to Windows and perform patch-checking
* Edit the domain policy to give the application communication access to the workstations.

##Open firewalls on Windows scan targets

You can open firewalls on Windows assets to allow InsightVM to perform deep scans on those targets within your network.

By default, Microsoft Windows XP SP2, Vista, Server 2003, and Server 2008 enable firewalls to block incoming TCP/IP packets. Maintaining this setting is generally a smart security practice. However, a closed firewall limits the application to discovering network assets during a scan. Opening a firewall gives it access to critical, security-related data as required for patch or compliance checks.

To find out how to open a firewall without disabling it on a Windows platform, see Microsoft’s documentation for that platform. Typically, a Windows domain administrator would perform this procedure.