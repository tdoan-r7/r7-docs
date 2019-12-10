---
title: "Setting Up a Sonar Query"
excerpt: ""
---
[Project Sonar](https://sonar.labs.rapid7.com/) is an initiative by the Rapid7 Labs team to improve security through the active analysis of public networks. It performs non-invasive scans of public IPv4 addresses for common services, extracts information from the services, and makes the data available to everyone.

By analyzing Project Sonar data, you can:
* View your environment from an outsider's perspective.
* Find assets that belong to your organization that you may not have been tracking.
* Get a snapshot of your public facing assets.
* Obtain a better understanding of your exposure surface area.

Project Sonar data can be added to a site and treated like any other data. Please just remember that Project Sonar data is not a definitive or comprehensive view; it's just a starting point you can use to learn more about your public Internet presence.

##Connecting to Project Sonar

Project Sonar is available to Nexpose Enterprise license key holders. If you have the proper licensing, your console will automatically connect to Project Sonar if it can reach the server at https://sonar.labs.rapid7.com via port 443. Your console must also have Dynamic Discovery enabled.

**To check the status of your connection to Project Sonar:**
1. Select **Administration** from the left navigation menu.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/e594b3f-s_nx_sonar_administration.png",
        "s_nx_sonar_administration.png",
        809,
        261,
        "#1e2930"
      ]
    }
  ]
}
[/block]
2. Under the _Discovery Options_, click the **manage** link for _Connections_.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/95767af-s_nx_sonar_manage.jpg",
        "s_nx_sonar_manage.jpg",
        585,
        221,
        "#e6eaeb"
      ]
    }
  ]
}
[/block]
3. On the _Discovery Connections_ page, check the status for _Sonar_. It should be _Connected_.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/0a3c015-s_nx_sonar_connection.jpg",
        "s_nx_sonar_connection.jpg",
        1236,
        452,
        "#1e2e3b"
      ]
    }
  ]
}
[/block]
##Setting up a Sonar query

As a Nexpose Administrator, you can set up queries that pull data from Sonar and add them to the console. These queries can also be used to set boundaries on the domains that Site Administrators have permissions to scan. In addition to the query, you can add filters to further refine the results that are added to the Nexpose Console. All results from Sonar are added to the _Discovered by Connection_ table on the _Assets_ page.

**To set up a Sonar query:**
1. Select **Administration** from the left navigation menu.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/e45af5b-s_nx_sonar_administration.png",
        "s_nx_sonar_administration.png",
        809,
        261,
        "#1e2930"
      ]
    }
  ]
}
[/block]
2. Under the _Discovery Options_, click the **manage** link for _Connections_.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/e7c74ef-s_nx_sonar_manage.jpg",
        "s_nx_sonar_manage.jpg",
        585,
        221,
        "#e6eaeb"
      ]
    }
  ]
}
[/block]
3. Click on the **Sonar** connection. 
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/4ec809a-s_nx_admin_sonar_connection.jpg",
        "s_nx_admin_sonar_connection.jpg",
        1309,
        237,
        "#f1f5f6"
      ],
      "caption": "Select the Sonar connection"
    }
  ]
}
[/block]
4. On the _Sonar Queries_ page, click the **New Sonar Query** button. 
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/012d456-s_nx_admin_new_sonar_query_button.jpg",
        "s_nx_admin_new_sonar_query_button.jpg",
        1313,
        203,
        "#ebf1f3"
      ]
    }
  ]
}
[/block]
5. Enter a name for the query. 
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/7baa7ec-s_nx_admin_sonar_query_name.jpg",
        "s_nx_admin_sonar_query_name.jpg",
        1308,
        279,
        "#eaeff2"
      ]
    }
  ]
}
[/block]
6. Add a filter for the domain you want to query. It can be a top level domain, such as 'rapid7.com', or a subdomain, such as 'community.rapid7.com'.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/ab1d8c0-s_nx_sonar_manage.jpg",
        "s_nx_sonar_manage.jpg",
        585,
        221,
        "#e6eaeb"
      ]
    }
  ]
}
[/block]
You can also add a scan date filter if you want to control the staleness of your asset data. The shorter the range, the less likely the data will be stale.
7. Test the query by running it. It may take awhile to complete and will display any results in the table.
8. Save the query when you are done.

