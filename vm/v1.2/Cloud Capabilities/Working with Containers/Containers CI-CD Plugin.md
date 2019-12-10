---
title: "Containers CI/CD Plugin"
excerpt: ""
---
#Overview

InsightVM features a container assessment plugin that you can utilize via a Continuous Integration, Continuous Delivery (CI/CD) tool. Use this plugin to analyze a container image for vulnerability assessment on the Insight platform.

The plugin has the following capabilities:
  * Configure custom rules for compliant container images
  * Trigger build actions based on compliance to your rules
  * Generate an assessment report

Container assessment plugin results are available both through your CI/CD tool and the Builds tab of InsightVM’s “Containers” screen.

#Whitelist Platform Traffic

The plugin uses the following hostnames to communicate with the Insight platform:
[block:parameters]
{
  "data": {
    "h-0": "Region",
    "h-1": "Hostname",
    "0-0": "United States",
    "1-0": "Europe",
    "4-0": "Australia",
    "3-0": "Japan",
    "2-0": "Canada",
    "0-1": "us.api.insight.rapid7.com",
    "1-1": "eu.api.insight.rapid7.com",
    "2-1": "ca.api.insight.rapid7.com",
    "3-1": "ap.api.insight.rapid7.com",
    "4-1": "au.api.insight.rapid7.com"
  },
  "cols": 2,
  "rows": 5
}
[/block]
In order for the plugin to transmit data, you must configure your network to allow traffic to the corresponding hostname of your designated InsightVM region.

[block:callout]
{
  "type": "info",
  "title": "NOTE",
  "body": "The region you chose for your plugin MUST match the region that has been selected previously in InsightVM. The plugin cannot communicate through a different region."
}
[/block]
#Install and Configure

Complete the following steps to configure your Jenkins plugin:
1. [Generate the Rapid7 API key](doc:containers-cicd-plugin#section-generate-the-rapid7-api-key)
2. [Install and configure the Jenkins plugin](doc:containers-cicd-plugin#section-install-and-configure-the-jenkins-plugin)

##Generate the Rapid7 API key

To use the Jenkins plugin, you need the Rapid7 API key to access the Rapid7 platform. 

In order to access the Rapid7 platform, you will need a Rapid7 Insight platform account, which is different from your InsightVM Rapid7 Security Console account. 

Here's how to get a Rapid7 Insight platform account: 
*  If you are an InsightIDR, InsightAppSec, InsightOps, or InsightPhish customer, you already have a Rapid7 Insight platform account. You can link your existing InsightVM Security Console to the Rapid7 Insight platform account you created with your other Rapid7 product by following the instructions here:
https://insightvm.help.rapid7.com/docs/activating-your-console-on-the-insight-platform
*  If you are already using the cloud capabilities of InsightVM and don’t have a Rapid7 Insight platform account, contact the [Rapid7 Technical Support team](https://rapid7support.force.com/customers/login) to request one. 

Follow these steps to generate the Rapid7 API key: 

1. Go to [https://insight.rapid7.com/platform#/ ](https://insight.rapid7.com/platform#/ )
2. Log in to your Rapid7 Insight platform account.  
3. Go to [API Keys](https://insight.rapid7.com/platform#/apiKeyManagement). 
4. Under **Organization Key**, click on **New Organization Key**. 
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/7a929d8-api_interface.png",
        "api_interface.png",
        3168,
        698,
        "#ebf0f2"
      ]
    }
  ]
}
[/block]
5. In the “Organization” dropdown menu, select your InsightVM organization name.
6. Enter a name for your key in the field. 
7. Click **Generate**. 
8. Copy and save the provided API Key.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/dec3c36-copy_api_obscured.png",
        "copy_api_obscured.png",
        1145,
        475,
        "#f4f6f7"
      ]
    }
  ]
}
[/block]

[block:callout]
{
  "type": "info",
  "title": "NOTE",
  "body": "This is the only time you will be able to see the API key, so store it in a safe place. If you misplace your API key, you can always generate a new one."
}
[/block]
9. Click Done. 
10. Your new API key will display in the “Organization Key” table. 

##Install and configure the Jenkins plugin 

