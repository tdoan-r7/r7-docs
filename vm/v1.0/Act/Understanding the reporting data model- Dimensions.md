---
title: "Understanding the reporting data model: Dimensions"
excerpt: ""
---
[block:callout]
{
  "type": "info",
  "body": "Data model 2.0.0 exposes information about linking assets across sites. All previous information is still available, and in the same format. As of data model 2.0.0, there is a _sites_ column in the dim_asset dimension that lists the sites to which an asset belongs."
}
[/block]
##Junk Scope Dimensions

The following dimensions are provided to allow the report designer access to the specific configuration parameters related to the scope of the report, including vulnerability filters.

##dim_pci_note

> _added in version 1.3.2_

**Description:** Dimension for the text descriptions of PCI special notes.

**Type:** junk

###Columns
[block:parameters]
{
  "data": {
    "h-0": "Column",
    "h-1": "Data Type",
    "h-2": "Nullable",
    "h-3": "Description",
    "h-4": "Associated Dimension",
    "0-0": "pci_note_id",
    "0-1": "integer",
    "0-2": "No",
    "0-3": "The code that represents the PCI note description",
    "1-0": "pci_note_text",
    "1-1": "text",
    "1-2": "No",
    "1-3": "The text detailing the PCI special note."
  },
  "cols": 5,
  "rows": 2
}
[/block]
##dim_scope_asset

**Description:** Provides access to the assets specifically configured within the configuration of the report. This dimension will contain a record for each asset selected within the report configuration.

**Type:** junk

###Columns
[block:parameters]
{
  "data": {
    "h-1": "Data Type",
    "h-0": "Column",
    "h-2": "Nullable",
    "h-3": "Description",
    "h-4": "Associated Dimension",
    "0-0": "asset_id",
    "0-1": "bigint",
    "0-2": "No",
    "0-3": "The identifier of the asset."
  },
  "cols": 5,
  "rows": 1
}
[/block]
##dim_scope_asset_group

**Description:** Provides access to the asset groups specifically configured within the configuration of the report. This dimension will contain a record for each asset group selected within the report configuration.

**Type:** junk

###Columns
[block:parameters]
{
  "data": {
    "h-0": "Column",
    "h-1": "Data Type",
    "h-2": "Nullable",
    "h-3": "Description",
    "h-4": "Associated Dimension",
    "0-0": "asset_group_id",
    "0-1": "bigint",
    "0-2": "No",
    "0-3": "The identifier of the asset group.",
    "0-4": "dim_asset_group"
  },
  "cols": 5,
  "rows": 1
}
[/block]
##dim_scope_filter_vulnerability_category_include

**Description:** Provides access to the names of the vulnerability categories that are configured to be included within the scope of the report. One record will be present for every category that is included. If no vulnerability categories are enabled for inclusion, this dimension table will be empty.

**Type:** junk

###Columns
[block:parameters]
{
  "data": {
    "h-0": "Column",
    "h-1": "Data Type",
    "h-2": "Nullable",
    "h-3": "Description",
    "h-4": "Associated Dimension",
    "0-0": "name",
    "0-1": "text",
    "0-2": "No",
    "0-3": "The name of the vulnerability category.",
    "0-4": "dim_vulnerability_category"
  },
  "cols": 5,
  "rows": 1
}
[/block]
##dim_scope_filter_vulnerability_severity

**Description:** Provides access to the severity filter enabled within the report configuration. The severity filter is exposed as the maximum severity score a vulnerability can have to be included within the scope of the report. This dimension is guaranteed to only have one record. If no severity filter is explicitly enabled, the minimum severity value will be 0.

**Type:** junk

###Columns
[block:parameters]
{
  "data": {
    "h-0": "Column",
    "h-1": "Data Type",
    "h-2": "Nullable",
    "h-3": "Description",
    "h-4": "Associated Dimension",
    "0-0": "min_severity",
    "0-1": "numeric(2)",
    "0-2": "No",
    "0-3": "The minimum severity that a vulnerability must have to be included in the scope of the report. If no filter is applied to severity, defaults to 0.",
    "0-4": "dim_vulnerability_category",
    "1-0": "severity_description",
    "1-1": "text",
    "1-2": "No",
    "1-3": "A human-readable description of the severity filter that is enabled.",
    "1-4": ""
  },
  "cols": 5,
  "rows": 2
}
[/block]
##dim_scope_filter_vulnerability_status

**Description:** Provides access to the vulnerability status filters enabled within the configuration of the report. A record will be present for every status filter that is enabled, and is guaranteed to have between a minimum one and maximum three statuses enabled.

**Type:** junk

###Columns
[block:parameters]
{
  "data": {
    "h-0": "Column",
    "h-1": "Data Type",
    "h-2": "Nullable",
    "h-3": "Description",
    "h-4": "Associated Dimension",
    "0-0": "status_id",
    "0-1": "character(1)",
    "0-2": "No",
    "0-3": "The identifier of the vulnerability status.",
    "0-4": "dim_vulnerability_status"
  },
  "cols": 5,
  "rows": 1
}
[/block]
##dim_scope_policy

> _added in version 1.3.0_

**Description:** This is the dimension for all policies within the scope of the report. It contains one record for every policy defined in the report scope. If none has been defined, it contains one record for every policy that has been scanned with at least one asset in the scope of the report.

**Type:** slowly changing (Type I)

###Columns
[block:parameters]
{
  "data": {
    "h-2": "Nullable",
    "h-0": "Column",
    "h-1": "Data Type",
    "h-3": "Description",
    "0-0": "policy_id",
    "0-1": "bigint",
    "0-2": "No",
    "0-3": "The identifier of the policy.",
    "1-0": "scope",
    "1-1": "text",
    "1-2": "No",
    "1-3": "The identifier for scope of policy. Policies that are automatically available have \"Built-in\" scope, whereas policies created by users have scope as \"Custom\"."
  },
  "cols": 4,
  "rows": 2
}
[/block]
##dim_scope_scan

**Description:** Provides access to the scans specifically configured within the configuration of the report. This dimension will contain a record for each scan selected within the report configuration.

**Type:** junk

###Columns
[block:parameters]
{
  "data": {
    "h-0": "Column",
    "h-1": "Data Type",
    "h-2": "Nullable",
    "h-3": "Description",
    "h-4": "Associated Dimension",
    "0-0": "scan_id",
    "0-1": "bigint",
    "0-2": "No",
    "0-3": "The identifier of the asset scan.",
    "0-4": "dim_scan"
  },
  "cols": 5,
  "rows": 1
}
[/block]
##dim_scope_site

**Description:** Provides access to the sites specifically configured within the configuration of the report. This dimension will contain a record for each site selected within the report configuration.

**Type:** junk

###Columns
[block:parameters]
{
  "data": {
    "h-0": "Column",
    "h-1": "Data Type",
    "h-2": "Nullable",
    "h-3": "Description",
    "h-4": "Associated Dimension",
    "0-0": "site_id",
    "0-1": "integer",
    "0-2": "No",
    "0-3": "The identifier of the site.",
    "0-4": "dim_site"
  },
  "cols": 5,
  "rows": 1
}
[/block]
#Core Entity Dimensions

##dim_asset

**Description:** Dimension that provides access to the textual information of all assets configured to be within the scope of the report. Only the information from the most recent scan of each asset is used to provide an accumulating summary. There will be one record in this dimension for every single asset in scope, including assets specified through configuring scans, sites, or asset groups to be within scope.

**Type:** slowly changing (Type I)

###Columns
[block:parameters]
{
  "data": {
    "h-0": "Column",
    "h-1": "Data Type",
    "h-2": "Nullable",
    "h-3": "Description",
    "h-4": "Associated Dimension",
    "0-0": "asset_id",
    "0-1": "bigint",
    "0-2": "No",
    "0-3": "The identifier of the asset.",
    "1-0": "mac_address",
    "1-1": "macaddr",
    "1-2": "Yes",
    "1-3": "The primary MAC address of the asset. If an asset has had no MAC address identified, the value will be _null_. If an asset has multiple MAC addresses, the primary or best address is selected.",
    "2-0": "ip_address",
    "2-1": "inet",
    "2-2": "No",
    "2-3": "The primary IP address of the asset. If an asset has multiple IP addresses, the primary or best address is selected. The IP address may be an IPv4 or IPv6 address.",
    "3-0": "host_name",
    "3-1": "text",
    "3-2": "Yes",
    "3-3": "The primary host name of the asset. If an asset has had no host name identified, the value will be null . If an asset has multiple host names, the primary or best address is selected. If the asset was scanned as a result of configuring the site with a host name target, that name will be guaranteed to be selected ss the primary host name.",
    "4-0": "operating_system_id",
    "4-1": "bigint",
    "4-2": "No",
    "4-3": "The identifier of the operating system fingerprint with the highest certainty on the asset. If the asset has no operating system fingerprinted, the value will be -1.",
    "4-4": "dim_operating_system",
    "5-0": "host_type_id",
    "5-1": "integer",
    "5-2": "No",
    "5-3": "The identifier of the type of host the asset is classified as. If the host type could not be detected, the value will be -1.",
    "5-4": "dim_host_type",
    "6-0": "sites",
    "6-1": "string",
    "6-2": "No",
    "6-3": "Comma separated list of site names.\n> _Added in version 2.0.0_",
    "7-0": "last_assessed_for_vulnerabilities",
    "7-1": "timestamp without time zone",
    "7-2": "Yes",
    "7-3": "The time at which the asset was last scanned for vulnerabilities. If the asset has never been scanned for vulnerabilities, the value will be null.\n> _Added in version 2.2.0_"
  },
  "cols": 5,
  "rows": 8
}
[/block]
##dim_asset_file

> _added in version 1.2.0_

**Description:** Dimension for files and directories that have been enumerated on an asset. Each record represents one file or directory discovered on an asset. If an asset has no files or groups enumerated, there will be no records in this dimension for the asset.

**Type:** slowly changing (Type I)

###Columns
[block:parameters]
{
  "data": {
    "h-0": "Column",
    "h-1": "Data Type",
    "h-2": "Nullable",
    "h-3": "Description",
    "h-4": "Associated Dimension",
    "0-0": "asset_id",
    "0-1": "bigint",
    "0-2": "No",
    "0-3": "The identifier of the asset.",
    "0-4": "dim_asset",
    "1-0": "file_id",
    "1-1": "bigint",
    "1-2": "No",
    "1-3": "The identifier of the file or directory.",
    "2-0": "type",
    "2-1": "text",
    "2-2": "No",
    "2-3": "The type of the item: Directory, File, or Unknown.",
    "3-0": "name",
    "3-1": "text",
    "3-2": "No",
    "3-3": "The name of the file or directory.",
    "4-0": "size",
    "4-1": "bigint",
    "4-2": "No",
    "4-3": "The size of the file or directory in bytes. If the size is unknown, the value will be -1."
  },
  "cols": 5,
  "rows": 5
}
[/block]
##dim_asset_group_account

**Description:** Dimension that provides the group accounts detected on an asset during the most recent scan of the asset. 

**Type:** slowly changing (Type I)

###Columns
[block:parameters]
{
  "data": {
    "h-0": "Column",
    "h-1": "Data Type",
    "h-2": "Nullable",
    "h-3": "Description",
    "h-4": "Associated Dimension",
    "0-0": "asset_id",
    "0-1": "bigint",
    "0-2": "No",
    "0-3": "The identifier of the asset",
    "0-4": "dim_asset",
    "1-0": "name",
    "1-1": "text",
    "1-2": "No",
    "1-3": "The name of the group detected."
  },
  "cols": 5,
  "rows": 2
}
[/block]
##dim_asset_group

**Description:** Dimension that provides access to the asset groups within the scope of the report. There will be one record in this dimension for every asset group which any asset in the scope of the report is associated to, including assets specified through configuring scans, sites, or asset groups.

**Type:** slowly changing (Type I)

###Columns
[block:parameters]
{
  "data": {
    "h-0": "Column",
    "h-1": "Data Type",
    "h-2": "Nullable",
    "h-3": "Description",
    "h-4": "Associated Dimension",
    "0-0": "asset_group_id",
    "0-1": "integer",
    "0-2": "No",
    "0-3": "The identifier of the asset group",
    "1-0": "name",
    "1-1": "text",
    "1-2": "No",
    "1-3": "The name of the asset group.",
    "2-0": "description",
    "2-1": "text",
    "2-2": "Yes",
    "2-3": "The optional description of the asset group. If no description is specified, the value will be _null_.",
    "3-0": "dynamic_membership",
    "3-1": "boolean",
    "3-2": "No",
    "3-3": "Indicates whether the membership of the asset group is computed dynamically using a dynamic asset filter, or is static (true if this group is a dynamic asset group)."
  },
  "cols": 5,
  "rows": 4
}
[/block]
##dim_asset_group_asset

**Description:** Dimension that provides access to the relationship between an asset group and its associated assets. For each asset group membership of an asset there will be a record in this table.

**Type:** slowly changing (Type I)

###Columns
[block:parameters]
{
  "data": {
    "h-0": "Column",
    "h-1": "Data Type",
    "h-2": "Nullable",
    "h-3": "Description",
    "h-4": "Associated Dimension",
    "0-0": "asset_group_id",
    "0-1": "integer",
    "0-2": "No",
    "0-3": "The identifier of the asset group.",
    "0-4": "dim_asset_group",
    "1-0": "asset_id",
    "1-1": "bigint",
    "1-2": "No",
    "1-3": "The identifier of the asset that belongs to the asset group.",
    "1-4": "dim_asset"
  },
  "cols": 5,
  "rows": 2
}
[/block]
##dim_asset_host_name

**Description:** Dimension that provides all primary and alternate host names for an asset. Unlike the  dim_asset dimension, this dimension will provide detailed information for the alternate host names detected on the asset. If an asset has no known host names, a record with an unknown host name will be present in this dimension. 

