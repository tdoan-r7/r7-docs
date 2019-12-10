---
title: "Running the application"
excerpt: ""
---
This section includes the following topics to help you get started with the application:
* [Managing the application in Linux](doc:running-the-application#section-managing-the-application-in-linux)
* [Managing the application in Windows](doc:running-the-application#section-managing-the-application-in-windows)

# Managing the application in Linux

If you disabled the initialize/start option as part of the installation, you will need to start the application manually.  The application will also automatically start after reboot.

The commands for starting or stopping the service are dependent on the **init** system. Inspect `/sbin/init` to determine if the system is using **systemd** or **sysV**.

```file /sbin/init``` will display if **init** is a real executable or a symbolic link. On a system running **systemd**, **init** is a symlink to `/lib/systemd/systemd`.
[block:callout]
{
  "type": "info",
  "body": "Run the commands below by selecting one argument from each group.  Example:\n\n`systemctl start nexposeconsole`",
  "title": "Running the proper command"
}
[/block]
### Managing the application on Systemd
```systemctl [status|start|stop] {nexposeconsole|nexposeengine}```

### Managing the application on SysV
```service {nexposeconsole|nexposeengine} [status|start|stop]```

## Verify the application is running
```ps aux | grep nexpose```

## Interacting with the application
By default, the application runs in a screen session to allow interactive commands to be executed.  Run ```screen -list``` as the root user to view the current screen sessions.

## Connect to the screen session
```screen -r nexpose```

Type ```help``` in the screen session for a list of interactive commands.

## Disconnect from the screen session
To detach from a screen session, press <**CTRL+A**> <**CTRL+D**>.
[block:callout]
{
  "type": "danger",
  "body": "Do not use <CTRL+C>, it will stop the application."
}
[/block]
##Enable/Disable the service from running at startup

### Enable/Disable the service on Systemd systems

To enable/disable the application from automatically running at startup, run the following command:
```systemctl [enable|disable] {nexposeconsole|nexposeengine}```

### Enable/Disable the service on SysV systems

To enable/disable the application from automatically running at startup, run the following command:
```update-rc.d {nexposeconsole|nexposeengine} [defaults|remove]```

# Managing the application in Windows

InsightVM is configured to start automatically when the host system starts. If you disabled the initialize/start option as part of the installation, or if you have configured your system to not start automatically as a service when the host system starts, you will need to start it manually.

Starting the Security Console for the first time will take 10 to 30 minutes because the database of vulnerabilities has to be initialized. You may log on to the Security Console Web interface immediately after the startup process has completed.

Your installation comes with dedicated start/stop applets that can be run from the Windows **Start** menu. If you have disabled automatic startup, use the following procedure to start the application manually:

1. Click the Windows **Start** button.
2. Browse to the **Rapid7** folder, or simply input “Rapid7” in the search field.
3. Click the **Start Security Console Service** or the **Stop Security Console Service** icon, depending on which you need to run.

Alternatively, you can start, stop, and check the status of InsightVM services from the **Windows Services Manager**.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/202ad46-services_1.png",
        "services_1.png",
        1098,
        74,
        "#14296d"
      ],
      "caption": "Security Console Services"
    }
  ]
}
[/block]

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/1f4a384-services_2.png",
        "services_2.png",
        1124,
        44,
        "#0e276e"
      ],
      "caption": "Scan Engine Service"
    }
  ]
}
[/block]
## Changing the configuration for starting automatically as a service

By default the application starts automatically as a service when Windows starts. You can disable this feature and control when the application starts and stops.
1. Click the **Windows Start** button, and select **Run...**
2. Type services.msc in the _Run_ dialog box.
3. Click **OK**.
4. Double-click the icon for the Security Console service in the _Services_ pane.
5. Select _Manual_ from the drop-down list for **Startup type**.
6. Click **OK**.
7. Close _Services_.