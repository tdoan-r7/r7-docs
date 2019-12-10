---
title: "Administration & maintenance"
excerpt: ""
---
This page concerns managing and maintaining the InsightVM system.

## How do I run manual product updates?

You can run update by using the Web interface (see [Managing versions, updates, and licenses](doc:managing-versions-updates-and-licenses)) or by using the update now command in the command console (see [Using the command console](doc:using-the-command-console)).

## I recently restored a backup. Now InsightVM is indicating that my license is expired.

The InsightVM license is one of the items that are included in a backup. When you restore a backup, InsightVM overwrites the current license with the license that was active at the time of the backup. Contact [Technical Support](doc:support-technical-support-and-customer-care) to have a new license key generated or to reactivate your old license.

## Can I import an arbitrary certificate that I generated?

The signed certificate must be based on a InsightVM-generated certificate signing request (CSR). Within InsightVM, you cannot import an arbitrary key pair/certificate that you generated. InsightVM, by default, uses a self-signed X.509 certificate, which is created during installation. You can replace this certificate with a custom, self-signed certificate or with a certificate signed by a trusted certification authority (CA), such as VeriSign, Thawte, or your own CA.

## How do I know if my version of InsightVM is up to date?

Currently, it is not possible to find out what the current version of InsightVM is by looking through the Web interface. InsightVM automatically installs software updates on a regular basis. To ensure that you are using the current version, enter the ```update now``` command any time on the admin/global/diag_console.html page of the InsightVM Security Console Web interface.

To find out what version of InsightVM is running, enter the command ```ver``` or ```version```on the admin/global/diag_console.html page.

## What gets backed up when I back up the InsightVM database?

A backup includes the following items:
* the database itself
* configuration files (nsc.xml nse.xml userdb.xml consoles.xml)
* licenses
* keystores
* report images
* custom report templates
* custom scan templates
* generated reports
* scan logs

Backing up these items makes it possible for you to migrate InsightVM from one host computer to another without having to obtain a new license or reconfigure InsightVM.

## What types of encryption does the application use?

To ensure the security of the application, InsightVM uses the following types of encryption algorithm keys in these areas:
* Identification/authentication: RSA
* Credential password storage: RSA
* Connection to the Web interface: RSA and HTTP over SSL
* Credential encryption: 3DES encrypted with RSA
* Security Console to Scan Engine communication: TLSv1.2, TLS_ECDHE_RSA_WITH_AES_128_CBC_SHA256 for backwards compatibility, and TLS_ECDHE_ECDSA_WITH_AES_256_GCM_SHA384.