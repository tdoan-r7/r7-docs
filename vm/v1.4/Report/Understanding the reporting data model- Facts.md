---
title: "Understanding the reporting data model: Facts"
excerpt: ""
---
The following facts are provided by the Reporting Data Model. Each fact table provides access to only information allowed by the configuration of the report. Any vulnerability status, severity or category filters will be applied in the facts, only allowing those results, findings, and counts for vulnerabilities in the scope to be exposed. Similarly, only assets within the scope of the report configuration are made available in the fact tables. By default, all facts are interpreted to be asset-centric, and therefore expose information for all assets in the scope of the report, regardless as to whether they were configured to be in scope with the use of an asset, scan, asset group, or site selection.
[block:callout]
{
  "type": "info",
  "body": "Data model 2.0.0 exposes information about linking assets across sites. All previous information is still available, and in the same format. As of data model 2.0.0, there is a sites column in the dim_asset dimension that lists the sites to which an asset belongs."
}
[/block]
For each fact, a dimensional star or snowflake schema is provided. For brevity and readability, only one level in a snowflake schema is detailed, and only two levels of dimensions are displayed. For more information on the attributes of these dimensions, refer to the Dimensions section below.

When dates are displayed as measures of facts, they will always be converted to match the time zone specified in the report configuration.

Only data from fully completed scans of assets are included in the facts. Results from aborted or interrupted scans will not be included.

###Common measures

It will be helpful to keep in mind some characteristics of certain measures that appear in the following tables.

####asset_compliance

This attribute measures the ratio of assets that are compliant with the policy rule to the total number of assets that were tested for the policy rule.

####assets

This attribute measures the number of assets within a particular level of aggregation.

####compliant_assets

This attribute measures the number of assets that are compliant with the policy rule (taking into account policy rule overrides.)

####exploits

This attribute measures the number of distinct exploit modules that can be used exploit vulnerabilities on each asset. When the level of grain aggregates multiple assets, the total is the summation of the exploits value for each asset. If there are no vulnerabilities found on the asset or there are no vulnerabilities that can be exploited with a exploit module, the count will be zero.

####malware_kits

This attribute measures the number of distinct malware kits that can be used exploit vulnerabilities on each asset. When the level of grain aggregates multiple assets, the total is the summation of the malware kits value for each asset. If there are no vulnerabilities found on the asset or there are no vulnerabilities that can be exploited with a malware kit, the count will be zero.

####noncompliant_assets

This attribute measures the number of assets that are not compliant with the policy rule (taking into account policy rule overrides.)

####not_applicable_assets

This attribute measures the number of assets that are not applicable for the policy rule (taking into account policy rule overrides.)

####riskscore

This attribute measures the risk score of each asset, which is based on the vulnerabilities found on that asset. When the level of grain aggregates multiple assets, the total is the summation of the riskscore value for each asset.

####rule_compliance

This attribute measures the ratio of policy rule test result that are compliant or not applicable to the total number of rule test results.

####vulnerabilities

This attribute measures the number of vulnerabilities discovered on each asset. When the level of grain aggregates multiple assets, the total is the summation of the vulnerabilities on each asset.

If a vulnerability was discovered multiple times on the same asset, it will only be counted once per asset. This count may be zero if no vulnerabilities were found vulnerable on any asset in the latest scan, or if the scan was not configured to perform vulnerability checks (as in the case of discovery scans).

The vulnerabilities count is also provided for each severity level:

* _Critical_: The number of vulnerabilities that are critical.
* _Severe_: The number of vulnerabilities that are severe.
* _Moderate_: The number of vulnerabilities that are moderate.

####vulnerabilities_with_exploit

This attribute measures the total number of a vulnerabilities on all assets that can be exploited with a published exploit module. When the level of grain aggregates multiple assets, the total is the summation of the vulnerabilities_with_exploit value for each asset. This value is guaranteed to be less than the total number of vulnerabilities. If no vulnerabilities are present, or none are subject to an exploit, the value will be zero.

####vulnerabilities_with_malware_kit

This attribute measures the number of vulnerabilities on each asset that are exploitable with a malware kit. When the level of grain aggregates multiple assets, the total is the summation of the vulnerabilities_with_malware_kit value for each asset. This value is guaranteed to be less than the total number of vulnerabilities. If no vulnerabilities are present, or none are subject to a malware kit, the value will be zero.

####vulnerability_instances

This attribute measures the number of occurrences of all vulnerabilities found on each asset. When the level of grain aggregates multiple assets, the total is the summation of the vulnerability_instances value for each asset. This value will count each instance of a vulnerability on each asset. This value may be zero if no instances were tested or found vulnerable (e.g. discover scans).

Attributes with a timestamp datatype, such as a first_discovered, honor the time zone specified in the report configuration.

###fact_all

> _added in version 1.1.0_

**Level of Grain:** The summary of the current state of all assets within the scope of the report.

**Fact Type:** accumulating snapshot

**Description:** Summaries of the latest vulnerability details across the entire report. This is an accumulating snapshot fact that updates after every scan of any asset within the report completes. This fact will include the data for the most recent scan of each asset that is contained within the scope of the report. As the level of aggregation is all assets in the report, this fact table is guaranteed to return one and only one row always.

####Columns
[block:parameters]
{
  "data": {
    "h-0": "Column",
    "h-1": "Data Type",
    "h-2": "Nullable",
    "h-3": "Description",
    "h-4": "Associated Dimension",
    "0-0": "vulnerabilities",
    "0-1": "bigint",
    "0-2": "No",
    "0-3": "The number of vulnerabilities across all assets.",
    "1-0": "critical_vulnerabilities",
    "1-1": "bigint",
    "1-2": "No",
    "1-3": "The number of critical vulnerabilities across all assets.",
    "2-0": "severe_vulnerabilities",
    "2-1": "bigint",
    "2-2": "No",
    "2-3": "The number of severe vulnerabilities across all assets.",
    "3-0": "moderate_vulnerabilities",
    "3-1": "bigint",
    "3-2": "No",
    "3-3": "The number of moderate vulnerabilities across all assets.",
    "4-0": "malware_kits",
    "4-1": "integer",
    "4-2": "No",
    "4-3": "The number of malware kits across all assets.",
    "5-0": "exploits",
    "5-1": "integer",
    "5-2": "No",
    "5-3": "The number of exploit modules across all assets.",
    "6-0": "vulnerabilities_with_malware_kit",
    "6-1": "integer",
    "6-2": "No",
    "6-3": "The number of vulnerabilities with a malware kit across all assets.",
    "7-0": "vulnerabilities_with_exploit",
    "7-1": "integer",
    "7-2": "No",
    "7-3": "The number of vulnerabilities with an exploit module across all assets.",
    "8-0": "vulnerability_instances",
    "8-1": "bigint",
    "8-2": "No",
    "8-3": "The number of vulnerability instances across all assets.",
    "9-0": "riskscore",
    "9-1": "double precision",
    "9-2": "No",
    "9-3": "The risk score across all assets.",
    "10-0": "pci_status",
    "10-1": "text",
    "10-2": "No",
    "10-3": "The PCI compliance status; either Pass or Fail."
  },
  "cols": 5,
  "rows": 11
}
[/block]
 ####Dimensional model
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/e787995-fact_all_v2_v1.1.0.png",
        "fact_all_v2_v1.1.0.png",
        243,
        204,
        "#0f0f0f"
      ],
      "caption": "Dimensional model for fact_all"
    }
  ]
}
[/block]
###fact_asset

**Level of Grain:** An asset and its current summary information.

**Fact Type:** accumulating snapshot

**Description:** The  fact_asset  fact table provides the most recent information for each asset within the scope of the report. For every asset in scope there will be one record in the fact table.

####Columns
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
    "1-0": "last_scan_id",
    "1-1": "bigint",
    "1-2": "No",
    "1-3": "The identifier of the scan with the most recent information being summarized.",
    "1-4": "dim_scan",
    "2-0": "scan_started",
    "2-1": "timestamp with time zone",
    "2-2": "No",
    "2-3": "The date and time at which the latest scan for the asset started.",
    "3-0": "scan_finished",
    "3-1": "timestamp with time zone",
    "3-2": "No",
    "3-3": "The date and time at which the latest scan for the asset completed.",
    "4-0": "vulnerabilities",
    "4-1": "bigint",
    "4-2": "No",
    "4-3": "The number of all distinct vulnerabilities on the asset",
    "5-0": "critical_vulnerabilities",
    "5-1": "bigint",
    "5-2": "No",
    "5-3": "The number of critical vulnerabilities on the asset.",
    "6-0": "severe_vulnerabilities",
    "6-1": "bigint",
    "6-2": "No",
    "6-3": "The number of severe vulnerabilities on the asset.",
    "7-0": "moderate_vulnerabilities",
    "7-1": "bigint",
    "7-2": "No",
    "7-3": "The number of moderate vulnerabilities on the asset.",
    "8-0": "malware_kits",
    "8-1": "integer",
    "8-2": "No",
    "8-3": "The number of malware kits associated with any vulnerabilities discovered on the asset.",
    "9-0": "exploits",
    "9-1": "integer",
    "9-2": "No",
    "9-3": "The number of exploits associated with any vulnerabilities discovered on the asset.",
    "10-0": "vulnerabilities_with_malware_kit",
    "10-1": "integer",
    "10-2": "No",
    "10-3": "The number of vulnerabilities with a known malware kit discovered on the asset.",
    "11-0": "vulnerabilities_with_exploit",
    "11-1": "integer",
    "11-2": "No",
    "11-3": "The number of vulnerabilities with a known exploit discovered on the asset.",
    "12-0": "vulnerability_instances",
    "12-1": "bigint",
    "12-2": "No",
    "12-3": "The number of vulnerability instances discovered on the asset",
    "13-0": "riskscore",
    "13-1": "double precision",
    "13-2": "No",
    "13-3": "The risk score of the asset.",
    "14-0": "pci_status",
    "14-1": "text",
    "14-2": "No",
    "14-3": "The PCI compliance status; either Pass or Fail.",
    "15-0": "aggregated_credential_status_id",
    "15-1": "integer",
    "15-2": "No",
    "15-3": "The status aggregated across all available services for the given asset in the given scan.",
    "15-4": "dim_aggregated_credential_status"
  },
  "cols": 5,
  "rows": 16
}
[/block]
####Dimensional model
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/8f242c8-d_data_model_fact_asset.jpg",
        "d_data_model_fact_asset.jpg",
        1821,
        669,
        "#deddde"
      ],
      "caption": "Dimensional model for fact_asset"
    }
  ]
}
[/block]
###fact_asset_date (startDate, endDate, dateInterval)

> _Added in version 1.1.0_

**Level of Grain:** An asset and its summary information on a specific date.

**Fact Type:** periodic snapshot

**Description:** This fact table provides a periodic snapshot for summarized values on an asset by date. The fact table takes three dynamic arguments, which refine what data is returned. Starting from startDate and ending on endDate, a summarized value for each asset in the scope of the report will be returned for every dateInterval period of time. This will allow trending on asset information by a customizable interval of time. In terms of a chart, startDate represents the lowest value in the range, the endDate the largest value in the range, and the dateInterval is the separation of the ticks of the range axis. If an asset did not exist prior to a summarization date, it will have no record for that date value. The summarized values of an asset represent the state of the asset in the most recent scan prior to the date being summarized; therefore, if an asset has not been scanned before the next summary interval, the values for the asset will remain the same.

For example, fact_asset_date(‘2013-01-01’, ‘2014-01-01’, INTERVAL ‘1 month’) will return a row for each asset for every month in the year 2013.

####Arguments
[block:parameters]
{
  "data": {
    "h-0": "Column",
    "h-1": "Data Type",
    "h-2": "Description",
    "0-0": "startDate",
    "0-1": "date",
    "0-2": "The first date to return summarizations for.",
    "1-0": "endDate",
    "1-1": "date",
    "1-2": "The last date to return summarizations for.",
    "2-0": "dateInterval",
    "2-1": "interval",
    "2-2": "The interval between the start and end date to return summarizations for."
  },
  "cols": 3,
  "rows": 3
}
[/block]
####Columns
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
    "1-0": "last_scan_id",
    "1-1": "bigint",
    "1-2": "No",
    "1-3": "The identifier of the scan with the most recent information being summarized.",
    "1-4": "dim_scan",
    "2-0": "scan_started",
    "2-1": "timestamp with time zone",
    "2-2": "No",
    "2-3": "The date and time at which the latest scan for the asset started.",
    "3-0": "scan_finished",
    "3-1": "timestamp with time zone",
    "3-2": "No",
    "3-3": "The date and time at which the latest scan for the asset completed.",
    "4-0": "vulnerabilities",
    "4-1": "bigint",
    "4-2": "No",
    "4-3": "The number of all distinct vulnerabilities on the asset.",
    "5-0": "critical_vulnerabilities",
    "5-1": "bigint",
    "5-2": "No",
    "5-3": "The number of critical vulnerabilities on the asset.",
    "6-0": "severe_vulnerabilities",
    "6-1": "bigint",
    "6-2": "No",
    "6-3": "The number of severe vulnerabilities on the asset.",
    "7-0": "moderate_vulnerabilities",
    "7-1": "bigint",
    "7-2": "No",
    "7-3": "The number of moderate vulnerabilities on the asset.",
    "8-0": "malware_kits",
    "8-1": "integer",
    "8-2": "No",
    "8-3": "The number of malware kits associated with any vulnerabilities discovered on the asset.",
    "9-0": "exploits",
    "9-1": "integer",
    "9-2": "No",
    "9-3": "The number of exploits associated with any vulnerabilities discovered on the asset.",
    "10-0": "vulnerabilities_with_malware_kit",
    "10-1": "integer",
    "10-2": "No",
    "10-3": "The number of vulnerabilities with a known malware kit discovered on the asset.",
    "11-0": "vulnerabilities_with_exploit",
    "11-1": "integer",
    "11-2": "No",
    "11-3": "The number of vulnerabilities with a known exploit discovered on the asset.",
    "12-0": "vulnerability_instances",
    "12-1": "bigint",
    "12-2": "No",
    "12-3": "The number of vulnerability instances discovered on the asset",
    "13-0": "riskscore",
    "13-1": "double precision",
    "13-2": "No",
    "13-3": "The risk score of the asset.",
    "14-0": "pci_status",
    "14-1": "text",
    "14-2": "No",
    "14-3": "The PCI compliance status; either Pass or Fail.",
    "15-0": "day",
    "15-1": "date",
    "15-2": "No",
    "15-3": "The date of the summarization of the asset."
  },
  "cols": 5,
  "rows": 16
}
[/block]
 ####Dimensional model
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/0d2dc04-d_data_model_fact_asset_date_v1.1.0.jpg",
        "d_data_model_fact_asset_date_v1.1.0.jpg",
        1198,
        512,
        "#e6e6e6"
      ],
      "caption": "Dimensional model for fact_asset_date(startDate, endDate, dateInterval)"
    }
  ]
}
[/block]
###fact_asset_discovery

