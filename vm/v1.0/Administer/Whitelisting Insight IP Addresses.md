---
title: "Whitelisting Insight IP Addresses"
excerpt: ""
---
Rapid7 provides a list of static IP addresses that you may use to whitelist traffic originating from the Insight platform to your on-premise JIRA or container registries.  These IP addresses are used for outbound traffic originating from InsightVM’s automated ticketing and container features. Whitelisting these IP addresses will allow ingress traffic from the Insight platform to communicate with JIRA servers you host and private container registries behind a firewall, allowing you to utilize container and automated ticketing with JIRA features.  
[block:callout]
{
  "type": "warning",
  "title": "",
  "body": "This does not address agent proxying use cases or scenarios relating to communication originating from customer environments to the Insight platform."
}
[/block]

We will avoid changing these IP addresses unless absolutely necessary. If we must make changes, we will update this page.

###United States
52.87.0.92
34.203.6.73
34.202.19.138
52.2.37.56

###Canada
35.182.161.111
52.60.69.60

###Europe
52.28.227.72
52.58.219.32

###Japan
13.113.44.15
52.69.171.127

###Australia
13.55.206.11
13.54.208.29
52.63.226.244