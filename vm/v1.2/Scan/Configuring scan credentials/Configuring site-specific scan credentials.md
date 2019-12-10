---
title: "Configuring site-specific scan credentials"
excerpt: ""
---
In this topic, you will learn how set up and test credentials for a site, how to restrict them to a specific asset or port, and how to edit and enable the use of previously created credentials.

When configuring scan credentials in a site, you have two options:

* Create a new set of credentials. Credentials created within a site are called _site-specific_ credentials and cannot be used in other sites.
* Enable a set of previously created credentials to be used in the site. This is an option if site-specific credentials have been previously created in your site or if shared credentials have been previously created and then assigned to your site.
[block:callout]
{
  "type": "info",
  "body": "To learn about credential types, review [Managing shared scan credentials](doc:managing-shared-scan-credentials)."
}
[/block]
## Starting configuration for a new set of site-specific credentials

The first action in creating new site-specific scan credentials is naming and describing them. Think of a name and description that will help you recognize at a glance which assets the credentials will be used for. This will be helpful, especially if you have to manage many sets of credentials.

If you want to add credentials while configuring a new site, click the **Create site** button on the _Home_ page.
OR
Click the **Create** tab at the top of the page and then select _Site_ from the drop-down list.

If you want to add credentials for an existing site, click that site's **Edit** icon in the _Sites_ table on the _Home_ page.
[block:callout]
{
  "type": "info",
  "body": "If you created the site through the integration with VMware NSX, you cannot edit scan credentials, which are unnecessary because the integration provides InsightVM with the depth of access to target assets that credentials would otherwise provide. See [Integrating NSX network virtualizations with scans](doc:integrating-nsx-network-virtualizations-with-scans)."
}
[/block]
1. Click the **Authentication** tab in the site configuration .
2. Click **Add Credentials**.
3. In the _Add Credentials_ form, enter a name and description for the new set of credentials.
4. Continue with configuring the account, as described in the next section.

## Configuring the account for authentication

If you do not know what authentication service to select or what credentials to use for that service, consult your network administrator.

**Note:** All credentials are protected with RSA encryption and triple DES encryption before they are stored in the database.

1. Click **Account** under the **Add Credentials** tab.
2. Select an authentication service or method from the drop-down list.
3. Enter all requested information in the appropriate text fields.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/e392fcb-s_nx_auth_account.jpg",
        "s_nx_auth_account.jpg",
        1972,
        964,
        "#1f2a39"
      ],
      "caption": "Configuring an account for site credentials"
    }
  ]
}
[/block]
4. If you want to test the credentials or restrict them see the following two sections. Otherwise, click **Create**.

The newly created credentials appear in the _Scan Credentials_ table, which you can view by clicking **Manage Authentication**.

## Testing the credentials

You can verify that a target asset in your site will authenticate the Scan Engine with the credentials you’ve entered. It is a quick method to ensure that the credentials are correct before you run the scan.
1. In the _Add Credentials_ form, expand the _Test Credentials_ section by clicking the arrow.
2. Expand the **Test Credentials** section.
3. Enter the name or IP address of the authenticating asset.

**Note:** If you do not enter a port number, the Security Console will use the default port for the service. For example, the default port for CIFS is 445.

1. To test authentication on a single port, enter a port number.
2. Click **Test credentials**.

**Note:** If you are testing _Secure Shell (SSH)_ or _Secure Shell (SSH) Public Key_ credentials and you have assigned elevated permissions, both credentials will be tested. Credentials for authentication on the target are tested first, and a message appears if the credentials failed. Permission elevation failures are reported in a separate message. See [Using SSH public key authentication](doc:using-ssh-public-key-authentication).

3. Note the result of the test. If it was not successful, review and change your entries as necessary, and test them again. The Security Console and scan logs contain information about authentication failure when testing or scanning with these credentials. See [Working with log files](doc:troubleshooting#section-working-with-log-files).
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/4bde6e4-s_nx_credential_test_success.jpg",
        "s_nx_credential_test_success.jpg",
        1960,
        1103,
        "#1f2a3a"
      ],
      "caption": "A successful test of site credentials"
    }
  ]
}
[/block]
4. If you want to restrict the credentials to a specific asset or port, see the following section. Otherwise, click **Create**.

## Limiting the credentials to a single asset and port

If a particular set of credentials is only intended for a specific asset and/or port, you can restrict the use of the credentials accordingly. Doing so can prevent scans from running unnecessarily longer due to authentication attempts on assets that don’t recognize the credentials.