**Type:** slowly changing (Type I)

###Columns
[block:parameters]
{
  "data": {
    "h-0": "Column",
    "h-1": "Data Type",
    "h-2": "Nullable",
    "h-3": "Description",
    "h-4": "Associated Dimension",
    "0-0": "asset_id",
    "0-1": "bigint",
    "0-2": "No",
    "0-3": "The identifier of the asset.",
    "0-4": "dim_asset",
    "1-0": "host_name",
    "1-1": "text",
    "1-2": "No",
    "1-3": "The host name associated to the asset, or 'Unknown' if no host name is associated with the asset.",
    "2-0": "source_type_id",
    "2-1": "character(1)",
    "2-2": "No",
    "2-3": "The identifier of the type of source which was used to detect the host name, or '-' if no host name is associated with the asset.",
    "2-4": "dim_host_name_source_type"
  },
  "cols": 5,
  "rows": 3
}
[/block]
##dim_asset_ip_address

**Description:** Dimension that provides all primary and alternate IP addresses for an asset. Unlike the dim_asset  dimension, this dimension will provide detailed information for the alternate IP addresses detected on the asset. As each asset is guaranteed to have at least one IP address, this dimension will contain at least one record for every asset in the scope of the report.

**Type:** slowly changing (Type I)

###Columns
[block:parameters]
{
  "data": {
    "h-0": "Column",
    "h-1": "Data Type",
    "h-2": "Nullable",
    "h-3": "Description",
    "h-4": "Associated Dimension",
    "0-0": "asset_id",
    "0-1": "bigint",
    "0-2": "No",
    "0-3": "The identifier of the asset.",
    "0-4": "dim_asset",
    "1-0": "ip_address",
    "1-1": "inet",
    "1-2": "No",
    "1-3": "The IP address associated to the asset.",
    "2-0": "type",
    "2-1": "text",
    "2-2": "No",
    "2-3": "A description of the type of the IP address, either of the values: “IPv6” or “IPv4”."
  },
  "cols": 5,
  "rows": 3
}
[/block]
##dim_asset_mac_address

**Description:** Dimension that provides all primary and alternate MAC addresses for an asset. Unlike the *dim_asset*  dimension, this dimension will provide detailed information for the alternate MAC addresses detected on the asset. If an asset has no known MAC addresses, a record with null MAC address will be present in this dimension. 

**Type:** slowly changing (Type I)

###Columns
[block:parameters]
{
  "data": {
    "h-0": "Column",
    "h-1": "Data Type",
    "h-2": "Nullable",
    "h-3": "Description",
    "h-4": "Associated Dimension",
    "0-0": "asset_id",
    "0-1": "bigint",
    "0-2": "No",
    "0-3": "The identifier of the asset the MAC address was detected on.",
    "0-4": "dim_asset",
    "1-0": "address",
    "1-1": "macaddr",
    "1-2": "Yes",
    "1-3": "The MAC address associated to the asset, or _null_ if the asset has no known MAC address."
  },
  "cols": 5,
  "rows": 2
}
[/block]
##dim_asset_operating_system

**Description:** Dimension that provides the primary and all alternate operating system fingerprints for an asset. Unlike the *dim_asset* dimension, this dimension will provide detailed information for all operating system fingerprints on an asset. If an asset has no known operating system, a record with an unknown operating system fingerprint will be present in this dimension. 

**Type:** slowly changing (Type I)

###Columns
[block:parameters]
{
  "data": {
    "h-0": "Column",
    "h-1": "Data Type",
    "h-2": "Nullable",
    "h-3": "Description",
    "h-4": "Associated Dimensions",
    "0-0": "asset_id",
    "0-1": "bigint",
    "0-2": "No",
    "0-3": "The identifier of the asset.",
    "0-4": "dim_asset",
    "1-0": "operating_system_id",
    "1-1": "bigint",
    "1-2": "No",
    "1-3": "The identifier of the operating system, or -1 if there is no known operating system.",
    "1-4": "dim_operating_system",
    "2-0": "fingerprint_source_id",
    "2-1": "integer",
    "2-2": "No",
    "2-3": "The source which was used to detect the operating system fingerprint, or -1 if there is no known operating system.",
    "2-4": "dim_fingerprint_source",
    "3-0": "certainty",
    "3-1": "real",
    "3-2": "No",
    "3-3": "A value between 0 and 1 indicating the confidence level of the fingerprint. The value is 0 if there no known operating system."
  },
  "cols": 5,
  "rows": 4
}
[/block]
 ##dim_asset_scan

**Description:** Dimension for the relationship between an asset and a scan, for all scans and assets within the scope of the report. A record will be present for each scan of each asset, with the time at which the scan started and completed on the asset.

**Type:** slowly changing (Type I)

###Columns
[block:parameters]
{
  "data": {
    "h-0": "Column",
    "h-1": "Data Type",
    "h-2": "Nullable",
    "h-3": "Description",
    "h-4": "Associated Dimension",
    "0-0": "scan_id",
    "0-1": "bigint",
    "0-2": "No",
    "0-3": "The unique identifier of the scan.",
    "0-4": "dim_scan",
    "1-0": "asset_id",
    "1-1": "bigint",
    "1-2": "No",
    "1-3": "The unique identifier of the asset.",
    "1-4": "dim_asset",
    "2-0": "scan_started",
    "2-1": "timestamp without time zone",
    "2-2": "No",
    "2-3": "The time at which the asset was first scanned in the scan. The timestamp is converted into the timezone specified within the report configuration.",
    "3-0": "scan_finished",
    "3-1": "timestamp without time zone",
    "3-2": "No",
    "3-3": "The time at which the asset completed scanning in each scan. The timestamp is converted into the timezone specified within the report configuration.",
    "4-0": "match_value",
    "4-1": "real",
    "4-2": "Yes",
    "4-3": "A value indicating the confidence with which this asset was correlated to an existing asset during a scan.”"
  },
  "cols": 5,
  "rows": 5
}
[/block]
##dim_asset_service

**Description:** Dimension that provides the services detected on an asset during the most recent scan of the asset. If an asset had no services enumerated during the scan, there will be no records in this dimension. 

**Type:** slowly changing (Type I)

###Columns
[block:parameters]
{
  "data": {
    "h-0": "Column",
    "h-1": "Data Type",
    "h-2": "Nullable",
    "h-3": "Description",
    "h-4": "Associated Dimension",
    "0-0": "asset_id",
    "0-1": "bigint",
    "0-2": "No",
    "0-3": "The identifier of the asset.",
    "0-4": "dim_asset",
    "1-0": "service_id",
    "1-1": "integer",
    "1-2": "No",
    "1-3": "The identifier of the service.",
    "1-4": "dim_service",
    "2-0": "protocol_id",
    "2-1": "smallint",
    "2-2": "No",
    "2-3": "The identifier of the protocol.",
    "2-4": "dim_protocol",
    "3-0": "port",
    "3-1": "integer",
    "3-2": "No",
    "3-3": "The port on which the service is running",
    "4-0": "service_fingerprint_id",
    "4-1": "bigint",
    "4-2": "No",
    "4-3": "The identifier of the fingerprint for the service, or -1 if a fingerprint is not available.",
    "4-4": "dim_service_fingerprint",
    "5-0": "certainty",
    "5-1": "real",
    "5-2": "No",
    "5-3": "The confidence level of the fingerprint, which ranges from 0 to 1.0. If there is no fingerprint, the value is 0."
  },
  "cols": 5,
  "rows": 6
}
[/block]
##dim_asset_service_configuration

> _added in version 1.2.1_

**Description:** Dimension that provides the most recent configurations that have been detected on the services of an asset during the latest scan of that asset. Each record represents a configuration value that has been detected on a service (e.g., banner and header values). If an asset has no services detected on it, there will be no records for the asset in the dimension.

**Type:** slowly changing (Type I)

###Columns
[block:parameters]
{
  "data": {
    "h-0": "Column",
    "h-1": "Data Type",
    "h-2": "Nullable",
    "h-3": "Description",
    "h-4": "Associated Dimension",
    "0-0": "asset_id",
    "0-1": "bigint",
    "0-2": "No",
    "0-3": "The identifier of the asset.",
    "0-4": "dim_asset",
    "1-0": "service_id",
    "1-1": "integer",
    "1-2": "No",
    "1-3": "The identifier of the service.",
    "1-4": "dim_service",
    "2-0": "name",
    "2-1": "text",
    "2-2": "No",
    "2-3": "The name of the configuration value.",
    "3-0": "value",
    "3-1": "text",
    "3-2": "Yes",
    "3-3": "The configuration value, which may be empty or null.",
    "4-0": "port",
    "4-1": "integer",
    "4-2": "No",
    "4-3": "The port on which the service was running."
  },
  "cols": 5,
  "rows": 5
}
[/block]
##dim_asset_service_credential

> _added in version 1.3.1_

**Description:** Dimension that presents the most recent credential statuses asserted for services on an asset in the latest scan.

**Type:** slowly changing

###Columns
[block:parameters]
{
  "data": {
    "h-0": "Column",
    "h-1": "Data Type",
    "h-2": "Nullable",
    "h-3": "Description",
    "h-4": "Associated Dimension",
    "0-0": "asset_id",
    "0-1": "bigint",
    "0-2": "No",
    "0-3": "The identifier of the asset.",
    "0-4": "dim_asset",
    "1-0": "service_id",
    "1-1": "integer",
    "1-2": "No",
    "1-3": "The identifier of the service.",
    "1-4": "dim_service",
    "2-0": "credential_status_id",
    "2-1": "smallint",
    "2-2": "No",
    "2-3": "The identifier of the credential status for the service credential.",
    "2-4": "dim_credential_status",
    "3-0": "protocol_id",
    "3-1": "smallint",
    "3-2": "No",
    "3-3": "The identifier of the protocol of the service.",
    "3-4": "dim_protocol",
    "4-0": "port",
    "4-1": "integer",
    "4-2": "No",
    "4-3": "The port on which the service is running."
  },
  "cols": 5,
  "rows": 5
}
[/block]
##dim_asset_software

**Description:** Dimension that provides the software enumerated on an asset during the most recent scan of the asset. If an asset had no software packages enumerated during the scan, there will be no records in this dimension. 

**Type:** slowly changing (Type I)

###Columns
[block:parameters]
{
  "data": {
    "h-0": "Column",
    "h-1": "Data Type",
    "h-2": "Nullable",
    "h-3": "Description",
    "h-4": "Associated Dimension",
    "0-0": "asset_id",
    "0-1": "bigint",
    "0-2": "No",
    "0-3": "The identifier of the asset",
    "0-4": "dim_asset.",
    "1-0": "software_id",
    "1-1": "bigint",
    "1-2": "No",
    "1-3": "The identifier of the software package",
    "1-4": "dim_software",
    "2-0": "fingerprint_source_id",
    "2-1": "integer",
    "2-2": "No",
    "2-3": "The source which was used to detect the software.",
    "2-4": "dim_fingerprint_source"
  },
  "cols": 5,
  "rows": 3
}
[/block]
##dim_asset_unique_id

> _added in version 2.1.0_

**Description:** Dimension for the most current unique identifiers of every asset. Each record represents a unique identifier enumerated on the asset. If an asset has no unique identifiers, a record will not be present in this dimension. An asset may have more than one unique identifier enumerated.

###Columns
[block:parameters]
{
  "data": {
    "h-0": "Column",
    "h-1": "Data Type",
    "h-2": "Nullable",
    "h-3": "Description",
    "h-4": "Associated Dimension",
    "0-0": "asset_id",
    "0-1": "bigint",
    "0-2": "No",
    "0-3": "The unique identifier of the the asset.",
    "0-4": "dim_asset",
    "1-0": "source",
    "1-1": "text",
    "1-2": "No",
    "1-3": "The source of the unique identifier, usually describing the mechanism used to acquire the unique ID.",
    "2-0": "unique_id",
    "2-1": "text",
    "2-2": "No",
    "2-3": "The unique identifier of the asset."
  },
  "cols": 5,
  "rows": 3
}
[/block]
##dim_asset_user_account

**Description:** Dimension that provides the user accounts detected on an asset during the most recent scan of the asset.

**Type:** slowly changing (Type I)

###Columns
[block:parameters]
{
  "data": {
    "h-0": "Column",
    "h-1": "Data Type",
    "h-2": "Nullable",
    "0-0": "asset_id",
    "h-3": "Description",
    "h-4": "Associated Dimension",
    "0-1": "bigint",
    "0-2": "No",
    "0-3": "The identifier of the asset.",
    "0-4": "dim_asset",
    "1-0": "name",
    "1-1": "text",
    "1-2": "Yes",
    "1-3": "The short, abbreviated name of the user account, which may be _null_.",
    "2-0": "full_name",
    "2-1": "text",
    "2-2": "Yes",
    "2-3": "The longer full name of the user account, which may be null."
  },
  "cols": 5,
  "rows": 3
}
[/block]
##dim_asset_vulnerability_solution

> _added in version 1.1.0_

**Description:** Dimension that provides access to what solutions can be used to remediate a vulnerability on an asset. Multiple solutions may be selected as the means to remediate a vulnerability on an asset. This occurs when multiple solutions can be chosen from to remediate a vulnerability. The solutions provided represent only the direct solutions associated with the vulnerability. To view the single best rollup recommended solution, use *dim_asset_vulnerability_best_solution* instead.

**Type:** slowly changing (Type I)

