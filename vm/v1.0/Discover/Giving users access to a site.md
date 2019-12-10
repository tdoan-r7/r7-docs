---
title: "Giving users access to a site"
excerpt: ""
---
When editing a site, you can control which users have access to it. Allowing users to configure and run scans on only those assets for which they are responsible is a security best practice, and it ensures that different teams in your organization are able to manage targeted segments of your network.

For example, your organization has an administrative office in Chicago, a sales office in Hong Kong, and a research center in Berlin. Each of these locations has its own site with a dedicated IT or security team in charge of administering its assets. By giving one team access to the Berlin site and not to the other two sites, you allow that team to monitor and patch the research center assets without being able to see sensitive information in the administrative or sales offices.

When Global Administrator creates a user account, he or she can grant the user access to all sites, or restrict access by adding the user to access lists for specific sites. See [Configure general user account attributes](doc:managing-users-and-authentication#section-configure-general-user-account attributes).

After users are added to a site's access list, you can control whether they actually can view the site as you are editing that site:

1. On the _Home_ page, click the **Edit** icon for the site that you want to add users to.
2. Click the **Info & Security** tab.
3. Click **Access**.
4. The _Site Access_ table displays every user in the site's access list. Select the check box for every user whom you want to give access to the site. 
   To give access to all displayed users, select the check box in the top row.

**Note:**  Global Administrators and users with access to all sites do not appear in the table. They automatically have access to any site.

5. Configure other site settings as desired.
6. When you have finished configuring the site, click **Save**.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/29f9df5-s_nx_add_user_to_site.jpg",
        "s_nx_add_user_to_site.jpg",
        1197,
        489,
        "#e0e6e6"
      ],
      "caption": "Adding users to a site"
    }
  ]
}
[/block]