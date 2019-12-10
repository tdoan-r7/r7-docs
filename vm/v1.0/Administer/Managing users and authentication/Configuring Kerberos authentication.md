---
title: "Configuring Kerberos authentication"
excerpt: ""
---
Complete the following steps to configure a Kerberos integration as an external authentication source.

# Define an external authentication source

1. Click the **Administration** tab.
2. In the “Global and Console Settings” window, click **Administer**.
3. On the “Security Console Configuration” screen, click the **Authentication** tab.
4. Under “Kerberos Authentication Source Listing”, click the Add Kerberos Source button.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/10fd3e6-administration_authentication_kerberos.png",
        "administration_authentication_kerberos.png",
        599,
        298,
        "#d3d7da"
      ]
    }
  ]
}
[/block]
5. Click the **Enable authentication source** checkbox.
6. Click the **Default realm** checkbox.
7. Enter the name of the Kerberos realm.
8. Enter the name of the key distribution center.
9. Click **Save**.

The **Authentication** tab will now list your new Kerberos authentication source.
10. Finally, click **Save** on the “Security Console Configuration” screen to finalize your authentication sources.

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

# Manually setting Kerberos encryption types

You can secure connections to the Kerberos source by specifying ticket encryption types for the connection to use.

1. Using a text editor, create a text file named `kerberos.properties`.
2. Add the following line to the file:

```
default_tkt_enctypes=
```
3. Append this line with one or more encryption types as desired.  Separate multiple types with a space.  Example:

```
default_tkt_enctypes= aes128-cts-hmac-sha1-96 aes256-cts-hmac-sha1-96
```
Choose from any of the following encryption types:

* des-cbc-md5
* des-cbc-crc
* des3-cbc-sha1
* rc4-hmac
* arcfour-hmac
* arcfour-hmac-md5
* aes128-cts-hmac-sha1-96
* aes256-cts-hmac-sha1-96


4. When finished, save the file in the `<install_dir>/nsc/conf` directory.  The changes will be applied when the Security Console restarts.