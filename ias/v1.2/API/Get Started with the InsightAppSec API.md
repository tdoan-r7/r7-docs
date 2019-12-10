---
title: "Get Started with the InsightAppSec API"
excerpt: ""
---
An application programming interface, or API, allows you to interact with other web components in a defined language in order to request or execute actions of the API's available services.

Because data transfer does involve bandwidth and resource usage, InsightAppSec leverages a RESTful API, which is more lightweight and uses less bandwidth than other APIs, such as SOAP APIs.

##InsightAppSec API Capabilities 
APIs easily allow you to move information between different applications and interfaces. With InsightAppSec, you can complete many of the main tasks available in the InsightAppSec interface, including, but not limited to:
  * Modifying vulnerability severity and status
  * Showing  specific applications and their scans
  * Displaying the vulnerabilities from a specific scan
  * Running and managing a scan
  * Creating a new application
  * Creating a  Scan Config
  * Stopping a long running to gather results
  * Cancel a scan
  * Delete a canceled scan
  * Updating the credentials for a Scan Config

#Before You Begin
Before you can use the InsightAppSec API, you should complete the following actions:
  * [Generate the API Key](doc:get-started-with-the-insightappsec-api#section-generate-an-insight-api-key)
  * [Understand how the API works with different roles](doc:get-started-with-the-insightappsec-api#section-roles-and-permissions)
  * [Understand basic API concepts](doc:get-started-with-the-insightappsec-api#section-api-concepts)
  * [Start using the API](doc:get-started-with-the-insightappsec-api#section-start-using-the-api)
  * [Perform basic operations using the API](#section-perform-basic-operations-using-the-api) 
  * [Use Additional Resources](doc:get-started-with-the-insightappsec-api#section-additional-resources)

##Generate an Insight  API Key
In order to interact with the API, you’ll need to generate an API key. There are two kinds of API keys: a User Key, and an Org Key.
  * User Keys: All role are able to generate a user key. This key is associated with your account and will track all changes and actions that you make.
  * Org Keys: Only platform admins can generate an Org key. This is a “super key” and can do everything in the API across all products.

While Platform Admins have access to both a User Key and an Org Key, Rapid7 Recommends that Platform admins use only the Org Key.

See [Managing API Keys](https://insight.help.rapid7.com/docs/managing-platform-api-keys) for more information.
[block:callout]
{
  "type": "warning",
  "title": "If you lose the API key, you must delete the original key and generate a new one."
}
[/block]
##Roles and Permissions
When you generate an API key, the InsightAppSec API inherits your product role and allows you to complete specific actions based on those roles. Platform Admins have Org Keys and can complete all actions in the API.

The following table details the available roles and permissions attached to your API key:
[block:parameters]
{
  "data": {
    "h-0": "Role",
    "h-1": "Permission",
    "0-0": "Product Admin",
    "0-1": "  * Manage Apps\n  * Read Attack Templates\n  * Manage Targets\n  * Manage Scan Configs\n  * Manage Scans\n  * Manage Vulnerabilities\n  * Administer Vulnerability Comments\n  * Manage Engines\n  * Manage Engine Groups\n  * Manage Schedules\n  * Manage Blackouts\n  * Manage Global Blackouts\n  * Manage Files ",
    "1-1": "  * Manage Apps\n  * Read Attack Templates\n  * Read Targets\n  * Manage Scan Configs\n  * Manage Scans\n  * Manage Vulnerabilities\n  * Manage Vulnerability Comments\n  * Read Engines\n  * Read Engine Groups\n  * Manage Schedules\n  * Manage Blackouts\n  * Manage Files ",
    "2-1": "  * Read Apps\n  * Read Attack Templates\n  * Read Targets\n  * Read Scan Configs\n  * Read Scans\n  * Read Vulnerabilities\n  * Read Vulnerability Comments\n  * Read Engines\n  * Read Engine Groups\n  * Read Schedules\n  * Read Blackouts\n  * Read Files ",
    "1-0": "Read Write",
    "2-0": "Read Only"
  },
  "cols": 2,
  "rows": 3
}
[/block]
Roles and privileges are constantly evolving along with the API. For the latest user privileges, refer to the "Permissions" table in the [InsightAppSec API documentation](https://help.rapid7.com/insightappsec/en-us/api/v1/docs.html#).
[block:callout]
{
  "type": "info",
  "body": "If you have a free trial of InsightAppSec, you will have the same permissions as a read-only user.",
  "title": "Trial Users"
}
[/block]
##API Concepts
Ensure you are familiar with the basic concepts of InsightAppSec. Read more about concepts [here](https://insightappsec.help.rapid7.com/docs/concepts). 

Before you use the API, you should be familiar with the following concepts:

  * API endpoint - An API endpoint represents the location where the resource or data you are requesting lives. Read more about [API endpoints](https://insight.help.rapid7.com/docs/api-overview#section-endpoint).
  * Authentication - When you use the API, you must authenticate with the API Key you copied from the Insight Platform. Read more about [API authentication](https://insight.help.rapid7.com/docs/api-overview#section-authentication).
  * Versioning - Because the InsightAppSec API interacts with several APIs, it is important that each API request specifies which version of those APIs to use. Read more about [API versioning](https://insight.help.rapid7.com/docs/api-overview#section-versioning).
  * Pagination - When you make a request from an API, the response results can be paginated, which allows for metadata on the current page and for the upcoming page with the response data. Read more about [API pagination](https://insight.help.rapid7.com/docs/api-overview#section-pagination).
  * Rate limiting - API rate limiting allows you to limit how many requests are made in limit window per API key or access token. At this time, API rate limiting is disabled on the Insight platform.  Read more about [API Rate Limiting](https://insight.help.rapid7.com/docs/api-overview#section-rate-limiting).

#Start Using the API
Once you have the API key, you can start to use the API to send, post, get, and delete data from InsightAppSec. 

First, decide which tool you want to use in order to interact with the API, such as Postman. Learn more about Postman here: https://www.getpostman.com/ 
[block:callout]
{
  "type": "success",
  "body": "Start using the [InsightAppSec API](https://help.rapid7.com/insightappsec/en-us/api/v1/docs.html) now."
}
[/block]
## Perform Basic Operations using the API
The following sections contain examples of basic InsightAppSec operations that you can perform using the API. The URL for a Rapid7 Insight API endpoint follows the structure: 
`{{base url}}/{{api}}/{{version}}/{{endpoint}}`

The `base url` depends on the region for your account. You can refer to the [Supported Regions](https://insight.help.rapid7.com/v1.0/docs/product-apis#section-supported-regions) article for a specific base URL based on your location. For our examples, we will assume that your account is in the US region and you are using version 1 of the API. The URL for an endpoint will then be:
`https://us.api.insight.rapid7.com/ias/v1/{{endpoint}}`. 

Rapid7 Insight platform APIs use the `X-Api-Key` header for authentication and authorization. Before you perform any API call with Postman, make sure you add a header `X-Api-Key` with the value as your [Insight API Key](#section-generate-an-insight-api-key). Postman considers header values as strings by default, so you do not need to add quotes around the API key. 
 
These examples contain all the information necessary to perform the API operation, such as the URL, operation, and the POST body. Placeholder text will be surrounded by curly braces (for example: `{{Provide domain name here}}`) so you can customize your API requests. Insert the information in the appropriate sections in Postman and click **Send**.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/d0ee1d3-Screen_Shot_2018-10-24_at_10.26.49_AM.png",
        "Screen Shot 2018-10-24 at 10.26.49 AM.png",
        1096,
        540,
        "#343335"
      ]
    }
  ]
}
[/block]
The “Expected Response” section in each example will explain what response status and response contents you should expect for a successful operation. Some processes are interconnected, so the response of one will become a request parameter for the other. 

### Add a Target
####Prerequisites
* Domain URL or IP address of a web application that you’d like to scan.

####Operation
POST 
####URL
`https://us.api.insight.rapid7.com/ias/v1/targets`
####Headers
```
X-Api-Key : {{Insight API Key}}
Content-Type : application/json
```
####Body
```
{
  "domain": "{{Your domain URL or IP address}}",
  "enabled": true
}
```

####Expected Response
**Status**
201 Created
**Header**
`Location : https://us.api.insight.rapid7.com:443/ias/v1/targets/{{Target ID}}`

###Create an App
####Operation
POST 
####URL
`https://us.api.insight.rapid7.com/ias/v1/apps/`
####Headers
```
X-Api-Key : {{Insight API Key}}
Content-Type : application/json
```
####Body
```
{
  "name": "API-test-app",
  "description": "Creating an app to test the API"
}
```
####Expected Response
**Status**
201 Created
**Header**
`Location : https://us.api.insight.rapid7.com:443/ias/v1/apps/{{App ID}}`

###Create a Scan Config
####Prerequisites
* App ID from [Create an App](#section-create-an-app)
* The unique ID of the attack template that you’d like to use for your scan config. You can obtain the IDs of all attack templates by running `GET https://us.api.insight.rapid7.com/ias/v1/attack-templates/`. 

####Operation
POST 
####URL
`https://us.api.insight.rapid7.com/ias/v1/scan-configs/`
####Headers
```
X-Api-Key : {{Insight API Key}}
Content-Type : application/json
```
####Body
```
{
  "name" : "api-test-scan-config",
  "description" : "Webscantest scan using the API",
  "app" : {
    "id" : "{{App ID}}"
  },
  "attack_template" : {
    "id" : "{{Attack template ID}}"
  }
}
```
####Expected Response
**Status**
201 Created
**Header**
`Location : https://us.api.insight.rapid7.com:443/ias/v1/scan-configs/{{Scan Config ID}}`

###Add a Domain to a Scan Config
####Prerequisites
* Domain URL or IP address from [Add a Target](#section-add-a-target)
* Scan config ID from [Create a Scan Config](#section-create-a-scan-config)

####Operation
PUT 
####URL
`https://us.api.insight.rapid7.com/ias/v1/scan-configs/{{Scan Config ID}}/options`
####Headers
```
X-Api-Key : {{Insight API Key}}
Content-Type : application/json
```
####Body
```
{
  "crawl_config": {
	"seed_url_list": [
      {
        "value": "{{Your domain URL or IP address}}"
      }
    ],
    "max_crawl_results": 101,
    "scope_constraint_list": [
      {
        "URL": "{{Your domain URL or IP address}}/*",
        "method": "ALL",
        "exclusion": "INCLUDE",
        "match_criteria": "WILDCARD",
        "http_parameter_list": []
      }
    ]
  },
  "attacker_config": {
    "scope_constraint_list": [
      {
        "URL": "{{Your domain URL or IP address}}/*",
        "method": "ALL",
        "exclusion": "INCLUDE",
        "match_criteria": "WILDCARD",
        "http_parameter_list": []
      }
    ]
  }
}
```
####Expected Response
**Status**
200 OK

###Run a Scan
####Prerequisites
* Scan config ID from [Create a Scan Config](#section-create-a-scan-config)

####Operation
POST 
####URL
`https://us.api.insight.rapid7.com/ias/v1/scans`
####Headers
```
X-Api-Key : {{Insight API Key}}
Content-Type : application/json
```
####Body
```
{
  "scan_config": {
    "id": "{{Scan Config ID}}"
  }
}
```
####Expected Response
**Status**
201 Created
**Header**
`Location : https://us.api.insight.rapid7.com:443/ias/v1/scans/{{Scan ID}}`

###Retrieve Scan Results
####Prerequisites
* Scan ID from [Run a Scan](#section-run-a-scan)

####Operation
POST 
####URL
`https://us.api.insight.rapid7.com/ias/v1/search`
####Headers
```
X-Api-Key : {{Insight API Key}}
Content-Type : application/json
```
####Body
```
{
   "type":"VULNERABILITY",
   "query":"vulnerability.scans.id='{{Scan ID}}'"
}
```
####Expected Response
**Status**
200 OK
**Body**
Details of vulnerabilities found in the scan presented in JSON format.


#Additional Resources

To learn more about the API, see the [API overview](https://insight.help.rapid7.com/docs/api-overview).

###Supported Regions
You can change the base URL of the API based on your region. See [Supported Regions](https://insight.help.rapid7.com/v1.0/docs/product-apis#section-supported-regions) for a specific base URL based on your location.