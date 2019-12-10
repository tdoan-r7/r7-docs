---
title: "Using SSH public key authentication"
excerpt: ""
---
You can use InsightVM to perform credentialed scans on assets that authenticate users with SSH public keys.

This method, also known as asymmetric key encryption, involves the creation of two related keys, or large, random numbers:

* a public key that any entity can use to encrypt authentication information
* a private key that only trusted entities can use to decrypt the information encrypted by its paired public key

When generating a key pair, keep the following guidelines in mind:

* The application supports SSH protocol version 2 RSA and DSA keys.
* Keys must be OpenSSH-compatible and PEM-encoded.
* RSA keys can range between 768 and 16384 bits.
* DSA keys must be 1024 bits.

This topic provides general steps for configuring an asset to accept public key authentication. For specific steps, consult the documentation for the particular system that you are using.

The ssh-keygen process will provide the option to enter a pass phrase. It is recommended that you use a pass phrase to protect the key if you plan to use the key elsewhere.

## Generating a key pair

1. Run the ssh-keygen command to create the key pair, specifying a secure directory for storing the new file.

This example involves a 2048-bit RSA key and incorporates the /tmp directory, but you should use any directory that you trust to protect the file.
```
ssh-keygen -t rsa -b 2048 -f /tmp/id_rsa
```

This command generates the private key files, id_rsa, and the public key file, id_rsa.pub.

2. Make the public key available for the application on the target asset.
3. Make sure that the computer with which you are generating the key has a .ssh directory. If not, run the mkdir command to create it:
```
mkdir /home/[username]/.ssh
```
4. Copy the contents of the public key that you created by running the command in step 1. The file is in /tmp/id_rsa.pub file.

**Note:** Some checks require root access.

Append the contents on the target asset of the /tmp/id_rsa.pub file to the .ssh/authorized_keys file in the home directory of a user with the appropriate access-level permissions that are required for complete scan coverage.
```
cat /[directory]/id_rsa.pub >> /home/[username]/.ssh/authorized_keys
```
5. Provide the private key.

After you provide the private key you must provide the application with SSH public key authentication.
## Providing SSH public key authentication

If you want to add SSH credentials while configuring a new site, click the **Create site** button on the _Home_ page.
OR
Click the **Create** tab at the top of the page and then select _Site_ from the drop-down list.

If you want to add SSH credentials for an existing site, click that site's **Edit** icon in the _Sites_ table on the _Home_ page.

1. Click the **Authentication** tab in the site configuration .
2. Click **Add Credentials**.
3. In the _Add Credentials_ form, enter a name and description for a new set of credentials if necessary.
4. Click **Account** under _Add Credentials_.
5. Select _Secure Shell (SSH) Public Key_ as the from **Service** drop-down list.

**Note:** ssh/authorized_keys is the default file for most OpenSSH- and Drop down-based SSH daemons. Consult the documentation for your Linux distribution to verify the appropriate file.

> This authentication method is different from the method listed in the drop-down as _Secure Shell (SSH)_. This latter method incorporates passwords instead of keys.

6. Enter the appropriate user name.
7. (Optional) Enter the Private key password used when generating the keys.
8. Confirm the private key password.
9. Copy the contents of that file into the **PEM-format private key** text box. The private key that you created is the /tmp/id_rsa file on the target asset.
10. (Optional) Elevate permissions to _sudo_ or _su_.
You can elevate permissions for both _Secure Shell (SSH)_ and _Secure Shell (SSH) Public Key_ services.
11. (Optional) Enter the appropriate user name. The permission elevation user needs to be set to root. To do this, the user's permission elevation type needs to be set to ```sudo``` and the permission elevation user needs to be set as ```root```.
12. The user name can be empty for sudo credentials. If you are using su credentials with no user name the credentials will default to root as the user name.

>If the SSH credential provided is a root credential, user ID =0, the permission elevation credentials will be ignored, even if the root account has been renamed. The application will ignore the permission elevation credentials when any account, root or otherwise named, with user ID 0 is specified.

13. When you have finished configuring the credentials, click **Create** if it is a new set, or **Save** if it is a previously created set.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/57a5202-s_nx_ssh_public_key.PNG",
        "s_nx_ssh_public_key.PNG",
        822,
        607,
        "#2b3542"
      ],
      "caption": "SSH Public Key configuration"
    }
  ]
}
[/block]