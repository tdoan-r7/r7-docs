---
title: "Container Image Scanner"
excerpt: ""
---
The Container Image Scanner is a Docker image that can collect information about images. You can run the Container Image Scanner locally or as part of a CI/CD build pipeline. Once the image is scanned, it will send this data to InsightVM and assess these images in the cloud. You’ll find your assessment findings as a JSON-formatted output in your terminal.

#Benefits
You can use the Container Image Scanner to: 
* Scan container images with almost any CI/CD system. 
* Enable quality gating to prevent images with vulnerabilities from being published or used in production. 
* Run anywhere with access to InsightVM.

#Things to Know
The Container Image Scanner has the following characteristics: 

* It outputs results in terminal. 
* It captures results in a command line interface. 
* It needs to be manually run per use.
* You can automate it through scripting in your CI/CD system.

#Requirements
To use this component, you need the following items:  
* A Docker host to run the application, such as Docker, Docker Swarm, or Kubernetes.
* An Insight account that is registered to Insight platform - the Security Console must also be activated on the Insight platform.
* A Rapid7 API Key.
[block:callout]
{
  "type": "info",
  "title": "Note",
  "body": "The region you specify must match the region that has been selected previously in InsightVM."
}
[/block]
Before starting, confirm that the following requirements are met: 
* Ensure that you can pull and run Docker images from public Docker Hub repositories.
* Ensure that you have [activate your console on the Insight platform](doc:activating-your-console-on-the-insight-platform) activated your Security Console on the Rapid7 Insight platform].
After activation, you will use the API key for Docker integration. 

If you meet the above requirements, proceed to the “Generate a Rapid7 API Key” section of this page.

[block:callout]
{
  "type": "info",
  "title": "NOTE",
  "body": "You’ll use the Rapid7 API key to access the Rapid7 Insight platform API. In order to access the Insight platform, you will need a [Rapid7 Insight account, which is different from your Security Console account](doc:activating-your-console-on-the-insight-platform#section-understand-different-user-identifications)."
}
[/block]
##Generate a Rapid7 API Key

After activating or signing in to your Insight account, you’ll need to [generate an API key](doc:managing-platform-api-keys#section-generating-an-organization-key), which will display in the “Organization Key” table. Keep it handy, since you’ll need a copy to integrate the Docker image with your Insight account in the “Deploy the Registry Sync App” section.

[block:callout]
{
  "type": "danger",
  "title": "Alert",
  "body": "If you lose or forget your API key, you will need to revoke it and generate a new one."
}
[/block]
#Deploy the Container Image Scanner
Follow these instructions to deploy the Docker image: 

1. [Access the docker image at DockerHub](https://hub.docker.com/r/rapid7/container-image-scanner) ([https://hub.docker.com/r/rapid7/container-image-scanner](https://hub.docker.com/r/rapid7/container-image-scanner)).
2. With your Rapid7 API key handy, follow the [deployment and usage instructions](https://hub.docker.com/r/rapid7/container-image-scanner) (https://hub.docker.com/r/rapid7/container-image-scanner).   

##Run the Container Image Scanner with Parameters 
When launching the container in order to configure the app, you must pass the configuration as parameters. See the [Container Image Scanner Docker Hub page](https://hub.docker.com/r/rapid7/container-image-scanner) ([https://hub.docker.com/r/rapid7/container-image-scanner](https://hub.docker.com/r/rapid7/container-image-scanner))for run commands and technical details. After running the container, the JSON output will print to `stdout`.
[block:callout]
{
  "type": "info",
  "title": "Tip",
  "body": "You can capture the JSON output with shell redirection or pipes."
}
[/block]