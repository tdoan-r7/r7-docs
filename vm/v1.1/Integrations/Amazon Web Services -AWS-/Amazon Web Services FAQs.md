---
title: "Amazon Web Services FAQs"
excerpt: ""
---
## Is an AMI scan engine required in each VPC, or can a scan engine in another VPC be routed to cover many VPCs?

A single engine can scan multiple peered VPCs. If VPCs are not peered, a scan engine must be deployed to each VPC. The pre-authorized scan engine can only scan private IPs associated with EC2 instances. Private IPs are only available/routable inside a VPC or across peered VPCs.
 
## Can an AMI scan engine be used to scan out, for externally facing on-premises assets? Can it be routed out to scan the elastic IP of AWS assets from an external perspective?

No, the pre-authorized scan engine can only scan private IPs associated with EC2 instances. Scanning external non-AWS IPs, or public AWS IPs (including elastic IPs and ELBs) is not allowed due to Amazon’s pre-authorization guidelines. Users wishing to scan external assets from an AWS-based scan engine can deploy a regular scan engine and obtain permission via Amazon’s Simulated Event Testing process (https://aws.amazon.com/security/penetration-testing).
 
## Is it possible to initiate an ad hoc scan by IP against an AWS host using an AMI engine?

No, Amazon’s pre-authorized guidelines require assets to be discovered by the AWS EC2 API, and prohibit the user from specifying a scan target by IP address. Users wishing to scan assets by specifying IP addresses via an AWS-based scan engine can deploy a regular scan engine and obtain permission from Amazon’s Simulated Event Testing process (https://aws.amazon.com/security/penetration-testing).
 
## Are there any restrictions in the methods used to authenticate to the Amazon API?

No, InsightVM can authenticate with the AWS EC2 API via IAM credentials (access key and secret access key) or IAM roles. The security console authenticates with the EC2 API, not the Scan Engine, so IAM roles can only be used if the console is hosted in AWS.

## Can the Scan Engine scan small or micro instances?

Amazon’s pre-authorized guidelines prohibit scanning m1.small, t1.micro and t2.nano instances to minimize impact on other AWS users. The pre-authorized Scan Engine is permitted to scan t2.micro and t2.small instances.
 
## Is there any way to get a different size instance for the certified AMI?

Yes, users are able to deploy the pre-authorized Scan Engine to any EC2 instance size that meets the Scan Engine’s system requirements (specifically 8GB of RAM). AWS often releases new instance types that may not be whitelisted for the Scan Engine. Rapid7 normally whitelists new instance types each time we publish an update to the AWS Marketplace. Please contact Rapid7 Support to request a new instance size.
 
## How many API calls does the discovery connection make? Are the engines making API calls?

The discovery connection only calls the ec2:DescribeInstances, ec2:DescribeImages and ec2:DescribeAddresses API resources. It may make multiple calls to these APIs depending on the number of discovered assets. The console makes API calls, not the scan engine.
 
##What is the process for authorization if users install their own engine?

Users who install their own engine should follow the Simulated Event Testing process documented at https://aws.amazon.com/security/penetration-testing/. Specifically, the user will need to submit a Penetration Testing Request Form to AWS with the EC2 instance ID of the Scan Engine and the IP range that will be scanned. AWS typically responds to this form within 2 business days and allows scanning for up to 90 days.
 
## Are there any other options for the certified AMI, such as different size instances?

The pre-authorized AMI is able to run on any instance size that meets the Scan Engine’s system requirements (specifically 8GB of RAM). There are no other options at this time.
 
## Are there any other restrictions that aren’t obvious from the implementation?

As part of the pre-authorized vulnerability scanning policies from Amazon, the Scan Engine AMI has two basic restrictions compared to regular Scan Engines:
1. It must only scan assets returned via the EC2 API within a single VPC or multiple peered VPCs
2. It must not allow the user to execute arbitrary code or accept incoming connections. This means users may not SSH into the Scan Engine, and the Scan Engine must initiate communication with the Console.