**Level of Grain:** A snapshot of the discovery dates for an asset.

**Fact Type:** accumulating snapshot

**Description:** The fact_asset_discovery fact table provides an accumulating snapshot for each asset within the scope of the report and details when the asset was first and last discovered. The discovery date is interpreted as the precise time that the asset was first communicated with during a scan, during the discovery phase of the scan. If an asset has only been scanned once both the first_discovered and last_discovered dates will be the same.

####Columns
[block:parameters]
{
  "data": {
    "h-0": "Column",
    "h-1": "Data Type",
    "h-2": "Nullable",
    "h-3": "Description",
    "h-4": "Associated Dimension",
    "0-0": "asset_id",
    "0-1": "big_int",
    "0-2": "No",
    "0-3": "The identifier of the asset.",
    "0-4": "dim_asset",
    "1-0": "first_discovered",
    "1-1": "timestamp without time zone",
    "1-2": "No",
    "1-3": "The date and time the asset was first discovered during any scan.",
    "2-0": "last_discovered",
    "2-1": "timestamp without time zone",
    "2-2": "No",
    "2-3": "The date and time the asset was last discovered during any scan."
  },
  "cols": 5,
  "rows": 3
}
[/block]
####Dimensional model
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/43fced4-d_data_model_dimensional_model.jpg",
        "d_data_model_dimensional_model.jpg",
        730,
        542,
        "#121212"
      ],
      "caption": "Dimensional model for fact_asset_discovery"
    }
  ]
}
[/block]
###fact_asset_group

**Level of Grain:** An asset group and its current summary information.

**Fact Type:** accumulating snapshot

**Description:** The  fact_asset_group fact table provides the most recent information for each asset group within the scope of the report. Every asset group that any asset within the scope of the report is currently a member of will be available within the scope (not just those specified in the configuration of the report). There will be one fact record for every asset group in the scope of the report. As scans are performed against assets, the information in the fact table will accumulate the most recent information for the asset group (including discovery scans).

####Columns
[block:parameters]
{
  "data": {
    "h-0": "Column",
    "h-1": "Data Type",
    "h-2": "Nullable",
    "h-3": "Description",
    "h-4": "Associated Dimension",
    "0-0": "asset_group_id \n(as named in versions 1.2.0 \nand later of the data model) group_id\n(as named in version 1.1.0)",
    "0-1": "bigint",
    "0-2": "No",
    "0-3": "The identifier of the asset group.",
    "0-4": "dim_asset_group",
    "1-0": "assets",
    "1-1": "bigint",
    "1-2": "No",
    "1-3": "The number of distinct assets associated to the asset group. If the asset group contains no assets, the count will be zero.",
    "2-0": "vulnerabilities",
    "2-1": "bigint",
    "2-2": "No",
    "2-3": "The number of all vulnerabilities discovered on assets in the asset group.",
    "3-0": "critical_vulnerabilities",
    "3-1": "bigint",
    "3-2": "No",
    "3-3": "The number of all critical vulnerabilities discovered on assets in the asset group.",
    "4-0": "severe_vulnerabilities",
    "4-1": "bigint",
    "4-2": "No",
    "4-3": "The number of all severe vulnerabilities discovered on assets in the asset group.",
    "5-0": "moderate_vulnerabilities",
    "5-1": "bigint",
    "5-2": "No",
    "5-3": "The number of all moderate vulnerabilities discovered on assets in the asset group.",
    "6-0": "malware_kits",
    "6-1": "integer",
    "6-2": "No",
    "6-3": "The number of malware kits associated with vulnerabilities discovered on assets in the asset group.",
    "7-0": "exploits",
    "7-1": "integer",
    "7-2": "No",
    "7-3": "The number of exploits associated with vulnerabilities discovered on assets in the asset group.",
    "8-0": "vulnerabilities_with_malware_kit",
    "8-1": "integer",
    "8-2": "No",
    "8-3": "The number of vulnerabilities with a known malware kit discovered on assets in the asset group.",
    "9-0": "vulnerabilities_with_exploit",
    "9-1": "integer",
    "9-2": "No",
    "9-3": "The number of vulnerabilities with a known exploit discovered on assets in the asset group.",
    "10-0": "vulnerability_instances",
    "10-1": "bigint",
    "10-2": "No",
    "10-3": "The number of vulnerability instances discovered on assets in the asset group.",
    "11-0": "riskscore",
    "11-1": "double precision",
    "11-2": "No",
    "11-3": "The risk score of the asset group.",
    "12-0": "pci_status",
    "12-1": "text",
    "12-2": "No",
    "12-3": "The PCI compliance status; either Pass or Fail."
  },
  "cols": 5,
  "rows": 13
}
[/block]
####Dimensional model
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/fd41fe5-d_data_model_fact_asset_group.jpg",
        "d_data_model_fact_asset_group.jpg",
        739,
        235,
        "#e6e3e6"
      ],
      "caption": "Dimensional model for fact_asset_group"
    }
  ]
}
[/block]
###fact_asset_group_date (startDate, endDate, dateInterval)

> _Added in version 1.1.0_

**Level of Grain:** An asset group and its summary information on a specific date.

**Fact Type:** periodic snapshot

**Description:** This fact table provides a periodic snapshot for summarized values on an asset group by date. The fact table takes three dynamic arguments, which refine what data is returned. Starting from startDate and ending on endDate, a summarized value for each asset group in the scope of the report will be returned for every dateInterval period of time. This will allow trending on asset group information by a customizable interval of time. In terms of a chart, startDate represents the lowest value in the range, the endDate the largest value in the range, and the dateInterval is the separation of the ticks of the range axis. If an asset group did not exist prior to a summarization date, it will have no record for that date value. The summarized values of an asset group represent the state of the asset group prior to the date being summarized; therefore, if the assets in an asset group have not been scanned before the next summary interval, the values for the asset group will remain the same.

For example, fact_asset_group_date(‘2013-01-01’, ‘2014-01-01’, INTERVAL ‘1 month’) will return a row for each asset group for every month in the year 2013.

####Arguments
[block:parameters]
{
  "data": {
    "h-0": "Column",
    "h-1": "Data Type",
    "h-2": "Description",
    "0-0": "startDate",
    "0-1": "date",
    "0-2": "The first date to return summarizations for.",
    "1-0": "endDate",
    "1-1": "date",
    "1-2": "The last date to return summarizations for.",
    "2-0": "dateInterval",
    "2-1": "interval",
    "2-2": "The interval between the start and end date to return summarizations for."
  },
  "cols": 3,
  "rows": 3
}
[/block]
####Columns
[block:parameters]
{
  "data": {
    "h-0": "Column",
    "h-1": "Data Type",
    "h-2": "Nullable",
    "h-3": "Description",
    "h-4": "Associated Dimension",
    "0-0": "group_id",
    "0-1": "bigint",
    "0-2": "No",
    "0-3": "The identifier of the asset group.",
    "0-4": "dim_asset_group",
    "1-0": "assets",
    "1-1": "bigint",
    "1-2": "No",
    "1-3": "The number of distinct assets associated to the asset group. If the asset group contains no assets, the count will be zero.",
    "2-0": "vulnerabilities",
    "2-1": "bigint",
    "2-2": "No",
    "2-3": "The number of all vulnerabilities discovered on assets in the asset group.",
    "3-0": "critical_vulnerabilities",
    "3-1": "bigint",
    "3-2": "No",
    "3-3": "The number of all critical vulnerabilities discovered on assets in the asset group.",
    "4-0": "severe_vulnerabilities",
    "4-1": "bigint",
    "4-2": "No",
    "4-3": "The number of all severe vulnerabilities discovered on assets in the asset group.",
    "5-0": "moderate_vulnerabilities",
    "5-1": "bigint",
    "5-2": "No",
    "5-3": "The number of all moderate vulnerabilities discovered on assets in the asset group.",
    "6-0": "malware_kits",
    "6-1": "integer",
    "6-2": "No",
    "6-3": "The number of malware kits associated with vulnerabilities discovered on assets in the asset group.",
    "7-0": "exploits",
    "7-1": "integer",
    "7-2": "No",
    "7-3": "The number of exploits associated with vulnerabilities discovered on assets in the asset group.",
    "8-0": "vulnerabilities_with_malware_kit",
    "8-1": "integer",
    "8-2": "No",
    "8-3": "The number of vulnerabilities with a known malware kit discovered on assets in the asset group.",
    "9-0": "vulnerabilities_with_exploit",
    "9-1": "integer",
    "9-2": "No",
    "9-3": "The number of vulnerabilities with a known exploit discovered on assets in the asset group.",
    "10-0": "vulnerability_instances",
    "10-1": "bigint",
    "10-2": "No",
    "10-3": "The number of vulnerability instances discovered on assets in the asset group.",
    "11-0": "riskscore",
    "11-1": "double precision",
    "11-2": "No",
    "11-3": "The risk score of the asset group.",
    "12-0": "pci_status",
    "12-1": "text",
    "12-2": "No",
    "12-3": "The PCI compliance status; either Pass or Fail.",
    "13-0": "day",
    "13-1": "date",
    "13-2": "No",
    "13-3": "The date of the summarization of the asset."
  },
  "cols": 5,
  "rows": 14
}
[/block]
####Dimensional model
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/38fb27d-d_dimensional_model_fact_asset_group_date_v1.1.0.jpg",
        "d_dimensional_model_fact_asset_group_date_v1.1.0.jpg",
        758,
        281,
        "#090909"
      ],
      "caption": "Dimensional model for fact_asset_group_date"
    }
  ]
}
[/block]
###fact_asset_group_policy_date

> _added in version 1.3.0_

**Type:** Periodic snapshot

**Description:** This fact table provides a periodic snapshot for summarized policy values on an asset group by date. The fact table takes three dynamic arguments, which refine what data is returned. Starting from startDate and ending on endDate, the summarized policy value for each asset group in the scope of the report will be returned for every dateInterval period of time. This will allow trending on asset group information by a customizable interval of time. In terms of a chart, startDate represents the lowest value in the range, the endDate the largest value in the range, and the dateInterval is the separation of the ticks of the range axis. If an asset group did not exist prior to a summarization date, it will have no record for that date value. The summarized policy values of an asset group represent the state of the asset group prior to the date being summarized; therefore, if the assets in an asset group have not been scanned before the next summary interval, the values for the asset group will remain the same.

####Arguments
[block:parameters]
{
  "data": {
    "h-0": "Column",
    "h-1": "Data Type",
    "h-2": "Nullable",
    "h-3": "Description",
    "0-0": "startDate",
    "0-1": "date",
    "0-2": "No",
    "0-3": "The first date to return summarizations for.",
    "1-0": "endDate",
    "1-1": "date",
    "1-2": "No",
    "1-3": "The last date to return summarizations for.",
    "2-0": "dateInterval",
    "2-1": "interval",
    "2-2": "No",
    "2-3": "The interval between the start and end date to return summarizations for."
  },
  "cols": 4,
  "rows": 3
}
[/block]
####Columns
[block:parameters]
{
  "data": {
    "h-0": "Column",
    "h-1": "Data Type",
    "h-2": "Nullable",
    "h-3": "Description",
    "h-4": "Associated Dimension",
    "0-0": "group_id",
    "0-1": "bigint",
    "0-2": "Yes",
    "0-3": "The unique identifier of the asset group.",
    "0-4": "dim_asset",
    "1-0": "day",
    "1-1": "date",
    "1-2": "No",
    "1-3": "The date which the summarized policy scan results snapshot is taken.",
    "2-0": "policy_id",
    "2-1": "bigint",
    "2-2": "Yes",
    "2-3": "The unique identifier of the policy within a scope.",
    "2-4": "dim_scan",
    "3-0": "scope",
    "3-1": "text",
    "3-2": "Yes",
    "3-3": "The identifier for scope of policy. Policies that are automatically available have \"Built-in\" scope, whereas policies created by users have scope as \"Custom\".",
    "3-4": "dim_policy",
    "4-0": "assets",
    "4-1": "integer",
    "4-2": "Yes",
    "4-3": "The total number of assets that are in the scope of the report and associated to the asset group.",
    "5-0": "compliant_assets",
    "5-1": "integer",
    "5-2": "Yes",
    "5-3": "The number of assets associated to the asset group that have not failed any while passed at least one policy rule test.",
    "6-0": "noncompliant_assets",
    "6-1": "integer",
    "6-2": "Yes",
    "6-3": "The number of assets associated to the asset group that have failed at least one policy rule test.",
    "7-0": "not_applicable_assets",
    "7-1": "integer",
    "7-2": "Yes",
    "7-3": "The number of assets associated to the asset group that have neither failed nor passed at least one policy rule test.",
    "8-0": "rule_compliance",
    "8-1": "numeric",
    "8-2": "Yes",
    "8-3": "The ratio of rule test results that are compliant with or not applicable to the total number of rule test results."
  },
  "cols": 5,
  "rows": 9
}
[/block]
###fact_asset_policy

