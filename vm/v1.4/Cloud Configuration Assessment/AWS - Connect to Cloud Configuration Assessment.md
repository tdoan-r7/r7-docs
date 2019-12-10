---
title: "AWS - Connect to Cloud Configuration Assessment"
excerpt: ""
---
[block:callout]
{
  "type": "info",
  "body": "A feature that is in \"preview\" has made enough progress to be suitable for customer use, albeit still in active development.\n\nInsightVM customers can take advantage of this preview offering to provide early feedback and usage data that will shape the final version of Cloud Configuration Assessment when it becomes Generally Available (GA).\n\nLike other preview features, the Cloud Configuration Assessment preview may not yet have all the functionality planned for the GA version and may only be accessible from cloud-enabled pages in InsightVM (such as the **Dashboard** tab).  Using this preview will not affect your production data.\n\nYou can provide your feedback on the Cloud Configuration Assessment preview by completing the following survey:\n\nhttps://www.surveygizmo.com/s3/4936396/VM-Cloud-Configuration-Assessment-Survey\n\nThe following features are not yet available in the preview, but are planned for GA:\n* Ability to group rules into benchmarks",
  "title": "NOTE: Cloud Configuration Assessment is currently available in \"preview\" form"
}
[/block]
This article explains how to create a connection to your Amazon Web Services (AWS) environment for use with the [Cloud Configuration Assessment](doc:cloud-configuration-assessment-overview) feature.

# Before You Begin

Before you set up a connection to Amazon Web Services (AWS), you'll need to access the following interfaces:

* Your Cloud Configuration Assessment interface in InsightVM
* Your choice of the AWS Management Console or the AWS Command Line Interface (CLI) tool

Make sure to have both of these interfaces open and available as you follow this guide.  After you create your IAM role with its attached policies, you'll need to go back to InsightVM to complete and test your connection.

# Connection Requirements

InsightVM must assume a custom IAM role with cross-account access in order to assess your AWS infrastructure.  This role includes two policies made entirely of **read-only** permissions:

* The default AWS “SecurityAudit” policy
* A custom policy that grants additional permissions required by the Cloud Configuration Assessment feature
[block:callout]
{
  "type": "warning",
  "title": "NOTE",
  "body": "The additional read-only permissions encompassed by this custom policy represent the auditable cloud configuration areas that are not included in the default AWS “SecurityAudit” policy."
}
[/block]
## How InsightVM Manages Simultaneous Connections to AWS Services

In the course of collecting data for Cloud Configuration Assessment, InsightVM will only connect to one AWS service per account at the same time. In order to mitigate against any potential service disruption, InsightVM will exponentially scale back data collection if rate limits are exceeded on the account.

# Connection Setup Methods

You can configure the necessary IAM role and its dependent policies in the AWS Management Console or the AWS Command Line Interface (CLI).
[block:callout]
{
  "type": "info",
  "title": "REMINDER",
  "body": "Have both InsightVM and your preferred AWS interface open during the setup process."
}
[/block]
## AWS Management Console Method

If you elect to use the AWS Management Console to configure your connection, you’ll need to do the following:

1. [Create the IAM Role](doc:aws-connect-to-cloud-configuration-assessment#section-create-the-iam-role)
2. [Attach Policies](doc:aws-connect-to-cloud-configuration-assessment#section-attach-policies)
3. [Finish Role Creation](doc:aws-connect-to-cloud-configuration-assessment#section-finish-role-creation)

### Create the IAM Role

**To create the necessary IAM role in the AWS Management Console:** 

1. In your AWS Management Console, expand the **Services** dropdown.  Under the “Security, Identity, & Compliance” section, click the **IAM** link.
2. On your left navigation menu, click the **Roles** tab to change the tab view.  Click the **Create role** button.
3. On the “Create role” page, select the **Another AWS account** option.
4. Enter `336818582268` in the “Account ID” field.
5. In the “Options” section, check the **Require external ID** box.
 * Checking this box produces an additional “External ID” field.
6. Switch to your InsightVM screen.  Click the **Management** tab in your left navigation menu.
7. On the “Settings” page, browse to the “Cloud Infrastructure” section.  Click **Add** next to the “Amazon Web Services” entry.
8. The “Add Cloud Infrastructure” panel appears.  Expand the **AWS Console** dropdown and copy your External ID.
9. Return to your AWS Management Console and paste this value in the “External ID” field.
10. Make sure that the **Require MFA** box is not checked.
11. Click the **Next: Permissions** button when finished to move to the next page.

### Attach Policies

With your new IAM role in place, you must now attach the required policies.

**To attach the required policies to your IAM role:**

1. In the “Attach permissions policies” section, filter for the “SecurityAudit” policy and check the box to attach it to your role.
 * “SecurityAudit” is the default AWS policy that the Cloud Configuration Assessment feature needs to function.
2. Click the **Create policy** button to configure the second custom policy required by InsightVM.  Your AWS Management Console opens a second browser tab for this process.
3. On the “Create policy” page, click the **JSON** tab.
4. Switch to your InsightVM screen.  Expand the **Managed Policy Document** dropdown and copy the JSON code shown.
 * To avoid formatting errors, you can click the provided **Copy** button to copy all JSON code.
5. Return to your AWS Management Console and paste the inline policy JSON code into the provided code editor space.
6. Click the **Review policy** button when finished.
7. On the “Review policy” page, name and optionally describe the policy.
8. Click the **Create policy** button when finished.
9. Return to the browser tab displaying the “Create role” page.  Click the refresh icon to ensure the policy list reflects your new policy.
10. Check the box of your custom policy to attach it to your role.
11. Click the **Next: Tags** button to move to the next page.

### Finish Role Creation

Lastly, you need to finalize the creation of your IAM role.

**To finish the role creation procedure:**

1. Optionally apply any tags according to your organization’s management best practices.
2. Click the **Next: Review** button to move to the next page.
3. On the “Review” page, name and optionally describe the role.
4. Click the **Create role** button when finished.
[block:callout]
{
  "type": "success",
  "title": "IAM role creation complete",
  "body": "Now that your new IAM role is ready for use, proceed to the “[Complete the Connection in InsightVM](doc:aws-connect-to-cloud-configuration-assessment#section-complete-the-connection-in-insightvm)” section of this guide."
}
[/block]
## AWS CLI Method

If you elect to use the AWS Command Line Interface (CLI) to configure your connection, you’ll need to do the following:

1. [Create the Rapid7 Custom Policy](doc:aws-connect-to-cloud-configuration-assessment#section-create-the-rapid7-custom-policy)
2. [Create the IAM Role (CLI)](doc:aws-connect-to-cloud-configuration-assessment#section-create-the-iam-role-cli-)
3. [Attach Policies (CLI)](doc:aws-connect-to-cloud-configuration-assessment#section-attach-policies-cli-)
[block:callout]
{
  "type": "warning",
  "title": "NOTE",
  "body": "You must have the [AWS CLI](https://aws.amazon.com/cli/) installed in order to use this connection setup method."
}
[/block]

[block:callout]
{
  "type": "danger",
  "title": "IMPORTANT",
  "body": "All the scripts in this CLI procedure use the name “Rapid7-Security-Audit” for both the IAM role and the custom policy attached to it for command consistency.  If you rename the role, the custom policy, or both, you must also adjust dependent commands with the correct name of your choosing."
}
[/block]
### Create the Rapid7 Custom Policy

The custom policy created in this step represents the extra **read-only** permissions that InsightVM needs to assess your AWS environment.

**To create the custom policy:**

1. Open a terminal or command prompt.
2. Copy and run the following script to create the custom policy required by InsightVM:
[block:callout]
{
  "type": "danger",
  "title": "IMPORTANT - Windows formatting requirements",
  "body": "If you intend to run this script with the AWS CLI tool on a Windows machine, you must escape all instances of double quotes (`”`) for the script to process correctly.\n\nYou can copy a revised version of this script below the “Create Policy Script - Windows Format” box."
}
[/block]

[block:code]
{
  "codes": [
    {
      "code": "\"Version\": \"2012-10-17\",\n    \"Statement\": [\n        {\n            \"Effect\": \"Allow\",\n            \"Action\": [\n                \"acm:ListTagsForCertificate\",\n                \"cloudtrail:ListPublicKeys\",\n                \"cloudtrail:ListTags\",\n                \"cloudtrail:GetTrailStatus\",\n                \"cloudtrail:GetEventSelectors\",\n                \"ecr:DescribeRepositories\",\n                \"ecr:GetLifecyclePolicy\",\n                \"ecr:GetRepositoryPolicy\",\n                \"ecr:ListImages\",\n                \"iam:GenerateServiceLastAccessedDetails\",\n                \"lambda:GetFunction\",\n                \"lambda:GetLayerVersion\",\n                \"lambda:GetLayerVersionPolicy\",\n                \"lambda:GetPolicy\",\n                \"lambda:ListFunctions\",\n                \"lambda:ListLayerVersions\",\n                \"sqs:ListQueues\",\n                \"sqs:ListDeadLetterSourceQueues\",\n                \"sqs:ListQueueTags\",\n                \"sqs:GetQueueUrl\",\n                \"sqs:GetQueueAttributes\",\n                \"states:DescribeStateMachineForExecution\",\n                \"states:DescribeActivity\",\n                \"states:DescribeStateMachine\",\n                \"states:DescribeExecution\",\n                \"states:ListExecutions\",\n                \"states:GetExecutionHistory\"\n            ],\n            \"Resource\": \"*\"\n        }\n    ]\n}'",
      "language": "json"
    }
  ]
}
[/block]

[block:callout]
{
  "type": "info",
  "title": "Create Policy Script - Windows Format",
  "body": "The following script is revised with escapes for every double quote`”` to accommodate Windows formatting requirements."
}
[/block]

[block:code]
{
  "codes": [
    {
      "code": "aws iam create-policy --policy-name Rapid7-Security-Audit --policy-document '{\n    \\\"Version\\\": \\\"2012-10-17\\\",\n    \\\"Statement\\\": [\n        {\n            \\\"Effect\\\": \\\"Allow\\\",\n            \\\"Action\\\": [\n                \\\"acm:ListTagsForCertificate\\\",\n                \\\"cloudtrail:ListPublicKeys\\\",\n                \\\"cloudtrail:ListTags\\\",\n                \\\"cloudtrail:GetTrailStatus\\\",\n                \\\"cloudtrail:GetEventSelectors\\\",\n                \\\"ecr:DescribeRepositories\\\",\n                \\\"ecr:GetLifecyclePolicy\\\",\n                \\\"ecr:GetRepositoryPolicy\\\",\n                \\\"ecr:ListImages\\\",\n                \\\"iam:GenerateServiceLastAccessedDetails\\\",\n                \\\"sqs:ListQueues\\\",\n                \\\"sqs:ListDeadLetterSourceQueues\\\",\n                \\\"sqs:ListQueueTags\\\",\n                \\\"sqs:GetQueueUrl\\\",\n                \\\"sqs:GetQueueAttributes\\\",\n                \\\"states:DescribeStateMachineForExecution\\\",\n                \\\"states:DescribeActivity\\\",\n                \\\"states:DescribeStateMachine\\\",\n                \\\"states:DescribeExecution\\\",\n                \\\"states:ListExecutions\\\",\n                \\\"states:GetExecutionHistory\\\"\n            ],\n            \\\"Resource\\\": \\\"*\\\"\n        }\n    ]\n  }'",
      "language": "json"
    }
  ]
}
[/block]
### Create the IAM Role (CLI)

With your custom policy ready for use, you must now create the IAM role.

**To create the necessary IAM role in the AWS CLI:**

1. Navigate to your InsightVM interface.  Click the **Management** tab in your left navigation menu.
2. On the “Settings” page, browse to the “Cloud Infrastructure” section.  Click **Add** next to the “Amazon Web Services” entry.
3. The “Add Cloud Infrastructure” panel appears.  Expand the **CLI** dropdown and copy the script under **Create IAM Role**.
 * InsightVM formats this script to automatically include your necessary External ID.
4. Return to your AWS CLI.  Paste and run the **Create IAM Role** script you copied from the previous step.
5. When the **Create IAM Role** script executes, take note the output for the Amazon Resource Name (ARN). You will need to provide this ARN to InsightVM during the connection configuration.

### Attach Policies (CLI)

After you create the IAM role, you must now attach the required policies.

**To attach the policies to the IAM role:**

1. Run the following command to attach the default AWS “SecurityAudit” policy to your new IAM role:
[block:code]
{
  "codes": [
    {
      "code": "aws iam attach-role-policy --role-name Rapid7-Security-Audit --policy-arn arn:aws:iam::aws:policy/SecurityAudit",
      "language": "json"
    }
  ]
}
[/block]
2. Run the following command to attach the custom Rapid7 policy to your new IAM role:
[block:code]
{
  "codes": [
    {
      "code": "aws iam attach-role-policy --role-name Rapid7-Security-Audit --policy-arn arn:aws:iam::aws:policy/Rapid7-Security-Audit",
      "language": "json"
    }
  ]
}
[/block]

[block:callout]
{
  "type": "success",
  "title": "IAM role creation complete",
  "body": "Now that your new IAM role is ready for use, proceed to the “[Complete the Connection in InsightVM](doc:aws-connect-to-cloud-configuration-assessment#section-complete-the-connection-in-insightvm)” section of this guide."
}
[/block]
# Complete the Connection in InsightVM

Now that your IAM role has been configured successfully with its attached policies, you can complete the connection configuration in InsightVM.

**To complete the connection configuration:**

1. Return to the **Management** tab in InsightVM.
2. Enter a name to describe your AWS account in the “Account Name” field.
3. Enter the ARN of the IAM role you just created in the “Role” field.  Click the **Continue** button.
4. Test the connection to verify the configuration is defined properly.
 * If the connection test fails, verify that you have completed the previous steps correctly according to your setup method of choice and try again.
5. Click the **Save** button when finished.
 * Note that you must allow InsightVM enough time to collect initial configuration data from your AWS infrastructure according to the [data collection interval guidelines](doc:cloud-configuration-assessment-overview#section-data-collection-intervals).
6. Finally, click the **Cloud Configuration** tab on your left navigation menu to view your assessment data.
[block:callout]
{
  "type": "success",
  "title": "AWS connection complete!",
  "body": "InsightVM should now have a working connection to your AWS environment for the purpose of using Cloud Configuration Assessment. You will begin to see results as InsightVM collects data, but note that the size and scope of your account ultimately affects how long this initial process takes.  The initial collection period for large accounts can take up to a few hours, so keep this in mind while your interface continues to update with new assessment results."
}
[/block]