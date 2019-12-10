---
title: "Bamboo Integration"
excerpt: ""
---
InsightAppSec integrates with Atlassian Bamboo build and release pipelines to empower development teams to autonomously test the integrity of an application in run-time within their own CI/CD workflow. Using the InsightAppSec Bamboo plugin within a Bamboo pipeline gives security teams essential feedback regarding a web application’s security posture and risk status as part of an integrated CI/CD task and allows development teams to pass/fail and fix fast.

# Overview
The InsightAppSec Bamboo Plugin utilizes the InsightAppSec RESTful API to dynamically retrieve applications, launch scans, monitor their progress, and generate reports based upon scan results. This plugin can be leveraged as both a Build and Release task within Atlassian Bamboo.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/f258239-image-01.png",
        "image-01.png",
        759,
        352,
        "#eef0f2"
      ]
    }
  ]
}
[/block]
# Key Capabilities
The extension is designed with the following capabilities:
  * Launch a new InsightAppSec scan during build or release
  * Perform scan monitoring
  * Provide a metrics report of scan results
  * Provide raw scan results
  * Enforce scan gating based on vulnerability query filtering
Scan gating provides an automated way to fail tasks as part of a build should scan results meet a defined vulnerability query, stopping certain risk from being promoted into production.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/9740413-image16.png",
        "image16.png",
        1590,
        224,
        "#f7f7f8"
      ]
    }
  ]
}
[/block]
###Metrics Report Output
Once the scan within the build or deploy plan has been completed, a report will be generated and added as an artifact to the Bamboo job. It contains metrics on vulnerability severity and attack modules retrieved from the scan.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/8abfa74-image18.png",
        "image18.png",
        1160,
        583,
        "#2d2d2d"
      ]
    }
  ]
}
[/block]
# Get Started
By integrating InsightAppSec into your CI solution, quality gates can be enforced to proactively secure applications before being released into production. The InsightAppSec Bamboo Plugin is a way to make security teams smarter while keeping development teams efficient. 
Visit the [Atlassian Marketplace Listing](https://marketplace.atlassian.com/1221109) to get the InsightAppSec Bamboo Plugin.

# Install the InsightAppSec Bamboo Plugin
Before utilizing the plugin as part of a build or deploy plan, it must first be installed within the Bamboo environment. There are two ways to accomplish this, from the Atlassian Marketplace or within Bamboo.

## Install the InsightAppSec Bamboo Plugin from Atlassian Marketplace
1. Navigate to the [Atlassian Marketplace Listing](https://marketplace.atlassian.com/1221109) or search for “Rapid7 InsightAppSec” from the Marketplace home. Bhai 
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/e3b812d-image7.png",
        "image7.png",
        1999,
        1292,
        "#e9eaeb"
      ]
    }
  ]
}
[/block]
2. Click the **Get it now** button to download the plugin in JAR format. 
3. Manually install the plugin within Bamboo Administration.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/1438424-image27.png",
        "image27.png",
        1155,
        452,
        "#b5bbc4"
      ]
    }
  ]
}
[/block]
## Install the InsightAppSec Bamboo Plugin from within Bamboo
1. In Bamboo Administration, click on **Find new apps** on the left panel of the administration page. this will open the Atlassian Marketplace for Bamboo.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/476d108-image17.png",
        "image17.png",
        296,
        242,
        "#f5f5f7"
      ]
    }
  ]
}
[/block]
2. Search the marketplace for “Rapid7 InsightAppSec”.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/dd22174-image5.png",
        "image5.png",
        1999,
        647,
        "#f5f5f6"
      ]
    }
  ]
}
[/block]
3. Click the **Install** button and agree to the terms of use.  This will then install the plugin and make it available for use without any manual steps.

With installation complete, you can now move on to plugin and task configuration.

# Create a Bamboo Plan with InsightAppSec Plugin
This plugin utilizes the InsightAppSec RESTful API to perform actions, such as retrieving applications and launching scans. To allow for this, we must first configure a connection to this API so all extension functionality can proceed accordingly.

