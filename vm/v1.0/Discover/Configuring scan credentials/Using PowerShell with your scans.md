---
title: "Using PowerShell with your scans"
excerpt: ""
---
Windows PowerShell is a command-line shell and scripting language that is designed for system administration and automation. As of PowerShell 2.0, you can use Windows Remote Management to run commands on one or more remote computers. By using PowerShell and Windows Remote Management with your scans, you can scan as though logged on locally to each machine. PowerShell support is essential to some policy checks in SCAP 1.2, and more efficiently returns data for some other checks.

In order to use Windows Remote Management with PowerShell, you must have it enabled on all the machines you will scan. If you have a large number of Windows assets to scan, it may be more efficient to enable it through group policy on your Windows domain.

Although it's possible to use Windows Remote Management with PowerShell via HTTP, it's far more secure to use the HTTPS service. The WinRM service will need to be configured correctly in order to leverage the HTTPS protocol. This can be achieved by reading the following article:

https://support.microsoft.com/en-us/help/2019527/how-to-configure-winrm-for-https

For scans to use Windows Remote Management with PowerShell, port 5985 (HTTP) or 5986 (HTTPS) must be available to the scan template. The scan templates for DISA, CIS, and USGCB policies have this port included by default; for others you will need to add it manually.

To add the port to the scan template:

1. Go to the _Administration_ page and select **Manage** in **Templates**.
Select the scan template you are using.
In the _Service Discovery_ tab, add **5985 or 5986** to the _Additional ports_ in the _TCP Scanning_ section.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/86c06ed-s_nx_port_5985.PNG",
        "s_nx_port_5985.PNG",
        701,
        385,
        "#2c333f"
      ],
      "caption": "Adding port 5985"
    }
  ]
}
[/block]
You also need to specify the appropriate service and credentials.

To specify the service and credentials, take the following steps:

If you want to add credentials while configuring a new site, click the **Create site** button on the _Home_ page.

If you want to add credentials for an existing site, click that site's **Edit** icon in the _Sites_ table on the _Home_ page.

1. Select **Authentication**.
2. Click **Add Credentials**.
3. In the _Add Credentials_ form, enter a name and description for a new set of credentials if necessary.
4. Click **Account** under _Add Credentials_.
5. Select the **Microsoft Windows/Samba (SMB/CIFS)** service.
6. Enter the domain, user name, and password for the service.
7. When you have finished configuring the credentials, click **Create** if it is a new set or **Save** if it is a previously created set.

For additional optional steps, see the following topics:

* [Testing the credentials](doc:configuring-site-specific-scan-credentials#section-testing-the-credentials) 
* [Limiting the credentials to a single asset and port](doc:configuring-site-specific-scan-credentials#section-limiting-the-credentials-to-a-single-asset-and-port) 

The application will automatically use PowerShell if the correct port is enabled, and if the correct Microsoft Windows/Samba (SMB/CIFS) credentials are specified.

If you have PowerShell enabled, but don’t want to use it for scanning, you may need to define a custom port list that does not include port 5985.

To disable access to the port:

1. Go to the _Administration_ page and select **Manage** in **Templates**.
2. Select the scan template you are using.
3. In the _Service Discovery_ tab, in _TCP Scanning_, for _Ports to Scan_, select **Custom (only use “Additional ports”)**.
4. In **Additional ports**, specify a list of ports that does not include port 5985.