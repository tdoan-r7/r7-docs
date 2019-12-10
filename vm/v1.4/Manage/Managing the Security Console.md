---
title: "Managing the Security Console"
excerpt: ""
---
* [Viewing general configuration settings](doc:managing-the-security-console#section-viewing-general-configuration-settings)
* [Changing the Security Console Web server default settings](doc:managing-the-security-console#section-changing-the-security-console-web-server-default-settings)
* [Managing the HTTPS certificate](doc:managing-the-security-console#section-managing-the-https-certificate)
* [Setting the Subject Alternative Name field](doc:managing-the-security-console#section-setting-the-subject-alternative-name-field)
* [Changing default Scan Engine settings](doc:managing-the-security-console#section-changing-default-scan-engine-settings)
* [Running in maintenance mode](doc:managing-the-security-console#section-running-in-maintenance-mode)

Although the default Security Console settings should work for a broad range of network environments, you can change settings to meet specific scanning requirements.
[block:callout]
{
  "type": "info",
  "body": "Click **Administer** next to _Console_ on the _Administration_ page to launch the Security Console Configuration panel."
}
[/block]
##Viewing general configuration settings

On the _General_ page, you can view the version and serial numbers for the instance of the Security Console that you are using.

##Changing the Security Console Web server default settings

The Security Console runs its own Web server, which delivers the user interface.

To change the Security Console web server default settings:
1. Go to the _Administration_ page.
2. Click **Administer** settings for the Security Console, under _Global and Console Settings_.
3. Go to the _Web Server_ page.
4. Enter a new number for the access port.
5. Enter a new session time-out. This value is the allowed number of seconds of user inactivity after which the Security Console times out, requiring a new logon.
6. Enter new numbers for initial request and maximum request handler threads, if necessary.
It is recommended that you consult Technical Support first. In this context, threads refer to the number of simultaneous connections that the Security Console will allow. Typically a single browser session accounts for one thread. If simultaneous user demand is high, you can raise the thread counts to improve performance. The Security Console will increase the thread count dynamically if required, so manual increases may be unnecessary.
7. Enter a new number for failed logon threshold if desired. This is the number of failed logon attempts that the Security Console permits before locking out the would-be user.
8. Click **Save**.

##Managing the HTTPS certificate

The application provides a self-signed X.509 certificate, which is created during installation. It is recommended that you replace it with a certificate that is signed by a trusted certifying authority (CA).
[block:callout]
{
  "type": "info",
  "body": "The signed certificate must be based on an application-generated CSR. The application does not allow you to import an arbitrary key pair or certificate that you generated."
}
[/block]
To manage certificates and generate a new certificate signing request (CSR):
1. Go to the _Administration_ page.
2. Click **Administer** settings for the Security Console.
3. Go to the _Web Server_ page.
4. Click **Manage Certificate**.
The Security Console displays a box titled _Manage Certificate_.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/29624da-s_manage_certificate.jpg",
        "s_manage_certificate.jpg",
        978,
        782,
        "#e4ecee"
      ],
      "caption": "Manage Certificate"
    }
  ]
}
[/block]
5. Click **Create New Certificate**.
The Security Console displays a box for new certificate information.
6. Enter the information and click **Create**.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/c89fc26-s_manage_certificate_create.png",
        "s_manage_certificate_create.png",
        655,
        535,
        "#e8f1f0"
      ],
      "caption": "Manage Certificate–Create New Certificate"
    }
  ]
}
[/block]
A dialog box appears indicating that a new self-signed certificate was created.

7. Click **Create CSR now**.
You can click **Later** to come back to this step and continue the process at another time.
8. Copy the generated CSR and send it to your CA.
9. Click **Import Certificate** on the _Manage Certificate_ dialog after it is signed by your CA.
10. Paste it in the text box and click **Import**.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/d38005d-s_manage_certificate_import.jpg",
        "s_manage_certificate_import.jpg",
        983,
        473,
        "#e7edee"
      ],
      "caption": "Manage Certificate–Import certificate signing request"
    }
  ]
}
[/block]
11. Click **Save** to save the new Security Console information.
The new certificate name appears on the _Web Server_ page.

## Setting the Subject Alternative Name field
[block:callout]
{
  "type": "warning",
  "title": "IMPORTANT",
  "body": "Consoles using externally signed (CA/non-CA) **must** have a SAN field. If the certificate is self signed, it does not require a SAN field."
}
[/block]
This process can be completed with the following steps:

1. In your installation directory, check the **keystores** folder for a file called **nscweb.ks**:

```
<install-dir>/nsc/keystores/nscweb.ks
```

