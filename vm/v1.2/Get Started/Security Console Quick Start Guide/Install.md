---
title: "Install"
excerpt: ""
---
Before continuing, make sure you have these items:

* The latest Linux or Windows [installer](doc:download)
* The corresponding [checksum file](doc:download#section-checksum-files) for your installer
* A license key

# Considerations

Read through these sections before you start the installation process.

## Default account creation

In the course of your installation, you’ll create a default account with Global Administrator privileges.  When you configure these credentials, take care to store them in a safe place.

## Installation options

There are two installation options:

* Security Console with a local Scan Engine
* Scan Engine only

If you’re following the [basic deployment plan](doc:basic-deployment-plan), you’ll install a **Security Console with a local Scan Engine**.
[block:callout]
{
  "type": "warning",
  "title": "Only installing a Scan Engine?",
  "body": "While this will generally be unnecessary for trial deployments, keep in mind that production deployments make extensive use of dedicated Scan Engines.\n\nScan Engines are controlled by the Security Console and cannot operate without being paired with one.  Scan Engine-only installations assume that you have a Security Console installed elsewhere in your network.\n\nSee the [Configuring distributed Scan Engines](doc:configuring-distributed-scan-engines) page for instructions on how to pair and configure a dedicated Scan Engine."
}
[/block]
## Enable/disable initialization

Enabled by default, this option will initialize the Security Console after it’s been installed.  Initialization configures the application for use and updates the vulnerability database.  If you enable initialization, your installation time will increase respective to that process.  Initialization time ranges from 10 to 30 minutes.
[block:callout]
{
  "type": "danger",
  "title": "IMPORTANT - FIPS Mode requirements",
  "body": "While most organizations do not require this configuration, ensure that you DO NOT initialize the console during your installation if you intend to use FIPS mode.\n\nFIPS mode must be configured before the Security Console is started for the first time.  See [Enabling FIPS mode](doc:enabling-fips-mode) for instructions."
}
[/block]
# Install

Now that you’ve considered your options, follow one of the procedures below according to your OS:

* [Linux](doc:install#section-linux)
* [Windows](doc:install#section-windows)

## Linux
[block:callout]
{
  "type": "warning",
  "title": "REQUIRED",
  "body": "You must have root-level access.\n\nFor Ubuntu and Red Hat installations, you must also have the `screen` package installed.  Use APT or YUM, respectively, to install the `screen` package."
}
[/block]
1. Make sure your installer and checksum file are in the same directory.
2. Open a terminal and browse to the directory where your installer and checksum file are located.
3. Run the following command, substituting `<installer_file_name>` with the appropriate value:

```
md5sum -c <installer_file_name>.md5sum
```
4. If this command returns an `OK` message, the file is valid.
 * If the check fails, download the installer again and retry.
5. Modify the permissions of the installer to make it executable:

```
chmod +x <installer_file_name>
```
6. Run the installer:

```
./<installer_file_name> -c
```
[block:callout]
{
  "type": "info",
  "title": "Using a GUI?",
  "body": "If you are using a Graphical User Interface, omit the `-c` switch at the end of the installer run command.  You’ll use a wizard similar to the Windows version instead."
}
[/block]
7. Follow the instructions prompted by the installer.  You’ll decide on the considerations mentioned previously throughout the process.

## Windows
[block:callout]
{
  "type": "warning",
  "title": "REQUIRED",
  "body": "You must have Administrator privileges."
}
[/block]
1. Make sure your installer and checksum file are in the same directory.
2. Open a command prompt and browse to the directory where your installer and checksum are located.
3. Run the following command, substituting `<installer_file_name>` with the appropriate value:

```
certutil -hashfile <installer_file_name> md5
```
4. Run the installer.
[block:callout]
{
  "type": "danger",
  "title": "IMPORTANT",
  "body": "A command line window will appear during the installation, but you will not need to interact with it.  DO NOT close this window."
}
[/block]
5. An installation wizard will guide you through the steps.  You’ll decide on the considerations mentioned previously throughout the process.
[block:callout]
{
  "type": "success",
  "title": "Installation complete!",
  "body": "You should now have the Security Console with a local Scan Engine installed.  It’s time to log in and complete your activation."
}
[/block]