###Columns
[block:parameters]
{
  "data": {
    "h-0": "Column",
    "h-1": "Data Type",
    "h-2": "Nullable",
    "h-3": "Description",
    "h-4": "Associated Dimension",
    "0-0": "asset_id",
    "0-1": "bigint",
    "0-2": "No",
    "0-3": "The surrogate identifier of the asset.",
    "0-4": "dim_asset",
    "1-0": "vulnerability_id",
    "1-1": "integer",
    "1-2": "No",
    "1-3": "The identifier of the vulnerability.",
    "1-4": "dim_vulnerability",
    "2-0": "solution_id",
    "2-1": "integer",
    "2-2": "No",
    "2-3": "The surrogate identifier of the solution that may be used to remediate the vulnerability on the asset.",
    "2-4": "dim_solution"
  },
  "cols": 5,
  "rows": 3
}
[/block]
##dim_asset_vulnerability_best_solution

> _added in version 2.2.0_

**Description:** Dimension that provides access to the best solution that is recommended to remediate a vulnerability on an asset.

**Type:** slowly changing (Type I)

###Columns
[block:parameters]
{
  "data": {
    "h-0": "Column",
    "h-1": "Data Type",
    "h-2": "Nullable",
    "h-3": "Description",
    "h-4": "Associated Dimension",
    "0-0": "asset_id",
    "0-1": "bigint",
    "0-2": "No",
    "0-3": "The surrogate identifier of the asset.",
    "0-4": "dim_asset",
    "1-0": "vulnerability_id",
    "1-1": "integer",
    "1-2": "No",
    "1-3": "The identifier of the vulnerability.",
    "1-4": "dim_vulnerability",
    "2-0": "solution_id",
    "2-1": "integer",
    "2-2": "No",
    "2-3": "The surrogate identifier of the solution that may be used to remediate the vulnerability on the asset.",
    "2-4": "dim_solution"
  },
  "cols": 5,
  "rows": 3
}
[/block]
##dim_fingerprint_source

**Description:** Dimension that provides access to the means by which an operating system or software package were detected on an asset.

**Type:** slowly changing (Type I) 

###Columns
[block:parameters]
{
  "data": {
    "h-0": "Column",
    "h-1": "Data Type",
    "h-2": "Nullable",
    "h-3": "Description",
    "h-4": "Associated Dimension",
    "0-0": "fingerprint_source_id",
    "0-1": "integer",
    "0-2": "No",
    "0-3": "The identifier of the source of a fingerprint.",
    "1-0": "source",
    "1-1": "text",
    "1-2": "No",
    "1-3": "The description of the source."
  },
  "cols": 5,
  "rows": 2
}
[/block]
##dim_mobile_asset_attribute

> _added in version 2.0.1_

**Description:** Dimension that provides information about mobile devices.

**Type:** slowly changing (Type I)

###Columns
[block:parameters]
{
  "data": {
    "h-0": "Column",
    "h-1": "Data Type",
    "h-2": "Nullable",
    "h-3": "Description",
    "h-4": "Associated Dimension",
    "0-0": "asset_id",
    "0-1": "bigint",
    "0-2": "No",
    "0-3": "The identifier of the asset.",
    "0-4": "dim_asset",
    "1-0": "attribute_name",
    "1-1": "text",
    "1-2": "No",
    "1-3": "The host name associated to the asset, or 'Unknown' if no host name is associated with the asset. Possible names include:\n\n  * Mobile Device ID\n  * Mobile Device Useragent\n  * Mobile Device Owner\n  * Mobile Device Model\n  * Mobile Device OS ",
    "2-0": "attribute_value",
    "2-1": "text",
    "2-2": "Yes",
    "2-3": "The actual value for each of the attributes listed in the attribute_name column, such as the device model or operating system."
  },
  "cols": 5,
  "rows": 3
}
[/block]
##dim_operating_system

**Description:** Dimension provides access to all operating system fingerprints detected on assets in any scan of the assets within the scope of the report. 

**Type:** slowly changing (Type I)

###Columns
[block:parameters]
{
  "data": {
    "h-0": "Column",
    "h-1": "Data Type",
    "h-2": "Nullable",
    "h-3": "Description",
    "h-4": "Associated Dimension",
    "0-0": "operating_system_id",
    "0-1": "bigint",
    "0-2": "No",
    "0-3": "The identifier of the operating system.",
    "1-0": "asset_type",
    "1-1": "integer",
    "1-2": "No",
    "1-3": "The type of asset the operating system applies to, which categorizes the operating system fingerprint. This type can distinguish the purpose of the asset that the operating system applies to.",
    "2-0": "description",
    "2-1": "text",
    "2-2": "No",
    "2-3": "The verbose description of the operating system, which combines the family, vendor, name, and version.",
    "3-0": "vendor",
    "3-1": "text",
    "3-2": "No",
    "3-3": "The vendor or publisher of the operating system. If the vendor was not detected, the value will be 'Unknown'.",
    "4-0": "family",
    "4-1": "text",
    "4-2": "No",
    "4-3": "The family or product line of the operating system. If the family was not detected, the value will be 'Unknown'.",
    "5-0": "name",
    "5-1": "text",
    "5-2": "No",
    "5-3": "The name of the operating system. If the name was not detected, the value will be 'Unknown'.",
    "6-0": "version",
    "6-1": "text",
    "6-2": "No",
    "6-3": "The version of the operating system. If the version was not detected, the value will be 'Unknown'.",
    "7-0": "architecture",
    "7-1": "text",
    "7-2": "No",
    "7-3": "The architecture the operating system is built for. If the architecture was not detected, the value will be 'Unknown'.",
    "8-0": "system",
    "8-1": "text",
    "8-2": "No",
    "8-3": "The terse description of the operating system, which combines the vendor and family.",
    "9-0": "cpe",
    "9-1": "text",
    "9-2": "Yes",
    "9-3": "The Common Platform Enumeration (CPE) value that corresponds to the operating system."
  },
  "cols": 5,
  "rows": 10
}
[/block]
##dim_policy

**Description:** This is the dimension for all metadata related to a policy. It contains one record for every policy that currently exists in the application.

**Type:** slowly changing (Type I)

###Columns
[block:parameters]
{
  "data": {
    "h-0": "Column",
    "h-1": "Data Type",
    "h-2": "Nullable",
    "h-3": "Description",
    "0-0": "policy_id",
    "0-1": "bigint",
    "0-2": "No",
    "0-3": "The identifier of the policy.",
    "1-0": "scope",
    "1-1": "text",
    "1-2": "No",
    "1-3": "The identifier for scope of policy. Policies that are automatically available have \"Built-in\" scope, whereas policies created by users have scope as \"Custom\".",
    "2-0": "title",
    "2-1": "text",
    "2-2": "No",
    "2-3": "The title of the policy as visible to the user.",
    "3-0": "description",
    "3-1": "text",
    "3-3": "A description of the policy.",
    "4-0": "total_rules",
    "4-1": "bigint",
    "4-3": "The sum of all the rules within the policy.",
    "5-0": "benchmark_name",
    "5-1": "text",
    "5-3": "The name of the collection of policies sharing the same source data to which the policy belongs. It includes metadata such as title, name, and applicable systems.",
    "6-0": "benchmark_version",
    "6-1": "text",
    "6-3": "The version number of the benchmark that includes the policy.",
    "7-0": "category",
    "7-1": "text",
    "7-3": "A grouping of similar benchmarks based on their source, purpose, or other criteria. Examples include FDCC, USGCB, and CIS."
  },
  "cols": 4,
  "rows": 8
}
[/block]
##dim_policy_group

> _added in version 1.3.0_

**Description:** This is the dimension for all the metadata for each rule within a policy. It contains one record for every rule within each policy.

**Type:** slowly changing (Type I)

###Columns
[block:parameters]
{
  "data": {
    "h-0": "Column",
    "h-1": "Data Type",
    "h-2": "Nullable",
    "h-3": "Description",
    "0-0": "policy_id",
    "0-1": "bigint",
    "0-2": "No",
    "0-3": "The identifier of the policy.",
    "1-0": "parent_group_id",
    "1-1": "bigint",
    "1-2": "Yes",
    "1-3": "Te identifier of the group this group directly belongs to. If this group belongs directly to the policy, this will be null.",
    "2-0": "scope",
    "2-1": "text",
    "2-2": "No",
    "2-3": "The identifier for scope of policy. Policies that are automatically available have \"Built-in\" scope, whereas policies created by users have scope as \"Custom\".",
    "3-0": "group_id",
    "3-1": "bigint",
    "3-2": "No",
    "3-3": "The identifier of the group.",
    "4-0": "title",
    "4-1": "text",
    "4-2": "Yes",
    "4-3": "The title of the group that is visible to the user. It describes a logical grouping of the policy rules.",
    "5-0": "description",
    "5-1": "text",
    "5-2": "Yes",
    "5-3": "A description of the group.",
    "6-0": "sub_groups",
    "6-1": "integer",
    "6-2": "No",
    "6-3": "The number of all groups descending from a group.",
    "7-0": "rules",
    "7-1": "integer",
    "7-2": "No",
    "7-3": "The number of all rules directly or indirectly belonging to a group."
  },
  "cols": 4,
  "rows": 8
}
[/block]
##dim_policy_rule

> _updated in version 1.3.0_

**Description:** This is the dimension for all the metadata for each rule within a policy. It contains one record for every rule within each policy.

**Type:** slowly changing (Type I)

###Columns
[block:parameters]
{
  "data": {
    "h-0": "Column",
    "h-1": "Data Type",
    "h-2": "Nullable",
    "h-3": "Description",
    "0-0": "policy_id",
    "0-1": "bigint",
    "0-2": "No",
    "0-3": "The identifier of the policy.",
    "1-0": "parent_group_id",
    "1-1": "bigint",
    "1-2": "Yes",
    "2-0": "scope",
    "2-1": "text",
    "2-2": "No",
    "2-3": "The identifier of the group the rule directly belongs to. If the rule belongs directly to the policy this will be null.",
    "3-0": "rule_id",
    "3-1": "bigint",
    "3-2": "No",
    "3-3": "The identifier of the rule.",
    "4-0": "title",
    "4-1": "text",
    "4-3": "The title of the rule, for each policy, that is visible to the user. It describes a state or condition with which a tested asset should comply.",
    "5-0": "description",
    "5-1": "text",
    "5-3": "A description of the rule.",
    "6-0": "severity",
    "6-1": "text",
    "6-2": "Yes",
    "6-3": "The severity of the rule. A textual value that can be one of the following: \"low\", \"medium\", \"high\", or \"unknown\".",
    "7-0": "rationale",
    "7-1": "text",
    "7-2": "Yes",
    "7-3": "Descriptive text explaining why compliance is important to the security of the target platform.",
    "8-0": "remediation",
    "8-1": "text",
    "8-2": "Yes",
    "8-3": "Instructions for remediating the non-compliant rule. Also referred to as \"fixtext\" in the policy content."
  },
  "cols": 4,
  "rows": 9
}
[/block]
##dim_policy_rule_cce_platform_nist_control_mapping

> _added in version 2.0.2_

**Description:** This dimension provides all National Institute of Standards and Technology (NIST) Special Publication 800-53 controls mappings for each Common Configuration Enumeration (CCE) within a rule.

**Type:** slowly changing (Type I)

###Columns
[block:parameters]
{
  "data": {
    "h-0": "Column",
    "h-1": "Data Type",
    "h-2": "Nullable",
    "h-3": "Description",
    "h-4": "Associated Dimension",
    "0-0": "rule_id",
    "0-1": "bigint",
    "0-2": "No",
    "0-3": "The identifier of the policy rule.",
    "0-4": "dim_policy_rule",
    "1-0": "rule_scope",
    "1-1": "text",
    "1-2": "No",
    "1-3": "The identifier for scope of policy. Policies that are automatically available have \"Built-in\" scope, whereas policies created by users have scope as \"Custom\".",
    "1-4": "dim_policy_rule",
    "2-0": "cce_item_id",
    "2-1": "bigint",
    "2-2": "No",
    "2-3": "The identifier of the CCE item.",
    "3-0": "platform",
    "3-1": "text",
    "3-2": "No",
    "3-3": "The platform of the CCE.",
    "4-0": "control_name",
    "4-1": "text",
    "4-2": "No",
    "4-3": "The name of the control mapping.",
    "5-0": "description",
    "5-1": "text",
    "5-2": "No",
    "5-3": "The published date of the control mapping.",
    "5-4": ""
  },
  "cols": 5,
  "rows": 6
}
[/block]
##dim_policy_override

> _added in version 1.3.0_

**Description:** Dimension that provides access to all policy rule overrides in any state that may apply to any assets within the scope of the report. This includes overrides that have expired or have been superceded by newer overrides.

**Type:** slowly changing (Type II)

###Columns
[block:parameters]
{
  "data": {
    "h-0": "Column",
    "h-1": "Data Type",
    "h-2": "Nullable",
    "h-3": "Description",
    "0-0": "override_id",
    "0-1": "bigint",
    "0-2": "No",
    "0-3": "The identifier of the policy rule override.",
    "1-0": "scope_id",
    "1-1": "character(1)",
    "1-2": "No",
    "1-3": "The identifier for scope of the override.",
    "2-0": "submitted_by",
    "2-1": "text",
    "2-2": "No",
    "2-3": "The login name of the user that submitted the policy override.",
    "3-0": "submitted_time",
    "3-1": "timestamp without time zone",
    "3-2": "No",
    "3-3": "The date the override was originally created and submitted.",
    "4-0": "comments",
    "4-1": "text",
    "4-2": "No",
    "4-3": "The description given at the time the policy override was submitted.",
    "5-0": "reviewed_by",
    "5-1": "text",
    "5-2": "Yes",
    "5-3": "The login name of the user that reviewed the policy override. If the override has been submitted and has not been reviewed, the value will be null.",
    "6-0": "review_comments",
    "6-1": "text",
    "6-2": "Yes",
    "6-3": "The comment that accompanies the latest review action. If the exception is submitted and has not been reviewed, the value will be null.",
    "7-0": "review_state_id",
    "7-1": "character(1)",
    "7-2": "No",
    "7-3": "The identifier of the review state of the override.",
    "8-0": "effective_time",
    "8-1": "timestamp without time zone",
    "8-2": "Yes",
    "8-3": "The date at which the rule override become effective. If the rule override is under review, the value will be null.",
    "9-0": "expiration_time",
    "9-1": "timestamp without time zone",
    "9-2": "Yes",
    "9-3": "The date at which the rule override will expire. If the exception has no expiration date set, the value is will be null.",
    "10-0": "new_status_id",
    "10-1": "character(1)",
    "10-2": "No",
    "10-3": "The identifier of the new value that this override applies to affected policy rule results."
  },
  "cols": 4,
  "rows": 11
}
[/block]
##dim_policy_override_scope