> _added in version 1.2.0_

**Level of Grain:** A policy result on an asset

**Fact Type:** accumulating snapshot

**Description:** This table provides an accumulating snapshot of policy test results on an asset. It displays a record for each policy that was tested on an asset in its most recent scan. Only policies scanned within the scope of report are included.

####Columns
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
    "1-0": "last_scan_id",
    "1-1": "bigint",
    "1-2": "No",
    "1-3": "The identifier of the scan",
    "1-4": "dim_scan",
    "2-0": "policy_id",
    "2-1": "bigint",
    "2-2": "No",
    "2-3": "The identifier of the policy",
    "2-4": "dim_policy",
    "3-0": "scope",
    "3-1": "text",
    "3-2": "No",
    "3-3": "The identifier for scope of policy. Policies that are automatically available have \"Built-in\" scope, whereas policies created by users have scope as \"Custom\".",
    "4-0": "date_tested",
    "4-1": "timestamp without timezone",
    "4-3": "The end date and time for the scan of the asset that was tested for the policy, in the time zone specified in the report configuration.",
    "5-0": "compliant_rules",
    "5-1": "bigint",
    "5-3": "The total number of each policy's rules in which all assets are compliant with the most recent scan.",
    "6-0": "noncompliant_rules",
    "6-1": "bigint",
    "6-3": "The total number of each policy's rules which at least one asset failed in the most recent scan.",
    "7-0": "not_applicable_rules",
    "7-1": "bigint",
    "7-3": "The total number of each policy's rules that were not applicable to the asset in the most recent scan.",
    "8-0": "rule_compliance",
    "8-1": "numeric",
    "8-3": "The ratio of policy rule test result that are compliant or not applicable to the total number of rule test results."
  },
  "cols": 5,
  "rows": 9
}
[/block]
####Dimensional model
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/410e441-d_data_model_fact_asset_scan_service.jpg",
        "d_data_model_fact_asset_scan_service.jpg",
        1817,
        654,
        "#dfdedf"
      ],
      "caption": "Dimensional model for fact_asset_policy"
    }
  ]
}
[/block]
###fact_asset_policy_date

> _added in version 1.3.0_

**Type:** Periodic snapshot

**Description:** This fact table provides a periodic snapshot for summarized policy values on an asset by date. The fact table takes three dynamic arguments, which refine what data is returned. Starting from startDate and ending on endDate, the summarized policy value for each asset in the scope of the report will be returned for every dateInterval period of time. This will allow trending on asset information by a customizable interval of time. In terms of a chart, startDate represents the lowest value in the range, the endDate the largest value in the range, and the dateInterval is the separation of the ticks of the range axis. If an asset did not exist prior to a summarization date, it will have no record for that date value. The summarized policy values of an asset represent the state of the asset prior to the date being summarized; therefore, if the assets in an asset group have not been scanned before the next summary interval, the values for the asset will remain the same.

####Arguments
[block:parameters]
{
  "data": {
    "h-0": "Column",
    "h-1": "Data Type",
    "h-2": "Nullable",
    "h-3": "Description",
    "0-0": "startDate",
    "0-1": "date",
    "0-2": "No",
    "0-3": "The first date to return summarizations for.",
    "1-0": "endDate",
    "1-1": "date",
    "1-2": "No",
    "1-3": "The last date to return summarizations for.",
    "2-0": "dateInterval",
    "2-1": "interval",
    "2-2": "No",
    "2-3": "The interval between the start and end date to return summarizations for."
  },
  "cols": 4,
  "rows": 3
}
[/block]
####Columns
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
    "0-2": "Yes",
    "0-3": "The unique identifier of the asset.",
    "0-4": "dim_asset",
    "1-0": "day",
    "1-1": "date",
    "1-2": "No",
    "1-3": "The date which the summarized policy scan results snapshot is taken.",
    "2-0": "scan_id",
    "2-1": "bigint",
    "2-2": "Yes",
    "2-3": "The unique identifier of the scan.",
    "2-4": "dim_scan",
    "3-0": "policy_id",
    "3-1": "bigint",
    "3-2": "Yes",
    "3-3": "The unique identifier of the policy within a scope.",
    "3-4": "dim_policy",
    "4-0": "scope",
    "4-1": "text",
    "4-2": "Yes",
    "4-3": "The identifier for scope of policy. Policies that are automatically available have \"Built-in\" scope, whereas policies created by users have scope as \"Custom\".",
    "5-0": "date_tested",
    "5-1": "timestamp without time zone",
    "5-2": "Yes",
    "5-3": "The time the asset was tested with the policy rules.",
    "6-0": "compliant_rules",
    "6-1": "integer",
    "6-2": "Yes",
    "6-3": "The number of rules that all assets are compliant with in the scan.",
    "7-0": "noncompliant_rules",
    "7-1": "integer",
    "7-2": "Yes",
    "7-3": "The number of rules that at least one asset failed in the scan.",
    "8-0": "not_applicable_rules",
    "8-1": "integer",
    "8-2": "Yes",
    "8-3": "The number of rules that are not applicable to the asset.",
    "9-0": "rule_compliance",
    "9-1": "numeric",
    "9-2": "Yes",
    "9-3": "The ratio of rule test results that are compliant or not applicable to the total number of rule test results."
  },
  "cols": 5,
  "rows": 10
}
[/block]
###fact_asset_policy_rule

> _added in version 1.3.0_

**Level of Grain:** A policy rule result on an asset

**Fact Type:** accumulating snapshot

**Description:** This table provides the rule results of the most recent policy scan for an asset within the scope of the report. For each rule, only assets that are subject to that rule and that have a result in the most recent scan are counted.

####Columns
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
    "1-0": "policy_id",
    "1-1": "bigint",
    "1-2": "No",
    "1-3": "The identifier of the policy",
    "1-4": "dim_policy",
    "2-0": "scope",
    "2-1": "text",
    "2-2": "No",
    "2-3": "The identifier for scope of policy. Policies that are automatically available have \"Built-in\" scope, whereas policies created by users have scope as \"Custom\".",
    "3-0": "rule_id",
    "3-1": "bigint",
    "3-2": "No",
    "3-3": "The identifier of the policy rule.",
    "3-4": "dim_policy_rule",
    "4-0": "scan_id",
    "4-1": "bigint",
    "4-2": "No",
    "4-3": "The identifier of the scan",
    "4-4": "dim_scan",
    "5-0": "date_tested",
    "5-1": "timestamp without timezone",
    "5-3": "The end date and time for the scan of the asset that was tested for the policy, in the time zone specified in the report configuration.",
    "6-0": "status_id",
    "6-1": "character(1)",
    "6-2": "No",
    "6-3": "The identifier of the status for the policy rule finding on the asset (taking into account policy rule overrides.)",
    "6-4": "dim_policy_rule_status",
    "7-0": "compliance",
    "7-1": "boolean",
    "7-2": "No",
    "7-3": "Whether the asset is compliant with the rule. True if and only if all of the policy checks for this rule have not failed, or the rule is overridden with the value true on the asset.",
    "8-0": "proof",
    "8-1": "text",
    "8-2": "Yes",
    "8-3": "The proof of the policy checks on the asset.",
    "9-0": "override_id",
    "9-1": "bigint",
    "9-2": "Yes",
    "9-3": "The unique identifier of the policy rule override that is applied to the rule on an asset. If multiple overrides apply to the rule at different levels of scope, the identifier of the override having the true effect on the rule (latest override) is returned.",
    "9-4": "dim_policy_rule_override",
    "10-0": "override_ids",
    "10-1": "bigint[]",
    "10-2": "Yes",
    "10-3": "The unique identifiers of the policy rule override that are applied to the rule on an asset. If multiple overrides apply to the rule at different levels of scope, the identifier of each override is returned in a comma-separated list.",
    "10-4": "dim_policy_rule_override"
  },
  "cols": 5,
  "rows": 11
}
[/block]
####Dimensional model
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/62be711-d_data_model_fact_asset_policy_rule.jpg",
        "d_data_model_fact_asset_policy_rule.jpg",
        1179,
        565,
        "#1b1c36"
      ],
      "caption": "Dimensional model for fact_policy_rule"
    }
  ]
}
[/block]
###fact_asset_scan

**Level of Grain:** A summary of a completed scan of an asset.

**Fact Type:** transaction

**Description:** The fact_asset_scan transaction fact provides summary information of the results of a scan for an asset. A fact record will be present for every asset and scan in which the asset was fully scanned in. Only assets configured within the scope of the report and vulnerabilities filtered within the report will take part in the accumulated totals. If no vulnerabilities checks were performed during the scan, for example as a result of a discovery scan, the vulnerability related counts will be zero.

####Columns
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
    "0-4": "dim_scan",
    "1-0": "asset_id",
    "1-1": "bigint",
    "1-2": "No",
    "1-3": "The identifier of the asset.",
    "1-4": "dim_asset",
    "2-0": "scan_started",
    "2-1": "timestamp without time zone",
    "2-2": "No",
    "2-3": "The time at which the scan for the asset was started.",
    "3-0": "scan_finished",
    "3-1": "timestamp without time zone",
    "3-2": "No",
    "3-3": "The time at which the scan for the asset completed.",
    "4-0": "vulnerabilities",
    "4-1": "bigint",
    "4-2": "No",
    "4-3": "The number of vulnerabilities found on the asset during the scan.",
    "5-0": "critical_vulnerabilities",
    "5-1": "bigint",
    "5-2": "No",
    "5-3": "The number of critical vulnerabilities found on the asset during the scan.",
    "6-0": "severe_vulnerabilities",
    "6-1": "bigint",
    "6-2": "No",
    "6-3": "The number of severe vulnerabilities found on the asset during the scan.",
    "7-0": "moderate_vulnerabilities",
    "7-1": "bigint",
    "7-2": "No",
    "7-3": "The number of moderate vulnerabilities found on the asset during the scan.",
    "8-0": "malware_kits",
    "8-1": "integer",
    "8-2": "No",
    "8-3": "The number of malware kits associated with vulnerabilities discovered during the scan.",
    "9-0": "exploits",
    "9-1": "integer",
    "9-2": "No",
    "9-3": "The number of exploits associated with vulnerabilities discovered during the scan.",
    "10-0": "vulnerabilities_with_malware_kit",
    "10-1": "integer",
    "10-2": "No",
    "10-3": "The number of vulnerabilities with a known malware kit discovered during the scan.",
    "11-0": "vulnerabilities_with_exploit",
    "11-1": "integer",
    "11-2": "No",
    "11-3": "The number of vulnerabilities with a known exploit discovered during the scan.",
    "12-0": "vulnerability_instances",
    "12-1": "bigint",
    "12-2": "No",
    "12-3": "The number of vulnerability instances found discovered during the scan.",
    "13-0": "riskscore",
    "13-1": "double precision",
    "13-2": "No",
    "13-3": "The risk score for the scan.",
    "14-0": "pci_status",
    "14-1": "text",
    "14-2": "No",
    "14-3": "The PCI compliance status; either Pass or Fail.",
    "15-0": "aggregated_credential_status_id",
    "15-1": "integer",
    "15-2": "No",
    "15-3": "The status aggregated across all available services for the given asset in the given scan.",
    "15-4": "dim_aggregated_credential_status"
  },
  "cols": 5,
  "rows": 16
}
[/block]
####Dimensional model
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/54a9bcf-d_data_model_fact_asset_scan.jpg",
        "d_data_model_fact_asset_scan.jpg",
        1800,
        646,
        "#e0dee0"
      ],
      "caption": "Dimensional model for fact_asset_scan"
    }
  ]
}
[/block]
###fact_asset_scan_operating_system

**Level of Grain:** An operating system fingerprint on an asset in a scan.

**Fact Type:** transaction

**Description:** The fact_asset_operating_system fact table provides the operating systems fingerprinted on an asset in a scan. The operating system fingerprints represent all the potential fingerprints collected during a scan that can be chosen as the primary or best operating system fingerprint on the asset. If an asset had no fingerprint acquired during a scan, it will have a record with values indicating an unknown fingerprint.

