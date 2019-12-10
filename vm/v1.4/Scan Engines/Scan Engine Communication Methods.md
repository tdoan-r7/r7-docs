---
title: "Scan Engine Communication Methods"
excerpt: ""
---
Scan Engines can initiate communication with the Security Console in one of two ways:

* [Standard (Console-to-Engine)](doc:scan-engine-communication-methods#section-standard-console-to-engine-)
* [Reverse (Engine-to-Console)](doc:scan-engine-communication-methods#section-reverse-engine-to-console-)

These communication methods are determined by how you pair the Scan Engine to the Security Console at the time of deployment.  On a fundamental basis, the purpose of both of these methods is to establish an open channel of communication between the console and the engine so that scan instructions and data can flow freely between the two.  The communication method that you choose to implement only determines where this channel originates.  In both cases, once communication is established, the Security Console and the Scan Engine perform their tasks together.

This article explains the differences between the standard console-to-engine and reverse engine-to-console communication methods, and also provides instructions on [how to change the communication method](doc:scan-engine-communication-methods#section-how-to-change-the-communication-method-of-a-scan-engine) of an engine that you have already paired.

[block:callout]
{
  "type": "info",
  "title": "TIP",
  "body": "For instructions on how to pair your Scan Engine according to these methods, see the [Distributed Scan Engines](doc:configuring-distributed-scan-engines) page."
}
[/block]
# Standard (Console-to-Engine)

This is the most common communication method for a distributed Scan Engine.  When the Security Console determines that a scan needs to take place on your target assets, it initiates the connection to communicate with the Scan Engine.

As a result, **Scan Engines** must allow inbound traffic on the default port of 40814 in order to create this connection.

# Reverse (Engine-to-Console)

The engine-to-console communication method, which is implemented by a “reverse” pairing procedure, is useful in cases where your security policies restrict inbound connections to the network hosting the scan engine.  In engine-to-console configurations, the Scan Engine routinely pings the Security Console to see if a scan job needs to be run.  If the Security Console does in fact have a scan job ready, it accepts the connection from the Scan Engine and the communication channel is established.

As a result, **Security Consoles** must allow inbound traffic on the default port of 40815 in order to create this connection.

# How to Change the Communication Method of a Scan Engine
[block:callout]
{
  "type": "danger",
  "title": "IMPORTANT",
  "body": "If you elect to adjust the communication method of your Scan Engine, make sure you adjust your firewall rules to accommodate its new status."
}
[/block]
If you need to change the communication method for a distributed Scan Engine that you have already paired to the Security Console, you can do so from the Scan Engine management page.

To change the communication direction of a distributed Scan Engine:

1. Browse to and click on the **Administration** tab in your left navigation menu.
2. In the “Scan Options” section, click **manage** next to “Engines”.
3. In the “Scan Engines” table, locate the entry for the Scan Engine that you want to adjust.
4. In the “Communication Status” column, click the arrow icon to switch between communication methods.