If the file does not exist, browse to the "Manage Certificate" window, located in the **Administration** tab **>** "Global and Console Settings" window **> Administer > Web Server** tab **> Manage Certificate** button. Select **Create New Certificate**.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/2687305-Screen_Shot_2017-11-20_at_3.04.36_PM.png",
        "Screen Shot 2017-11-20 at 3.04.36 PM.png",
        649,
        529,
        "#e5eff0"
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
        "https://files.readme.io/efd36dc-Manage_Certificate.png",
        "Manage_Certificate.png",
        639,
        524,
        "#e8f0f0"
      ]
    }
  ]
}
[/block]
2. Enter the SAN information and click **Create**.  Another dialogue box will appear.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/bb4cf37-Create_CSR_Now.png",
        "Create_CSR_Now.png",
        799,
        603,
        "#2a3741"
      ]
    }
  ]
}
[/block]
3. Click **Create CSR Now**.
[block:callout]
{
  "type": "warning",
  "title": "NOTE",
  "body": "In order to complete the next step successfully, make sure you have execute permission on `/opt/rapid7/Nexpose/_jvm1.8.0_102/bin/keytool`, and verify with your network administrator that assigning execute permissions for this binary is acceptable.\n\nThis can be done by running as administrator on Windows or issuing a `chmod +x` command on the Linux file from the command line."
}
[/block]
4. Select your operating system.

**To set the subject alternative name field in Linux operating systems, follow these steps:**

a. Open a command prompt as an administrator on the host machine.

```
cd [install_dir]/rapid7/nexpose/_jvm1.8.0_102/bin
```
b. Log in via SSH into Nexpose Server and run the following as root:

```
./keytool -certreq -alias nscweb -sigalg sha512WithRSA -keystore /opt/rapid7/nexpose/nsc/keystores/nscweb.ks -storepass 'r@p1d7k3y$t0r3' -ext san=dns:samplehostname.com,ip:127.0.0.1 -file filename.csr
```

The **console.csr** file can be sent to a CA to be signed.
[block:callout]
{
  "type": "info",
  "body": "This directory requires superuser elevation:\n\n`<install-dir>/_jvm1.8.0_102/bin/keytool -certreq \\`"
}
[/block]
**To set the subject alternative name field in Windows operating systems, follow these steps:**

a. Open a command prompt as an administrator on the host machine.

```
C:\Program Files\Rapid7\Nexpose\_jvm1.8.0_192\bin
```

b. Run as admin.

```
.\keytool.exe -certreq -alias nscweb -sigalg sha512WithRSA -keystore "c:\Program Files\rapid7\nexpose\nsc\keystores\nscweb.ks" -storepass "r@p1d7k3y$t0r3" -ext san=dns:samplehostname.com,ip:127.0.0.1 -file filename.csr
```

Once the **filename.csr** is generated, send it to the Certificate Authority (CA) to be signed, then load into Nexpose.
[block:callout]
{
  "type": "warning",
  "title": "NOTE",
  "body": "The CA should take the SAN data in your CSR and add it to the certificate when signed. This is not automatically added through the CSR, so it is recommended to verify this ahead of time in order to make sure the CA added the SAN data during the signing process."
}
[/block]
5. Check the signed certificate returned by your CA to make sure the SAN is present:

```
openssl x509 -text -noout -in SignedCert.crt
```
The details should contain something similar to the following:
```
X509v3 extensions:
X509v3 Issuer Alternative Name:
DNS:samplehostname.com, IP Address:127.0.0.1
```
6. Import the signed certificate (a PEM file) into the InsightVM UI:
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/1278603-certificatemanager_import.png",
        "certificatemanager_import.png",
        648,
        532,
        "#e5efef"
      ]
    }
  ]
}
[/block]
##Changing default Scan Engine settings

The Security Console communicates with distributed Scan Engines over a network to initiate scans and retrieve scan results. If you want to obtain scan status information more quickly or reduce bandwidth or resource consumption required for Security Console-to-Scan-Engine communication, you can tune various settings on the Scan Engines page of the Security Console Configuration panel. 

###Configuring Security Console connections with distributed Scan Engines

The Security Console establishes connections with distributed Scan Engines to launch scans and retrieve scan results. This communication can be disrupted by low network bandwidth, high latency, or situations in which Scan Engines are performing high numbers of simultaneous scans. If any of these conditions exist in your environment, you may want to consider increasing connection settings on the _Scan Engines_ configuration page:
[block:callout]
{
  "type": "warning",
  "body": "It is recommended that you consult with Technical Support before tuning these settings."
}
[/block]
* The **Connection timeout** setting controls how long the Security Console waits for the creation of a connection with a distributed Scan Engine.
* The **Response timeout** setting controls how long the Security Console waits for a response from an Scan Engine that it has contacted.

