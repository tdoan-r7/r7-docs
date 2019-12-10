---
title: "Using the command console"
excerpt: ""
---
If you are a Global Administrator, you can perform certain Security Console operations using the command console. You can see real-time diagnostics and a behind-the-scenes view of the application when you use this tool.

You can type help to see a list of all available commands and their descriptions. For more detailed information, see [Available commands](doc:using-the-command-console#section-available-commands).

##Accessing the command console

Global Administrators have access to the Security Console to perform administrative functions. For a list of commands, see [Available commands](doc:using-the-command-console#section-available-commands).

###Accessing the command console in Windows

1. Click the **Administration** tab in the Security Console Web interface.
The Security Console displays the _Administration_ page.
2. Click the link to **Run** console commands, which is displayed with the _Troubleshooting_ item.
The command console page appears with a box for entering commands.
3. Enter a command.
4. Click **Execute**.

###Accessing the command console in Linux

To use the Security Console Web interface in Linux:
1. Start a console screen session if one is not already in progress.
If the host is remote, use SSH to log on first.
2. Type commands and click **ENTER**.

If you are running the Security Console on an Appliance, you can perform all operations using the Appliance’s LCD or via the Security Console Web interface.

For more information on using the Appliance LCD, see the installation and quick-start guide, which you can download from the _Support_ page of **Help**.

##Available commands

A list of available commands follows. Text in square brackets contain optional parameters, as explained in the action descriptions. Text in arrow brackets contain variables.
[block:parameters]
{
  "data": {
    "h-0": "Command",
    "h-1": "Action",
    "0-1": "Activate the application with a license key.",
    "0-0": "activate",
    "1-0": "database diagnostics",
    "1-1": "Check the database for inconsistencies, such as partially deleted sites or missing synopsis data, which can affect counts of assets, sites, asset groups, scans, or nodes as displayed in the Web interface.",
    "2-0": "[show] diag[nostics]",
    "2-1": "Display diagnostic information about the Security Console.",
    "3-1": "Stop the Security Console service.",
    "3-0": "exit",
    "4-0": "garbagecollect",
    "4-1": "Start the garbage collector, a Java application that frees up drive space no longer used to store data objects.",
    "5-0": "get property [<name>]",
    "5-1": "View the value assigned to a parameter associated with the Scan Engine. Example: ```get property os.version```. The Security Console would return: ```os.version=5.1```. If you type get property without a parameter name, the Security Console will list all properties and associated values. You can view and set certain properties, such as the IP socket number, which the application uses for communication between the Security Console and the Scan Engine. Other properties are for system use only; you may view them but not set them.",
    "6-0": "heap dump",
    "6-1": "“Dump” or list all the data and memory addresses “piled up” by the Java garbage collector. The dump file is saved as heap.hprof in the nsc directory.",
    "7-0": "help",
    "7-1": "Display all available commands.",
    "8-0": "license request from-email-address [mail-relay-server]",
    "8-1": "E-mail a request for a new license. The email-address parameter is your address as the requestor. The optional ```mail-relay-server``` parameter designates an internally accessible mail server to which the license server should connect to send the e-mail. After you execute this command, the application displays a message that the e-mail has been sent. When you receive the license file, store it in the ```nsc/licenses``` directory without modifying its contents. Licenses have a ```.lic``` suffix.",
    "9-0": "log rotate",
    "9-1": "Compress and save the nsc.log file and then create a new log.",
    "10-0": "ping \nhost-address \n[tcp-port]",
    "10-1": "Ping the specified host using an ICNMP ECHO request, ICP ACK packet, and TCP SYN packet. The default TCP port is 80.",
    "11-0": "quit",
    "11-1": "Stop the Security Console service.",
    "12-0": "restart",
    "12-1": "Stop the Security Console service and then start it again.",
    "13-0": "[show] \nschedule",
    "13-1": "Display the currently scheduled jobs for scans, auto-update retriever, temporal risk score updater, and log rotation.",
    "14-0": "show host",
    "14-1": "Display information about the Security Console host, including its name, address, hardware configuration, and Java Virtual Machine (JVM) version. The command also returns a summary of disk space used by the installation with respect to the database, scans, reports, and backups.",
    "15-0": "show licenses",
    "15-1": "Display information about all licenses currently in use. Multiple licenses may operate at once.",
    "16-0": "show locked accounts",
    "16-1": "List all user accounts locked out by the Security Console. The application can lock out a user who attempts too many logons with an incorrect password.",
    "17-0": "show mem",
    "17-1": "List statistics about memory use.",
    "18-0": "[send] support [from-email-address] [mail-relay-server] \n[message-body]",
    "18-1": "Send logs generated by the Security Console and Scan Engine(s) for troubleshooting support. By default, the application sends the request to a log server via HTTPS. Alternatively, you can e-mail the request by specifying a sender's e-mail address or outbound mail relay server. You also can type a brief message with the e-mail request. When you execute the command, the Security Console displays a scrolling list of log data, including scheduled scans, auto-updates, and diagnostics.",
    "19-0": "[show] threads",
    "19-1": "Display the list of active threads in use.",
    "20-0": "traceroute host-address",
    "20-1": "Determine the IP address route between your local host and the host name or IP address that you specify in the command. When you execute this command, the Security Console displays a list of IP addresses for all “stops” or devices on the given route.",
    "21-0": "unlock account <name>",
    "21-1": "Unlock the user account named in the command.",
    "22-0": "update engines",
    "22-1": "Send pending updates to all defined Scan Engines.",
    "23-0": "update now",
    "23-1": "Check for and apply updates manually and immediately, instead of waiting for the Security Console to automatically retrieve the next update.",
    "24-0": "[ver] version",
    "24-1": "Display the current software version, serial number, most recent update, and other information about the Security Console and local Scan Engine. Add “console” to the command to display information about the Security Console only. Add “engines” to the command to display information about the local Scan Engine and all remote Scan Engines paired with the Security Console.",
    "25-0": "?",
    "25-1": "Display all available commands."
  },
  "cols": 2,
  "rows": 26
}
[/block]