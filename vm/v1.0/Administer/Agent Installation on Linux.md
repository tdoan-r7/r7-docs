---
title: "Agent Installation on Linux"
excerpt: ""
---
**Please note that this installation requires administrator privileges. **
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/4d3d18e-Screen_Shot_2017-08-28_at_1.37.52_PM.png",
        "Screen Shot 2017-08-28 at 1.37.52 PM.png",
        2326,
        1296,
        "#36404c"
      ]
    }
  ]
}
[/block]
The primary way to install the Insight Agent for Linux is command line installation. 

##Command Line Installation
Ideal for automating many installations, this is a required installation method if you wish to use the agent in local mode and control settings with a configuration file.

Run: `sudo ./agent_installer.sh install_start` in the folder of the Agent that you downloaded.
[block:callout]
{
  "type": "info",
  "title": "Disable auditd service",
  "body": "In order for the Insight Agent to work on Linux, you must disable the auditd service."
}
[/block]
###Uninistall via the Command Line
Run the following command in order to uninstall the Insight Agent on Linux:

`/opt/rapid7/ir_agent/agent_installer.sh uninstall`

##Supported OS
The following Operating Systems are supported:
  * Debian 7.0 - 8.2
  * CentOS 5.2 - 7.3
  * Oracle Enterprise Linux (OEL) 5.2 - 7.3
  * Red Hat Enterprise Linux (RHEL) 5.2 - 7.3
  * Ubuntu 11.04 - 18.04
  * Fedora 17 - 25
  * SUSE Linux Enterprise Server (SLES) 11 -12
  * SUSE Linux Enterprise Desktop (SLED) 11 -12
  * openSUSE LEAP (42.1 - 42.2)
  * Amazon Linux

###Checking Your Version
Run the following command to check your Insight Agent version:

`sudo cat /opt/rapid7/ir_agent/agent.log | grep "Agent Info" | tail -1l`

#Troubleshooting

  * The agent log can be found in `/opt/rapid7/ir_agent` in the agent.log. If you search for the keyword, "logging", this will take you to the agent following and if there is any issues you should see them with `[Error]` messages.
  * Make sure the agent is running by running `sudo service ir_agent status` in terminal.