> _added in version 1.3.0_

**Description:** Dimension for the possible scope for a Policy override, such as _Global_, _Asset_, or _Asset Instance_.

**Type:** normal

###Columns
[block:parameters]
{
  "data": {
    "h-0": "Column",
    "h-1": "Data Type",
    "h-2": "Nullable",
    "h-3": "Description",
    "0-0": "scope_id",
    "0-1": "character(1)",
    "0-2": "No",
    "0-3": "The identifier of the policy rule override scope.",
    "1-0": "description",
    "1-1": "text",
    "1-2": "No",
    "1-3": "The description of the policy rule override scope."
  },
  "cols": 4,
  "rows": 2
}
[/block]
##dim_policy_override_review_state

> _added in version 1.3.0_

**Description:** Dimension for the possible states for a Policy override, such as _Submitted_, _Approved_, or _Rejected_.

**Type:** normal

###Columns
[block:parameters]
{
  "data": {
    "h-0": "Column",
    "h-1": "Data Type",
    "h-2": "Nullable",
    "h-3": "Description",
    "0-0": "state_id",
    "0-1": "character(1)",
    "0-2": "No",
    "0-3": "The identifier of the policy rule override state.",
    "1-0": "description",
    "1-1": "text",
    "1-2": "No",
    "1-3": "The description of the policy rule override state."
  },
  "cols": 4,
  "rows": 2
}
[/block]
##dim_policy_result_status

> _added in version 1.3.0_

**Description:** Dimension for the possible statuses for a Policy Check result, such as _Pass_, _Fail_, or _Not Applicable_.

**Type:** normal

###Columns
[block:parameters]
{
  "data": {
    "h-0": "Column",
    "h-1": "Data Type",
    "h-2": "Nullable",
    "h-3": "Description",
    "0-0": "status_id",
    "0-1": "character(1)",
    "0-2": "No",
    "0-3": "The identifier of the policy rule status.",
    "1-0": "description",
    "1-1": "text",
    "1-2": "No",
    "1-3": "The description of the policy rule status code."
  },
  "cols": 4,
  "rows": 2
}
[/block]
##dim_scan_engine

> _added in version 1.2.0_

**Description:** Dimension for all scan engines that are defined. A record is present for each scan engine to which the owner of the report has access.

**Type:** slowly changing (Type I)

###Columns
[block:parameters]
{
  "data": {
    "h-0": "Column",
    "h-1": "Data Type",
    "h-2": "Nullable",
    "h-3": "Description",
    "h-4": "Associated Dimension",
    "0-0": "scan_engine_id",
    "0-1": "integer",
    "0-2": "No",
    "0-3": "The unique identifier of the scan engine.",
    "1-0": "name",
    "1-1": "text",
    "1-2": "No",
    "1-3": "The name of the scan engine.",
    "2-0": "address",
    "2-1": "text",
    "2-2": "No",
    "2-3": "The address (either IP or host name) of the scan engine.",
    "3-0": "port",
    "3-1": "integer",
    "3-2": "No",
    "3-3": "The port the scan engine is running on."
  },
  "cols": 5,
  "rows": 4
}
[/block]
##dim_scan_template

> _added in version 1.2.0_

**Description:** Dimension for all scan templates that are defined. A record is present for each scan template in the system.

**Type:** slowly changing (Type I)

###Columns
[block:parameters]
{
  "data": {
    "h-0": "Column",
    "h-1": "Data Type",
    "h-2": "Nullable",
    "h-3": "Description",
    "h-4": "Associated Dimension",
    "0-0": "scan_template_id",
    "0-1": "text",
    "0-2": "No",
    "0-3": "The identifier of the scan template.",
    "1-0": "name",
    "1-1": "text",
    "1-2": "No",
    "1-3": "The short, human-readable name of the scan template.",
    "2-0": "description",
    "2-1": "text",
    "2-2": "No",
    "2-3": "The verbose description of the scan template."
  },
  "cols": 5,
  "rows": 3
}
[/block]
##dim_service

**Description:** Dimension that provides access to the name of a service detected on an asset in a scan. This dimension will contain a record for every service that was detected during any scan of any asset within the scope of the report.

**Type:** slowly changing (Type I)

###Columns
[block:parameters]
{
  "data": {
    "h-0": "Column",
    "h-1": "Data Type",
    "h-2": "Nullable",
    "0-3": "The identifier of the service.",
    "h-3": "Description",
    "h-4": "Associated Dimension",
    "0-0": "service_id",
    "0-1": "integer",
    "0-2": "No",
    "1-0": "name",
    "1-1": "text",
    "1-2": "No",
    "1-3": "The descriptive name of the service."
  },
  "cols": 5,
  "rows": 2
}
[/block]
 ##dim_service_fingerprint

**Description:** Dimension that provides access to the detailed information of a service fingerprint. This dimension will contain a record for every service fingerprinted during any scan of any asset within the scope of the report. 

**Type:** slowly changing (Type I)

###Columns
[block:parameters]
{
  "data": {
    "h-0": "Column",
    "h-1": "Data Type",
    "h-2": "Nullable",
    "h-3": "Description",
    "h-4": "Associated Dimension",
    "0-0": "service_fingerprint_id",
    "0-1": "bigint",
    "0-2": "No",
    "0-3": "The identifier of the service fingerprint.",
    "1-0": "vendor",
    "1-1": "text",
    "1-2": "No",
    "1-3": "The vendor name for the service. If the vendor was not detected, the value will be 'Unknown'.",
    "2-0": "family",
    "2-1": "text",
    "2-2": "No",
    "2-3": "The family name or product line of the service. If the family was not detected, the value will be 'Unknown'.",
    "3-0": "name",
    "3-1": "text",
    "3-2": "No",
    "3-3": "The name of the service. If the name was not detected, the value will be 'Unknown'.",
    "4-0": "version",
    "4-1": "text",
    "4-2": "No",
    "4-3": "The version name or number of the service. If the version was not detected, the value will be 'Unknown'."
  },
  "cols": 5,
  "rows": 5
}
[/block]
##dim_site

**Description:** Dimension that provides access to the textual information of all sites configured to be within the scope of the report. There will be one record in this dimension for every site which any asset in the scope of the report is associated to, including assets specified through configuring scans, sites, or asset groups.

**Type:** slowly changing (Type I)

###Columns
[block:parameters]
{
  "data": {
    "h-0": "Column",
    "h-1": "Data Type",
    "h-2": "Nullable",
    "h-3": "Description",
    "0-0": "site_id",
    "0-1": "integer",
    "0-2": "No",
    "0-3": "The identifier of the site.",
    "h-4": "Associated Dimension",
    "1-0": "name",
    "1-1": "text",
    "1-2": "No",
    "1-3": "The name of the site.",
    "2-0": "description",
    "2-1": "text",
    "2-2": "Yes",
    "2-3": "The optional description of the site. If the site has no description, the value will be null.",
    "3-0": "risk_factor",
    "3-1": "real",
    "3-2": "No",
    "3-3": "A numeric value that can be used to weight risk score computations. The default value is 1, but possible values from .33 to 3.0 to match the importance level.",
    "4-0": "importance",
    "4-1": "text",
    "4-2": "No",
    "4-3": "The importance of the site. The site importance is one of the following values: ‘Very Low’, ‘Low'’ 'Normal', ‘High’, or ‘Very High.’",
    "5-0": "dynamic_targets",
    "5-1": "boolean",
    "5-2": "No",
    "5-3": "Indicates whether the list of targets scanned by the site are dynamically configured (dynamic site).",
    "6-0": "organization_name",
    "6-1": "text",
    "6-2": "Yes",
    "6-3": "The optional name of the organization the site is associated to.",
    "7-0": "organization_url",
    "7-1": "text",
    "7-2": "Yes",
    "7-3": "The optional URL of the organization the site is associated to.",
    "8-0": "organization_contact",
    "8-1": "text",
    "8-2": "Yes",
    "8-3": "The optional contact name of the organization the site is associated to.",
    "9-0": "organization_job_title",
    "9-1": "text",
    "9-2": "Yes",
    "9-3": "The optional job title of the contact of the organization the site is associated to.",
    "10-0": "organization_email",
    "10-1": "text",
    "10-2": "Yes",
    "10-3": "The optional e-mail of the contact of the organization the site is associated to.",
    "11-0": "organization_phone",
    "11-1": "text",
    "11-2": "Yes",
    "11-3": "The optional phone number of the organization the site is associated to.",
    "12-0": "organization_address",
    "12-3": "The optional postal address of the organization the site is associated to.",
    "12-2": "Yes",
    "12-1": "text",
    "13-0": "organization_city",
    "13-1": "text",
    "13-2": "Yes",
    "13-3": "The optional city name of the organization the site is associated to.",
    "14-0": "organization_state",
    "14-1": "text",
    "14-2": "Yes",
    "14-3": "The optional state name of the organization the site is associated to.",
    "15-0": "organization_country",
    "15-1": "text",
    "15-2": "Yes",
    "15-3": "The optional country name of the organization the site is associated to.",
    "16-0": "organization_zip",
    "16-1": "text",
    "16-2": "Yes",
    "16-3": "The optional zip code of the organization the site is associated to.",
    "17-0": "last_scan_id",
    "17-1": "bigint",
    "17-2": "No",
    "17-3": "The identifier of the latest scan of the site that was run.",
    "17-4": "dim_scan"
  },
  "cols": 5,
  "rows": 18
}
[/block]
##dim_site_asset

**Description:** Dimension that provides access to the relationship between a site and its associated assets. For each asset within the scope of the report, a record will be present in this table that links to its associated site. The values in this dimension will change whenever a scan of a site is completed.

**Type:** slowly changing (Type II)

###Columns
[block:parameters]
{
  "data": {
    "h-0": "Column",
    "h-1": "Data Type",
    "h-2": "Nullable",
    "h-3": "Description",
    "h-4": "Associated Dimension",
    "0-0": "site_id",
    "0-1": "integer",
    "0-2": "No",
    "0-3": "The identifier of the site.",
    "0-4": "dim_site",
    "1-0": "asset_id",
    "1-1": "bigint",
    "1-2": "No",
    "1-3": "The identifier of the asset.",
    "1-4": "dim_asset"
  },
  "cols": 5,
  "rows": 2
}
[/block]
##dim_scan

**Description:** Dimension that provides access to the scans for any assets within the scope of the report.

**Type:** slowly changing (Type II)

###Columns
[block:parameters]
{
  "data": {
    "h-0": "Column",
    "h-1": "Data Type",
    "h-2": "Nullable",
    "h-3": "Description",
    "h-4": "Associated Dimension",
    "0-0": "scan_id",
    "0-1": "bigint",
    "0-2": "No",
    "0-3": "The identifier of the scan.",
    "1-0": "started",
    "1-1": "timestamp without time zone",
    "1-2": "No",
    "1-3": "The date and time at which the scan started.",
    "2-0": "finished",
    "2-1": "timestamp without time zone",
    "2-2": "Yes",
    "2-3": "The date and time at which the scan finished. If the scan did not complete normally, or is still in progress, this value will be null.",
    "3-0": "status_id",
    "3-1": "character(1)",
    "3-2": "No",
    "3-3": "The current status of the scan.",
    "3-4": "dim_scan_status",
    "4-0": "type_id",
    "4-1": "character(1)",
    "4-2": "No",
    "4-3": "The type of scan, which indicates whether the scan was started manually by a user or on a schedule.",
    "4-4": "dim_scan_type"
  },
  "cols": 5,
  "rows": 5
}
[/block]
##dim_site_scan

**Description:** Dimension that provides access to the relationship between a site and its associated scans. For each scan of a site within the scope of the report, a record will be present in this table.

**Type:** slowly changing (Type II)

###Columns
[block:parameters]
{
  "data": {
    "h-0": "Column",
    "h-1": "Data Type",
    "h-2": "Nullable",
    "h-3": "Description",
    "h-4": "Associated Dimension",
    "0-0": "site_id",
    "0-1": "integer",
    "0-2": "No",
    "0-3": "The identifier of the site.",
    "0-4": "dim_site",
    "1-0": "scan_id",
    "1-1": "bigint",
    "1-2": "No",
    "1-3": "The identifier of the scan.",
    "1-4": "dim_scan"
  },
  "cols": 5,
  "rows": 2
}
[/block]
##dim_site_scan_config

> _added in version 1.2.0_

**Description:** Dimension for the current scan configuration for a site.

**Type:** slowly changing (Type I)

###Columns
[block:parameters]
{
  "data": {
    "h-0": "Column",
    "h-1": "Data Type",
    "h-2": "Nullable",
    "0-3": "The unique identifier of the site.",
    "h-3": "Description",
    "h-4": "Associated Dimension",
    "0-0": "site_id",
    "0-1": "integer",
    "0-2": "No",
    "0-4": "dim_site",
    "1-0": "scan_template_id",
    "1-1": "text",
    "1-2": "No",
    "1-3": "The identifier of the currently configured scan template.",
    "1-4": "dim_scan_template",
    "2-0": "scan_engine_id",
    "2-1": "integer",
    "2-2": "No",
    "2-3": "The identifier of the currently configured scan engine.",
    "2-4": "dim_scan_engine"
  },
  "cols": 5,
  "rows": 3
}
[/block]
##dim_site_target

