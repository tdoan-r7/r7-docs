---
title: "overview"
excerpt: ""
---
# Jenkins Continuous Integration with AppSpider

The AppSpider Plugin for Jenkins allows you to configure settings to automatically trigger AppSpider scans when builds of your web application complete. This enables your team to find security defects earlier in the software development lifecycle and automatically assign those defects to developers for remediation.

The plugin is only available for AppSpider Enterprise.

Continuous Integration is a software development process in which developers on a team can integrate their work frequently. Each integration is verified by an automated build, one or more times per day. Many organizations that adopt this approach accelerate the software development process through automation and allow a team to develop cohesive software more rapidly thus streamlining QA efforts and reducing cost and time to market.

Jenkins is an open source continuous integration tool written in Java. Builds can be started by various means, including being triggered by commit in a version control system, by scheduling via a cron-like mechanism, by building when other builds have completed, and by requesting a specific build URL.

# Installation Instructions

There are 2 methods of installing the AppSpider Plugin for Jenkins Continuous Integration.

## Installation Method 1

When using this method, an HPI file is required to successfully install the AppSpider plugin for Jenkins.

1. Clone the git repository.  
  
`https://github.com/rapid7/jenkinspider.git`

2. Change the directory to the jenkinspider repository.  
  
`$ cd jenkinspider`

3. Build the hpi file. For first time build run:  
  
`$ mvn hpi:run`

4. When the build is complete, cancel the session by typing **CTRL + C**. This step is needed to generate the necessary folder. 
 

If the build is successful, the hpi file is located at _target/jenkinspider.hpi_. For successful builds, you'll be able to run:

`$ mvn hpi:hpi`

## Installation Method 2 
 

1. Open Jenkins in a browser.

2. Select **Manage Jenkins**.

![](https://help.rapid7.com/appspider/content/resources/images/jenkins/Manage Jenkins.jpg)

1. Select **Manage Plugins**.

![](https://help.rapid7.com/appspider/content/resources/images/jenkins/Manage plugin.jpg)

1. In the plugin page, select the **Available** tab.

![](https://help.rapid7.com/appspider/content/resources/images/jenkins/Available tab.jpg)

1. Locate the _AppSpider Plugin_ and select the corresponding checkbox. You can scroll down, or type _AppSpider_ in the filter textbox.

2. Depending on how your Jenkins installation is set up, you may or may not need to restart Jenkins after installing the plugin. See your organization's Jenkins administrator for more information. Depending on your organization's needs, select either **Install without restart** or **Download now and install after restart**.

![](https://help.rapid7.com/appspider/content/resources/images/jenkins/Install.jpg)

## Setting up the global configuration 
 

Configure global settings and paths in order to trigger AppSpider scans when builds complete.

1. Select **Manage Jenkins**.

![](https://help.rapid7.com/appspider/content/resources/images/jenkins/03000001.png)

1. Select **Configure System**.

![](https://help.rapid7.com/appspider/content/resources/images/jenkins/03000002.png)

1. Scroll down to **AppSpider Global Configuration** and provide the requested information.

![](https://help.rapid7.com/appspider/content/resources/images/jenkins/03000003.png)

- **AppSpider Rest Url** : The RESTful API url used by AppSpider Enterprise.

- **Username** : The username used to log into AppSpider Enterprise. 
 
- **Password** : The password used to log into AppSpider Enterprise.

1. Save the settings.

## Configuring an existing build to initiate an AppSpider scan

Builds can be configured to kick off AppSpider scans by selecting the appropriate AppSpider scan configuration.

1. Open an existing build and select **Configure**.

![](https://help.rapid7.com/appspider/content/resources/images/jenkins/03000004.png)

1. Scroll down to the **Post-Build Actions** section.

![](https://help.rapid7.com/appspider/content/resources/images/jenkins/03000005.png)

1. From the **Post-Build Actions** dropdown, select **Scan build using AppSpider**.

![](https://help.rapid7.com/appspider/content/resources/images/jenkins/03000006.png)

 

1. Provide the requested information in the **Scan build using AppSpider** section.

![](https://help.rapid7.com/appspider/content/resources/images/jenkins/03000007.png)

- **Scan configuration** : A list of all available scan configurations in AppSpider Enterprise.

- **Report name** : After a successful scan, AppSpider will generate an xml report. This is what Jenkins will rename the xml report to.

- **Run the scan after the build finish?** : If selected, after a successful build, this will trigger an AppSpider scan to the build. Otherwise, the build will continue.

- **Obtain the report after the scan finished?** : If this option is selected, Jenkins will obtain the report generated by AppSpider and placed it on the build workspace.

5. Select **Save**.

## Creating a new scan configuration 
 

You can use the _Create a new scan configuration through the plugin_ option instead of using an existing scan configuration in AppSpider Enterprise.  The scan configuration will be created in AppSpider Enterprise by the plugin. These will all be simple scan configurations (no authentication) with standard options.

1. Select **Create new scan configuration**.

![](https://help.rapid7.com/appspider/content/resources/images/jenkins/03000008.png)

- **Name** : Name of the new scan configuration.

- **Url** : The URL that AppSpider will scan.

- **Scan Engine Group** : A list of all available scan engine groups in AppSpider Enterprise.  
  
- Select the **Validate** button to ensure that the url entered is valid and can be reached by AppSpider Enterprise.

- Select **Save**.