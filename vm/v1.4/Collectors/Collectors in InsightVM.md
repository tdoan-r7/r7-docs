---
title: "Collectors in InsightVM"
excerpt: ""
---
InsightVM can now utilize the Collector to transmit vulnerability data to the Insight platform.  If you are also an InsightIDR or InsightOps subscriber, you can use any Collectors you have already deployed for this InsightVM functionality.

See the following pages for Collector requirements, installation, and troubleshooting:

 * [Collector Requirements](doc:collector-requirements)
 * [Collector Installation and Deployment](doc:collector-installation-and-deployment)
 * [Collector Troubleshooting](doc:collector-troubleshooting)

# How Agents and Collectors Communicate

Collectors act as intermediaries between your deployed Insight Agents and the Insight platform.  If no usable [proxy rule](https://insightagent.help.rapid7.com/docs/proxy-configuration) is defined on the agent and if the path to a Collector is deemed most efficient, the agent can send its data to the Collector instead of reporting directly to the Insight platform. Collectors then send this data to the Insight platform for assessment.

To decide on the most suitable path, the agent automatically probes all communication routes to the Insight platform and weighs them according to a communication efficiency metric.  This metric is composed of both distance and latency figures.  Possible communication routes include:

* [Proxy rule definitions](https://insightagent.help.rapid7.com/docs/proxy-configuration) configured on the agent or agent endpoint
* Routes to on-premises Collectors
* Standard direct communication from the agent to the Insight platform

After the agent gathers efficiency metrics for all possible paths, it checks if a proxy rule has been defined.  If the proxy rule exists and is usable, the agent uses the proxy route over all other paths, regardless of efficiency.  If no proxy is found or usable at the time, the agent uses the communication route with the best efficiency metric, which can be a route through a Collector or a standard direct communication route to the Insight platform.

By their nature and use case, communication routes through properly deployed Collectors yield better efficiency metrics than standard direct communication to the Insight platform.  However, these metrics can degrade if the Collector is too far away or under substantial load.  If you have not configured your agents with proxy rules and want to minimize the possibility of your agents communicating directly with the Insight platform, proper Collector placement and resource allocation is essential.
[block:callout]
{
  "type": "warning",
  "title": "Reminder - Collectors and Proxy Rules",
  "body": "[Proxy rule definitions](https://insightagent.help.rapid7.com/docs/proxy-configuration) configured on your agents take precedence over any Collector paths, regardless of their communication efficiency."
}
[/block]
As with InsightIDR and InsightOps use cases, you can deploy multiple Collectors based on your data needs and the geographic location of your assets.

# Browse Collectors in InsightVM

To access the Collectors area in InsightVM, click the **Management** tab in your left navigation menu.  At the top of the screen, click the **Collectors** tab.  Any Collectors in your network are displayed on the “Manage Collector” page.  The **Collectors** tab also includes direct links to Collector download and activation pages, as well as relevant documentation.