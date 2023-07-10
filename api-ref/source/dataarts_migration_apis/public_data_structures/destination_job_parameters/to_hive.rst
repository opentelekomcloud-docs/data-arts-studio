:original_name: dataartsstudio_02_0299.html

.. _dataartsstudio_02_0299:

To Hive
=======

Sample JSON File
----------------

.. code-block::

   "to-config-values": {
           "configs": [
             {
               "inputs": [
                 {
                   "name": "toJobConfig.hive",
                   "value": "hive"
                 },
                 {
                   "name": "toJobConfig.database",
                   "value": "rf_database"
                 },
                 {
                   "name": "toJobConfig.table",
                   "value": "rf_to"
                 },
                 {
                   "name": "toJobConfig.tablePreparation",
                   "value": "DO_NOTHING"
                 },
                 {
                   "name": "toJobConfig.columnList",
                   "value": "aa&bb&cc&dd"
                 },
                 {
                   "name": "toJobConfig.shouldClearTable",
                   "value": "true"
                 }
               ],
               "name": "toJobConfig"
             }
           ]
         }

Parameter Description
---------------------

+------------------------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| Parameter                    | Mandatory       | Type            | Description                                                                                                                                                                |
+==============================+=================+=================+============================================================================================================================================================================+
| toJobConfig.hive             | No              | String          | Data source to which data is written                                                                                                                                       |
+------------------------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| toJobConfig.database         | No              | String          | Name of the database to which data is written. For example, **default**.                                                                                                   |
+------------------------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| toJobConfig.table            | Yes             | String          | Name of the table to which data is written                                                                                                                                 |
+------------------------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| toJobConfig.tablePreparation | Yes             | Enumeration     | The options for data write to tables are as follows:                                                                                                                       |
|                              |                 |                 |                                                                                                                                                                            |
|                              |                 |                 | -  **DO_NOTHING**: Do not create the table automatically.                                                                                                                  |
|                              |                 |                 | -  **CREATE_WHEN_NOT_EXIST**: If the destination database does not contain the table specified by **tableName**, CDM automatically creates the table.                      |
|                              |                 |                 | -  **DROP_AND_CREATE**: Delete the table specified by **tableName**, and then create the table again.                                                                      |
+------------------------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| toJobConfig.columnList       | No              | String          | List of fields to be loaded. Use **&** to separate field names. For example, **id&gid&name**.                                                                              |
+------------------------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| toJobConfig.shouldClearTable | No              | Boolean         | Whether to clear the data in the target table before data import. If this parameter is set to **true**, the data in the target table is cleared before the job is started. |
+------------------------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
