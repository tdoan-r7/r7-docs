---
title: "Amazon Web Services (AWS)"
excerpt: ""
---
* [Getting started with AWS and InsightVM](doc:amazon-web-services#section-getting-started-with-aws-and-insightvm)
* [Cross-Account Asset Import and Scanning](doc:amazon-web-services#section-cross-account-asset-import-and-scanning)
* [VPC Peering](doc:amazon-web-services#section-vpc-peering)
* [Creating a connection](doc:amazon-web-services#section-creating-a-connection)

InsightVM users are able to deploy their scan engines to scan their AWS assets, with the option of using a pre-authorized Scan Engine or a regular Scan Engine. Customers can run a security console in AWS or on-premise. One or more Scan Engines can pair with the console and perform vulnerability scans. 
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/1088436-Diagram_AWS_Arch_Flow_Engine_Deployment.jpg",
        "Diagram AWS Arch Flow Engine Deployment.jpg",
        6392,
        5858,
        "#ecf0f2"
      ]
    }
  ]
}
[/block]

[block:api-header]
{
  "type": "basic",
  "title": "Getting started with AWS and InsightVM"
}
[/block]
There are two options for using InsightVM and AWS: Pre-Authorized Scan Engine or Regular Scan Engine. 

A pre-authorized scan engine does not require authorization from AWS to scan and allows users immediate access to scan. However certain restrictions in the security console apply, including:

  * Assets must be discovered through the Amazon EC2 API, therefore you cannot deploy a network scan
  * You will not be allowed interactive access to the scan engine (e.g. ssh, RDP, etc.)
  * You can only scan within peered or globally routable VPCs, you cannot scan the internet
  * No support for EC2 Classic

A regular scan engine requires authorization and compliance with AWS. Receiving authorization from AWS can take up to 72 hours and must be renewed every 90 days after creating a connection. InsightVM imposes no restrictions on the scan engine however you must still abide by AWS terms. More information can be found at https://aws.amazon.com/security/penetration-testing/.

## Configuring your AWS Environment with InsightVM

Creating EC2 Security Groups for InsightVM
We recommend creating two security groups: one for the scan engine and one for the scan targets.  The scan target security group should be attached to every EC2 asset you wish to scan.

1. From your AWS Management Console, click on the All Services or Services drop-down arrow.
2. Under the Compute category, click EC2. This will display the EC2 Console page.
3. In the Resources area, click Security Groups.
4. Click Create Security Group. This will display a Create Security Group pop-up window.

## Creating a Scan Engine Security Group
1. Create a name for your security group by typing in the Security Group Name field. Including “scan-engine” in the name would be helpful for differentiating between security groups.
2. Create a description for your security group is optional however, it may be beneficial if there are multiple users using this group.
3. Select the VPC your security console belongs to from the drop-down menu. This security group should have no incoming rules. However, you may create outbound rules that allow the scanner to scan the network ranges that you are deploying instances to.
4. Click **Create**.

## Creating Scan Targets Security Group
1. Create a name for your security group by typing in the Security Group Name field. Including “scan-targets” in the name would be helpful for differentiating between security groups.
2. Create a description for your security group is optional however, it may be beneficial if there are multiple users using this group.
3. Select the VPC your security console belongs to from the drop-down menu. 
4. Under Security Group Rules, select Inbound and click Add Rule. 
5. Under the Type column, select All traffic from the drop-down menu.
6. Under the Source column, select Custom from the drop-down menu and type in the Group ID of your Scan Engine Security Group.
7. Click create.

