---
title: "Troubleshooting your activation"
excerpt: ""
---
Your license key is your access to all the features you need to start using the application. Before you can being using the application you must activate your license using the license key you received. Your license must be active so that you can perform operations like running scans and creating reports. If you received an error message when you tried to activate your license you can try the troubleshooting techniques identified below before contacting Technical Support.

License keys are good for one use; if you are performing the installation for a second time or if you receive errors during product activation and these techniques have not worked for you, contact Technical Support.

Try the following techniques to troubleshoot your activation:

####Did I enter the license key correctly?
* Verify that you entered the license key correctly.

####Is there an issue with my browser?
* Confirm the browser you are using is supported. See [Using the Web interface](doc:using-the-web-interface) for a list of supported browsers.
* Clear the browser cache.

####Are my proxy settings correct?

* If you are using a proxy server, verify that your proxy settings are correct because inaccurate settings can cause your license activation to fail.
   * Go to the _Administration_ page and, in the **Global and Console Settings** area, for Console, click **Administer**. When the **Security Console Configuration** page opens, click **Proxy Settings**.  Ensure that the address, port, domain, User ID, and password are entered correctly.
   * If you are not using a proxy, ensure the **Name or address field** is specified as _updates.rapid7.com_. Changing this setting to another server address may cause your activation to fail. Contact Technical Support if you require a different server address and you receive errors during activation.

####Are there issues with my network or operating system?
* By running diagnostics, you can find operating system and network issues that could be preventing license activation.
   * Go to the _Administration_ page and click **Diagnose** and _troubleshoot problems with the Security Console_.
   * Select the OS Diagnostics and Network Diagnostics checkboxes.
   * Click **Perform diagnostics** to see the current status of your installation. The results column will provide valuable information such as, if DNS name resolution is successful, if firewalls are enabled, and if the Gateway ping returns a ‘DEAD’ response.
* Confirm that all traffic is allowed out over port 80 to updates.rapid7.com.
   * If you are using Linux, open a terminal and enter ```telnet updates.rapid7.com 80```. You will see ```Connected``` if traffic is allowed.
   * If you are using Windows, open a browser and enter http://updates.rapid7.com. You should see a blank page.
   * White-list the IP address of the application server on your firewall so that it can send traffic outbound to http://updates.rapid7.com.
   * Make the same rule changes on your proxy server.
   * If you see an error message after adding the IP address to a white-list you will need to determine what is blocking the application.

####Are there issues with firewalls in my network?
* Confirm that host-based firewall and antivirus detection are disabled on the system you are installing the application on. See _Using anti-virus software on the server_ in the _administrator’s guide_ for more information.
* Ensure the IP address of the application server is white-listed through firewalls and content filters. This will allow you to reach the update server and pull down any necessary .jar files for activation and updates.

####Have I tried everything?

* Restart the application, in some cases a browser anomaly can cause an error message that your activation failed. Restarting may be successful in those rare cases.