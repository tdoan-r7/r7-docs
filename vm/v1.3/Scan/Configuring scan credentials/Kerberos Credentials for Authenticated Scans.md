---
title: "Kerberos Credentials for Authenticated Scans"
excerpt: ""
---
The Security Console now allows you to configure scan credentials using the Kerberos network authentication protocol. Like all other scan credential options, you can configure Kerberos scan credentials on a site-specific or shared basis.

# Requirements

Unlike other scan credential types, the Kerberos scan credential feature relies on a matching external authentication source configuration in the Security Console. To use Kerberos for authenticated scanning, you must configure a Kerberos external authentication source.

If you have not configured this external authentication source already, see the [Kerberos authentication](doc:configuring-kerberos-authentication) page for instructions on how to do so.

# Constraints

Since this feature relies on a matching Keberos external authentication source to operate, organizations with multi-console environments must take extra steps to avoid any configuration conflicts.

If your organization has multiple Security Console deployments that all use the same Scan Engine, all external Kerberos authentication sources on those consoles **must be identical**.  If discrepancies exist between each external authentication source, it could prevent the Scan Engine from authenticating properly to target assets.
[block:callout]
{
  "type": "warning",
  "title": "NOTE - Credential Test Limitation",
  "body": "Kerberos credential tests with distributed Scan Engines will fail until you have successfully run an authenticated scan using those credentials on the same target.  This behavior is expected since the Security Console does not use the needed information from the matching Kerberos external authentication source until a scan initiates.\n\nGiven this condition, do not be alarmed when your credential test fails in first-time configurations.  To determine if your Kerberos credentials are configured properly, attempt an authenticated scan with those same credentials and verify that the volume of your scan results is sufficiently large to indicate authentication."
}
[/block]
# Kerberos Scan Credential Configuration Procedures

After verifying that your Security Console meets the [external authentication source requirements](doc:kerberos-credentials-for-authenticated-scans#section-requirements), you can configure Kerberos scan credentials in the following ways:

* [Site-specific credentials](doc:kerberos-credentials-for-authenticated-scans#section-configure-site-specific-credentials)
* [Shared credentials](doc:kerberos-credentials-for-authenticated-scans#section-configure-shared-credentials)

## Configure Site-Specific Credentials

**To configure Kerberos scan credentials in a site configuration:**

1. In a new or existing site configuration, click the **Authentication** tab.
2. Click the **Add Credentials** subtab. The **General** portion of the “Add Credentials” view displays.
3. Name and optionally describe your credentials.
4. Click the **Account** subtab to open the credential service selection view.
5. Expand the dropdown next to “Service” and select **Kerberos**.
6. Enter the name of your Kerberos realm in the “Realm” field.
7. Enter your username, password, and password confirmation.
8. If desired, open the **Restrictions** tab to restrict the use of these credentials to a single asset.
9. Click **Create** when finished.
10. Finally, click **Save** in the upper right corner of the screen to save your site configuration.

## Configure Shared Credentials

**To configure shared Kerberos scan credentials:**

1. In your left navigation menu, click the **Administration** tab.
2. In the “Scan Options” section, click **Create** next to “Shared Credentials”.
3. The “Shared Scan Credential Configuration” page displays.  On the **General** tab, name and optionally describe your credentials.
4. Click the **Account** tab. Expand the dropdown next to “Service” and select **Kerberos**.
5. Enter the name of your Kerberos realm in the “Realm” field.
6. Enter your username, password, and password confirmation.
7. If desired, open the **Restrictions** tab to restrict the use of these credentials to a single asset.
8. Click the **Site Assignment** tab. Determine whether the credentials should be available to all sites or just those that you specify.
9. Finally, click **Save** in the upper right corner of the screen to complete your shared credential configuration.
[block:callout]
{
  "type": "success",
  "title": "Kerberos credentials are ready!",
  "body": "You should now have properly configured Kerberos scan credentials for the purposes of running authenticated scans."
}
[/block]