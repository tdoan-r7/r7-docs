---
title: "Installing in Windows environments"
excerpt: ""
---
This section describes how to install InsightVM on a Windows host. It also describes options that are available to you during the installation.

### Before you begin

Confirm the following items:

- You are logged onto Windows as an administrator.
- Your system meets the minimum installation requirements. 
- You have all of the items you need to complete the installation. See [Installing the Application](doc:installing-the-application#section-making-sure-you-have-necessary-items)  for details. 
- You have uninstalled any previously installed copies of the application. See [Running the Windows uninstaller](doc:running-the-windows-uninstaller) for details. 

## Running the Windows installer
To install the application in Windows, take the following steps:

1. Double-click the **installer icon**. 

The installer displays a message that it is preparing the wizard to guide you through the installation. Then the _Welcome_ page of the wizard is displayed.

Command-line windows open once you begin the installation. Although you do not need to interact with them, do not close them.

The installation will stop if you close the command line interface windows.

Click **Next**. The _Type and destination_ page is displayed.

1. Follow the instructions in the installer. If you want to enable FIPS mode, do not select the option to initialize the application after installation. FIPS mode must be enabled before the application runs for the first time.   
  
If you are installing just the Scan Engine, you may need to specify the Shared Secret to pair it with a Security Console. Global Administrators can generate a Shared Secret in the Administration section of the Security Console. Select **manage** next to _Engines_, click **Generate** next to _Shared Secret_, and copy and paste the Shared Secret into the Installation Wizard.
2. See [Getting Started](doc:getting-started-with-insightvm) for information on getting started using the application.