:original_name: dataartsstudio_02_0302.html

.. _dataartsstudio_02_0302:

To DDS
======

Sample JSON File
----------------

.. code-block::

   "to-config-values": {
           "configs": [
             {
               "inputs": [
                 {
                   "name": "toJobConfig.database",
                   "value": "demo"
                 },
                 {
                   "name": "toJobConfig.collectionName",
                   "value": "cdmbase"
                 },
                 {
                   "name": "toJobConfig.columnList",
                   "value": "_char&_varchar"
                 },
                 {
                   "name": "toJobConfig.isBatchMigration",
                   "value": "false"
                 }
               ],
               "name": "toJobConfig"
             }
           ]
         }

Parameter Description
---------------------

+------------------------------+-----------+---------+--------------------------------------------------------------------------------------------------+
| Parameter                    | Mandatory | Type    | Description                                                                                      |
+==============================+===========+=========+==================================================================================================+
| toJobConfig.database         | Yes       | String  | Name of the MongoDB/DDS database                                                                 |
+------------------------------+-----------+---------+--------------------------------------------------------------------------------------------------+
| toJobConfig.collectionName   | Yes       | String  | Name of the MongoDB/DDS collection                                                               |
+------------------------------+-----------+---------+--------------------------------------------------------------------------------------------------+
| toJobConfig.columnList       | No        | String  | List of fields to be extracted. Use **&** to separate field names. For example, **id&gid&name**. |
+------------------------------+-----------+---------+--------------------------------------------------------------------------------------------------+
| toJobConfig.isBatchMigration | No        | Boolean | Whether to migrate all data in the database                                                      |
+------------------------------+-----------+---------+--------------------------------------------------------------------------------------------------+
