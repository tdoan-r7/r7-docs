---
title: "Configuring distributed Scan Engines"
excerpt: ""
---
Your organization may distribute Scan Engines in various locations within your network, separate from your Security Console.Unlike the local Scan Engine, which is installed with the Security Console, you need to separately configure distributed engines and pair them with the console, as explained in this section.

Configuring a distributed Scan Engine involves the following steps:

* [Adding an engine](doc:configuring-distributed-scan-engines#section-adding-an-engine) 
* [Pairing the Scan Engine with the Security Console](doc:configuring-distributed-scan-engines#section-pairing-the-scan-engine-with-the-security-console) 
* [Assigning a site to the new Scan Engine](doc:configuring-distributed-scan-engines#section-assigning-a-site-to-the-new-scan-engine) 

## Before you configure and pair a distributed Scan Engine

1. Install the Scan Engine. See the installation guide for instructions. You can download it from [Support: Technical Support and Customer Care](doc:support-technical-support-and-customer-care).
2. Start the Scan Engine. You can only configure a new Scan Engine if it is running.

##Configuring the Security Console to work with a new Scan Engine

By default, the Security Console initiates a TCP connection to Scan Engines over port 40814. If a distributed Scan Engine is behind a firewall, make sure that port 40814 is open on the firewall to allow communication between the Security Console and Scan Engine.

## Adding an engine

The first step for integrating the Security Console and the new Scan Engine is adding information about the Scan Engine.

You can add a Scan Engine while you're configuring a site:

If you are adding an engine while configuring a new site, click the **Create site** button on the _Home_ page.
If you are adding a new engine option to an existing site, click that site's **Edit** icon in the _Sites_ table on the _Home_ page.

1. In the _Site Configuration_ click the **Engines** tab.
2. Select the **Add Scan Engine** tab and then the **General** tab.
3. Enter a unique name that will make it easy for you to remember the engine.
4. Enter the Scan Engine's address and port number on which it will listen for communication from the Security Console.
5. Click **Save**.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/d275ee2-s_nx_add_engine.jpg",
        "s_nx_add_engine.jpg",
        1839,
        804,
        "#1d2939"
      ],
      "caption": "Adding a Scan Engine"
    }
  ]
}
[/block]
After you add the engine, the Security Console creates the _consoles.xml_ file. You will need to edit this file in the pairing process.

If you are a Global Administrator, you also have the option to add an engine through the _Administration_ tab:

1. Click the **Administration** icon.
2. On the _Administration_ page, click **Create** to the right of _Scan Engines_.
3. Click the **General** tab of the _Scan Engine Configuration_ panel.
4. Enter a unique name that will make it easy for you to remember the engine.
5. Enter the IP address and port on for the computer on which the engine is installed.
6. If you have already created sites, you can assign sites to the new Scan Engine by going to the _Sites_ page of this panel. If you have not yet created sites, you can perform this step during site creation.
7. Click **Save**.
After you add the engine, the Security Console creates the _consoles.xml_ file. You will need to edit this file in the pairing process.

## Pairing the Scan Engine with the Security Console

**Note:** You must log on to the operating system of the Scan Engine as a user with administrative permissions before performing the next steps.

Edit the _consoles.xml_ file in the following step to pair the Scan Engine with the Security Console.
1. Open the consoles.xml file using a text editing program. Consoles.xml is located in the [installation_directory]/nse/conf directory on the Scan Engine.
2. Locate the line for the console that you want to pair with the engine. The console will be marked by a unique identification number and an IP address.
3. Change the value for the _Enabled_ attribute from _0_ to _1_.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/5b98d8b-s_nx_consoles_xml.jpg",
        "s_nx_consoles_xml.jpg",
        658,
        238,
        "#edf0f0"
      ],
      "caption": "The Scan Engine's consoles.xml file showing that the Security Console is enabled"
    }
  ]
}
[/block]
4. Save and close the file.
5. Restart the Scan Engine, so that the configuration change can take effect.


Verify that the console and engine are now paired:
1. Click the **Administration** icon.
2. On the _Administration_ page, click **Manage** to the right of _Scan Engines_.
3. On the _Scan Engines_ page, locate the Scan Engine that you added.
Note that the status for the engine is Unknown.
4.Click the **Refresh** icon for the engine.
The Status column indicates with a color-coded arrow whether the Security Console or a Scan Engine is initiating communication in each pairing. The color of the arrow indicates the status of the communication. A green arrow indicates _Active_ status, which means you can now assign a site to this Scan Engine and run a scan with it.

For more information on communication status, see _Managing the Security Console_ in the InsightVM _Administrator's Guide_. [Changing Scan Engine communication direction in the Console](doc:managing-the-security-console#section-changing-scan-engine-communication-direction-in-the-console)
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/559e3ae-s_nx_admin_scan_engine_active.jpg",
        "s_nx_admin_scan_engine_active.jpg",
        1758,
        871,
        "#eff3f4"
      ],
      "caption": "The Scan Engines table with the **Refresh** icon and Active status highlighted"
    }
  ]
}
[/block]
**Note:** If you change the address of the Scan Engine, you will have to pair it with the Security Console again.

On the _Scan Engines_ page, you can also perform the following tasks:
* You can edit the properties of any listed Scan Engine by clicking **Edit** for that engine.
* You can delete a Scan Engine by clicking **Delete** for that engine.
* You can manually apply an available update to the scan engine by clicking **Update** for that engine. To perform this task using the command prompt, see [Using the command console](doc:using-the-command-console).

You can configure certain performance settings for all Scan Engines on the _Scan Engines_ page of the Security Console configuration panel. For more information, see [Changing default Scan Engine settings](doc:managing-the-security-console#section-changing-default-scan-engine-settings).

## Assigning a site to the new Scan Engine

**Note:** If you have not yet set up a site, create one first. See [Creating and editing sites](doc:creating-and-editing-sites).

If you are assigning a site to an engine while configuring it, see [Selecting a Scan Engine for a site](doc:selecting-a-scan-engine-for-a-site).

If you are assigning a site via the _Administration_ tab:
1. Go to the _Sites_ page of the _Scan Engine Configuration panel_ and click **Select Sites**.
The console displays a box listing all the sites in your network.
2. Click the check boxes for sites you wish to assign to the new Scan Engine and click **Save**.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/ca2f411-s_nx_admin_scan_engine_assign_site.png",
        "s_nx_admin_scan_engine_assign_site.png",
        1170,
        555,
        "#f3f7f7"
      ],
      "caption": "Assigning a site to a Scan Engine"
    }
  ]
}
[/block]
The sites appear on the _Sites_ page of the _Scan Engine Configuration_ panel.

3. Click **Save** to save the new Scan Engine information.