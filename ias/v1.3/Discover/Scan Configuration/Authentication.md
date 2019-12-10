---
title: "Authentication"
excerpt: ""
---
Web applications often have a section for registered users only. These parts of the web application can only be assessed by logging in to the app. <<product>> supports a number of ways to authenticate into your application. These can be configured in the Authentication tab of the Scan Config wizard. 

### Simple Form Authentication 
As the name suggests, this technique helps you sign in to websites using simple form-based authentication. The login form should consist of a username field, a password field, and a submit button. You can refer to this wikipedia article to learn more about form based authentication: https://en.wikipedia.org/wiki/HTTP%2BHTML_form-based_authentication.

If your target app uses simple form authentication, you can configure the authentication process using the following steps:
1. Open the Authentication > Authentication Type screen.
2. Click the **Authentication Type** dropdown and select "Simple Form Authentication". A login form will appear.
3. Enter your Username and Password in the respective fields.

### Macro Authentication
Rapid7 AppSec Macros are sequences of actions such as clicking of buttons or text entry in a web page. Once you have the [AppSec Chrome Extension](doc:appsec-chrome-extension)  installed, you can use macros to record the actions needed to authenticate into your application.

1. Open the Authentication > Authentication Type screen. Click the **Authentication Type** dropdown and select "Macro Authentication".
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
3. A confirmation dialog will appear, notifying that the recording sequence has begun. The macro window will open at the URL you provided. Simply log in normally. Once you have logged in successfully, close the macro window and click the ‘Stop Recording’ button. 
4. A message will appear confirming that the recording was successful. Name your macro and click the ‘Save Macro’ button.
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
5. Save and run your config. It will now attempt authentication using your recorded macro. If successful the following will appear in the scan’s event log.
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
###Traffic
You may run into Web applications built with technologies that are not supported by the <<product>> crawler. You can authenticate into such applications by using a Web Proxy tool such as the Traffic Recorder in the Rapid7 AppSec toolkit. Using the proxy tool, you can record the interactions (e.g. HTTP GET and POST requests) between the front end application and the back end server in a Traffic File. <<product>> can use these interactions to authenticate into your application.

Use the following steps to authenticate with a Traffic file:
 
1. Complete the steps for logging into your application, and record the interactions in a traffic file on your computer. Traffic files can be of the following formats:
  * AppSec toolkit Traffic Files (*.trec)
  * Burp Files (*.xml)
  * Paros Files (*.txt)
  * WebScarab Files (conversationlog)
  * HAR (HTTP Archive) Files (*.har)
  * Fiddler Files (*.saz)
2. Open the Authentication > Authentication Type screen. Click the **Authentication Type** dropdown and select "Traffic".
3. Click the **Choose File** button. This will open the "Choose File" popup. 
4. Click the **Upload File** button and upload the traffic file from your computer. 
5. Select the newly uploaded file or an existing traffic file from the "All my Files" tab in the popup.
6. Click the **Use 1 Selected File(s)** button.

###HTTP Authentication 
The HTTP protocol supports authentication using a username and password. You can use this reference article to learn more about HTTP Authentication: https://docs.microsoft.com/en-us/dotnet/framework/wcf/feature-details/understanding-http-authentication

<<product>> supports the Basic, NTLM, and Kerberos protocols for HTTP authentication. If your target app uses HTTP authentication, you can configure the authentication process using the following steps:
1. Open the Authentication > HTTP Authentication screen.
2. Click the **Enable HTTP Auth** switch to enable HTTP authentication.
3. Enter your Username and Password in the respective fields.

##Advanced
While attempting authenticated scanning of an app, <<product>> needs a way to learn that authentication has been successful. It attempts to deduce the logged-in state of the app by examining the headers and body of web pages. The fields in the Authentication > Advanced tab can be used to train <<product>> to recognize the logged-in state of your application. You can use the Regex Builder of the Rapid7 AppSec Toolkit to test your regular expressions before using them in <<product>>.
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
* **Logged-in Regex** - If the text on your page matches this regular expression, <<product>> assumes that you are still logged in. This regex usually matches the "Sign out" link, since the sign-out option is only available if the user is still logged in.
* **Logged-in Header Regex** - If your application always populates a specific HTTP header when a user is logged-in, you can use a matching regex in this field. If the headers match the regex, <<product>> will assume that the user is logged-in.
* **Session Loss Regex** - If the text on a page matches this regex, <<product>> will assume that it has been logged out of the target app, and will try to re-login using the login link.
* **Session Loss Header Regex** - If an HTTP header matches this regex, <<product>> will assume that it has been logged out of the target app, and will try to re-login using the login link. The defalt value looks for the Location header (reference: https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Location) which indicates that the browser is being redirected to a new page. 
* **Logout Link Regex** - This field helps <<product>> to avoid crawling the Logout link and accidentally signing itself out of the app. The default value ```(sign|log|time)[ -]?(in|on|out|off)|password``` also tries to avoid the "change password" link so <<product>> does not accidentally change your passwords during its testing.
* **Logout Post Body regex** - If the text on a page matches this regex, it means that <<product>> has been logged out. If there are more tests remaining, <<product>> will attempt to re-login into the app. 
* **Assume Good Login** - You may sometimes be unable to find a regex that matches the logged-in state of the app. There may  be multiple login links leading to different areas of the product, and <<product>> might be attempting the same credentials everywhere leading to account lockouts. You can enable the **Assume Good Login** switch to instruct <<product>> not to check for logged-in state after the initial log in.