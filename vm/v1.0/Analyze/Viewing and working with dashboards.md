---
title: "Viewing and working with dashboards"
excerpt: ""
---
Dashboards provide visibility into assets, vulnerabilities, remediations, scans, and software found by InsightVM. At a glance, you can get a dynamic and detailed picture of the aspects of your security landscape that are most important to you.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/dd76ab7-default-dashboard.png",
        "default-dashboard.png",
        1574,
        910,
        "#3f4854"
      ]
    }
  ]
}
[/block]
##Creating a new dashboard

To add a new, blank dashboard, click the **downward-facing arrow** next to the name of the dashboard you are currently viewing, then click the first item on the list, **Create a New Dashboard**.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/fbd834e-create-dashboard.png",
        "create-dashboard.png",
        643,
        100,
        "#3c444f"
      ]
    }
  ]
}
[/block]
Add a name (required) and a description (optional) for the new dashboard, then click **OK**.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/40ad8c9-add-dashboard.png",
        "add-dashboard.png",
        601,
        273,
        "#46505e"
      ]
    }
  ]
}
[/block]
Your dashboard will be added and ready to use.

##Creating a dashboard from a template

In addition to the ability to add a blank new dashboard, there are several built-in options for dashboards that can be added. These dashboard templates can be viewed, searched for, and added under the _Dashboard Library_ menu. To access the _Dashboard Library_ menu, click the **downward-facing arrow** next to the name of the dashboard you are currently viewing, then click the last item on the list, **See More in the R7 Library**.

* [Asset](doc:viewing-and-working-with-dashboards#section-asset)
* [Vulnerability](doc:viewing-and-working-with-dashboards#section-vulnerability)
* [Threat Feed](doc:viewing-and-working-with-dashboards#section-threat-feed)
* [Containers](doc:viewing-and-working-with-dashboards#section-containers)
* [Remediations](doc:viewing-and-working-with-dashboards#section-remediations)
* [Samba](doc:viewing-and-working-with-dashboards#section-samba)
* [WannaCry](doc:viewing-and-working-with-dashboards#section-wannacry)
* [Petya-like Ransomware](doc:viewing-and-working-with-dashboards#section-petya-like-ransomware)
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/b6a444d-Rapid7_Exposure_Analytics.png",
        "Rapid7_Exposure_Analytics.png",
        1068,
        731,
        "#465260"
      ]
    }
  ]
}
[/block]
There, you will be able to add a new dashboard using the template of your choice by clicking the **Add** button for that template. Add a name (required) and a description (optional) for the new dashboard, then click **OK**. Your dashboard will be added and ready to use.

##Asset
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/80465ed-Asset-Dashboard.png",
        "Asset-Dashboard.png",
        1313,
        784,
        "#3f4855"
      ]
    }
  ]
}
[/block]
These dashboards give an overview of all the Assets found in your Sites, including such information as environment status, freshness of asset data, changing risk in assets, and prioritization of assets. There are three such templates for you to choose from.

##Vulnerability
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/afce5f6-Vulnerability-Dashboard.png",
        "Vulnerability-Dashboard.png",
        1303,
        785,
        "#3e4754"
      ]
    }
  ]
}
[/block]
These dashboards provide an overview of all the vulnerabilities in your environment, including what is exploitable, changes in threat exposure, and slicing-and-dicing of vulnerability data. There are two templates in this category.

##Threat Feed
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/05dec56-threat_feed.png",
        "threat_feed.png",
        1600,
        821,
        "#3e4753"
      ]
    }
  ]
}
[/block]
This dashboard presents data collected from Rapid7 Threat Feed sources and shows which assets in your network have certain vulnerabilities - the same vulnerabilities that the Rapid7 Threat Feed tracks and monitors due to active exploitation in the wild.  Cards shown here can list vulnerabilities based on their exploitability, the number of your vulnerable assets, the skill required to exploit those vulnerabilities, and common malware kits being used. This dashboard helps illuminate vulnerabilities that may not be garnering many headlines in the news but merit a closer look because they are the vulnerabilities attackers are leveraging by choice.

##Containers
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/1ba37bb-containers.png",
        "containers.png",
        1600,
        820,
        "#3b4450"
      ]
    }
  ]
}
[/block]
This dashboard provides information about containers in your environment, including image assessment percentages, most commonly deployed images, assets ordered by the number of running containers, and your most vulnerable images.

##Remediations
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/8aa7879-remediations.png",
        "remediations.png",
        1600,
        825,
        "#3b444f"
      ]
    }
  ]
}
[/block]
This dashboard provides a consolidated space for quickly viewing progress related to your remediation projects.  Cards shown here can track the most common solutions applied when remediating vulnerabilities on your network, your top remediators, and the statuses of your ongoing projects.

##Samba
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/07b0b5d-samba.png",
        "samba.png",
        1917,
        983,
        "#3a434f"
      ]
    }
  ]
}
[/block]
This specialized dashboard provides visibility on your network’s exposure to the Samba vulnerability (CVE-2017-7494).  Cards shown here detail your top riskiest assets with the Samba vulnerability, the overall number of findings, total vulnerable assets, vulnerable assets by operating system, and the most common exploits.

##WannaCry
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/5880d4f-wannacry.png",
        "wannacry.png",
        1917,
        982,
        "#3a434e"
      ]
    }
  ]
}
[/block]
This specialized dashboard provides visibility on your network’s exposure to the WannaCry vulnerabilities.  Cards shown here detail the most common WannaCry vulnerabilities, the overall number of findings, total vulnerable assets, vulnerable assets by operating system, and the most common exploits.

##Petya-like Ransomware
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/29b7f3a-petya.png",
        "petya.png",
        1919,
        983,
        "#3a434e"
      ]
    }
  ]
}
[/block]
This specialized dashboard uses the same cards found in its WannaCry equivalent, but is tuned for Petya-like ransomware vulnerabilities.

##Other Dashboards

In addition to using existing templates, you can also customize dashboards to your personal needs. See [Creating custom dashboards](doc:creating-custom-dashboards) for more information.

##Timing out

Your session may time out after approximately ten (10) minutes of inactivity in the Dashboards feature. This may happen even if you are active in the InsightVM Console.

If a timeout occurs, you may see a blank screen or be unable to interact with data: for example, you may no longer be able to expand cards. To resolve the timeout, log out of your InsightVM Security Console and log in again.