####Columns
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
    "0-3": "The identifier of the asset the operating system is associated to.",
    "0-4": "dim_asset",
    "1-0": "scan_id",
    "1-1": "bigint",
    "1-2": "No",
    "1-3": "The identifier of the scan the asset was fingerprinted in.",
    "1-4": "dim_scan",
    "2-0": "operating_system_id",
    "2-1": "bigint",
    "2-2": "No",
    "2-3": "The identifier of the operating system that was fingerprinted on the asset in the scan. If a fingerprint was not found, the value will be -1.",
    "2-4": "dim_operating_system",
    "3-0": "fingerprint_source_id",
    "3-1": "integer",
    "3-2": "No",
    "3-3": "The identifier of the source that was used to acquire the fingerprint. If a fingerprint was not found, the value will be -1.",
    "3-4": "dim_fingerprint_source",
    "4-0": "certainty",
    "4-1": "real",
    "4-2": "No",
    "4-3": "A value between 0 and 1 that represents the confidence level of the fingerprint. If a fingerprint was not found, the value will be 0."
  },
  "cols": 5,
  "rows": 5
}
[/block]
####Dimensional model
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/fff608e-d_data_model_dimensional_model_2.jpg",
        "d_data_model_dimensional_model_2.jpg",
        1241,
        522,
        "#161516"
      ],
      "caption": "Dimensional model for fact_asset_scan_operating_system"
    }
  ]
}
[/block]
###fact_asset_scan_policy 

> _Available in version 1.2.0_

**Level of Grain:** A policy result for an asset in a scan

**Fact Type:** transaction

**Description:** This table provides the details of policy test results on an asset during a scan. Each record provides the policy test results for an asset for a specific scan. Only policies within the scope of report are included.

####Columns
[block:callout]
{
  "type": "info",
  "body": "As of version 1.3.0, passed_rules and failed_rules are now called compliant_rules and noncompliant_rules."
}
[/block]

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
    "1-0": "scan_id",
    "1-1": "bigint",
    "1-2": "No",
    "1-3": "The identifier of the scan",
    "1-4": "dim_scan",
    "2-0": "policy_id",
    "2-1": "bigint",
    "2-2": "No",
    "2-3": "The identifier of the policy",
    "2-4": "dim_policy",
    "3-0": "scope",
    "3-1": "text",
    "3-2": "No",
    "3-3": "The identifier for scope of policy. Policies that are automatically available have \"Built-in\" scope, whereas policies created by users have scope as \"Custom\".",
    "4-0": "date_tested",
    "4-1": "timestamp without timezone",
    "4-3": "The end date and time for the scan of the asset that was tested for the policy, in the time zone specified in the report configuration.",
    "5-0": "compliant_rules",
    "5-1": "bigint",
    "5-3": "The total number of each policy's rules for which the asset passed in the most recent scan.",
    "6-0": "noncompliant_rules",
    "6-1": "bigint",
    "6-3": "The total number of each policy's rules for which the asset failed in the most recent scan.",
    "7-0": "not_applicable_rules",
    "7-1": "bigint",
    "7-3": "The total number of each policy's rules that were not applicable to the asset in the most recent scan.",
    "8-0": "rule_compliance",
    "8-1": "numeric",
    "8-3": "The ratio of policy rule test result that are compliant or not applicable to the total number of rule test results."
  },
  "cols": 5,
  "rows": 9
}
[/block]
####Dimensional model
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/95110e2-d_data_model_fact_asset_scan_policy.jpg",
        "d_data_model_fact_asset_scan_policy.jpg",
        1213,
        580,
        "#e3e3e3"
      ],
      "caption": "Dimensional model for fact_asset_scan_policy"
    }
  ]
}
[/block]
###fact_asset_scan_software

**Level of Grain:** A fingerprint for an installed software on an asset in a scan.

**Fact Type:** transaction

**Description:** The fact_asset_scan_software fact table provides the installed software packages enumerated or detected during a scan of an asset. If an asset had no software packages enumerated in a scan there will be no records in this fact.

####Columns
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
    "1-0": "scan_id",
    "1-1": "bigint",
    "1-2": "No",
    "1-3": "The identifier of the scan",
    "1-4": "dim_scan",
    "2-0": "software_id",
    "2-1": "bigint",
    "2-2": "No",
    "2-3": "The identifier of the software fingerprinted.",
    "2-4": "dim_software",
    "3-0": "fingerprint_source_id",
    "3-1": "bigint",
    "3-2": "No",
    "3-3": "The identifier of the source used to fingerprint the software.",
    "3-4": "dim_fingerprint_source"
  },
  "cols": 5,
  "rows": 4
}
[/block]
####Dimensional model
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/d5c160b-d_data_model_fact_asset_scan_software.jpg",
        "d_data_model_fact_asset_scan_software.jpg",
        1200,
        513,
        "#191819"
      ],
      "caption": "Dimensional model for fact_asset_scan_software"
    }
  ]
}
[/block]
####fact_asset_scan_service

**Level of Grain:** A service detected on an asset in a scan.

**Fact Type:** transaction

**Description:** The  fact_asset_scan_service  fact table provides the services detected during a scan of an asset. If an asset had no services enumerated in a scan there will be no records in this fact. 

####Columns
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
    "1-0": "scan_id",
    "1-1": "bigint",
    "1-2": "No",
    "1-3": "The identifier of the scan.",
    "1-4": "dim_scan",
    "2-0": "date",
    "2-1": "timestamp without time zone",
    "2-2": "No",
    "2-3": "The date and time at which the service was enumerated.",
    "3-0": "service_id",
    "3-1": "integer",
    "3-2": "No",
    "3-3": "The identifier of the service.",
    "3-4": "dim_service",
    "4-0": "protocol_id",
    "4-1": "smallint",
    "4-2": "No",
    "4-3": "The identifier of the protocol the service was utilizing.",
    "4-4": "dim_protocol",
    "5-0": "port",
    "5-1": "integer",
    "5-2": "No",
    "5-3": "The port the service was running on.",
    "6-0": "service_fingerprint_id",
    "6-1": "bigint",
    "6-2": "No",
    "6-3": "The identifier of the fingerprint of the service describing the configuration of the service.",
    "6-4": "dim_service_fingerprint",
    "7-0": "credential_status_id",
    "7-1": "smallint",
    "7-2": "No",
    "7-3": "The result of the user-provided credentials per asset per scan per service. Services for which credential status is assessed are: SNMP, SSH, Telnet and CIFS.",
    "7-4": "dim_credential_status"
  },
  "cols": 5,
  "rows": 8
}
[/block]
####Dimensional model
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/d19af97-d_data_model_fact_asset_scan_service.jpg",
        "d_data_model_fact_asset_scan_service.jpg",
        1817,
        654,
        "#dfdedf"
      ],
      "caption": "Dimensional model for fact_asset_scan_service"
    }
  ]
}
[/block]
###fact_asset_scan_vulnerability_finding

> _Added in version 1.1.0_

**Level of Grain:** A vulnerability finding on an asset in a scan.

**Fact Type:** transaction

**Description:** This fact tables provides an accumulating snapshot for all vulnerability findings on an asset in every scan of the asset. This table will display a record for each unique vulnerability discovered on each asset in the every scan of the asset. If multiple occurrences of the same vulnerability are found on the asset, they will be rolled up into a single row with a vulnerability_instances count greater than one. Only vulnerabilities with no active exceptions applies will be displayed.

####Dimensional model
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/9859867-d_data_model_fact_asset_vuln_finding_v1.1.0.jpg",
        "d_data_model_fact_asset_vuln_finding_v1.1.0.jpg",
        1350,
        689,
        "#161616"
      ],
      "caption": "Dimensional model for fact_asset_scan_vulnerability_finding"
    }
  ]
}
[/block]
###fact_asset_scan_vulnerability_instance

> _added in version 1.1.0_

**Level of Grain:** A vulnerability instance on an asset in a scan.

**Fact Type:** transaction

**Description:**  The > fact_asset_scan_vulnerability_instance  fact table provides the details of a vulnerability instance discovered during a scan of an asset. Only vulnerability instances found to be vulnerable and with no exceptions actively applied will be present within the fact table. A vulnerability instance is a unique vulnerability result found discovered on the asset. If the multiple occurrences of the same vulnerability are found on the asset, one row will be present for each instance.

####Columns
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
    "1-0": "scan_id",
    "1-1": "bigint",
    "1-2": "No",
    "1-3": "The identifier of the scan.",
    "1-4": "dim_scan",
    "2-0": "vulnerability_id",
    "2-1": "integer",
    "2-2": "No",
    "2-3": "The identifier of the vulnerability the finding is for.",
    "2-4": "dim_vulnerability",
    "3-0": "date",
    "3-1": "timestamp without time zone",
    "3-2": "No",
    "3-3": "The date and time at which the vulnerability finding was detected. This time is the time at which the asset completed scanning during the scan.",
    "4-0": "status_id",
    "4-1": "character(1)",
    "4-2": "No",
    "4-3": "The identifier of the status of the vulnerability finding that indicates the level of confidence of the finding.",
    "4-4": "dim_vulnerability_status",
    "5-0": "proof",
    "5-1": "text",
    "5-2": "No",
    "5-3": "The proof indicating the reason that the vulnerability exists. The proof is exposed in formatting markup that can be striped using the function _proofAsText_",
    "5-4": "",
    "6-0": "key",
    "6-1": "text",
    "6-2": "Yes",
    "6-3": "The secondary identifier of the vulnerability finding that discriminates the result from similar results of the same vulnerability on the same asset. This value is optional and will be null when a vulnerability does not need a secondary discriminator.",
    "7-0": "service_id",
    "7-1": "integer",
    "7-2": "No",
    "7-3": "The service the vulnerability was discovered on, or -1 if the vulnerability is not associated with a service.",
    "7-4": "dim_service",
    "8-0": "port",
    "8-1": "integer",
    "8-2": "No",
    "8-3": "The port on which the vulnerable service was running, or -1 if the vulnerability is not associated with a service",
    "9-0": "protocol_id",
    "9-1": "integer",
    "9-2": "No",
    "9-3": "The protocol the vulnerable service was running, or -1 if the vulnerability is not associated with a service.",
    "9-4": "dim_protocol"
  },
  "cols": 5,
  "rows": 10
}
[/block]
####Dimensional model
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/0afcfdd-d_data_model_fact_asset_scan_vuln_instance_v1.1.0.jpg",
        "d_data_model_fact_asset_scan_vuln_instance_v1.1.0.jpg",
        1366,
        754,
        "#171717"
      ],
      "caption": "Dimensional model for fact_asset_scan_vulnerability_instance"
    }
  ]
}
[/block]
###fact_asset_scan_vulnerability_instance_excluded

> _added in version 1.1.0_

**Level of Grain:** A vulnerability instance on an asset in a scan with an active vulnerability exception applied.

**Fact Type:** transaction

**Description:** The  fact_asset_scan_vulnerability_instance_excluded  fact table provides the details of a vulnerability instance discovered during a scan of an asset with an exception applied. Only vulnerability instances found to be vulnerable and with exceptions actively applied will be present within the fact table. If the multiple occurrences of the same vulnerability are found on the asset, one row will be present for each instance.

####Columns
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
    "1-0": "scan_id",
    "1-1": "bigint",
    "1-2": "No",
    "1-3": "The identifier of the scan.",
    "1-4": "dim_scan",
    "2-0": "vulnerability_id",
    "2-1": "integer",
    "2-2": "No",
    "2-3": "The identifier of the vulnerability.",
    "2-4": "dim_vulnerability",
    "3-0": "date",
    "3-1": "timestamp without time zone",
    "3-2": "No",
    "3-3": "The date and time at which the vulnerability finding was detected. This time is the time at which the asset completed scanning during the scan.",
    "4-0": "status_id",
    "4-1": "character(1)",
    "4-2": "No",
    "4-3": "The identifier of the status of the vulnerability finding that indicates the level of confidence of the finding.",
    "4-4": "dim_vulnerability_status",
    "5-0": "proof",
    "5-1": "text",
    "5-2": "No",
    "5-3": "The proof indicating the reason that the vulnerability exists. The proof is exposed in formatting markup that can be striped using the function \n_proofAsText_",
    "6-0": "key",
    "6-1": "text",
    "6-2": "Yes",
    "6-3": "The secondary identifier of the vulnerability finding that discriminates the result from similar results of the same vulnerability on the same asset. This value is optional and will be null when a vulnerability does not need a secondary discriminator.",
    "7-0": "service_id",
    "7-1": "integer",
    "7-2": "No",
    "7-3": "The service the vulnerability was discovered on, or -1 if the vulnerability is not associated with a service.",
    "7-4": "dim_service",
    "8-0": "port",
    "8-1": "integer",
    "8-2": "No",
    "8-3": "The port on which the vulnerable service was running, or -1 if the vulnerability is not associated with a service.",
    "9-0": "protocol_id",
    "9-1": "integer",
    "9-2": "No",
    "9-3": "The protocol the vulnerable service was running, or -1 if the vulnerability is not associated with a service.",
    "9-4": "dim_protocol"
  },
  "cols": 5,
  "rows": 10
}
[/block]
####Dimensional model
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/3c2cbe3-fact_asset_scan_vulnerability_exception_v1.1.0.png",
        "fact_asset_scan_vulnerability_exception_v1.1.0.png",
        1366,
        752,
        "#e7e7e7"
      ],
      "caption": "Dimensional model for fact_asset_scan_vulnerability_instance_excluded"
    }
  ]
}
[/block]
###fact_asset_vulnerability_age

> _Added in version 1.2.0_

**Level of Grain:** A vulnerability on an asset.

**Fact Type:** accumulating snapshot

**Description:** This fact table provides an accumulating snapshot for vulnerability age and occurrence information on an asset. For every vulnerability to which an asset is currently vulnerable, there will be one fact record. The record indicates when the vulnerability was first found, last found, and its current age. The age is computed as the difference between the time the vulnerability was first discovered on the asset, and the current time. If the vulnerability was temporarily remediated, but rediscovered, the age will be from the first discovery time. If a vulnerability was found on a service, remediated and discovered on another service, the age is still computed as the first time the vulnerability was found on any service on the asset.

