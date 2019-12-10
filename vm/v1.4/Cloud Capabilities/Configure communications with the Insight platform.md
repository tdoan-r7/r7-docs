---
title: "Configure communications with the Insight platform"
excerpt: ""
---
[block:callout]
{
  "type": "info",
  "title": "Still need to opt-in to the cloud?",
  "body": "See [Activating your console on the Insight platform](doc:activating-your-console-on-the-insight-platform) for instructions."
}
[/block]
# Data upload

You may need to whitelist the following hostnames according to your selected region for outbound traffic in order to successfully upload data to the Insight platform:
[block:callout]
{
  "type": "info",
  "title": "Port information",
  "body": "All hostnames listed below are reached via TCP port 443."
}
[/block]

[block:parameters]
{
  "data": {
    "h-0": "Region",
    "h-1": "Web",
    "h-2": "Data",
    "h-3": "S3",
    "h-4": "Australia",
    "0-0": "United States",
    "0-1": "exposure-analytics.insight.rapid7.com",
    "0-2": "data.insight.rapid7.com",
    "0-3": "s3.amazonaws.com",
    "1-0": "Canada",
    "2-0": "Europe",
    "3-0": "Japan",
    "4-0": "Australia",
    "1-1": "ca.exposure-analytics.insight.rapid7.com",
    "2-1": "eu.exposure-analytics.insight.rapid7.com",
    "3-1": "ap.exposure-analytics.insight.rapid7.com",
    "4-1": "au.exposure-analytics.insight.rapid7.com",
    "1-2": "ca.data.insight.rapid7.com",
    "2-2": "eu.data.insight.rapid7.com",
    "3-2": "ap.data.insight.rapid7.com",
    "4-2": "au.data.insight.rapid7.com",
    "1-3": "s3.ca-central-1.amazonaws.com",
    "2-3": "s3.eu-central-1.amazonaws.com",
    "3-3": "s3-ap-northeast-1.amazonaws.com",
    "4-3": "s3-ap-southeast-2.amazonaws.com"
  },
  "cols": 4,
  "rows": 5
}
[/block]
# Ticketing and Container Registry connections

Rapid7 provides the following list of static IP addresses that you may use to whitelist traffic originating from the Insight platform to your on-prem JIRA or container registries:
[block:callout]
{
  "type": "info",
  "title": "Port information",
  "body": "All IP addresses listed below are reached via TCP port 443."
}
[/block]

[block:callout]
{
  "type": "warning",
  "title": "NOTE",
  "body": "This does not address agent proxying use cases or scenarios relating to communication originating from customer environments to the Insight platform."
}
[/block]

[block:parameters]
{
  "data": {
    "h-0": "United States",
    "h-1": "Canada",
    "h-2": "Europe",
    "h-3": "Japan",
    "h-4": "Australia",
    "0-0": "52.87.0.92",
    "1-0": "34.203.6.73",
    "2-0": "34.202.19.138",
    "3-0": "52.2.37.56",
    "0-1": "35.182.161.111",
    "1-1": "52.60.69.60",
    "0-2": "52.28.227.72",
    "1-2": "52.58.219.32",
    "0-3": "13.113.44.15",
    "1-3": "52.69.171.127",
    "0-4": "13.55.206.11",
    "1-4": "13.54.208.29",
    "2-4": "52.63.226.244"
  },
  "cols": 5,
  "rows": 4
}
[/block]
##Data Transmitted to the Insight Platform

The following types of information are transmitted to the Insight platform:
* Asset information
* Asset groups
* Asset owners
* Vulnerabilities
* Vulnerability exceptions
* Tags
* Scan Engine information
* InsightVM Console information
* User information

InsightVM does not transmit service or user credentials of any kind to the Insight platform.
[block:callout]
{
  "type": "info",
  "title": "Looking for Security Console port information?",
  "body": "See [Requirements](doc:requirements) for console-specific port needs."
}
[/block]