> _added in version 1.2.0_

**Description:** Dimension for all the included and excluded targets of a site. For all sites in the scope of the report, a record will be present for each unique IP range and/or host name defined as an included or excluded address in the site configuration. If any global exclusions are applied, these will also be provided at the site level.

**Type:** slowly changing (Type I)

###Columns
[block:parameters]
{
  "data": {
    "h-0": "Column",
    "h-1": "Data Type",
    "h-2": "Nullable",
    "0-3": "The identifier of the site.",
    "h-3": "Description",
    "h-4": "Associated Dimension",
    "0-0": "site_id",
    "0-1": "integer",
    "0-2": "No",
    "0-4": "dim_site",
    "1-0": "type",
    "1-1": "text",
    "1-2": "No",
    "1-3": "Either host or ip to indicate the type of address.",
    "2-0": "included",
    "2-1": "boolean",
    "2-2": "No",
    "2-3": "True if the target is included in the configuration, or false if it is excluded.",
    "3-0": "target",
    "3-1": "text",
    "3-2": "No",
    "3-3": "The address of the target. If _host_, this is the host name. If _ip_ type, this is the IP address in text form (result of running the HOST function).",
    "4-0": "scope",
    "4-1": "text",
    "4-2": "Yes",
    "4-3": "The scope of an exclusion: global if the exclusion is a global exclusion, site if the exclusion is defined on the site, or NULL if included (see above) is true."
  },
  "cols": 5,
  "rows": 5
}
[/block]
 ##dim_software

**Description:** Dimension that provides access to all the software packages that have been enumerated across all assets within the scope of the report. Each record has detailed information for the fingerprint of the software package.

**Type:** slowly changing (Type I)

###Columns
[block:parameters]
{
  "data": {
    "h-0": "Column",
    "h-1": "Data Type",
    "h-2": "Nullable",
    "h-3": "Description",
    "h-4": "Associated Dimension",
    "0-0": "software_id",
    "0-1": "bigint",
    "0-2": "No",
    "0-3": "The identifier of the software package.",
    "1-0": "vendor",
    "1-1": "text",
    "1-2": "No",
    "1-3": "The vendor that produced or published the software package.",
    "2-0": "family",
    "2-1": "text",
    "2-2": "No",
    "2-3": "The family or product line of the software package.",
    "3-0": "name",
    "3-1": "text",
    "3-2": "No",
    "3-3": "The name of the software.",
    "4-0": "version",
    "4-1": "text",
    "4-2": "No",
    "4-3": "The version of the software.",
    "5-0": "software_class_id",
    "5-1": "integer",
    "5-2": "No",
    "5-3": "The identifier of the class of software.",
    "5-4": "dim_software_class",
    "6-0": "cpe",
    "6-1": "text",
    "6-2": "Yes",
    "6-3": "The Common Platform Enumeration (CPE) value that corresponds to the software."
  },
  "cols": 5,
  "rows": 7
}
[/block]
 ##dim_software_class

**Description:** Dimension for the types of classes of software that can be used to classify or group the purpose of the software. 

**Type:** slowly changing (Type I)

###Columns
[block:parameters]
{
  "data": {
    "h-0": "Column",
    "h-1": "Data Type",
    "h-2": "Nullable",
    "h-3": "Description",
    "0-0": "software_class_id",
    "h-4": "Associated Dimension",
    "0-1": "integer",
    "0-2": "No",
    "0-3": "The identifier of the software class.",
    "1-0": "description",
    "1-1": "text",
    "1-2": "No",
    "1-3": "The description of the software class, which may be 'Unknown'."
  },
  "cols": 5,
  "rows": 2
}
[/block]
##dim_solution

> _added in version 1.1.0_

**Description:** Dimension that provides access to all solutions defined.

**Type:** slowly changing (Type I)

###Columns
[block:parameters]
{
  "data": {
    "h-0": "Column",
    "h-1": "Data Type",
    "h-2": "Nullable",
    "h-3": "Description",
    "h-4": "Associated Dimension",
    "0-0": "solution_id",
    "0-1": "integer",
    "0-2": "No",
    "0-3": "The identifier of the solution.",
    "1-0": "nexpose_id",
    "1-1": "text",
    "1-2": "No",
    "1-3": "The identifier of the solution within the application.",
    "2-0": "estimate",
    "2-1": "interval (0)",
    "2-2": "No",
    "2-3": "The amount of required time estimated to implement this solution on a single asset. The minimum value is 0 minutes, and the precision is measured in seconds.",
    "3-0": "url",
    "3-1": "text",
    "3-2": "Yes",
    "3-3": "An optional URL link defined for getting more information about the solution. When defined, this may be a web page defined by the vendor that provides more details on the solution, or it may be a download link to a patch.",
    "4-0": "solution_type",
    "4-1": "solution_type",
    "4-2": "No",
    "4-3": "Type of the solution, can be PATCH, ROLLUP or WORKAROUND. A patch type indicates that the solution involves applying a patch to a product or operating system. A rollup patch type indicates that the solution supercedes other vulnerabilities and rolls up many workaround or patch type solutions into one step.",
    "5-0": "fix",
    "5-1": "text",
    "5-2": "Yes",
    "5-3": "The steps that are a part of the fix this solution prescribes. The fix will usually contain a list of procedures that must be followed to remediate the vulnerability. The fix will be provided in an HTML format.",
    "6-0": "summary",
    "6-1": "text",
    "6-2": "No",
    "6-3": "A short summary of solution which describes the purpose of the solution at a high level and is suitable for use as a summarization of the solution.",
    "7-0": "additional_data",
    "7-1": "text",
    "7-2": "Yes",
    "7-3": "Additional information about the solution, in an HTML format.",
    "8-0": "applies_to",
    "8-1": "text",
    "8-2": "Yes",
    "8-3": "Textual representation of the types of system, software, and/or services that the solution can be applied to. If the solution is not restricted to a certain type of system, software or service, this field will be null."
  },
  "cols": 5,
  "rows": 9
}
[/block]
##dim_solution_supercedence

> _added in version 1.1.0_

**Description:** Dimension that provides all superceding associations between solutions. Unlike *dim_solution_highest_supercedence*, this dimension provides access to the entire graph of superceding relationships. If a solution does not supercede any other solution, it will not have any records in this dimension.

**Type:** slowly changing (Type I)

###Columns
[block:parameters]
{
  "data": {
    "h-0": "Column",
    "h-1": "Data Type",
    "h-2": "Nullable",
    "h-3": "Description",
    "h-4": "Associated Dimension",
    "0-0": "solution_id",
    "0-1": "integer",
    "0-2": "No",
    "0-3": "The identifier of the solution.",
    "0-4": "dim_solution",
    "1-0": "superceding_solution_id",
    "1-1": "integer",
    "1-2": "No",
    "1-4": "dim_solution",
    "1-3": "The identifier of the superceding solution."
  },
  "cols": 5,
  "rows": 2
}
[/block]
##dim_solution_highest_supercedence

> _added in version 1.1.0_

**Description:** Dimension that provides access to the highest level superceding solution for every solution. If a solution has multiple superceding solutions that themselves are not superceded, all will be returned. Therefore a single solution may have multiple records returned. If a solution is not superceded by any other solution, it will be marked as being superceded by itself (to allow natural joining behavior).

**Type:** slowly changing (Type I)

###Columns
[block:parameters]
{
  "data": {
    "h-0": "Column",
    "h-1": "Data Type",
    "h-2": "Nullable",
    "h-3": "Description",
    "h-4": "Associated Dimension",
    "0-0": "solution_id",
    "0-1": "integer",
    "0-2": "No",
    "0-3": "The identifier of the solution.",
    "0-4": "dim_solution",
    "1-0": "superceding_solution_id",
    "1-1": "integer",
    "1-2": "No",
    "1-3": "The surrogate identifier of a solution that is known to supercede the solution, and which itself is not superceded (the highest level of supercedence). If the solution is not superceded, this is the same identifier as *solution_id*.",
    "1-4": "dim_solution"
  },
  "cols": 5,
  "rows": 2
}
[/block]
##dim_solution_prerequisite

> _added in version 1.1.0_

**Description:** Dimension that provides an association between a solution and all the prerequisite solutions that must be applied before it. If a solution has no prerequisites, it will have no records in this dimension.

**Type:** slowly changing (Type I)

###Columns
[block:parameters]
{
  "data": {
    "h-0": "Column",
    "h-1": "Data Type",
    "h-2": "Nullable",
    "h-3": "Description",
    "h-4": "Associated Dimension",
    "0-0": "solution_id",
    "0-1": "integer",
    "0-2": "No",
    "0-3": "The identifier of the solution.",
    "0-4": "dim_solution",
    "1-0": "required_solution_id",
    "1-1": "integer",
    "1-2": "No",
    "1-3": "The identifier of the solution that is required to be applied before the solution can be applied.",
    "1-4": "dim_solution"
  },
  "cols": 5,
  "rows": 2
}
[/block]
##dim_tag

> _added in version 1.2.0_

**Description:** Dimension for all tags that any assets within the scope of the report belong to. Each tag has either a direct association or indirection association to an asset based off site or asset group association or off dynamic membership criteria.

**Type:** slowly changing (Type I)

###Columns
[block:parameters]
{
  "data": {
    "h-0": "Column",
    "h-1": "Data Type",
    "h-2": "Nullable",
    "h-3": "Description",
    "h-4": "Associated Dimension",
    "0-0": "tag_id",
    "0-1": "integer",
    "0-2": "No",
    "0-3": "The identifier of the tag.",
    "1-0": "tag_name",
    "1-1": "text",
    "1-2": "No",
    "1-3": "The name of the tag. Names are unique for tags within a type.",
    "2-0": "tag_type",
    "2-1": "text",
    "2-2": "No",
    "2-3": "The type of the tag. The supported types are CRITICALITY, LOCATION, OWNER, and CUSTOM.",
    "3-0": "source",
    "3-1": "text",
    "3-2": "No",
    "3-3": "The original application that created the tag.",
    "4-0": "creation_date",
    "4-1": "timestamp",
    "4-2": "No",
    "4-3": "The date and time at which the tag was created.",
    "5-0": "risk_modifier",
    "5-1": "float",
    "5-2": "Yes",
    "5-3": "The risk modifier for a CRITICALITY typed tag.",
    "6-0": "color",
    "6-1": "text",
    "6-2": "Yes",
    "6-3": "The risk modifier for a CRITICALITY typed tag."
  },
  "cols": 5,
  "rows": 7
}
[/block]
##dim_tag_asset

> _added in version 1.2.0_

**Description:** Dimension for the association between an asset and a tag. For each asset there will be one record with an association to only one tag. This dimension only provides current associations. It does not indicate whether an asset was previously associated with a tag.

**Type:** slowly changing (Type I)

###Columns
[block:parameters]
{
  "data": {
    "h-0": "Column",
    "h-1": "Data Type",
    "h-2": "Nullable",
    "h-3": "Description",
    "h-4": "Associated Dimension",
    "0-0": "tag_id",
    "0-1": "integer",
    "0-2": "No",
    "0-3": "The unique identifier of the tag.",
    "0-4": "dim_tag",
    "1-0": "asset_id",
    "1-1": "bigint",
    "1-2": "No",
    "1-3": "The unique identifier of the asset.",
    "1-4": "dim_asset",
    "2-0": "association",
    "2-1": "text",
    "2-2": "No",
    "2-3": "The association that the tag has with the asset. It can be a direct association (tag) or an indirect association through a site (site), a group (group) or the tag dynamic search criteria (criteria).",
    "3-0": "site_id",
    "3-1": "integer",
    "3-2": "Yes",
    "3-3": "The site identifier by which an asset indirectly associates with the tag.",
    "3-4": "dim_site",
    "4-0": "group_id",
    "4-1": "integer",
    "4-2": "Yes",
    "4-3": "The asset group identifier by which an asset indirectly associates with the tag.",
    "4-4": "dim_asset_group"
  },
  "cols": 5,
  "rows": 5
}
[/block]
##dim_vulnerability_solution

> _added in version 1.1.0_

**Description:** Dimension that provides access to the relationship between a vulnerability and its (direct) solutions. These solutions are only those which are directly known to remediate the vulnerability, and does not include rollups or superceding solutions. If a vulnerability has more than one solution, multiple associated records will be present. If a vulnerability has no solutions, it will have no records in this dimension.

**Type:** slowly changing (Type I)

###Columns
[block:parameters]
{
  "data": {
    "h-0": "Column",
    "h-1": "Data Type",
    "h-2": "Nullable",
    "h-3": "Description",
    "h-4": "Associated Dimension",
    "0-0": "vulnerability_id",
    "0-1": "integer",
    "0-2": "No",
    "0-3": "The identifier of the vulnerability.",
    "0-4": "dim_vulnerability",
    "1-0": "solution_id",
    "1-1": "integer",
    "1-2": "No",
    "1-3": "The identifier of the solution that vulnerability may be remediated with.",
    "1-4": "dim_solution"
  },
  "cols": 5,
  "rows": 2
}
[/block]
##dim_vulnerability

**Description:** Dimension for all the metadata related to a vulnerability. This dimension will contain one record for every vulnerability included within the scope of the report. The values in this dimension will change whenever the risk model of the Security Console is modified.

**Type:** slowly changing (Type I)

