---
title: "Configuring data warehousing settings"
excerpt: ""
---
[block:callout]
{
  "type": "info",
  "body": "Currently, only PostgreSQL 9.4 or higher databases are supported as a warehousing target."
}
[/block]
You can configure the Security Console to export data into an external data warehouse. You can use this feature to obtain a richer set data for integration with your own internal reporting systems, such as Business Intelligence tools. The export performs an extract, transform, and load (ETL) process into the target warehouse using a dimensional model.

You can view the schema for this model [here](https://help.rapid7.com/nexpose/en-us/warehouse/warehouse-schema.html).

# Scheduling

The frequency of the ETL process to the external warehouse should be configured with your reporting needs in mind. The frequency of export matches the granularity of data points available for trending using historical fact tables. Due to the amount of data that can be exported, the warehousing process may take some time to complete. The recommended schedule setting is every 1 week. Care should be taken to schedule this export during non-critical scanning windows to minimize impact.

# Configuration

Data warehousing can be configured by a Global Administrator. Before configuring the Security Console settings, ensure that the destination warehouse database server has been configured (For more information, see [Deploying and Configuring the Warehouse](doc:configuring-data-warehousing-settings#section-deploying-and-configuring-the-warehouse)). To configure data warehouse export settings:

1. Click **Manage** next to _Data Warehousing_ on the _Administration_ page.
2. Enter database server settings on the _Database_ page.
   * _Enable export_ - Indicates whether exporting is currently enabled.
   * _Data model_ - Indicates the type of warehouse schema to be used. _Dimensional_ is recommended and the _Legacy_ model is deprecated.
   * _Server address_ - The IP or host name of the target warehouse.
   * _Server port_ - The port the target warehouse is accepting external connections on.
   * _Database name_ - The name of the database to export to the model into.
   * _User/Password_ - The credentials of the user to perform the export as. This user must have write access to the database.
   * _Encrypt data in transit_ - If enabled, will use a SSL connection to the target database during the ETL process. This ensures that all data transmitted to the warehouse is encrypted in transit (Note: The warehouse is not encrypted at rest by default). The recommended setting is enabled.
   * _Validate server identity_ - If enabled, verifies the server identity when Encrypt data in transit is also enabled. If the server certificate is unsigned and this option is enabled, the export process will not function properly. Disabling this setting allows trusting of self-signed certificates, but no longer prevents man-in-the-middle (MitM) attacks. The recommended setting is enabled.
3. Test the connection using the **Test Connection** button. This will attempt to establish a connection with the target warehouse database. Any errors will be presented, and you may reconfigure the settings or the target warehouse database appropriately until the connection is successful.
4. Go to the _Schedule_ page to configure the export frequency.
   * Select a date and time to start the export process
   * Select an interval during which to repeat this process. The recommended setting is every 1 week. If you do want to run it more frequently, we recommend to run it no more often than every 24 hours.
5. Click **Save**.

# Upgrading from the Legacy Model

The following are recommended if you have an existing data warehouse configuration in place:

1. **Change the Data model from _Legacy to Dimensional_:** This will change the structure of the output schema to an easier to use and more comprehensively supported data model. You will be required to update any consumers of the warehouse to use the new model. When the new model is used, the existing schema elements will remain untouched, but no longer update during future ETL processes.
2. **Enable encryption and identity validation:** These settings were previously not supported, meaning any data in transit was not encrypted during the export process. Encryption of data in transit is recommend going forward, so you are encouraged to enable the _Encrypt data in transit_ and _Validate server identity_ settings. These changes will require a reconfiguration of SSL in the destination warehouse database. See "Deploying and Configuring the Warehouse" section for more information.

# Schema Changes

The dimensional warehouse schema is guaranteed to be backwards compatible when changes are made. The ETL process performed by the Security Console may periodically add additional data elements to the schema, but this will not cause any reports or queries against this schema to break in the future. The following will not be subject to change in the schema:

* Available tables, columns, and functions, including their names
* Column and function data types

The following changes made be made in future iterations of the ETL process:
* Additional columns are added to an existing table
* New tables or functions are added

When changes are made to the model, applying a product upgrade and performing a new ETL process will upgrade the model in the target warehouse.

# Reporting on the Warehouse

After the export process, the data warehouse is immediately available for reporting using any of: 1) direct connections; 2) a business intelligence tool; and/or 3) any additional custom tools/scripts or off-the-shelf software. During the export (ETL) process numerous DDL and DML queries are executed that manipulate the state of the warehouse. Consequently, the warehouse should not be accessed during this time period.

# Deploying and Configuring the Warehouse

The data warehouse is a host running a PostgreSQL 9.4 or later database server. Management and configuration of the data warehouse server must be performed manually. The warehouse must be configured to support an external connection on the PostgreSQL database port, and allow ingress network traffic from the Security Console. Configuration of the warehouse for optimum performance varies based on the number of simultaneous connections needed, as well as the disk speed and available ram.

Hardware Requirements:

* 2 GHz+ processor (Quad-core processor recommended)
* 32 GB RAM (minimum), 72 GB+ RAM (recommended)
* 1 TB HDD (minimum), 2 TB+ HDD (recommended)
* 100 Mbps network interface (minimum), 1 Gbps (recommended)

Follow these steps to install and configure a new data warehouse:

1. Install PostgreSQL 9.4 or later, ensuring all available patches are applied
2. Configure the _postgresql.conf_ with the following recommended minimum settings (you may reconfigure to your hardware and connection requirements accordingly):

All PostgreSQL versions:
[block:parameters]
{
  "data": {
    "h-0": "Setting",
    "h-1": "32 GB RAM",
    "h-2": "72 GB RAM",
    "0-0": "max_connections",
    "0-1": "10",
    "0-2": "20",
    "1-0": "shared_buffers",
    "1-1": "8 GB",
    "1-2": "18 GB",
    "2-0": "work_mem",
    "2-1": "419 MB",
    "2-2": "471 MB",
    "3-0": "maintenance_work_mem",
    "3-1": "2 GB",
    "3-2": "2 GB",
    "4-0": "checkpoint_segments",
    "4-1": "128",
    "4-2": "256",
    "5-0": "effective_cache_size",
    "5-1": "24 GB",
    "5-2": "54 GB",
    "6-0": "checkpoint_completion_target",
    "6-1": "0.9",
    "6-2": "0.9",
    "7-0": "wal_buffers",
    "7-1": "16 MB",
    "7-2": "32 MB",
    "8-0": "auto_vacuum",
    "8-1": "off",
    "8-2": "off"
  },
  "cols": 3,
  "rows": 9
}
[/block]
PostgreSQL 9.6+:
[block:parameters]
{
  "data": {
    "h-0": "Setting",
    "h-1": "32 GB or 72 GB RAM",
    "0-0": "min_parallel_relation_size",
    "0-1": "8 MB",
    "1-0": "force_parallel_mode",
    "1-1": "on",
    "2-0": "max_worker_processes",
    "2-1": "number of CPU cores * 2",
    "3-0": "max_parallel_workers_per_gather",
    "3-1": "number of CPU cores / 2"
  },
  "cols": 2,
  "rows": 4
}
[/block]
3. To enable SSL (and encryption of data in transit), acquire a certificate and enable the following in the _postgresql.conf_ file:
   * ```ssl = on```
   * ```ssl_ciphers = 'HIGH:MEDIUM:+3DES:!aNULL'```
   * ```ssl_cert_file = 'server.crt'```
   * ```ssl_key_file = 'server.key'```
   * ```password_encryption = on```
4. Launch the postgreSQL process.