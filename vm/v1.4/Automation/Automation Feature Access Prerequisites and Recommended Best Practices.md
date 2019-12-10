---
title: "Automation Feature Access Prerequisites and Recommended Best Practices"
excerpt: ""
---
Automation on InsightVM is now available to customers with an [insight.rapid7.com](https://insight.rapid7.com) account.  The goal of this article is to familiarize you with all the prerequisites needed to enable the Automation interface in your InsightVM environment.  Additionally, in order to best prepare you for success with these Automation features, ensure that you complete the recommended best practices described here as well.

# Prerequisites

Your InsightVM environment must meet all of the following prerequisites in order to access Automation features.

## You Must Have an InsightVM License

Automation features are only available to customers with an InsightVM license.  Automation features are not available to customers with a legacy Nexpose Now license.

## You Must Be a Global Administrator

You must be a Global Administrator in the Security Console to access and use the Automation interface and its features.

## Enable Cloud Access

Your Security Console must be activated on the Rapid7 Insight platform in order to access the Automation interface.

Complete the [console activation procedure](doc:activating-your-console-on-the-insight-platform) if you have not already done so.

## Configure Communications With the Insight Platform

Your Security Console must be able to reach the necessary hostnames according to your selected region.

See the [Configure communications with the Insight platform](doc:configure-communications-with-the-insight-platform) page for instructions.

## Complete the User Account Mapping Process

Finally, you must successfully complete the user account mapping process to enable the Automation interface in your InsightVM environment.  If you are eligible for Automation access, InsightVM automatically prompts you to complete this mapping when you attempt to open any of your existing cloud capabilities on your left navigation menu.  You will only need to complete this mapping once per individual user.

See our [Help page](doc:email-confirmation-for-insight-platform-account-mapping) for additional information and instructions on how to complete this mapping successfully.

# Recommended Best Practices

The following recommendations, although not required to access Automation features, will nonetheless ensure that your environment is best prepared to support them going forward.

## Verify That Your Network Connection is Stable

As with other InsightVM cloud capabilities, Automation features depend on a successful sync between your InsightVM console and the Rapid7 Insight platform.  An unstable network connection can interfere with this sync process.  Verify that your network connection is stable and free of issues in order to provide the best conditions for a successful sync.

## Update Your Console to Latest Version

As is best practice anytime you attempt to access new functionality in a software product, make sure you are running the latest version of the Security Console before proceeding.

If you have opted not to receive automatic product updates for the Security Console, see the [Managing versions, updates, and licenses](doc:managing-versions-updates-and-licenses) page to learn how to perform a manual update.

## Perform a Database Backup

Also in line with general best practice, when you are making changes to your environment or enabling new functionality, perform a database backup.

See the [Database backup/restore and data retention](doc:database-backuprestore-and-data-retention) page for instructions.

## Use Only Your Own Email Address For Your insight.rapid7.com Account

[insight.rapid7.com](https://insight.rapid7.com) accounts use email addresses as unique identifiers and are intended for individual users.  Rapid7 does not recommend creating [insight.rapid7.com](https://insight.rapid7.com) accounts based on preexisting shared Security Console logins.

Additionally, ensure that you submit an email address meant only for your exclusive use when completing the [user account mapping process](doc:email-confirmation-for-insight-platform-account-mapping) described previously.  **All individual users** must complete the account mapping process separately, so the creation of an [insight.rapid7.com](https://insight.rapid7.com) account based on a shared console login is unnecessary.
[block:callout]
{
  "type": "success",
  "title": "You’re ready for Automation!",
  "body": "Now that you’ve satisfied the prerequisites and implemented the recommended best practices, you can start using Automation features.  See the [Automation Features](doc:automation) page to get started."
}
[/block]