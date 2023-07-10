:original_name: dataartsstudio_02_0290.html

.. _dataartsstudio_02_0290:

From Redis/DCS (to Be Brought Offline)
======================================

Sample JSON File
----------------

.. code-block::

   "from-config-values": {
           "configs": [
             {
               "inputs": [
                 {
                   "name": "fromJobConfig.isBatchMigration",
                   "value": "false"
                 },
                 {
                   "name": "fromJobConfig.keyPrefix",
                   "value": "rf_string_from"
                 },
                 {
                   "name": "fromJobConfig.keySeparator",
                   "value": ":"
                 },
                 {
                   "name": "fromJobConfig.valueStoreType",
                   "value": "STRING"
                 },
                 {
                   "name": "fromJobConfig.valueSeparator",
                   "value": ","
                 },
                 {
                   "name": "fromJobConfig.columnList",
                   "value": "1&2&3&4&5&6&7&8&9&10&11&12"
                 }
               ],
               "name": "fromJobConfig"
             }
           ]
         }

Parameter Description
---------------------

-  Redis job parameter description

   +--------------------------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter                      | Mandatory       | Type            | Description                                                                                                                                                               |
   +================================+=================+=================+===========================================================================================================================================================================+
   | fromJobConfig.isBatchMigration | No              | Boolean         | Whether to migrate all data in the database                                                                                                                               |
   +--------------------------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | fromJobConfig.keyPrefix        | Yes             | String          | Key prefix, which is the name of the corresponding association table.                                                                                                     |
   |                                |                 |                 |                                                                                                                                                                           |
   |                                |                 |                 | Mapping between Redis and the association table: *Name of the association table + delimiter* is a Redis key, and a row of data in the association table is a Redis value. |
   +--------------------------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | fromJobConfig.keySeparator     | Yes             | String          | Key delimiter, which separates the association table and primary key                                                                                                      |
   +--------------------------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | fromJobConfig.valueStoreType   | Yes             | String          | Storage mode of rows of data in the association table on Redis. The options are **string** and **hash**.                                                                  |
   |                                |                 |                 |                                                                                                                                                                           |
   |                                |                 |                 | -  **STRING**: indicates that a row of data is stored as a character string using delimiters to separate columns. This mode reduces storage space occupation.             |
   |                                |                 |                 | -  **HASH**: indicates that a row of data is stored in *column name:column value* format in the hash table.                                                               |
   +--------------------------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | fromJobConfig.valueSeparator   | No              | String          | Value delimiter. The default value is **\\tab**. This parameter is valid when **valueStoreType** is set to **STRING**.                                                    |
   +--------------------------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | fromJobConfig.columnList       | No              | String          | List of fields to be extracted. Use **&** to separate field names. For example, **id&gid&name**.                                                                          |
   +--------------------------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | fromJobConfig.formats          | No              | Data structure  | Time format. For details, see :ref:`Description of the fromJobConfig.formats parameter <dataartsstudio_02_0290__en-us_topic_0108272845_li45055411174737>`.                |
   +--------------------------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

-  .. _dataartsstudio_02_0290__en-us_topic_0108272845_li45055411174737:

   Description of the **fromJobConfig.formats** parameter

   ========= ========= ====== =======================================
   Parameter Mandatory Type   Description
   ========= ========= ====== =======================================
   name      Yes       String Column number. For example, **1**.
   value     Yes       String Time format. For example, *yyyy-MM-dd*.
   ========= ========= ====== =======================================
