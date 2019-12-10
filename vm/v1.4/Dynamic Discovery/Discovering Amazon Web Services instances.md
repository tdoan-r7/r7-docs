---
title: "Discovering Amazon Web Services instances"
excerpt: ""
---
If your organization uses Amazon Web Services (AWS) for computing, storage, or other operations, Amazon may occasionally move your applications and data to different hosts. By initiating Dynamic Discovery of AWS instances, you can scan and report on these instances on a continual basis. The connection occurs via the AWS API.

In the AWS context, an *instance* is a copy of an Amazon Machine Image running as a virtual server in the AWS cloud. The Security Console correlates assets based on instance IDs. If you terminate an instance and later recreate it from the same image, it will have a new instance ID. That means that if you scan a recreated instance, the scan data will not be correlated with that of the preceding incarnation of that instance. The results will be two separate instances in the scan results.

The Security Console has **two connection types** that can help discover your AWS instances:

* *[Amazon Web Services Asset Sync](doc:discovering-amazon-web-services-instances#section-amazon-web-services-asset-sync)* allows you to import AWS assets from one or more accounts into a pre-existing **static** site. The discovery of assets happens automatically, without the need to run a vulnerability scan in your AWS environment. The Amazon Web Services Asset Sync connection imports instance tags from AWS and associates them as custom tags on your assets. This allows you to port your instance grouping logic from AWS into the Security Console, and to create Asset Groups based on AWS tags. Tags imported from AWS are always prefixed with Amazon-web-services, making them easily identifiable.
With this connection, you can also leverage the AWS AssumeRole functionality in order to reuse credentials across multiple accounts.
[block:callout]
{
  "type": "info",
  "body": "_Amazon Web Services Asset Sync_ is the newer and **recommended** connection type for AWS dynamic discovery.\n\nFollow [these steps](doc:creating-and-managing-dynamic-discovery-connections#section-adding-an-amazon-web-services-asset-sync-connection) to create an _Asset Sync_ connection."
}
[/block]

[block:callout]
{
  "type": "info",
  "title": "NOTE",
  "body": "Each Amazon Web Services Asset Sync connection can support up to 1000 Amazon Resource Names (ARNs) for discovery across AWS accounts."
}
[/block]
* *[Amazon Web Services (legacy)](doc:amazon-web-services#section-aws-legacy-connection)* requires you to create and scan a **dynamic** site in order to discover your EC2 instances. Since this connection imports all your instances from AWS every couple of minutes, it is more resource-intensive than the AWS Asset Sync connection.
[block:callout]
{
  "type": "warning",
  "body": "This original _Amazon Web Services_ connection type is now a **legacy** connection.  _Amazon Web Services Asset Sync_ is preferable for AWS dynamic discovery."
}
[/block]
# Preparing for Dynamic Discovery in an AWS environment

Before you initiate Dynamic Discovery and start scanning in an AWS environment, you need to:

* be aware of how your deployment of the Security Console components affects the way Dynamic Discovery works
* create an AWS IAM user or IAM role
* create an AWS policy for your IAM user or IAM role

# Inside or outside the AWS network

When configuring your AWS connection, you can specify whether:

* your Security Console is inside the AWS network
* your Scan Engine is inside the AWS network

These configurations determine which additional settings and configurations you will need.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/5d3b4d5-s_nx_dynamic_discovery_vsphere_assets_filtered.jpg",
        "s_nx_dynamic_discovery_vsphere_assets_filtered.jpg",
        2058,
        1168,
        "#202b3a"
      ],
      "caption": ""
    }
  ]
}
[/block]
# Outside the network: Creating an IAM user

If your Security Console is located outside the AWS network, the AWS Application Programming Interface (API) must be able to recognize it as a trusted entity before allowing it to connect and discover AWS instances. To make this possible, you will need to create IAM user, which is an AWS identity for the Security Console, with permissions that support Dynamic Discovery. When you create an IAM user, you will also create an access key that the Security Console will use to log onto the API.


