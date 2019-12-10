---
title: "Discovering Virtual Machines Managed by VMware vCenter or ESX/ESXi"
excerpt: ""
---
An increasing number of high-severity vulnerabilities affect virtual targets and devices that support them, such as the following:

* management consoles
* management servers
* administrative virtual machines
* guest virtual machines
* hypervisors

Merely keeping track of virtual assets and their various states and classifications is a challenge in itself. To manage their security effectively you need to keep track of important details: For example, which virtual machines have Windows operating systems? Which ones belong to a particular resource pool? Which ones are currently running? Having this information available keeps you in synch with the continual changes in your virtual asset environment, which also helps you to manage scanning resources more efficiently. If you know what scan targets you have at any given time, you know what and how to scan.

In response to these challenges the application supports dynamic discovery of virtual assets managed by VMware vCenter or ESX/ESXi.

Once you initiate Dynamic Discovery it continues automatically as long as the discovery connection is active.

## Preparing the target VMware environment for Dynamic Discovery

To perform dynamic discovery in VMware environments, the Security Console can connect to either a vCenter server or directly to standalone ESX(i) hosts.

To determine if the application supports a connection to an ESX(i) host that is managed by vCenter, consult VMware’s interoperability matrix at http://partnerweb.vmware.com/comp_guide2/sim/interop_matrix.php.

The application supports direct connections to the following ESX(i) versions:

* ESX 4.1
* ESX 4.1, Update 1
* ESXi 4.1
* ESXi 4.1, Update 1
* ESXi 5.0
* ESXi 5.5
* ESXi 6.0

You must configure your VMware vSphere deployment to communicate through HTTPS. To perform Dynamic Discovery, the Security Console initiates connections to the vSphere application program interface (API) via HTTPS.

If the Security Console and your target vCenter or virtual asset host are in different subnetworks that are separated by a device such as a firewall, you will need to make arrangements with your network administrator to enable communication, so that the application can perform Dynamic Discovery.

Make sure that port 443 is open on the vCenter or virtual machine host because the application needs to contact the target in order to initiate the connection.

When creating a discovery connection, you will need to specify account credentials so that the application can connect to vCenter or the ESX/ESXi host. Make sure that the account has permissions at the root server level to ensure all target virtual assets are discoverable. If you assign permissions on a folder in the target environment, you will not see the contained assets unless permissions are also defined on the parent resource pool. As a best practice, it is recommended that the account have read-only access.

Make sure that virtual machines in the target environment have VMware Tools installed on them. Assets can be discovered and will appear in discovery results if they do not have VMware Tools installed. However, with VMware Tools, these target assets can be included in dynamic sites. This has significant advantages for scanning. See [Configuring a site using a Dynamic Discovery connection](doc:configuring-a-site-using-a-dynamic-discovery-connection) .