####Columns
[block:parameters]
{
  "data": {
    "h-0": "Column",
    "h-1": "Data Type",
    "h-2": "Nullable",
    "h-3": "Desription",
    "h-4": "Associated Dimension",
    "0-0": "asset_id",
    "0-1": "bigint",
    "0-2": "No",
    "0-3": "The unique identifier of the asset.",
    "0-4": "dim_asset",
    "1-0": "vulnerability_id",
    "1-1": "integer",
    "1-2": "No",
    "1-3": "The unique identifier of the vulnerability.",
    "1-4": "dim_vulnerability",
    "2-0": "age",
    "2-1": "interval",
    "2-2": "No",
    "2-3": "The age of the vulnerability on the asset, in the interval format.",
    "3-0": "age_in_days",
    "3-1": "numeric",
    "3-2": "No",
    "3-3": "The age of the vulnerability on the asset, specified in days.",
    "4-0": "first_discovered",
    "4-1": "timestamp without timezone",
    "4-2": "No",
    "4-3": "The date on which the vulnerability was first discovered on the asset.",
    "5-0": "most_recently_discovered",
    "5-1": "timestamp without timezone",
    "5-2": "No",
    "5-3": "The date on which the vulnerability was most recently discovered on the asset."
  },
  "cols": 5,
  "rows": 6
}
[/block]
###fact_asset_vulnerability_finding
> _Added in version 1.2.0_

**Level of Grain:** A vulnerability finding on an asset.

**Fact Type:** accumulating snapshot

**Description:** This fact tables provides an accumulating snapshot for all current vulnerability findings on an asset. This table will display a record for each unique vulnerability discovered on each asset in the most recent scan of the asset. If multiple occurrences of the same vulnerability are found on the asset, they will be rolled up into a single row with a vulnerability_instances count greater than one. Only vulnerabilities with no active exceptions applies will be displayed.

####Columns
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
    "1-0": "scan_id",
    "1-1": "bigint",
    "1-2": "No",
    "1-3": "The identifier of the last scan for the asset in which the vulnerability was detected.",
    "1-4": "dim_scan",
    "2-0": "vulnerability_id",
    "2-1": "integer",
    "2-2": "No",
    "2-3": "The identifier of the vulnerability.",
    "2-4": "dim_vulnerability",
    "3-0": "vulnerability_instances",
    "3-1": "bigint",
    "3-2": "No",
    "3-3": "The number of occurrences of the vulnerability detected on the asset, guaranteed to be greater than or equal to one.",
    "4-0": "vulnerability_instances",
    "4-1": "bigint",
    "4-2": "No",
    "4-3": "The number of occurrences of the vulnerability detected on the asset, guaranteed to be greater than or equal to one."
  },
  "cols": 5,
  "rows": 5
}
[/block]
####Dimensional model
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/7d08886-d_data_model_fact_asset_vuln_finding_v1.1.0.jpg",
        "d_data_model_fact_asset_vuln_finding_v1.1.0.jpg",
        1350,
        689,
        "#161616"
      ],
      "caption": "Dimensional model for fact_asset_vulnerability_finding"
    }
  ]
}
[/block]
###fact_asset_vulnerability_instance

**Level of Grain:** A vulnerability instance on an asset.

**Fact Type:** accumulating snapshot

**Description:** This table provides an accumulating snapshot for all current vulnerability instances on an asset. Only vulnerability instance found to be vulnerable and with no exceptions actively applied will be present within the fact table. If the multiple occurrences of the same vulnerability are found on the asset, a row will be present for each instance.

####Columns
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
    "1-0": "scan_id",
    "1-1": "bigint",
    "1-2": "No",
    "1-3": "The identifier of the scan the vulnerability instance was found in.",
    "1-4": "dim_scan",
    "2-0": "vulnerability_id",
    "2-1": "integer",
    "2-2": "No",
    "2-3": "The identifier of the vulnerability.",
    "2-4": "dim_vulnerability",
    "3-0": "vulnerability_exception_id",
    "3-1": "integer",
    "3-2": "Yes",
    "3-3": "The unique identifier of a vulnerability exception that is pending for the vulnerability instance. If a vulnerability instance has no pending exceptions, this value will be null. If multiple pending exceptions apply to the vulnerability at different levels of scope, the identifier of the exception at the lowest (most fine-grained) level is returned.",
    "3-4": "dim_vulnerability_exception",
    "4-0": "vulnerability_exception_ids",
    "4-1": "text",
    "4-2": "Yes",
    "4-3": "The unique identifiers of all vulnerability exceptions that are pending for the vulnerability instance. If a vulnerability instance has no pending exceptions, this value will be null. If multiple pending exceptions apply to the vulnerability at different levels of scope, then the the identifier of all exceptions will be returned in a comma-separated value string.",
    "4-4": "dim_vulnerability_exception",
    "5-0": "date",
    "5-1": "timestamp without time zone",
    "5-2": "No",
    "5-3": "The date and time at which the vulnerability finding was detected. This time is the time at which the asset completed scanning during the scan.",
    "6-0": "status_id",
    "6-1": "character(1)",
    "6-2": "No",
    "6-3": "The identifier of the status of the vulnerability finding that indicates the level of confidence of the finding.",
    "6-4": "dim_vulnerability_status",
    "7-0": "proof",
    "7-1": "text",
    "7-2": "No",
    "7-3": "The proof indicating the reason that the vulnerability exists. The proof is exposed in formatting markup that can be striped using the function _proofAsText_",
    "8-0": "key",
    "8-1": "text",
    "8-2": "Yes",
    "8-3": "The secondary identifier of the vulnerability finding that discriminates the result from similar results of the same vulnerability on the same asset. This value is optional and will be null when a vulnerability does not need a secondary discriminator.",
    "9-0": "service_id",
    "9-1": "integer",
    "9-2": "No",
    "9-3": "The service the vulnerability was discovered on, or -1 if the vulnerability is not associated with a service.",
    "9-4": "dim_service",
    "10-0": "port",
    "10-1": "integer",
    "10-2": "No",
    "10-3": "The port on which the vulnerable service was running, or -1 if the vulnerability is not associated with a service.",
    "11-0": "protocol_id",
    "11-1": "integer",
    "11-2": "No",
    "11-3": "The protocol the vulnerable service was running, or -1 if the vulnerability is not associated with a service.",
    "11-4": "dim_protocol"
  },
  "cols": 5,
  "rows": 12
}
[/block]
####Dimensional model
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/e27fac4-fact_asset_vulnerability_v1.1.0.png",
        "fact_asset_vulnerability_v1.1.0.png",
        1357,
        709,
        "#e7e7e7"
      ],
      "caption": "Dimensional model for fact_asset_vulnerability"
    }
  ]
}
[/block]
###fact_asset_vulnerability_instance_excluded

**Level of Grain:** A vulnerability instance on an asset with an active vulnerability exception applied.

**Fact Type:** accumulating snapshot

**Description:** The fact_asset_vunerability_instance_excluded   fact table provides an accumulating snapshot for all current vulnerability instances on an asset.  If the multiple occurrences of the same vulnerability are found on the asset, a row will be present for each instance.

####Columns
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
    "1-0": "vulnerability_id",
    "1-1": "integer",
    "1-2": "No",
    "1-3": "The identifier of the vulnerability.",
    "1-4": "dim_vulnerability",
    "2-0": "date_tested",
    "2-1": "timestamp without time zone",
    "2-2": "No",
    "2-3": "The date and time at which the vulnerability finding was detected. This time is the time at which the asset completed scanning during the scan.",
    "3-0": "status_id",
    "3-1": "character(1)",
    "3-2": "No",
    "3-3": "The identifier of the status of the vulnerability finding that indicates the level of confidence of the finding.",
    "3-4": "dim_vulnerability_status",
    "4-0": "proof",
    "4-1": "text",
    "4-2": "No",
    "4-3": "The proof indicating the reason that the vulnerability exists. The proof is exposed in formatting markup that can be striped using the function _proofAsText_",
    "5-0": "key",
    "5-1": "text",
    "5-2": "Yes",
    "5-3": "The secondary identifier of the vulnerability finding that discriminates the result from similar results of the same vulnerability on the same asset. This value is optional and will be null when a vulnerability does not need a secondary discriminator.",
    "6-0": "service_id",
    "6-1": "integer",
    "6-2": "No",
    "6-3": "The service the vulnerability was discovered on, or -1 if the vulnerability is not associated with a service.",
    "6-4": "dim_service",
    "7-0": "port",
    "7-1": "integer",
    "7-3": "The port on which the vulnerable service was running, or -1 if the vulnerability is not associated with a service.",
    "7-2": "No",
    "8-0": "protocol_id",
    "8-1": "integer",
    "8-2": "No",
    "8-3": "The protocol the vulnerable service was running, or -1 if the vulnerability is not associated with a service.",
    "8-4": "dim_protocol"
  },
  "cols": 5,
  "rows": 9
}
[/block]
####Dimensional model
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/cf7e11b-fact_asset_vulnerability_exception_v1.1.0.png",
        "fact_asset_vulnerability_exception_v1.1.0.png",
        1366,
        747,
        "#e7e7e7"
      ],
      "caption": "Dimensional model for fact_asset_vulnerability_exception"
    }
  ]
}
[/block]
###fact_pci_asset_scan_service_finding

> _added in version 1.3.2_

**Level of Grain:** A service finding on an asset in a scan.

**Fact Type:** Transaction

**Description:** The  fact_pci_asset_scan_service_finding  table is the transaction fact for a service finding on an asset for a scan. This fact provides a record for each service on every asset within the scope of the report for every scan it was included in. The level of grain is a unique service finding. If no services were found on an asset in a scan, it will have no records in this fact table. For PCI purposes, each service finding is mapped to a vulnerability. Services for which a version was fingerprinted are mapped to an additional vulnerability.

####Columns
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
    "0-3": "The unique identifier of the asset.",
    "0-4": "dim_asset",
    "1-0": "scan_id",
    "1-1": "bigint",
    "1-2": "No",
    "1-3": "The unique identifier of the scan the service finding was found in.",
    "1-4": "dim_scan",
    "2-0": "service_id",
    "2-1": "integer",
    "2-2": "No",
    "2-3": "The identifier of the definition of the service.",
    "2-4": "dim_service",
    "3-0": "vulnerability_id",
    "3-1": "integer",
    "3-2": "No",
    "3-3": "The unique identifier of the vulnerability.",
    "3-4": "dim_vulnerability",
    "4-0": "protocol_id",
    "4-1": "smallint",
    "4-2": "No",
    "4-3": "The identifier of the protocol the service was utilizing.",
    "4-4": "dim_protocol",
    "5-0": "port",
    "5-1": "integer",
    "5-2": "No",
    "5-3": "The port the service was running on."
  },
  "cols": 5,
  "rows": 6
}
[/block]
###fact_pci_asset_service_finding

> _added in version 1.3.2_

**Level of Grain:** A service finding on an asset from the latest scan of the asset.

**Fact Type:** Accumulating snapshot

**Description:** The  fact_pci_asset_service_finding  fact table provides an accumulating snapshot fact for all service findings on an asset for the latest scan of every asset. The level of grain is a unique service finding. If no services were found on an asset in a scan, it will have no records in this fact table. For PCI purposes, each service finding is mapped to a vulnerability. Services for which a version was fingerprinted are mapped to an additional vulnerability.

####Columns
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
    "0-3": "The unique identifier of the asset.",
    "0-4": "dim_asset",
    "1-0": "scan_id",
    "1-1": "bigint",
    "1-2": "No",
    "1-3": "The unique identifier of the scan the service finding was found in.",
    "1-4": "dim_scan",
    "2-0": "service_id",
    "2-1": "integer",
    "2-2": "No",
    "2-3": "The identifier of the definition of the service.",
    "2-4": "dim_service",
    "3-0": "vulnerability_id",
    "3-1": "integer",
    "3-2": "No",
    "3-3": "The unique identifier of the vulnerability.",
    "3-4": "dim_vulnerability",
    "4-0": "protocol_id",
    "4-1": "smallint",
    "4-2": "No",
    "4-3": "The identifier of the protocol the service was utilizing.",
    "4-4": "dim_protocol",
    "5-0": "port",
    "5-1": "integer",
    "5-2": "No",
    "5-3": "The port the service was running on."
  },
  "cols": 5,
  "rows": 6
}
[/block]
###fact_pci_asset_special_note

> _added in version 1.3.2_

**Level of Grain:** A note finding on a vulnerability or service on an asset (plus port and protocol, if applicable) from the latest scan of the asset.

**Fact Type:** Accumulating snapshot

**Description:** The  fact_pci_asset_special_note  fact table provides an accumulating snapshot fact for all vulnerability or service findings with applied special notes on an asset for the latest scan of every asset. The level of grain is a unique vulnerability or service finding, determined by asset, port and protocol.

