---
title: "Discovering Microsoft Azure instances"
excerpt: ""
---
The Microsoft Azure discovery connection provides visibility on your virtual assets as they are created, used, and destroyed within the Azure infrastructure.  Properly configured Azure discovery connections perform the following tasks:

* Discover new assets that are created in Azure.
* Remove destroyed assets from your Security Console.
* Synchronize Azure tags with your Security Console asset tags.

# Preparing your environment

Before a connection can be created, Azure must be configured to communicate with the Security Console.  Complete the steps detailed on the [Azure Documentation pages](https://docs.microsoft.com/en-us/azure/azure-resource-manager/resource-group-create-service-principal-portal).  After completing these steps, you should have the following pieces of information:

* Tenant ID
* Application ID
* Application Secret Key
[block:callout]
{
  "type": "info",
  "title": "TIP",
  "body": "Record the values for each of these fields.  You will be required to provide them during the Azure discovery connection creation setup."
}
[/block]
## Assigning “Reader” rights for the Security Console

The Security Console must have permission to access your Azure-based assets.  In Azure, this permission should be configured at the “Subscriptions” scope.

1. In your Azure portal, search for “subscriptions” in the search bar.
2. Click your subscription to open it.
3. Click **Access Control (IAM)**.  Existing users/roles will be shown.
4. Click **Add**.
5. In the “Add permissions” window, complete the fields as follows:
  * Set "Role" to **Reader**.
  * Set "Assign access to" to **Azure AD user, group, or application**.
  * Set "Select" to the Application ID that you created earlier.
[block:callout]
{
  "type": "warning",
  "title": "NOTE",
  "body": "The Application ID must be searched in order for it to appear on this screen."
}
[/block]
6. Click **Save**.

# Creating a connection

When the previous steps have been completed, you’ll be ready to create a connection.  See our connection creation guide at [Creating and managing Dynamic Discovery connections](doc:creating-and-managing-dynamic-discovery-connections) and browse to [Adding a Microsoft Azure Connection](doc:creating-and-managing-dynamic-discovery-connections#section-adding-a-microsoft-azure-connection).