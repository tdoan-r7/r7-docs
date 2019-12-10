---
title: "Performing configuration assessment"
excerpt: ""
---
Performing regular audits of configuration settings on your assets may be mandated in your organization. Whether you work for a United States government agency, a company that does business with the federal government, or a company with strict security rules, you may need to verify that your assets meet a specific set of configuration standards. For example, your company may require that all of your workstations lock out users after a given number of incorrect logon attempts.

Like vulnerability scans, policy scans are useful for gauging your security posture. They help to verify that your IT department is following secure configuration practices. Using the application, you can scan your assets as part of a configuration assessment audit. A license-enabled feature named Policy Manager provides compliance checks for several configuration standards:

###USGCB 2.0 policies

The United States Government Configuration Baseline (USGCB) is an initiative to create security configuration baselines for information technology products deployed across U.S. government agencies. USGCB 2.0 evolved from FDCC (see below), which it replaces as the configuration security mandate in the U.S. government. Companies that do business with the federal government or have computers that connect to U.S. government networks must conform to USGCB 2.0 standards. For more information, go to usgcb.nist.gov.

###USGCB 1.0 policies

USGCB 2.0 is not an “update” of 1.0. The two versions are considered separate entities. For that reason, the application includes USGCB 1.0 checks in addition to those of the later version. For more information, go to usgcb.nist.gov.

###FDCC policies

The Federal Desktop Core Configuration (FDCC) preceded USGCB as the U.S. government-mandated set of configuration standards. For more information, go to fdcc.nist.gov.

###CIS benchmarks

These benchmarks are consensus-based, best-practice security configuration guidelines developed by the not-for-profit Center for Internet Security (CIS), with input and approval from the U.S. government, private-sector businesses, the security industry, and academia. The benchmarks include technical control rules and values for hardening network devices, operating systems, and middleware and software applications. They are widely held to be the configuration security standard for commercial businesses. For more information, go to www.cisecurity.org.

###How do I run configuration assessment scans?

Configure a site with a scan template that includes Policy Manager checks. Depending on your license, the application provides built-in USGCB, FDCC, and CIS templates. These templates do not include vulnerability checks. If you prefer to run a combined vulnerability/policy scan, you can configure a custom scan template that includes vulnerability checks and Policy Manager policies or benchmarks. See the following sections for more information:
* [Selecting the type of scanning you want to do](doc:configuring-custom-scan-templates#section-selecting-the-type-of-scanning-you-want-to-do)
* [Selecting Policy Manager checks](doc:selecting-policy-manager-checks) 

###How do I know if my license enables Policy Manager?

To verify that your license enables Policy Manager and includes the specific checks that you want to run, go the _Licensing_ page on the _Security Console Configuration_ panel. See [Viewing, activating, renewing, or changing your license](doc:managing-versions-updates-and-licenses#section-viewing-activating-renewing-or-changing-your-license).

###What platforms are supported by Policy Manager checks?

For a complete list of platforms that are covered by Policy Manager checks, go to the Rapid7Community at https://community.rapid7.com/docs/DOC-2061.

###How do I view Policy Manager scan results?

Go to the _Policies_ page, where you can view results of policy scans, including those of individual rules that make up policies. You can also override rule results. See [Working with Policy Manager results](doc:working-with-policy-manager-results).

###Can I create custom checks based on Policy Manager checks?

You can customize policy checks based on Policy Manager checks. See [Creating a custom policy](doc:creating-a-custom-policy).