####Columns
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
    "0-3": "The unique identifier of the asset.",
    "0-4": "dim_asset",
    "1-0": "scan_id",
    "1-1": "bigint",
    "1-2": "No",
    "1-3": "The unique identifier of the scan.",
    "1-4": "dim_scan",
    "2-0": "service_id",
    "2-1": "integer",
    "2-2": "No",
    "2-3": "The identifier of the definition of the service.",
    "2-4": "dim_service",
    "3-0": "protocol_id",
    "3-1": "smallint",
    "3-2": "No",
    "3-3": "The identifier of the protocol the service was utilizing.",
    "3-4": "dim_protocol",
    "4-0": "port",
    "4-1": "integer",
    "4-2": "No",
    "4-3": "The port the service was running on.",
    "5-0": "pci_note_id",
    "5-1": "integer",
    "5-2": "No",
    "5-3": "The unique identifier of the pci special note applied to the vulnerability or service finding.",
    "5-4": "dim_pci_note",
    "6-0": "items_noted",
    "6-1": "text",
    "6-2": "No",
    "6-3": "A list of distinct identifiers for findings on a given asset, port, and protocol."
  },
  "cols": 5,
  "rows": 7
}
[/block]
###fact_policy
> _added in version 1.2.0_

**Level of Grain:** A summary of findings related to a policy.

**Fact Type:** accumulating snapshot 

**Description:** This table provides a summary for the results of the most recent policy scan for assets within the scope of the report. For each policy, only assets that are subject to that policy's rules and that have a result in the most recent scan with no overrides are counted.

####Columns
[block:callout]
{
  "type": "info",
  "body": "As of version 1.3.0, a separate value has been created for not_applicable_assets and is no longer included in compliant_assets."
}
[/block]

[block:parameters]
{
  "data": {
    "h-0": "Column",
    "h-1": "Data Type",
    "h-2": "Nullable",
    "h-3": "Description",
    "h-4": "Associated Dimension",
    "0-0": "policy_id",
    "0-1": "bigint",
    "0-2": "No",
    "0-3": "The identifier of the policy.",
    "0-4": "dim_policy",
    "1-0": "scope",
    "1-1": "text",
    "1-2": "No",
    "1-3": "The identifier for scope of policy. Policies that are automatically available have \"Built-in\" scope, whereas policies created by users have scope as \"Custom\".",
    "2-0": "rule_compliance",
    "2-1": "numeric",
    "2-2": "No",
    "2-3": "The ratio of policy rule test result that are compliant or not applicable to the total number of rule test results.",
    "3-0": "total_assets",
    "3-1": "bigint",
    "3-2": "No",
    "3-3": "The number of assets within the scope of the report that were tested for the policy.",
    "4-0": "compliant_assets",
    "4-1": "bigint",
    "4-2": "No",
    "4-3": "The number of assets that did not fail but passed at least a rule within the policy in the last test.",
    "5-0": "non_compliant_assets",
    "5-1": "bigint",
    "5-2": "No",
    "5-3": "The number of assets that failed at least one rule within the policy in the last test.",
    "6-0": "not_applicable_assets",
    "6-1": "bigint",
    "6-2": "No",
    "6-3": "The number of assets that neither passed nor failed at least a rule within the policy in the last test.",
    "7-0": "asset_compliance",
    "7-1": "numeric",
    "7-2": "No",
    "7-3": "The ratio of assets that are compliant with the policy to the total number of assets that were tested for the policy."
  },
  "cols": 5,
  "rows": 8
}
[/block]
####Dimensional model
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/d77f393-d_data_model_fact_policy.jpg",
        "d_data_model_fact_policy.jpg",
        681,
        318,
        "#191919"
      ],
      "caption": "Dimensional model for fact_policy"
    }
  ]
}
[/block]
###fact_policy_group

> _added in version 1.3.0_

**Level of Grain:** A summary of findings related to a policy group.

**Fact Type:** accumulating snapshot

**Description:** This table provides a summary for the group rules's results of the most recent policy scan for assets within the scope of the report. All rules that are directly or indirectly descend from it and are counted.

####Columns
[block:parameters]
{
  "data": {
    "h-0": "Column",
    "h-1": "Data Type",
    "h-2": "Nullable",
    "h-3": "Description",
    "0-0": "scope",
    "h-4": "Associated Dimension",
    "0-1": "text",
    "0-2": "No",
    "0-3": "The identifier for scope of policy. Policies that are automatically available have \"Built-in\" scope, whereas policies created by users have scope as \"Custom\".",
    "1-0": "policy_id",
    "1-1": "bigint",
    "1-2": "No",
    "1-3": "The identifier of the policy.",
    "1-4": "dim_policy",
    "2-0": "group_id",
    "2-1": "bigint",
    "2-2": "No",
    "2-3": "The identifier of the policy group.",
    "2-4": "dim_policy_group",
    "3-0": "non_compliant_rules",
    "3-1": "integer",
    "3-2": "No",
    "3-3": "The number of rules that doesn't have 100% asset compliance (taking into account policy rule overrides.)",
    "4-0": "compliant_rules",
    "4-1": "integer",
    "4-2": "No",
    "4-3": "The number of rules that have 100% asset compliance (taking into account policy rule overrides.)",
    "5-0": "rule_compliance",
    "5-1": "numeric",
    "5-2": "True",
    "5-3": "The ratio of rule test result that are compliant or not applicable to the total number of rule test results within the policy group. If the group has no rule or no testable rules (rule with no check, hence no result exists), this will have a null value."
  },
  "cols": 5,
  "rows": 6
}
[/block]
####Dimensional model


[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/3a3fd92-d_data_model_fact_policy_group.jpg",
        "d_data_model_fact_policy_group.jpg",
        579,
        403,
        "#ebf3ea"
      ],
      "caption": "Dimensional model for fact_policy_group"
    }
  ]
}
[/block]
###fact_policy_rule

> _added in version 1.3.0_

**Level of Grain:** A summary of findings related to a policy rule.

**Fact Type:** accumulating snapshot

**Description:** This table provides a summary for the rule results of the most recent policy scan for assets within the scope of the report. For each rule, only assets that are subject to that rule and that have a result in the most recent scan are counted.

####Columns
[block:parameters]
{
  "data": {
    "h-0": "Column",
    "h-1": "Data Type",
    "h-2": "Nullable",
    "h-3": "Description",
    "h-4": "Associated Dimension",
    "0-0": "scope",
    "0-1": "text",
    "0-2": "No",
    "0-3": "The identifier for scope of policy. Policies that are automatically available have \"Built-in\" scope, whereas policies created by users have scope as \"Custom\".",
    "1-0": "policy_id",
    "1-1": "bigint",
    "1-2": "No",
    "1-3": "The identifier of the policy.",
    "1-4": "dim_policy",
    "2-0": "rule_id",
    "2-1": "bigint",
    "2-2": "No",
    "2-3": "The identifier of the policy rule.",
    "2-4": "dim_policy_rule",
    "3-0": "compliant_assets",
    "3-1": "integer",
    "3-2": "No",
    "3-3": "The number of assets that are compliant with the rule (taking into account policy rule overrides.)",
    "4-0": "noncompliant_assets",
    "4-1": "integer",
    "4-2": "No",
    "4-3": "The number of assets that are not compliant with the rule (taking into account policy rule overrides.)",
    "5-0": "not_applicable_asset",
    "5-1": "integer",
    "5-2": "No",
    "5-3": "The number of assets that are not applicable for the rule (taking into account policy rule overrides.)",
    "6-0": "asset_compliance",
    "6-1": "numeric",
    "6-2": "No",
    "6-3": "The ratio of assets that are compliant with the policy rule to the total number of assets that were tested for the policy rule."
  },
  "cols": 5,
  "rows": 7
}
[/block]
####Dimensional model
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/03c317b-d_data_model_fact_policy_rule.jpg",
        "d_data_model_fact_policy_rule.jpg",
        725,
        359,
        "#eaf0ea"
      ],
      "caption": "Dimensional model for fact_policy_rule"
    }
  ]
}
[/block]
###fact_remediation (count, sort_column)

> _added in version 1.1.0_

**Level of Grain:** A solution with the highest level of supercedence and the effect applying that solution would have on the scope of the report.

**Fact Type:** accumulating snapshot

**Description:** A function which returns a result set of the top "count" solutions showing their impact as specified by the sorting criteria. The criteria can be used to find solutions that have a desirable impact on the scope of the report, and can be limited to a subset of all solutions. The aggregate effect of applying each solution is computed and returned for each record. Only the highest-level superceding solutions will be selected, in other words, only solutions which have no superceding solution.

####Arguments
[block:parameters]
{
  "data": {
    "h-0": "Column",
    "h-1": "Data Type",
    "h-2": "Description",
    "0-0": "count",
    "0-1": "integer",
    "0-2": "The number of solutions to limit the output of this function to. The sorting and aggregation are performed prior to the limit.",
    "1-0": "sort_column",
    "1-1": "text",
    "1-2": "The name and sort order of the column to sort results by. Any column within the fact can be used to sort the results prior to them being limited. Multiple columns can be sorted using a traditional SQL fragment (Example: 'assets DESC, exploits DESC')."
  },
  "cols": 3,
  "rows": 2
}
[/block]
####Columns
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
    "1-0": "assets",
    "1-1": "bigint",
    "1-2": "No",
    "1-3": "The number of assets that require the solution to be applied. If the solution applies to a vulnerability not detected on any asset, the value may be zero.",
    "2-0": "vulnerabilities",
    "2-1": "numeric",
    "2-2": "No",
    "2-3": "The total number of vulnerabilities that would be remediated.",
    "3-0": "critical_vulnerabilities",
    "3-1": "numeric",
    "3-2": "No",
    "3-3": "The total number of critical vulnerabilities that would be remediated.",
    "4-0": "severe_vulnerabilities",
    "4-1": "numeric",
    "4-2": "No",
    "4-3": "The total number of severe vulnerabilities that would be remediated.",
    "5-0": "moderate_vulnerabilities",
    "5-1": "numeric",
    "5-2": "No",
    "5-3": "The total number of moderate vulnerabilities that would be remediated.",
    "6-0": "malware_kits",
    "6-1": "integer",
    "6-2": "No",
    "6-3": "The total number of malware kits that would no longer be used to exploit vulnerabilities if the solution were applied.",
    "7-0": "exploits",
    "7-1": "integer",
    "7-2": "No",
    "7-3": "The total number of exploits that could no longer be used to exploit vulnerabilities if the solution were applied.",
    "8-0": "vulnerabilities_with_malware_kit",
    "8-1": "integer",
    "8-2": "No",
    "8-3": "The total number of vulnerabilities with a known malware kit that would remediated by the solution.",
    "9-0": "vulnerabilities_with_exploit",
    "9-1": "integer",
    "9-2": "No",
    "9-3": "The total number of vulnerabilities with a published exploit module that would remediated by the solution.",
    "10-0": "vulnerability_instances",
    "10-1": "numeric",
    "10-2": "No",
    "10-3": "The total number of occurrences of any vulnerabilities that are remediated by the solution.",
    "11-0": "riskscore",
    "11-1": "double precision",
    "11-2": "No",
    "11-3": "The risk score that is reduced by performing the remediation.",
    "12-0": "pci_status",
    "12-1": "text",
    "12-2": "No",
    "12-3": "The PCI compliance status; either Pass or Fail."
  },
  "cols": 5,
  "rows": 13
}
[/block]
####Dimensional model

 
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/17d547a-fact_remediation_relationships_v1.1.0_495x184.png",
        "fact_remediation_relationships_v1.1.0_495x184.png",
        495,
        184,
        "#e6e6e6"
      ],
      "caption": "Dimensional model for fact_remediation(count, sort_column)"
    }
  ]
}
[/block]
###fact_remediation_impact (count, sort_column)

> _added in version 1.1.0_

**Level of Grain:** A solution with the highest level of supercedence and the affect applying that solution would have on the scope of the report.

**Fact Type:** accumulating snapshot

**Description:** Fact that provides a summarization of the impact that applying a subset of all remediations would have on the scope of the report. The criteria can be used to find solutions that have a desirable impact on the scope of the report, and can be limited to a subset of all solutions. The aggregate effect of applying all solutions is computed and returned as a single record. This fact will be guaranteed to return one and only one record.

