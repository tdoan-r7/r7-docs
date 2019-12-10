---
title: "Managing shared scan credentials"
excerpt: ""
---
You can create and manage scan credentials that can be used in multiple sites. Using _shared credentials_ can save time if you need to perform authenticated scans on a high number of assets in multiple sites that require the same credentials. It’s also helpful if these credentials change often. For example, your organization’s security policy may require a set of credentials to change every 90 days. You can edit that set in one place every 90 days and apply the changes to every site where those credentials are used. This eliminates the need to change the credentials in every site every 90 days.

To configure shared credentials, you must have a Global Administrator role or a custom role with Manage Site permissions.

To learn the differences between shared and site-specific credentials, review [Shared Credentials vs. Site Specific Credentials](doc:configuring-scan-credentials#section-shared-credentials-vs-site-specific-credentials).

###Creating a set of shared scan credentials

Creating a set of shared scan credentials includes the following actions:

1. [Naming and describing the new set of shared credentials](doc:managing-shared-scan-credentials#section-naming-and-describing-the-new-set-of-shared-credentials) 
2. [Configuring the account for authentication](doc:managing-shared-scan-credentials#section-configuring-the-account-for-authentication) 
3. [Restricting the credentials to a single asset and port](doc:managing-shared-scan-credentials#section-restricting-the-credentials-to-a-single-asset-and-port)
4. [Assigning shared credentials to sites](doc:managing-shared-scan-credentials#section-assigning-shared-credentials-to-sites)

After you create a set of shared scan credentials you can take the following actions to manage them:

* [Viewing shared credentials](doc:managing-shared-scan-credentials#section-viewing-shared-credentials)
* [Editing shared credentials that were previously created](doc:managing-shared-scan-credentials#section-editing-shared-credentials-that-were-previously-created)
* [Verifying scan credential authentication](doc:managing-shared-scan-credentials#section-verifying-scan-credential-authentication)
* [Understanding credential authentication scan](doc:managing-shared-scan-credentials#section-understanding-credential-authentication-status)

###Naming and describing the new set of shared credentials

Think of a name and description that will help Site Owners recognize at a glance which assets the credentials will be used for.

1. Click the **Administration** tab.
2. On the Administration page, click the **create** link for _Shared Scan Credentials_.
The Security Console displays the _General_ page of the _Shared Scan Credentials Configuration_ panel.
3. Enter a name for the new set of credentials.
4. Enter a description for the new set of credentials.
5. Continue with configuring the account, as described in the next section.

###Configuring the account for authentication

Configuring the account involves selecting an authentication method or service and providing all settings that are required for authentication, such as a user name and password.

If you do not know what authentication service to select or what credentials to use for that service, consult your network administrator.

1. Go to the _Account_ page of the _Shared Scan Credentials Configuration_ panel.
2. Select an authentication service or method from the drop-down list.
3. Enter all requested information in the appropriate text fields.
4. If you want to test the credentials or restrict them see the following two sections. Otherwise, click **Save**.

###Testing shared scan credentials

You can verify that a target asset will authenticate a Scan Engine with the credentials you’ve entered. It is a quick method to ensure that the credentials are correct before you run the scan.

For shared scan credentials, a successful authentication test on a single asset does not guarantee successful authentication on all sites that use the credentials.

1. Go to the _Account_ page of the _Credentials Configuration_ panel.
2. Expand the **Test Credentials** section.
3. Select the Scan Engine with which you will perform the test.
4. Enter the name or IP address of the authenticating asset.
5. To test authentication on a single port, enter a port number.
6. Click **Test credentials**.

Note the result of the test. If it was not successful, review and change your entries as necessary, and test them again.

1. Upon seeing a successful test result, configure any other settings as desired.
2. If you want to restrict the credentials to a specific asset or port, see the following section. Otherwise, click **Save**.

###Restricting the credentials to a single asset and port

If a particular set of credentials is only intended for a specific asset and/or port, you can restrict the use of the credentials accordingly. Doing so can prevent scans from running unnecessarily longer due to authentication attempts on assets that don’t recognize the credentials.

If you restrict credentials to a specific asset and/or port, they will not be used on other assets or ports.

Specifying a port allows you to limit your range of scanned ports in certain situations. For example, you may want to scan Web applications using HTTP credentials. To avoid scanning all Web services within a site, you can specify only those assets with a specific port.

1. Go to the _Restrictions_ page of the _Shared Scan Credentials Configuration_ panel.
2. Enter the host name or IP address of the asset that you want to restrict the credentials to.
OR
Enter host name or IP address of the asset and the number of the port that you want to restrict the credentials to.
3. When you have finished configuring the set of credentials, click **Save**.

###Assigning shared credentials to sites

You can assign a set of shared credentials to one or more sites. Doing so makes them appear in lists of available credentials for those site configurations. Site Owners still have to enable the credentials in the site configurations. See [Configuring scan credentials](doc:configuring-scan-credentials).

To assign shared credentials to sites, take the following steps:

1. Go to the _Site assignment_ page of the _Shared Scan Credentials Configuration_ panel.
2. Select one of the following assignment options:
* Assign the credentials to all current and future sites
* Create a custom list of sites that can use these credentials

If you select the latter option, the Security Console displays a button for selecting sites.
1. Click Select Sites.
The Security Console displays a table of sites.
2. Select the check box for each desired site, or select the check box in the top row for all sites. Then click **Add sites**.
The selected sites appear on the _Site Assignment_ page.
3. Configure any other settings as desired. When you have finished configuring the set of credentials, click **Save**.

###Viewing shared credentials

1. Click the Administration icon.
The Security Console displays the _Administration_ page.
2. Click the **manage** link for _Shared Scan Credentials_.
The Security Console displays a page with a table that lists each set of shared credentials and related configuration information.

###Editing shared credentials that were previously created

The ability to edit credentials can be very useful, especially if passwords change frequently.

1. Click the **Administration** icon.
The Security Console displays the _Administration_ page.
2. Click the **manage** link for _Shared Scan Credentials_.
The Security Console displays a page with a table that lists each set of shared credentials and related configuration information.
3. Click the name of the credentials that you want to change, or click **Edit** for that set of credentials.
4. Change the configuration as desired. See the following topics for more information:


* [Naming and describing the new set of shared credentials](doc:managing-shared-scan-credentials#section-naming-and-describing-the-new-set-of-shared-credentials)
* [Configuring the account for authentication](doc:managing-shared-scan-credentials#section-configuring-the-account-for-authentication)
* [Testing shared scan credentials](doc:managing-shared-scan-credentials#section-testing-shared-scan-credentials)
* [Restricting the credentials to a single asset and port](doc:managing-shared-scan-credentials#section-restricting-the-credentials-to-a-single-asset-and-port)
* [Assigning shared credentials to sites](doc:managing-shared-scan-credentials#section-assigning-shared-credentials-to-sites)

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

##Understanding credential authentication status

In the _Authentication_ column, the security console will display one of the following notes to determine the status of your credential authentication:

* **Unknown:** Credentials that do not return a success status or run a discovery scan.
* **Partial Credential Success:** Many different types of credentials were used, with one or more service being correct and one or more being incorrect.
* **Credential Success:** Correct credentials were provided for range of assets.
* **Credential Failure:** Incorrect credentials were provided for range of assets.
* **No Credentials Used:** No credentials provided for range of assets.