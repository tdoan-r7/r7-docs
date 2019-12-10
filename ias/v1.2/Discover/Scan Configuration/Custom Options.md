---
title: "Custom Options"
excerpt: ""
---
##Proxy
Some organizations require users to access web applications through a proxy server so that traffic can be monitored. You can learn about proxy servers here: https://en.wikipedia.org/wiki/Proxy_server
If your target app requires access through a proxy, you can configure the proxy connection using the "Custom Options > Proxy" screen. There are several options available in this screen.

* **No Proxy** - Use this option if your app can be accessed without a proxy server.
* **Manual configuration** - If you know the URL/IP address and port of the proxy server, you can add it in the manual configuration section.
* **Automatic configuration** - Some organisations have multiple proxies and specific rules around what proxy can be used to access which application. In order to simplify this process, these rules are written in a Proxy Auto-Config (PAC) file. You can find an example of a PAC file here: https://findproxyforurl.com/example-pac-file/.
If you have a PAC file hosted online, you can provide the URL in this field. Make sure that the URL is accessible from the system running the <<product>> engine.

If the proxy requires authentication, you must provide the username and password in the respective fields. 

##Performance
The **Performance** subsection allows you to tune the balance between efficiency and thoroughness of scanning. The performance parameters will also depend on the hardware and network capabilities of your application server. Some examples of editable parameters are *Number of URL Retry Attempts*, *Min Delay Between Requests (ms)*, and *Maximum Bandwidth (KB/s)*. 

There are also some flags that can be switched *On* or *Off* based on your scan preferences:
* Close connection after every request - You should turn this on if your application has not been programmed to handle HTTP pipelining.
* Sequential scan - Enabling this option will ensure that InsightAppSec tries all attacks selected in your scan configuration on one link before moving to the next one.

##HTTP Headers
The **HTTP Headers** subsection allows you to enter some commonly used headers such as *Accept* and *Content-type*. There is also an area for you to enter other custom headers in the format `header-name=header-value`. Each new header in this box should be added in a new line.