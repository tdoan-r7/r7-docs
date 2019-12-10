---
title: "Post-Installation Engine-to-Console Pairing"
excerpt: ""
---
[block:callout]
{
  "type": "warning",
  "title": "NOTE",
  "body": "This article is intended for users that elected to skip the Engine-to-Console (also referred to as “reverse”) pairing segment during the installation of a distributed Scan Engine.\n\nFor documentation on standard pairing and reverse pairing performed during an installation, see the [Distributed Scan Engines](doc:configuring-distributed-scan-engines) page."
}
[/block]
Distributed Scan Engine install wizards allow you to pair your new engine to your Security Console immediately at install time if you select the **Engine-to-Console** communication method.  However, if you decide to skip this pairing step, you must complete the pairing with a different procedure after the installation completes.

This article details this post-installation reverse pairing procedure.

# Reverse Pair (Engine-to-Console)

In order to configure an engine-to-console pairing (also known as a “reverse” pair) on a Scan Engine you have already installed, you must manually add a new Security Console entry to the Scan Engine configuration and confirm the pairing with a console-generated shared secret.  Consequently, the first step of all reverse pairing procedures is to generate the shared secret in the Security Console.

## Generate a Scan Engine Shared Secret

To generate a shared secret in the Security Console:

1. Browse to and click on the **Administration** tab in your left navigation menu.
2. In the “Scan Options” section, click **manage** next to “Engines”.
3. In the “Generate Scan Engine Shared Secret” section, click **Generate**.
4. Copy the shared secret for now.  You will use this shared secret to authenticate the connection between the Scan Engine and the Security Console.
[block:callout]
{
  "type": "info",
  "title": "TIP",
  "body": "Multiple Scan Engines can use the same console-generated shared secret for each of their reverse pairing procedures.  However, shared secrets are only valid for 60 minutes.  If your shared secret expires, you must generate a new one to complete any further reverse pairing procedures."
}
[/block]
## Add Your Security Console to the Scan Engine

Reverse pairing procedures for both Windows and Linux Scan Engine hosts must be completed using a command line interface.  You can pass commands to the Scan Engine in the following ways according to your host operating system:

### Windows Command Line Access

To open the Scan Engine command line on a Windows host:

1. Use Remote Desktop Protocol to log into your Scan Engine host, or access the host directly.
2. Open your **Start** menu and browse to the Scan Engine service applet.
3. Start the Scan Engine service in interactive mode to open the command line interface.

### Linux Command Line Access

To open the Scan Engine command line on a Linux host:

1. Open a terminal and SSH into your Scan Engine host with the following command.  Substitute `<user>` and `<address>` with the necessary values:

```
ssh <user>@<address>
```

2. After you log in to the Scan Engine host, run `sudo -i` to start a shell with elevated privileges.
3. Now that your shell has elevated privileges, start a `screen` session with the Scan Engine using the following command:

```
screen -x nexpose
```
[block:callout]
{
  "type": "danger",
  "title": "WARNING",
  "body": "Do not use `ctrl` + `c` to exit from a screen session.  This terminates the Scan Engine service.\n\nTo detach safely from a screen session on the Scan Engine, use `ctrl` + `a` +`d`."
}
[/block]
### Scan Engine Commands

Now that you have a command line interface open, you can add the Security Console to the Scan Engine.  The following commands apply to Scan Engines on both **Windows** and **Linux** hosts:

1. Add your intended Security Console with the following command.  Substitute `<address>` with the IP address of the Security Console:

```
add console <address>
```

2. Run `show consoles` to list all Security Console entries, including your new addition.  Locate your new Security Console by its IP address and take note of its console ID.
3. Using the console ID discovered in the previous step, run the following command to connect the Scan Engine to your Security Console.  Substitute `<ID>` with the necessary console ID value:

```
connect to console <ID>
```

4. Run `show consoles` again and verify that the value for `connectTo` is `1` for the intended Security Console.
5. Initiate the prompt to provide the shared secret to the Scan Engine with the following command.  Substitute `<ID>` with the same console ID as before:

```
add shared secret <ID>
```

6. When prompted, enter your shared secret that you generated in the Security Console.  A verification message indicates that the shared secret was applied successfully.
7. Finally, run the following command to enable the Security Console on the Scan Engine.  As usual, substitute `<ID>` with your console ID:

```
enable console <ID>
```

8. After the pairing completes, close the session to finish.

[block:callout]
{
  "type": "success",
  "title": "Your post-installation Scan Engine pair is finished!",
  "body": "Now that your Scan Engine is paired with the Security Console, [refresh your Scan Engine status](doc:configuring-distributed-scan-engines#section-refresh-your-new-scan-engine) to confirm that the communication line is open and working."
}
[/block]