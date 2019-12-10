---
title: "Infrastructure Assessment Preview - Configure a Connection to AWS"
excerpt: ""
---
Infrastructure Assessment in InsightVM is a policy-based assessment feature that provides visibility on potential weaknesses that affect cloud infrastructure security.  The feature relies solely on read-only permissions to collect necessary cloud configuration data.

Infrastructure Assessment is currently offered as a preview for select customers with AWS environments.  This guide explains the available setup methods for configuring a connection to your AWS infrastructure.

# How to Follow This Guide

Connection configuration requires concurrent setup in two areas:

* Your Infrastructure Assessment interface in InsightVM
* Your choice of the AWS console or the AWS Command Line Interface (CLI)

Have both of these interfaces open and available as you follow this guide.  After creating your IAM role with its attached policies using your configuration method of choice, return to InsightVM to complete and test your connection.

# Connection Requirements

InsightVM must assume a custom IAM role with cross-account access in order to assess your AWS infrastructure.  This role includes two policies made entirely of **read-only** permissions:

* The default AWS “SecurityAudit” policy
* A custom policy that grants additional permissions required by the Infrastructure Assessment feature
[block:callout]
{
  "type": "warning",
  "title": "NOTE",
  "body": "The additional read-only permissions encompassed by this custom policy represent the auditable cloud configuration areas that are not included in the default AWS “SecurityAudit” policy."
}
[/block]
# Connection Setup Methods

You can configure the necessary IAM role and its dependent policies in the [AWS console](doc:infrastructure-assessment#section-aws-console-method) or the [AWS Command Line Interface (CLI)](doc:infrastructure-assessment#section-aws-cli-method).
[block:callout]
{
  "type": "warning",
  "title": "REMINDER",
  "body": "Have both InsightVM and your AWS interface of choice open and available during the setup procedure."
}
[/block]
## AWS Console Method

Complete the following procedure to configure a connection in the AWS console.

### Create the IAM Role

1. In your AWS console, expand the **Services** dropdown.  Under the “Security, Identity, & Compliance” section, click **IAM**.
2. On your left navigation menu, click **Roles** to change the tab view.  Click **Create role**.
3. On the “Create role” page, select **Another AWS account**.
4. Enter `336818582268` in the “Account ID” field.
5. Next to “Options”, check the **Require external ID** box.
 * Checking this box produces an additional “External ID” field.
6. Navigate to your InsightVM interface.  Click the **Management** tab in your left navigation menu.
7. On the “Settings” page, browse to the “Infrastructure” section.  Click **Add** next to “Amazon Web Services” to retrieve your External ID.
8. Return to your AWS console and paste this value in the “External ID” field.
9. Make sure that the **Require MFA** box is not checked.
10. Click **Next: Permissions** when finished.

### Attach Policies

1. In the “Attach permissions policies” section, filter for the “SecurityAudit” policy and check the box to attach it to your role.
 * “SecurityAudit” is the default AWS policy that Infrastructure Assessment needs to function.
2. Click **Create policy** to configure the second custom policy required by InsightVM.  Your AWS console opens a second browser tab for this process.
3. On the “Create policy” page, click the **JSON** tab.
4. Navigate back to your InsightVM interface.  Expand the “Assume Inline Policy” dropdown and copy the JSON code shown.
 * To avoid copy errors, you can click the provided **Copy to clipboard** button to copy all JSON code.
5. Return to your AWS console and paste the inline policy JSON code into the provided code editor space.
6. Click **Review policy** when finished.
7. On the “Review policy” page, name and optionally describe the policy.
8. Click **Create policy** when finished.
9. Return to the browser tab displaying the “Create role” page.  Click the refresh icon to ensure the policy list reflects your new policy.
10. Check the box of your custom policy to attach it to your role.
11. Click **Next: Tags**.

### Finish Role Configuration

1. Optionally apply any tags according to your organization’s management best practices.
2. Click **Next: Review**.
3. On the “Review” page, name and optionally describe the role.
4. Click **Create role** when finished.
[block:callout]
{
  "type": "success",
  "title": "IAM role creation complete",
  "body": "Now that your new IAM role is ready for use, proceed to the “[Complete the Connection in InsightVM](doc:infrastructure-assessment#section-complete-the-connection-in-insightvm)” section of this guide."
}
[/block]
## AWS CLI Method

Complete the following procedure to configure a connection with the AWS CLI.
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
  "body": "All the scripts in this CLI procedure use the name “Rapid7-Security-Audit” for both the IAM role and the custom policy attached to it for command consistency.  If you rename either the role, the custom policy, or both, you must also adjust dependent commands with the correct name of your choosing."
}
[/block]
### Create the Rapid7 Custom Policy

