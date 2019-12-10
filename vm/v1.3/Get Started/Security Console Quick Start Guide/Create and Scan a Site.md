---
title: "Create and Scan a Site"
excerpt: ""
---
Now that you’ve [taken a tour of the Home page](doc:tour-the-home-page), it’s time to dive into the world of asset scanning.  In the course of this article, you’ll create and scan your first site and get a quick look at the results.

# Sites Explained

In InsightVM, a site is a collection of assets that are targeted for a scan.  While you can populate a site with any group of assets as you see fit, be mindful that conditions such as network bandwidth, latency, and the number of included assets ultimately affect scan efficiency.  In general, you should focus your site configurations based on this principle: efficient data collection.

# Objective

For the purpose of this guide, you will create a basic site that targets a single asset of your choice for an authenticated scan using the **Full Audit without Web Spider** template.
[block:callout]
{
  "type": "info",
  "title": "Why use authenticated scans?",
  "body": "Authentication provides the Scan Engine with significantly broader access to your asset in order to find vulnerabilities.  As a result, authenticated scans yield far more vulnerability results than unauthenticated scans.  If you really want to know how vulnerable your asset is, authentication is a must."
}
[/block]
Site configurations are feature rich.  Access control, tagging, and scheduling are only a few of the options available here, but you can explore these features later.  For now, let’s stick to the basics that a site needs to run a scan.

## Example Scan Targets

The following scan targets are good examples of possible assets to include in your first site:

* Your personal workstation
* A test or lab system (non-production)
* Any system for which you have administrator credentials

# Create Your First Site

From the **Home** page of your Security Console, click the **Create** dropdown and select **Site**.  The Security Console displays the “Site Configuration” screen.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/0cee7c8-securityconsole_site_config.png",
        "securityconsole_site_config.png",
        1780,
        807,
        "#afb4b8"
      ]
    }
  ]
}
[/block]
Site configuration options are organized into clickable tabs by category.  An orange bar above the tab title indicates that the configuration category is missing required information.

## “Info & Security”

On the **General** tab, name and describe your site.  While common names include department titles or office locations for the assets being scanned, you can name this site after your target asset or “sample site” for easy reference.

## “Assets”

The **Assets** tab is where you specify which of your assets should be included in the site, and if necessary, which should be excluded as well.  You can specify individual assets by their Fully Qualified Domain Name (FQDN) or IP address, but IP address ranges are the most effective method.  Site configurations accept a variety of IPv4 and IPv6 range notations, including Classless Inter-Domain Routing (CIDR).
[block:callout]
{
  "type": "info",
  "title": "TIP",
  "body": "To learn more about possible address range notation, see the [Adding assets to sites](doc:adding-assets-to-sites) page."
}
[/block]
For your first site, target your asset of choice by typing its IP address in the “Assets” field under “Include”.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/8105e22-securityconsole_site_config_asset.png",
        "securityconsole_site_config_asset.png",
        415,
        266,
        "#dde3e6"
      ]
    }
  ]
}
[/block]
## “Authentication”

The **Authentication** tab allows you to configure different sets of credentials depending on the type of asset you target for a scan.

### Configure Credentials

Click the **Add Credentials** tab to configure a set of credentials for your site to use:

1. On the** General **sub-tab, name and optionally describe your credentials.
 * This name will identify these credentials on the **Manage Authentication** tab when saved.
2. On the **Account** tab, select the authentication service you want to use.
[block:callout]
{
  "type": "info",
  "title": "TIP",
  "body": "While several options are available here for a variety of scenarios, Rapid7 recommends the following two services as a good starting point for authenticated scans:\n\n* **Microsoft Windows/Samba (SMB/CIFS)** for Windows machines\n* **Secure Shell (SSH)** for Linux and Mac machines\n\nYou can read more about authentication on the following pages:\n\n* [Authentication on Unix and related targets: best practices](doc:authentication-on-unix-and-related-targets-best-practices)\n* [Authentication on Windows: best practices](doc:authentication-on-windows-best-practices)"
}
[/block]
3. Complete the username and password fields as required.

