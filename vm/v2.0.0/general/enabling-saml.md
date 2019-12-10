---
title: "enabling-saml"
excerpt: ""
---
# Enabling SAML for AppSpider Enterprise

Security Assertion Markup Language (SAML) is an XML-based standard for single sign-on (SSO) authentication that enables you to access applications you have rights to use. AppSpider Enterprise offers integration with SAML 2.0, which allows you to use an identity provider (IdP) to handle the sign-in process and provide the credentials your users need to authenticate to AppSpider Enterprise.

To enable SAML for AppSpider Enterprise, there are two things you'll need to do:

- Create a SAML certificate with your IdP and install the certificate on the server running AppSpider Enterprise.

- Modify the `samlProviders.config` file to include the information for your IdP and to enable SAML for AppSpider Enterprise.

## Creating a SAML certificate with your IdP

SAML certificates enable you to increase security between your IdP and your SAML applications. To learn how to create SAML certificates, please visit your IdP's documentation. You'll need to create one for AppSpider Enterprise.

After you create the SAML certificate, you'll need to download the certificate, and store it on your AppSpider Enterprise server. You'll need details from the SAML certificate, such as the location of where the certificate is installed, to configure SAML for AppSpider Enterprise.

## Modifying the SAML configuration file

1. Open `C:\Program Files(x86)\Rapid7\AppSpider Enterprise x.x\IIS.NET\samlProviders.config` with a text editor. Replace "x.x" in the file path with the version of AppSpider Enterprise you are running.

You may need to have administrator privileges to edit the file.

1. Find the element `<samlProviders enabled="false">` and change its value to `true` to provision users to use SAML. 
 
2. Find the line that starts with `<provider>`. You _must_ provide the information for the following options:

- **signOnUrl** - The URL of the IdP handling your sign-in requests, such as http://IDP\_servername/saml2/sso/1234. 
 
- **issuer** - The unique entity identifier for your IdP, such as http://saml.yourcompany.com. 
 
- **title** - The company name you'll use to log in to AppSpider Enterprise. This is the information you will enter when you log in to AppSpider Enterprise via SAML. 
 

1. Find the line that starts with `<certificate>`. You _must_ provide the information for the following options:

- **findValue** - The subject of the certificate.

- **storeLocation** - The location of the certificate on your local machine.

- **storeName** - The certificate's storage name. By default, this value is "My," which means that the certificate is located in Local Machine \> Personal storage. 
 

1. Find the line that starts with `<provideConfiguration>`. You _must_ provide the information for the following options:

- **autoAttachToClient** - The enterprise client that you want to assign to SAML users. A client is a collection of users who interact with AppSpider Enterprise and sets bounds on the people can use the application. 
 
- **autoAttachSysAdmins** - The IdP username you want to assign as a system administrator. You can only specify one user name for this option. 
 
-  **autoAttachGroups** - The name of the enterprise group that can log in to AppSpider Enterprise to manage access to the application. 
 

1. If you want to send login data to your IdP, you can add the following line to the configuration file: `<samlRequestParams ID="" AssertionConsumerServiceURL="" Issuer="" />`, where:

- **ID** - An identifier for AppSpider Enterprise.

- **AssertionConsumerServiceURL** - The SAML login for AppSpider Enterprise, such as `https://<servername>/AppSpiderEnterprise/Account/LoginSaml`.

- **Issuer** - The server name.

1. Save the file.

## Using SAML to log in to AppSpider Enterprise

After you have enabled and configured SAML for AppSpider Enterprise, you can navigate to the AppSpider Enterprise login page and use the SAML button to log in to the application.

![](https://help.rapid7.com/appspider/content/resources/images/saml/saml-login.jpg)

You'll be prompted for your company name, which is the title you defined in the SAML configuration file.

![](https://help.rapid7.com/appspider/content/resources/images/saml/company-name.jpg)

If SAML is set up properly, you'll be logged in to AppSpider Enterprise.