---
title: "Using a Proxy Server"
excerpt: ""
---
If the Security Console does not have direct Internet access, you can configure a proxy server to download updates to keep the application updated. You can also use a proxy server to send logs and exposure analytics to Technical Support.

It is important that your proxy settings are correct. Inaccurate proxy settings may cause your license activation to fail. In most cases, Technical Support will tell you if you need to change these settings.


To configure proxy settings
1. Click the *Administration* icon. The **Administration** page opens.
2. In the **Global and Console Settings** area, for **Console**, click **Administer**. The **Security Console Configuration** page opens.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/d45344c-proxy_tab.JPG",
        "proxy_tab.JPG",
        1671,
        477,
        "#2e3641"
      ]
    }
  ]
}
[/block]
3. Click **Proxy Settings** and complete the appropriate fields. 
  * In the **Name or address** field, if you want to use a proxy server, enter its name or IP address. If you are not using a proxy, this field defaults to 'updates.rapid7.com'. If you change this setting to another server address, your activation may fail. Contact Technical Support if you require a different server address and you receive errors during activation.
  * In the **Port** field, if you want to use a proxy server, and it uses a different port number for communication with the Security Console, enter that port number. The **Port** field is set to 80 by default because the Security Console contacts the update server on that port.
  * In the **Response timeout** field, enter the interval that the Security Console will wait to receive a requested package before initiating a timeout of the transfer. The default setting is 30,000 ms or 30 seconds. The minimum setting is 1,000 ms, and the maximum is 2,147,483,647 ms. A proxy server may not relay an entire requested package to the Security Console until it downloads and analyzes the package in its entirety. Larger packages require more time. To determine how long to allow for a response interval, see [Determining a response timeout interval for the proxy].
  * In the **Domain**, **User ID**, and **Password** fields, if you are using a proxy server, enter the appropriate information. If you are not using a proxy server, you can leave these fields blank.
  * In the **Use Proxy Server for Send Logs and Rapid7 Insight Platform communication** area:
  * Check the **Send support logs** box if you want to onboard your Security Console to our cloud platform and use the proxy server to handle communication between the console and the R7 platform. 
  * Check the **Exposure Analytics** box if you want to use the proxy server to handle 
  communication between the Security Console and the Rapid7Insight Platform.
4.  Click **Save**.


## Determining a response timeout interval for the proxy
To determine a timeout interval for the proxy server, find out how much time the Security Console requires to download a certain number of megabytes. You can, for example, locate the downloaded .JAR archive for a recent update and learn from the log file how long it took for the Security Console to download a file of that size.

1. Open the nsc.log file, located in the `[installation_directory]/nsc` directory. Look for a sequence of lines that reference the download of an update, such as the following:
~~~~
2013-06-05T00:04:10 [INFO] [Thread: Security Console] Downloading update ID
1602503.
~~~~
~~~~
2013-06-05T00:04:12 [INFO] [Thread: Security Console] Response via 1.1
proxy.example.com.
~~~~
~~~~
2013-06-05T00:05:05 [INFO] [Thread: Security Console] Response via 1.1
proxy.example.com.
~~~~
~~~~
2013-06-05T00:05:07 [INFO] [Thread: Security Console] Acknowledging receipt
of update ID 1602503.
~~~~
Note the time elapsed between the first entry `Downloading update ID...` and the last entry `Acknowledging receipt of update...`.
2. Go to the directory on the Security Console host where the .JAR archives for updates are stored: `[installation_directory]/updates/packages]`. 
3. Locate the file with the update ID referenced in the log entries and note its size. Using the time required for the download and the size of the file, you can estimate the timeout interval required for downloading future updates. It is helpful to use a larger update file for the estimate.

**Tip:** In most cases, a timeout interval of 5 minutes (300,000 ms) is generally sufficient.