---
title: "Vulnerabilities frequently asked questions"
excerpt: ""
---
This page concerns vulnerabilities.

## How does the application verify that a Certificate Authority is trustworthy?

During a Web site scan, the application checks the name of the Certificate Authority (CA) that issued the site's certificate against a list of trusted CAs that is included with the product. If the CA doesn't match a name on the list, the application reports a vulnerability. The list of trusted CAs is viewable in the proof section of the reported vulnerability details.

## What is the "X.509 Certificate Subject CN does not match the entity name" vulnerability?

When the application scans a Web site, it verifies the validity of site's security certificate. If a certificate is invalid, an attacker can launch a man-in-the-middle attack and gain full control of the data stream. One of the requirements of a valid X.509 certificate is that its subject common name (CN) field must match the name associated with the asset. For example, in a certificate presented by "https://www.example.com/", the CN should be "www.example.com". If this is not the case, the application reports a vulnerability.

Before issuing a certificate, a Certification Authority (CA) must check the identity of the entity requesting the certificate, as specified in the CA's Certification Practice Statement (CPS).

## How do I determine if my server supports weak SSL ciphers?

If your server supports weak SSL ciphers, the application will report a vulnerability:

* "TLS/SSL Server Supports Weak Cipher Algorithms"

You can learn about this vulnerability and how to remediate it by reading the vulnerability details.

To determine if your server supports weak SSL ciphers...

Make sure that OpenSSL is installed on the server.
```
# openssl s_client -connect SERVERNAME:443 -cipher LOW:EXP
```
If the server does not support weak ciphers you will see the following error message or something similar:
```
# openssl s_client -connect SERVERNAME:443 -cipher LOW:EXP
CONNECTED(00000003)
461:error:140790E5:SSL routines:SSL23_WRITE:ssl handshake
failure:s23_lib.c:226:
```

## How do I determine if my server supports SSLv2?

SSLv2 is a version of SSL known to be vulnerable. If your server supports it, the application will report a vulnerability, which may be one of the following:
* "TLS/SSL Server Supports SSLv2" (common)
* "TLS/SSL Server Does Not Support Newer TLS or SSLv3 Protocols" (very rare)

You can learn about these vulnerabilities and how to remediate them by reading the vulnerability details.

To determine if your server supports SSLv2...

Make sure that OpenSSL is installed on the server.

Run the following command, assuming port 443 provides HTTPS connections: ```# openssl s_client -ssl2 -connect SERVERNAME:443```

If the server does not support SSLv2 you will see the following error message or something similar:
```
# openssl s_client -ssl2 -connect SERVERNAME:443
CONNECTED(00000003)
458:error:1407F0E5:SSL routines:SSL2_WRITE:ssl handshake
failure:s2_pkt.c:428:
```
####What's the difference between "confirmed," "unconfirmed," and "potential" vulnerabilities?

When the application scans an asset, it performs a sequence of discoveries, verifying the existence of an asset, port, service, and variety of service (for example, an Apache Web server or an IIS Web server). Then, it attempts to test the asset for vulnerabilities known to be associated with that asset, based on the information gathered in the discovery phase. If it is able to verify a vulnerability, it reports a "confirmed" vulnerability. If the application is unable to verify a vulnerability known to be associated with that asset, it reports an "unconfirmed" or "potential" vulnerability. The difference between these latter two classifications is the level of probability. Unconfirmed vulnerabilities are more likely to exist than potential ones, based on the asset's profile. See the FAQ about potential vulnerabilities in this section.

## What is a potential vulnerability?

The application runs software version checks required by the Payment Card Industry (PCI) for compliance audits. Regardless of how many patches or protection mechanisms have been implemented on a scanned asset, it will flag a vulnerability if it discovers a software version known to be vulnerable. If it cannot prove the vulnerability actually exists, it will classify it as a "potential vulnerability."

## What do the vulnerability severity rankings mean?

The application assigns one of three severity rankings to every vulnerability that it discovers:
* moderate
* severe
* critical

The application uses various factors to rate severity, including CVSS scores, vulnerability age and prevalence, and whether exploits are available.

## What methods does the application use to detect vulnerabilities?

The application uses exploitation methods typically associated with hackers, inspecting registry keys, banners, software version numbers, and other indicators of susceptibility.

## How does the Security Console check for obsolete software vulnerabilities?

Obsolete software vulnerabilities are checked based on fingerprint results and other data. The Security Console will find devices that are vulnerable, if the devices have software that is known to be obsolete. The qualification for obsolete varies; but, in general, it depends on information published by the software vendors as to whether the product is end-of-life (EOL) or otherwise not supported. Rapid7 makes determinations on a case-by-case basis, in the event that there is insufficient data provided or accessible from the vendor as to whether the software product would be considered obsolete.