---
title: "Managing Container Images"
excerpt: ""
---
The Container details view displays information about all of your  container images and their associated repositories. You can also view details for specific images and repositories, assess images when necessary, and manage container registry connections.

[block:callout]
{
  "type": "info",
  "body": "If you cannot select an image ID, you may need to add a registry connection.",
  "title": "Selecting an image ID"
}
[/block]
The images details default to the Images view which displays all of the public and private Container images in your environment. Additionally, you can click the **Assessed** filter to view status or the **Not Assessed** filter to view images that were not assessed.  If an image is not assessed, the **Assess** button is available.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/0027a04-Containers_details.JPG",
        "Containers_details.JPG",
        1808,
        425,
        "#3f4957"
      ]
    }
  ]
}
[/block]
The Images view, and the **Assessed** and **Not Assessed** filters display the following information:
  * ID - Displays the image ID. 
  * Repository - Displays the name of the Repository where the image resides.
  * Tags - Displays the tags associated with this image. Note that only up to four tags will display. Additional tags will not display. . 
  * Risk Score - Displays the image calculated risk score. See the Risk Scoring FAQ for more information.
  * Vulnerabilities - Displays the number of known vulnerabilities for this image. The options are Moderate, Severe, or Critical. Hover over the number in this column to see the breakdown of these vulnerabilities. 
  * Critical, Severe, and Moderate - Displays the vulnerability breakdown for the selected image. These are the same numbers that appear if you hover over an item in the Vulnerabilities column. 
  * Operating System - Displays the operating system on which the image is based.
  * Hosts - Displays the number of hosts that are running on this image.
  * Packages - The number of installed system packages and software.
  * Size - Displays the size of this image.
  * Created On - Displays the date on which the image was created.
  * Assessment - Displays the assessed status for an image. If this column  is blank for an image, the assessment is complete. If an Assess button appears, the image is not yet assessed. Press to begin assessing the image. A spinner appears while the assessment is in progress. 
[block:api-header]
{
  "title": "Viewing image details"
}
[/block]
Use the "Containers > Images" view to view image details.  

To view image details:

1. Click the **Container** icon. The Container details page opens to the Images view. 
2. Click an item in the **ID** column. The Image Details view opens to display the **Images Details** panel and the related views.


[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/a4d727d-Container_Image_Details_panel.JPG",
        "Container_Image Details panel.JPG",
        1857,
        604,
        "#404957"
      ]
    }
  ]
}
[/block]
Image details include the **Registry**, **ID**, **Created date**, **Layers**, **Operating System**, **Size**, **Format**, and **Tags**. You can also click a row in this view to open a panel that displays vulnerabilities information for an image. 

Additionally, you can view the following filters:
  * The **Packages** filter displays information about the software packages that are contained in the image and the current aggregated status. Click a row in this view to open a panel that displays Vulnerabilities, including Vulnerability Name, Published On date, and Risk Score. 
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/3fee925-Container_packages.JPG",
        "Container_packages.JPG",
        1520,
        402,
        "#3d4753"
      ]
    }
  ]
}
[/block]
 * The filter that displays the repository name displays repository details, including Tags, Risk Score, Vulnerabilities, OS, Packages, Layers, Size, and Created On date. If necessary, you can also Assess a repository in this view.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/6993bfd-Containers_lib_node.JPG",
        "Containers_lib_node.JPG",
        1851,
        458,
        "#404a58"
      ]
    }
  ]
}
[/block]
  * The **Layers** filter displays a history of revisions to an image, displayed in the order that the change is made. You cannot modify the original image, so when a changes is made, a new image ID is created. If a layer does not display any vulnerability information, it means that that the new layer did not require any package changes. Click a row in this filter to open a panel that displays Basic Information, Vulnerabilities, and the Commands added to the associated layer. 
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/0d67d9c-Containers_layers.JPG",
        "Containers_layers.JPG",
        1538,
        357,
        "#3d4755"
      ]
    }
  ]
}
[/block]
  * The **Vulnerabilities** filter displays information about the vulnerabilities for this image. Click a row in this filter to open a panel that displays Basic Information, including a Description of the vulnerability, Categories, and CVSS.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/e57e643-Containers_vulnerabilities.JPG",
        "Containers_vulnerabilities.JPG",
        1516,
        430,
        "#3e4856"
      ]
    }
  ]
}
[/block]
  * The **Hosts** filter displays lets you view and manage the hosts that deployed this image. Click a row in this filter to display  Asset Details for this host.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/575de96-Container_host.JPG",
        "Container_host.JPG",
        1518,
        299,
        "#3d4855"
      ]
    }
  ]
}
[/block]