If you restrict credentials to a specific asset and/or port, they will not be used on other assets or ports.

Specifying a port allows you to limit your range of scanned ports in certain situations. For example, you may want to scan Web applications using HTTP credentials. To avoid scanning all Web services within a site, you can specify only those assets with a specific port.

1. Click the **Account** under the **Add Credentials** tab.
2. Enter only the host name or IP address of the asset that you want to restrict the credentials to.
OR
Enter host name or IP address of the asset and the number of the port that you want to restrict the credentials to.
[block:callout]
{
  "type": "info",
  "body": "If you do not enter a port number, the Security Console will use the default port for the service. For example, the default port for CIFS is 445."
}
[/block]
3. When you have finished configuring the set of credentials, click **Create**.
[block:callout]
{
  "type": "info",
  "body": "To verify successful scan authentication on a specific asset, search the scan log for that asset. If the message “*A set of [service_type] administrative credentials have been verified.*” appears with the asset, authentication was successful."
}
[/block]
## Enabling a previously created set of credentials for use in a site

If a set of credentials is not enabled for a site, the scan will not attempt authentication on target assets with those credentials. Make sure to enable credentials if you want to use them.

1. To enable credentials for an existing site, click that site's **Edit** icon in the _Sites_ table on the _Home_ page.
2. Click the **Authentication** link in the Site configuration .
The _Scan Credentials_ table lists any site-specific credentials that were created for the site or any shared credentials that were assigned to the site. For more information, see [Shared Credentials vs. Site Specific Credentials](doc:configuring-scan-credentials#section-shared-credentials-vs-site-specific-credentials).
3. Select the **Enable** check box for any set of credentials that you want to scan with.
Click the **Save** button for the site configuration.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/dcc7049-s_nx_enable_credentials.jpg",
        "s_nx_enable_credentials.jpg",
        2227,
        791,
        "#202b3a"
      ],
      "caption": "Enabling a set of credentials for a site"
    }
  ]
}
[/block]
## Editing a previously created set of site credentials
[block:callout]
{
  "type": "warning",
  "body": "You cannot edit shared scan credentials in the _Site Configuration_ panel. To edit shared credentials, go to the _Administration_ page and select the **manage** link for Shared scan credentials. See [Editing shared credentials that were previously created](doc:managing-shared-scan-credentials#section-editing-shared-credentials-that-were-previously-created). You must be a Global Administrator or have the Manage Site permission to edit shared scan credentials."
}
[/block]
The ability to edit credentials can be very useful, especially if passwords change frequently. You can only edit site-specific credentials in a _Site Configuration_ panel.

1. To enable credentials for an existing site, click that site's **Edit** icon in the _Sites_ table on the _Home_ page.
2. Click the **Authentication** tab in the Site configuration .
3. Click the hyperlink name of any set of credentials that you want to edit.
4. Change the configuration as desired. See the following topics for more information:
> * [Starting configuration for a new set of site-specific credentials](doc:configuring-site-specific-scan-credentials#section-starting-configuration-for-a-new-set-of-site-specific-credentials) 
> * [Configuring the account for authentication](doc:configuring-site-specific-scan-credentials#section-configuring-the-account-for-authentication) 
> * [Testing the credentials](doc:configuring-site-specific-scan-credentials#section-testing-the-credentials) 
> * [Limiting the credentials to a single asset and port](doc:configuring-site-specific-scan-credentials#section-limiting-the-credentials-to-a-single-asset-and-port) 
5. When you have finished editing the credentials, click **Save**.

## Verifying scan credential authentication

1. Upon completion of a scan, on the _Scan Overview_ page, view the _Completed Assets_ table.
2. Locate the asset you have added credentials to.
3. Look at the _Authentication_ column for the located asset.
4. For more information on Understanding Credential Authentication Status, see the next section.
5. For more details, click on the status.
The Security Console will bring you to the _Node_ Page.
6. In the asset details, locate _Credentials_ and click on the detail listed.
7. The Security Console will bring you to the _Services_ table.
8. Under the _Authentication_ column, the security console will display which credential was a success or failure.

## Understanding credential authentication status

In the _Authentication_ column, the security console will display one of the following notes to determine the status of your credential authentication:

* **Unknown:** Credentials did not return a status or you were running a discovery scan.
* **Partial Credential Success:** Many different types of credentials were used, with one or more service being correct and one or more being incorrect.
* **Credential Success:** Correct credentials were provided for range of assets.
* **Credential Failure:** Incorrect credentials were provided for range of assets.
* **No Credentials Used:** No credentials provided for range of assets.