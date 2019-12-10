---
title: "Managing Container Connections"
excerpt: ""
---
You can view and manage your current registry connections and create new connections from the "Settings" page for connections. From the "Settings" page, you can also set up connections to your ticketing server to map each remediation status to a project status in your ticketing program. 
[block:api-header]
{
  "title": "Viewing connection settings"
}
[/block]
To access the "Settings" page, click the **Management** icon or the **Manage Connections** button on the "Repository Details" page. 


[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/c9d54fb-Container_settings1.JPG",
        "Container_settings1.JPG",
        1308,
        612,
        "#424c5b"
      ]
    }
  ]
}
[/block]
The "Connections" area displays all of your current connections and lets you add additional connections. 


  * To view all of your connections in the connection status area, click **All**. 
  * To view only your ticketing connections in the connection status area, click **Ticketing**. 
  * To view specific ticketing connections, click its name in the "Ticketing" area.
  * To view all of your registry connections in the connection status area, click **Registries**. 
  * To view all of the connections for a specific registry, click its name in the "Registries" section.
[block:api-header]
{
  "title": "Viewing the connection status"
}
[/block]
The connection status area lets you view, edit, and delete your current connections. This area contains the name of the connection, connection status, the type of connection, and repository credentials. 


Connections can have one of the following statuses:

  * **Connected** - Based on this configuration, containers are synchronized to InsightVM  based on your current scan schedule.
  * **Error Authorization failed** - Your authorization credentials may not be valid. See Editing a registry connection for more information.
  * **Not found** - The specified registry is not found. See Adding a registry connection to add a connection.
  * **SSL Handshake** - Your SSL Certificate may not be valid.
  * **Unknown** - This is an unidentified error.  Please contact our support team for assistance.
[block:api-header]
{
  "title": "Adding a repository configuration"
}
[/block]
You can add a repository configuration to a registry connection if you have limited access to specific repositories within a registry.
[block:callout]
{
  "type": "info",
  "body": "This is an optional step and should only be used if you cannot access all of your available repositories with a single credential."
}
[/block]
To add a repository configuration:

1. From the "Settings" page, locate the registry connection you want to modify and click **Edit**.
2. From the "Edit Registry" panel, click **Repositories Connection Settings**.
3. Click **New Configuration** and complete the necessary fields. 
4. Test the connection before you save it. If the test is successful, a success notification appears. If the test fails, an error notification appears. Check your credentials or connectivity and try again. 
5. Click **Save**.

The new repository connection appears in the list and in the Repository Credentials dropdown.
[block:api-header]
{
  "title": "Adding a registry connection of the same type"
}
[/block]
You can add an additional registry of the same type if you want to restrict access to a specific repository and not sync all the available repos for the original account, and then add a repository connection. See Adding a Repository Connection for more information.

To add a registry connection of the same type: 

1. From the "Settings" page, locate the registry connection you want to add and click **Add**.
2. On the Add Registry panel, click **Select an existing registry connection** and select a registry from the dropdown list. 
3. Click **OK**.
[block:api-header]
{
  "title": "Editing a registry connection"
}
[/block]
You can edit an existing registry connection if you need to change the connection settings.

To edit a registry connection:

1. From the "Settings" page, locate the registry connection you want to modify and click **Edit**.
2. From the "Edit Registry" panel, click **Registry Connection Settings**.
3. Edit the appropriate information. 
4. Test the connection before you save it. If the test is successful, a success notification appears. If the test fails,an error notification appears. Check your credentials or connectivity and try again. 
5. Click **Save**. 

You can add an additional registry of the same type if you want to restrict access to a specific repository and not sync all the available repos for the original account, and then add a repository connection.
[block:api-header]
{
  "title": "Deleting a registry connection"
}
[/block]
You can delete a connection at any time. You may want to delete a connection that has an error that you cannot repair or is no longer needed. If you delete a connection, you may have to assess the associated image and create a new connection if necessary. 

To delete a connection:

  * From the "Settings" page, find the connection you want to remove and delete it. When the confirmation message appears, click **Continue** to delete it.

[block:api-header]
{
  "title": "Modifying the registry connection fields"
}
[/block]
Use the following information for your specific registry to create or edit your registry connections.
[block:callout]
{
  "type": "warning",
  "body": "As a best practice, we recommend connecting registries using credentials that are provisioned as **read-only**."
}
[/block]

