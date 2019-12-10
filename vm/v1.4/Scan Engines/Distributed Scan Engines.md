---
title: "Distributed Scan Engines"
excerpt: ""
---
Distributed Scan Engines are separate from the Security Console and are strategically provisioned and located in a way that makes your scanning environment as efficient as possible.  If you intend to maintain a production deployment of the Security Console, distributed Scan Engines are an absolute necessity.

This article guides you through the deployment and configuration process for distributed Scan Engines.

# Deployment Process at a Glance

Deploying a distributed Scan Engine involves the following procedures:

* Installing a new Scan Engine on a separate host machine
* Pairing the Scan Engine to the Security Console according to your communication method of choice
* Refreshing the Scan Engine in the Security Console to verify that the pairing was successful

# Methods of Communication

Scan Engines and Security Consoles must be able to communicate with each other in order to initiate scans and integrate scan data.  Distributed Scan Engines can communicate with a Security Console in two ways:

* **Console-to-Engine** - This is the standard method of communication.  In this case, the Security Console directs the Scan Engine to perform a task by initiating a TCP connection over port 40814.
* **Engine-to-Console** - Also known as the “reverse” communication method, engine-to-console pairings rely on the Scan Engine initiating the connection to the Security Console when the engine starts.
[block:callout]
{
  "type": "info",
  "title": "TIP",
  "body": "You can read more about these configurations on the [Scan Engine Communication Methods](doc:scan-engine-communication-methods) Help page."
}
[/block]
# Requirements

To ensure that you’re set up for success with a distributed Scan Engine, make sure you complete the following preliminary steps:

* Verify that your intended Scan Engine host meets the [system requirements](https://www.rapid7.com/products/insightvm/system-requirements/).
* If firewalls are present on your network, make sure you whitelist the necessary ports for your Security Console and Scan Engine host according to the communication method of your choice.  Consult the following table for port whitelist requirements.

[block:parameters]
{
  "data": {
    "h-1": "Source",
    "h-2": "Destination",
    "h-3": "Port",
    "h-4": "Protocol",
    "0-0": "**Console-to-Engine** ",
    "1-0": "**Engine-to-Console** ",
    "0-1": "Console",
    "0-2": "Scan Engine",
    "0-3": "40814",
    "0-4": "TCP",
    "1-1": "Engine",
    "1-2": "Console",
    "1-3": "40815",
    "1-4": "TCP"
  },
  "cols": 5,
  "rows": 2
}
[/block]

[block:callout]
{
  "type": "warning",
  "title": "NOTE",
  "body": "The ports shown in this table are the default ports used by the Security Console and Scan Engine.  If you modify these default ports during the deployment procedure, make sure your firewall rules match your port modifications."
}
[/block]
# Download and Install the Scan Engine

After verifying that you meet the hardware and networking requirements, you’re ready to download and install the Scan Engine on your intended host machine.
[block:callout]
{
  "type": "danger",
  "title": "REMINDER",
  "body": "Do not install a distributed Scan Engine on a host that already has a Security Console!\n\n“Distributed” Scan Engines are so named because they use hardware entirely reserved for their use.  All Security Console installations already include a local Scan Engine."
}
[/block]

[block:callout]
{
  "type": "warning",
  "title": "NOTE - Distributed Scan Engines on virtual machines",
  "body": "If you intend to deploy a distributed Scan Engine on a virtual machine, ensure that you provision the virtual machine with sufficient reserved memory according to the system requirements.\n\nConfiguring a virtual machine with shared memory may cause the Scan Engine to run out of memory during a scan."
}
[/block]
## Download the Scan Engine Installer

The InsightVM product installer is also responsible for installing distributed Scan Engines.  Visit the [Download](doc:download) page to download the Linux or Windows installer according to the operating system of your intended host machine.

## Install the Scan Engine
[block:callout]
{
  "type": "info",
  "title": "TIP",
  "body": "The following procedure applies to both the Linux command line and the Windows installation wizard."
}
[/block]
Launch the product installer to get started.  Follow the initial prompts until you reach the component selection and communication direction step.

### Select Components

After going through the necessary acknowledgements, you’ll be prompted to select which components you want to install.

Select **Scan Engine only**.  This tells the installer that you intend to deploy a distributed Scan Engine.

### Select a Communication Direction

After selecting your components, you’ll be prompted to select a communication direction.
[block:callout]
{
  "type": "info",
  "title": "Which communication method should I use?",
  "body": "Deciding how your Scan Engine communicates with the Security Console ultimately depends on the configuration and topology of your network.  Production deployments commonly have both Scan Engine types in place in order to accommodate scanning conditions like asset location and the presence of firewalls.\n\nSee the [Scan Engine Communication Methods](doc:scan-engine-communication-methods) Help page for best practices and use case information."
}
[/block]
**If you select the Engine-to-Console method**, you will have the opportunity to configure a reverse pair with your Security Console during the Scan Engine installation.  Although you can skip this pairing step if you want to, Rapid7 recommends that you take advantage of this pairing opportunity since the [post-install reverse pairing procedure](doc:post-installation-engine-to-console-pairing) involves more complicated steps.

To configure a reverse pair during a Scan Engine installation:

1. When prompted by the install wizard, enter the IP address of your Security Console.
2. Provide the installer with the Security Console shared secret.
 * You can generate a shared secret in the Security Console by navigating to the **Administration** tab **>** "Scan Options" section **> manage** next to "Engines" **>** "Generate Scan Engine Shared Secret" section **> Generate**.
[block:callout]
{
  "type": "info",
  "title": "TIP",
  "body": "Multiple Scan Engines can use the same console-generated shared secret for each of their reverse pairing procedures.  However, shared secrets are only valid for 60 minutes.  If your shared secret expires, you must generate a new one to complete any further reverse pairing procedures."
}
[/block]
3. Test your connection to ensure that your Security Console and Scan Engine can communicate properly.
4. Continue with the rest of the Scan Engine installation.
5. After your Scan Engine finishes installing, proceed directly to the [Refresh Your New Scan Engine](doc:configuring-distributed-scan-engines#section-refresh-your-new-scan-engine) section of this guide.

**If you select the Console-to-Engine method**, you’ll need to configure a standard pair with your Security Console after the Scan Engine installation completes.  Continue with the rest of the installation at this time.  After your Scan Engine finishes installing, proceed to the [Pair Your Scan Engine to the Security Console](doc:configuring-distributed-scan-engines#section-pair-your-scan-engine-to-the-security-console) section of this guide.

# Pair Your Scan Engine to the Security Console
[block:callout]
{
  "type": "warning",
  "title": "NOTE",
  "body": "Make sure your new Scan Engine is running and reachable before proceeding with a post-installation pairing procedure.  You must also have admin-level access to your Scan Engine host to complete these pairing procedures."
}
[/block]
All new Scan Engines must be paired to the Security Console in order to be usable for scanning.  These engine pairing procedures differ based on the method of communication you want to implement.

Consult one of the following pairing procedures for your communication method of choice:

* [Standard Pair (Console-to-Engine)](doc:configuring-distributed-scan-engines#section-standard-pair-console-to-engine-)
* [Reverse Pair (Engine-to-Console)](doc:configuring-distributed-scan-engines#section-reverse-pair-engine-to-console-)

## Standard Pair (Console-to-Engine)

In order to configure a console-to-engine pairing, the Security Console must be made aware that a new Scan Engine is available for use and must be provided with instructions on how to reach it.  Consequently, the first step of all standard pairing procedures is to add your new Scan Engine to the Security Console.

You can add a new Scan Engine within a site configuration or through the **Administration** page.

### Add an Engine in a Site Configuration

To add a Scan Engine in a site configuration:

1. In a new or existing site configuration, click the **Engines** tab.
 * You can create a new site by expanding the **Create** dropdown next to the left navigation menu, or access an existing site by clicking its edit icon in the “Sites” table of the **Home** page.
2. Click the **Add Scan Engine** subtab.
3. Name your Scan Engine.
4. Enter the IP address of your Scan Engine in the “Address” field.
5. If you need to adjust the default port number, modify the value shown in the “Port” field.
6. Assuming your site has the minimum set of required information, click **Save** when finished.

### Add an Engine through Administration

To add a Scan Engine through the **Administration** tab:

1. Browse to and click on the **Administration** tab in your left navigation menu.
2. In the “Scan Options” section, click **create** next to “Engines”.
3. On the **General** tab, name your Scan Engine.
4. Enter the IP address of your Scan Engine in the “Address” field.
5. Click **Save** when finished.

Properly added Scan Engines generate a `consoles.xml` file on the Scan Engine host.  You will modify this file in the next step.

### Modify consoles.xml

The `consoles.xml` file generated on your Scan Engine host in the previous step contains an entry for the Security Console that added the Scan Engine.  You must enable the console to complete the pairing.

To modify the `consoles.xml` file for a Linux or Windows host:

1. Browse to the `consoles.xml` file in your Scan Engine directory.  By default, this file is located in the following places according to the operating system of your Scan Engine host:
 * **Linux** - `/opt/rapid7/nexpose/nse/conf/consoles.xml`
 * **Windows** - `Files\Rapid7\NeXpose\nse\conf\consoles.xml`
2. Open `consoles.xml` with a text editor of your choice.  Navigate to the `<consoles>` element.  The Security Console that added the Scan Engine appears as a `<console>` element with several attributes.
 * You can identify the correct Security Console by checking that the `lastAddress` attribute matches the IP address of the Security Console you want to pair with.
3. Change the value for the `enabled` attribute from `0` to `1`.
4. Save and close the `consoles.xml` file.
5. Restart the Scan Engine host so your changes can take effect.
[block:callout]
{
  "type": "success",
  "title": "Pairing procedure complete!",
  "body": "Proceed to the [verification step](doc:configuring-distributed-scan-engines#section-refresh-your-new-scan-engine) to finish your Scan Engine deployment."
}
[/block]
## Reverse Pair (Engine-to-Console)

If you took advantage of the reverse pairing configuration opportunity during your Scan Engine installation, then you’ve already completed this step!  Proceed directly to the [Refresh Your New Scan Engine](doc:configuring-distributed-scan-engines#section-refresh-your-new-scan-engine) section of this guide to verify that your Scan Engine is ready for use.

However, if you installed a Scan Engine with the **Engine-to-Console** method selected without completing the reverse pairing step, you must complete the pairing with a separate procedure.  See the [Post-Installation Engine-to-Console Pairing](doc:post-installation-engine-to-console-pairing) page for instructions on how to do this.

# Refresh Your New Scan Engine

After completing a standard or reverse pair for your Scan Engine, you must refresh its status to verify that the Security Console can communicate with it properly.

To refresh your new Scan Engine in the Security Console:

1. Browse to and click on the **Administration** tab in your left navigation menu.
2. In the “Scan Options” section, click **manage** next to “Engines”.
3. In the “Scan Engines” section, click **Refresh Displayed Engines**.  This ensures that your Scan Engine table is up-to-date.
4. Locate the distributed Scan Engine that you paired to the Security Console.  Click the icon in the “Refresh” column to complete the verification process.

If you have properly configured and paired your Scan Engine, it now displays up-to-date version and communication status information.  The “Communication Status” column itself indicates both the current communication method by arrow and connection state by color.  Arrows pointing to “Engine” indicate a standard pairing, while arrows pointing to “Console” indicate reverse pairing.  Additionally, arrow icons can have the following color codes:

* **Green** - Scan Engine is active
* **Orange** - Scan Engine status is unknown
 * An “unknown” status indicates that the Security Console and the Scan Engine could not communicate even though no error was recorded.  This is often the result of a significant lapse between pings.  Refresh the Scan Engine status to attempt communication again.
* **Red** - There are three possibilities associated with this color code:
 * **Pending Authorization** - This state indicates that the Security Console has not yet been enabled on the Scan Engine.  Consoles must be enabled on the Scan Engine [during the pairing procedure](doc:configuring-distributed-scan-engines#section-pair-your-scan-engine-to-the-security-console).
 * **Incompatible** - This state indicates that the Security Console and Scan Engine are on different versions.  Consoles and engines must be on the same version in order to communicate properly.
 * **Down** - This state indicates that the Scan Engine is offline.
[block:callout]
{
  "type": "success",
  "title": "Congratulations!",
  "body": "You should now have successfully deployed a distributed Scan Engine."
}
[/block]