### Test Your Credentials
[block:callout]
{
  "type": "warning",
  "title": "Always test your credentials before saving them!",
  "body": "Your scan will attempt to use your credentials upon initializing, but the scan will not stop if that authentication attempt fails.  As a result, a site with invalid credentials will return far fewer vulnerabilities.  Always test your credentials to make sure the Scan Engine can properly authenticate to your target asset."
}
[/block]
Site configurations include a built-in credential testing function:

1. On the **Add Credentials** tab, click the arrow next to **Test Credentials** to expand the dropdown.
2. Specify the IP address or FQDN of the asset you want to test against.
3. Specify the port number for your authentication service.
[block:callout]
{
  "type": "info",
  "title": "Default ports for SSH and SMB/CIFS",
  "body": "By default, InsightVM attempts SSH communication through port 22 and SMB/CIFS communication through port 445."
}
[/block]
4. Click **Test Credentials** when finished.

### Credential Test Results Explained

Successful credential tests show a green confirmation message.  Failed tests appear in red and may show the following text:

* **Invalid credentials** - Your username and/or password were incorrect.
* **Connection refused** - You specified the wrong port number, the port is not open on the host, or a firewall actively blocked the connection.
* **Host not found** - The IP address or FQDN specified was not found on the network.  This means that you entered the wrong address, the host network cannot be reached from the network subnet hosting the console, or the host is not connected.

After you’ve successfully tested your credentials, click **Create** to save them.

## “Templates”

Sites must be configured to use a specific Scan Template during the scanning process.  You can think of the Scan Template as the method by which the Scan Engine probes your assets.

On the **Select Scan Template** tab, select **Full Audit without Web Spider**.

Generally considered as the default Scan Template for the Security Console, **Full Audit without Web Spider** has the following traits:

* Performs only safe checks
* Looks for network-based vulnerabilities
* Checks for patches and hotfixes
* Audits at the application layer
* Scans only default ports

This template also excludes policy checking and web spidering, hence its name.  As a consequence, it’s fast, broadly scoped, and reliable.
[block:callout]
{
  "type": "info",
  "title": "TIP",
  "body": "You can read more about available Scan Templates from the [Scan Templates](doc:scan-templates) page."
}
[/block]
## “Engines”

In accordance with our [basic deployment plan](doc:basic-deployment-plan), this site should be configured to use the local Scan Engine.

On the **Select Scan Engine** tab, make sure the local Scan Engine is selected.  When you eventually have a deployment in place for production scanning, you can configure your sites with dedicated Scan Engines and engine pools from this same location.

# Save and Scan Your Site

You should now have all the information required for your first basic site.  Keep in mind that there are many other options for site configurations that were not covered here, but this basic configuration is suitable for your first scan.

Click **Save & Scan** in the upper right corner of your screen to save your site configuration and scan it immediately.
[block:callout]
{
  "type": "info",
  "title": "TIP",
  "body": "If you would like to learn more about site configuration capabilities, the [Site creation scenarios](doc:site-creation-scenarios) page is a good place to start."
}
[/block]
# Scan Progress

After initiating your first scan, the Security Console displays the site details page.  The “Scan Progress” section at the top gives you a live look at the progress of the ongoing scan as it runs.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/62109e3-securityconsole_scan_progress.png",
        "securityconsole_scan_progress.png",
        1749,
        304,
        "#e9eef1"
      ]
    }
  ]
}
[/block]
Upon completion, the “Scan Status” column displays “Completed successfully”.

# View Scan Results

Now that your first scan has completed, take a quick glance at the vulnerability results for your asset.

On the same site details page, browse to the “Completed Assets” section and click the address link for your asset.  The scanned asset detail view contains information about your asset, including the type of operating system its running, whether its a physical or virtual machine, and its calculated risk score.  Risk scores help you determine which vulnerabilities pose the most risk to your business so you can prioritize remediation accordingly.

You can also examine each individual vulnerability that was detected on the asset by browsing to the “Vulnerabilities” table.

Don’t get too overwhelmed by the findings!  Next, you’ll make this information more consumable by generating a report of these findings.
[block:callout]
{
  "type": "success",
  "title": "You’ve got your first vulnerability results!",
  "body": "You should now have a saved site configuration and your first scan results.  Undoubtedly, you’ll want to address these vulnerabilities as soon as possible, but first you need to turn these findings into actionable information. The Security Console offers a variety of report formats for your security team’s consumption.  Let’s generate a report now."
}
[/block]