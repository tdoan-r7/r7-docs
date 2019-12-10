---
title: "Log in and activate"
excerpt: ""
---
With your installation complete, you can now log in to the Security Console.
[block:callout]
{
  "type": "info",
  "title": "Have your license key ready!",
  "body": "You will enter your license key immediately after logging in."
}
[/block]
# Do you need to initialize?

If you chose not to initialize the console during installation, you must do so now.  Reboot your system at this time to automatically start the necessary services.  Alternatively, you can manually start the services using the controls shown on the [Service start, stop, and status controls](doc:service-start-stop-and-status-controls) page.
[block:callout]
{
  "type": "info",
  "title": "TIP",
  "body": "The Security Console and Scan Engine services will start automatically on host startup from this point forward."
}
[/block]
# Log in

Open your supported browser and connect to the following address, substituting `<console_address>` with the FQDN or IP address of the machine where your Security Console is installed:

```
https://<console_address>:3780
```
[block:callout]
{
  "type": "info",
  "title": "Accessing the Security Console from the same machine that it’s installed on?",
  "body": "In this case, you can quickly access the web interface by connecting to `https://localhost:3780`."
}
[/block]

[block:callout]
{
  "type": "warning",
  "title": "Initialization progress",
  "body": "If you just started to initialize after installation, it may still be in progress when you connect to the Security Console.  You must wait for this process to complete before you can log in."
}
[/block]
A login prompt will display.  Enter the credentials that you set up during the Security Console installation and click **LOG ON**.

# Activate

After you log in successfully, an activation prompt will appear.  Enter your activation key in the provided field to activate your license.  The activation process should only take a few minutes.
[block:callout]
{
  "type": "warning",
  "title": "NOTE",
  "body": "In the rare event that product updates become available during the activation process, the time to activate may be extended."
}
[/block]

[block:callout]
{
  "type": "success",
  "title": "Congratulations!",
  "body": "You’ve successfully deployed the Security Console!  Now let's get familiar with the web interface."
}
[/block]