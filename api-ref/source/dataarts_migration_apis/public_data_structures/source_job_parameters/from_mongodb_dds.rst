:original_name: dataartsstudio_02_0289.html

.. _dataartsstudio_02_0289:

From MongoDB/DDS
================

Sample JSON File
----------------

.. code-block::

   "from-config-values": {
           "configs": [
             {
               "inputs": [
                 {
                   "name": "fromJobConfig.database",
                   "value": "cdm"
                 },
                 {
                   "name": "fromJobConfig.collectionName",
                   "value": "rf_from"
                 },
                 {
                   "name": "fromJobConfig.columnList",
                   "value": "TINYTEST&SMALLTEST&INTTEST&INTEGERTEST&BIGINTTEST&FLOATTEST"
                 },
                 {
                   "name": "fromJobConfig.isBatchMigration",
                   "value": "false"
                 },
                 {
                   "name": "fromJobConfig.filters",
                   "value": "{'last_name': 'Smith'}"
                 }
               ],
               "name": "fromJobConfig"
             }
           ]
         }

Parameter Description
---------------------

+--------------------------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------+
| Parameter                      | Mandatory       | Type            | Description                                                                                                                      |
+================================+=================+=================+==================================================================================================================================+
| fromJobConfig.database         | Yes             | String          | Name of the MongoDB/DDS database                                                                                                 |
+--------------------------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------+
| fromJobConfig.collectionName   | Yes             | String          | Name of the MongoDB/DDS collection                                                                                               |
+--------------------------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------+
| fromJobConfig.columnList       | No              | String          | List of fields to be extracted. Use **&** to separate field names. For example, **id&gid&name**.                                 |
+--------------------------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------+
| fromJobConfig.isBatchMigration | No              | Boolean         | Whether to migrate all data in the database                                                                                      |
+--------------------------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------+
| fromJobConfig.filters          | No              | String          | Filter condition for files. CDM migrates only the data that meets the filter condition. Examples:                                |
|                                |                 |                 |                                                                                                                                  |
|                                |                 |                 | #. Filter by expression: **{'last_name': 'Smith'}** indicates that all files whose **last_name** value is **Smith** are queried. |
|                                |                 |                 | #. Filter by parameter: **{ x : "john" }, { z : 1 }** indicates that all **z** fields whose **x** is **john** are queried.       |
|                                |                 |                 | #. Filter by condition: **{ "field" : { $gt: 5 } }** indicates that the **field** values greater than 5 are queried.             |
+--------------------------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------+
