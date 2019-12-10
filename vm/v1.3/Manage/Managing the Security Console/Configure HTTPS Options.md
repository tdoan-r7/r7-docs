---
title: "Configure HTTPS Options"
excerpt: ""
---
Depending on your environment, you may not want to use the default HTTPS options in the Security Console. However, note that changes in the HTTPS options may result in the following:

  * An invalid configuration can be produced, which will prevent the web server startup until it has been fixed and restarted. Until then, users will see a generic connection error in their web browser.
  * Some API clients may be too old to connect using modern protocol and ciphers, resulting in TLS/SSL failure error messages and potential breaking of any scripts in use.
  * 3rd party integrations may not support modern protocol or ciphers and could fail to connect, resulting in TLS/SSL failure error messages and potential breaking of any scripts in use. 

These changes do not impact scanning functionality.

#Configure HTTPS Options
Complete this procedure to change the default TLS and SSL configuration. 

**To change the HTTPS options:**

1. [Stop the Nexpose service](https://nexpose.help.rapid7.com/docs/service-start-stop-and-status-controls) 
2. In your Security Console, go to the `[installation path]/nsc/` directory.
3. Find the `CustomEnvironment.properties` file. If this file does not exist, you must create it. The filename and extension are case sensitive. Read more about this process [here](https://nexpose.help.rapid7.com/docs/enabling-fips-mode).
4. Open the file. The default configuration appears.
5. Decide which of the following protocols you want to use for SSL/TLS:
  * SSLv3
  * SSLv2Hello
  * TLSv1
  * TLSv1.1
  * TLSv1.2
6. To configure the enabled protocols, add the following line to the file where each protocol is separated by a comma without any spaces: `com.rapid7.nexpose.nsc.sslEnabledProtocols=TLSv1,TLSv1.1,TLSv1.2`
  * Supported protocols are limited to Java 8:  https://docs.oracle.com/javase/8/docs/technotes/guides/security/StandardNames.html#jssenames 
7. To configure the enabled cipher suites using Apache-style syntax, add the following line to the file:  `com.rapid7.nexpose.nsc.sslEnabledCiphers=ECDH+AESGCM:DH+AESGCM:ECDH+AES256:DH+AE S256:ECDH+AES128:DH+AES:!aNULL:!MD5:!DSS`
  *  If these cypher suites are not suitable, please review other recommendations from Mozilla here: https://wiki.mozilla.org/Security/Server_Side_TLS#Recommended_configurations 
8. Save the file.
9. Restart the Nexpose Service.

#Learn More
To read additional information about the HTTPS option, please read the following Rapid7 blog posts:
  * https://blog.rapid7.com/2015/10/14/tls-coverage-improvements-in-nexpose-602/ 
  * https://blog.rapid7.com/2015/12/16/more-tls-improvements-in-nexpose/