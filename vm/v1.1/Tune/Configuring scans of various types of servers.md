---
title: "Configuring scans of various types of servers"
excerpt: ""
---
##Configuring spam relaying settings

Mail relay is a feature that allows SMTP servers to act as open gateways through which mail applications can send e-mail. Commercial operators, who send millions of unwanted spam e-mails, often target mail relay for exploitation. Most organizations now restrict mail relay services to specific domain users.

To configure spam relay settings:

1. Go to the _Spam Relaying_ page:
2. Type an e-mail address in the appropriate text field.
This e-mail address should be external to your organization, such as a Yahoo! or Hotmail address. The application will attempt to send e-mail from this account to itself using any mail services and mail scripts that it discovers during the scan. If the application receives the e-mail, this indicates that the servers are vulnerable.
3. Type a URL in the **HTTP_REFERRER to use** field.
This is typically a Web form that spammers might use to generate Spam e-mails.
4. Configure any other template settings as desired. When you have finished configuring the scan template, click **Save**.

##Configuring scans of database servers

InsightVM performs several classes of vulnerability and policy checks against a number of databases, including:
* MS SQL/Server versions 6, 7, 2000, 2005, 2008
* Oracle versions 6 through 12
* Sybase Adaptive Server Enterprise (ASE) versions 9, 10 and 11
* DB2 version 9
* AS/400
* PostgreSQL versions 6, 7, 8, 9
* MySQL Server versions 3, 4, 5
* Mongo DB versions 2, 3

For all databases, the application discovers tables and checks system access, default credentials, and default scripts. Additionally, it tests table access, stored procedure access, and decompilation.

To configure to scan database servers:
1. Go to the _Database Servers_ page.
2. Enter the name of a DB2 database in the appropriate text field that the database can connect to.
3. Enter the name of a Postgres database in the appropriate text field that the application can connect to.
InsightVM attempts to verify an SID on a target asset through various methods, such as discovering common configuration errors and default guesses. You can now specify additional SIDs for verification.
4. Enter the names of Oracle SIDs in the appropriate text field, to which it can connect. Separate multiple SIDs with commas.
5. Configure any other template settings as desired. When you have finished configuring the scan template, click **Save**.

##Configuring scans of mail servers

You can configure InsightVM to scan mail servers.

To configure to scan mail servers:
1. Go to the _Mail Servers_ page.
2. Type a read timeout value in the appropriate text field.
This setting is the interval at which the application retries accessing the mail server. The default value is 30 seconds.
3. Type an inaccurate time difference value in the appropriate text field.
This setting is a threshold outside of which the application will report inaccurate time readings by system clocks. The inaccuracy will be reported in the system log.
4. Configure any other template settings as desired. When you have finished configuring the scan template, click **Save**.

##Configuring scans of CVS servers

InsightVM tests a number of vulnerabilities in the Concurrent Versions System (CVS) code repository. For example, in versions prior to v1.11.11 of the official CVS server, it is possible for an attacker with write access to the CVSROOT/passwd file to execute arbitrary code as the cvsd process owner, which usually is root.

To configure scanning CVS servers:
1. Go to the _CVS Servers_ page.
2. Enter the name of the CVS repository root directory in the text box.
3. Configure any other template settings as desired. When you have finished configuring the scan template, click **Save**.

##Configuring scans of DHCP servers

DHCP Servers provide Border Gateway Protocol (BGP) information, domain naming help, and Address Resolution Protocol (ARP) table information, which may be used to reach hosts that are otherwise unknown. Hackers exploit vulnerabilities in these servers for address information.

To configure InsightVM to scan DHCP servers:
1. Go to the _DHCP servers_ page.
2. Type a DHCP address range in the text field. The application will then target those specific servers for DHCP interrogation.
3. Configure any other template settings as desired. When you have finished configuring the scan template, click **Save**.

##Configuring scans of Telnet servers

Telnet is an unstructured protocol, with many varying implementations. This renders Telnet servers prone to yielding inaccurate scan results. You can improve scan accuracy by providing InsightVM with regular expressions.

To configure scanning of Telnet servers:
1. Go to the _Telnet Servers_ page.
2. Type a character set in the appropriate text field.
3. Type a regex for a logon prompt in the appropriate text field.
4. Type a regex for a password prompt in the appropriate text field.
5. Type a regex for failed logon attempts in the appropriate text field.
6. Type a regex for questionable logon attempts in the appropriate text field.
For more information, go to [Using regular expressions](doc:using-regular-expressions).
7. Configure any other template settings as desired. When you have finished configuring the scan template, click **Save**.