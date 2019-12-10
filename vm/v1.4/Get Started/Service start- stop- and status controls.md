---
title: "Service start, stop, and status controls"
excerpt: ""
---
Use the following controls and commands to start, stop, or check the status of the Security Console and Scan Engine services.

Service controls are organized according to the operating system of the host machine:

* [Linux](doc:service-start-stop-and-status-controls#section-linux)
* [Windows](doc:service-start-stop-and-status-controls#section-windows)

# Linux

Service commands for Linux installations depend on the `init` system.  Inspect `/sbin/init` to determine if your system is using `systemd` or `sysV`.

`systemd` - `init` is a symbolic link to `/lib/systemd/systemd`.
`sysV` - `init` is a real executable.

## systemd commands
[block:parameters]
{
  "data": {
    "h-0": "Function",
    "h-1": "Security Console",
    "h-2": "Scan Engine",
    "0-0": "Start",
    "1-0": "Stop",
    "2-0": "Status",
    "0-1": "`systemctl start nexposeconsole`",
    "0-2": "`systemctl start nexposeengine`",
    "1-1": "`systemctl stop nexposeconsole`",
    "1-2": "`systemctl stop nexposeengine`",
    "2-1": "`systemctl status nexposeconsole`",
    "2-2": "`systemctl status nexposeengine`"
  },
  "cols": 3,
  "rows": 3
}
[/block]
## sysV commands
[block:parameters]
{
  "data": {
    "h-0": "Function",
    "h-1": "Security Console",
    "h-2": "Scan Engine",
    "0-0": "Start",
    "1-0": "Stop",
    "2-0": "Status",
    "0-1": "`service nexposeconsole start`",
    "0-2": "`service nexposeengine start`",
    "1-1": "`service nexposeconsole stop`",
    "1-2": "`service nexposeengine stop`",
    "2-1": "`service nexposeconsole status`",
    "2-2": "`service nexposeengine status`"
  },
  "cols": 3,
  "rows": 3
}
[/block]
# Windows

Your Security Console installation includes dedicated start and stop applets:

1. Open your **Start** menu.
2. Browse to the “Rapid7” folder.
3. Run the **Start Security Console Service** or **Stop Security Console Service** applet as required.

Alternatively, you can start, stop, and check the status of the Security Console, Scan Engine, and database services from Windows Services Manager:

1. Open your **Start** menu.
2. Click **Run**.
3. Enter `services.msc` in the provided field.  Click **OK**.
4. Browse to the following services to check their status:
 * "Nexpose PostgreSQL Server"
 * "Nexpose Security Console"
 * "Nexpose Scan Engine"
5. Right click the service to stop and start as required.