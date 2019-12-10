---
title: "Authentication"
excerpt: ""
---
Web applications often have a section for registered users only. This part of the web application can only be assessed by logging into the app. The process for logging in is called "Authentication". <<product>> supports a number of ways to authenticate into your application. These can be configured in the Authentication tab of the Scan Config wizard.

# Simple Form Authentication 
As the name suggests, this technique helps you log into websites that use simple form-based authentication. These websites have a login form that consists of a username field, a password field, and a submit button. You can refer to this wikipedia article to learn more about form-based authentication: https://en.wikipedia.org/wiki/HTTP%2BHTML_form-based_authentication.

If your target app uses simple form authentication, you can configure the authentication settings using the following steps:
1. Open the Authentication > Authentication Type screen.
2. Click the Authentication Type dropdown and select "Simple Form Authentication." A login form will appear.
3. Enter your username and password in the respective fields.

# Macro Authentication
<<product>> may sometimes be unable to reach the login page of your application, or the login form may become available only after a certain specific sequence of actions has been carried out on your website. For example, the login form may appear in a pop-up that gets dynamically generated via Javascript when the "Login" button is pressed from the "Administration" window. You can enable <<product>> to perform this sequence of steps by recording a macro.
 
A macro is a sequence of actions, such as clicking of buttons, or text entry in a web page recorded in a `.rec` file. During the scan, <<product>> can replay the actions in this file to log in to the web application. You will need the [AppSec Chrome Extension](doc:appsec-chrome-extension) in order to record macros to authenticate into your application. If you wish to use macro authentication, you can configure it using the following steps:
1. Open the **Authentication > Authentication Type** screen. Click the **Authentication Type** dropdown and select "Macro Authentication".
2. Click the **Record New Macro** button and enter the login URL for your application. Once you have done so click the **Start Recording** button.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/9c7fb76-Selection_120.png",
        "Selection_120.png",
        934,
        456,
        "#4a565f"
      ]
    }
  ]
}
[/block]
3. A confirmation dialog will appear, notifying that the recording sequence has begun. The macro window will open at the URL you provided. Simply log in normally. Once you have logged in successfully, close the macro window and click the **Stop Recording** button. 
4. A message will appear confirming that the recording was successful. Name your macro and click the **Save Macro** button.
You should now see your recorded macro.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/d1f86f3-Selection_122.png",
        "Selection_122.png",
        512,
        136,
        "#768389"
      ]
    }
  ]
}
[/block]
5. Save and run your config. It will now attempt authentication using your recorded macro. If successful, the following will appear in the scan’s event log:
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/d08d95f-Selection_127.png",
        "Selection_127.png",
        619,
        36,
        "#46525b"
      ]
    }
  ]
}
[/block]
# Traffic
You may run into web applications built with technologies that are not supported by the <<product>> crawler. You can authenticate into such applications by using a web proxy tool such as the Traffic Recorder in the [Rapid7 AppSec Toolkit](https://blog.rapid7.com/2018/06/14/new-insightappsec-releases-compliance-reports-and-the-appsec-toolkit/). Using the proxy tool, you can record the interactions (e.g. HTTP GET and POST requests) between the front end application and the back end server in a Traffic File. <<product>> can replay these interactions to authenticate into your application.

Use the following steps to authenticate with a Traffic file:
 
1. Complete the steps for logging into your application and record the interactions in a traffic file on your computer. Traffic files can be of the following formats:
  * AppSec toolkit Traffic Files (*.trec)
  * Burp Files (*.xml)
  * Paros Files (*.txt)
  * WebScarab Files (conversationlog)
  * HAR (HTTP Archive) Files (*.har)
  * Fiddler Files (*.saz)
2. Open the **Authentication > Authentication Type** screen. Click the **Authentication Type** dropdown and select "Traffic".
3. Click the **Choose File** button. This will open the "Choose File" popup. 
4. Click the **Upload File** button and upload the traffic file from your computer. 
5. Select the newly uploaded file or an existing traffic file from the "All my Files" tab in the popup.
6. Click the **Use 1 Selected File(s)** button.

#Bootstrap

Many modern web applications use security measures, like two-factor authentication and CAPTCHA, that require manual intervention for logging in to the application. For example, your application may require a one time password sent via SMS. Bootstrap authentication will pause the active scan and allow you to interactively log in to the target application. After authentication is complete, you can resume the scan. The scan engine will continue to crawl and attack your application.

In order to enable bootstrap authentication, you’ll need:
  * Chrome browser
  * The latest version of the AppSec Chrome Extension
  * Engine version number 7.2.049 or later, if you are using an on-premises scan engine

##Enabling Bootstrap Authentication for a Scan
To enable bootstrap authentication for your scan, go to **Authentication > Authentication Type**. Click the **Authentication Type** dropdown and select "Bootstrap".

After you have started the scan:
1. Monitor the scans table. When your scan is ready for authentication, the “Status” column will show the message “Awaiting Authentication”.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/04fd0b6-Awaiting_Authentication.png",
        "Awaiting Authentication.png",
        852,
        350,
        "#4e5963"
      ]
    }
  ]
}
[/block]
2. Click on the name of the scan to open the scan window. You will see the “Authenticate Scan” button on the upper right side of the screen.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/5381cc1-Authenticate_Scan_button.png",
        "Authenticate Scan button.png",
        1116,
        124,
        "#484f5e"
      ]
    }
  ]
}
[/block]
3. Click the **Authenticate Scan** button. If you have not installed the AppSec Chrome Extension, you will see a message prompting you to install it.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/5e1dd11-Chrome_plugin_prompt.png",
        "Chrome plugin prompt.png",
        1348,
        1212,
        "#505c66"
      ]
    }
  ]
}
[/block]
If you have installed the extension, you will see the “Bootstrap Authentication” screen. 
4. Enter the URL of the application and click **Start**. 
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/a6d46a4-Bootstrap_authentication.png",
        "Bootstrap authentication.png",
        613,
        369,
        "#4f5b67"
      ]
    }
  ]
}
[/block]
A popup message with the name of the file where the bootstrap authentication web traffic will be recorded on the Insight Platform will appear. Click **OK** to continue. 
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/ffca19d-Recorded_file_name.png",
        "Recorded file name.png",
        417,
        192,
        "#dddfe1"
      ]
    }
  ]
}
[/block]
A Chrome browser window will pop up and open the web page for your URL.
5. Log in to the application. When the login process is successful, close the Chrome window and return to the “Bootstrap Authentication” screen.
[block:callout]
{
  "type": "warning",
  "title": "Note",
  "body": "During this step, you should only perform the steps required for logging in to the application. The InsightAppSec scan engine will replay these steps and match the pattern from the **Advanced > Logged-in Regex** field to the web page open in the browser. After it confirms that the authentication was successful, it will continue the scan."
}
[/block]
6. Click **Stop**. The Bootstrap Authentication screen will close, and you will return to the scan window. 
7. Monitor the “Event Log” to ensure that authentication has been successful.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/3869918-Event_Log.png",
        "Event Log.png",
        727,
        356,
        "#3e4852"
      ]
    }
  ]
}
[/block]
The Chrome extension records the web traffic of your authentication session and converts it into an HTTP Archive (HAR) file. The scan engine replays this traffic in memory to log in to your application. If the login is successful, you will see the message “Session ‘Authentication with Bootstrap File:’ logged in” in the event log. 
You can also see the status “Logged In” under the Crawled Links count on the scan page. 
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/b80bac0-Screen_Shot_2019-01-16_at_3.41.22_PM.png",
        "Screen Shot 2019-01-16 at 3.41.22 PM.png",
        166,
        122,
        "#38414a"
      ]
    }
  ]
}
[/block]
If the login is not successful, you should ensure that the regular expression in the “Logged-in Regex” field from the “[Advanced](doc:authentication#section-advanced)” screen matches the text in the web page that appears after authentication. If the indicator for logged-in state is hidden under a menu item, expand it so that InsightAppSec can examine it and check the logged-in state. 
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/596fd2f-Logout_Link.png",
        "Logout Link.png",
        221,
        204,
        "#38444e"
      ]
    }
  ]
}
[/block]
For example, if you want to use the presence of the “Logout” link as an indicator that user is logged in, you should expand the drop down where the Logout link is hidden as part of the authentication steps.

