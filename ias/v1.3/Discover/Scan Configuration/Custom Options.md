---
title: "Custom Options"
excerpt: ""
---
The **Proxy** subsection allows you to configure an HTTP or HTTPS proxy that you might want to use to relay your scan requests to your App. If your proxy server requires authentication, you can also save your credentials here.

The **Performance** subsection allows you to tune the balance between efficiency and thoroughness of scanning. The performance parameters will also depend on the hardware and network capabilities of your application server. Some examples of editable parameters are *Number of URL Retry Attempts*, *Min Delay Between Requests (ms)*, and *Maximum Bandwidth (KB/s)*. 

There are also some flags that can be switched *On* or *Off* based on your scan preferences:
* Close connection after every request - You should turn this on if your application has not been programmed to handle HTTP pipelining.
* Sequential scan - Enabling this option will ensure that InsightAppSec tries all attacks selected in your scan configuration on one link before moving to the next one.

The **HTTP Headers** subsection allows you to enter some commonly used headers such as *Accept* and *Content-type*. There is also an area for you to enter other custom headers in the format `header-name=header-value`. Each new header in this box should be added in a new line.