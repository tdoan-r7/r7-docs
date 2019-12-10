---
title: "Scan Engine Data Collection - Rules and Details"
excerpt: ""
---
This article explains the rules and details that may apply to Scan Engine data collection in specific scanning scenarios.

# Enumeration Limitations on Active Directory Domain Controllers

When a vulnerability scan successfully authenticates to a target asset, the Scan Engine enumerates all individual user accounts and user groups found on that asset.  Due to their nature and purpose, assets that have been deployed as Active Directory domain controllers can often have thousands of these user accounts and user groups.

In order to mitigate against the potential performance impact of user enumeration on scans that target Active Directory domain controllers, Scan Engines will only enumerate up to 2,000 individual user accounts and 2,000 user groups per asset.

As a result of this rule, the maximum possible number of enumerated user-related objects is 4,000 per asset.