:original_name: dataartsstudio_01_0015.html

.. _dataartsstudio_01_0015:

Constraints
===========

**CDM System Constraints**
--------------------------

#. You cannot modify the flavor of an existing cluster. If you require a higher flavor, create a cluster with your desired flavor.

#. Arm CDM clusters do not support agents. The CDM cluster version (Arm or x86) is determined by the architecture of underlying resources.

#. CDM does not support the function of controlling the data migration speed. Therefore, do not perform data migration during peak hours.

#. During data migration, CDM imposes pressure on the data source. You are advised to create a database account for data migration and configure an account policy to reduce the resource consumption of the data source. For example, you can configure a policy to delete the connections of the account when the CPU usage exceeds 30% to prevent impact on services.

#. The baseline and maximum bandwidths of the NIC of the cdm.large CDM instance is 0.8 Gbit/s and 3 Gbit/s, respectively. The theoretical maximum volume of data that can be transmitted per instance per day is about 8 TB. Similarly, the baseline and maximum bandwidths of the NIC of the cdm.xlarge instance are 4 Gbit/s and 10 Gbit/s, respectively, and the theoretical maximum volume of data that can be transmitted per instance per day is about 40 TB. The baseline and maximum bandwidths of the NIC of the cdm.4xlarge instance is 36 Gbit/s and 40 Gbit/s, respectively, and the theoretical maximum volume of data that can be transmitted per instance per day is about 360 TB. You can use multiple CDM instances if you want faster data transfer.

   The actual amount of data that can be migrated in a day depends on the data source type, the read and write performance of the source and destination, and the actual available bandwidth. Typically you can migrate as much as 8 TB per day (large file migration to OBS) using the cdm.large instance. It is recommended that you test the speed with a small amount of data before migration.

#. CDM supports incremental file migration (by skipping repeated files), but does not support resumable transfer.

   For example, if three files are to be migrated and the second file fails to be migrated due to the network fault. When the migration task is started again, the first file is skipped. The second file, however, cannot be migrated from the point where the fault occurs, but can only be migrated again.

#. During file migration, a single task supports millions of files. If there are too many files in the directory to be migrated, you are advised to split the files into different directories and create multiple tasks.

#. You can export links and jobs configured on CDM to a local directory. To ensure password security, CDM does not export the link password of the corresponding data source. Therefore, before importing job configurations to CDM, you need to manually input the password in the exported JSON file or configure the password in the import dialog box.

#. The cluster cannot automatically upgrade to a new version. You need to use the job export and import functions to upgrade the cluster to the new version.

#. If OBS is unavailable, CDM does not automatically back up users' job configurations. You need to export and back up configuration data using the export function.

#. If VPC peering connection is configured, the peer VPC subnet may overlap with the CDM management network. As a result, data sources in the peer VPC cannot be accessed. You are advised to use the public network for cross-VPC data migration, or contact the administrator to add specific routes to the VPC peering connection in the CDM background.

#. If the destination of a CDM job is a DWS or NewSQL database, constraints of the source end, such as the primary key and unique index, cannot be migrated together.

#. When performing a CDM job, ensure that the JSON file formats of the two clusters are the same so that jobs can be imported from the source cluster to the destination cluster.

#. If a running job is interrupted unexpectedly, the data that has been written to the destination will not be deleted. You must manually delete the data if needed.

#. The size of a file to be transferred cannot exceed 1 TB.

**General Constraints on Database Migration**
---------------------------------------------

#. CDM is mainly used for batch migration. It supports only limited incremental migration but does not support real-time incremental migration.

#. The entire DB migration of CDM supports only data table migration but not migration of database objects such as stored procedures, triggers, functions, and views.

   CDM applies only to scenarios where databases are migrated to the cloud at a time, including homogeneous and heterogeneous database migrations. CDM is not applicable to data synchronization, for example, disaster recovery and real-time synchronization.