##Filtering data from Project Sonar

A filter is a rule that you can use to refine the results from a Sonar query. You create them when you want to specify requirements for the assets you add to your console. A filter comprises of a filter type, search operator, and filter value.

###Filter types

You can create filters based on:
* A domain name, such as 'rapid7.com' or 'community.rapid7.com'
* A scan date, such as 'within the last 30 days'

###Search operators

A filter uses an operator to match assets to the value you have provided. You can use the following operators to build a filter:
* **Contains** — Filters based on a partial match. For example, the filter 'domain name contains rapid7.com' returns all assets that contain 'rapid7.com' in the domain.
* **Within the last** — Filters base on a time frame. This operator is only used with scan date filters and only accepts an integer. For example, the filter 'Sonar scan date within the last 7 days' returns assets that Sonar has scanned in the past week.

##Setting the scan date for Sonar queries

You can create a scan date filter to control the staleness of your asset data. Stale data occurs when the asset has been scanned by Sonar, but the asset has changed IP addresses since the scan was performed. Typically, the longer it has been since Project Sonar has scanned an asset, the more likely it is that the data is stale.

To reduce the possibility of adding stale data to your site, you should create a scan date filter. A more recent scan date range, like 7 days, can help ensure that you don't accidentally add assets that do not belong to you. If you apply a scan date filter and do not see any results from Sonar, you may need to extend the range the filter is using.

##Clearing the Sonar Cache

Clearing your Sonar cache will clear all Sonar assets from the _Discovered by Connection_ table on the _Assets_ page. You may want to clear your Sonar cache after you have deleted a Sonar query or you want to force a refresh on existing Sonar queries.

**To clear the Sonar cache:**
1. Select **Administration** from the left navigation menu.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/954b2f7-s_nx_sonar_administration.png",
        "s_nx_sonar_administration.png",
        809,
        261,
        "#1e2930"
      ]
    }
  ]
}
[/block]
2. Under the _Discovery Options_, click the **manage** link for _Connections_.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/d6f1824-s_nx_sonar_manage.jpg",
        "s_nx_sonar_manage.jpg",
        585,
        221,
        "#e6eaeb"
      ]
    }
  ]
}
[/block]
3. Click on the **Sonar** connection. 
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/28f0e74-s_nx_admin_sonar_connection.jpg",
        "s_nx_admin_sonar_connection.jpg",
        1309,
        237,
        "#f1f5f6"
      ],
      "caption": "Select the Sonar connection"
    }
  ]
}
[/block]
4. Click the **Clear All Sonar Assets** button. 
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/034d257-s_nx_admin_sonar_clear_cache.jpg",
        "s_nx_admin_sonar_clear_cache.jpg",
        1369,
        205,
        "#e8eef1"
      ]
    }
  ]
}
[/block]
When you go to the _Discovered by Connection_ table on the _Assets_ page, you will not see any Sonar assets listed. Any existing Sonar queries that you still have set up will continue to return asset data, which will be added to the table the next time the query runs.

##Deleting a Sonar query

Deleting a Sonar query removes it from the connection. It does not delete the connection itself. The connection will continue to persist, but will not add any data to your console. The data that has already been added to the console will be retained.

**To delete a Sonar query:**
1. Select **Administration** from the left navigation menu.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/165bded-s_nx_sonar_administration.png",
        "s_nx_sonar_administration.png",
        809,
        261,
        "#1e2930"
      ]
    }
  ]
}
[/block]
2. Under the Discovery Options, click the manage link for Connections.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/2854982-s_nx_sonar_manage.jpg",
        "s_nx_sonar_manage.jpg",
        585,
        221,
        "#e6eaeb"
      ]
    }
  ]
}
[/block]
3. Click on the **Sonar** connection. 
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/68f8973-s_nx_admin_sonar_connection.jpg",
        "s_nx_admin_sonar_connection.jpg",
        1309,
        237,
        "#f1f5f6"
      ],
      "caption": "Select the Sonar connection"
    }
  ]
}
[/block]
4. Click the **Delete** button next to the query you want to remove. 
The query is deleted from the connection.