---
title: "Azure DevOps Integration"
excerpt: ""
---
InsightAppSec integrates with Azure DevOps build and release pipelines to empower development teams to autonomously test the integrity of an application at runtime within their own CI/CD workflow. Using the InsightAppSec Azure DevOps extension within an Azure DevOps Pipeline gives security teams essential feedback regarding a web application’s security posture and risk status as part of an integrated CI/CD task and allows development teams to pass/fail and fix fast.

# Overview
The InsightAppSec Azure DevOps Extension utilizes the InsightAppSec RESTful API to dynamically retrieve applications, launch scans, monitor their progress, and generate reports based upon scan results. This extension can be leveraged as both a Build and Release task within Azure DevOps.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/2f94f9e-insightappsec-azure-devops-workflow.png",
        "insightappsec-azure-devops-workflow.png",
        5075,
        2590,
        "#7e989b"
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
        "https://files.readme.io/0200e13-image18.png",
        "image18.png",
        1590,
        224,
        "#f7f7f8"
      ]
    }
  ]
}
[/block]
###Metrics Report Output
Once the scan within the build or release pipeline has been completed, a report will be generated and written to the current working directory in Azure DevOps. It contains metrics on vulnerability severity and attack modules retrieved from the scan.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/0b82e3b-image3.png",
        "image3.png",
        1034,
        586,
        "#2d2d2d"
      ]
    }
  ]
}
[/block]
# Get Started
By integrating InsightAppSec into your CI solution, quality gates can be enforced to proactively secure applications before being released into production. The InsightAppSec Azure DevOps Extension is a way to make security teams smarter while keeping development teams efficient. 
Visit the [Visual Studio Marketplace Listing](https://marketplace.visualstudio.com/items?itemName=rapid7.rapid7-insightappsec-extension) to get the InsightAppSec Azure DevOps Extension.

#Install the InsightAppSec Azure DevOps Extension
Before utilizing the extension as part of a build or release pipeline, it must be installed under the selected organization. To do this: 
1. Navigate to the [Visual Studio Marketplace Listing](https://marketplace.visualstudio.com/items?itemName=rapid7.rapid7-insightappsec-extension) or locate the extension there by searching for Rapid7 InsightAppSec.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/40ed7c6-image14.png",
        "image14.png",
        1912,
        894,
        "#e7e7e7"
      ]
    }
  ]
}
[/block]
2. Click the **Get it free** button to begin the installation process.
3. The next page allows you to select the organization within Azure DevOps where the extension will be installed. There is the potential of utilizing it for multiple organizations, but it must be individually installed under each one.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/df46b91-image1.png",
        "image1.png",
        1912,
        933,
        "#aabcc9"
      ]
    }
  ]
}
[/block]
Select your organization and click the **Install** button. A successful installation screen should soon follow, confirming that the extension is now ready for use within your organization.

# Create a Service Connection
You must create a Service Connection before configuring the Rapid7 InsightAppSec extension within a pipeline. To do this:
1. Go to the homepage of your organization, then select the project whose pipelines will be utilizing the extension.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/40f5194-image9.png",
        "image9.png",
        1915,
        936,
        "#f4f5f5"
      ]
    }
  ]
}
[/block]
2. On the project’s homepage, select the **Project Settings** option, then click on **Service Connections** under the Pipelines header.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/9c4c934-image25.png",
        "image25.png",
        1913,
        937,
        "#f9f9f9"
      ]
    }
  ]
}
[/block]
3. This extension utilizes the InsightAppSec RESTful API to perform actions, such as retrieving applications and launching scans. To allow for this, we must first configure a connection to this API so all extension functionality can proceed accordingly.
Click **New service connection** to begin with this configuration, then select the Rapid7 InsightAppSec connection type.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/489cc4a-screenshot1.png",
        "screenshot1.png",
        811,
        381,
        "#f8fafc"
      ]
    }
  ]
}
[/block]
4. Provide a “Connection name” for this service connection, preferably something specific to note that this is associated with InsightAppSec.
The **Region** can be selected from the dropdown, and it refers to your Rapid7 InsightAppSec region.
The **API Token** is a unique key that will also be provided by Rapid7 and serve as an identifier for API authentication.
5. Click **OK** to create the connection. The connection will be listed under "Service Connections", should you ever need to edit it.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/0758917-image4.png",
        "image4.png",
        1911,
        930,
        "#f7f8f8"
      ]
    }
  ]
}
[/block]
# Create a Pipeline with the InsightAppSec Extension
With the service connection configured, the next step is to actually create a build or release pipeline that will utilize the new extension.

