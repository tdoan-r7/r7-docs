---
title: "Azure Security Center"
excerpt: ""
---
# Overview

Azure Security Center features an integration with the Rapid7 Insight Agent.  Configure this integration to make use of the following benefits:

* Automate the mass deployment of the Insight Agent across all your Azure virtual machines
* Assess the risk of these virtual machines with InsightVM
* View resulting assessment data from both Azure Security Center and your InsightVM dashboards

# Before you start

First, ensure that you meet the [system requirements](https://insightagent.help.rapid7.com/docs/requirements) for the Insight Agent.  Next, have the following resources open and available:

* Your **Dashboard** screen in InsightVM
* Your Microsoft Azure portal

# InsightVM: Download the configuration package and copy the public key

The configuration package contains the necessary Insight Agent configuration files and certificates required for deployment.

1. On the **Dashboard** screen of InsightVM, browse to (or add) either of the following cards:
 * “Assets with Agents by Operating System”
 * “Number of Assets with an Agent”
2. Once added, click **Manage Agents** on the card you’ve chosen.
3. In the upper-right corner of the card’s expanded view, click the **Download Agent** button.
4. Browse to the “Deploy Insight Agent from Microsoft Azure” section and click the **Get Package** button.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/accc494-VM_agent_package.png",
        "VM_agent_package.png",
        1131,
        241,
        "#27323d"
      ]
    }
  ]
}
[/block]
The `azure-config.zip` file will be downloaded to your system.
[block:callout]
{
  "type": "danger",
  "title": "IMPORTANT",
  "body": "Do not extract the `azure-config.zip` file.  It will be uploaded in ZIP form later."
}
[/block]
5. From this same screen, click **Get the Public Key**.
6. The “Azure Security Center Encoded Public Key” window will display.  Copy the key at this time.
[block:callout]
{
  "type": "info",
  "title": "What is the public key used for?",
  "body": "The public key generated here allows Azure to encrypt the data transmitted to InsightVM."
}
[/block]
# Azure Security Center: Configure a new vulnerability assessment solution

The package and public key saved previously will be used to complete the security solution configuration in Azure.

1. In your Azure portal, click **Security Center** on the left navigation menu.
2. Browse to the additional menu items under “Overview”.  Click **Recommendations** under “Resource Security Hygiene”.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/07e0125-azure_security_recommendations_nav.png",
        "azure_security_recommendations_nav.png",
        966,
        1254,
        "#8b8b8c"
      ]
    }
  ]
}
[/block]
3. In your listed recommendations, click **Add a vulnerability assessment solution**.
4. Specify which of your existing virtual machines will have the solution installed.  Click **Install on # VMs** when ready.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/5bda60d-azure_vm_select.png",
        "azure_vm_select.png",
        1160,
        494,
        "#c9cecf"
      ]
    }
  ]
}
[/block]
5. On the “Add a Vulnerability Assessment” window, click **Create New**.
6. Select **Rapid7** as the solution partner.  A vulnerability management configuration page will display.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/3549cd2-azure_r7config.png",
        "azure_r7config.png",
        622,
        1296,
        "#e7e8eb"
      ]
    }
  ]
}
[/block]
7. Under “Resource group”, select **Use existing**.  Specify the resource group from the dropdown list.
8. Under “Location”, specify your InsightVM region.
9. Under “Rapid7 Configuration File”, upload the `azure-config.zip` file you downloaded previously.
10. Under “Public key”, paste the key value you copied from InsightVM.
11. Specify “Auto deploy” as either **On** or **Off**.
[block:callout]
{
  "type": "info",
  "title": "TIP",
  "body": "If you choose to enable auto deployment, Azure Security Center will automatically deploy the Insight Agent to any newly discovered virtual machines that are not yet protected."
}
[/block]
12. Click **OK** when finished.

Your newly configured vulnerability assessment solution will now be installed on your target virtual machines, followed by data collection and assessment.

# View assessment data

In addition to your InsightVM dashboards, you can now view resulting vulnerability assessment data in Azure Security Center:

1. Return to your **Recommendations** page.  You will be alerted to new vulnerabilities detected by the Rapid7 solution that are affecting your virtual machines.
2. Click **Remediate Vulnerabilities - by a Vulnerability Assessment solution**.  A new window will display containing individual vulnerabilities organized by their severity.
[block:callout]
{
  "type": "info",
  "body": "Although the terminology is different, Azure Security Center follows the same vulnerability risk metrics as InsightVM.",
  "title": "Severity categorization"
}
[/block]
3. Click any of the listed vulnerability records to see additional details, remediation solutions, and affected virtual machines.

# Support

If you need assistance setting up the Azure Security Center integration, visit our [Support Portal](https://rapid7support.force.com/customers/login) or reach us via our [Contact](https://www.rapid7.com/contact/) page.