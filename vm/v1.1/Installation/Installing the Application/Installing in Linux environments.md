---
title: "Installing in Linux environments"
excerpt: ""
---
See the instructions for your specific supported Linux distribution.

## Do I need to disable SELinux?

SELinux is a security-related feature that must be disabled before you can install the application.

Later versions of Ubuntu do not include SELinux, or it is automatically set to` permissive`. It is recommended that you check the status before you start the installation.

To disable SELinux, take these steps:

1. Open the SELinux configuration file in your preferred text editor. 

Example: `$ vi /etc/selinux/config`

2. Go the line that begins with `SELINUX=.`

If the setting is `enforcing`, change it to `disabled:``SELINUX=disabled`

3. Save and close the file.
4. Restart the server for the change to take effect: `$ shutdown -r now`

At this point you can check the installer file to make sure it is not corrupted or begin the installation. It is recommended that you check the installer file before you begin the installation.

## Ensuring that the installer file is not corrupted

This procedure shows you how to check the installer file you downloaded to make sure it is not corrupted. This helps to prevent installation problems.

Make sure that you downloaded the installation file and the md5sum file. See [Installing the Application](doc:installing-the-application) for details.

To check the installer file, take these steps:

1. Go to the directory that contains the installer and the md5sum file. If you have not changed any settings, this will be `Downloads`.
2. Run the md5sum program with the -c option to check the MD5 checksum: 

`$ md5sum -c [installer_file_name].md5sum`

- If this command returns an `OK` message, the file is valid. 
- If it returns a “FAILED” message, download the installer and md5sum file again, and repeat this procedure. 

## Installing in Ubuntu 

Make sure that:

- You have downloaded all items necessary for installation. See [Installing the Application](doc:installing-the-application).
- You have root-level access.
- (Recommended) You check the installer file to make sure it was not corrupted during the download. 

###Manually installing necessary packages in Ubuntu

If sudo is active in your environment, and if your account is listed in the sudoers file, you can use sudo ‑i to run the commands.
Rapid7 recommends using apt-get to install packages on Ubuntu.
To install the necessary packages:

1. To verify that you have apt-get, run: 

`
              $ apt-get –v`

2. To determine if you have a required package and install it if necessary, run:

` $ apt-get install [package_name]`

The following package should be installed: 
- screen

## Installing in Red Hat 

You must have root-level access to run the installation. If sudo is active in your environment, and if your account is listed in the sudoers file, you can use sudo -i to run the commands.

Make sure that:

- You have downloaded all items necessary for installation. See [Installing the Application](doc:installing-the-application) for details.
- You have yum and RPM, which you need to install packages on Red Hat. 
- You have a Red Hat Enterprise Linux license. 
- (Recommended) You check the installer file to make sure it was not corrupted during the download.

### Manually installing necessary packages in Red Hat

You need yum and RPM to install packages on Red Hat.

1. To verify that you have yum and RPM, run: `$ yum --version `
2. To determine if you have a required package and install it as necessary, run:

`$ yum install [package_name] `

The following package should be installed: `screen`.

## Running the Linux installer

This procedure shows you how to install the application in a Linux environment.

### If you are using a graphical user interface

If you are using an interface such as KDE or Gnome, omit the `–c flag` in step 3 of the procedure. The installer opens a wizard to guide you through the installation (similar to the Windows installation wizard (see [Installing in Windows Environments](doc:installing-in-windows-environments)). The rest of the steps in this procedure reflect installation using the command line interface.

### Before you begin

Make sure that:

- Your system meets the minimum installation requirements. 
- You have all of the items you need to complete the installation.
- You have disabled SELinux (if necessary). 
- (Recommended) You check the installer file to make sure it was not corrupted during the download.  
- You have installed the required packages for your Linux platform. 
- You have uninstalled any previously installed copies. See [Running the Linux uninstaller](doc:running-the-linux-uninstaller) . 

The installation will fail if you do not install all necessary packages.

To install the application, take these steps:

1. Go to the directory that contains the installer.
2. Change the permissions for the installation file to make it executable:

`$ chmod +x [installation_file_name]`

3. Start the installer:

`$ ./[installation_file_name] –c`

The installer displays information about the application.

4. Follow the instructions in the installer. If you want to enable FIPS mode, do not select the option to initialize the application after installation. FIPS mode must be enabled before the application runs for the first time.   
  
If you are installing just the Scan Engine, you may need to specify the Shared Secret to pair it with a Security Console. Global Administrators can generate a Shared Secret in the Administration section of the Security Console. Select **manage** next to _Engines_, click **Generate** next to _Shared Secret_, and copy and paste the Shared Secret into the Installation Wizard.
5. See [Getting Started](doc:getting-started-with-insightvm) for information on getting started using the application.