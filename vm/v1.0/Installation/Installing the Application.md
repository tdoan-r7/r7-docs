---
title: "Installing the Application"
excerpt: ""
---
## Installation requirements
Make sure that your host hardware and network support the installation operations.

### Hardware requirements
See the Rapid7 Web site for hardware requirements:
[http://www.rapid7.com/products/insightvm/system-requirements/](http://www.rapid7.com/products/insightvm/system-requirements/).

It is recommended that you install the application on a computer that does not have an Intrusion Detection System (IDS), an Intrusion Prevention System (IPS), or a firewall enabled. These devices block critical operations that are dependent on network communication.

The 64-bit configuration is recommended for enterprise-scale deployments.

Scan Engines contact target assets using TCP, UDP, and ICMP to perform scans. They do not initiate outbound communication with the Security Console.

Ideally there should be no firewalls or similar devices between a Scan Engine and its target assets. Also, scanning may also require some flexibility in security policies. For more information, see the _administrator's guide_.

## Supported platforms
See the Rapid7 Web site for supported platforms:
[http://www.rapid7.com/products/insightvm/system-requirements/](http://www.rapid7.com/products/insightvm/system-requirements/).

## Making sure you have necessary items
Make sure you have all of the following items before you begin the installation process:

- installers for all supported environments (.bin files for Linux and .exe files for Windows)
- the md5sum, which helps to ensure that installers are not corrupted during download
- documentation, including this guide
- a license key, which you need to activate your license when you log on
[block:callout]
{
  "type": "info",
  "body": "Installers and md5sum files can be found [here](https://kb.help.rapid7.com/docs/insightvm-and-nexpose-installers-md5sum-files-and-virtual-appliances)."
}
[/block]
If you do not have any of these items, contact your account representative. If you purchased the application or registered for an evaluation, Rapid7 sent you an e-mail that includes links for downloading these items and the license key. It is recommended that you add InsightVM to your e-mail client white list communication to ensure you receive future e-mails about InsightVM.

During the installation, the installer runs a system check and identifies any system components or settings that meet the minimum requirements but not the recommended requirements. If any items are identified, you can continue the installation, but you should consider modifying your system after the installation to ensure optimal performance. For example, if your system does not have the recommended the amount of RAM, you may encounter performance issues with RAM-intensive operations, such as running scans or reports. To prevent this, you should consider adding RAM to your system.

## Uninstalling a previously installed copy

Installing and using multiple copies of the software on the same server is not supported. If you install multiple copies on the same server, the application will not function properly.

Each copy of the software must be installed from scratch. This means that if you already have a copy installed, you must uninstall it before you install the new copy you downloaded.

Use the procedure in the section [Running the Windows uninstaller](doc:running-the-windows-uninstaller) or [Running the Linux uninstaller](doc:running-the-linux-uninstaller) to uninstall any previously installed copies.

## Creating an account during installation

When you install the application, you create a default Global Administrator account. You will use the account to log onto the application after you complete the installation.

Recovery of credentials is not supported. If you forget your user name or password, you will have to reinstall the program. Credentials are case-sensitive.

As you enter credentials, the complexity requirements are displayed to ensure that you create strong (secure) credentials. Even if your password meets the requirements, it is recommended that you make your password as strong as possible for better security. A “heat bar” is displayed that gradually changes color from red to green as you make your password stronger.

A Global Administrator can create and modify accounts after installation. See [Managing users and authentication](doc:managing-users-and-authentication).

## Installation choices

During the installation, you will make several choices, including the following:

- Select the component(s) you want to install and where to install them. 
- Enable the application to initialize during the installation and start automatically after installation. 
- If you install only the Scan Engine, you must select a communication direction between an existing Security Console and the new Scan Engine. 

### Selection of components

You can either install a Security Console with a local Scan Engine or you can install a distributed Scan Engine. If you install the latter, you must have a Security Console running in your environment before you can use the Scan Engine. The Security Console controls all Scan Engine activity.

### Application initialization and automatic start option

You can choose to have the application initialize during installation and automatically start once you finish the installation. By default, this option is enabled. If you do not want initialization to occur during installation, you must disable it.

You can only leave this option enabled if you install both components (the Scan Engine and Security Console). If you choose to install only the Scan Engine, this option is not available.

The benefit to leaving the option enabled is that you can start using the application immediately after the installation is complete. This is because the initialization process prepares the application for use by updating the database of vulnerability checks and performing the initial configuration.

Because the time required for the initialization process ranges from 10 to 30 minutes, leaving the option enabled increases the total installation time by 10 to 30 minutes. Although disabling the option shortens the installation time, it takes longer to start the application because it has to initialize before you can begin using it.

### Communication direction between Console and Engine

Which direction is preferred depends on your network configuration:

- Engine to Console: The Scan Engine will actively inform the Security Console that it is available for communication. This configuration allows a console that is behind a firewall and is configured to allow inbound connections to establish a communication channel.
- Console to Engine: The Scan Engine will listen for communication from the Security Console. This configuration is most effective when the engine and console are on the same area of the network.

### Tips for using the installation wizard

The pages of the wizard are listed in the left page of the wizard, and the current page is highlighted. You can use the list to check your progress.

Each page of the wizard has a **Previous** button and a **Cancel** button. Use the **Previous** button to go to a previous page if you need to review or change an installation setting. Use the **Cancel** button only if you need to cancel the installation. If you cancel at any point in during the installation process, no files are installed and you need to go back to the beginning of the installation process.