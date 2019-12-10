---
title: "Software and Appliance installation frequently asked questions"
excerpt: ""
---
This page concerns installation procedures for InsightVM software and the Nexpose Appliance.

##Can I install InsightVM on a system that already has PostgreSQL installed?

No. InsightVM includes its own instance of PostgreSQL. To ensure that it runs properly, you have to stop and remove any instances of PostgreSQL on the host system before installing InsightVM.

##I'm trying to reinstall InsightVM but my license key doesn't work.

InsightVM license keys can only be used once. Contact [Rapid7 Technical Support](mailto:support@rapid7.com) to obtain a new license key.

##How do I make InsightVM start as a daemon in Linux?

If you disabled the intialize/start option as part of the installation, you will need to start InsightVMmanually.

To start InsightVM from the command line, take the following steps:
1. Go to the directory that contains the script that starts InsightVM:
```$ cd [installation_directory]/nsc```

2. Run the script:
```$ ./nsc.sh```
[block:callout]
{
  "type": "warning",
  "body": "To detach from a InsightVM screen session, press CONTROL and type a and then d. Do not use CONTROL-c, which will stop InsightVM."
}
[/block]
The installation creates a daemon named nexposeconsole.rc in the /etc/init.d/ directory.

To manually start, stop, or restart the daemon:
1. Go to the /nsc directory in the installation directory:
```$ cd [installation_directory]/nsc```

2. Run the script to start, stop, or restart the daemon. For the security console, the script file name is nscsvc. For a scan engine, the service name is nsesvc:
```$ ./[service_name] <start|stop>```

To prevent the InsightVM daemon from automatically starting when the host system starts:
```$ update-rc.d [daemon_name] remove```

####I can't start my appliance.

First, make sure that the Appliance is plugged into a power source. Then press the Select button, which has the green checkmark (ü), on the front panel.  If you continue to have difficulty, contact Rapid7 Technical Support.

##What Windows operating systems can I install InsightVM on?

See the Rapid7 Web site for hardware requirements:
[http://www.rapid7.com/products/nexpose/system-requirements.jsp](http://www.rapid7.com/products/nexpose/system-requirements.jsp)

##What Linux operating systems can I install InsightVM on?

See the Rapid7 Web site for hardware requirements:
[http://www.rapid7.com/products/nexpose/system-requirements.jsp](http://www.rapid7.com/products/nexpose/system-requirements.jsp)

##How do I change the time on the Nexpose Appliance?

Using the buttons on the front panel of the Appliance, go the Date/Time submenu under the **Configure** menu in the LCD. There, you can set a new time.

##How do I uninstall InsightVM software?

Each instance of InsightVM must be installed from scratch. If you need to reinstall the program, you must first remove it. Multiple copies of the same instance of the product will not function correctly and are not supported.
[block:callout]
{
  "type": "warning",
  "body": "Uninstalling will completely remove all InsightVM components. It will also delete sites, configurations, reports, and any scan data on discovered assets, nodes and vulnerabilities. Make sure to back up all of your data before proceeding."
}
[/block]
In Windows:
1. Start the uninstaller.
   a. If you created a shortcut folder during installation, click the Windows **Start** button, go the InsightVM folder, and select **InsightVM Uninstaller**.
OR
Click the Windows **Start** button, select the **Windows Control Panel**, and select the option to uninstall or remove a program, depending on the version of Windows you're running.
   b. Double-click InsightVM in the list of programs.

2. Run the uninstaller program.
   a. The uninstaller displays a _Welcome_ page. Note the warning about backing up data. Click **Next**.
   b. The uninstaller displays a status bar with a message that uninstallation is in progress.
   c. The uninstaller displays a message that uninstallation is complete. Click **Finish**.
[block:callout]
{
  "type": "warning",
  "body": "The uninstaller opens a command-line interface window behind the installation wizard window. Although you will not use the command-line window, do not close it. Doing so will stop the uninstallation process."
}
[/block]
In Linux:

1. Run the command: ```$[installation directory]/.install4j```
2. Run the command: ```$./uninstall```
[block:callout]
{
  "type": "info",
  "body": ".install4j is a hidden directory. To list hidden directories, run the command ```ls -a```."
}
[/block]