1. From within Atlassian Bamboo, navigate to Bamboo Administration.  In the left hand panel, select Shared Credentials.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/914ec6a-image2.png",
        "image2.png",
        917,
        431,
        "#dfe5ef"
      ]
    }
  ]
}
[/block]
2. Select the “Add new credentials” dropdown followed by choosing the “Username and password” option to begin with creating a credential to be used by the plugin.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/3f70f2e-image8.png",
        "image8.png",
        605,
        504,
        "#f6f7f9"
      ]
    }
  ]
}
[/block]
3. Provide a “Credential name” that begins with “Rapid7” for this credential. 
[block:callout]
{
  "type": "warning",
  "body": "If the credential is not prefixed with “Rapid7” it will not appear as an option within the Bamboo task configuration for the plugin.",
  "title": "Note"
}
[/block]
4. The “Username” field should be populated with a human readable field; however, this field is not used.  Finally, the “Password” is used to store the API Token which is a unique key that is provided by Rapid7 and serves as an identifier for API authentication.
5. Click “Save credentials” and the credential will be created and listed under Shared credentials, should you ever need to edit it.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/bdbdba9-image13.png",
        "image13.png",
        962,
        443,
        "#e3e9f2"
      ]
    }
  ]
}
[/block]
6. With the shared credential configured, the next step is to create a build or deploy plan that will utilize the new plugin.  If a Build or Deploy plan already exists, navigate to it and edit the plan.  If a new plan needs created for use with the InsightAppSec plugin, use the “Create plan” option in the top navigation of Bamboo.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/9a8143b-image1.png",
        "image1.png",
        1007,
        729,
        "#f7f8f9"
      ]
    }
  ]
}
[/block]
7. Once a new Build or Deploy plan exists, a new Task can be added to it.  Select “Add task” and then search for “Rapid7” or “InsightAppSec”.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/dd0cdf0-image3.png",
        "image3.png",
        969,
        523,
        "#fbfbfc"
      ]
    }
  ]
}
[/block]

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/6d2db40-image10.png",
        "image10.png",
        867,
        533,
        "#fcfcfc"
      ]
    }
  ]
}
[/block]
8. Select the “Rapid7 InsightAppSec Scan” task, which will then provide prompts for configuring the task for the specific App and Scan Configuration in scope.
9. The base configuration of the task will require the Region and API Key to be chosen.  Ensure the proper region is chosen for your Rapid7 organization.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/d4c67e5-image24.png",
        "image24.png",
        979,
        601,
        "#f4f6fa"
      ]
    }
  ]
}
[/block]
This is also where the proper API Key will be selected as configured previously.  It is important to remember that depending on the API key used, different permissions will be provided when running scans.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/fc8f10c-image9.png",
        "image9.png",
        443,
        187,
        "#e1e7ee"
      ]
    }
  ]
}
[/block]
When configuring the task, you will also be required to provide the “App Name” and “Scan Config Name” to identify what to run the scan for.  These names should already exist within InsightAppSec as a previously created App and Scan Config.  While saving the task, a validation will be made against the InsightAppSec API to ensure these items exist.  If they do not, an error prompt will be provided to inform the user.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/09baa62-image15.png",
        "image15.png",
        396,
        154,
        "#f4f4f7"
      ]
    }
  ]
}
[/block]
10. It is possible to configure “Task Advancement” in three different ways.  This allows for flexibility with what to do after triggering a scan as part of the Build or Deploy plan.
  * **COMPLETED** - Move on from task after the initiated scan has completed
  * **STARTED** - Move on from task once the scan has been submitted and started
  * **SUBMITTED** - Move on from task immediately after submitting scan 
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/b2e17db-image25.png",
        "image25.png",
        311,
        93,
        "#9cadc4"
      ]
    }
  ]
}
[/block]
Depending on the advancement option selected, additional settings will be provided to further configure the task.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/3c8a245-image22.png",
        "image22.png",
        653,
        309,
        "#f8f9fb"
      ]
    }
  ]
}
[/block]
11. Finally, an optional “Vulnerability Query Enforcement” setting is provided in order to do gating based on scan results.  This option is only visible when “Task Advancement” is set to “COMPLETED”.  When selecting this option, it is important to define a query which is used to fail the scan if any vulnerability findings are returned that match the query for the specific scan.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/ae26ed5-image20.png",
        "image20.png",
        695,
        193,
        "#f6f7f9"
      ]
    }
  ]
}
[/block]
In this example, the scan will fail if any findings are returned with a severity of HIGH.  This is a simple way to gate InsightAppSec scans as part of the CI/CD pipeline.  It is possible to configure multiple query conditions as long as they match the API documentation.  Review the “Useful Examples” for assistance: https://help.rapid7.com/insightappsec/en-us/api/v1/docs.html#tag/Search
Here is a list of all the settings in greater detail:
* **Task Description** - The description of the task as it will appear in the plan	
* **InsightAppSec Region** - Dropdown of InsightAppSec regions for connecting to the API.
* **InsightAppSec API Key** - A drop-down menu to select the Rapid7 API Key to be used.
* **App Name** - A text field to input the InsightAppSec application name that will be utilized in the scan.
* **Scan Config Name** - A text field to input the InsightAppSec scan configuration that will be utilized in the scan.	
* **Advance task when scan has been** - A drop-down menu to dictate when to move on from task; options: COMPLETED, STARTED, SUBMITTED.
* **Status Check Interval** - The frequency (in minutes) that the scan’s status will be checked. Dependent on task advancement set to COMPLETED or STARTED.
* **Max Scan Pending Duration** - The time (in minutes) to wait for the scan to be started. Task will be marked a failure if pending duration is reached.
* **Max Scan Execution Duration** - The time (in minutes) to wait for the scan to be completed. Task will be marked a failure if max execution duration is reached.
* **Findings Report Generation** - Option used to determine whether a raw JSON findings report will be generated and added as an artifact for the build.
* **Vulnerability Query Enforcement** - Option used to determine whether the build will fail if the provided query returns results.
* **Vulnerability Query** - The query executed against the completed scan's findings to retrieve any matching vulnerabilities. Dependent on the option Vulnerabilities Query Enforcement being checked.

