---
title: "Collector Installation and Deployment"
excerpt: ""
---
After you’ve verified that your intended Collector host meets the [system and network requirements](doc:collector-requirements), complete the following procedure to download, install, and activate a Collector on your network.

In InsightVM, browse to the Collector download page:

1. In your left navigation menu, open the **Management** tab.
2. Under “Settings”, click the **Collectors** tab.
3. In the upper right corner of the screen, click **Download Collector**.

The “Download Collector” page contains buttons for the Windows `.exe` installer and the Linux  `.sh` installer.

Consult one of the following installation procedures based on your operating system:

* [Linux](doc:collector-installation-and-deployment#section-linux)
* [Windows](doc:collector-installation-and-deployment#section-windows)

# Linux
[block:callout]
{
  "type": "warning",
  "title": "Linux Installation Procedure Note",
  "body": "This procedure assumes that you will provide the `.sh` installer script to a remote Linux host via Secure Copy (SCP) or a similar method.\n\nAdditionally, your account must have read and write access."
}
[/block]
To install the Collector on a remote Linux host:

1. Send the `InsightSetup-Linux64.sh` installer script to your target Linux host using your method of choice.
2. SSH to the target system and navigate to the installer’s current directory.
3. Modify the permissions of the script to make it executable:

```
chmod +x InsightSetup-Linux64.sh
```
4. Run the script to start the installer:

```
./InsightSetup-Linux64.sh
```
5. A terminal wizard guides you through the installation process.  Proceed through the system settings and license prompts to start the installation.
6. When the installation completes, copy the value shown next to `Agent key:`.
7. Proceed to the [Collector activation step](doc:collector-installation-and-deployment#activate-your-collector) when ready.

# Windows
[block:callout]
{
  "type": "warning",
  "title": "Windows Installation Procedure Note",
  "body": "This procedure assumes that you intend to install the Collector on the same Windows host you used to download the installer."
}
[/block]
To install the Collector on your Windows host:

1. Run the `InsightSetup-Windows64.exe` installer.  A wizard guides you through the installation process.
2. The wizard displays your activation key during the installation.  Copy the activation key at this time.
3. When the Collector finishes installing, proceed to the [Collector activation step](doc:collector-installation-and-deployment#activate-your-collector).

# Activate Your Collector

With your Collector installed and your activation key ready, you can now activate this Collector in your environment:

1. Return to the Collector management space in InsightVM.  In the upper right corner of the screen, click **Activate Collector**.
2. Specify a name for your Collector in the provided field.
3. Paste your activation key in the corresponding field and click **Activate**.

After starting the activation process, InsightVM returns you to the Collector management space.  Your new Collector appears in a “waiting” state while activation is in progress.

If your Collector activation succeeds, a green check mark appears next to its name along with its hostname, IP address, OS version, CPU usage, and memory usage.