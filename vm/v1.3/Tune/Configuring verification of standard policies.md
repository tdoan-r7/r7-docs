---
title: "Configuring verification of standard policies"
excerpt: ""
---
##Configuring testing for Oracle policy compliance

To configure the application to test for Oracle policy compliance you must edit the default XML policy template for Oracle (oracle.xml), which is located in [installation_directory]/plugins/java/1/OraclePolicyScanner/1.

To configure the application to test for Oracle policy compliance:

1. Copy the default template to a new file name.
2. Edit the policy elements within the XML tags.
3. Move the new template file back into the [installation_directory]/plugins/java/1/OraclePolicyScanner/1 directory.

To add credentials for Oracle Database policy compliance scanning:

1. Go to the _Credentials_ page for the site that will incorporate the new scan template.
2. Select _Oracle_ as the login service domain.
3. Type a user name and password for an Oracle account with DBA access. See [Configuring scan credentials](doc:configuring-scan-credentials).
4. Configure any other template settings as desired. When you have finished configuring the scan template, click **Save**.

##Configure testing for Lotus Domino policy compliance

To configure the application to test for Lotus Domino policy compliance you must edit the default XML policy template for Lotus Domino (domino.xml), which is located in [installation_directory]/plugins/java/1/NotesPolicyScanner/1.

To configure the application to test for Lotus Domino policy compliance:

1. Copy the default template to a new file name.
2. Edit the policy elements within the XML tags.
3. Move the new template file back into the [installation_directory]/plugins/java/1/NotesPolicyScanner/1.
4. Go to the _Lotus Domino Policy_ page and enter the new policy file name in the text field.

To add credentials for Lotus Domino policy compliance scanning:

1. Go to the _Credentials _page for the site that will incorporate the new scan template.
2. Select _Lotus Notes/Domino_ as the login service domain.
3. Type a Notes ID password in the text field. See [Configuring scan credentials](doc:configuring-scan-credentials).
4. For Lotus Notes/Domino policy compliance scanning, you must install a Notes client on the same host computer that is running the Security Console.
5. Configure any other template settings as desired. When you have finished configuring the scan template, click **Save**.

##Configure testing for Windows Group Policy compliance

You can configure InsightVM to verify whether assets running with Windows operating systems are compliant with Microsoft security standards. The installation package includes three different policy templates that list security criteria against that you can use to check settings on assets. These templates are the same as those associated with Windows Policy Editor and Active Directory Group Policy. Each template contains all of the policy elements for one of the three types of Windows target assets: workstation, general server, and domain controller.

A target asset must meet all the criteria listed in the respective template for the application to regard it as compliant with Windows Group Policy. To view the results of a policy scan, create a report based on the Audit or Policy Evaluation report template. Or, you can create a custom report template that includes the Policy Evaluation section. See [Fine-tuning information with custom report templates](doc:configuring-custom-report-templates#section-fine-tuning-information-with-custom-report-templates).

The templates are _.inf_ files located in the plugins/java/1/WindowsPolicyScanner/1 path relative to the application base installation directory:

* The basicwk.inf template is for workstations.
* The basicsv.inf template is for general servers.
* The basicdc.inf template is for domain controllers.
[block:callout]
{
  "type": "warning",
  "body": "Use caution when running the same scan more than once with less than the lockout policy time delay between scans. Doing so could also trigger account lockout."
}
[/block]
You also can import template files using the Security Templates Snap-In in the Microsoft Group Policy management Console, and then saving each as an _.inf_ file with a specific name corresponding to the type of target asset.

You must provide the application with proper credentials to perform Windows policy scanning. See [Configuring scan credentials](doc:configuring-scan-credentials).

Go to the _Windows Group Policy_ page, and enter the _.inf_ file names for workstation, general server, and domain controller policy names in the appropriate text fields.

To save the new scan template, click **Save**.

##Configure testing for CIFS/SMB account policy compliance

InsightVM can test account policies on systems supporting CIFS/SMB, such as Microsoft Windows, Samba, and IBM AS/400:

1. Go to the **CIFS/SMB Account Policy** page.
2. Type an account lockout threshold value in the appropriate text field.
This the maximum number of failed logins a user is permitted before the asset locks out the account.
3. Type a minimum password length in the appropriate text field.
4. Configure any other template settings as desired. When you have finished configuring the scan template, click **Save**.

##Configure testing for AS/400 policy compliance

To configure InsightVM to test for AS/400 policy compliance:
1. Go to the _AS/400 Policy_ page.
2. Type an account lockout threshold value in the appropriate text field.
This the maximum number of failed logins a user is permitted before the asset locks out the account. The number corresponds to the QMAXSIGN system value.
3. Type a minimum password length in the appropriate text field.
This number corresponds to the QPWDMINLEN system value and specifies the minimum length of the password field required.
4. Select a **minimum security level** from the drop-down list.
This level corresponds to the minimum value that the QSECURITY system value should be set to. The level values range from Password _security (20)_ to _Advanced integrity protection (50)_.
5. Configure any other template settings as desired. When you have finished configuring the scan template, click **Save**.

##Configure testing for UNIX policy compliance

To configure InsightVM to test for UNIX policy compliance:
1. Go to the _Unix Policy_ page.
2. Type a number in the text field labeled **Minimum account umask value**.
This setting controls the permissions that the target system grants to any new files created on it. If the application detects broader permissions than those specified by this value, it will report a policy violation.
3. Configure any other template settings as desired. When you have finished configuring the scan template, click **Save**.