Once you have configured the settings for the Rapid7 InsightAppSec task, as well as completed any additional tasks you want in the plan, Save the task and the plan.

# Execution
Once the plugin and task have been configured, the plan can be run to initiate all the tasks.  Once the InsightAppSec Scan task is reached, a scan will be triggered within InsightAppSec and then the task will continue based on the configurations set.  To run the plan, navigate to the Plan and select “Run plan”.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/7c01564-image23.png",
        "image23.png",
        338,
        133,
        "#e1e4ea"
      ]
    }
  ]
}
[/block]
Once the InsightAppSec task is reached within the run, logs of its status will be found in the job output.  This can be helpful to know when the job moves from Pending to Running state.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/d652f55-image19.png",
        "image19.png",
        1220,
        706,
        "#e5ebf5"
      ]
    }
  ]
}
[/block]
In the scenario where vulnerability query gating is enforced, the build may fail if any findings meet the query criteria.  This will result in the task and plan failing with details of the number of findings meeting the criteria.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/831a945-image11.png",
        "image11.png",
        1317,
        455,
        "#f0dcdb"
      ]
    }
  ]
}
[/block]
### Reports Artifacts
Whether a successful or failed build, report artifacts will be provided and archived for the job.  
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/39c61be-image4.png",
        "image4.png",
        1282,
        256,
        "#fbfcfc"
      ]
    }
  ]
}
[/block]
There are two possible reports that will be generated.  The first is a metrics report with a rollup of counts regarding vulnerability severity and modules.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/9071f0a-zz_-_image18.png",
        "zz - image18.png",
        1160,
        583,
        "#2d2d2d"
      ]
    }
  ]
}
[/block]
The second is a raw report of scan findings.  This report will only be generated if “Findings Report Generation” is enabled during task configuration.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/c3fd021-image6.png",
        "image6.png",
        607,
        168,
        "#f5f4f8"
      ]
    }
  ]
}
[/block]
These two reports can be used for more sophisticated gating, trending of scan findings, or even generation of tickets based on the content.  While those functions are not implemented in the plugin, providing the reports should make it that much easier to ingest that data if additional functionality is needed based on scan results.

