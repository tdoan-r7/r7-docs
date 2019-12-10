---
title: "Database credential requirements for scanning policies"
excerpt: ""
---
Credentials provide InsightVM with the necessary access to scan an asset. Several types of authentication are supported for policy scanning, including authentication for databases such as Microsoft SQL Server (MSSQL) and Oracle.

You add credentials for databases the same way you create [shared credentials for authenticated scans](doc:managing-shared-scan-credentials). You'll need to add two sets of credentials: one for the database itself and one for the asset. For example, if you have Oracle installed on a Linux machine, you'll need to provide the credentials to log in to the Linux machine as well as credentials for the database. If you are scanning a SQL server, you'll need to specify the CIFS/SMB credentials that are needed to connect to the Windows asset.

# Requirements for MSSQL credentials

For MSSQL databases, if you aren't using Windows authentication, the following information is required:

* **Service** - The service identifies the type of database you want to add credentials for. In this case, you need to set this option to "Microsoft SQL Server."
* **Database** - This is the name of the database you're using. The default database is "master."
* **User name** - This is the user name for the account that will be used for authenticating to the database. You can use the sa account, which is the SQL Server system administrator account and has the necessary privileges for authenticating to the service and querying information.
* **Password** - This is the password for the account that will be used for authenticating to the database.

If you are using Windows authentication, you'll need to provide the following information:

* **Service** - The service identifies the type of database you want to add credentials for. In this case, you need to set this option to "Microsoft SQL Server."
* **Database** - This is the name of the database you're using. The default database is "master."
* **Domain** - If you are using Windows authentication, you'll need to choose the **Use Windows Auth** option and provide the name of the Windows domain.
* **User name** - This is the user name for the account that will be used for authenticating to the database. You can use the "sa" account, which is the SQL Server system administrator account and has the necessary privileges for authenticating to the service and querying information. If you choose not to use the "sa" account, the account that you use the CONNECT right granted to it.
* **Password** - This is the password for the account that will be used for authenticating to the database.

# Requirements for Oracle credentials

For Oracle databases, the following information is required for authentication:

* **Service** - The service identifies the type of database you want to add credentials for. In this case, you need to set this option to "Oracle."
* **SID** - The SID represents the unique name for the database. The default SID is "orcl." If your Oracle environment has been set up to use multiple SIDs, choose the Oracle Net Listener Password option and enter your listener password to enumerate SIDs from your environment. For more information on configuring your Oracle Net Listener password, see [Oracle’s help documentation](https://docs.oracle.com/cd/E11882_01/network.112/e41945/listenercfg.htm#NETAG010).
   * If you want the scan to enumerate all the SIDS found, you need to specify the SIDs. Use the root credentials provided for the scan instead of the listener password for SID enumeration. The Oracle Listener password on Oracle 12c is not supported.
* **User name** - The user name for the account that will be used for authenticating to the database. You can use the `sys as sysdba` account, which is a default admin account that is created during installation.
* **Password** - The password for the account that will be used for authenticating to the database.
* **Permissions** - InsightVM requires access to the following tables:

```
DBA_USERS_WITH_DEFPWD, ALL_USERS, V$PARAMETER, DBA_PROFILES, DBA_USERS, DBA_TAB_PRIVS, DBA_SYS_PRIVS, DBA_ROLE_PRIVS, ALL_TABLES, DBA_PROXIES, DBA_STMT_AUDIT_OPTS, DBA_PRIV_AUDIT_OPTS, DBA_OBJ_AUDIT_OPTS, V$INSTANCE
```
[block:callout]
{
  "type": "info",
  "title": "NOTE",
  "body": "InsightVM requires access to the `sys.registry$history` table in order to determine the patch level of the database. If you’re scanning Oracle DB 12.1.0.2 or newer versions, the scanner needs access to the `sys.dba_registry_sqlpatch` table instead of `sys.registry$history`."
}
[/block]
# Creating a user account with limited access

While InsightVM will scan your database when configured to log in as a highly privileged role such as "sysdba," it is not recommended. You can create a user with more limited access by running the following commands:

```
CREATE USER nxpscan IDENTIFIED BY aStrongerPasswordThanThis;
GRANT create session TO nxpscan;
GRANT select ON sys.registry$history TO nxpscan;
```

After you create this account, you can configure a site to use your new Oracle credentials.

# Policy scanning for DB2 and Sybase

Policy scanning for DB2 and Sybase is currently not available.