On the left menu, hover over **Pipelines** and navigate to either **Builds** or **Releases**, depending on on the type of pipeline you wish to create.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/55256d6-image19.png",
        "image19.png",
        1914,
        935,
        "#f7f8f8"
      ]
    }
  ]
}
[/block]
Any existing pipelines, along with their success or failure status, will be listed here. The InsightAppSec extension can be added to a brand new pipeline or within an existing one. This guide will detail adding it to a new pipeline, though the steps for existing pipelines remain largely the same.
1. Start by clicking the **+ New** dropdown, and then select **New build pipeline.**
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/b9d8148-image8.png",
        "image8.png",
        1909,
        936,
        "#f8f8f8"
      ]
    }
  ]
}
[/block]
2. The new pipeline wizard will open. You can either select your repository via the provided YAML options, or use the classic editor to do so without YAML. In this example, we’ll proceed with the classic editor.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/2ff648a-image13.png",
        "image13.png",
        1914,
        937,
        "#f3f4f4"
      ]
    }
  ]
}
[/block]
3. This will take you to another page for repository selection. Select the appropriate source, project, and branch options, and click **Continue**.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/8f71ccd-image2.png",
        "image2.png",
        1914,
        938,
        "#f4f4f4"
      ]
    }
  ]
}
[/block]
3. Next is the template selection. If preferred, select from the several existing templates, or otherwise select **Empty job** at the top to begin from scratch.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/21fb996-image6.png",
        "image6.png",
        1915,
        938,
        "#f4f5f5"
      ]
    }
  ]
}
[/block]
4. This will start a fresh template to allow for the addition of any number of tasks. Click the **+** sign on “Agent job 1” to add a task where we can utilize the Rapid7 InsightAppSec extension.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/74a44c1-image5.png",
        "image5.png",
        1913,
        936,
        "#f4f4f4"
      ]
    }
  ]
}
[/block]
5. A full list of tasks will be displayed. Use the search box at the top right and search for “InsightAppSec” to quickly find the Rapid7 extension. You will see both the Marketplace listing, which displays the status of the extension (in this case it should be "Installed"), and the task itself that can be added to a pipeline.
Hover over the task and select the **Add** button to add it as a task for the pipeline.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/e425e5b-screenshot2.png",
        "screenshot2.png",
        1915,
        937,
        "#f1f3f5"
      ]
    }
  ]
}
[/block]
6. You may see a "Some settings need attention" warning associated with the task due to the fact that it has some fields that are required. The pipeline will not save if these fields are not addressed.
Click on the newly added task to view all of its fields.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/3e549dc-image23.png",
        "image23.png",
        1912,
        933,
        "#f4f4f4"
      ]
    }
  ]
}
[/block]
This is the initial view of the task and its settings. These settings will allow for configuration of the task, its connection to InsightAppSec, and its scanning. Here is a list of all the settings in greater detail:

