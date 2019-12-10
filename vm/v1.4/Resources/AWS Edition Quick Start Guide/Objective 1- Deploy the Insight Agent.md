---
title: "Objective 1: Deploy the Insight Agent"
excerpt: ""
---
The Insight Agent is software that collects security-relevant data from the device on which it is installed.  Unlike traditional collectors with costly processing overhead, the agent relies on asset status changes in order to perform its specific data collection tasks as directed by the Insight platform.  This service-based deployment is what makes InsightVM assessment features possible—all while reducing the burden on the asset itself.

For this objective, you will install the Insight Agent on each of your EC2 instances for ongoing vulnerability assessment.

# Deployment Methods

The Insight Agent supports a variety of deployment methods for both virtual and on-premises assets.  See our [Insight Agent Help pages](https://insightagent.help.rapid7.com/docs/overview) for complete agent download and installation documentation.

## Manual Deployment

If you intend to deploy the agent manually with a preconfigured AMI, make sure that you follow the guidelines listed on the [Virtualization](https://insightagent.help.rapid7.com/docs/virtualization) page to avoid data reporting conflicts.

## Automated Deployment With AWS System Manager Documents

You can also use AWS tooling to make sure that every EC2 instance you provision includes the agent automatically.  See our [blog post](https://blog.rapid7.com/2018/11/12/how-to-automate-insight-agent-deployment-in-aws/) for instructions on how to do this.

# Initial Data Collection Time

Once you have the agent installed on your assets, allow at least six hours for each of them to report some usable data to the Insight platform.  Feel free to take a break and come back to the rest of this guide at a later time.
[block:callout]
{
  "type": "success",
  "title": "Insight Agent deployed!",
  "body": "You should now have the Insight Agent deployed on your EC2 instances.  After you’ve allowed enough time for your agents to collect some data, you can build your first dashboard."
}
[/block]