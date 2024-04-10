:original_name: dataartsstudio_02_0282.html

.. _dataartsstudio_02_0282:

From a Relational Database
==========================

Sample JSON File
----------------

.. code-block::

   "from-config-values": {
           "configs": [
             {
               "inputs": [
                 {
                   "name": "fromJobConfig.useSql",
                   "value": "false"
                 },
                 {
                   "name": "fromJobConfig.schemaName",
                   "value": "rf_database"
                 },
                 {
                   "name": "fromJobConfig.tableName",
                   "value": "rf_from"
                 },
                 {
                   "name": "fromJobConfig.columnList",
                   "value": "AA&BB"
                 },
                 {
                   "name": "fromJobConfig.incrMigration",
                   "value": "false"
                 }
               ],
               "name": "fromJobConfig"
             }
           ]
         }

Parameter Description
---------------------

+-------------------------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| Parameter                     | Mandatory       | Type            | Description                                                                                                                                                                                                                                                                                                      |
+===============================+=================+=================+==================================================================================================================================================================================================================================================================================================================+
| fromJobConfig.useSql          | Yes             | Boolean         | Whether to use the customized SQL statement to export data when exporting relational database data                                                                                                                                                                                                               |
+-------------------------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| fromJobConfig.sql             | No              | String          | Customized SQL statement. CDM executes the SQL statement to export data.                                                                                                                                                                                                                                         |
+-------------------------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| fromJobConfig.schemaName      | Yes             | String          | Database mode or tablespace. For example, **public**.                                                                                                                                                                                                                                                            |
|                               |                 |                 |                                                                                                                                                                                                                                                                                                                  |
|                               |                 |                 | .. note::                                                                                                                                                                                                                                                                                                        |
|                               |                 |                 |                                                                                                                                                                                                                                                                                                                  |
|                               |                 |                 |    The parameter value can contain wildcard characters (``*``), which is used to export all databases whose names start with a certain prefix or end with a certain suffix. The examples are as follows:                                                                                                         |
|                               |                 |                 |                                                                                                                                                                                                                                                                                                                  |
|                               |                 |                 |    -  **SCHEMA\*** indicates that all databases whose names starting with **SCHEMA** are exported.                                                                                                                                                                                                               |
|                               |                 |                 |    -  **\*SCHEMA** indicates that all databases whose names ending with **SCHEMA** are exported.                                                                                                                                                                                                                 |
|                               |                 |                 |    -  **\*SCHEMA\*** indicates that all databases whose names containing **SCHEMA** are exported.                                                                                                                                                                                                                |
+-------------------------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| fromJobConfig.tableName       | Yes             | String          | Table name. For example, **TBL_EXAMPLE**.                                                                                                                                                                                                                                                                        |
|                               |                 |                 |                                                                                                                                                                                                                                                                                                                  |
|                               |                 |                 | .. note::                                                                                                                                                                                                                                                                                                        |
|                               |                 |                 |                                                                                                                                                                                                                                                                                                                  |
|                               |                 |                 |    The table name can contain wildcard characters (``*``), which is used to export all tables whose names start with a certain prefix or end with a certain suffix. The number and types of fields in the tables must be the same. The examples are as follows:                                                  |
|                               |                 |                 |                                                                                                                                                                                                                                                                                                                  |
|                               |                 |                 |    -  **table\*** indicates that all tables whose names starting with **table** are exported.                                                                                                                                                                                                                    |
|                               |                 |                 |    -  **\*table** indicates that all tables whose names ending with **table** are exported.                                                                                                                                                                                                                      |
|                               |                 |                 |    -  **\*table\*** indicates that all tables whose names containing **table** are exported.                                                                                                                                                                                                                     |
+-------------------------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| fromJobConfig.whereClause     | No              | String          | WHERE clause used to specify the data to be extracted. If no WHERE clause is configured, the entire table will be extracted. For example, **age > 18 and age <= 60**.                                                                                                                                            |
+-------------------------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| fromJobConfig.columnList      | No              | String          | List of fields to be extracted. Use **&** to separate field names. For example, **id&gid&name**.                                                                                                                                                                                                                 |
+-------------------------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| fromJobConfig.partitionColumn | No              | String          | Partition field to be extracted, by which a job is split in multiple sub-jobs executed concurrently. For example, **id**.                                                                                                                                                                                        |
+-------------------------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| fromJobConfig.usePartition    | No              | Boolean         | When data is exported from the Oracle database, data can be extracted from each partition in a partitioned table. When this function is enabled, you can use the **fromJobConfig.partitionList** parameter to specify the partitions in the Oracle table. This function does not support non-partitioned tables. |
+-------------------------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| fromJobConfig.partitionList   | No              | String          | Oracle table partitions to be migrated. Separate multiple partitions with ampersands (&). If you do not set this parameter, all partitions will be migrated.                                                                                                                                                     |
+-------------------------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
