---
title: "Insight Agents with InsightVM"
excerpt: ""
---
As an InsightVM subscriber, you can access several feature-rich cloud capabilities powered by the Insight platform. To complement the on-premises scanning infrastructure that you may already have, you can also install the Insight Agent across your network for the purpose of vulnerability assessment.
[block:callout]
{
  "type": "info",
  "title": "How do Scan Engines and Insight Agents differ?",
  "body": "See our [Scan Engine and Insight Agent Comparison](doc:scan-engine-and-insight-agent-comparison) page to learn more about how these data collection tools compare side by side."
}
[/block]

[block:callout]
{
  "type": "info",
  "title": "Where can I view my Insight Agents after I've deployed them?",
  "body": "The Agent Management view in your Insight platform account page is the central location for monitoring all the Insight Agents you have deployed across your organization.\n\nSee the [Agent Management Help page](https://insightagent.help.rapid7.com/docs/agent-management) to learn how to access this view."
}
[/block]
To ensure coverage for your whole organization, deploy the Insight Agent when the requirements of traditional scanning conflict with the network characteristics of your assets.

# Benefits of Using the Insight Agent with InsightVM

The Insight Agent best addresses the vulnerability assessment needs of assets that have the following characteristics:

* **Assets running from remote locations** - You may have assets in your organization that operate outside of your company network for long periods of time and regularly connect to the internet in different locations.  While a traditional scan requires target assets to be present on your network in order to be assessed, the Insight Agent can send vulnerability data to the Insight platform as long as the asset has an internet connection. Whether the asset is on your company network or on its assigned user’s home network, the Insight Agent has you covered.
* **Assets with heavy scanning restrictions** - Some of your assets may serve in roles that are too business-critical to absorb the load of a traditional scan during standard hours of operation. This means you often have to find a suitable scanning window for these assets, which can be difficult depending on the role they play. Insight Agents are considerably less burdensome by comparison because the actual assessment process is the responsibility of the Insight platform.
* **Assets restricted by credentials** - Traditional scans rely on configured credentials in InsightVM in order to authenticate to the target asset, which yields more comprehensive vulnerability results.  Since Insight Agents monitor the asset from within, their assessments are functionally authenticated already, thus sparing you from having to configure credentials at all.

# Learn More on the Insight Agent Help Pages

Insight Agents are an important part of any InsightVM deployment, and even more so if your organization also subscribes to [InsightIDR](https://insightidr.help.rapid7.com/docs/) or [InsightOps](https://insightops.help.rapid7.com/docs/).  For this reason, Rapid7 continually develops and maintains a dedicated documentation set for all Insight Agent related resources.

Check out the [Insight Agent Help pages](https://insightagent.help.rapid7.com/docs/) to read more about the following topics:

* Overview information, including the types of data that the Insight Agent collects and how the agent software updates
* Comprehensive requirements, including supported operating systems, network configuration, and application settings
* Complete download and install instructions for both Insight Agent installer types
* Mass deployment guidelines
* Advanced configuration options
* Common troubleshooting solutions
[block:callout]
{
  "type": "success",
  "body": "https://insightagent.help.rapid7.com/docs/",
  "title": "Check out the Insight Agent Help pages!"
}
[/block]