## Creating an IAM User or Role
It is necessary to create either an IAM User or Role in order to give the security console access to your EC2 API. If your security console is running inside of AWS, you should create an IAM Role and attach it to the console via an instance profile. If your security console is running outside of AWS, you should create an IAM User.
[block:callout]
{
  "type": "info",
  "body": "If the \"Console Inside AWS\" option is checked when the AWS Asset Sync discovery connection is created it will use the instance profile.",
  "title": "Note"
}
[/block]
You must attach an IAM policy to your IAM user or role that allows InsightVM to list EC2 instances and monitor CloudTrail for instance related events. A minimal policy to allow this looks like this:
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
       "ec2:DescribeAddresses"
     ],
     "Resource": "*"
  }]
}
```
For more information on creating a user, see http://docs.aws.amazon.com/IAM/latest/UserGuide/getting-started_create-admin-group.html

For more information on creating a role, see http://docs.aws.amazon.com/IAM/latest/UserGuide/id_roles_create.html 

[block:api-header]
{
  "title": "Cross-Account Asset Import and Scanning"
}
[/block]
If you have multiple accounts that you would like to import assets from you can provide role ARN(s) from those accounts, and optionally a session name, when creating the AWS Asset Sync discovery connection. More information about using STS Assume Role for cross-account access can be found in the AWS documentation [here](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_roles_use_permissions-to-switch.html) and [here](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_roles_common-scenarios_aws-accounts.html). 

In order to scan across accounts using the pre-authorized engine, the VPC where the engine and the target assets are located must be peered.

[block:api-header]
{
  "title": "VPC Peering"
}
[/block]
Through the pre-authorized scan engine InsightVM supports scanning multiple peered VPCs. However, if your AWS environment does not use VPC peering you must define separate InsightVM Asset Groups and a Static Site that uses that asset group for each VPC. The AWS Asset Sync connection automatically tags assets with a VPC tag (even if the "Import Tags" option is unchecked) which you can use to create these Asset Groups.
[block:callout]
{
  "type": "info",
  "title": "Note",
  "body": "A single pre-authorized engine can be associated with multiple peered VPCs. If VPCs are not peered, a scan engine must be deployed to each VPC."
}
[/block]
If you've imported assets from multiple accounts, you will need to peer the VPCs between accounts. See the AWS documentation [here](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/peer-with-vpc-in-another-account.html).

## Generating a Scan Engine Shared Secret
A scan engine shared secret is generated to pair the engine with the console.
1. From InsightVM, navigate to the Administration page.
2. In the Scan Options section, locate Engines and click Manage.
3. Scroll to the Generate Scan Engine Shared Secret.
4. Click Generate.
[block:callout]
{
  "type": "info",
  "title": "Note",
  "body": "The shared secret expires in 60 minutes. After that time, you can generate a new one."
}
[/block]
## Pairing Sites and New Scan Engines with EC2 User Data
It is required to launch a pre-authorized scan engine with user data in order for your engine to be properly paired to your console. Before launching a pre-authorized scan engine, you must deploy and license a security console.

1. Create a temporary Scan Engine Shared Secret for your VPC. The shared secret expires in 60 minutes. After that time, you can generate a new one.
2. From Rapid7 VM Scan Engine page in the AWS Marketplace (https://aws.amazon.com/marketplace/pp/B01CBHJL4K), click Continue to begin launching the pre-authorized engine.
3. Click on the Launch drop-down arrow and locate the region you will be launching from. 
4. Click Launch with EC2 Console. 
5. This will display the Choose an Instance Type page. Generally, it is recommended to select a m4.xlarge or larger instance type, but any instance that meets our minimum system requirements is acceptable. For more information on our system requirements, see https://www.rapid7.com/products/insightvm/system-requirements/. Click Next: Configure Instance Details.
6. This will display the Configure Instance Details page. After filling out your instance details, scroll to find Advanced Details and click the drop-down arrow to expand the section. Provide the following EC2 user data, replacing the bracketed information with information for your InsightVM console:


```
NEXPOSE_CONSOLE_HOST=<hostname or ip of your console>
NEXPOSE_CONSOLE_PORT=40815
NEXPOSE_CONSOLE_SECRET=<shared secret generated earlier>
```


7. Finish launching the EC2 instance as normal. Note that it can take up to 15 minutes for the Scan Engine to pair with the Console.
8. Create a new InsightVM Site for the AWS account. Proceed in creating your Site as normal. When you get to Assets, click Connection to specify your assets by.
9. Select AWS from the Connection drop-down option menu.
10. Navigate to and click on Create Connection section. 
11. From the Connection Type drop-down menu, select Amazon Web Services. 
12. Give your connection a name.
13. Select the Region that you launched your EC2 console from.
14. Select whether your Console and Scan Engine are located inside AWS. If you are launching a pre-authorized Scan Engine you must select Scan Engine is Inside AWS.
15. Provide your IAM User data or AWS Connection Settings, depending on the option selected in the previous step. It is required to use user data in order for your account to be properly paired.
16. Finish creating a new InsightVM Site as normal. Once completed, the engine and site are now paired.
[block:api-header]
{
  "title": "Creating a connection"
}
[/block]
Before starting the connection creation steps, see [Discovering Amazon Web Services Instances](doc:discovering-amazon-web-services-instances) for important configuration information.

When you’re ready to create a connection, see [Creating and managing Dynamic Discovery connections](doc:creating-and-managing-dynamic-discovery-connections) and browse to the [Amazon Web Services Asset Sync](doc:creating-and-managing-dynamic-discovery-connections#section-adding-an-amazon-web-services-asset-sync-connection) section.
[block:callout]
{
  "type": "info",
  "title": "NOTE",
  "body": "_Amazon Web Services Asset Sync_ is the newer, preferred connection type.  The original _AWS_ connection type is now a legacy connection."
}
[/block]
## AWS legacy connection

The AWS legacy connection will only use the EC2 Describe capabilities, and the following code sample indicates how the policy should be defined: 
```
{
  "Version": "2012-10-17",
  "Statement": [{
     "Effect": "Allow",
     "Action": [
       "ec2:DescribeInstances",
       "ec2:DescribeImages",
       "ec2:DescribeAddresses"
     ],
     "Resource": "*"
  }]
}
```