###Columns
[block:parameters]
{
  "data": {
    "h-0": "Column",
    "h-1": "Data Type",
    "h-2": "Nullable",
    "h-3": "Description",
    "h-4": "Associated Dimension",
    "0-0": "vulnerability_id",
    "0-1": "integer",
    "0-2": "No",
    "0-3": "The identifier of the vulnerability.",
    "1-0": "description",
    "1-1": "text",
    "1-2": "No",
    "1-3": "Long description for the vulnerability.",
    "2-0": "nexpose_id",
    "2-1": "text",
    "2-2": "No",
    "2-3": "A textual identifier of a vulnerability unique to the application.",
    "3-0": "title",
    "3-1": "text",
    "3-2": "No",
    "3-3": "The short, succinct title of the vulnerability.",
    "4-0": "date_published",
    "4-1": "date",
    "4-2": "No",
    "4-3": "The date that the vulnerability was published by the source of the vulnerability (third-party, software vendor, or another authoring source).",
    "5-0": "date_added",
    "5-1": "date",
    "5-2": "No",
    "5-3": "The date that the vulnerability was first checked by the application.",
    "6-0": "severity_score",
    "6-1": "smallint",
    "6-2": "No",
    "6-3": "The numerical severity of the vulnerability, measured on a scale of 0 to 10 using whole numbers. A value of zero indicates low severity, and a value of 10 indicates high severity.",
    "7-0": "severity",
    "7-1": "text",
    "7-2": "No",
    "7-3": "A human-readable description of the severity_score value. Possible values are 'Critical' , 'Severe' , and 'Moderate'.",
    "8-0": "pci_severity_score",
    "8-1": "smallint",
    "8-2": "No",
    "8-3": "The numerical PCI severity score of the vulnerability, measured on a scale of 1 to 5 using whole numbers.",
    "9-0": "pci_status",
    "9-1": "text",
    "9-2": "No",
    "9-3": "A human-readable description as to whether if the vulnerability was detected on an asset in a scan it would cause a PCI failure. Possible values are ' Pass ' or ' Fail '.",
    "10-0": "riskscore",
    "10-1": "double precision",
    "10-2": "No",
    "10-3": "The risk score of the vulnerability as computed by the risk model currently configured on the Security Console.",
    "11-0": "cvss_vector",
    "11-1": "text",
    "11-2": "No",
    "11-3": "A full CVSS vector in the CVSSv2 notation.",
    "12-0": "cvss_access_vector_id",
    "12-1": "character(1)",
    "12-2": "No",
    "12-3": "The access vector (AV) code that represents the CVSS access vector value of the vulnerability.",
    "12-4": "dim_cvss_access_vector_type",
    "13-0": "cvss_access_complexity_id",
    "13-1": "character(1)",
    "13-2": "No",
    "13-3": "The access complexity (AC) code that represents the CVSS access complexity value of the vulnerability.",
    "13-4": "dim_cvss_access_complexity",
    "14-0": "cvss_authentication_id",
    "14-1": "character(1)",
    "14-2": "No",
    "14-3": "The authentication (Au) code that represents the CVSS authentication value of the vulnerability.",
    "14-4": "dim_cvss_access_authentication_type",
    "15-0": "cvss_confidentiality_impact_id",
    "15-1": "character(1)",
    "15-2": "No",
    "15-3": "The confidentiality impact (C) code that represents the CVSS confidentiality impact value of the vulnerability.",
    "15-4": "dim_cvss_confidentiality_impact",
    "16-0": "cvss_integrity_impact_id",
    "16-1": "character(1)",
    "16-2": "No",
    "16-3": "The integrity impact (I) code that represents the CVSS integrity impact value of the vulnerability.",
    "16-4": "dim_cvss_integrity_impact_type",
    "17-0": "cvss_availability_impact_id",
    "17-1": "character(1)",
    "17-2": "No",
    "17-3": "The availability impact (A) code that represents the CVSS availability impact value of the vulnerability.",
    "17-4": "dim_cvss_availability_impact",
    "18-0": "cvss_score",
    "18-1": "real",
    "18-2": "No",
    "18-3": "The CVSS score of the vulnerability, on a scale of 0 to 10.",
    "19-0": "pci_adjusted_cvscore",
    "19-1": "real",
    "19-2": "No",
    "19-3": "Value between 0 and 10 representing the CVSS score of the vulnerability, adjusted if necessary according to PCI rules.",
    "19-4": "s_s",
    "20-0": "cvss_exploit_score",
    "20-1": "real",
    "20-2": "No",
    "20-3": "The base exploit score contribution to the CVSS score.",
    "21-0": "cvss_impact_score",
    "21-1": "real",
    "21-2": "No",
    "21-3": "The base impact score contribution to the CVSS score.",
    "22-0": "pci_special_notes",
    "22-1": "text",
    "22-2": "Yes",
    "22-3": "Notes attached to the vulnerability according to PCI rules.",
    "23-0": "denial_of_service",
    "23-1": "boolean",
    "23-2": "No",
    "23-3": "Indicates whether the vulnerability is classified as a denial-of-service vulnerability.",
    "24-0": "exploits",
    "24-1": "bigint",
    "24-2": "No",
    "24-3": "The number of distinct exploits that are associated with the vulnerability. If no exploits are associated to this vulnerability, the value will be zero.",
    "25-0": "malware_kits",
    "25-1": "bigint",
    "25-2": "No",
    "25-3": "The number of malware kits that are associated with the vulnerability. If no malware kits are associated to this vulnerability, the value will be zero.",
    "26-0": "date_modified",
    "26-1": "date",
    "26-2": "No",
    "26-3": "The date the vulnerability was last modified in a content release. The granularity of the date is a day."
  },
  "cols": 5,
  "rows": 27
}
[/block]
 ##dim_vulnerability_category

**Description:** Dimension that provides the relationship between a vulnerability and a vulnerability category.

**Type:** normal

###Columns
[block:parameters]
{
  "data": {
    "h-0": "Column",
    "h-1": "Data Type",
    "h-2": "Nullable",
    "0-0": "category_id",
    "h-3": "Description",
    "h-4": "Associated Dimension",
    "0-1": "integer",
    "0-2": "No",
    "0-3": "The identifier of the vulnerability category.",
    "1-0": "vulnerability_id",
    "1-1": "integer",
    "1-2": "No",
    "1-3": "The identifier of the vulnerability the category applies to.",
    "1-4": "dim_vulnerability",
    "2-0": "category_name",
    "2-1": "text",
    "2-2": "No",
    "2-3": "The descriptive name of the category."
  },
  "cols": 5,
  "rows": 3
}
[/block]
##dim_vulnerability_exception

**Description:** Dimension that provides access to all vulnerability exceptions in any state (including deleted) that may apply to any assets within the scope of the report. The exceptions available in this dimension will change as the their state changes, or any new exceptions are created over time.

**Type:** slowly changing (Type II)

###Columns
[block:parameters]
{
  "data": {
    "h-0": "Column",
    "h-1": "Data Type",
    "h-2": "Nullable",
    "h-3": "Description",
    "h-4": "Associated Dimension",
    "0-0": "vulnerability_exception_id",
    "0-1": "integer",
    "0-2": "No",
    "0-3": "The identifier of the vulnerability exception.",
    "1-0": "vulnerability_id",
    "1-1": "integer",
    "1-2": "No",
    "1-3": "The identifier of the vulnerability.",
    "1-4": "dim_vulnerability",
    "2-0": "scope_id",
    "2-1": "character(1)",
    "2-2": "No",
    "2-3": "The scope of the vulnerability exception, which dictates what assets the exception applies to.",
    "2-4": "dim_exception_scope",
    "3-0": "reason_id",
    "3-1": "character(1)",
    "3-2": "No",
    "3-3": "The reason that the vulnerability exception was submitted.",
    "3-4": "dim_exception_reason",
    "4-0": "additional_comments",
    "4-1": "text",
    "4-2": "Yes",
    "4-3": "Optional comments associated with the last state change of the vulnerability exception.",
    "5-0": "submitted_date",
    "5-1": "timestamp without time zone",
    "5-2": "No",
    "5-3": "The date the vulnerability was originally created and submitted, in the time zone specified by the report configuration.",
    "6-0": "submitted_by",
    "6-1": "text",
    "6-2": "No",
    "6-3": "The login name of the user that submitted the vulnerability exception.",
    "7-0": "review_date",
    "7-1": "timestamp without time zone",
    "7-2": "Yes",
    "7-3": "The date the vulnerability exception was reviewed, in the time zone specified by the report configuration. If the exception was rejected, approved, or recalled, this is the date of the last state transition made on the exception. If an exception is submitted and has not been reviewed, the value will be _null_.",
    "8-0": "reviewed_by",
    "8-1": "text",
    "8-2": "Yes",
    "8-3": "The login name of the user that reviewed the vulnerability exception. If the exception is submitted and has not been reviewed, the value will be _null_.",
    "9-0": "review_comment",
    "9-1": "text",
    "9-2": "Yes",
    "9-3": "The comment that accompanies the latest review action. If the exception is submitted and has not been reviewed, the value will be _null_.",
    "10-0": "expiration_date",
    "10-1": "date",
    "10-2": "Yes",
    "10-3": "The date at which the vulnerability exception will expire. If the exception has no expiration date set, the value is will be _null_.",
    "11-0": "status_id",
    "11-1": "character(1)",
    "11-2": "No",
    "11-3": "The status (state) of the vulnerability exception.",
    "11-4": "dim_exception_status",
    "12-0": "site_id",
    "12-1": "integer",
    "12-2": "Yes",
    "12-3": "The identifier of the site that the exception applies to. If this is not a site-level exception, the value will be _null_.",
    "12-4": "dim_site",
    "13-0": "asset_id",
    "13-1": "bigint",
    "13-2": "Yes",
    "13-3": "The identifier of the asset that the exception applies to. If this is not an asset-level or instance-level exception, the value will be _null_.",
    "13-4": "dim_asset",
    "14-0": "port",
    "14-1": "integer",
    "14-2": "Yes",
    "14-3": "The port that the exception applies to. If this is not an instance-level exception, the value will be _null_.",
    "15-0": "key",
    "15-1": "text",
    "15-2": "Yes",
    "15-3": "The secondary identifier of the vulnerability the exception applies to. If this is not an instance-level exception, the value will be _null_."
  },
  "cols": 5,
  "rows": 16
}
[/block]
 ##dim_vulnerability_exploit

**Description:** Dimension that provides the relationship between a vulnerability and an exploit.

**Type:** normal

###Columns
[block:parameters]
{
  "data": {
    "h-0": "Column",
    "h-1": "Data Type",
    "h-2": "Nullable",
    "h-3": "Description",
    "h-4": "Associated Dimension",
    "0-0": "exploit_id",
    "0-1": "integer",
    "0-2": "No",
    "0-3": "The identifier of the exploit.",
    "1-0": "vulnerability_id",
    "1-1": "integer",
    "1-2": "No",
    "1-3": "The identifier of the vulnerability.",
    "1-4": "dim_vulnerability",
    "2-0": "title",
    "2-1": "text",
    "2-2": "No",
    "2-3": "The short, succinct title of the exploit.",
    "3-0": "description",
    "3-1": "text",
    "3-2": "Yes",
    "3-3": "The optional verbose description of the exploit. If there is no description, the value is _null_.",
    "4-0": "skill_level",
    "4-1": "text",
    "4-2": "No",
    "4-3": "The skill level required to perform the exploit. Possible values include 'Expert', 'Novice', and 'Intermediate'.",
    "5-0": "source_id",
    "5-1": "text",
    "5-2": "No",
    "5-3": "The source which defined and published the exploit. Possible values include 'Exploit DB' and 'Metasploit Module'.",
    "6-0": "source_key",
    "6-1": "text",
    "6-2": "No",
    "6-3": "The identifier of the exploit in the source system, used as a key to index into the publisher's repository of metadata for the exploit."
  },
  "cols": 5,
  "rows": 7
}
[/block]
##dim_vulnerability_malware_kit

**Description:** Dimension that provides the relationship between a vulnerability and a malware kit.

**Type:** normal

###Columns
[block:parameters]
{
  "data": {
    "h-0": "Column",
    "h-1": "Data Type",
    "h-2": "Nullable",
    "h-3": "Description",
    "h-4": "Associated Dimension",
    "0-0": "vulnerability_id",
    "0-1": "integer",
    "0-2": "No",
    "0-3": "The identifier of the vulnerability the malware kit is associated to.",
    "0-4": "dim_vulnerability",
    "1-0": "name",
    "1-1": "text",
    "1-2": "No",
    "1-3": "The name of the malware kit.",
    "2-0": "popularity",
    "2-1": "text",
    "2-2": "No",
    "2-3": "The popularity of the malware kit, which signifies how common or accessible it is. Possible values include 'Uncommon', 'Occasional' , 'Rare' , 'Common' , 'Favored' , 'Popular' , and 'Unknown'."
  },
  "cols": 5,
  "rows": 3
}
[/block]
##dim_vulnerability_reference

**Description:** Dimension that provides the references associated to a vulnerability, which provide links to external sources of data and information related to a vulnerability.

**Type:** normal

###Columns
[block:parameters]
{
  "data": {
    "h-0": "Column",
    "h-1": "Data Type",
    "h-2": "Nullable",
    "h-3": "Description",
    "h-4": "Associated Dimension",
    "0-0": "vulnerability_id",
    "0-1": "integer",
    "0-2": "No",
    "0-3": "The identifier of the vulnerability.",
    "0-4": "dim_vulnerability",
    "1-0": "source",
    "1-1": "text",
    "1-2": "No",
    "1-3": "The name of the source of the vulnerability information. The value is guaranteed to be provided in all upper-case characters.",
    "2-0": "reference",
    "2-1": "text",
    "2-2": "No",
    "2-3": "The reference that keys or links into the source of the vulnerability information. If the source is 'URL', the reference is 'URL'. Otherwise, the value is typically a key or identifier that indexes into the source repository."
  },
  "cols": 5,
  "rows": 3
}
[/block]
#Enumerated and Constant Dimensions

