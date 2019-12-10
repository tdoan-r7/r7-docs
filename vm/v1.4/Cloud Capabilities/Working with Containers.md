---
title: "Working with Containers"
excerpt: ""
---
A container represents a software application and may contain all of the necessary code, run-time, system tools, and libraries needed to run the application. 

Using containers to manage application deployment is a rapidly growing technology, but Container hosts may be packed with risk. InsightVM provides visibility into vulnerabilities and risk associated with the components and layers of a container. 

You can use InsightVM to:

  * Discover which assets are acting as container hosts in your environment.
  * Increase the visibility of where your container hosts live so you can manage your container problems.
  * Identify your running or stopped containers. 
  * Identify container hosts that do not comply with CIS benchmarks for common OSes or comply with the official Docker CIS benchmark.
  * Provide visibility and risk associated with the packages and layers of a container.
  * Perform vulnerability assessment on the container image as it is built and deployed. 
  * Provide suggestions for remediation.
[block:api-header]
{
  "type": "basic",
  "title": "Supported registries"
}
[/block]
A registry contains one or more repositories. These repositories contain groups of container images. InsightVM supports the following registries:
  * Amazon EC2 Container Registry (ECR)
  * Azure Container Registry
  * Docker Hub
  * Privately Hosted Docker Registry 
  * Google Container Registry (GCR)
  * Quay.io 

[block:callout]
{
  "type": "info",
  "title": "NOTE",
  "body": "InsightVM can connect to other registries as long as they implement the proper Docker Registry protocol. If your desired registry is not listed here, confirm that it is compatible with Docker Registry HTTP API V2 before creating a connection."
}
[/block]

[block:api-header]
{
  "title": "Discovering containers"
}
[/block]
If you use containers in your environment, as part of your normal scanning process, InsightVM syncs to your containers so that you can see where your hosts live and begin to manage your container issues when necessary.  

Use the Asset details page to view your Containers.
[block:callout]
{
  "type": "warning",
  "title": "NOTE",
  "body": "The user credentials configured in your site configuration must have the necessary elevated privileges in order for the scan to run the commands that discover containers.  You can ensure that these privileges are in place by configuring your scan with one of the following options:\n\n* Scan with the root user\n* Scan with [privilege escalation](doc:elevating-permissions) using `sudo`, `su`, `sudo+su`, and others\n* Add the scan user to the container group, such as a Docker group"
}
[/block]

[block:api-header]
{
  "title": "Searching for containers"
}
[/block]
Use the **Filtered Asset Search** to search for containers. You can also search by container status and container image. 

You can also search for specific container images and repositories using the query search. To access this  search field, click the Containers icon, and then open the **Images Details** page or the  Repositories view. 

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/9084231-Containers_search.JPG",
        "Containers_search.JPG",
        1506,
        440,
        "#3f4857"
      ]
    }
  ]
}
[/block]

[block:api-header]
{
  "title": "Viewing containers"
}
[/block]
The Containers dashboard provides a quick view of all container host assets and lists of commonly deployed images and assets sorted by the number of running containers. 

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/c9538e7-Containers_dashboard.JPG",
        "Containers_dashboard.JPG",
        1008,
        596,
        "#414b59"
      ]
    }
  ]
}
[/block]
The Container dashboard displays the following cards by default:

  * **Most Commonly Deployed Images** - Displays the container images that are used the most.
  * **Image Assessment** - Displays the percentage of images that were assessed for vulnerabilities.
  * **Container Hosts** - Displays the number of assets that have the Docker software installed and can run containers, but may not be deployed.
  * **Assets with Deployed Containers** - Displays the number of active assets that have containers deployed and running.
  * **Most Vulnerable Images** - Displays container images that have the most vulnerabilities of the total scanned.

To view the Container dashboard:

  * Click the **Dashboard** icon. 
  * Click the **Dashboard** dropdown and choose the dashboard you want to view.

[block:callout]
{
  "type": "info",
  "body": "If this is the first time you are viewing the Container dashboard, go to the Rapid7 Recommends These Dashboard Templates area, click **Containers Dashboard**, give the dashboard a name and description, and then click **OK**.",
  "title": "Viewing the Container dashboard for the first time"
}
[/block]