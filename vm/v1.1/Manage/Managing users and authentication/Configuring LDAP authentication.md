---
title: "Configuring LDAP authentication"
excerpt: ""
---
Complete the following steps to configure an LDAP integration as an external authentication source.

# Define an external authentication source

1. Click the **Administration** tab.
2. In the “Global and Console Settings” window, click **Administer**.
3. On the “Security Console Configuration” screen, click the **Authentication** tab.
4. Under “LDAP/AD Authentication Source Listing”, click the **Add LDAP/AD Source** button.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/9a6295c-administration_authentication_LDAP.png",
        "administration_authentication_LDAP.png",
        499,
        791,
        "#e7ebed"
      ]
    }
  ]
}
[/block]
5. Click the **Enable authentication source** checkbox.
6. Enter a name for the source.
7. In the “Server name” field, enter the exact DNS hostname of your AD server.
[block:callout]
{
  "type": "info",
  "title": "TIP",
  "body": "If you are unsure of the DNS hostname that you should use, you can locate it by running `nslookup` in the command line.\n\nAlternatively, free tools such as Softerra LDAP Browser can verify the DNS hostname for you."
}
[/block]
8. Enter a server port number.
[block:callout]
{
  "type": "warning",
  "title": "NOTE",
  "body": "Default LDAP port numbers are as follows:\n\n* 389\n* 636\n\nDefault Microsoft AD with Global Catalog port numbers are as follows:\n\n* 3268\n* 3269 (SSL)"
}
[/block]
9. If desired, specify LDAP authentication credentials.
[block:callout]
{
  "type": "info",
  "title": "TIP",
  "body": "Use the provided **Username** and **Password** fields to specify LDAP credentials in cases where your LDAP/AD server does not allow for an anonymous bind."
}
[/block]
10. If desired, check the **Require secure communications (SSL)** checkbox.
11. If desired, specify permitted authentication methods.  Multiple entries can be delimited with commas, semicolons, or spaces.
[block:callout]
{
  "type": "warning",
  "title": "NOTE",
  "body": "Simple Authentication and Security Layer (SASL) authentication methods for permitting LDAP user authentication are defined by the Internet Engineering Task Force in document RFC 2222 http://www.ietf.org/rfc/rfc2222.txt. The application supports the following methods:\n\n* GSSAPI\n* CRAM-MD5\n* DIGEST-MD5\n* SIMPLE\n* PLAIN\n\nWe do not recommend using PLAIN for non-SSL LDAP connections."
}
[/block]
12. If desired, check the **Follow LDAP referrals** checkbox.
[block:callout]
{
  "type": "info",
  "title": "LDAP referrals explained",
  "body": "As the application attempts to authenticate a user, it queries the target LDAP server. The LDAP and AD directories on this server may contain information about other directory servers capable of handling requests for contexts that are not defined in the target directory. If so, the target server will return a referral message to the application, which can then contact these additional LDAP servers. For information on LDAP referrals, see the following document LDAPv3 RFC 2251:\n\n* http://www.ietf.org/rfc/rfc2251.txt"
}
[/block]
13. If desired, specify a search base.
[block:callout]
{
  "type": "info",
  "title": "LDAP search bases explained",
  "body": "You can initiate LDAP searches at different levels within the directory.  A search base is a specific part of the tree where the application will start the search.  Example:\n\nCN=sales,DC=acme,DC=com"
}
[/block]
14. Manually set attribute mappings, or click any of the available buttons to autofill the fields based on presets.
15. Click **Save**.

The Authentication tab will now list your new LDAP authentication source.
16. Finally, click **Save** on the “Security Console Configuration” screen to finalize your authentication sources.

# Create user accounts

With your external authentication source defined, you can now create accounts for your users.

1. Click the **Administration** tab.
2. In the “Users” window, click **Create**.
3. On the “User Configuration” screen’s **General** tab, select your new authentication method from the dropdown list.
4. Complete all fields as required.
[block:callout]
{
  "type": "warning",
  "title": "NOTE",
  "body": "Password fields are disabled when external authentication sources are selected.  The Security console does not control, or allow for, password changes for users authenticated by external sources."
}
[/block]
5. Click **Save** when finished.