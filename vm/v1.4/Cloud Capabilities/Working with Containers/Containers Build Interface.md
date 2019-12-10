---
title: "Containers Build Interface"
excerpt: ""
---
#Overview

Container assessment results provided by the CI/CD Jenkins plugin are shown in a dedicated space on the Builds tab of the “Containers” screen.  
[block:callout]
{
  "type": "info",
  "title": "Still need to install the plugin?",
  "body": "See our [Containers CI/CD Plugin page](doc:containers-cicd-plugin) for instructions."
}
[/block]
#View all builds
On your “Containers” screen, click the **Builds** tab.

A table displays all build jobs that have been configured and run with the container assessment plugin. Relevant data includes the latest image assessed, build system, build date, compliance status, and the number of vulnerabilities found.

Click any of the compliance status tabs to filter the “Jobs” table to display only those corresponding records.

##View job details
Click a link in the “Build Job” column to inspect that particular job in detail.

The “Build Job Details” screen has the following features:

  * The results of the latest build will be shown with compliance statuses for each configured rule.
  * The “Build History” graph details several assessment data trends for your job.  Use the provided dropdown to switch between available graphs.
  * The “Assessed Job Builds” table records all builds that have been run for your job.  Click any of these rows to inspect the compliance results of individual rules.

#Build Compliance in Image Details

The latest build results are also viewable from the “Image Details” screen of applicable container images.

1. On your **Images** tab, click the ID of any image denoted with a “B” symbol to inspect it.
2. Images that have been assessed with the plugin will feature an additional **Build Compliance** tab, along with the latest overall compliance result.  Click this tab to inspect individual policy rules and their corresponding build actions.
3. If desired, click the name link of the build job to navigate directly to the relevant “Build Job Details” screen for this container image.