* **Display name** - The name of the task as it will appear in the pipeline.
* **IAS Connection** - A service connection that allows for connection and authentication to the InsightAppSec API. Drop-down menu containing the connection that was shown configured in a previous step.
* **Application** - A drop-down menu to select the InsightAppSec application that will be scanned.
* **Scan Configuration** - A text field to input the InsightAppSec scan configuration that will be utilized in the scan.
* **Wait for scan completion?** - Option used to determine whether the pipeline will continue to the next step after launching the scan, or whether it will wait for its completion.
* **Scan Status Interval** - The frequency (in minutes) that the scan’s status will be checked upon and logged. Dependent on “Wait for scan completion” being checked.
* **Generate findings report?** - Option used to generate a raw JSON report that contains all findings from a completed scan.
* **Fail scan on timeout?** - Option used to determine whether the scan will be cancelled and marked as failed if it reaches the timeout limit. Dependent on “Wait for scan completion” being checked.
* **Timeout** - The timeout for the scan completion (in minutes). Dependent on “Fail scan on timeout” being checked.
* **Scan Gating** - Option used to determine whether the build will fail if the provided query returns results.
* **Vulnerability Query** - The query executed against the completed scan’s findings to retrieve any matching vulnerabilities. Dependent on the option “Scan Gating” being checked.

Below is a full example configuration of the settings within the task. Note the usage of the “Wait for scan completion” option and its dependent fields, as well as the usage of Scan Gating. In this case, that query will result in the build failing, should the scan return any vulnerabilities whose severity is HIGH.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/ab73c1d-image16.png",
        "image16.png",
        758,
        970,
        "#fafbfb"
      ]
    }
  ]
}
[/block]
7. Once you have configured the settings for the Rapid7 InsightAppSec task, as well as completed any additional tasks you want in the pipeline, select one of the two Save options to ensure the pipeline is saved for future use. “Save” will simply save the pipeline’s current state, while “Save & queue” will immediately launch the pipeline and begin with the execution of each configured task.

###Output
Once the scan within the build or release pipeline has completed, a report will be generated and written to the Build.ArtifactStagingDirectory in Azure DevOps. It contains metrics on vulnerability severity and attack modules retrieved from the scan.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/0b82e3b-image3.png",
        "image3.png",
        1034,
        586,
        "#2d2d2d"
      ]
    }
  ]
}
[/block]
To utilize the contents of this report, an additional step can be added to the pipeline to save it as an artifact that will be associated with the build. The step is titled “Publish pipeline artifact” and can be used multiple times within the same build pipeline.

Below is an example of the configuration that should be used with this step, as the Build.ArtifactStagingDirectory is currently where the report is published by default.

Note that the “Wait for scan completion” option must be checked in order to retrieve the report in this manner, because it is comprised of the results that are generated upon scan completion.

**File directory or path:** `$(Build.ArtifactStagingDirectory)`
**Artifact name:** `insightappsec-scan-metrics.json`
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/1170b22-image7.png",
        "image7.png",
        781,
        433,
        "#fafafb"
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
        "https://files.readme.io/865861d-image12.png",
        "image12.png",
        1909,
        929,
        "#f5f5f6"
      ]
    }
  ]
}
[/block]
This page, accessible via the Builds menu option under Pipelines, shows the details of a completed build pipeline. Note the blue Artifacts button at the top right of the page. This is where the report will be stored with the build, and it can be downloaded as needed for any additional usage.

If you choose to generate a findings report as well, the exact same “Publish pipeline artifact” step can be added to the pipeline a second time to save that report as its own artifact, with the name insightappsec-scan-findings.json.

# Troubleshooting
###The extension doesn’t appear when I search for it while creating a pipeline.
The extension must first be installed under your organization in order for it to be available for usage in a pipeline. Go to the Azure DevOps homepage (https://dev.azure.com/organizationName) and click on Organization Settings, then select Extensions. Check to see if the extension is listed under the Installed tab. If not, then you can find it under its Visual Studio Marketplace Listing.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/d368da7-image21.png",
        "image21.png",
        1912,
        937,
        "#fcfcfc"
      ]
    }
  ]
}
[/block]
###The pipeline failed and I’m not sure why.
There are logs available within the Rapid7 InsightAppSec step of the pipeline that can tell you why the pipeline may have failed. Go into Pipelines under Builds or Releases, then select the build that failed. You can click the Rapid7 InsightAppSec step here to view all of the logs and any error messages that may have resulted in pipeline failure.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/e766656-image15.png",
        "image15.png",
        1914,
        937,
        "#e2e1e1"
      ]
    }
  ]
}
[/block]
###There are API errors occurring in the logs when running the pipeline.
API errors are most likely due to an issue with the connection that was setup to be used with this extension. In the Rapid7 InsightAppSec Connection that you created, double check the URL and the API key fields that were entered. The URL should be formatted as follows:
https://us.api.insight.rapid7.com/ias/v1