#. If CDM fails to migrate an entire database or table, the data that has been imported to the target table will not be rolled back automatically. If you want to perform migration in transaction mode, configure the **Import to Staging Table** parameter to enable a rollback upon a migration failure.

   In extreme cases, the created stage table or temporary table cannot be automatically deleted. You need to manually clear the table (the name of the stage table ends with **\_cdm_stage**), for example, **cdmtet_cdm_stage**).

#. If CDM needs to access data sources in the on-premises data center (for example, the on-premises MySQL database), the data sources must support Internet access and the CDM instances must be bound with elastic IP addresses. In this case, the security practice is to configure the firewall or security policies to allow only the EIPs of the CDM instances to access the local data sources.

#. Only common data types are supported, including character strings, digits, and dates. Object types are limited. If objects are too large, migration cannot be performed.

#. Only the GBK and UTF-8 character sets are supported.

#. A field name cannot contain & or %.

#. jdbc2hive and hive2jdbc entire DB migration is implemented by field name mapping, and is unavailable if the source and destination field names are inconsistent.

**Permissions Configuration for Relational Database Migration**
---------------------------------------------------------------

Common minimum permissions required by relational database migration:

-  MySQL: You need to have the read permission on the **INFORMATION_SCHEMA** database and data tables.
-  Oracle: You need to have the **resource** role and have the **select** permissions on the data table in the tablespace.
-  Dameng: You need to have the **select any table** permission in the schema.
-  DWS: You need to have the **schema usage** permission and the query permission on the data tables.
-  SQL Server: You need to have the **sysadmin** permission.
-  PostgreSQL: You need to have the **select** permission on schema tables in the database.

**Constraints on FusionInsight HD and Apache Hadoop**
-----------------------------------------------------

If the FusionInsight HD and Apache Hadoop data sources are deployed in the on-premises data center, CDM must access all nodes in the cluster for reading and writing the Hadoop files. Therefore, the network access must be enabled for each node.

**Constraints on DWS and FusionInsight LibrA**
----------------------------------------------

#. If the DWS primary key or table contains only one field, the field type must be a common character string, value, or date. When data is migrated from another database to DWS, if automatic table creation is selected, the primary key must be of the following types. If no primary key is set, at least one of the following fields must be set. Otherwise, the table cannot be created and the CDM job fails.

   -  INTEGER TYPES: TINYINT, SMALLINT, INT, BIGINT, NUMERIC/DECIMAL
   -  CHARACTER TYPES: CHAR, BPCHAR, VARCHAR, VARCHAR2, NVARCHAR2, TEXT
   -  DATA/TIME TYPES: DATE, TIME, TIMETZ, TIMESTAMP, TIMESTAMPTZ, INTERVAL, SMALLDATETIME

   .. note::

      For clusters of version 2.9.1.200 or earlier, the NVARCHAR2 data type is not supported for DWS.

#. In DWS, the character string **''** is null. A null character string cannot be inserted into a field with non-null constraints. This is inconsistent with the MySQL behavior. MySQL does not consider that **''** is null. Migration from MySQL to DWS may fail due to the preceding reason.
#. When the Gauss Data Service (GDS) mode is used to quickly import data to DWS, you need to configure a security group or firewall policy to allow DataNodes of DWS or FusionInsight LibrA to access port 25000 of the CDM IP address.
#. When data is imported to DWS in GDS mode, CDM automatically creates a foreign table for data import. The table name ends with a universally unique identifier (UUID), for example, **cdmtest_aecf3f8n0z73dsl72d0d1dk4lcir8cd**. If a job fails, it will be automatically deleted. In extreme cases, you may need to manually delete it.

**Constraints on OBS**
----------------------

#. During file migration, the system automatically transfers the files concurrently. In this case, **Concurrent Extractors** in the task configuration is invalid.

#. Resumable transmission is not supported. If CDM fails to transfer files, OBS fragments are generated. You need to clear fragments on the OBS console to prevent space occupation.

#. CDM does not support the versioning control function of OBS.