1. Open a terminal or command prompt.
2. Copy and run the following script to create the custom policy required by InsightVM:
[block:code]
{
  "codes": [
    {
      "code": "aws iam create-policy --policy-name Rapid7-Security-Audit --policy-document '{\n    \"Version\": \"2012-10-17\",\n    \"Statement\": [\n        {\n            \"Effect\": \"Allow\",\n            \"Action\": [\n                \"acm:ListTagsForCertificate\",\n                \"cloudtrail:ListPublicKeys\",\n                \"cloudtrail:ListTags\",\n                \"cloudtrail:GetTrailStatus\",\n                \"cloudtrail:GetEventSelectors\",\n                \"ecr:DescribeRepositories\",\n                \"ecr:GetLifecyclePolicy\",\n                \"ecr:GetRepositoryPolicy\",\n                \"ecr:ListImages\",\n                \"iam:GenerateServiceLastAccessedDetails\",\n                \"sqs:ListQueues\",\n                \"sqs:ListDeadLetterSourceQueues\",\n                \"sqs:ListQueueTags\",\n                \"sqs:GetQueueUrl\",\n                \"sqs:GetQueueAttributes\",\n                \"states:DescribeStateMachineForExecution\",\n                \"states:DescribeActivity\",\n                \"states:DescribeStateMachine\",\n                \"states:DescribeExecution\",\n                \"states:ListExecutions\",\n                \"states:GetExecutionHistory\"\n            ],\n            \"Resource\": \"*\"\n        }\n    ]\n  }'",
      "language": "json"
    }
  ]
}
[/block]
### Create the IAM role

1. Navigate to your InsightVM interface.  Click the **Management** tab in your left navigation menu.
2. On the “Settings” page, browse to the “Infrastructure” section.  Click **Add** next to “Amazon Web Services” to retrieve your External ID.
3. Return to your AWS CLI.  Copy the following script, but substitute the `<EXTERNAL-ID>` portion shown with the value you copied from InsightVM.
[block:code]
{
  "codes": [
    {
      "code": "aws iam create-role --role-name Rapid7-Security-Audit --assume-role-policy-document '{\n  \"Version\": \"2012-10-17\",\n  \"Statement\": [\n    {\n      \"Sid\": \"\",\n      \"Effect\": \"Allow\",\n      \"Principal\": {\n        \"AWS\": \"arn:aws:iam::336818582268:root\"\n      },\n      \"Action\": \"sts:AssumeRole\",\n      \"Condition\": {\n        \"StringEquals\": {\n          \"sts:ExternalId\": \"<EXTERNAL-ID>\"\n        }\n      }\n    }\n  ]\n}'",
      "language": "json"
    }
  ]
}
[/block]
4. With your External ID added to the previous script, run it in your terminal or command prompt to create the IAM role.

### Attach Policies

1. Run the following command to attach the default AWS “SecurityAudit” policy to your new IAM role:
[block:code]
{
  "codes": [
    {
      "code": "aws iam attach-role-policy --role-name Rapid7-Security-Audit --policy-arn arn:aws:iam::aws:policy/SecurityAudit",
      "language": "text"
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
      "language": "text"
    }
  ]
}
[/block]

[block:callout]
{
  "type": "success",
  "title": "IAM role creation complete",
  "body": "Now that your new IAM role is ready for use, proceed to the “[Complete the Connection in InsightVM](doc:infrastructure-assessment#section-complete-the-connection-in-insightvm)” section of this guide."
}
[/block]
# Complete the Connection in InsightVM

1. Return to the **Management** tab in your InsightVM interface.
2. Enter a name to describe your AWS account in the “Account Name” field.
3. Enter the ARN of the IAM role you just created in the “Role” field.  Click **Continue**.
4. Test the connection to verify the configuration is defined properly.
 * If the connection test fails, verify that you have completed the previous steps correctly according to your setup method of choice and try again.
5. Click **Save** when finished.
6. Click the **Infrastructure** tab on your left navigation menu to view your assessment data.
[block:callout]
{
  "type": "success",
  "title": "AWS connection complete!",
  "body": "InsightVM should now have a working connection to your AWS environment for the purpose of using Infrastructure Assessment."
}
[/block]