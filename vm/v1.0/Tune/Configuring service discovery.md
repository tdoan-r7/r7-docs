---
title: "Configuring service discovery"
excerpt: ""
---
Once the application verifies that a host is live, or running, it begins to scan ports to collect information about services running on the computer. The target range for service discovery can include TCP and UDP ports.

TCP ports (RFC 793) are the endpoints of logical connections through which networked computers carry on “conversations.”

Well Known ports are those most commonly found to be open on the Internet.

The range of ports may be extended beyond Well Known Port range. Each vulnerability check may add a set of ports to be scanned. Various back doors, trojan horses, viruses, and other worms create ports after they have installed themselves on computers. Rogue programs and hackers use these ports to access the compromised computers. These ports are not predefined, and they may change over time. Output reports will show which ports were scanned during vulnerability testing, including maliciously created ports.

Various types of port scan methods are available as custom options. Most built-in scan templates incorporate the Stealth scan (SYN) method, in which the port scanner process sends TCP packets with the SYN (synchronize) flag. This is the most reliable method. It's also fast. In fact, a SYN port scan is approximately 20 times faster than a scan with the full-connect method, which is one of the other options for the TCP port scan method.

The exhaustive template and penetration tests are exceptions in that they allow the application to determine the optimal scan method. This option makes it possible to scan through firewalls in some cases; however, it is somewhat less reliable.

Although most templates include UDP ports in the scope of a scan, they limit UDP ports to well-known numbers. Services that run on UDP ports include DNS, TFTP, and DHCP. If you want to be absolutely thorough in your scanning, you can include more UDP ports, but doing so will increase scan time.

##Performance considerations for port scanning

Scanning all possible ports takes a lot of time. If the scan occurs through a firewall, and the firewall has been set up to drop packets sent to non-authorized devices, than a full-port scan may span several hours to several days. If you configure the application to scan all ports, it may be necessary to change additional parameters.

Service discovery is the most resource-sensitive phase of scanning. The application sends out hundreds of thousands of packets to scan ports on a mere handful of assets.

The more ports you scan, the longer the scan will take. And scanning the maximum number of ports is not necessarily more accurate. It is a best practice select target ports based on discovery data. If you simply are not sure of which ports to scan, use well known numbers. Be aware, though, that attackers may avoid these ports on purpose or probe additional ports for service attack opportunities.
[block:callout]
{
  "type": "info",
  "body": "The application relies on network devices to return “ICMP port unreachable” packets for closed UDP ports."
}
[/block]
If you want to be a little more thorough, use the target list of TCP ports from more aggressive templates, such as the exhaustive or penetration test template.

If you plan to scan UDP ports, keep in mind that aside from the reliability issues discussed earlier, scanning UDP ports can take a significant amount of time. By default, the application will only send two UDP packets per second to avoid triggering the ICMP rate-limiting mechanisms that are built into TCP/IP stacks for most network devices. Sending more packets could result in packet loss. A full UDP port scan can take up to nine hours, depending on bandwidth and the number of target assets.

To reduce scan time, do not run full UDP port scans unless it is necessary. UDP port scanning generally takes longer than TCP port scanning because UDP is a “connectionless” protocol. In a UDP scan, the application interprets non-response from the asset as an indication that a port is _open_ or _filtered_, which slows the process. When configured to perform UDP scanning, the application matches the packet exchange pace of the target asset. Oracle Solaris only responds to 2 UDP packet failures per second as a rate limiting feature, so this scanning in this environment can be very slow in some cases.

##Configuration steps for service discovery

1. Go to the _Scan Template Configuration—Service Discovery_ page.
[block:callout]
{
  "type": "info",
  "body": "You can achieve the most “stealthy” scan by running a vulnerability test with port scanning disabled. However, if you do so, the application will be unable to discover services, which will hamper fingerprinting and vulnerability discovery."
}
[/block]
2. Select a TCP port scan method from the drop-down list.
3. Select which TCP ports you wish to scan from the drop-down list.
If you want to scan additional TCP ports, enter the numbers or range in the **Additional ports** text box.
[block:callout]
{
  "type": "info",
  "body": "If you want to scan with PowerShell, add port 5985 to the port list if it is not already included. If you have enabled PowerShell but do not want to scan with that capability, make sure that port 5985 is not in the port list. See the topic [Configuring scan credentials](doc:configuring-scan-credentials) for more information."
}
[/block]
4. Select which UDP ports you want to scan from the drop-down list.

If you want to scan additional UDP ports, enter the desired range in the **Additional ports** text box.
[block:callout]
{
  "type": "info",
  "body": "Consult Technical Support to change the default service file setting."
}
[/block]
5. If you want to change the service names file, enter the new file name in the text box.
This properties file lists each port and the service that commonly runs on it. If scans cannot identify actual services on ports, service names will be derived from this file in scan results.
The default file, default-services.properties, is located in the following directory: <installation_directory/plugins/java/1/NetworkScanners/1.
You can replace the file with a custom version that lists your own port/service mappings.
6. Configure any other template settings as desired. When you have finished configuring the scan template, click **Save**.

##Changing discovery performance settings

You can change default scan settings to maximize speed and resource usage during asset and service discovery. If you do not change any of these discovery performance settings, scans will auto-adjust based on network conditions.

