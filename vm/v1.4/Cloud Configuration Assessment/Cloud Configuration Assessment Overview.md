---
title: "Cloud Configuration Assessment Overview"
excerpt: ""
---
[block:callout]
{
  "type": "info",
  "title": "NOTE: Cloud Configuration Assessment is currently available in \"preview\" form",
  "body": "A feature that is in \"preview\" has made enough progress to be suitable for customer use, albeit still in active development.\n\nInsightVM customers can take advantage of this preview offering to provide early feedback and usage data that will shape the final version of Cloud Configuration Assessment when it becomes Generally Available (GA).\n\nLike other preview features, the Cloud Configuration Assessment preview may not yet have all the functionality planned for the GA version and may only be accessible from cloud-enabled pages in InsightVM (such as the **Dashboard** tab).  Using this preview will not affect your production data.\n\nYou can provide your feedback on the Cloud Configuration Assessment preview by completing the following survey:\n\nhttps://www.surveygizmo.com/s3/4936396/VM-Cloud-Configuration-Assessment-Survey\n\nThe following features are not yet available in the preview, but are planned for GA:\n* Ability to group rules into benchmarks"
}
[/block]
Cloud Configuration Assessment in InsightVM is a policy-based assessment feature that provides visibility on the weaknesses that impact the security of cloud infrastructure.  If your organization subscribes to Infrastructure-as-a-Service (IaaS) resources, you can use Cloud Configuration Assessment to assess, address, and monitor the non-compliant resources found in these services to minimize their risk of attack and exploitation.

To access the Cloud Configuration Assessment interface, click the **Cloud Configuration** tab on your left navigation menu.

This series of articles guides you through how to connect your cloud infrastructure to InsightVM and explains how to read your assessment results.

# How Cloud Configuration Assessment Works

Cloud Configuration Assessment works by collecting the configuration data from your IaaS resources.  To collect this data, you need to create connections between InsightVM and your IaaS environments.

With properly configured connections in place, InsightVM can assess your configuration data for policy compliance. The assessment capability is built on a library of rule checks composed of the complete CIS AWS Foundations benchmark, best practice checks from AWS, and proprietary checks from Rapid7.  All these checks are tailored to the specific architecture of many cloud services in use today.  The feature determines compliance per rule on a binary “Pass” or “Fail” basis and ranks their severity according to [Rapid7’s own severity scale](doc:cloud-configuration-assessment-interface-guide#section-severity-scale).

## Data Collection Intervals

InsightVM collects data for Cloud Configuration Assessment in intervals.  These collection intervals can vary anywhere between every two and twelve hours depending on the particular service being assessed. In general, InsightVM collection frequency depends on how dynamic the service is -- the more dynamic the service, the more frequent the collections are. For new connections, you must allow InsightVM enough time to collect an initial set of data before you can view any assessment results.

# Terminology

The Cloud Configuration Assessment interface uses the following terms:

* **Connections** - Account-based access roles that give InsightVM **read-only** access to your IaaS resources.  You can manage and edit each of your saved connections from the **Management** tab of your left navigation menu.
* **Findings** -  Individual instances of a specific rule check across your IaaS resources.  You can have multiple findings of the same rule with varying results as each finding is attached to a specific resource.
* **Resources** - Individual deployed instances of your IaaS services.  For example, if you are an AWS subscriber using the Elastic Compute Cloud (EC2) service, each of your running EC2 instances is considered a resource.
* **Rules** - Specialized policy-based checks tailored to the traits of each of your IaaS services.  These rules evaluate to either a “Pass” or “Fail” status.
* **Exceptions** - User-configured designations that prevent specific rules from counting against your assessment results.  You can configure exceptions for individual findings, a custom scope of findings, or rules in their entirety.

# Supported IaaS Providers

Cloud Configuration Assessment supports connections to the following IaaS providers:

* [Amazon Web Services](doc:aws-connect-to-cloud-configuration-assessment)