The following dimensions are static in nature and all represent mappings of codes, identifiers, and other constant values to human readable descriptions.

##dim_cvss_access_vector

**Description:** Dimension for the possible CVSS access vector values.

**Type:** normal

###Columns
[block:parameters]
{
  "data": {
    "h-0": "Column",
    "h-1": "Data Type",
    "h-2": "Nullable",
    "h-3": "Description",
    "0-0": "type_id",
    "0-1": "character(1)",
    "0-2": "No",
    "0-3": "The identifier of the access vector type.",
    "h-4": "Associated Dimension",
    "1-0": "description",
    "1-1": "text",
    "1-2": "No",
    "1-3": "The description of the access vector type."
  },
  "cols": 5,
  "rows": 2
}
[/block]
###Values

###Columns
[block:parameters]
{
  "data": {
    "h-0": "Notes & Detailed Description",
    "h-1": "status_id",
    "h-2": "Description",
    "0-0": "'L'",
    "1-0": "'A'",
    "2-0": "'N'",
    "0-1": "'Local'",
    "0-2": "A vulnerability exploitable with only  local access requires the attacker to have either physical access to the vulnerable system or a local (shell) account.",
    "1-1": "'Adjacent Network'",
    "1-2": "A vulnerability exploitable with adjacent network access requires the attacker to have access to either the broadcast or collision domain of the vulnerable software.",
    "2-1": "'Network'",
    "2-2": "A vulnerability exploitable with network access means the vulnerable software is bound to the network stack and the attacker does not require local network access or local access."
  },
  "cols": 3,
  "rows": 3
}
[/block]
##dim_aggregated_credential_status

> _added in version 1.3.1_

**Description:** Dimension the containing the status aggregated across all available services for the given asset in the given scan.

**Type:** normal

###Columns
[block:parameters]
{
  "data": {
    "h-0": "Column",
    "h-1": "Data Type",
    "h-2": "Nullable",
    "h-3": "Description",
    "h-4": "Associated Dimension",
    "0-0": "aggregated_credential_status_id",
    "1-0": "aggregated_credential_status_description",
    "0-1": "smallint",
    "0-2": "No",
    "0-3": "The credential status ID associated with the fact_asset_scan_service.",
    "0-4": "No",
    "1-1": "text",
    "1-2": "No",
    "1-3": "The human-readable description of the credential status.",
    "1-4": "No"
  },
  "cols": 5,
  "rows": 2
}
[/block]
###Values

###Columns
[block:parameters]
{
  "data": {
    "h-0": "Notes & Detailed Description",
    "h-1": "status_id",
    "h-2": "Description",
    "0-0": "'No credentials supplied'",
    "0-1": "1",
    "0-2": "One or more services for which credential status is reported were detected in the scan, but there were no credentials supplied for any of them.",
    "1-0": "'All credentials failed'",
    "1-1": "2",
    "1-2": "One or more services for which credential status is reported were detected in the scan, and all credentials supplied for these services failed to authenticate.",
    "2-0": "'Credentials partially successful'",
    "2-1": "3",
    "2-2": "At least two of the four services for which credential status is reported were detected in the scan, and for some services the provided credentials failed to authenticate, but for at least one there was a successful authentication.",
    "3-0": "'All credentials successful'",
    "3-1": "4",
    "3-2": "One or more services for which credential status is reported were detected in the scan, and for all of these services for which credentials were supplied authentication with provided credentials was successful.",
    "4-0": "'N/A'",
    "4-1": "-1",
    "4-2": "None of the four applicable services (SNMP, SSH, Telnet, CIFS) was discovered in the scan."
  },
  "cols": 3,
  "rows": 5
}
[/block]
##dim_credential_status

> _added in version 1.3.1_

**Description:** Dimension for the scan service credential status in human-readable form.

**Type:** normal

###Columns
[block:parameters]
{
  "data": {
    "h-0": "Column",
    "h-1": "Data Type",
    "h-2": "Nullable",
    "h-3": "Description",
    "h-4": "Associated Dimension",
    "0-0": "credential_status_id",
    "0-1": "smallint",
    "0-2": "No",
    "0-3": "The credential status ID associated with the fact_asset_scan_service.",
    "1-0": "credential_status_description",
    "1-1": "text",
    "1-2": "No",
    "1-3": "The human-readable description of the credential status."
  },
  "cols": 5,
  "rows": 2
}
[/block]
###Values

###Columns
[block:parameters]
{
  "data": {
    "h-0": "Notes & Detailed Description",
    "h-1": "status_id",
    "h-2": "Description",
    "0-0": "'No credentials supplied'",
    "0-1": "1",
    "0-2": "No credentials were supplied. Applicable to all four services (SNMP, SSH, Telnet, or CIFS).",
    "1-0": "'Login failed'",
    "1-1": "2",
    "1-2": "The login failed. Applicable to all four services (SNMP, SSH, Telnet, or CIFS).",
    "2-0": "'Login successful'",
    "2-1": "3",
    "2-2": "The login succeeded. The login failed. Applicable to all four services (SNMP, SSH, Telnet, or CIFS).",
    "3-0": "'Allowed elevation of privileges'",
    "3-1": "4",
    "3-2": "Elevation of privileges was allowed. Applicable to SSH only.",
    "4-0": "'Root'",
    "4-1": "5",
    "4-2": "The credentials allowed login as root. Applicable to SSH and Telnet only.",
    "5-0": "'Login as local admin'",
    "5-1": "6",
    "5-2": "The credentials allowed login as local admin. Applicable to CIFS only.",
    "6-0": "'N/A'",
    "6-1": "-1",
    "6-2": "This status is listed for all the services that are not SNMP, SSH, Telnet, or CIFS."
  },
  "cols": 3,
  "rows": 7
}
[/block]
##dim_cvss_access_complexity

**Description:** Dimension for the possible CVSS access complexity values.

**Type:** normal

###Columns
[block:parameters]
{
  "data": {
    "h-0": "Column",
    "h-1": "Data Type",
    "h-2": "Nullable",
    "h-3": "Description",
    "h-4": "Associated Dimension",
    "0-0": "type_id",
    "0-1": "character(1)",
    "0-2": "No",
    "0-3": "The identifier of the access complexity type.",
    "1-0": "description",
    "1-1": "text",
    "1-2": "No",
    "1-3": "The description of the access complexity type."
  },
  "cols": 5,
  "rows": 2
}
[/block]
###Values

###Columns
[block:parameters]
{
  "data": {
    "h-0": "Notes & Detailed Description",
    "h-1": "status_id",
    "h-2": "Description",
    "0-0": "'H'",
    "1-0": "'M'",
    "2-0": "'L'",
    "0-1": "'High'",
    "0-2": "Specialized access conditions exist.",
    "1-1": "'Medium'",
    "1-2": "The access conditions are somewhat specialized.",
    "2-2": "Specialized access conditions or extenuating circumstances do not exist.",
    "2-1": "'Low'"
  },
  "cols": 3,
  "rows": 3
}
[/block]
##dim_cvss_authentication

**Description:** Dimension for the possible CVSS authentication values.

**Type:** normal

###Columns
[block:parameters]
{
  "data": {
    "h-0": "Column",
    "h-1": "Data Type",
    "h-2": "Nullable",
    "h-3": "Description",
    "h-4": "Associated Dimension",
    "0-0": "type_id",
    "0-1": "character(1)",
    "0-2": "No",
    "0-3": "The identifier of the authentication type.",
    "1-0": "description",
    "1-1": "text",
    "1-2": "No",
    "1-3": "The description of the authentication type."
  },
  "cols": 5,
  "rows": 2
}
[/block]
 ###Values

###Columns
[block:parameters]
{
  "data": {
    "h-0": "Notes & Detailed Description",
    "h-1": "status_id",
    "h-2": "Description",
    "0-0": "'M'",
    "0-1": "'Multiple'",
    "0-2": "Exploiting the vulnerability requires that the attacker authenticate two or more times, even if the same credentials are used each time",
    "1-0": "'S'",
    "1-1": "'Single'",
    "1-2": "The vulnerability requires an attacker to be logged into the system (such as at a command line or via a desktop session or web interface).",
    "2-2": "Authentication is not required to exploit the vulnerability.",
    "2-0": "'N'",
    "2-1": "'None'"
  },
  "cols": 3,
  "rows": 3
}
[/block]
##dim_cvss_confidentiality_impact

**Description:** Dimension for the possible CVSS confidentiality impact values.

**Type:** normal

###Columns
[block:parameters]
{
  "data": {
    "h-0": "Column",
    "h-1": "Data Type",
    "h-2": "Nullable",
    "h-3": "Description",
    "h-4": "Associated Dimension",
    "0-0": "type_id",
    "0-1": "character(1)",
    "0-2": "No",
    "0-3": "The identifier of the confidentiality impact type.",
    "1-0": "description",
    "1-1": "text",
    "1-2": "No",
    "1-3": "The description of the confidentiality impact type."
  },
  "cols": 5,
  "rows": 2
}
[/block]
###Values

###Columns
[block:parameters]
{
  "data": {
    "h-0": "Notes & Detailed Description",
    "h-1": "status_id",
    "h-2": "Description",
    "0-0": "'P'",
    "0-1": "'Partial'",
    "0-2": "There is considerable informational disclosure. Access to some system files is possible, but the attacker does not have control over what is obtained, or the scope of the loss is constrained.",
    "1-0": "'C'",
    "1-1": "'Complete'",
    "1-2": "There is total information disclosure, resulting in all system files being revealed. The attacker is able to read all of the system's data (memory, files, etc.).",
    "2-0": "'N'",
    "2-1": "'None'",
    "2-2": "There is no impact to the confidentiality of the system."
  },
  "cols": 3,
  "rows": 3
}
[/block]
##dim_cvss_integrity_impact

**Description:** Dimension for the possible CVSS integrity impact values.

**Type:** normal

###Columns
[block:parameters]
{
  "data": {
    "h-0": "Column",
    "h-1": "Data Type",
    "h-2": "Nullable",
    "h-3": "Description",
    "h-4": "Associated Dimension",
    "0-0": "type_id",
    "1-0": "description",
    "0-1": "character(1)",
    "1-1": "text",
    "0-2": "No",
    "1-2": "No",
    "0-3": "The identifier of the confidentiality impact type.",
    "1-3": "The description of the confidentiality impact type."
  },
  "cols": 5,
  "rows": 2
}
[/block]
###Values

###Columns
[block:parameters]
{
  "data": {
    "h-0": "Notes & Detailed Description",
    "h-1": "status_id",
    "h-2": "Description",
    "0-0": "'P'",
    "1-0": "'C'",
    "2-0": "'N'",
    "0-1": "'Partial'",
    "1-1": "'Complete'",
    "2-1": "'None'",
    "0-2": "Modification of some system files or information is possible, but the attacker does not have control over what can be modified, or the scope of what the attacker can affect is limited.",
    "1-2": "There is a total compromise of system integrity. There is a complete loss of system protection, resulting in the entire system being compromised. The attacker is able to modify any files on the target system.",
    "2-2": "There is no impact to the integrity of the system."
  },
  "cols": 3,
  "rows": 3
}
[/block]
##dim_cvss_availability_impact

**Description:** Dimension for the possible CVSS availability impact values.

**Type:** normal

###Columns
[block:parameters]
{
  "data": {
    "h-0": "Column",
    "h-1": "Data Type",
    "h-2": "Nullable",
    "h-3": "Description",
    "h-4": "Associated Dimension",
    "0-0": "type_id",
    "0-1": "character(1)",
    "0-2": "No",
    "0-3": "The identifier of the availability impact type.",
    "1-0": "description",
    "1-1": "text",
    "1-2": "No",
    "1-3": "The description of the availability impact type."
  },
  "cols": 5,
  "rows": 2
}
[/block]
###Values

###Columns
[block:parameters]
{
  "data": {
    "h-0": "Notes & Detailed Description",
    "h-1": "status_id",
    "h-2": "Description",
    "0-0": "'P'",
    "1-0": "'C'",
    "2-0": "'N'",
    "0-1": "'Partial'",
    "1-1": "'Complete'",
    "2-1": "'None'",
    "0-2": "There is reduced performance or interruptions in resource availability.",
    "1-2": "There is a total shutdown of the affected resource. The attacker can render the resource completely unavailable.",
    "2-2": "There is no impact to the availability of the system."
  },
  "cols": 3,
  "rows": 3
}
[/block]
##dim_exception_scope

**Description:** Dimension that provides all scopes a vulnerability exception can be defined on.

**Type:** normal

###Columns
[block:parameters]
{
  "data": {
    "h-0": "Column",
    "h-1": "Data Type",
    "h-2": "Nullable",
    "h-3": "Description",
    "h-4": "Associated Dimension",
    "0-0": "scope_id",
    "0-1": "character(1)",
    "0-2": "No",
    "0-3": "The identifier of the scope of a vulnerability exception.",
    "1-0": "short_description",
    "1-1": "text",
    "1-2": "No",
    "1-3": "A succinct, one-word description of the scope.",
    "2-0": "description",
    "2-1": "text",
    "2-2": "No",
    "2-3": "A verbose description of the scope."
  },
  "cols": 5,
  "rows": 3
}
[/block]
###Values

###Columns
[block:parameters]
{
  "data": {
    "h-0": "Notes & Detailed Description",
    "h-1": "scope_id",
    "h-2": "short_description",
    "h-3": "Description",
    "0-0": "'G'",
    "0-1": "'Global'",
    "0-2": "'All instances (all assets)'",
    "0-3": "The vulnerability exception is applied to all assets in every site.",
    "1-0": "'S'",
    "1-1": "'Site'",
    "1-2": "'All instances in this site'",
    "1-3": "The vulnerability exception is applied to only assets within a specific site.",
    "2-0": "'D'",
    "2-1": "'Asset'",
    "2-2": "'All instances on this asset'",
    "2-3": "The vulnerability exception is applied to all instances of the vulnerability on an asset.",
    "3-0": "'I'",
    "3-1": "'Instance'",
    "3-2": "'Specific instance on this asset'",
    "3-3": "The vulnerability exception is applied to a specific instances of the vulnerability on an asset (either all instances without a port, or instances sharing the same port and key)."
  },
  "cols": 4,
  "rows": 4
}
[/block]
##dim_exception_reason

