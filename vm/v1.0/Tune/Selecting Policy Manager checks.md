---
title: "Selecting Policy Manager checks"
excerpt: ""
---
If you work for a U.S. government agency, a vendor that transacts business with the government or for a company with strict configuration security policies, you may be running scans to verify that your assets comply with United States Government Configuration Baseline (USGCB) policies, Center for Internet Security (CIS) benchmarks, or Federal Desktop Core Configuration (FDCC). Or you may be testing assets for compliance with customized policies based on these standards. The built-in USGCB, CIS, and FDCC scan templates include checks for compliance with these standards. See [Scan templates](doc:scan-templates).

These templates do not include vulnerability checks, so if you want to run vulnerability checks with the policy checks, create a custom version of a scan template using one of the following methods:

* Add vulnerability checks to a customized copy of USGCB, CIS, DISA, or FDCC template.
* Add USGCB, CIS, DISA STIG, or FDCC checks to one of the other templates that includes the vulnerability checks that you want to run.
* Create a scan template and add USGCB, CIS, DISA STIG, or FDCC checks and vulnerability checks to it.

To use the second or third method, you will need to select USGCB, CIS, DISA STIGS, or FDCC checks by taking the following steps. You must have a license that enables the Policy Manager and FDCC scanning.

1. Select **Policies** in the _General_ page of the _Scan Template Configuration_ panel.
2. Go to the _Policy Manager_ page of the _Scan Template Configuration_ panel.
3. Select a policy.
4. Review the name, affected platform, and description for each policy.
5. Select the check box for any policy that you want to include in the scan.
6. If you are required to submit policy scan results in Asset Reporting Format (ARF) reports to the U.S. government for SCAP certification, select the check box to store SCAP data.
[block:callout]
{
  "type": "info",
  "body": "Stored SCAP data can accumulate rapidly, which can have a significant impact on file storage."
}
[/block]
7. If you want to enable recursive file searches on Windows systems, select the appropriate check box. It is recommended that you not enable this capability unless your internal security practices require it. See [Enabling recursive searches on Windows](doc:selecting-policy-manager-checks#section-enabling-recursive-searches-on-windows).
[block:callout]
{
  "type": "danger",
  "body": "Recursive file searches can increase scan times significantly. A scan that typically completes in several minutes on an asset may not complete for several hours on that single asset, depending on various environmental conditions."
}
[/block]
8. Configure any other template settings as desired. When you have finished configuring the scan template, click **Save**.

For information about verifying USGCB, CIS, or FDCC compliance, see [Working with Policy Manager results](doc:working-with-policy-manager-results).
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/3a178c7-s_nx_scan_template_policy_manager.jpg",
        "s_nx_scan_template_policy_manager.jpg",
        1860,
        836,
        "#1d2735"
      ],
      "caption": "Selecting Policy Manager check settings"
    }
  ]
}
[/block]
##Enabling recursive searches on Windows

By default, recursive file searches are disabled for scans on assets running Microsoft Windows. Searching every sub-folder of a parent folder in a Windows file system can increase scan times on a single asset by hours, depending on the number of folders and files and other conditions. Only enable recursive file searches if your internal security practices require it or if you require it for certain rules in your policy scans. The following rules require recursive file searches:

DISA-6/Win2008
SV-29465r1_rule
Remove Certificate Installation Files

DISA-1/Win7
SV-25004r1_rule
Remove Certificate Installation Files
[block:callout]
{
  "type": "info",
  "body": "Recursive file searches are enabled by default on Linux systems and cannot be disabled."
}
[/block]