####Arguments
[block:parameters]
{
  "data": {
    "h-0": "Column",
    "h-1": "Data Type",
    "h-2": "Description",
    "0-0": "count",
    "0-1": "integer",
    "0-2": "The number of solutions to determine the impact for. The sorting and aggregation are performed prior to the limit.",
    "1-0": "sort_column",
    "1-1": "text",
    "1-2": "The name and sort order of the column to sort results by. Any column within the fact can be used to sort the results prior to them being limited. Multiple columns can be sorted using a traditional SQL fragment (Example: 'assets DESC, exploits DESC')."
  },
  "cols": 3,
  "rows": 2
}
[/block]
####Columns
[block:parameters]
{
  "data": {
    "h-0": "Column",
    "h-1": "Data Type",
    "h-2": "Nullable",
    "h-3": "Description",
    "h-4": "Associated Dimension",
    "0-0": "solutions",
    "0-1": "integer",
    "0-2": "No",
    "0-3": "The number of solutions selected and for which the remediation impact is being summarized (will be less than or equal to count).",
    "1-0": "assets",
    "1-1": "bigint",
    "1-2": "No",
    "1-3": "The total number of assets that require a remediation to be applied.",
    "2-0": "vulnerabilities",
    "2-1": "bigint",
    "2-2": "No",
    "2-3": "The total number of vulnerabilities that would be remediated.",
    "3-0": "critical_vulnerabilities",
    "3-1": "bigint",
    "3-2": "No",
    "3-3": "The total number of critical vulnerabilities that would be remediated.",
    "4-0": "severe_vulnerabilities",
    "4-1": "bigint",
    "4-2": "No",
    "4-3": "The total number of severe vulnerabilities that would be remediated.",
    "5-0": "moderate_vulnerabilities",
    "5-1": "bigint",
    "5-2": "No",
    "5-3": "The total number of moderate vulnerabilities that would be remediated.",
    "6-0": "malware_kits",
    "6-1": "integer",
    "6-2": "No",
    "6-3": "The total number of malware kits that would no longer be used to exploit vulnerabilities if all selected remediations were applied.",
    "7-0": "exploits",
    "7-1": "integer",
    "7-2": "No",
    "7-3": "The total number of exploits that would no longer be used to exploit vulnerabilities if all selected remediations were applied.",
    "8-0": "vulnerabilities_with_malware_kit",
    "8-1": "integer",
    "8-2": "No",
    "8-3": "The number of vulnerabilities with a known malware kit that would be remediated.",
    "9-0": "vulnerabilities_with_exploit",
    "9-1": "integer",
    "9-2": "No",
    "9-3": "The number of vulnerabilities with a known exploit that would be remediated.",
    "10-0": "vulnerability_instances",
    "10-1": "bigint",
    "10-2": "No",
    "10-3": "The total number of occurrences of any vulnerabilities that are remediated by any remediation selected.",
    "11-0": "riskscore",
    "11-1": "double precision",
    "11-2": "No",
    "11-3": "The risk score that is reduced by performing all the selected remediations.",
    "12-0": "pci_status",
    "12-1": "text",
    "12-2": "No",
    "12-3": "The PCI compliance status; either Pass or Fail."
  },
  "cols": 5,
  "rows": 13
}
[/block]
####Dimensional model
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/81895da-fact_remediation_impact_v1.1.0.png",
        "fact_remediation_impact_v1.1.0.png",
        281,
        263,
        "#0e0e0e"
      ],
      "caption": "Dimensional model for fact_remediation_impact(count, sort_column)"
    }
  ]
}
[/block]
####fact_scan

**Level of Grain:** A summary of the results of a scan.

**Fact Type:** accumulating snapshot

**Description:** The  fact_scan fact provides the summarized information for every scan any asset within the scope of the report was scanned during. For each scan, there will be a record in this fact table with the summarized results.

####Columns
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
    "0-3": "The identifier of the scan",
    "0-4": "dim_scan",
    "1-0": "assets",
    "1-1": "bigint",
    "1-2": "No",
    "1-3": "The number of assets that were scanned",
    "2-0": "vulnerabilities",
    "2-1": "bigint",
    "2-2": "No",
    "2-3": "The number of all vulnerabilities discovered in the scan.",
    "3-0": "critical_vulnerabilities",
    "3-1": "bigint",
    "3-2": "No",
    "3-3": "The number of all critical vulnerabilities discovered in the scan.",
    "4-0": "severe_vulnerabilities",
    "4-1": "bigint",
    "4-2": "No",
    "4-3": "The number of all severe vulnerabilities discovered in the scan.",
    "5-0": "moderate_vulnerabilities",
    "5-1": "bigint",
    "5-2": "No",
    "5-3": "The number of all moderate vulnerabilities discovered in the scan.",
    "6-0": "malware_kits",
    "6-1": "integer",
    "6-2": "No",
    "6-3": "The number of malware kits associated with vulnerabilities discovered in the scan.",
    "7-0": "exploits",
    "7-1": "integer",
    "7-2": "No",
    "7-3": "The number of exploits associated with vulnerabilities discovered in the scan.",
    "8-0": "vulnerabilities_with_malware_kit",
    "8-1": "integer",
    "8-2": "No",
    "8-3": "The number of vulnerabilities with a malware kit discovered in the scan.",
    "9-0": "vulnerabilities_with_exploit",
    "9-1": "integer",
    "9-2": "No",
    "9-3": "The number of vulnerabilities with an exploit discovered in the scan.",
    "10-0": "vulnerability_instances",
    "10-1": "bigint",
    "10-2": "No",
    "10-3": "The number of vulnerability instances discovered during the scan.",
    "11-0": "riskscore",
    "11-1": "double precision",
    "11-2": "No",
    "11-3": "The risk score for the scan results",
    "12-0": "pci_status",
    "12-1": "text",
    "12-2": "No",
    "12-3": "The PCI compliance status; either Pass or Fail."
  },
  "cols": 5,
  "rows": 13
}
[/block]
####Dimensional model
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/418c5e1-d_data_model_fact_scan_.png",
        "d_data_model_fact_scan_.png",
        686,
        274,
        "#e7e7e7"
      ],
      "caption": "Dimensional model for fact_scan"
    }
  ]
}
[/block]
###fact_site

**Level of Grain:** A summary of the current state of a site.

**Fact Type:** accumulating snapshot

**Description:** The  fact_site table provides a summary record at the level of grain for every site that any asset in the scope of the report belongs to. For each site, there will be a record in this fact table with the summarized results, taking into account any vulnerability filters specified in the report configuration. The summary of each site will display the accumulated information for the most recent scan of each asset, not just the most recent scan of the site.

####Columns
[block:parameters]
{
  "data": {
    "h-0": "Column",
    "h-1": "Data Type",
    "h-2": "Nullable",
    "h-3": "Description",
    "h-4": "Associated Dimension",
    "0-0": "site_id",
    "0-1": "bigint",
    "0-2": "No",
    "0-3": "The identifier of the site.",
    "0-4": "dim_site",
    "1-0": "assets",
    "1-1": "bigint",
    "1-2": "No",
    "1-3": "The total number of assets in the site.",
    "2-0": "last_scan_id",
    "2-1": "bigint",
    "2-2": "No",
    "2-3": "The identifier of the most recent scan for the site.",
    "3-0": "vulnerabilities",
    "3-1": "bigint",
    "3-2": "No",
    "3-3": "The number of vulnerabilities discovered on assets in the site.",
    "4-0": "critical_vulnerabilities",
    "4-1": "bigint",
    "4-2": "No",
    "4-3": "The number of critical vulnerabilities discovered on assets in the site.",
    "5-0": "severe_vulnerabilities",
    "5-1": "bigint",
    "5-2": "No",
    "5-3": "The number of severe vulnerabilities discovered on assets in the site.",
    "6-0": "moderate_vulnerabilities",
    "6-1": "bigint",
    "6-2": "No",
    "6-3": "The number of moderate vulnerabilities discovered on assets in the site.",
    "7-0": "malware_kits",
    "7-1": "integer",
    "7-2": "No",
    "7-3": "The number malware kits associated with vulnerabilities discovered on assets in the site.",
    "8-0": "exploits",
    "8-1": "integer",
    "8-2": "No",
    "8-3": "The number exploits associated with vulnerabilities discovered on assets in the site.",
    "9-0": "vulnerabilities_with_malware_kit",
    "9-1": "integer",
    "9-2": "No",
    "9-3": "The number of vulnerabilities with a malware kit discovered on assets in the site.",
    "10-0": "vulnerabilities_with_exploit",
    "10-1": "integer",
    "10-2": "No",
    "10-3": "The number of vulnerabilities with an exploit kit discovered on assets in the site.",
    "11-0": "vulnerability_instances",
    "11-1": "bigint",
    "11-2": "No",
    "11-3": "The number of vulnerability instances discovered on assets in the site.",
    "12-0": "riskscore",
    "12-1": "double precision",
    "12-2": "No",
    "12-3": "The risk score of the site.",
    "13-0": "pci_status",
    "13-1": "text",
    "13-2": "No",
    "13-3": "The PCI compliance status; either Pass or Fail."
  },
  "cols": 5,
  "rows": 14
}
[/block]
####Dimensional model
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/6fd5101-d_data_model_fact_site.jpg",
        "d_data_model_fact_site.jpg",
        667,
        307,
        "#eae7ea"
      ],
      "caption": "Dimensional model for fact_site"
    }
  ]
}
[/block]
####fact_site_date (startDate, endDate, dateInterval)

> _Added in version 1.1.0_

**Level of Grain:** A site and its summary information on a specific date.

**Fact Type:** periodic snapshot

**Description:** This fact table provides a periodic snapshot for summarized values on a site by date. The fact table takes three dynamic arguments, which refine what data is returned. Starting from startDate and ending on endDate, a summarized value for each site in the scope of the report will be returned for every dateInterval period of time. This will allow trending on site information by a customizable interval of time. In terms of a chart, startDate represents the lowest value in the range, the endDate the largest value in the range, and the dateInterval is the separation of the ticks of the range axis. If a site did not exist prior to a summarization date, it will have no record for that date value. The summarized values of a site represent the state of the site in the most recent scans prior to the date being summarized; therefore, if a site has not been scanned before the next summary interval, the values for the site will remain the same.

For example, fact_site_date(‘2013-01-01’, ‘2014-01-01’, INTERVAL ‘1 month’) will return a row for each site for every month in the year 2013.

####Arguments
[block:parameters]
{
  "data": {
    "h-0": "Column",
    "h-1": "Data Type",
    "h-2": "Description",
    "0-0": "startDate",
    "0-1": "date",
    "0-2": "The first date to return summarizations for.",
    "1-0": "endDate",
    "1-1": "date",
    "1-2": "The last date to return summarizations for.",
    "2-0": "dateInterval",
    "2-1": "interval",
    "2-2": "The interval between the start and end date to return summarizations for."
  },
  "cols": 3,
  "rows": 3
}
[/block]
####Columns
[block:parameters]
{
  "data": {
    "h-0": "Column",
    "h-1": "Data Type",
    "h-2": "Nullable",
    "h-3": "Description",
    "h-4": "Associated Dimension",
    "0-0": "site_id",
    "0-1": "bigint",
    "0-2": "No",
    "0-3": "The identifier of the site.",
    "0-4": "dim_site",
    "1-0": "assets",
    "1-1": "bigint",
    "1-2": "No",
    "1-3": "The total number of assets in the site.",
    "2-0": "last_scan_id",
    "2-1": "bigint",
    "2-2": "No",
    "2-3": "The identifier of the most recent scan for the site.",
    "3-0": "vulnerabilities",
    "3-1": "bigint",
    "3-2": "No",
    "3-3": "The number of vulnerabilities discovered on assets in the site.",
    "4-0": "critical_vulnerabilities",
    "4-1": "bigint",
    "4-2": "No",
    "4-3": "The number of critical vulnerabilities discovered on assets in the site.",
    "5-0": "severe_vulnerabilities",
    "5-1": "bigint",
    "5-2": "No",
    "5-3": "The number of severe vulnerabilities discovered on assets in the site.",
    "6-0": "moderate_vulnerabilities",
    "6-1": "bigint",
    "6-2": "No",
    "6-3": "The number of moderate vulnerabilities discovered on assets in the site.",
    "7-0": "malware_kits",
    "7-1": "integer",
    "7-2": "No",
    "7-3": "The number malware kits associated with vulnerabilities discovered on assets in the site.",
    "8-0": "exploits",
    "8-1": "integer",
    "8-2": "No",
    "8-3": "The number exploits associated with vulnerabilities discovered on assets in the site.",
    "9-0": "vulnerabilities_with_malware_kit",
    "9-1": "integer",
    "9-2": "No",
    "9-3": "The number of vulnerabilities with a malware kit discovered on assets in the site.",
    "10-0": "vulnerabilities_with_exploit",
    "10-1": "integer",
    "10-2": "No",
    "10-3": "The number of vulnerabilities with an exploit kit discovered on assets in the site.",
    "11-0": "vulnerability_instances",
    "11-1": "bigint",
    "11-2": "No",
    "11-3": "The number of vulnerability instances discovered on assets in the site.",
    "12-0": "riskscore",
    "12-1": "double precision",
    "12-2": "No",
    "12-3": "The risk score of the site.",
    "13-0": "pci_status",
    "13-1": "text",
    "13-2": "No",
    "13-3": "The PCI compliance status; either Pass or Fail.",
    "14-0": "day",
    "14-1": "date",
    "14-2": "No",
    "14-3": "The date of the summarization of the asset"
  },
  "cols": 5,
  "rows": 15
}
[/block]
####Dimensional model
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/0ddbd07-d_data_model_fact_site_date_v1.1.0.jpg",
        "d_data_model_fact_site_date_v1.1.0.jpg",
        679,
        339,
        "#dfdfdf"
      ],
      "caption": "Dimensional model for fact_site_date(startDate, endDate, dateInterval)"
    }
  ]
}
[/block]
###fact_site_policy_date

> _added in version 1.3.0_

**Type:** Periodic snapshot

**Description:** This fact table provides a periodic snapshot for summarized policy values on site by date. The fact table takes three dynamic arguments, which refine what data is returned. Starting from startDate and ending on endDate, the summarized policy value for each site in the scope of the report will be returned for every dateInterval period of time. This will allow trending on site information by a customizable interval of time. In terms of a chart, startDate represents the lowest value in the range, the endDate the largest value in the range, and the dateInterval is the separation of the ticks of the range axis. If a site did not exist prior to a summarization date, it will have no record for that date value. The summarized policy values of a site represent the state of the site prior to the date being summarized; therefore, if the site has not been scanned before the next summary interval, the values for the site will remain the same.