To configure these settings, take the following steps:
1. Go to the _Scan Engines_ page in the _Security Console Configuration_ panel.
2. Click the _Administration_ tab.
3. On the _Administration_ page, click **manage** for the Security Console.
4. Click **Scan Engines** in the _Security Console Configuration_ panel.
5. Adjust the _Connections_ settings.
6. Edit the value in the Connection timeout field to change the number of milliseconds that elapse before a connection timeout occurs.
7. Edit the value in the Response timeout field to change the number of milliseconds that elapse before the Security Console no longer waits for a response from an Scan Engine.
8. Click **Save** in the top bar of the panel to save the changes.
9. Restart the Security Console so that the configuration changes can take effect.
[block:callout]
{
  "type": "info",
  "body": "Because millisecond values can be difficult to read, a time value that is easier to read appears to the right of each value field. As you change either timeout value, note how the equivalent value changes."
}
[/block]
###Allocating threads for monitoring scans

The Security Console allocates a thread pool for retrieving scan status information. You can adjust the number of threads, which corresponds to the number of scan status messages that the Security Console can retrieve simultaneously. For example, if you increase the number of distributed Scan Engines and the number of scans running simultaneously, you can increase the threads in the pool so that the Security Console can retrieve more status messages at the same time.
[block:callout]
{
  "type": "warning",
  "body": "It is recommended that you consult with Technical Support before tuning these settings."
}
[/block]
Keep in mind that retrieval time is subject to network conditions such as bandwidth and latency. Whenever the number of active threads in use exceeds the overall number of threads in the pool, the Security Console removes unused scan status threads after specific time interval. If you notice an overall decrease in the frequency of scan status messages, you may want to consider increasing the timeout value.

To adjust pool settings for scan status threads, take the following steps:

1. Go to the _Scan Engines_ page in the _Security Console Configuration_ panel.
2. Click the **Administration** tab.
3. Click **manage** for the Security Console on the _Administration_ page.
4. Click **Scan Engines** in the _Security Console Configuration_ panel.
5. Adjust the _Scan Status_ settings.
6. Edit the value in the **Thread idle timeout** field to change the number of milliseconds that elapse before the Security Console removes unused scan threads.
7. Edit the value in the **Thread pool size** field to change the number of threads in the pool for monitoring scan status.
8. Click **Save** in the top bar of the panel to save the changes.
9. Restart the Security Console so that the configuration changes can take effect.
[block:callout]
{
  "type": "info",
  "body": "Because millisecond values can be difficult to read, a time value that is easier to read appears to the right of each value field. As you change either timeout value, note how the equivalent value changes."
}
[/block]
###Retrieving incremental scan results from distributed Scan Engines

The Security Console communicates with Scan Engines over a network to retrieve scan results. By default, the Security Console retrieves scan results from distributed Scan Engines incrementally, displaying results in the Web interface as it integrates the data, rather than retrieving the full set of results after each scan completes. This allows you to view scan results as they become available while a scan is in progress.

Incremental retrieval modulates bandwidth usage throughout the scan. It also makes it unnecessary for the Security Console to retrieve all the data at the end of the scan, which could cause a significant, temporary increase in bandwidth usage, especially with large sets of data.

The _Scan Engines_ page of the _Security Console Configuration_ panel displays a check box for incremental retrieval of scan results. It is selected by default. Do not disable this option unless directed to do so by Technical Support.


##Running in maintenance mode
[block:callout]
{
  "type": "info",
  "body": "Only global administrators are permitted to run the application in maintenance mode."
}
[/block]
Maintenance mode is a startup mode in which the application performs general maintenance tasks and recovers from critical failures of one or more of its subsystems. During maintenance mode, you cannot run scans or reports. Available functions include logging, the database, and the Security Console Web interface.
[block:callout]
{
  "type": "info",
  "body": "The application automatically runs in maintenance mode when a critical internal error occurs."
}
[/block]
When the application is running in maintenance mode, you see the page _/admin/maintenance/index.html_ upon logging on. This page shows all available maintenance tasks and indicates the current status of the task that is being performed. You cannot select a new task until the current task is completed. Afterward, you can switch tasks or click **Restart** to return to normal operating mode.

To work in Maintenance mode:
1. Click the _Administration_ tab.
2. On the _Administration_ page, click **Maintenance**.

The Security Console displays the _Maintenance Mode_ page.