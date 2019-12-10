---
title: "Creating a logon for Web site session authentication with HTTP headers"
excerpt: ""
---
When using HTTP headers to authenticate the Scan Engine, make sure that the session ID header is valid between the time you save this ID for the site and when you start the scan. For more information about the session ID header, consult your Web administrator.

Not every Web site supports the storage of cookies, so it is helpful to verify that header authentication is possible on your target Web site before you use this method. Verification involves exporting the cookie values from the target Web site. Various tools are available for this task. For example, if you use Firefox as your browser, you can install the Cookie Exporter, Cookie Importer, and Firebug addons. The following steps incorporate Firefox as the browser for illustration:

1. After installing Cookie Exporter, Cookie Importer, and Firebug, restart Firefox and enable cookies.
2. Log onto the target Web site.
3. From the Firefox _Tools_ menu, select **Export Cookies**... and save the exported cookies to a .txt file.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/bb1c759-s_firefox_export_cookies.jpg",
        "s_firefox_export_cookies.jpg",
        390,
        210,
        "#d6d3ce"
      ],
      "caption": "Exporting cookies from Firefox"
    }
  ]
}
[/block]
4. Open the .txt file and delete all but the session cookies, since you’ll need those for authentication. One header defines the credentials, and the other defines the session. Save the updated file.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/2bcc125-s_imported_cookies.jpg",
        "s_imported_cookies.jpg",
        931,
        198,
        "#eaeae6"
      ],
      "caption": "The exported cookies file with all but the session cookies removed."
    }
  ]
}
[/block]
5. Restart the browser and clear your browser history.
6. From the Firefox _Tools_ menu, select **Import Cookies...** Firefox displays a message indicating that two cookies were imported.
7. Navigate to the target Web site. If header authentication is possible, you will bypass the logon page, and you will immediately be authenticated.

After verifying that header authentication is possible, start the HTTP headers configuration:

If you want to configure HTTP headers while configuring a new site, click the **Create site** button on the _Home_ page.
OR
Click the **Create** tab at the top of the page and then select _Site_ from the drop-down list.

If you want to configure HTTP headers for an existing site, click that site's **Edit** icon in the _Sites_ table on the _Home_ page.

1. Click the **Authentication** tab in the site configuration .
2. Click **Add Web Authentication**.
3. In the _Add Web Application Authentication_ form, select **HTTP Headers** from the **Type** drop-down list.
4. Enter a name for the new header settings.
5. In the **Base URL** text box, enter the main address from which all paths in the target Web site begin.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/4d3b85f-s_nx_web_app_URLs.jpg",
        "s_nx_web_app_URLs.jpg",
        2234,
        919,
        "#1f2a39"
      ],
      "caption": "Web App URLs"
    }
  ]
}
[/block]
Continue with adding a header:

**Tip:** If you do not know any of the required information for configuring a Web form logon, consult the developer of the target Web site.

1. In the _HTTP Header Values_ table, click the **Add Header** hyperlink.
2. In the pop-up dialog box, enter a name/value pair for the header and click the **Add Header** button.
* _Name_ corresponds to a specific data type, such as the Web host name, Web server type, session identifier, or supported languages. The name can only include letters and numerals. It cannot include spaces or special characters.
* _Value_ corresponds to the actual value string that the console sends to the server for that data type. For example, the value for a session ID (SID) might be a uniform resource identifier (URI).

For example, a name/value pair may specify a name/value pair for a session ID. The name might be _Session-id_, and the value might be _URI_.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/e59126b-s_nx_name_value_pair.jpg",
        "s_nx_name_value_pair.jpg",
        2052,
        1344,
        "#1f2939"
      ],
      "caption": "Name/value pair"
    }
  ]
}
[/block]
If you are not sure what header to use, consult your Web administrator.

After you enter the name/value pair, it appears in the _HTTP Header Values_ table.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/ea0a199-s_nx_HTTP_header_values_table.jpg",
        "s_nx_HTTP_header_values_table.jpg",
        2071,
        776,
        "#202b3b"
      ],
      "caption": "HTTP Header Values table"
    }
  ]
}
[/block]
Continue with creating a regular expression for logon failure and testing the logon:

1. Change the regular expression (regex) if you want to use one that is different from the default value.
The default value works in most logon cases. If you are unsure of what regular expression to use, consult the Web administrator. For more information, see [Using regular expressions](doc:using-regular-expressions).
2. Click **Test logon** to make sure that the Scan Engine can successfully log on to the Web application.
If the Security Console displays a success notification, click **Save**.
If logon failure occurs, change any settings as necessary and try again.