Changing packet-related settings can affect the triangle. See [Keep the “triangle” in mind when you tune](doc:working-with-scan-templates-and-tuning-scan-performance#section-keep-the-triangle-in-mind-when-you-tune). Shortening send-delay intervals theoretically increases scan speeds, but it also can lead to network congestion depending on bandwidth. Lengthening send-delay intervals increases accuracy. Also, longer delays may be necessary to avoid blacklisting by firewalls or IDS devices.

##How ports are scanned

In the following explanation of how ports are scanned, the numbers indicated are default settings and can be changed. The application sends a block of 10 packets to a target port, waits 10 milliseconds, sends another 10 packets, and continues this process for each port in the range. At the end of the scan, it sends another round of packets and waits 10 milliseconds for each block of packets that have not received a response. The application repeats these attempts for each port five times.

If the application receives a response within the defined number of retries, it will proceed with the next phase of scanning: service discovery. If it does not receive a response after exhausting all discovery methods defined in the template, it reports the asset as being _DEAD_ in the scan log.

When the target asset is on a local system segment (not behind a firewall), the scan occurs more rapidly because the asset will respond that ports are closed. The difficulty occurs when the device is behind a firewall, which consumes packets so that they do not return to the Scan Engine. In this case the application will wait the maximum time between port scans. TCP port scanning can exceed five hours, especially if it includes full-port scans of 65K ports.

Try to scan the asset on the local segment inside the firewall. Try not to perform full TCP port scans outside a device that will drop the packets like a firewall unless necessary.

You can change the following performance settings:
[block:callout]
{
  "type": "warning",
  "body": "For minimum retries, packet-per-second rate, and simultaneous connection requests, the default value of 0 disables manual settings, in which case, the application auto-adjusts the settings. To enable manual settings, enter a value of 1 or greater."
}
[/block]
###Maximum retries

This is the maximum number of attempts to contact target assets. If the limit is exceeded with no response, the given asset is not scanned. The default number of UDP retries is 5, which is high for a scan through a firewall. If UDP scanning is taking longer than expected, try reducing the retry value to 2 or 3.

You may be able speed up the scanning process by reducing the maximum retry count from the default of 4. Lowering the number of retries for sending packets is a good accuracy adjustment in a network with high-traffic or strict firewall rules. In an environment like this, it’s easier to lose packets. Consider setting the retry value at 3. Note that the scan will take longer.

###Timeout interval

Set the number of milliseconds to wait between retries. You can set an initial timeout interval, which is the first setting that the scan will use. You also can set a range. For maximum timeout interval, any value lower than 5 ms disables manual settings, in which case, the application auto-adjusts the settings. The discovery may auto-adjust interval settings based on varying network conditions.

###Scan delay

This is the number of milliseconds to wait between sending packets to each target host.
[block:callout]
{
  "type": "warning",
  "body": "Reducing these settings may cause scan results to become inaccurate."
}
[/block]
Increasing the delay interval for sending TCP packets will prevent scans from overloading routers, triggering firewalls, or becoming blacklisted by Intrusion Detection Systems (IDS). Increasing the delay interval for sending packets is another measure that increases accuracy at the expense of time.

You can increase the accuracy of port scans by slowing them down with 10- to 25-millisecond delays.

###Packet-per-second rate

This is the number of packets to send each second during discovery attempts. Increasing this rate can increase scan speed. However, more packets are likely to be dropped in congestion-heavy networks, which can skew scan results.
[block:callout]
{
  "type": "info",
  "body": "To enable the defeat rate limit, you must have the Stealth (SYN) scan method selected. See  [Scan templates](doc:scan-templates)."
}
[/block]
An additional control, called **Defeat Rate Limit** (also known as defeat-rst-rate limit), enforces the minimum packet-per-second rate. This may improve scan speed when a target host limits its rate of RST (reset) responses to a port scan. However, enforcing the packet setting under these circumstances may cause the scan to miss ports, which lowers scan accuracy. Disabling the defeat rate limit may cause the minimum packet setting to be ignored when a target host limits its rate of RST (reset) responses to a port scan. This can increase scan accuracy.

###Parallelism (simultaneous connection requests)

This is the number of discovery connection requests to be sent to target hosts simultaneously. More simultaneous requests can mean faster scans, subject to network bandwidth. This setting has no effect if values have been set for scan delay.

###Configuration steps for tuning discovery performance

1. Go to the _Scan Template Configuration—Discovery Performance_ page.
2. For **Maximum retries**, drag the slider to the left or right to adjust the value if desired.
3. For **Timeout interval**, drag the sliders to the left or right to adjust the **Initial**, **Minimum**, and **Maximum** values if desired.
4. For **Scan Delay**, drag the sliders to the left or right to adjust the values if desired.
5. For **Packet-per-second rate**, drag the sliders to the left or right to adjust the **Minimum** and **Maximum** values if desired.
6. Select the **Defeat Rate Limit** checkbox to enforce the minimum packet-per-second rate if desired.
7. For **Parallelism**, drag the sliders to the left or right to adjust the **Minimum** and **Maximum** values if desired.
8. Configure any other template settings as desired. When you have finished configuring the scan template, click **Save**.