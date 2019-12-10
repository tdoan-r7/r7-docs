---
title: "Container Registry Sync App"
excerpt: ""
---
The Container Registry Sync app is a Docker image that can collect information about the images in a container registry in your environment. You can run the Container Registry Sync app locally to send data about your container images to InsightVM and assess these images in the cloud without exposing your network. You’ll find your assessment findings in InsightVM.  

#Benefits
The Container Registry Sync app circumvents the need to allow incoming connections from the InsightVM cloud to assess the container images in your private registry, which may be hosted on-premises or privately in the cloud. Your entire registry (or specific repositories) for multiple container images can be fingerprinted by the sync app on premises. 

You can use the Container Registry Sync app to: 
* Assess container images stored in on-premises registries without opening your network to InsightVM.
* Easily manage security controls for outbound data transfer, versus inbound data transfer.
* Only send image metadata to InsightVM, so your proprietary data does not leave your network.
* Use less bandwidth than registry connections. 

After deploying the application, here are some things to keep in mind regarding the Container Registry Sync app: 

* During the first run, the application will fingerprint all tagged images from a connected registry, no matter if it is associated with a running container or not.
* Recurring scans run every hour by default, unless you set a different time. Only new fingerprints are sent to InsightVM. 
* After fingerprints are collected, they are immediately sent to the Insight platform, where they are immediately assessed upon receipt. 

#Requirements
To use this component, you need:  
* A Docker host to run the application, such as Docker, Docker Swarm, or Kubernetes.
* An InsightVM account that is registered to Insight platform - the Security Console must be activated onto the Insight platform.
* A Rapid7 API Key.

Before starting, confirm that you: 
* Can pull and run Docker images from public Docker Hub repositories.
* [Activated your Security Console to the Rapid7 Insight platform](doc:activating-your-console-on-the-insight-platform). After activation, you will use the API key for Docker integration. 

If you meet the above requirements, skip to the “Generate a Rapid7 API Key” section.
[block:callout]
{
  "type": "info",
  "title": "Note - API key and the Insight Platform Access",
  "body": "You’ll use the Rapid7 API key to access the Rapid7 Insight platform API. In order to access the Insight platform, you will need a [Rapid7 Insight platform account, which is different from your Security Console account](doc:activating-your-console-on-the-insight-platform#section-understand-different-user-identifications)."
}
[/block]
##Generate a Rapid7 API Key

After activating or logging into your Insight platform account, you’ll need to [generate an API key](https://insight.help.rapid7.com/docs/managing-platform-api-keys#section-generating-an-organization-key), which will display in the “Organization Key” table. Keep it handy, since you’ll need a copy to integrate the Docker image with your Insight platform account in the “Deploy the Registry Sync App” section.
[block:callout]
{
  "type": "danger",
  "body": "If you lose or forget your API key, you will need to revoke it and generate a new one.",
  "title": "Alert"
}
[/block]
#Deploy the Registry Sync App
Use the following instructions to deploy the Docker image: 

1. [Access the docker image at DockerHub](https://hub.docker.com/r/rapid7/container-registry-sync-app) (https://hub.docker.com/r/rapid7/container-registry-sync-app).
2. With your Rapid7 API key handy, follow the [deployment and usage instructions](https://hub.docker.com/r/rapid7/container-registry-sync-app).   

##Configure the Registry Sync App
You must do one of the following when launching the container in order to configure the app: 
* Pass configuration as environment variables
* Pass configuration in a YAML file using a volume mount, which makes local files available to the container. For more information, [see Docker help docs](https://docs.docker.com/engine/reference/commandline/run/#mount-volume--v---read-only).  


See the [Registry Sync App Docker Hub page](https://hub.docker.com/r/rapid7/container-registry-sync-app) for configuration and technical details. Securing configuration data involves using secrets management tools. Due to the variety of methods available to secure environment variables or configuration files within a Docker host, doing so is outside the scope of this document.

#Monitor Status and Progress
Using Docker’s built-in logs, you can view progress or status messages about fingerprinting, as well as registry and API connections. Additionally, by exposing port 8080 from the container, you can access the embedded web server for the status of connections to the container registry, the Insight API, and available disk space. This can be used for automated monitoring and alerting.

For more information on containers, see our [Working With Containers help doc](doc:working-with-containers).