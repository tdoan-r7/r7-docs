---
title: "Configuring scan authentication on target Web applications"
excerpt: ""
---
Scanning Web applications at a granular level of detail is especially important, since publicly accessible Internet hosts are attractive targets for attack. By giving the scan inside access with authentication, you can inspect Web assets for critical vulnerabilities such as SQL injection and cross-site scripting.

Two authentication methods are available for Web applications:

* _Web site form authentication_: Many Web authentication applications challenge users to log on with forms. With this method, the Security Console retrieves a logon form from the Web application. You specify credentials in that form that the Web application will accept. Then, a Scan Engine submits those credentials to a Web site before scanning it. See [Creating a logon for Web site form authentication](doc:creating-a-logon-for-web-site-form-authentication). 
In some cases, it may not be possible to use a form. For example, a form may use a CAPTCHA test or a similar challenge that is designed to prevent logons by computer programs. Or, a form may use JavaScript, which is not supported for security reasons. If these circumstances apply to your Web application, you may be able to authenticate the application with the following method.

* _Web site session authentication_: The Scan Engine sends the target Web server an authentication request that includes an HTTP header—usually the session cookie header—from the logon page. See [Creating a logon for Web site session authentication with HTTP headers](doc:creating-a-logon-for-web-site-session-authentication-with-http-headers). 

The authentication method you use depends on the Web server and authentication application you are using. It may involve some trial and error to determine which method works better. It is advisable to consult the developer of the Web site before using this feature.
[block:callout]
{
  "type": "info",
  "body": "For HTTP servers that challenge users with Basic authentication or Integrated Windows authentication (NTLM), configure a set of scan credentials using the service called _Web Site HTTP Authentication_. To use this service, select **Add Credentials** and then **Account** in the _Authentication_ tab of the site configuration. See [Configuring site-specific scan credentials](doc:configuring-site-specific-scan-credentials)."
}
[/block]