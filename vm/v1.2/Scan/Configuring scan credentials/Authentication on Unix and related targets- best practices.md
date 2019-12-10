---
title: "Authentication on Unix and related targets: best practices"
excerpt: ""
---
For scanning Unix and related systems such as Linux, it is possible to scan most vulnerabilities without root access. You will need root access for a few vulnerability checks, and for many policy checks. If you plan to scan with a non-root user, you need to make sure the account has specified permissions, and be aware that the non-root user will not find certain checks.The following sections contain guidelines for what to configure and what can only be found with root access. Due to the complexity of the checks and the fact they are updated frequently, this list is subject to change.

To ensure near-comprehensive vulnerability coverage when scanning as a non-root user, you need to either:

* Elevate permissions so that you can run commands as root without using an actual root account.

OR

* Configure your systems such that your non-root scanning user has permissions on specified commands and directories.

The following sections describe the configuration for these options.

### Configuring your scan environment to support permission elevation

One way to elevate scan permissions without using a root user or performing a custom configuration is to use permission elevation, such as sudo or pbrun. These options require specific configuration (for instance, for pbrun, you need to whitelist the user's shell), but do not require you to customize permissions as described in _Commands the application runs_ below. 

### Commands the application runs

The following section contains guidelines for what commands the application runs when scanning. The vast majority of these commands can be run without root. As indicated above, this list is subject to change as new checks are added.

The majority of the commands are required for one of the following:

* getting the version of the operating system
* getting the versions of installed software packages
* running policy checks implemented as shell scripts
[block:callout]
{
  "type": "info",
  "body": "The application expects that the commands are part of the $PATH variable and there are no non-standard $PATH collisions."
}
[/block]
The following commands are required for all Unix/Linux distributions:
* ifconfig
* java
* sha1
* sha1sum
* md5
* md5sum
* awk
* grep
* egrep
* cut
* id
* ls

InsightVM will attempt to scan certain files, and will be able to perform the corresponding checks if the user account has the appropriate access to those files. The following is a list of files or directories that the account needs to be able to access:
* /etc/group
* /etc/passwd
* grub.conf
* menu.lst
* lilo.conf
* syslog.conf
* /etc/permissions
* /etc/securetty
* /var/log/postgresql
* /etc/hosts.equiv
* .netrc
* '/', '/dev', '/sys', and '/proc' "/home" "/var" "/etc"
* /etc/master.passwd
* sshd_config

For Linux, the application needs to read the following files, if present, to determine the distribution:
* /etc/debian_release
* /etc/debian_version
* /etc/redhat-release
* /etc/redhat_version
* /etc/os-release
* /etc/SuSE-release
* /etc/fedora-release
* /etc/slackware-release
* /etc/slackware-version
* /etc/system-release
* /etc/mandrake-release
* /etc/yellowdog-release
* /etc/gentoo-release
* /etc/UnitedLinux-release
* /etc/vmware-release
* /etc/slp.reg
* /etc/oracle-release

On any Unix or related variants (such as Ubuntu or OS X), there are specific commands the account needs to be able to perform in order to run specific checks. These commands should be whitelisted for the account.

The account needs to be able to perform the following commands for certain checks:
* cat
* find
* mysqlaccess
* mysqlhotcopy
* sh
* sysctl
* dmidecode
* perlsuid
* apt-get
* rpm

For the following types of distributions, the account needs execute permissions as indicated.

**AIX:**
[block:callout]
{
  "type": "info",
  "body": "Root privileges are required in order to correctly run without false positive vulnerabilities being reported."
}
[/block]
* lslpp –cL to list packages
* oslevel
* emgr -l

**Blue Coat:**
* show version

**Cisco:**
Required for vulnerability scanning:
* show version (**Note:** this is used on multiple Cisco platforms, including IOS, PIX, ASA, and IOR-XR)

Required for policy scanning:
* show running-config all
* show line
* show snmp community
* show snmp group
* show snmp user
* show clock
* show ip ssh
* show ip interface
* show cdp
* show tech-support password

**Debian-based distributions (e.g. Ubuntu):**
* uname
* dpkg
* egrep
* cut
* xargs

**F5:**
* either "version", "show", or "tmsh show sys version"

**FreeBSD:**
* freebsd-version is needed to fingerprint FreeBSD versions 10 and later
* The user account needs permissions to execute cat /var/db/freebsd-update/tag on FreeBSD version earlier than 10.
* FreeBSD package fingerprinting requires:
   * pkg info
   * pkg_info

**Juniper:**
* uname
* show version

**Mac OS X:**
* /usr/sbin/softwareupdate
* /usr/sbin/system_profiler
* sw_vers

**Palo Alto Networks PAN-OS:**
* show system info

**RPM-based distributions (e.g. Red Hat, SUSE, or Oracle):**
* uname
* rpm
* chkconfig

**Solaris:**
* showrev
* pkginfo
* ndd

**VMware ESX/ESXi:**
* vmware -v
* rpm
* esxupdate -a query || esxupdate query

##Vulnerability Checks that require RootExecutionService

For certain vulnerability checks, root access is required. If you choose to scan with a non-root user, be aware that these vulnerabilities will not be found, even if they exist on your system.The following is a list of checks that require root access:
[block:callout]
{
  "type": "info",
  "body": "You can search for the Vulnerability ID in the search bar of the Security Console to find the description and other details."
}
[/block]

[block:parameters]
{
  "data": {
    "h-0": "Vulnerability Title",
    "h-1": "Vulnerability ID",
    "0-0": "Solaris Serial Login Prompts",
    "0-1": "solaris-serial-login-prompts",
    "1-0": "Solaris Loose Destination Multihoming",
    "1-1": "solaris-loose-dst-multihoming",
    "2-0": "Solaris Forward Source Routing Enabled",
    "2-1": "solaris-forward-source-route",
    "3-1": "solaris-echo-multicast-reply",
    "3-0": "Solaris Echo Multicast Reply Enabled",
    "4-0": "Solaris ICMP Redirect Errors Accepted",
    "4-1": "solaris-redirects-accepted",
    "5-0": "Solaris Reverse Source Routing Enabled",
    "5-1": "solaris-reverse-source-route",
    "6-1": "solaris-forward-directed-broadcasts",
    "6-0": "Solaris Forward Directed Broadcasts Enabled",
    "7-1": "solaris-timestamp-broadcast-reply",
    "7-0": "Solaris Timestamp Broadcast Reply Enabled",
    "8-0": "Solaris Echo Broadcast Reply Enabled",
    "8-1": "solaris-echo-broadcast-reply",
    "9-0": "Solaris Empty Passwords",
    "9-1": "solaris-empty-passwords",
    "10-1": "unix-check-openssh-ssh-version-two*",
    "10-0": "OpenSSH config allows SSHv1 protocol*",
    "11-1": "unix-rhosts-file",
    "11-0": ".rhosts files exist",
    "12-0": ".netrc files exist",
    "12-1": "unix-netrc-files",
    "13-0": "MySQL mysqlhotcopy Temporary File Symlink Attack",
    "13-1": "unix-mysql-mysqlhotcopy-temp-file",
    "14-1": "unix-partition-mounting-weakness",
    "14-0": "Partition Mounting Weakness"
  },
  "cols": 2,
  "rows": 15
}
[/block]
* _OpenSSH config allows SSHv1 protocol/unix-check-openssh-ssh-version-two_ is conceptually the same as another check, _SSH server supports SSH protocol v1 clients/ssh-v1-supported_, which does not require root.