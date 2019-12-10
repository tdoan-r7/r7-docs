---
title: "Jenkins Integration"
excerpt: ""
---
The InsightAppSec Jenkins plugin provides an easy way to integrate your build process with the InsightAppSec REST API. Using this plugin, Jenkins can automatically run a scan against your web apps and make a decision about the pass/fail status of the build based on the scan result. This decision can be made by using different rules, for example, the maximum number of vulnerabilities found or thresholds of vulnerability severity.

## Prerequisites
To use the plugin you will need:
* A user account on the Insight Platform with `Read Write` or `Admin` access.
* Access to InsightAppSec. Note that free trial users are unable to start a scan via the API and so may not use the plugin.

## Installation
The plugin may be installed using the plugin manager. For more information, see https://plugins.jenkins.io/insightappsec. 

Additionally, the plugin can be installed by manually building the `hpi` file and uploading to your Jenkins installation.

## Usage
There are two ways to use this integration - as a build step of a freestyle project, or as part of a pipeline. 

### Freestyle Project
You can use the plugin as a build step of a freestyle projectAfter opening a freestyle project, enable the plugin by selecting** Add build step** in the dropdown menu and select "Scan using InsightAppSec".

You will then be presented with the plugin configuration pane. The configuration options are as follows:
* **Data Storage Region** [required] - The data storage region of the target InsightAppSec instance.
* **Insight API Key** [required] - The Insight API Key you wish to use for scanning. More information on Jenkins-managed Insight API Keys can be found [here](doc:jenkins-integration#section-the-jenkins-managed-insight-api-key).
* **App** [required] - The app containing the scan config you wish to scan. Provided the region and API key are compatible, a list of apps that the API key has access to will pre-populate in the dropdown. This may take some seconds to load. 
* **Scan Config** [required] - The existing scan config you wish to scan. Provided the region and API key are compatible, as well as having previously selected an app, the scan configs belonging to the selected app will pre-populate in the dropdown. This may take some seconds to load.
* **Advance build when** [required] - This configuration option augments how the build advances based on the status of the scan submitted. There are four options to choose from:
    * **Scan has been submitted** - Advance the build when the scan has been submitted successfully.
    * **Scan has been started** - Advance the build when the scan has been started successfully.
    * **Scan has been completed** - Advance the build when the scan has been completed successfully.
    * **Vulnerability query has returned no vulnerabilities** - Advance the build when the scan has been completed and the vulnerability search query has returned no vulnerabilities. 
* **Vulnerability query** [optional] - An InsightAppSec search query may be supplied to search vulnerabilities found by the scan. For example, if you wish to fail the build when high severity vulnerabilities have been found, use: `vulnerability.severity='HIGH'`.
The query supplied will automatically be scoped to the scan. For more information on vulnerability search queries, consult the InsightAppSec API search documentation [here](https://help.rapid7.com/insightappsec/en-us/api/v1/docs.html#tag/Search). 
If left blank, the build will fail when **any** vulnerabilities have been found in the scan.
[block:callout]
{
  "type": "warning",
  "body": "This option is ignored unless \"Vulnerability results query has returned no vulnerabilities\" has been selected as the build advance option.",
  "title": "Note"
}
[/block]
* **Max scan pending duration** [optional] - A max scan pending duration may be provided so that the length of time the CI process takes to provide feedback can be controlled. The duration will take effect when the scan has been submitted. Upon reaching the duration, the scan will be cancelled and the build will fail.
The following format must be used for defining a duration: 
``` 
0d 5h 30m 
(d) - Days
(h) - Hours
(m) - Minutes
```
A quantity must be supplied for each of the above. For example:
```
1 day: 1d 0h 0m
5 hours: 0d 5h 0m
3 hours, 30 minutes: 0d 3h 30m
``` 
[block:callout]
{
  "type": "warning",
  "body": "This option is ignored if \"Scan has been submitted\" has been selected as the build advance option.",
  "title": "Note"
}
[/block]
* **Max scan execution duration** [optional] - A max scan execution duration may be provided to control the amount of time the CI process takes to provide feedback. The duration will take effect when the scan moves into scanning state. Upon reaching the duration, the in-progress scan will be stopped and the build will advance as normal. The format is the same as above.
[block:callout]
{
  "type": "warning",
  "body": "This option is ignored if \"Scan has been submitted\" or \"Scan has been started\" has been selected as the build advance option.",
  "title": "Note"
}
[/block]
* **Enable scan results** [optional] - This option is disabled by default. Use this as a flag to indicate if scan results should be viewable after a build has finished. When enabled, a new action to view scan results, labeled "InsightAppSec Scan Results" will appear.
[block:callout]
{
  "type": "warning",
  "body": "All users with access to view the build job history can view InsightAppSec scan results**. This option is ignored if \"Scan has been submitted\" or \"Scan has been started\" has been selected as the build advance option.",
  "title": "Note"
}
[/block]
### Pipeline
You can use the plugin as part of a pipeline. The following table describes the configuration options. 

| Field    | Valid Values                 | Required|                                                        
|----------|------------------------------|---------|
| `region` | `US` // united states <br> `EU` // europe <br> `AU` // australia <br> `CA` // canada <br> `AP` // japan  | true |  
| `insightCredentialsId`         |     < your credentials id >                         | true |
| `scanConfigId`         | < your scan config id>                              | true |
| `buildAdvanceIndictor`         | `SCAN_SUBMITTED` <br> `SCAN_STARTED` <br> `SCAN_COMPLETED` <br> `VULNERABILITY_QUERY` | true |
| `vulnerabilityQuery`         | A valid vulnerability search query| false |
| `maxScanPendingDuration`         | A duration string in the format described above | false |
| `maxScanExecutionDuration`         | A duration string in the format described above | false |
| `enableScanResults`         | `true` <br> `false` | false |

#### Example

Minimal configuration:
```groovy
insightAppSec region: 'US', insightCredentialsId: 'My ID', scanConfigId: 'f5984f53-2399-47e2-a6b9-010933cbc440', buildAdvanceIndicator: VULNERABILITY_QUERY
```

Full configuration:
```groovy
insightAppSec region: 'US', insightCredentialsId: 'My ID', scanConfigId: 'f5984f53-2399-47e2-a6b9-010933cbc440', buildAdvanceIndicator: VULNERABILITY_QUERY, vulnerabilityQuery: 'vulnerability.severity=\'HIGH\'', maxScanPendingDuration: '0d 0h 10m', maxScanExecutionDuration: '0d 10h 0m', enableScanResults: true
```

###The Jenkins Managed Insight API Key
This plugin provides a new type of managed Jenkins credential called the Insight API Key. A credential can be added while building a configuration or using the credentials manager.

####Build Configuration
During build configuration, use the **Add** button next to the "Insight API Key" field to open the credentials modal.
    
####Credentials Manager
1. From the Jenkins homepage, select "Credentials".
2. Select the desired scope, global is appropriate.
3. Click **Add Credentials**.
4. Select "Insight API Key" as the kind, then provide:
    * Name (A friendly name to refer to these credentials. For example, "Bob's API Key")
    * Insight API Key (the API Key to connect to the Insight Platform). Instructions for creating an API Key can be found [here](https://insight.help.rapid7.com/docs/managing-platform-api-keys).
[block:callout]
{
  "type": "warning",
  "title": "Note",
  "body": "When using the credentials manager there is a known UI issue that blocks the API Key field with the **OK** button, and you may need to resize the page to view it."
}
[/block]
## Development
To run the plugin locally, `cd` to the root directory and invoke:
```
mvn hpi:run
```
When the output shows `INFO: Jenkins is fully up and running` navigate to `http://localhost:8080/jenkins/` and you will see the sandbox Jenkins homepage.

## Additional References
* InsightAppSec API documentation: https://help.rapid7.com/insightappsec/en-us/api/v1/docs.html
* Jenkins plugin tutorial: https://wiki.jenkins.io/display/JENKINS/Plugin+tutorial