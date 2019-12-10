---
title: "Using the Agent with InsightVM"
excerpt: ""
---
Insight Agents are vital tools to monitor assets in your organization, either on the network, or in the hands of remote employees. To help you understand how agents can help you, let’s take a look at some of the benefits of agents while using InsightVM:
* **You can track remote assets:** Some assets owned by your organization may be off the organization’s network for long periods of time. For example, a laptop used by an employee who works remotely may not be on the company network. You can place an agent on this asset and have it send data back to the platform so that it can be assessed for vulnerabilities.
* **You can assess assets that are under heavy scanning restrictions:** If an asset is used in critical infrastructure or in day-to-day business operations, it may be difficult to find a convenient window to scan it thoroughly. For a more thorough assessment, you can deploy an agent that is only active for 30 seconds so that it can collect data and send it back to your Insight product for a more thorough assessment.
* **You can access assets without credentials:** This spares you from having to store credentials in InsightVM.

##Data Collected by Insight Agents using InsightVM
When deployed, an agent collects data from the endpoint, compresses it, and sends it back to InsightVM for analysis. The data it collects includes:
* Basic asset identification information
* Windows registry information
* File version and package information
[block:callout]
{
  "type": "info",
  "body": "For more information about the Insight Agent, please go to [https://insightagent.help.rapid7.com/](https://insightagent.help.rapid7.com/)."
}
[/block]