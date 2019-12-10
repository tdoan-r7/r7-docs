---
title: "Configuring asset discovery"
excerpt: ""
---
Asset discovery configuration involves three options:

* determining if target assets are live
* collecting information about discovered assets
* reporting any assets with unauthorized MAC addresses

If you choose not to configure asset discovery in a custom scan template, the scan will begin with service discovery.

##Determining if target assets are live

Determining whether target assets are live can be useful in environments that contain large numbers of assets, which can be difficult to keep track of. Filtering out dead assets from the scan job helps reduce scan time and resource consumption.

Three methods are available to contact assets:
* ICMP echo requests (also known as “pings”)
* ARP pings (for local network)
* TCP packets
* UDP packets

The potential downside is that firewalls or other protective devices may block discovery connection requests, causing target assets to appear dead even if they are live. If a firewall is on the network, it may block the requests, either because it is configured to block network access for any packets that meet certain criteria, or because it regards any scan as a potential attack. In either case, the application reports the asset to be _DEAD_ in the scan log. This can reduce the overall accuracy of your scans. Be mindful of where you deploy Scan Engines and how Scan Engines interact with firewalls. See [Make your environment “scan-friendly”](doc:using-other-tuning-options#section-make-your-environment-scan-friendly).

Using more than one discovery method promotes more accurate results. If the application cannot verify that an asset is live with one method, it will revert to another.
[block:callout]
{
  "type": "warning",
  "body": "The Web audit and Internet DMZ audit templates do not include any of these discovery methods."
}
[/block]
Peripheral networks usually have very aggressive firewall rules in place, which blunts the effectiveness of asset discovery. So for these types of scans, it’s more efficient to have the application “assume” that a target asset is live and proceed to the next phase of a scan, service discovery. This method costs time, because the application checks ports on all target assets, whether or not they are live. The benefit is accuracy, since it is checking all possible targets.

By default, the Scan Engine uses ARP and ICMP requests, also known as pings, to seek out an asset during device discovery. There are a couple of drawbacks of this approach. A firewall may discard the pings, either because it is configured to block network access for any packets that meet certain criteria, or because it regards any scan as a potential attack. In either case, the application infers that the device is not present, and reports it as _DEAD_ in the scan log. On the other hand, a firewall may be configured to send proxy ARP responses, which could result in non-existent assets appearing to be alive.
[block:callout]
{
  "type": "info",
  "body": "Selecting both TCP and UDP for device discovery causes the application to send out more packets than with one protocol, which uses up more network bandwidth."
}
[/block]
You can select TCP and/or UDP as additional or alternate options for locating live hosts. With these protocols, the application attempts to verify the presence of assets online by opening connections. Firewalls are often configured to allow traffic on port 80, since it is the default HTTP port, which supports Web services. If nothing is registered on port 80, the target asset will send a “port closed” response, or no response, to the Scan Engine. This at least establishes that the asset is online and that port scans can occur. In this case, the application reports the asset to be _ALIVE_ in scan logs.

If you select TCP or UDP for device discovery, make sure to designate ports in addition to 80, depending on the services and operating systems running on the target assets. You can view TCP and UDP port settings on default scan templates, such as Discovery scan and Discovery scan (aggressive) to get an idea of commonly used port numbers.

TCP is more reliable than UDP for obtaining responses from target assets. It is also used by more services than UDP. You may wish to use UDP as a supplemental protocol, as target devices are also more likely to block the more common TCP and ICMP packets.

On the point of using TCP packets for device discovery, you must remember that the Scan Engine considers any response from a device as a proof of its liveness. This may cause non-existent targets to appear in scan results due to an intermediate device (e.g. firewall, router, etc.) sending TCP reset responses to the Scan Engine. If this problem exists in your environment, you can choose the option to not treat TCP reset responses as live assets. The risk of selecting this option is that you may miss devices that have been configured to provide only reset responses.

If a scan target is listed as a host name in the site configuration, the application attempts DNS resolution. If the host name does not resolve, it is considered _UNRESOLVED_, which, for the purposes of scanning, is the equivalent of _DEAD_.

UDP is a less reliable protocol for asset discovery since it doesn’t incorporate TCP’s handshake method for guaranteeing data integrity and ordering. Unlike TCP, if a UDP port doesn’t respond to a communication attempt, it is usually regarded as being open.

##Fine-tuning scans with verification of live assets

Asset discovery can be an efficient accuracy boost. Also, disabling asset discovery can actually bump up scan times. The application only scans an asset if it verifies that the asset is live. Otherwise, it moves on. For example, if it can first verify that 50 hosts are live on a sparse class C network, it can eliminate unnecessary port scans.

It is a good idea to enable ICMP and to configure intervening firewalls to permit the exchange of ICMP echo requests and reply packets between the application and the target network.

Make sure that TCP is also enabled for asset discovery, especially if you have strict firewall rules in your internal networks. Enabling UDP may be excessive, given the dependability issues of UDP ports. To make the judgment call with UDP ports, weigh the value of thoroughness (accuracy) against that of time.

If you do not select any discovery methods, scans assume that all target assets are live, and immediately begin service discovery.

##Ports used for asset discovery

If the application uses TCP or UDP methods for asset discovery, it sends request packets to specific ports. If the application contacts a port and receives a response that the port is open, it reports the host to be “live” and proceeds to scan it.

The PCI audit template includes extra TCP ports for discovery. With PCI scans, it’s critical not to miss any live assets.

##Configuration steps for verifying live assets

1. Go to the _Scan Template Configuration—Asset Discovery_ page.
2. Select one or more of the displayed methods to locate live hosts.
3. If you select TCP or UDP, enter one or more port numbers for each selection. The application will send the TCP or UDP packets to these ports.
4. Configure any other template settings as desired. When you have finished configuring the scan template, click **Save**.

##Collecting information about discovered assets

You can collect certain information about discovered assets and the scanned network before performing vulnerability checks. All of these discovery settings are optional.

##Finding other assets on the network

The application can query DNS and WINS servers to find other network assets that may be scanned.

Microsoft developed Windows Internet Name Service (WINS) for name resolution in the LAN manager environment of NT 3.5. The application can interrogate this broadcast protocol to locate the names of Windows workstations and servers. WINS usually is not required. It was developed originally as a system database application to support conversion of NETBIOS names to IP addresses.

If you enable the option to discover other network assets, the application will discover and interrogate DNS and WINS servers for the IP addresses of all supported assets. It will include those assets in the list of scanned systems.

##Collecting Whois information
[block:callout]
{
  "type": "info",
  "body": "Whois does not work with internal RFC1918 addresses."
}
[/block]
Whois is an Internet service that obtains information about IP addresses, such as the name of the entity that owns it. You can improve Scan Engine performance by not requiring interrogation of a Whois server for every discovered asset if a Whois server is unavailable in the network.

##Fingerprinting TCP/IP stacks

The application identifies as many details about discovered assets as possible through a set of methods called IP fingerprinting. By scanning an asset’s IP stack, it can identify indicators about the asset’s hardware, operating system, and, perhaps, applications running on the system. Settings for IP fingerprinting affect the accuracy side of the performance triangle.

The retries setting defines how many times the application will repeat the attempt to fingerprint the IP stack. The default retry value is 0. IP fingerprinting takes up to a minute per asset. If it can’t fingerprint the IP stack the first time, it may not be worth additional time make a second attempt. However, you can set it to retry IP fingerprinting any number of times.

Whether or not you do enable IP fingerprinting, the application uses other fingerprinting methods, such as analyzing service data from port scans. For example, by discovering Internet Information Services (IIS) on a target asset, it can determine that the asset is a Windows Web server.

The certainty value, which ranges between 0.0 and 1.0 reflects the degree of certainty with which and asset is fingerprinted. If a particular fingerprint is below the minimum certainty value, the application discards the IP fingerprinting information for that asset. As with the performance settings related to asset discovery, these settings were carefully defined with best practices in mind, which is why they are identical.

Configuration steps for collecting information about discovered assets:
1. Go to the _Scan Template Configuration—Asset Discovery_ page.
2. If desired, select the check box to discover other assets on the network, and include them in the scan.
3. If desired, select the option to collect Whois information.
4. If desired, select the option to fingerprint TCP/IP stacks.
5. If you enabled the fingerprinting option, enter a retry value, which is the number of repeated attempts to fingerprint IP stacks if first attempts fail.
6. If you enabled the fingerprinting option, enter a minimum certainty level. If a particular fingerprint is below the minimum certainty level, it is discarded from the scan results.
7. Configure any other template settings as desired. When you have finished configuring the scan template, click **Save**.

##Reporting unauthorized MAC addresses

You can configure scans to report unauthorized MAC addresses as vulnerabilities. The Media Access Control (MAC) address is a hardware address that uniquely identifies each node in a network.

In IEEE 802 networks, the Data Link Control (DLC) layer of the OSI Reference Model is divided into two sub layers: the Logical Link Control (LLC) layer and the Media Access Control (MAC) layer.The MAC layer interfaces directly with the network media. Each different type of network media requires a different MAC layer. On networks that do not conform to the IEEE 802 standards but do conform to the OSI Reference Model, the node address is called the Data Link Control (DLC) address.

In secure environments it may be necessary to ensure that only certain machines can connect to the network. Also, certain conditions must be present for the successful detection of unauthorized MAC addresses:

* SNMP must be enabled on the router or switch managing the appropriate network segment.
* The application must be able to perform authenticated scans on the SNMP service for the router or switch that is controlling the appropriate network segment. See [Enabling authenticated scans of SNMP services](doc:configuring-asset-discovery#section-enabling-authenticated-scans-of-snmp-services).
* The application must have a list of trusted MAC address against which to check the set of assets located during a scan. See [Creating a list of authorized MAC addresses](doc:configuring-asset-discovery#section-creating-a-list-of-authorized-mac-addresses).
* The scan template must have MAC address reporting enabled. See [Enabling reporting of MAC addresses in the scan template](doc:configuring-asset-discovery#section-enabling-reporting-of-mac-addresses-in-the-scan-template).
* The Scan Engine performing the scan must reside on the same segment as the systems being scanned.

##Enabling authenticated scans of SNMP services

To enable the application to perform authenticated scans to obtain the MAC address, take the following steps:

1. Click **Edit** of the site for which you are creating the new scan template on the _Home_ page of the console interface.
The console displays the _Site Configuration_ panel for that site.
2. Go to the _Credentials_ page and click **Add credentials**.
The console displays a _New Login_ box.
3. Enter logon information for the SNMP service for the router or switch that is controlling the appropriate network segment. This will allow the application to retrieve the MAC addresses from the router using ARP requests.
4. Test the credential if desired.
For detailed information about configuring credentials, see [Configuring scan credentials](doc:configuring-scan-credentials).
5. Click Save.
The new logon information appears on the _Credentials_ page.
6. Click the **Save** tab to save the change to the site configuration.

##Creating a list of authorized MAC addresses

To create a list of trusted MAC addresses, take the following steps:

1. Using a text editor, create a file listing trusted MAC addresses. The application will not report these addresses as violating the trusted MAC address vulnerability. You can give the file any valid name.
2. Save the file in the application directory on the host computer for the Security Console.
The default path in a Windows installation is:
C:Program Files\[installation_directory]\plugins\java\1\NetworkScanners\1\\[file_name]
The default location under Linux is:
/opt/[installation_directory]/java/1/NetworkScanners/1/[filename]

##Enabling reporting of MAC addresses in the scan template

To enable reporting of unauthorized MAC addresses in the scan template, take the following steps:
1. Go to the _Scan Template Configuration—Asset Discovery_ page.
2. Select the option to report unauthorized MAC addresses.
3. Enter the full directory path location and file name of the file listing trusted Mac addresses.
4. Configure any other template settings as desired. When you have finished configuring the scan template, click **Save**.

With the trusted MAC file in place and the scanner value set, the application will perform trusted MAC vulnerability testing. To do this it first makes a direct ARP request to the target asset to pick up its MAC address. It also retrieves the ARP table from the router or switch controlling the segment. Then, it uses SNMP to retrieve the MAC address from the asset and interrogates the asset using its NetBIOS name to retrieve its MAC address.