Before starting, you will need the following Jenkins plugins: 

  * [https://plugins.jenkins.io/plain-credentials](https://plugins.jenkins.io/plain-credentials) version 1.4 (or compatible)
  * https://plugins.jenkins.io/docker-java-api version 3.0.14 (or compatible)

After generating your API key, follow these steps to install and configure the Jenkins plugin:
[block:callout]
{
  "type": "info",
  "title": "NOTE",
  "body": "This procedure requires administrator privileges in Jenkins.\nJenkins version **2.89.3** is the minimum supported version."
}
[/block]
1. [Download the plugin](http://download2.rapid7.com/download/InsightVM/rapid7-insightvm-container-assessment-1.0.1.hpi) from Rapid7 website. Verify your download with [MD5](http://download2.rapid7.com/download/InsightVM/rapid7-insightvm-container-assessment-1.0.1.hpi.md5) or [SHA1](http://download2.rapid7.com/download/InsightVM/rapid7-insightvm-container-assessment-1.0.1.hpi.sha1).
2. Log into Jenkins as an admin user.
3. Click **Manage Jenkins** in your navigation menu.
4. On the “Manage Jenkins” page, click **Manage Plugins**.
5. Click the **Advanced** tab.
6. Under the “Upload Plugin” section, click **Choose file** to browse to the Rapid7 Jenkins plugin. 
7. Click **Upload**. 
8. Select the “Restart Jenkins” option. 
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/f32c950-restart_Jenkins_annotated.png",
        "restart_Jenkins_annotated.png",
        2133,
        693,
        "#f8f7f7"
      ]
    }
  ]
}
[/block]
9. After Jenkins restarts, return to the “Manage Jenkins” page.
10. Click **Configure System**.
11. Scroll to the “Rapid7 InsightVM Container Assessment” section.
12. In the “InsightVM Region” field, select the region that InsightVM uses to access the platform.
13. In the “Insight Platform API Key” field, click **Add**. In the dropdown menu, select “Jenkins” to configure the Insight platform API key that you generated earlier. 
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/bfb5753-jenkins_token_obscued.png",
        "jenkins_token_obscued.png",
        1173,
        230,
        "#f8f9f9"
      ]
    }
  ]
}
[/block]
14. In the window that appears, complete these fields:
  a. In the “Domain” field, select "Global credentials (unrestricted)."
  b. In the “Kind” field, select "Secret text."
  c. In the "Scope" field, select “Global (Jenkins, nodes, items, all child items, etc).” 
  d. In the “Secret” field, enter your API key.
  e. Leave the “ID” field blank.
  f. Enter a description for your reference.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/b8e3df0-global_credentials.png",
        "global_credentials.png",
        1131,
        420,
        "#efebeb"
      ]
    }
  ]
}
[/block]
15. Click **Add**.
16. Select your newly configured credential from the dropdown menu.
[block:callout]
{
  "type": "info",
  "title": "NOTE",
  "body": "Click **Test Connection** to verify that the region and token are valid."
}
[/block]
17. Click Save to complete your plugin configuration.

#Job Setup

You must configure your build jobs to use the plugin after installation. Complete the steps for your chosen CI/CD tool:

##Jenkins Build Job Setup
The plugin supports the following Jenkins build methods:

###Freestyle Build
“Freestyle” is the classic job builder. Build steps can be added or removed via the user interface:

1. In a new or existing job, click **Add build step**.
2. Select **Assess Container Image with Rapid7 InsightVM**. This will add a build step with a blank configuration.
3. Configure the items under “Options” as desired.
4. Click **Add** under the respective “Rules” section to configure the conditions that will trigger a build action. Two rule types are available:
  * “Threshold Rules” - Sets a numeric limit. Values that exceed this limit will trigger the build action.
  * “Name Rules” - Matches text using the “contains” operator. A match will trigger the build action.

[block:callout]
{
  "type": "info",
  "title": "NOTE",
  "body": "The order of your configured rules will not matter when the job is run. Any individual rule can trigger the build action specified."
}
[/block]

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/054b8d1-add_build_step_copy.png",
        "add_build_step copy.png",
        950,
        567,
        "#f2f1f1"
      ]
    }
  ]
}
[/block]
5. Click Save when finished.

###Pipeline Build

The “Pipeline” method involves generating build step scripts from the plugin and adding them to the existing Pipeline script:

1. In a new or existing job, browse to the “Pipeline” section.
2. Click **Pipeline Syntax** below the “Script” field.
3. Open the dropdown next to “Sample Step” and select "assessContainerImage: Assess Container Image with Rapid7 InsightVM". 
4. Configure your build options and rules in the same manner as before.
5. Click **Generate Pipeline Script** when finished.
6. Add your new step script to the existing Pipeline script.  
[block:code]
{
  "codes": [
    {
      "code": "// Assess the image\n       assessContainerImage failOnPluginError: true,\n           imageId: \"${my_image.id}\",\n           thresholdRules: [\n              exploitableVulnerabilities(action: 'Mark Unstable', threshold: '1')\n            ],\n            nameRules: [\n              vulnerablePackageName(action: 'Fail', contains: 'nginx')\n           ]\n",
      "language": "text",
      "name": "Pipeline Script"
    }
  ]
}
[/block]
7. See the following example for correct location and syntax:
[block:code]
{
  "codes": [
    {
      "code": "node {\n   // Define a variable to use across stages\n   def my_image\n   stage('Build') {\n       // Get Dockerfile and code from Git (or other source control)\n       checkout scm\n       // Build Docker image and set image reference\n       my_image = docker.build(\"test-app:${env.BUILD_ID}\")\n       echo \"Built image ${my_image.id}\"\n   }\n   stage('Test') {\n       // Assess the image\n       assessContainerImage failOnPluginError: true,\n           imageId: \"${my_image.id}\",\n           thresholdRules: [\n              exploitableVulnerabilities(action: 'Mark Unstable', threshold: '1')\n            ],\n            nameRules: [\n              vulnerablePackageName(action: 'Fail', contains: 'nginx')\n           ]\n   }\n   stage('Deploy') {\n       echo \"Deploying image ${my_image.id} to somewhere...\"\n       // Push image and deploy a container\n   }\n}\n",
      "language": "text",
      "name": "Pipeline Script Example"
    }
  ]
}
[/block]
8. Click Save when finished.
[block:callout]
{
  "type": "info",
  "title": "NOTE",
  "body": "Threshold rules must be unique per type. For example, you cannot have two rules for Critical Vulnerabilities. Only one instance of the rule will be applied."
}
[/block]
#View Assessment Results

After running a build, you can view assessment results in the following ways:

##Assessment Results in Jenkins
Jenkins will generate an assessment report once the build finishes.

1. Open the individual build that ran the plugin.
2. Click **Rapid7 Assessment** on your navigation menu.

##Assessment Results in InsightVM
The results of your build jobs are viewable on the Builds tab of the “Containers” screen in InsightVM. See [Containers Build Interface](doc:containers-build-interface): to learn more about this feature.