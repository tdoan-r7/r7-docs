---
title: "Activating your console on the Insight platform"
excerpt: ""
---
InsightVM license holders can opt in to take advantage of powerful capabilities available only in the Rapid7 Insight platform.  These capabilities include:

## Dashboards

* Build customizable, data-driven interfaces in order to continuously monitor your security environment from a compact, informative space.
* Make use of specialized **cards** to show data in a way that is most meaningful to your organization.
* Choose from a variety of Rapid7 templates, such as _Assets_, _Remediations_, and _Exploitable Vulnerability_ builds, or create and configure your own.

## Projects

* Create, assign, monitor, and automate ticketing for remediation projects using **Remediation Workflow**.
* Define the scope of both static and dynamic remediation projects by implementing asset filters based on risk score, exploitability, and other metrics.
* Make use of various ticketing integrations so that priority remediation tasks can be automatically assigned.
* The **Projects** interface provides a centralized location for tracking the progress of all remediation tasks that are ongoing throughout your organization.

## Containers

* Monitor risk assessment for all images that are running containers in your environment from the **Containers** interface.
* Sort your images in a variety of ways, including by creation date, risk score, the number of vulnerabilities found, and the number of hosts associated with each.
* Manage container registry connections and search for repositories from the **Repositories** table view.

# What is the Insight platform?

The Insight platform is a cloud-based security data collection and processing infrastructure.  All Rapid7 Insight products use this data to help your organization achieve its security goals.  The advent of the cloud is what makes some of InsightVM’s more robust features possible.

You can learn more about the Insight platform in the following articles:

* [https://www.rapid7.com/products/insight-platform/](https://www.rapid7.com/products/insight-platform/)
* [https://www.rapid7.com/trust](https://www.rapid7.com/trust)

The **Dashboard**, **Projects**, **Containers**, and **Management** interfaces are only accessible to organizations that have activated their Security Console on the Insight platform.
[block:callout]
{
  "type": "warning",
  "title": "Whitelist requirements",
  "body": "You may need to configure whitelisting for outbound traffic in order to upload data to the Insight platform.  See [Configure communications with the Insight platform](doc:configure-communications-with-the-insight-platform) for details."
}
[/block]
# Activation Process

Before triggering the activation wizard, you must elect to use the Insight platform.

In the Security Console, click or hover your mouse cursor over the menu stack in the upper left corner of the screen:

1. Click the **Administration** tab.
2. Browse to the _Global and Console Settings_ window.  Next to **Console**, click **Administer**.
3. _The Security Console Configuration_ screen will be shown.  Click the **Insight Platform** tab.
4. Enable the **Use Insight Platform** radio button.
5. Click **Save**.

Your Security Console will now be able to communicate with the Insight platform.  The activation wizard can be triggered by clicking any of the following tabs:

* **Dashboard**
* **Projects**
* **Containers**
* **Management**

You will be prompted with a welcome message.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/e840a08-Insight_Platform_1.png",
        "Insight_Platform_1.png",
        1600,
        557,
        "#26292a"
      ]
    }
  ]
}
[/block]
Click **Next**.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/4169aec-Insight_Platform_2.png",
        "Insight_Platform_2.png",
        1600,
        718,
        "#27292a"
      ]
    }
  ]
}
[/block]
Click **Next**.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/033340a-Insight_Platform_3.png",
        "Insight_Platform_3.png",
        1600,
        711,
        "#252828"
      ]
    }
  ]
}
[/block]
Give your Security Console a name.  The console’s name will serve as its unique identifier.  This will allow your organization to sort scan data by the Security Console that collected it.

Once you've named the console, click **Next**.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/c87f874-Insight_Platform_4.png",
        "Insight_Platform_4.png",
        1600,
        716,
        "#242627"
      ]
    }
  ]
}
[/block]
Select the cloud data location from the options shown.  Once you’ve made your selection, click **Next**.

It may take a few moments for the connection to complete.  Once completed, dashboards, remediation workflow, and container assessment features will be available for use.