#Selenium
Selenium is a framework for automated testing of web applications. Users can record actions like entering data in forms and clicking buttons using Selenium and replay them on demand to ensure that the web application behaves as desired. 

<<product>> supports authentication using Selenium files, so you can record the actions needed to log in to your application in a Selenium `.html` file.  During the scan, <<product>> can replay the actions in this file to log in to the web application. The following is a Selenium authentication file for http://webscantest.com.


[block:code]
{
  "codes": [
    {
      "code": "<?xml version=\"1.0\" encoding=\"UTF-8\"?>\n<!DOCTYPE html PUBLIC \"-//W3C//DTD XHTML 1.0 Strict//EN\" \"http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd\">\n<html xmlns=\"http://www.w3.org/1999/xhtml\" xml:lang=\"en\" lang=\"en\">\n<head profile=\"http://selenium-ide.openqa.org/profiles/test-case\">\n<meta http-equiv=\"Content-Type\" content=\"text/html; charset=UTF-8\" />\n<link rel=\"selenium.base\" href=\"http://webscantest.com/\" />\n<title>selenium</title>\n</head>\n<body>\n<table cellpadding=\"1\" cellspacing=\"1\" border=\"1\">\n<thead>\n<tr><td rowspan=\"1\" colspan=\"3\">selenium</td></tr>\n</thead><tbody>\n<tr>\n\t<td>open</td>\n\t<td>/</td>\n\t<td></td>\n</tr>\n<tr>\n\t<td>clickAndWait</td>\n\t<td>link=Login</td>\n\t<td></td>\n</tr>\n<tr>\n\t<td>type</td>\n\t<td>name=login</td>\n\t<td>admin</td>\n</tr>\n<tr>\n\t<td>type</td>\n\t<td>name=passwd</td>\n\t<td>admin</td>\n</tr>\n<tr>\n\t<td>clickAndWait</td>\n\t<td>name=submit_login</td>\n\t<td></td>\n</tr>\n</tbody></table>\n</body>\n</html>",
      "language": "xml"
    }
  ]
}
[/block]
Use the following steps to authenticate with a Selenium file:
1. Complete the steps for logging in to your application and record the interactions in a Selenium file of the `.html` format.
2. Open the **Authentication > Authentication Type** screen. Click the **Authentication Type** dropdown and select "Selenium".
3. Click the **Choose File** button. This will open the "Choose File" popup. 
4. Click the **Upload File** button and upload the Selenium file from your computer. 
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/ca492b9-Selection_140.png",
        "Selection_140.png",
        738,
        438,
        "#4d5a65"
      ]
    }
  ]
}
[/block]
5. Select the newly uploaded file or an existing Selenium file from the "All my Files" tab in the popup.
6. Click the **Use 1 Selected File(s)** button.