#. During incremental migration, the number of files or objects in the source directory of a single job depends on the CDM cluster flavor. A cdm.large cluster supports a maximum of 300,000 files; a cdm.medium cluster supports a maximum of 200,000 files; and a cdm.small cluster supports a maximum of 100,000 files.

   If the number of files or objects in a single directory exceeds the upper limit, split the files or objects into multiple migration jobs based on subdirectories.

**Constraints on DLI**
----------------------

-  To use CDM to migrate data to DLI, you must have the read permissions of OBS.
-  If the destination is DLI, you are advised to set the number of concurrent extractors to 1. Otherwise, data may fail to be written.

**Constraints on Oracle**
-------------------------

Real-time incremental data synchronization is not supported for Oracle databases.

**Constraints on DCS and Redis**
--------------------------------

#. The Redis service of the third-party cloud cannot serve as the migration source. However, the Redis set up in the on-premises data center or on the ECS can be the migration source and destination.
#. Only the hash and string data formats are supported.

**Constraints on DDS and MongoDB**
----------------------------------

When you migrate MongoDB or DDS data, CDM reads the first row of the collection as an example of the field list. If the first row of data does not contain all fields of the collection, you need to manually add fields.

**Constraints on CSS and Elasticsearch**
----------------------------------------

#. CDM supports automatic creation of indexes and field types. The index and field type names can contain only lowercase letters.

#. You cannot modify the field type under an index after it is created, but only create another field.

   If you need to modify the field type, you need to create an index or run the Elasticsearch command on Kibana to delete the existing index and create another index (the data is also deleted).

#. When the field type of the index created by CDM is date, the data format must be *yyyy-MM-dd HH:mm:ss.SSS Z*. For example, **2018-08-08 08:08:08.888 +08:00**.

   During data migration to CSS, if the original data of the **date** field does not meet the format requirements, you can use the expression conversion function of CDM to convert the data to the preceding format.

**Constraints on Kafka**
------------------------

-  The data in the message body is a record in CSV format that supports multiple delimiters. Messages cannot be parsed in binary or other formats.
-  If the source is MRS Kafka, custom fields are not supported in field mapping.
-  If the source is DMS Kafka, custom fields are supported in field mapping.

**Constraints on CloudTable and HBase**
---------------------------------------

#. When you migrate data from CloudTable or HBase, CDM reads the first row of the table as an example of the field list. If the first row of data does not contain all fields of the table, you need to manually add fields.
#. Because HBase is schema-less, CDM cannot obtain the data types. If the data is stored in binary format, CDM cannot parse the data.

**Constraints on Hive**
-----------------------

-  If Hive stores timestamp data in Parquet format, timestamps are accurate to the nanosecond, for example, 2023-03-27 00:00:00.000. If the source data precision is higher than the nanosecond, the data will be truncated during field mapping. For example, if the source data is **2023-03-27 00:00:00.12345**, it will be truncated to **2023-03-27 00:00:00.123** at the destination.

-  If Hive serves as the migration destination and the storage format is Textfile, delimiters must be explicitly specified in the statement for creating Hive tables. The following is an example:

   .. code-block::

      CREATE TABLE csv_tbl(
      smallint_value smallint,
      tinyint_value tinyint,
      int_value int,
      bigint_value bigint,
      float_value float,
      double_value double,
      decimal_value decimal(9, 7),
      timestmamp_value timestamp,
      date_value date,
      varchar_value varchar(100),
      string_value string,
      char_value char(20),
      boolean_value boolean,
      binary_value binary,
      varchar_null varchar(100),
      string_null string,
      char_null char(20),
      int_null int
      )
      ROW FORMAT SERDE 'org.apache.hadoop.hive.serde2.OpenCSVSerde'
      WITH SERDEPROPERTIES (
      "separatorChar" = "\t",
      "quoteChar"     = "'",
      "escapeChar"    = "\\"
      )
      STORED AS TEXTFILE;
