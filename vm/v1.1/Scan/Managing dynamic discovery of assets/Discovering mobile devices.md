---
title: "Discovering mobile devices"
excerpt: ""
---
An increasing number of users are connecting their personal mobile devices to corporate networks. These devices increase and expand attack surfaces in your environment with vulnerabilities that allow attackers to bypass security restrictions and perform unauthorized actions or execute arbitrary code.

You can discover devices with Apple iOS or Google Android operating systems that are connected to Microsoft Exchange over ActiveSync. All versions of iOS and Android are supported.

The Security Console discovers mobile devices that are managed with Microsoft Exchange ActiveSync protocol. The Dynamic Discovery feature currently supports Exchange versions 2010 and 2013 and Office 365.

You can connect to the mobile data via one of three Microsoft Windows server configurations:

* a connection to an Exchange server via LDAP/Active Directory (AD)
* a Windows Remote Management (WinRM) gateway connecting to an on-premise Exchange server via the PowerShell framework
* a WinRM gateway connecting to a Cloud-based Office 365 server

The advantage of using one of the WinRM configurations is that asset data discovered through one of these methods includes the most recent time that each mobile device was synchronized with the Exchange server. This can be useful if you do not want your reports to include data from old devices that are no longer in use on the network. You can create a dynamic asset group for mobile devices with old devices filtered out. See [Performing filtered asset searches](doc:performing-filtered-asset-searches).

## Preparing for Dynamic Discovery of mobile devices

Depending on which Windows server configuration you are using, you will need to take some preliminary steps to prepare your target environment for discovery.

### LDAP/AD

For the discovery connection, the Security Console requires credentials for a user with read permission on the mobile device objects in Active Directory. The user must be a member of the Organization Management Security Group in Microsoft Exchange or a user that has been granted read access to the mobile device objects.This allows the Security Console to perform LDAP queries.

Take the following steps on the AD server to grant account Read-only permissions to the AD Organizational Unit(s) (OU) that contain users with ActiveSync (Mobile) devices:
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/be3a964-s_ad_mobile_select_OU.jpg",
        "s_ad_mobile_select_OU.jpg",
        1848,
        1164,
        "#ececec"
      ],
      "caption": "Selecting the Users OU in ADSI Edit"
    }
  ]
}
[/block]
1. Start the Active Directory Service Interfaces Editor (ADSI Edit) and connect to the AD environment.
2. Select the OU that contains users with ActiveSync (Mobile) devices. In this example, the Users OU contains users with ActiveSync devices.
3. Right-click the Users OU and select **Properties**.
4. Select the **Security** tab.
5. Click the **Add** button and add the user account that the Security Console will use for connecting to the AD server.
6. Select the user and click **Advanced**.
7. Select the user and click **Edit** .
8. From the **Applies to** drop-down list, select _Descendant msExchActiveSyncDevice objects_.

Repeat the previous steps for any additional OUs containing ActiveSync (Mobile) devices.

## WinRM

The setup requirements and steps in the target environment are practically identical for PowerShell and Office 365 configurations:

### Servers and credentials

* WinRM gateway server with a user account that has WinRM permissions
* Exchange server with an administrator account or a user account that has View-Only Organizational Management or higher role
[block:callout]
{
  "type": "info",
  "body": "The WinRM gateway may also be the Exchange server or the Security Console, if the Security Console is running on Windows."
}
[/block]
## Setting up the WinRM gateway
[block:callout]
{
  "type": "warning",
  "body": "Consult a Windows server administrator if you are unfamiliar with these procedures."
}
[/block]
The WinRM gateway must have an available https WinRM listener at port 5986. Typical steps to enable this include the following:

1. Verify that the server has a Server Authentication certificate installed that is not expired or self-signed. For more information, see [https://technet.microsoft.com/en-us/library/cc731183.aspx](https://technet.microsoft.com/en-us/library/cc731183.aspx) .
2. Enable the WinRM https listener:
```C:\> winrm quickconfig -transport:https```
3. Increase the WinRM memory limit with a PowerShell command (Minimum setting is 1024 MB; but 2048 MB is recommended.):
```[PS] C:\> set-item wsman:localhost\Shell\MaxMemoryPerShellMB 2048```
4. Open port 5986 on the Windows firewall:
```C:\> netsh advfirewall firewall add rule name=
"Windows Remote Management (HTTPS-In)" dir=in action=allow protocol=TCP localport=5986```

The following instructions are available for enabling WinRM for an account other than administrator: see the Negotiate Authentication section here: (https://msdn.microsoft.com/en-us/library/aa384295(v=vs.85).aspx.

### Network connectivity

* The Security Console must be able to connect to the WinRM gateway via port 5986 over https or WS-Management protocol.
* The WinRM gateway must be able to connect to the Exchange server over port 80 and perform necessary kerberos authentication.

## Troubleshooting WinRM connection issues

If WinRM fails using a domain controller as WinRM gateway, see the blog at [http://www.projectleadership.net/blog/](http://www.projectleadership.net/blog/) for assistance. Typically, running ```setspn -L [server_name]``` returns two WinRM configurations; but, in this case, none are displayed.

If the PowerShell script fails with error _Process is terminated due to StackOverflowException._, the WinRM memory limit is insufficient. Increase the setting by running the PowerShell command:

```[PS] C:\> set-item wsman:localhost\Shell\MaxMemoryPerShellMB 2048```

##Troubleshooting Exchange connectivity

To verify and troubleshoot Exchange connectivty, open the PowerShell Windows WinRM gateway server with the WinRM credentials. Then run the following Powershell command with your Exchange user credentials and the Exchange server fully qualified domain name for your organization:
```
$cred = Get-Credential
$s = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri http://exchangeserver.domain.com/ -credential $cred
Import-PSSession $s
Get-ActiveSyncDevice
```
This will display a window to enter the credentials. If the _New-PSSession_ fails this indicates that the remote PowerShell connection to the Exchange server failed.

If the _Get-ActiveSyncDevices_ command returns _not devices_, this may indicate that your Exchange account has insufficient permission to perform the query.

## Troubleshooting connections with the Office 365 configuration

The Office 365 configuration works exactly like the PowerShell configuration, except that it communicates with Microsoft's Exchange server in the Cloud and connects to the gateway somewhat differently via PowerShell.

Use the following script to troubleshoot Office365 exchange connectivity:
```
$cred = Get-Credential
$s = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://outlook.office365.com/powershell -credential $cred -Authentication Basic -AllowRedirection
Import-PSSession $s
Get-ActiveSyncDevice
```
After preparing your network for discovery, see [Creating and managing Dynamic Discovery connections](doc:creating-and-managing-dynamic-discovery-connections) .

## General best practices for managing mobile discovery

To optimize discovery results on a continuing basis, observe some best practices for managing your environment:

####Test your environment

Test your ActiveSync environment to verify all components are working and communicating properly. This will help improve your coverage.

####Create device access rules

Creating rules for ActiveSync devices in your network further expands your control. You can, for example, create rules for approving quarantined devices.

####Manage and increase device partnerships

Individual users in your organization may use multiple devices, each with its own partnership or set of ActiveSync attributes created during the initial synchronization. Additionally, users routinely upgrade from one version of a device to another, which also increases the potential number of partnerships to support. Managing these partnerships is important for tracking ActiveSync devices in your environment. It involves the removal of old devices from the Exchange server, which can help create a more accurate mobile risk assessment.