---
title: "Integrating NSX network virtualizations with scans"
excerpt: ""
---
Virtual environments are extremely fluid, which makes it difficult to manage them from a security perspective. Assets go online and offline continuously. Administrators re-purpose them with different operating systems or applications, as business needs change. Keeping track of virtual assets is a challenge, and enforcing security policies on them is an even greater challenge.

The vAsset Scan feature addresses this challenge by integrating InsightVM scanning with the VMware NSX network virtualization platform. The integration gives a Scan Engine direct access to an NSX network of virtual assets by registering the Scan Engine as a security service within that network. This approach provides several benefits:

* The integration automatically creates a InsightVM site, eliminating manual site configuration.
* The integration eliminates the need for scan credentials. As an authorized security service in the NSX network, the Scan Engine does not require additional authentication to collect extensive data from assets.
* Security management controls in NSX use scan results to automatically apply security policies to assets, saving time for IT or security teams. For example, if a scan flags a vulnerability that violates a particular policy, NSX can quarantine the affected asset until appropriate remediation steps are performed.
[block:callout]
{
  "type": "info",
  "body": "The vAsset Scan feature is a different feature and license option from vAsset Discovery, which is related to the creation of dynamic sites that can later be scanned. For more information about that feature, see [Managing dynamic discovery of assets](doc:managing-dynamic-discovery-of-assets)."
}
[/block]
##Activities in an NSX-integrated site

When you create a site through this NSX integration process, you cannot do the following actions in the Site Configuration:

* Edit assets, which are dynamically added as part of the integration process.
* Change the Scan Engine, which is automatically configured as part of the integration process.
* Change the assigned scan template, which is Full Audit.
* Add scan credentials, which are unnecessary because the integration provides InsightVM with the depth of access to target assets that credentials would otherwise provide.

##Requirements for the vAsset Scan feature

To use the vAsset Scan feature, you need the following components:
* a InsightVM installation with the vAsset Scan feature enabled in the license
* VMware ESXi 5.5 hosts
* VMware vCenter Server 5.5
* VMware NSX 6.0 or 6.1
* Guest Introspection deployed
* VMware Tools installed with VMCI drivers

##Deployment steps for the vAsset Scan feature

Deploying the vScan feature involves the following sequence of steps:

1. [Deploy the VMware Guest Introspection service](doc:integrating-nsx-network-virtualizations-with-scans#section-deploy-the-vmware-guest-introspection-service) 
2. [Integrating NSX network virtualization with scans](doc:integrating-nsx-network-virtualizations-with-scans) 
3. [Download the Nexpose scan engine OVF](doc:integrating-nsx-network-virtualizations-with-scans#section-download-the-nexpose-scan-engine-ovf) 
4. [Register InsightVM with NSX Manager](doc:integrating-nsx-network-virtualizations-with-scans#section-register-insightvm-with-nsx-manager) 
5. [Deploy the Scan Engine from NSX](doc:integrating-nsx-network-virtualizations-with-scans#section-deploy-the-scan-engine-from-nsx) 
6. [Create a security group](doc:integrating-nsx-network-virtualizations-with-scans#section-create-a-security-group) 
7. [Create a security policy](doc:integrating-nsx-network-virtualizations-with-scans#section-create-a-security-policy) 
8. [Power on a Windows Virtual Machine](doc:integrating-nsx-network-virtualizations-with-scans#section-power-on-a-windows-virtual-machine) 
9. [Scan the security group](doc:integrating-nsx-network-virtualizations-with-scans#section-scan-the-security-group) 

##Deploy the VMware Guest Introspection service

1. Log onto the VMware vSphere Web Client.
2. From the _Home_ menu, select **Network & Security**.
3. From the _Network & Security_ menu, select **Installation**.
4. In the _Installation_ pane, select the **Service Deployments** tab. Click the green plus sign ![Alt](https://files.readme.io/3030481-i_nsx_plus.jpg) and then select the check box for **Guest Introspection**. Then click the **Next** button to configure the deployment.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/4637a40-Deploy_VMware_Guest_Introspection_service.png",
        "Deploy_VMware_Guest_Introspection_service.png",
        2520,
        1348,
        "#979c9f"
      ],
      "caption": "The vSphere Web Client-Select Services & Schedule pane"
    }
  ]
}
[/block]
1. In the _Select clusters_ pane, select a datacenter and cluster to deploy the Guest Introspection on. Then click **Next**.
2. In the _Select storage_ pane, select a data store for the VMware Endpoint. Then click **Next**.
3. In the _Configure management network_ pane, select a network and IP assignment for the VMware Endpoint. Then click **Next**.
4. In the _Ready to complete_ pane, click **Finish**.

##Download the Nexpose scan engine OVF

Click the **Update** link on the _Administration page_ under _NSX Manager_.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/69a2769-Update_NSX_OVF.png",
        "Update_NSX_OVF.png",
        1136,
        460,
        "#2a313e"
      ]
    }
  ]
}
[/block]

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/b239d08-Download_OVF.png",
        "Download_OVF.png",
        2252,
        410,
        "#ecf3f3"
      ]
    }
  ]
}
[/block]
##Windows

If you are in a Windows environment, take the following steps:
1. Verify that InsightVM is licensed for the Virtual Scanning feature:
  a. Click the **Administration** tab in the InsightVM Security Console.
  b. On the _Administration_ page, under Global and Console Settings, select the Administer link for Console.
  c. In the Security Console Configuration panel, select Licensing.
  d. On the Licensing page, look at the list of license-supported features and that Virtual Scanning is marked with a green check mark.
2. Verify the NexposeVASE.ovf file is accessible from the Security Console by typing the following URL in your browser: 
https<i></i>://[Security_Console_IP_address]:3780/nse/ovf/NexposeVASE.ovf.

