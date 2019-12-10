---
title: "Collector Troubleshooting"
excerpt: ""
---
#Collector Activation Key Does Not Work
First, make sure you have the correct activation key. It's located in the AgentKey.html file in the `/agent-key/` subdirectory of the destination directory where you installed the collector.

If the key is correct but still does not work, it may have been voided. This can occur if you do not activate the collector immediately after installing it or if you have restarted the server where the collector is installed.

If the activation key has been voided, you will need to delete and reinstall your Collector.

##Where is the Activation Key for Linux Collectors?
If you cannot find the activation key for Linux installations, you can find it here: `/opt/rapid7/collector/agent-key/Agent_Key.html`

#Collector Shows as Inactive
Try restarting the Collector service. Contact Rapid7 support if restarting does not fix your issue.
* For Linux Collectors, run `service collector restart` from the command line. On some systems, this command may need superuser privileges (`sudo`).
* For Windows collectors, open the Services app and restart the 'Collector' service.

##Collector Failed to Activate
If activation fails, there is likely a network or routing configuration that is preventing your Collector host from communicating with the Insight platform.  Verify that you have properly configured the necessary whitelisting allowances as detailed on the [Collector Requirements](doc:collector-requirements) page.
    
#Increasing RAM to the Collector  
You can increase the amount of RAM allocated to the collector in environments that require a lot of RAM. To do so, place a file in the same directory where you installed the collector with the name `collector.vmoptions` which contains the following line:

``` shell
-Xmx#g
```

where "#" is the number of GB of memory the collector should use. 
  * For a 4GB machine, you can tell the collector to use 3GB of memory by putting ```–Xmx3g``` in the file. 
  * For an 8GB machine, you can tell the collector to take 6GB of memory by saving a collector.vmoptions file in the collector directory with the line ```–Xmx6g```.

#Unqualified Hostname
Error: **The hostname [hostname of machine running the Collector] is not fully qualified. Agents may not be able to connect to this collector**

To resolve this error, do one of the following:

On a VM:
1. Power off your virtual machine.
2. Change the machine name to a FQDN.
3. Power on your virtual machine. 

For Windows:

1. In the Control Panel, go to Network and Sharing Center, and select Change Settings  in the Computer Name, Domain, and Workgroup section.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/a05ccc0-VerifyFQDNonWindows.png",
        "VerifyFQDNonWindows.png",
        1118,
        628,
        "#f8f9fa"
      ]
    }
  ]
}
[/block]
2. Right-click on the network adapter you are configuring and choose Properties
3. Select Internet Protocol 4 (TCP/IPv4) and then choose Properties. Click on Advanced and then DNS.  
4. Add in the DNS suffix (or suffixes).



[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/3e93ea2-VerifyFQDNonWindows2.png",
        "VerifyFQDNonWindows2.png",
        393,
        484,
        "#ebedef"
      ]
    }
  ]
}
[/block]
#Installation Error on Linux
When installing the Collector on a Linux host, this error can occur:
[block:code]
{
  "codes": [
    {
      "code": "Unpacking JRE ...\nStarting Installer ...\njava.lang.NoClassDefFoundError: java.awt.Container\n        at com.install4j.runtime.installer.frontend.headless.AbstractHeadlessScreenExecutor.init(AbstractHeadlessScreenExecutor.java:67)\n        at com.install4j.runtime.installer.frontend.headless.ConsoleScreenExecutor.init(ConsoleScreenExecutor.java:24)\n        at com.install4j.runtime.installer.frontend.headless.InstallerConsoleScreenExecutor.init(InstallerConsoleScreenExecutor.java:6)\n        at com.install4j.runtime.installer.Installer.getScreenExecutor(Installer.java:92)\n        at com.install4j.runtime.installer.Installer.runInProcess(Installer.java:58)\n        at com.install4j.runtime.installer.Installer.main(Installer.java:46)\n        at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)\n        at sun.reflect.NativeMethodAccessorImpl.invoke(Unknown Source)\n        at sun.reflect.DelegatingMethodAccessorImpl.invoke(Unknown Source)\n        at java.lang.reflect.Method.invoke(Unknown Source)\n        at com.exe4j.runtime.LauncherEngine.launch(LauncherEngine.java:65)\n        at com.install4j.runtime.launcher.UnixLauncher.main(UnixLauncher.java:57)",
      "language": "java"
    }
  ]
}
[/block]
This error indicates that you are missing one or more 32-bit libraries. To solve this issue, run the following command on the Linux host: `sudo apt-get install ia32-libs`

#Uninstall Error on RH Linux

When uninstalling the collector on a RHEL machine, complete the following if you see this error: 

```
Could not display the GUI. This application needs access to an X Server.
 *******************************************************************
You can also run this application in console mode without 
access to an X server by passing the argument -c
*******************************************************************
```
1. Install the RPM package `redhat-lsb.i686`
2. Run the uninstall script again.

#Linux Collectors Do Not Show Collector Details
View your Linux Collector details on **Data Collection > Data Collection Health > Collectors.**

If your Linux collectors are not showing details like the hostname, IP address, OS version, or CPU and Memory usage, the Collector may be having trouble running code from the `/tmp` directory. 

Some distributions of Linux prevent code from running in the `/tmp` directory for security reasons. To verify this is the issue, open your Collector's log file and look for log lines similar to the following:

```
java.lang.UnsatisfiedLinkError: /tmp/jna-3506402/jna5825717272410834572.tmp: /tmp/jna-3506402/jna5825717272410834572.tmp: failed to map segment from shared object: Operation not permitted
```
To fix this issue, execute the following command in the  `/opt/rapid7/insightidr` directory:
`sudo bash -c 'mkdir tmp && echo "-Djava.io.tmpdir=/opt/rapid7/insightidr/tmp" > collector.vmoptions'`

Then, restart the Collector service after executing the above command to resolve the issue.