## Amazon ECR

ECR registries are saved using the following URI format: `<aws_account_id>.dkr.ecr.<region>.amazonaws.com`. For example, `1234567890.dkr.ecr.us-east-1.amazonaws.com`. InsightVM requires read-only access to ECR to list repositories, images, tags, and to pull images. Here are the required policy actions for accessing all repositories and images in the registry:

  * ecr:GetAuthorizationToken
  * ecr:BatchCheckLayerAvailability
  * ecr:GetDownloadUrlForLayer
  * ecr:DescribeRepositories
  * ecr:ListImages
  * ecr:DescribeImages
  * ecr:BatchGetImage

For more information on ECR IAM policies, see  [Amazon ECR IAM Policies and Roles](https://docs.aws.amazon.com/AmazonECR/latest/userguide/ECR_IAM_policies.html).

If you use repository policies to control docker push/pull access, InsightVM still requires the following policy actions to be allowed in order to list repositories and images:

  * ecr:GetAuthorizationToken
  * ecr:DescribeRepositories
  * ecr:ListImages
  * ecr:DescribeImages

For more information on ECR repository policies, see [Amazon ECR Repository Policies](https://docs.aws.amazon.com/AmazonECR/latest/userguide/RepositoryPolicies.html).

To add an Amazon ECR registry connection:

1. Enter a name and the account ID.
2. select the region from the drop-down. 
3. In the Global credential area, enter the Access Key and Secret Key.

## Azure Container Registry

1. Navigate to the Azure Active Directory dashboard and go to **App registrations > New application registration**.
2. Enter a name (e.g. InsightVM) for the application and **https://insight.rapid7.com** as the **Sign-on URL**. The **Application type** should be **Web app / API**.
3. Save the new application. Make sure to copy the the **Application ID** for later use.
4. After saving, click on the **Keys** button under "API ACCESS". Give the new key a name, and save to reveal the key value. Save this value for reference.
5. Navigate to your container registry dashboard. Click **Access Control (IAM) > Add**. Select the **Reader** role, then search for the application name you saved previously. Save the permissions change.
6. Create a new Azure Registry from the Exposure Analytics Partner Connections page. Fill in the required fields and save.  The field **Registry Name on Azure** must match the name of the Azure Container Registry resource you wish to connect.

## Docker Hub

To create your registry connection, you'll need to provide a name, and in the "Global Credential" area, you'll need to enter a username and password.

## Privately Hosted Docker Registry
[block:callout]
{
  "type": "info",
  "body": "All registry connections use HTTPS and require a valid, trusted certificate. If you need to whitelist traffic to your private registry see [Configure communications with the Insight platform](https://insightvm.help.rapid7.com/docs/configure-communications-with-the-insight-platform#section-ticketing-and-container-registry-connections)."
}
[/block]
To create your registry connection, you'll need to enter a name, host, and port.
## Google Container Registry

To create your registry:

1. Create a new service account in the project that hosts your container registry. Do not select a role.
2. Verify that **Furnish a new private key** is selected and click CREATE. The private key file downloads to your computer.
3. Navigate to Google Cloud Storage, select the row for the bucket that contains your container registry, and click **SHOW INFO PANEL**.
4. In the "Add members" box, type the name of the service account you created,  select the role **Storage Object Viewer**, and then click **Add**.
5. In InsightVM, enter the Name, GCR Host, and Project ID that hosts your container registry. 
6. In the "Private Key" box, copy and paste the entire contents of the downloaded JSON key document. 
7. Save your changes.

## Quay

You must have a Quay Organization account with access to your container repositories for this configuration to work. User accounts will not work.

1. Navigate to the "Applications" tab in your organization account. 
2. Click **Create New Application** and enter a name for the application. 
3. For Homepage URL, enter https://insight.rapid7.com as both the Homepage URL and the Redirect/Callback URL Prefix. 
4. Save your changes.
5. Go to the "Generate Token" tab for your newly created application. Select **View all visible repositories**, click **Generate Access Token**, and save the generated token for reference.
6. In InsightVM, enter a name for the registry. Then, enter the name of the Quay Organization under which you granted the access token. 
7. In the "Key" field, enter the generated token. 
8. Save your changes.