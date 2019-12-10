---
title: "Managing certificates for scanning"
excerpt: ""
---
During scans, InsightVM checks Web sites and TLS or SSL servers for specific Root certificates to verify that these entities are validated by trusted Certificate Authorities (CAs).

The Security Console installation includes a number of preset certificates trusted by commonly used browsers from Microsoft, Google, Mozilla, and Apple. Additionally, you can import Root certificates that were expressly created by trusted CAs for targets that you want to scan.

The application reports a certificate signed by an unknown or untrusted entity as a vulnerability. A malicious party pretending to be a trusted entity can stage a man-in-the-middle attack, eavesdropping on TLS/SSL connections.

##Importing custom certificates

The permission required for this task is Manage Global Settings, which typically belongs to a Global Administrator.
[block:callout]
{
  "type": "warning",
  "body": "Make sure the custom certificate is a Root CA certificate. Otherwise, the full certificate chain cannot be validated during a scan. Also, the certificate must be in Privacy Enhanced Mail (PEM) base64 encoded format."
}
[/block]
1. Open the certificate file on the computer hosting it, and copy the contents of the file, including the entire BEGIN and END lines. Example:
```
-----BEGIN CERTIFICATE-----
MIIHQDCCBSigAwIBAgIJAMStF8UUH6doMA0GCSqGSIb3DQEBCwUAMIHBMQswCQYD
VQQGEwJVUzERMA8GA1UECBMITmVicmFza2ExFjAUBgNVBAcTDU5lYnJhc2thIENp
-----END CERTIFICATE-----
```
2. Click the **Administration** icon in the Security Console Web interface.
3. In the _Scan Options_ area of the _Administration_ page, click the **Manage** link for _Root Certificates_.
4. On the _Certificates_ page, click the **Import Certificates** button.
5. Paste the copied certificate into the text box and click _Import_.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/bf33b4d-s_nx_import_custom_root_certificate.jpg",
        "s_nx_import_custom_root_certificate.jpg",
        802,
        409,
        "#293640"
      ],
      "caption": "The dialog box for importing a Root certificate"
    }
  ]
}
[/block]
The certificate appears in the _Custom Certificates_ table. You also can view preset certificates on the _Root Certificates_ page.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/0dd21bb-s_nx_admin_scan_certificates.jpg",
        "s_nx_admin_scan_certificates.jpg",
        1265,
        794,
        "#f1f5f4"
      ],
      "caption": "The Root Certificates page"
    }
  ]
}
[/block]
##Removing certificates

Removing a root certificate from the trust store affects future scans in that any scanned certificates that were signed by the root certificate authority will no longer be trusted. They will be reported as vulnerabilities.

The permission required for removing custom certificates is _Manage Global Settings_, which typically belongs to a Global Administrator.
1. Click the **Administration** icon in the Security Console Web interface.
2. In the _Scan Options_ area of the _Administration_ page, click the **Manage** link for _Root Certificates_.
3. On the _Certificates_ page, find the certificate you want to delete from the _Custom Certificates_ table.
4. Click the **Delete** icon. The table refreshes and no longer displays the deleted certificate.
[block:callout]
{
  "type": "info",
  "body": "You cannot delete preset certificates."
}
[/block]