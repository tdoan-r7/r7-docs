---
title: "Understanding the reporting data model: Functions"
excerpt: ""
---
To ease the development and design of queries against the Reporting Data Model, several utility functions are provided to the report designer.
[block:callout]
{
  "type": "info",
  "body": "Data model 2.0.0 exposes information about linking assets across sites. All previous information is still available, and in the same format. As of data model 2.0.0, there is a _sites_ column in the dim_asset dimension that lists the sites to which an asset belongs."
}
[/block]
####age

> _added in version 1.2.0_

**Description:** Computes the difference in time between the specified date and now. Unlike the built-in age function, this function takes as an argument the unit to calculate in. This function will compute the age and round based on the specified unit. Valid unit values are (precision of the output):

* _years_ (2 digit precision)
* _months_ (2 digit precision)
* _weeks_ (2 digit precision)
* _days_ (1 digit precision)
* _hours_ (1 digit precision)
* _minutes_ (0 digit precision)

The computation of age is not timezone aware, and uses heuristic values for time. In other words, the age is computed as the elapsed time between the date and now, not the calendar time. For example, a year is assumed to comprise 365.25 days, and a month 30.4 days.

**Input:** (timestamp, text) The date to compute the age for, and the unit of the computation.

**Output:** (numeric) The value of the age, in the unit specified, with a precision based on the input unit.

####baselineComparison

**Description:** A custom aggregate function that performs a comparison between a set of identifiers from two snapshots in time within a grouping expression to return a baseline evaluation result, either ‘New’, ‘Old’, or ‘Same’. This result indicates whether the entity being grouped appeared in only the most recent state (‘New’), in only the previous state (‘Old’), or in both states (‘Same’). This aggregate can aggregate over the identifiers of objects that are temporal in nature (such as scan identifiers).

**Input:** (bigint, bigint)  The identifier of any value in either the new or old state, followed by the identifier of the most recent state.

**Output:** (text)  A value indicating whether the baseline evaluates to ‘New’, ‘Old’, or ‘Same’.

####csv

> _added in version 1.2.0_

**Description:** Returns a comma-separated list of values defined within an aggregated group. This function can be used as a replacement for the syntax array_to_string(array_agg(column), ','). When creating the list of values, the order is defined as the order observed in the aggregate.

**Input:** (text) The textual value to place in the output list.

**Output:** (text) A comma-separated list of all the values in the aggregate.

####htmlToText

> _added in version 1.2.0_

**Description:** Formats HTML content and structure into a flattened, plain-text format. This function can be used to translate fields with content metadata, such as vulnerability proofs, vulnerability descriptions, solution fixes, etc.

**Input:** (text) The value containing embedded HTML content to format.

**Output:** (text) The plain-text representation.

####lastScan

**Description:** Returns the identifier of the most recent scan of an asset.

**Input:** (bigint) The identifier of the asset.

**Output:** (bigint) The identifier of the scan that successfully completed most recently on the asset. As every asset must have had one scan completed, this is guaranteed to not return null.

####maximumSeverity

> _added in version 1.2.0_

**Description:** Returns the maximum severity value within an aggregated group. When used across a grouping that contains multiple vulnerabilities with varying severities, this aggregate can be used to select the highest severity of them all. For example, the aggregate of _Severe_ and _Moderate_ is _Severe_. This aggregate should only be used on columns containing severity rankings for a vulnerability.

**Input:** (text) A severity value to select from.

**Output:** (text) The maximum severity value found within a group: _Critical_, _Moderate_, or _Severe_.

####previousScan

**Description:** Returns the identifier of the scan that took place prior to the most recent scan of the asset (see the function lastScan).

**Input:** (bigint) The identifier of the asset.

**Output:** (bigint) The identifier of the scan that occurred prior to the most recent scan of the asset. If an asset was only scanned once, this will return null.

####proofAsText

> _Deprecated as of version 1.2.0. Use htmlToText() instead._

**Description:** Formats the proof of a vulnerability instance to be output into a flattened, plain-text format. This function is an alias for the htmlToText() function.

**Input:** (text) The proof value to format, which may be null.

**Output:** (text) The proof value formatted for display as plain text.

####scanAsOf

**Description:** Returns the identifier of the scan that took place on an asset prior to the specified date (exclusive).

**Input:** (bigint, timestamp) The identifier of the asset and the date to search before.

**Output:** (bigint) The identifier of the scan that occurred prior to the specified date on the asset, or null if no scan took place on the asset prior to the date.

####scanAsOfDate

> _added in version 1.2.0_

**Description:** Returns the identifier of the scan that took place on an asset prior to the specified date. See _scanAsOf()_ if you are using a timestamp field.

**Input:** (bigint, date) The identifier of the asset and the date to search before.

**Output:** (bigint) The identifier of the scan that occurred prior to the specified date on the asset, or null if no scan took place on the asset prior to the date.