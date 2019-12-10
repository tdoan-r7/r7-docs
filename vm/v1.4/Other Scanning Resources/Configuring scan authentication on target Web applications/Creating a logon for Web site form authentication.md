---
title: "Creating a logon for Web site form authentication"
excerpt: ""
---
Start the configuration for the HTML form authetication:

If you create a logon while configuring a new site, click the **Create site** button on the _Home_ page.
OR
Click the **Create** tab at the top of the page and then select _Site_ from the drop-down list.

If you want to create a logon for an existing site, click that site's **Edit** icon ![Alt](https://files.readme.io/2acc5b1-i_nx_edit_icon.jpg) in the _Sites_ table on the _Home_ page.

1. Click the **Authentication** tab in the Site Configuration.
2. Click **Add Web Authentication**.
3. In the _Add Web Application Authentication_ form, select **Add HTML form** from the **Type** drop-down list.
4. Enter a name for the new HTML form logon settings.

**Tip:** If you do not know any of the required information for configuring a Web form logon, consult the developer of the target Web site.

5. In the **Base URL** text box, enter the main address from which all paths in the target Web site begin.
The credentials you enter for logging on to the site will apply to any page on the site, starting with the base URL. Include the protocol with the address. Example: http://<i></i>example.com or https://<i></i>example.com
6. In the **Logon Page URL** text box, enter the page that contains the form for logging onto the Web site. It should also include the protocol. 
Examples: http://<i></i>example.com/logon.html
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/61720e9-s_nx_web_app_URLs.jpg",
        "s_nx_web_app_URLs.jpg",
        2234,
        919,
        "#1f2a39"
      ],
      "caption": "Entering Web application URLs"
    }
  ]
}
[/block]
7. Click **Next**.
The Security Console contacts the Web server to retrieve any available forms. If it fails to make contact or retrieve any forms, it displays a failure notification. If it retrieves forms, it displays additional configuration steps.

Customize the logon form (if necessary):

1. From the **Form** drop-down list, select the form for logging onto the Web application. Based on your selection, a table of fields appears for that particular form.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/54b48bc-s_nx_selecting_form.jpg",
        "s_nx_selecting_form.jpg",
        2051,
        1396,
        "#1f2a39"
      ],
      "caption": "Editing the form"
    }
  ]
}
[/block]
2. Change the value for any field if necessary.
[block:callout]
{
  "type": "info",
  "body": "If the original value was provided by the Web server, you must first clear the check box before entering a new value. _Only_ change the value to match what the server will accept at logon. If you are not certain of what value to use, contact your Web administrator."
}
[/block]
3. Click **Save**.
The Security Console displays the field table with any changed values according to your edits. Repeat the editing steps for any other values that you want to change.

When all the fields are configured according to your preferences, continue with creating a regular expression for logon failure and testing the logon:

1. Change the regular expression (regex) if you want to use one that is different from the default value.
The default value works in most logon cases. If you are unsure of what regular expression to use, consult the Web administrator. For more information, see [Using regular expressions](doc:using-regular-expressions).
2. Click **Test logon** to make sure that the Scan Engine can successfully log on to the Web application.
If the Security Console displays a success notification, click **Save**.
If logon failure occurs, change any settings as necessary and try again.
[block:callout]
{
  "type": "info",
  "body": "To find an appropriate regex, try logging onto the target Web site with incorrect credentials. If the site displays a message such as _Logon failed_ or _Invalid credentials_, you can use that string for the regex."
}
[/block]