##Register InsightVM with NSX Manager

InsightVM must be registered with VMware NSX before it can be deployed into the virtual environment.
1. Log onto the InsightVM Security Console.
Example: ```https://[IP_address_of_Virtual_Appliance]:3780```
The default user name is _nxadmin_, and the default password is _nxpassword_.
2. As a security best practice, change the default credentials immediately after logging on. To do so, click the **Administration** icon. On the _Administration_ page, click the **manage** link next to _Users_. On the _Users_ page, edit the default account with new, unique credentials, and click **Save**.
3. On the _Administration_ page, click the **Create** link next to _NSX Manager_ to create a connection between InsightVM and NSX Manager.
4. On the _General_ page of the _NSX Connection Manager_ panel, enter a connection name, the fully qualified domain name for the NSX Manager server, and a port number. The default port for NSX Manager is 443.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/29caf0b-s_nsx_connection_general.jpg",
        "s_nsx_connection_general.jpg",
        2091,
        391,
        "#182635"
      ],
      "caption": "The InsightVM NSX Connection Manager panel-General page"
    }
  ]
}
[/block]
5. On the _Credentials_ page of the _NSX Connection Manager_ panel, enter credentials for Nexpose to use when connecting with NSX Manager.
6. Select the Callback IP address from the drop down menu. If the Nexpose console has multiple IP addresses, select the IP that can be reached by the NSX Manager.
[block:callout]
{
  "type": "warning",
  "body": "These credentials must be created on NSX in advance, and the user must have the NSX Enterprise Administrator role."
}
[/block]

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/663e0e5-s_nsx_connection_credentials.jpg",
        "s_nsx_connection_credentials.jpg",
        2066,
        355,
        "#172535"
      ],
      "caption": "The InsightVM NSX Connection Manager panel-Credentials page"
    }
  ]
}
[/block]
## Deploy the Scan Engine from NSX

This deployment authorizes the Scan Engine to run as a security service in NSX. It also automatically creates a site in InsightVM.

1. Log onto the VMware vSphere Web Client.
2. From the _Home_ menu, select **Network & Security**.
3. From the _Network & Security_ menu, select **Installation**.
4. From the _Installation_ menu, select **Service Deployments**.
5. In the _Installation_ pane, click the green plus sign ![Alt](https://files.readme.io/3030481-i_nsx_plus.jpg) and then select the check box for **Rapid7 Nexpose Scan Engine**. Then click the **Next** button to configure the deployment.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/0d26cb4-Deploy_VMware_Guest_Introspection_service.png",
        "Deploy_VMware_Guest_Introspection_service.png",
        2520,
        1348,
        "#979c9f"
      ],
      "caption": "Configuring Scan Engine settings in NSX"
    }
  ]
}
[/block]
6. Select the cluster in which to deploy the Rapid7 Nexpose Scan Engine.
[block:callout]
{
  "type": "info",
  "body": "One Scan Engine will be deployed to each host in the selected cluster."
}
[/block]
7. Configure the deployment according to your environment settings. Then click **Finish**.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/19265f5-NSX_Configuring_Scan_Engine.png",
        "NSX_Configuring_Scan_Engine.png",
        1920,
        1122,
        "#e8eaef"
      ],
      "caption": "Configuring Scan Engine settings in NSX"
    }
  ]
}
[/block]

[block:callout]
{
  "type": "info",
  "body": "The Service Status will display Warning while the Scan Engine is initializing."
}
[/block]
##Create a security group

This procedure involves creating a group of virtual machines for InsightVM to scan. You will apply a security policy to this group in the following procedure.

1. From the _Home_ menu in vSphere Web Client, select **Network & Security**.
2. From the _Network & Security_ menu in vSphere Web Client, select **Service Composer**.
3. In the _Service Composer_ pane, click **New Security Group**.
4. Create a security group. Use either dynamic criteria selection or enter individual virtual machine names.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/0af8a6a-s_nsx_create_security_group.jpg",
        "s_nsx_create_security_group.jpg",
        965,
        567,
        "#e7e4ea"
      ],
      "caption": "Creating a security group in NSX"
    }
  ]
}
[/block]
##Create a security policy

This new policy applies the Scan Engine as a Guest Introspection service for the security group.

1. After you create a security group click, select it and click **Apply Policy**. Then, click the **New Security Policy...** link.
2. Create a new security policy for the _Rapid7 Nexpose Scan Engine_ Guest Introspection service, selecting the following settings:
  * **Action:** _Apply_
  * **Service Type:** Grayed out / not modifiable (may contain anti-virus)
  * **Service Name:** __Rapid7 Nexpose Scan Engine_
  * **Service Profile:** _Rapid7 Nexpose Scan Engine_default (Vulnerability Management)_
  * **Service Configuration:** _default_
  * **State:** _Enabled_
  * **Enforced:** _Yes_
3. Click **OK**.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/5ecea6c-Create_Scan_Engine_Security_Policy.png",
        "Create_Scan_Engine_Security_Policy.png",
        2520,
        1350,
        "#828484"
      ],
      "caption": "Creating a security policy in NSX"
    }
  ]
}
[/block]
##Power on a Windows Virtual Machine

This machine will serve as a scan target to verify that the integration is operating correctly.
1. Power on a Windows Virtual Machine that has VMware Tools version 9.4.0 or later installed.

## Scan the security group

The rules of the policy will be enforced within the security group based on scan results.
1. Log onto the InsightVM Security Console.
2. In the _Site Listing_ table, find the site that was auto-created when you deployed the Scan Engine from NSX.
3. Click the **Scan*8 icon to start the scan.

For information about monitoring the scan see [Running a manual scan](doc:running-a-manual-scan).