Learn about [IAM users](http://docs.aws.amazon.com/IAM/latest/UserGuide/id.html) and how to [create them](http://docs.aws.amazon.com/IAM/latest/UserGuide/id_users_create.html).
[block:callout]
{
  "type": "warning",
  "body": "When you create an IAM user, make sure to select the option to create an access key ID and secret access key. You will need these credentials when setting up the discovery connection. You will have the option to download these credentials. Be careful to download them in a safe, secure location.\n When you create an IAM user, make sure to select the option to create a custom policy."
}
[/block]
# Inside the network: Creating an IAM role

If your Security Console is installed on an AWS instance and, therefore, inside the AWS network, you need to create an IAM role for that instance. A role is simply a set of permissions. You will not need to create an IAM user or access key for the Security Console.

Learn about [IAM users](http://docs.aws.amazon.com/IAM/latest/UserGuide/id.html) and how to [create them](http://docs.aws.amazon.com/IAM/latest/UserGuide/id_users_create.html).

**Note:** When you create an IAM role, make sure to select the option to create a custom policy.

# Creating a custom policy for your IAM user or role
When creating an IAM user or role, you have to apply a policy to it, which defines your permissions within the AWS environment. Amazon requires your AWS policy to include minimal permissions for security reasons. To meet this requirement, select the **Create a custom policy** option.
You can create the policy in JSON format using the editor in the AWS Management Console. 

# Amazon Web Services Asset Sync
[block:callout]
{
  "type": "warning",
  "title": "NOTE - Connectivity requirements",
  "body": "You must allow your Security Console to establish TCP connections to your EC2, STS, and CloudTrail endpoints for the Asset Sync discovery connection to function properly. Check the following \"AWS Regions and Endpoints\" document to find the endpoint URLs that correspond to the region where your Amazon services are hosted:\n\nhttps://docs.aws.amazon.com/general/latest/gr/rande.html"
}
[/block]
The AWS Asset Sync connection uses the AWS EC2 Describe functionality to initially discover assets, and then monitors AWS CloudTrail logs to detect any changes in the environment. In order to use this connection, your IAM user or role should have access to certain CloudTrail and EC2 functionalities. The following is an example of a policy with these permissions:
```
{
  "Version": "2012-10-17",
  "Statement": [{
    "Effect": "Allow",
    "Action": [
      "cloudtrail:LookupEvents",
      "cloudtrail:DescribeTrails"
     ],
     "Resource": "*"
   },
   {
     "Effect": "Allow",
     "Action": [
       "ec2:DescribeInstances",
       "ec2:DescribeImages",
       "ec2:DescribeAddresses",
       "ec2:DescribeNetworkInterfaces"
     ],
     "Resource": "*"
  }]
}
```
Users of the AWS Asset Sync connection can leverage *AWS AssumeRole* to decide which assets across all their AWS accounts to include in a single site. AssumeRole is available to Security Consoles within and outside of the AWS environment. To use STS AssumeRole the user must also have a policy similar to the following:
```
{
  "Version": "2012-10-17",
  "Statement": {
    "Effect": "Allow",
    "Action": "sts:AssumeRole",
    "Resource": "arn:aws:iam::ACCOUNT-ID-WITHOUT-HYPHENS:role/Test*"
  }
}
```
If you are using STS Assume Role in a cross-account scenario, the role in the secondary account will need the EC2:Describe policy, the CloudTrail policy, and a trust relationship with the principal account. More information about using STS Assume Role for cross-account access can be found in the AWS documentation [here](http://docs.aws.amazon.com/IAM/latest/UserGuide/id_roles_use_permissions-to-switch.html) and [here](http://docs.aws.amazon.com/IAM/latest/UserGuide/id_roles_common-scenarios_aws-accounts.html).

# Scan Engine inside or outside AWS network

It is a best practice to scan AWS instances with a distributed Scan Engine that is deployed within the AWS network, also known as the Elastic Compute Cloud (EC2) network. This allows you to scan private IP addresses and collect information that may not be available with public IP addresses, such as internal databases.

If your Scan Engine is inside the AWS network, the Security Console will discover and scan assets using their private IPs.
[block:callout]
{
  "type": "warning",
  "body": "If the private IP space in your AWS network overlaps with the private IP space in your corporate network, some assets in AWS may share the same IP address as assets in your corporate network."
}
[/block]
If your Scan Engine is outside the AWS network, the Security Console will only scan assets with Elastic IP (EIP) addresses assigned to them. The Security Console will use these EIPs when scanning. You will not be able to manually edit the asset list in your site configuration or in a manual scan window. Dynamic Discovery will include instances without EIP addresses, but they will not appear in the asset list for the site configuration.