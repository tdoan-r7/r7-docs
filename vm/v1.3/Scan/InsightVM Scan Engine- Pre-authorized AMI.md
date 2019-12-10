---
title: "InsightVM Scan Engine: Pre-authorized AMI"
excerpt: ""
---
The InsightVM pre-authorized AWS scan engine Amazon Machine Image (AMI) provides an easy way to scan dynamic Elastic Compute Cloud (EC2) assets without requiring prior approval from AWS customer support. This allows you to understand and manage risk associated with your dynamic EC2 assets by quickly deploying the Nexpose pre-authorized Scan Engine via the Amazon Web Services (AWS) Marketplace.

Once you create an AWS connection (see [Installing, Configuring and Using](doc:insightvm-scan-engine-pre-authorized-ami#section-installing-configuring-and-using)), the console pulls a list of EC2 instances via the AWS API.  The engine scans these instances for vulnerabilities using a combination of port scans, service detection, unauthenticated checks and authenticated checks.  Because the engine is pre-authorized by AWS, this normally suspicious traffic is allowed to occur between your EC2 instances without the need to fill out a separate form.

##Dependencies

Before deploying the pre-authorized engine, you must deploy and license a InsightVM console. 

When launching the scan engine AMI, you must pair the engine to the console.  The console and the engine are both hosted by the customer.  This means the console location will vary by customer.  Because the engine does not have any user accessible interface, you must provide console information to the engine when launching the AMI.   This is done using EC2 user data (see [Installing, Configuring and Using](doc:insightvm-scan-engine-pre-authorized-ami#section-installing-configuring-and-using)).

You must have an EC2 VPC populated with some virtual machines to be scanned.

If your console is hosted within AWS, you can assign an IAM role to the instance. Otherwise, you will need to provide IAM credentials. See [Managing dynamic discovery of assets](doc:managing-dynamic-discovery-of-assets). 

The console must allow access on TCP port 40815 from the engine.

The engine does not need to allow new inbound connections, but it must be able to establish outbound communication to port 40815 on the console.  For accurate scan results, the engine should allow unfiltered communication on all ports with instances in the VPC over their private IP addresses. 

##Known Constraints

By design, the pre-authorized engine is only allowed to scan assets in a single VPC.  The customer is expected to deploy multiple pre-authorized engines if they wish to scan multiple VPCs.  If the customer wishes to scan non-AWS assets, they are expected to deploy engines outside of AWS.

InsightVM currently does not scan some smaller instances due to AWS limitations. These instances may appear in the discovery results, but Amazon currently does not permit scanning them.

##Installing, Configuring and Using

##Preparing the InsightVM console and your AWS environment

1. Prepare your AWS environment. See [Discovering Amazon Web Services instances](doc:discovering-amazon-web-services-instances).
2. The console needs to accept incoming connections on port 40815 from the engine.
  * Modify your console EC2 security groups or your firewall to allow this.
3. Create an Amazon Web Services connection. See [Creating and managing Dynamic Discovery connections](doc:creating-and-managing-dynamic-discovery-connections).
4. Make sure you have your InsightVM console IP address or hostname and your InsightVM console port ready.
5. You will need to generate a shared secret. You can do this at the beginning of the setup process, or wait, since there is a 60 minute time period that the shared secret is valid.

##Access the Pre-Authorized Rapid7 VM Scan Engine on the Amazon Web Services Marketplace

The first step is to access the Pre-Authorized Rapid7 VM Scan Engine from the Amazon Web Services Marketplace.

1. Access the Amazon Web Services Marketplace.
2. Search for "Rapid7 VM Scan Engine (Pre-authorized)".
 * You can also access the listing directly from this location: https://aws.amazon.com/marketplace/pp/B07MFM8XLB.
3. Click **Continue**.
4. On the _Launch on EC2_ page, select the **Manual Launch** option.
5. Review the terms of service and accept the terms. Wait to receive subscription confirmation from Amazon Web Services. You may need to reload the page.

##Generate a shared secret on the InsightVM console

1. Generate a shared secret on the console that will be used to pair the engine.
  a. On the InsightVM console, navigate to **Administration** -> **Scan Options** -> **Engines** -> **Manage**.
  b.Generate a new shared secret at the bottom of the page.
  c. The shared secret expires in 60 minutes. After that time, you can generate a new one.

##Launch the InsightVM engine AMI on the Amazon Web Services Marketplace

1. Select a region.
2. Select **Launch with EC2 console**.
3. Choose an instance type. m4.large or higher is recommended.
4. Proceed to configure instance details.
5. Configure where the instance will launch.
6. Generate a shared secret from your InsightVM console if you have not done so already. See [Generate a shared secret on the InsightVM console](doc:insightvm-scan-engine-pre-authorized-ami#section-generate-a-shared-secret-on-the-insightvm-console).
7. Expand **Advanced Details**.
8. You must provide the following user data. Replace the bracketed section <> with information about your console:
```
NEXPOSE_CONSOLE_HOST=<hostname or ip of your console>
NEXPOSE_CONSOLE_PORT=40815
NEXPOSE_CONSOLE_SECRET=<shared secret generated earlier>
```
9. We recommend at least 8 GB of RAM and at least 100 GB of disk space.
10. The security group must prevent all inbound access.  It must allow outbound access to port 40815 on your console.  It must allow outbound access to ports 80 and 443 on the internet for automatic updates.  It should allow outbound access to all ports on potential scan targets.
11. Launch the instance.
12. Once the image boots, it can take up 10-15 minutes to pair with the console.
13. Verify the engine pairs with the console via the engine listing in the console (**Administration** -> **Scan Options** -> **Engines** -> **Manage**).

##Troubleshooting

The AWS pre-authorized scan engine does not allow interactive logins.

* You can check the AWS instance system log for errors related to the user data you provided.
[block:callout]
{
  "type": "warning",
  "body": "AMIs launched into EC2 classic will be automatically shut down shortly after booting."
}
[/block]
To troubleshoot, use the AWS console to view the system log

1. Go to the EC2 console
2. View instances
3. Select the pre-authorized scan engine instance you created earlier
4. Select **Actions** -> **Image Settings** -> **Get System Log**.
5. Look for messages that start with _pair-nexpose-engine_.

##Scan and Review

Once you have your AWS pre-authorized Scan Engine set up, you can begin using it to scan your AWS assets. The following is a brief overview of where the appropriate settings are found in the InsightVM console configuration.

1. Create an Amazon Web Services connection. Select the **Security Console and Scan Engine are inside AWS network** checkbox. See [Creating and managing dynamic discovery connections](doc:creating-and-managing-dynamic-discovery-connections).
2. Create a site. See [Creating and editing sites](doc:creating-and-editing-sites).
 * Specify assets by **Connection**. Specify the connection you created in Step 1.
 * Select the engine you created earlier. It should be visible by its EC2 private DNS name, for example ip-172.31.2.3.us-east-1.compute.internal.
3. Scan the site.
4. Review the results. See [Act](doc:act).