####Arguments
[block:parameters]
{
  "data": {
    "h-0": "Column",
    "h-1": "Data Type",
    "h-2": "Nullable",
    "h-3": "Description",
    "0-0": "startDate",
    "0-1": "date",
    "0-2": "No",
    "0-3": "The first date to return summarizations for.",
    "1-0": "endDate",
    "1-1": "date",
    "1-2": "No",
    "1-3": "The end of the period where the scan results of an asset will be returned. If it is later the the current date, it will be replaced by the later.",
    "2-0": "dateInterval",
    "2-1": "interva",
    "2-2": "No",
    "2-3": "The interval between the start and end date to return summarizations for."
  },
  "cols": 4,
  "rows": 3
}
[/block]
####Columns
[block:parameters]
{
  "data": {
    "h-0": "Column",
    "h-1": "Data Type",
    "h-2": "Nullable",
    "h-3": "Description",
    "h-4": "Associated Dimension",
    "0-0": "site_id",
    "0-1": "bigint",
    "0-2": "Yes",
    "0-3": "The unique identifier of the site.",
    "0-4": "dim_site",
    "1-0": "day",
    "1-1": "date",
    "1-2": "No",
    "1-3": "The date when the summarized policy scan results snapshot is taken.",
    "2-0": "policy_id",
    "2-1": "bigint",
    "2-2": "Yes",
    "2-3": "The unique identifier of the policy within a scope.",
    "2-4": "dim_site",
    "3-0": "scope",
    "3-1": "text",
    "3-2": "Yes",
    "3-3": "The identifier for scope of policy. Policies that are automatically available have \"Built-in\" scope, whereas policies created by users have scope as \"Custom\".",
    "4-0": "assets",
    "4-1": "integer",
    "4-2": "Yes",
    "4-3": "The total number of assets that are in the scope of the report and associated to the asset group.",
    "5-0": "compliant_assets",
    "5-1": "integer",
    "5-2": "Yes",
    "5-3": "The number of assets associated to the asset group that have not failed any while passed at least one policy rule test.",
    "6-0": "noncompliant_assets",
    "6-1": "integer",
    "6-2": "Yes",
    "6-3": "The number of assets associated to the asset group that have failed at least one policy rule test.",
    "7-0": "not_applicable_assets",
    "7-1": "integer",
    "7-2": "Yes",
    "7-3": "The number of assets associated to the asset group that have neither failed nor passed at least one policy rule test.",
    "8-0": "rule_compliance",
    "8-1": "numeric",
    "8-2": "Yes",
    "8-3": "The ratio of policy rule test result that are compliant or not applicable to the total number of rule test results."
  },
  "cols": 5,
  "rows": 9
}
[/block]
###fact_tag

> _added in version 1.2.0_

**Level of Grain:** The current summary information for a tag.

**Fact Type:** Accumulating snapshot

**Description:** The fact_tag table provides an accumulating snapshot fact for the summary information of a tag. The summary information provided is based on the most recent scan of every asset associated with the tag. If a tag has no accessible assets, there will be a fact record with zero counts. Only tags associated with assets, sites, or asset groups in the scope of the report will be present in this fact.

####Columns
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
    "1-0": "assets",
    "1-1": "bigint",
    "1-2": "No",
    "1-3": "The total number of accessible assets associated with the tag. If the tag has no accessible assets in the current scope or membership, this value can be zero.",
    "2-0": "vulnerabilities",
    "2-1": "bigint",
    "2-2": "No",
    "2-3": "The sum of the count of vulnerabilities on each asset. This value is equal to the sum of the critical_vulnerabilities, severe_vulnerabilities, and moderate_vulnerabilities columns.",
    "3-0": "critical_vulnerabilities",
    "3-1": "bigint",
    "3-2": "No",
    "3-3": "The sum of the count of critical vulnerabilities on each asset.",
    "4-0": "severe_vulnerabilities",
    "4-1": "bigint",
    "4-2": "No",
    "4-3": "The sum of the count of severe vulnerabilities on each asset.",
    "5-0": "moderate_vulnerabilities",
    "5-1": "bigint",
    "5-2": "No",
    "5-3": "The sum of the count of moderate vulnerabilities on each asset.",
    "6-0": "malware_kits",
    "6-1": "integer",
    "6-2": "No",
    "6-3": "The sum of the count of malware kits on each asset.",
    "7-0": "exploits",
    "7-1": "integer",
    "7-2": "No",
    "7-3": "The sum of the count of exploits on each asset.",
    "8-0": "vulnerabilities_with_malware_kit",
    "8-1": "integer",
    "8-2": "No",
    "8-3": "The sum of the count of vulnerabilities with malware kits on each asset.",
    "9-0": "vulnerabilities_with_exploit",
    "9-1": "integer",
    "9-2": "No",
    "9-3": "The sum of the count of vulnerabilities with exploits on each asset.",
    "10-0": "vulnerability_instances",
    "10-1": "bigint",
    "10-2": "No",
    "10-3": "The sum of the vulnerability instances on each asset.",
    "11-0": "riskscore",
    "11-1": "double precision",
    "11-2": "No",
    "11-3": "The sum of the risk score on each asset.",
    "12-0": "pci_status",
    "12-1": "text",
    "12-2": "No",
    "12-3": "The PCI compliance status; either Pass or Fail of the assets that have the tag."
  },
  "cols": 5,
  "rows": 13
}
[/block]
###fact_tag_date

> _added in version 1.2.1_

**Type:** Periodic snapshot

**Description:** The fact_tag_date table provides a periodic snapshot fact for summarized scan results for a tag over time. Each fact record represents the summary information for a tag in a scan in which the assets associated with that tag were fully and successfully scanned in that day or in the closest prior day.

This function takes a start date, end date and interval as arguments. If the end date is after the current date, then it will be replaced by the current date. Snapshots will be generated from the start date to the end date based on the interval value. If on a certain day no scan data can be found, a record for that day for all fields, except for the day and assets field, will have a null value.

####Arguments
[block:parameters]
{
  "data": {
    "h-0": "Column",
    "h-1": "Data Type",
    "h-2": "Nullable",
    "h-3": "Description",
    "0-0": "startDate",
    "0-1": "date",
    "0-2": "No",
    "0-3": "The first date to return summarizations for.",
    "1-0": "endDate",
    "1-1": "date",
    "1-2": "No",
    "1-3": "The end of the period where the scan results of a tag will be returned. If it is later than the current date, it will be replaced by the current date.",
    "2-0": "dateInterval",
    "2-1": "interval",
    "2-2": "No",
    "2-3": "The interval between the start and end date to return summarizations for."
  },
  "cols": 4,
  "rows": 3
}
[/block]
####Columns
[block:parameters]
{
  "data": {
    "h-0": "Column",
    "h-1": "Data Type",
    "h-2": "Nullable",
    "h-3": "Description",
    "h-4": "Associated Dimension",
    "0-0": "tag_id",
    "0-1": "bigint",
    "0-2": "Yes",
    "0-3": "The unique identifier of the tag.",
    "0-4": "dim_tag",
    "1-0": "day",
    "1-1": "date",
    "1-2": "No",
    "1-3": "The date the summary tag results are for.",
    "2-0": "assets",
    "2-1": "bigint",
    "2-2": "No",
    "2-3": "The total number of assets that are in the scope of the report and associated with the tag. If the tag has no assets in the current scope or membership, this value can be zero.",
    "3-0": "vulnerabilities",
    "3-1": "bigint",
    "3-2": "No",
    "3-3": "The sum of the counts of vulnerabilities associated with the tag. This value is equal to the sum of the critical_vulnerabilities, severe_vulnerabilities, and moderate_vulnerabilities columns.",
    "4-0": "critical_vulnerabilities",
    "4-1": "bigint",
    "4-2": "No",
    "4-3": "The sum of the counts of critical vulnerabilities associated with the tag.",
    "5-0": "severe_vulnerabilities",
    "5-1": "bigint",
    "5-2": "No",
    "5-3": "The sum of the counts of severe vulnerabilities associated with the tag.",
    "6-0": "moderate_vulnerabilities",
    "6-1": "bigint",
    "6-2": "No",
    "6-3": "The sum of the counts of moderate vulnerabilities associated with the tag.",
    "7-0": "malware_kits",
    "7-1": "integer",
    "7-2": "No",
    "7-3": "The sum of the counts of malware kits associated with the tag.",
    "8-0": "exploits",
    "8-1": "integer",
    "8-2": "No",
    "8-3": "The sum of the counts of exploits associated with the tag.",
    "9-0": "vulnerabilities_with_malware_kit",
    "9-1": "integer",
    "9-2": "No",
    "9-3": "The sum of the counts of vulnerabilities with malware kits associated with the tag.",
    "10-0": "vulnerabilities_with_exploit",
    "10-1": "integer",
    "10-2": "No",
    "10-3": "The sum of the counts of vulnerabilities with exploits associated with the tag.",
    "11-0": "vulnerability_instances",
    "11-1": "bigint",
    "11-2": "No",
    "11-3": "The sum of the instances of vulnerabilities associated with the tag.",
    "12-0": "riskscore",
    "12-1": "double precision",
    "12-2": "No",
    "12-3": "The sum of the risk scores associated with the tag.",
    "13-0": "pci_status",
    "13-1": "text",
    "13-2": "No",
    "13-3": "The compliance level ('Pass' or 'Fail') of the tag according to PCI standards."
  },
  "cols": 5,
  "rows": 14
}
[/block]
###fact_tag_policy_date

> _added in version 1.3.0_

**Type:** Periodic snapshot

**Description:** The fact_tag_policy_date table provides an accumulating snapshot fact for summarized policy information of a tag. The summarized policy information provided is based on the most recent scan of every asset associated with the tag. If a tag has no accessible assets, there will be a fact record with zero counts. Only tags associated with assets, sites, or asset groups in the scope of the report will be present in this fact.

####Arguments
[block:parameters]
{
  "data": {
    "h-0": "Column",
    "h-1": "Data Type",
    "h-2": "Nullable",
    "h-3": "Description",
    "0-0": "startDate",
    "0-1": "date",
    "0-2": "No",
    "0-3": "The first date to return summarizations for.",
    "1-0": "endDate",
    "1-1": "date",
    "1-2": "No",
    "1-3": "The end of the period where the scan results of an asset will be returned. If it is later the the current date, it will be replaced by the later.",
    "2-0": "dateInterval",
    "2-1": "interval",
    "2-2": "No",
    "2-3": "The interval between the start and end date to return summarizations for."
  },
  "cols": 4,
  "rows": 3
}
[/block]
####Columns
[block:parameters]
{
  "data": {
    "h-0": "Column",
    "h-1": "Data Type",
    "h-2": "Nullable",
    "h-3": "Description",
    "h-4": "Associated Dimension",
    "0-0": "tag_id",
    "0-1": "bigint",
    "0-2": "Yes",
    "0-3": "The unique identifier of the tag.",
    "0-4": "dim_tag",
    "1-0": "day",
    "1-1": "date",
    "1-2": "No",
    "1-3": "The date which the summarized policy scan results snapshot is taken.",
    "2-0": "policy_id",
    "2-1": "bigint",
    "2-2": "Yes",
    "2-3": "The unique identifier of the policy within a scope.",
    "2-4": "dim_policy",
    "3-0": "scope",
    "3-1": "text",
    "3-2": "Yes",
    "3-3": "The identifier for scope of policy. Policies that are automatically available have \"Built-in\" scope, whereas policies created by users have scope as \"Custom\".",
    "4-0": "assets",
    "4-1": "integer",
    "4-2": "Yes",
    "4-3": "The total number of assets that are in the scope of the report and associated to the asset group.",
    "5-0": "compliant_assets",
    "5-1": "integer",
    "5-2": "Yes",
    "5-3": "The number of assets associated to the asset group that have not failed any while passed at least one policy rule test.",
    "6-0": "noncompliant_assets",
    "6-1": "integer",
    "6-2": "Yes",
    "6-3": "The number of assets associated to the asset group that have failed at least one policy rule test.",
    "7-0": "not_applicable_assets",
    "7-1": "integer",
    "7-2": "Yes",
    "7-3": "The number of assets associated to the asset group that have neither failed nor passed at least one policy rule test.",
    "8-0": "rule_compliance",
    "8-1": "numeric",
    "8-2": "Yes",
    "8-3": "The ratio of PASS or NOT APPLICABLE results for the rules to the total number rule results."
  },
  "cols": 5,
  "rows": 9
}
[/block]
###fact_vulnerability

> _added in version 1.1.0_

**Level of Grain:** A summary of findings of a vulnerability.

**Fact Type:** accumulating snapshot

**Description:** The fact_vulnerability table provides a summarized record for each vulnerability within the scope of the report. For each vulnerability, the count of assets subject to the vulnerability is measured. Only assets with a finding in their most recent scan with no exception applied are included in the totals.

####Columns
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
    "0-3": "The identifier of the vulnerability",
    "0-4": "dim_vulnerability",
    "1-0": "affected_assets",
    "1-1": "bigint",
    "1-2": "No",
    "1-3": "The number of assets that have the vulnerability. This count may be zero if no assets are vulnerable.",
    "2-0": "vulnerability_instances",
    "2-1": "bigint",
    "2-2": "No",
    "2-3": "The number of instances or occurrences of the vulnerability across all assets.",
    "3-0": "most_recently_discovered",
    "3-1": "timestamp without time zone",
    "3-2": "No",
    "3-3": "The most recent date and time at which any asset within the scope of the report was discovered to be vulnerable to the vulnerability."
  },
  "cols": 5,
  "rows": 4
}
[/block]
 ####Dimensional model
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/0127a43-fact_vulnerability_v1.1.0.png",
        "fact_vulnerability_v1.1.0.png",
        905,
        670,
        "#e6e6e6"
      ],
      "caption": "Dimensional model for fact_vulnerability"
    }
  ]
}
[/block]