With the “us” value being the only thing that would potentially differ. This value is dependent on your region.  A full list of supported region codes is documented here: https://insight.help.rapid7.com/docs/product-apis#section-supported-regions

###I didn’t get any reports saved in Azure DevOps after my scan completed.
This could occur for a couple reasons:
The “Wait for scan completion” option wasn’t checked. This must be checked in order for reports to be generated.
The scan was considered a “failed scan” for any number of reasons, and reports are not generated for a failed scan. Check the logs for the InsightAppSec task to find out why the scan failed.
The pipeline is missing the Publish Pipeline Artifact step(s) required for saving those reports as artifacts. Though the reports are always generated for a successful scan, they are not saved as artifacts without the usage of Publish Pipeline Artifact. Refer to the extension’s configuration guide to see an example of this extra artifact step.

###The scan portion of the pipeline isn’t logging enough.
You can control the frequency of logging a scan’s status with the “Scan Status Interval” field. Inputting a 5 in this field will result in logging the scan’s current status every 5 minutes, for instance. The lower the number, the more frequent the logs. Other errors that occur during the scan will always be immediately logged, regardless of this number.

###The scan gating didn’t seem to work and my build was successful.
Double check the query that was input in the Vulnerability Query field. This requires a specific type of formatting that could result in the query not returning any results if not adhered to. Here’s an example of scan gating based on severity. Note the single quotes used.

`vulnerability.severity='LOW'`

Additional query options can be found in the InsightAppSec API documentation. Only filters for the Vulnerability Resource Type should be leveraged.

###The pipeline immediately went to the next step upon launching the scan, without giving any scan status updates.
To receive logging with scan status updates, you must check the “Wait for scan completion box?” and provide a “Scan Status Interval” during configuration. Otherwise the pipeline will proceed to the next task immediately after launching the scan in InsightAppSec.

Immediately moving on to the next task can be helpful in environments where no gating or feedback to Azure DevOps is necessary and teams only want to trigger scans when new changes are made available.

###The logs say that my scan timed out.
Failing the scan on timeout is an option included in the extension. If it timed out, then the scan is taking longer than expected to complete based on this configuration. You can either uncheck the “Fail scan on timeout?” option, or increase the “Timeout” number. It may also be worth double-checking whether the scan was in a state of PENDING for a long time, since this could indicate some amount of time was lost due to issues with engine availability.

###There’s an error that mentions an invalid application or scan configuration.
This is most likely an issue with the value input for the Scan Configuration during setup. This field is not a dropdown option, but rather is a plain text input field. This means that there’s the potential for mistakes or typos in this field. It’s also possible that the scan configuration and/or application were deleted since the last time the task was configured.

# Support
Need help? We’ve got you covered. Sign into the Customer Portal for our top recommended help articles, and to connect with our awesome Support Team.

**Create and manage your cases with ease** and get routed to the right product specialist.
[CUSTOMER PORTAL SIGN IN](https://rapid7ipimseu.okta-emea.com/home/salesforce/0oa2eo6xizl7cdqH40i7/46)
**Introducing the Scheduler:** Customers can now schedule time with a support engineer, directly in the Customer Portal. [Learn how](https://kb.help.rapid7.com/docs/schedule-a-meeting-with-our-support-team).

### Having trouble logging in?
  * [Create your account](https://kb.help.rapid7.com/page/using-the-customer-portal#section-my-support-account-doesn-t-work-anymore)
  * [Reset your password](https://insight.rapid7.com/login)
  * [Customer Portal FAQs](https://kb.help.rapid7.com/page/using-the-customer-portal#section-faqs)