# HTTP Authentication 
The HTTP protocol supports authentication using a username and password. You can use this reference article to learn more about HTTP Authentication: https://docs.microsoft.com/en-us/dotnet/framework/wcf/feature-details/understanding-http-authentication

<<product>> supports the Basic, NTLM, and Kerberos protocols for HTTP authentication. If your target app uses HTTP authentication, you can configure the authentication process using the following steps:

1. Open the **Authentication > HTTP Authentication** screen.
2. Click the **Enable HTTP Auth** switch to enable HTTP authentication.
3. Enter your username and password in the respective fields.

# OAuth
OAuth (https://oauth.net/) is an authorization method that is used by applications to grant fine grained access to clients. <<product>> supports OAuth 2.0 which is the industry-standard protocol for authorization. OAuth 2.0 focuses on client developer simplicity while providing specific authorization flows for web applications, desktop applications, mobile phones, and living room devices. If your application has granted <<product>> the access to certain capabilities, you can enter the required details in the **Authentication > OAuth** screen. When starting a scan, <<product>> can provide these details to your application and receive an access token. 

Depending on your use case, you will need to use a different OAuth flow. The “grant type” property determines the OAuth flow that your application is using. You can learn more about grant types here: https://oauth.net/2/grant-types/.  

<<product>> supports the following grant types:
1. [Authorization Code](doc:authentication#section-authorization-code)
2. [Implicit](doc:authentication#section-implicit)
3. [Resource Owner Password Credentials](doc:authentication#section-resource-owner-password-credentials)
4. [Client Credentials](doc:authentication#section-client-credentials)

The following chart can help you choose the appropriate grant type for your application.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/f17f5fa-Grant_Types_chart.png",
        "Grant Types chart.png",
        876,
        406,
        "#dce7f1"
      ]
    }
  ]
}
[/block]
## Set Up OAuth Authentication
If you want to scan an application that uses OAuth, you will need to know the grant type used by your application. You can usually get this information from your application developers. If you examine the traffic from a connection, you can also often see the grant type in the URL.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/62e9576-Screen_Shot_2019-08-14_at_2.51.46_PM.png",
        "Screen Shot 2019-08-14 at 2.51.46 PM.png",
        2328,
        722,
        "#868d94"
      ]
    }
  ]
}
[/block]
The **Authentication > OAuth** screen has a number of options to configure your application's OAuth properties. You will need to click the **Enable OAUTH** switch to enable OAuth authentication, and then provide the required values based on your grant type.

  * **Resource Owner URL** - An entity capable of granting access to a protected resource. Optional, in most cases should be equal to Resource Server URL  
  * **Resource Server URL** - The identifier for your API server. The resource server handles authenticated requests after the application has obtained an access token
  * **Authentication Server URL** - The authentication server URL, obtained from your identity provider (reference: https://en.wikipedia.org/wiki/Identity_provider)
  * **Redirect URI** - The URL that the authorization server will redirect the user back to, with an authorization code or access token in the URL. Resource Server URL will be used if empty
  * **Client Scope** - One or more space-separated strings indicating which permissions the application is requesting. The specific OAuth API you’re using will define the scopes that it supports
  * **Client ID** - The public identifier for the application, obtained from your identity provider
  * **Client Secret** - The application’s client secret, obtained from your identity provider. This ensures that the request to get the access token is made only from the application
  * **Client State** - The application generates a random string and includes it in the request. It should then check that the same value is returned after the user authorizes the app. This is used to prevent CSRF attacks
  * **ExtensionGrant** - Can be ignored at this moment
  * **Username** - The username of the end user in case of using the “Resource Owner Password Credentials” or “Client Credentials” grant types
  * **Password** - The password of the end user in case of using the “Resource Owner Password Credentials” or “Client Credentials” grant types
  * **Username Form** - The username for additional form authentication flow on the application
  * **Password Form** - The password for additional form authentication flow on the application
  * **Never Do Basic Auth** - Prevents <<product>> from sending HTTP Basic authentication header (base65 encoded Username and Password values) in case of using “Resource Owner Password Credentials” or “Client Credentials” 

##OAuth Grant Types
The following sections describe which OAuth properties you need to provide to InsightAppSec based on your grant type. 

###Authorization Code 
The Authorization Code grant type is used by web and mobile apps. It differs from most of the other grant types by first requiring the app launch a browser to begin the flow. At a high level, the flow has the following steps:
  * The application opens a browser to send the user to the OAuth server
  * The user sees the authorization prompt and approves the app’s request
  * The user is redirected back to the application with an authorization code in the query string
  * The application exchanges the authorization code for an access token

The Authorization Code flow is best used by server-side apps where the source code is not publicly exposed. The apps should be server-side because the request that exchanges the authorization code for a token requires a client secret, which will have to be stored in your client. The server-side app requires an end-user, however, because it relies on interaction with the end-user’s web browser which will redirect the user and then receive the authorization code. See https://developer.okta.com/authentication-guide/auth-overview/#authorization-code-flow and https://developer.okta.com/authentication-guide/implementing-authentication/auth-code for more information.

####Mandatory properties
  * Resource Server URL
  * Client ID 

###Implicit
The Implicit grant type is a simplified flow that can be used by public clients, where the access token is returned immediately without an extra authorization code exchange step.

It is generally not recommended to use the implicit flow (and some servers prohibit this flow entirely). In the time since the spec was originally written, the industry best practice has changed to recommend that public clients should use the authorization code flow with the PKCE extension instead.

####Mandatory properties
  * Resource Server URL
  * Client ID 

NOTE: PKCE is not supported yet

###Resource Owner Password Credentials
The resource owner password credentials grant type is suitable in cases where the resource owner has a trust relationship with the client, such as the device operating system or a highly privileged application.  The authorization server should take special care when enabling this grant type and only allow it when other flows are not viable.
See https://tools.ietf.org/html/rfc6749#section-4.3 for more information.

####Mandatory properties
  * Resource Server URL
  * Username 
  * Password

###Client Credentials
The Client Credentials grant is used when applications request an access token to access their own resources, not on behalf of a user.
The client needs to authenticate themselves for this request. Typically the service will allow either additional request parameters Client Id and Client Secret, or accept the Client Id and Client Secret in the HTTP Basic auth header.

####Mandatory properties
  * Resource Server URL

##Additional OAuth Properties
In addition to the properties in the OAuth section of the Authentication screen, there are some Advanced Options that can be helpful to configure the OAuth flow for your application.

  * **JsonPostBodies** - Support JSON format on OAuth Authorization Server requests and responses
  * **OAuthCustomField** - Any additional parameters that should be sent to the Authorization Server
[block:callout]
{
  "type": "info",
  "title": "Note",
  "body": "In most cases, except the Implicit grant type, OAuth authentication can be bypassed using a macro. If you are having trouble configuring OAuth with InsightAppSec, you should try [Macro authentication](doc:authentication#section-macro-authentication)."
}
[/block]
# Advanced
While attempting authenticated scanning of an app, <<product>> needs a way to know that authentication has been successful. It attempts to deduce the logged-in state of the app by examining the headers and body of web pages. The fields in the Authentication > Advanced tab can be used to train <<product>> to recognize the logged-in state of your application. 
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/b20fefb-Selection_125.png",
        "Selection_125.png",
        294,
        670,
        "#727b80"
      ]
    }
  ]
}
[/block]
* **Login Link Regex** -  A regular expression that matches the text on the link that points to the login page. <<product>> will use this regex to find the login link and apply the user-provided credentials. If the user is already logged in, this regex will help <<product>> from accidentally crawling the login again. 
* **Logged-in Regex** - If the text on your page matches this regular expression, <<product>> assumes that you are still logged in. This regex usually matches the sign out link, since the sign-out option is only available if the user is still logged in.
* **Logged-in Header Regex** - If your application always populates a specific HTTP header when a user is logged-in, you can use a matching regex in this field. If the headers match the regex, <<product>> will assume that the user is logged-in.
* **Session Loss Regex** - If the text on a page matches this regex, <<product>> will assume that it has been logged out of the target app, and will try to re-login using the login link.
* **Session Loss Header Regex** - If an HTTP header matches this regex, <<product>> will assume that it has been logged out of the target app, and will try to re-login using the login link. The defalt value looks for the Location header (reference: https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Location) which indicates that the browser is being redirected to a new page. 
* **Logout Link Regex** - This field helps <<product>> to avoid crawling the logout link and accidentally signing itself out of the app. The default value ```(sign|log|time)[ -]?(in|on|out|off)|password``` also tries to avoid the "change password" link so <<product>> does not accidentally change your passwords during its testing.
* **Logout Post Body regex** - If the text on a page matches this regex, it means that <<product>> has been logged out. If there are more tests remaining, <<product>> will attempt to re-login into the app. 
* **Assume Good Login** - You may sometimes be unable to find a regex that matches the logged-in state of the app. There may  be multiple login links leading to different areas of the product, and <<product>> might be attempting the same credentials everywhere leading to account lockouts. You can enable the **Assume Good Login** switch to instruct <<product>> not to check for logged-in state after the initial log in.

You can use the Regex Builder of the [Rapid7 AppSec Toolkit](https://blog.rapid7.com/2018/06/14/new-insightappsec-releases-compliance-reports-and-the-appsec-toolkit/) to test your regular expressions before using them in <<product>>.