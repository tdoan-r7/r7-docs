---
title: "Scan Engine and Insight Agent Comparison"
excerpt: ""
---
#Scan Engine Overview
A scan engine is an application used with the Security Console that helps discover and collect network asset data and scans them for vulnerabilities and policy compliance. For more information, see our [scan engines](doc:selecting-a-scan-engine-for-a-site) Help documentation. 
#Insight Agent Overview
The Insight Agent is lightweight software you can install on supported assets—in the cloud or on-premises—to easily centralize and monitor data on the Insight platform. For more information, see our [Insight Agent](https://insightagent.help.rapid7.com/docs/overview) Help documentation. 
[block:html]
{
  "html": "<div>\n<table style=\"font-size: 14px\">\n  \n  <tr>\n    <td width=\"25%\"></td>\n    <td>Insight Agent</td>\n    <td colspan=\"2\" style=\"text-align:center\">Scan Engine</td>\n  </tr>\n  \n  <tr>\n    <td width=\"25%\"></td>\n    <td></td>\n    <td>Unauthenticated</td>\n     <td>Authenticated</td>\n  </tr>\n   \n  <tr>\n    <td>Speed</td>\n    <td>Fastest</td>\n     <td>Faster</td>\n     <td>Fast</td>\n   \n \n  </tr>\n   <tr>\n    <td>Credentials</td>\n    <td>None</td>\n    <td>None</td>\n    <td>Required</td>\n  </tr>\n  \n  <tr>\n    <td>Supports Scheduling</td>\n    <td>No</td>\n    <td>Yes</td>\n    <td>Yes</td>\n  </tr>\n  \n  <tr>\n    <td>Scan Blackouts</td>\n    <td>No</td>\n    <td>Yes</td>\n    <td>Yes</td>\n  </tr>\n  \n  <tr>\n    <td>Collection</td>\n    <td>Regularly</td>\n    <td>During scan</td>\n    <td>During scan</td>\n  </tr>\n  \n  <tr>\n    <td>Type of Check</td>\n    <td>Local only</td>\n     <td>Remote only</td>\n    <td>Local, remote, and policy</td>\n   \n  </tr>\n  \n</table>\n</style>\n</div>"
}
[/block]
#Flexible Deployment Options
The agent and scan engine are designed to complement each other. If both scan the same asset, the console will automatically recognize the data and merge the results.

##Scan Engine Usage Scenarios
*  To perform remote or policy checks
*  To discover assets via discovery scans or connections
*  To assess assets unsupported by the agent, such as network devices

##Agent Usage Scenarios
*  Asset is located outside of the corporate network
*  Asset is located in a highly isolated or micro-segmented network
*  Asset does not have remote access services (SMB, SSH, etc.) enabled
*  Asset remote access credentials are unavailable
*  Asset is only online for short periods of time
*  Asset is sensitive to network-based scanning
*  Asset requires continuous monitoring as opposed to periodic scans
*  Asset is in a dynamic, cloud, or other complex modern environment that requires flexible deployment
[block:callout]
{
  "type": "info",
  "title": "NOTE",
  "body": "The agent is currently supported on Windows, Linux, and Mac operating systems."
}
[/block]