# Troubleshooting
### The Rapid7 InsightAppSec Scan task doesn’t appear when I search for it while creating a plan.
The plugin must first be installed in your Bamboo environment in order for it to be available for usage in a Build or Deploy plan. Go to “Manage Apps” from within Bamboo Administration and then search for “Rapid7 InsightAppSec” in order to install the plugin.  The plugin can also be found on the [Atlassian Marketplace](https://marketplace.atlassian.com/1221109). Settings, then select Extensions. Check to see if the extension is listed under the Installed tab. If not, then you can find it under its 

### My API Key is not available in the credential dropdown.
You must first create a shared credential under Bamboo Administration in order for API keys can be made available for setting up a task.  Ensure any API keys that have been created for use by the InsightAppSec Plugin begin with “Rapid7” as part of the shared credential name.

### The job or task failed and I’m not sure why.
There are logs available within the Bamboo job that runs the Rapid7 InsightAppSec task of the plan.  Go to the running plan job and select “Summary” for any running jobs or “Logs” for previously completed jobs to historical logs.

### There are API errors occurring in the logs when running the pipeline.
API errors are most likely due to an issue with the API key or region that was setup to be used with the configured task. In the Rapid7 InsightAppSec Scan task that you added, double check the Region and API Key are correct for your InsightAppSec environment.  

### I didn’t get any artifacts saved for the job on completion.
This could occur for a few reasons:
* The “Task Advancement” option is configured for “SUBMITTED” or “STARTED”. In each scenario, the task will not wait for scan completion which is necessary to generate the artifacts.
* The scan was considered a “failed scan” for any number of reasons, and reports are not generated for a failed scan. Check the logs for the InsightAppSec task to find out why the scan failed.
* The “Findings Report Generation” option was not selected so only the metrics report will be generated.

### The scan gating didn’t seem to work and my build was successful.
Double check the query that was input in the Vulnerability Query field. This requires a specific type of formatting that could result in the query not returning any results if not adhered to. Here’s an example of scan gating based on severity. Note the single quotes used.

vulnerability.severity='HIGH’

Additional query options can be found in the [InsightAppSec API documentation](https://help.rapid7.com/insightappsec/en-us/api/v1/docs.html#tag/Search). Only filters for the Vulnerability Resource Type should be leveraged.

### The plan immediately went to the next step upon launching the scan, without giving any scan status updates.
To receive logging with scan status updates, you must set “Task Advancement” to “COMPLETED” along with a “Scan Status Interval” defined. Otherwise the plan will proceed to the next task immediately after submitting or starting the scan in InsightAppSec.

Immediately moving on to the next task can be helpful in environments where no gating or feedback to Atlassian Bamboo is necessary and teams only want to trigger scans when new changes are deployed.

### The logs say that my scan timed out.
Failing the scan on timeout is an option included in the extension. If it timed out, then the scan is taking longer than expected to complete based on this configuration. You will need to adjust the “Max Scan Execution” setting to a timeout that is appropriate for the environment and application.

# Support
Need help? We’ve got you covered. Sign into the Customer Portal for our top recommended help articles, and to connect with our awesome Support Team.

**Create and manage your cases with ease** and get routed to the right product specialist.
[CUSTOMER PORTAL SIGN IN](https://rapid7ipimseu.okta-emea.com/home/salesforce/0oa2eo6xizl7cdqH40i7/46)
**Introducing the Scheduler:** Customers can now schedule time with a support engineer, directly in the Customer Portal. [Learn how](https://kb.help.rapid7.com/docs/schedule-a-meeting-with-our-support-team).

### Having trouble logging in?
  * [Create your account](https://kb.help.rapid7.com/page/using-the-customer-portal#section-my-support-account-doesn-t-work-anymore)
  * [Reset your password](https://insight.rapid7.com/login)
  * [Customer Portal FAQs](https://kb.help.rapid7.com/page/using-the-customer-portal#section-faqs)