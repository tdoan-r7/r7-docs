---
title: "Discovering Assets managed by Active Directory"
excerpt: ""
---
The Active Directory connection allows InsightVM to collect information from the catalog of assets in Active Directory. This reduces the effort for network administrators to keep the asset list in InsightVM updated. InsightVM also pulls in OS information from Active Directory where available, so you can create asset groups by the hostname and the OS, or automatically add newly discovered assets into existing asset groups.
[block:callout]
{
  "type": "info",
  "body": "Assets are synchronized from Active Directory once per day."
}
[/block]
Active Directory discovery connections must be created from the Administration page. To learn more, see _Creating a connection outside of a site configuration_.
[block:callout]
{
  "type": "warning",
  "body": "In order to create an Active Directory connection, you will need to have a static site already configured. You can use an existing site or create a new one. If creating a new one, you may need to add an asset as a placeholder since the Active Directory connection will not be available yet."
}
[/block]