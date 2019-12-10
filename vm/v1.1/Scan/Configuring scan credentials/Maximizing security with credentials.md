---
title: "Maximizing security with credentials"
excerpt: ""
---
The application provides features to protect your credentials from unauthorized use. It securely stores and transmits credentials using encryption. Global Administrators can assign permission to add and edit credentials to only those users that should have that level of access. For more information, see [Managing users and authentication](doc:managing-users-and-authentication). When creating passwords, make sure to use standard best practices, such as long, complex strings with combinations of lower- and upper-case letters, numerals, and special characters.

## Security best practices on Windows

If you plan to run authenticated scans on Windows assets, keep in mind some security strategies related to automated Windows authentication. Compromised or untrusted assets can be used to steal information from systems that attempt to log onto them with credentials. This attack method threatens any network component that uses automated authentication, such as backup services or vulnerability assessment products.

There are a number of countermeasures you can take to help prevent this type of attack or mitigate its impact. For example, make sure that Windows passwords for InsightVM contain 32 or more characters generated at random. And change these passwords on a regular basis.

See the white paper for [key strategies and mitigation techniques](https://community.rapid7.com/community/infosec/blog/2014/09/17/mitigating-service-account-credential-theft).