[block:api-header]
{
  "title": "Assessing an image"
}
[/block]
If the image is accessible, the system will assess it for vulnerabilities and update when the scan is done. If the image is not accessible, a window appears. You'll need to add a registry connection to allow InsightVM to pull the image (recommended), or manually upload the image using the output of the docker save command.
[block:callout]
{
  "type": "warning",
  "title": "NOTE",
  "body": "You can't view images that are not attached to a container in your environment or repository, so the window is only accessible from a container."
}
[/block]
You may need to assess an image if it is in a private repository and a registry connection is not configured to allow access to it.  You can also reassess an image if necessary.
**Note:** The Assess button only appears if an image has not been assessed. 

To assess an image: 

1.Click the **Container** icon. 
2. Click the **Assess** button located in the **Assessment** column.
[block:callout]
{
  "type": "warning",
  "body": "Microsoft Windows based images are not currently supported. Detailed information and assessment results for these images will not be available."
}
[/block]

[block:api-header]
{
  "title": "Reassessing an image"
}
[/block]
To reassess an image: 

1.Click the **Container** icon. 
2. In the **ID** or **Tags** column , click the image that you want to reassess. 
3. Click the **Reassess Image** button located on the "Image Details" view.

If the image is accessible, the system will assess it for vulnerabilities and update when the scan is done. If the image is not accessible, a window appears. You'll need to add a registry connection to allow InsightVM to pull the image. 
[block:api-header]
{
  "title": "Viewing repositories"
}
[/block]
Use the **Repositories** view to display all of your repositories, both public and private, from the supported registries. Registries store repositories; repositories contain images. Click a specific registry filter to view registries by vendor. You can also click any line in this view to open a panel that displays Basic Information, Tags, and Images.


[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/2c722c3-Containers_repos.JPG",
        "Containers_repos.JPG",
        1826,
        510,
        "#3d4754"
      ]
    }
  ]
}
[/block]
The Repositories view and individual repository filters share the following information: 
  * Repository - The name of the repository.
  * Description - A description of the repository.
  * Tags - The tags associated with this repository. You can click a tag to view details about the the images in its repository.
  * Vendor - The vendor associated with this repository.

[block:api-header]
{
  "title": "Viewing repository details"
}
[/block]
Repository details include information about the Registry, ID, Vulnerabilities, OS/Version, Layers, Size, Image Format, and Created On date. You can also manage connections and assess a repository, if necessary.


[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/a43b6b9-Container_repo_details.JPG",
        "Container_repo_details.JPG",
        1834,
        579,
        "#404958"
      ]
    }
  ]
}
[/block]
The Repositories Details view displays the following information:

  * ID - Displays the repository ID. 
  * Tags - Displays the tags associated with this repository.
  * Risk Score - Displays the calculated risk score. See the Risk Scoring FAQ for more information.
  * Vulnerabilities - Displays the number of known vulnerabilities for this repository. The options are Moderate, Severe, or Critical. Hover over the number in this column to see the breakdown of these vulnerabilities. 
  * Critical, Severe, and Moderate - Displays the vulnerability breakdown for the selected repository. These are the same numbers that appear if you hover over an item in the vulnerability column. 
  * Operating System - Displays the operating system on which the repository is running.
  *  Hosts - Displays the number of active hosts for this image.
  * Packages - The number of installed system packages and software.
  * Size - Displays the size of this repository.
  * Created On - Displays the date on which the repository was created.
  * Assessment - Displays the assessed status for a repository. If there is an Assess button, click it to assess this repository.  

To view repository details: 

1. Click the **Container** icon. 
2. Click **Repositories**.  The **Repository Details** view opens. 
3. Click an item in the **Repository** column to see the details.