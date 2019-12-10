---
title: "Using LM/NTLM hash authentication"
excerpt: ""
---
InsightVM can pass LM and NTLM hashes for authentication on target Windows or Linux CIFS/SMB services. With this method, known as “pass the hash,” it is unnecessary to “crack” the password hash to gain access to the service.

Several tools are available for extracting hashes from Windows servers. One solution is Metasploit, which allows automated retrieval of hashes. For information about Metasploit, go to [www.rapid7.com](https://www.rapid7.com/).

When you have the hashes available, take the following steps:

If you want to add credentials while configuring a new site, click the **Create site** button on the _Home_ page.
OR
Click the **Create** tab at the top of the page and then select _Site_ from the drop-down list.

If you want to add credentials for an existing site, click that site's **Edit** icon in the Sites table on the _Home_ page.

1. Select **Authentication**.
2. Click **Add Credentials**.
3. In the _Add Credentials_ form, enter a name and description for a new set of credentials if necessary.
4. Click **Account** under _Add Credentials_.
5. Select _Microsoft Windows/Samba LM/NTLM Hash (SMB/CIFS)_ from the **Service** drop-down list.
6. (Optional) Enter the appropriate domain.
7. Enter a user name.
8. Enter or paste in the LM hash followed by a colon (:) and then the NTLM hash. Make sure there are no spaces in the entry. The following example includes hashes for the password _test_:
```
01FC5A6BE7BC6929AAD3B435B51404EE:0CB6948805F797BF2A82807973B89537
```
9. Alternatively, using the NTLM hash alone is acceptable as most servers disregard the LM response:
```
0CB6948805F797BF2A82807973B89537
```
10. When you have finished configuring the credentials, click **Create** if it is a new set or **Save** if it is a previously created set.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/374253a-s_nx_ntlm_hash.PNG",
        "s_nx_ntlm_hash.PNG",
        1187,
        586,
        "#2c3643"
      ],
      "caption": "NTLM hash"
    }
  ]
}
[/block]