**Description:** Dimension for all possible reasons that can be used within a vulnerability exception.

**Type:** normal

###Columns
[block:parameters]
{
  "data": {
    "h-0": "Column",
    "h-1": "Data Type",
    "h-2": "Nullable",
    "h-3": "Description",
    "h-4": "Associated Dimension",
    "0-0": "reason_id",
    "0-1": "character(1)",
    "0-2": "No",
    "0-3": "The identifier for the reason of the vulnerability exception.",
    "1-0": "description",
    "1-1": "text",
    "1-2": "No"
  },
  "cols": 5,
  "rows": 2
}
[/block]
###Values

###Columns
[block:parameters]
{
  "data": {
    "h-0": "Notes & Detailed Description",
    "h-1": "reason_id",
    "h-2": "Description",
    "0-1": "'False positive'",
    "0-0": "'F'",
    "0-2": "The vulnerability is a false-positive and was confirmed to be an inaccurate result.",
    "1-1": "'Compensating control'",
    "1-0": "'C'",
    "1-2": "There is a compensating control in place unique to the site or environment that mitigates the vulnerability.",
    "2-0": "'R'",
    "2-1": "'Acceptable risk'",
    "2-2": "The vulnerability is deemed an acceptable risk to the organization.",
    "3-2": "The vulnerability is deemed to be acceptable with normal use (not a vulnerability to the organization).",
    "3-1": "'Acceptable use'",
    "3-0": "'U'",
    "4-0": "'O'",
    "4-1": "'Other'",
    "4-2": "Any other reason not covered in a build-in reason."
  },
  "cols": 3,
  "rows": 5
}
[/block]
##dim_exception_status

**Description:** Dimension for the possible statuses (states) of a vulnerability exception.

**Type:** normal

###Columns 
[block:parameters]
{
  "data": {
    "h-0": "Column",
    "h-1": "Data Type",
    "h-2": "Nullable",
    "h-3": "Description",
    "0-0": "status_id",
    "h-4": "Associated Dimension",
    "0-1": "character(1)",
    "0-2": "No",
    "0-3": "The identifier of the exception status.",
    "1-3": "The description or name of the exception status.",
    "1-2": "No",
    "1-1": "text",
    "1-0": "description"
  },
  "cols": 5,
  "rows": 2
}
[/block]
 ###Values

###Columns
[block:parameters]
{
  "data": {
    "h-0": "Notes & Detailed Description",
    "h-1": "status_id",
    "h-2": "Description",
    "0-1": "'Under review'",
    "0-0": "'U'",
    "0-2": "The exception was submitted and is waiting for review from an approver.",
    "1-1": "'Approved'",
    "1-2": "The exception was approved by a reviewer and is actively applied.",
    "1-0": "'A'",
    "2-1": "'Rejected'",
    "2-0": "'R'",
    "2-2": "The exception was rejected by the reviewer and requires further action by the submitter.",
    "3-1": "'Recalled'",
    "3-2": "The exception was deleted by the reviewer or recalled by the submitted.",
    "3-0": "'D'",
    "4-0": "'E'",
    "4-1": "'Expired'",
    "4-2": "The exception has expired due to an expiration date."
  },
  "cols": 3,
  "rows": 5
}
[/block]
##dim_host_name_source_type

**Description:** Dimension for the types of sources used to detect a host name on an asset.

**Type:** normal

###Columns
[block:parameters]
{
  "data": {
    "h-0": "Column",
    "h-1": "Data Type",
    "h-2": "Nullable",
    "h-3": "Description",
    "h-4": "Associated Dimension",
    "0-0": "type_id",
    "0-1": "character(1)",
    "0-2": "No",
    "0-3": "The identifier of the source type.",
    "1-3": "The description of the source type code.",
    "1-2": "No",
    "1-1": "text",
    "1-0": "description"
  },
  "cols": 5,
  "rows": 2
}
[/block]
###Values

###Columns
[block:parameters]
{
  "data": {
    "h-0": "Notes & Detailed Description",
    "h-1": "type_id",
    "h-2": "Description",
    "0-1": "'User Defined'",
    "0-0": "'T'",
    "0-2": "The host name of the asset was acquired as a result of being specified as a target within the scan (in the site configuration).",
    "1-1": "'DNS'",
    "1-2": "The host name discovered during a scan using the domain name system (DNS).",
    "1-0": "'D'",
    "2-1": "'NetBIOS'",
    "2-0": "'N'",
    "2-2": "The host name was discovered during a scan using the NetBios protocol.",
    "3-1": "'LDAP'",
    "3-2": "The host name was discovered using LDAP.",
    "3-0": "'L'",
    "4-1": "'EPSEC'",
    "4-0": "'E'",
    "4-2": "The host name was discovered using VMWare EPSEC.",
    "5-1": "'DCE'",
    "5-0": "'C'",
    "6-0": "'-'",
    "6-1": "'N/A'",
    "5-2": "The host name was discovered using DCE.",
    "6-2": "The source of the host name could not be determined or is unknown."
  },
  "cols": 3,
  "rows": 7
}
[/block]
##dim_host_type

**Description:** Dimension for the types of hosts that an asset can be classified as.

**Type:** normal

###Columns
[block:parameters]
{
  "data": {
    "h-0": "Column",
    "h-1": "Data Type",
    "h-2": "Nullable",
    "h-3": "Associated Dimension",
    "0-0": "host_type_id",
    "0-1": "integer",
    "0-2": "No",
    "0-3": "The identifier of the host type.",
    "1-0": "description",
    "1-1": "text",
    "1-2": "No",
    "1-3": "The description of the host type code."
  },
  "cols": 4,
  "rows": 2
}
[/block]
###Values

###Columns
[block:parameters]
{
  "data": {
    "h-0": "host_type_id",
    "0-0": "1",
    "1-0": "2",
    "2-0": "3",
    "3-0": "4",
    "4-0": "-1",
    "h-1": "Description",
    "0-1": "'Virtual Machine'",
    "1-1": "'Hypervisor'",
    "2-1": "'Bare Metal'",
    "3-1": "'Mobile'",
    "4-1": "'Unknown'",
    "0-2": "The asset is a generic virtualized asset resident within a virtual machine.",
    "h-2": "Explanation",
    "1-2": "The asset is a virtualized asset within Hypervisor.",
    "2-2": "The asset is a physical machine.",
    "3-2": "The asset type is a mobile device (added in version 2.0.1)",
    "4-2": "The asset type is unknown or could not be determined."
  },
  "cols": 3,
  "rows": 5
}
[/block]
##dim_scan_status

**Description:** Dimension for all possible statuses of a scan.

**Type:** normal

###Columns
[block:parameters]
{
  "data": {
    "h-0": "Column",
    "h-1": "Data type",
    "h-2": "Nullable",
    "h-3": "Description",
    "h-4": "Associated Dimension",
    "0-0": "status_id",
    "0-1": "character(1)",
    "0-2": "No",
    "0-3": "The identifier of the status a scan can have.",
    "1-0": "description",
    "1-1": "text",
    "1-2": "No",
    "1-3": "The description of the status code."
  },
  "cols": 5,
  "rows": 2
}
[/block]
###Values

###Columns
[block:parameters]
{
  "data": {
    "h-0": "Notes & Detailed Description",
    "h-1": "Status_id",
    "h-2": "Description",
    "0-0": "'A'",
    "0-1": "'Aborted'",
    "0-2": "The scan was either manually or automatically aborted by the system. If a scan is marked as aborted, it usually terminated abnormally. Aborted scans can occur when an engine is interrupted (terminated) while a scan is actively running.",
    "1-1": "'Successful'",
    "1-0": "'C'",
    "1-2": "The scan was successfully completed and no errors were encountered (this includes scans that were manually or automatically resumed).",
    "2-1": "'Running'",
    "2-2": "The scan is actively running and is in a non-paused state.",
    "2-0": "'U'",
    "3-0": "'S'",
    "3-1": "'Stopped'",
    "3-2": "The scan was manually stopped by the user.",
    "4-0": "'E'",
    "4-1": "'Failed'",
    "4-2": "The scan failed to launch or run successfully.",
    "5-0": "'P'",
    "5-1": "'Paused'",
    "5-2": "The scan is halted because a user manually paused the scan or the scan has met its maximum scan duration.",
    "6-0": "'-'",
    "6-1": "'Unknown'",
    "6-2": "The status of the scan cannot be determined."
  },
  "cols": 3,
  "rows": 7
}
[/block]
##dim_scan_type

**Description:** Dimension for all possible types of scans.

**Type:** normal

###Columns
[block:parameters]
{
  "data": {
    "h-0": "Column",
    "h-1": "Data Type",
    "h-2": "Nullable",
    "h-3": "Description",
    "h-4": "Associated Dimension",
    "0-0": "type_id",
    "0-1": "character(1)",
    "0-2": "No",
    "0-3": "The identifier of the type a scan can be.",
    "1-0": "description",
    "1-1": "text",
    "1-2": "No",
    "1-3": "The description of the type code."
  },
  "cols": 5,
  "rows": 2
}
[/block]
###Values

###Columns
[block:parameters]
{
  "data": {
    "h-0": "Notes & Detailed Description",
    "h-1": "type_id",
    "h-2": "Description",
    "0-1": "'Manual'",
    "0-0": "'A'",
    "0-2": "The scan was manually launched by a user.",
    "1-1": "'Scheduled'",
    "1-0": "'S'",
    "1-2": "The scan was launched automatically by the Security Console on a schedule.",
    "2-2": "The scan type could not be determined or is unknown.",
    "2-1": "'Unknown'",
    "2-0": "'-'"
  },
  "cols": 3,
  "rows": 3
}
[/block]
##dim_vulnerability_status

**Description:** Dimension for the statuses a vulnerability finding result can be classified as.

**Type:** normal

###Columns
[block:parameters]
{
  "data": {
    "h-0": "Column",
    "h-1": "Data Type",
    "h-2": "Nullable",
    "h-3": "Description",
    "h-4": "Associated Dimension",
    "0-0": "status_id",
    "0-1": "character(1)",
    "0-2": "No",
    "0-3": "The identifier of the vulnerability status.",
    "1-0": "description",
    "1-1": "text",
    "1-2": "No",
    "1-3": "The description of the vulnerability status."
  },
  "cols": 5,
  "rows": 2
}
[/block]
###Values

###Columns
[block:parameters]
{
  "data": {
    "h-0": "Notes & Detailed Description",
    "h-1": "status_id",
    "h-2": "Description",
    "0-0": "'2'",
    "1-0": "'3'",
    "2-0": "'9'",
    "2-1": "'Potential vulnerability'",
    "1-1": "'Vulnerable version'",
    "0-1": "'Confirmed vulnerability'",
    "0-2": "The vulnerability was discovered and either exploited or confirmed.",
    "1-2": "The vulnerability was discovered within a version of the installed software or operating system.",
    "2-2": "The vulnerability was discovered, but not exploited or confirmed."
  },
  "cols": 3,
  "rows": 3
}
[/block]
##dim_protocol

**Description:** Dimension that provides all possible protocols that a service can be utilizing on an asset.

**Type:** normal

###Columns
[block:parameters]
{
  "data": {
    "h-0": "Column",
    "h-1": "Data Type",
    "h-2": "Nullable",
    "h-3": "Description",
    "h-4": "Associated Dimension",
    "0-0": "protocol_id",
    "0-1": "integer",
    "0-2": "No",
    "0-3": "The identifier of the protocol.",
    "1-0": "name",
    "1-1": "text",
    "1-2": "No",
    "1-3": "The name of the protocol.",
    "2-0": "description",
    "2-1": "text",
    "2-2": "No",
    "2-3": "The non-abbreviated description of the protocol."
  },
  "cols": 5,
  "rows": 3
}
[/block]
###Values

###Columns
[block:parameters]
{
  "data": {
    "h-0": "protocol_id",
    "h-1": "Name",
    "h-2": "Description",
    "0-0": "0",
    "0-1": "'IP'",
    "0-2": "'Internet Protocol'",
    "1-0": "1",
    "1-1": "'ICMP'",
    "1-2": "'Internet Control Message Protocol'",
    "2-0": "2",
    "2-1": "'IGMP'",
    "2-2": "'Internet Group Management Protocol'",
    "3-0": "3",
    "3-1": "'GGP'",
    "3-2": "'Gateway-to-Gateway Protocol'",
    "4-0": "6",
    "4-1": "'TCP'",
    "4-2": "'Transmission Control Protocol'",
    "5-0": "12",
    "5-1": "'PUP'",
    "5-2": "'PARC Universal Protocol'",
    "6-0": "17",
    "6-1": "'UDP'",
    "6-2": "'User Datagram Protocol'",
    "7-0": "22",
    "7-1": "'IDP'",
    "7-2": "'Internet Datagram Protocol'",
    "8-0": "50",
    "8-1": "'ESP'",
    "8-2": "'Encapsulating Security Payload'",
    "9-0": "77",
    "9-1": "'ND'",
    "9-2": "'Network Disk Protocol'",
    "10-0": "255",
    "10-1": "'RAW'",
    "10-2": "'Raw Packet'",
    "11-0": "-1",
    "11-1": "''",
    "11-2": "'N/A'"
  },
  "cols": 3,
  "rows": 12
}
[/block]