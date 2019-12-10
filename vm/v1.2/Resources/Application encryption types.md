---
title: "Application encryption types"
excerpt: ""
---
To ensure the security of the application, Nexpose uses the following types of encryption algorithm keys in these areas:

* Identification/authentication: RSA
* Credential password storage: RSA
* Connection to the Web interface: RSA and HTTP over SSL
* Credential encryption: 3DES encrypted with RSA
* Security Console to Scan Engine communication: TLSv1.2, TLS_ECDHE_RSA_WITH_AES_128_CBC_SHA256 for backwards compatibility, and TLS_ECDHE_ECDSA_WITH_AES_256_GCM_SHA384.