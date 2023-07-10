:original_name: dataartsstudio_02_0303.html

.. _dataartsstudio_02_0303:

To DCS
======

Sample JSON File
----------------

.. code-block::

    "to-config-values": {
              "configs": [
                  {
                      "inputs": [
                          {
                             "name": "toJobConfig.isBatchMigration",
                             "value": "false"
                          },
                          {
                             "name": "toJobConfig.shouldClearDatabase",
                             "value": "false"
                          },
                          {
                              "name": "toJobConfig.keyPrefix",
                              "value": "cdm_string"
                          },
                          {
                              "name": "toJobConfig.keySeparator",
                              "value": ":"
                          },
                          {
                              "name": "toJobConfig.primaryKeyList",
                              "value": "1"
                          },
                          {
                              "name": "toJobConfig.valueStoreType",
                              "value": "STRING"
                          },
                          {
                              "name": "toJobConfig.valueSeparator",
                              "value": ","
                          },
                          {
                              "name": "toJobConfig.columnList",
                              "value": "1&2&3&4&5&6&7&8&9&10&11&12"
                          }
                      ],
                      "name": "toJobConfig"
                  }
              ]
          }

Parameter Description
---------------------

-  Parameter description

   +---------------------------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter                       | Mandatory       | Type            | Description                                                                                                                                                               |
   +=================================+=================+=================+===========================================================================================================================================================================+
   | toJobConfig.isBatchMigration    | No              | Boolean         | Whether to migrate all data in the database                                                                                                                               |
   +---------------------------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | toJobConfig.shouldClearDatabase | No              | Boolean         | Whether to clear data before import                                                                                                                                       |
   +---------------------------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | toJobConfig.keyPrefix           | Yes             | String          | Key prefix, which is similar to the table name of a relational database                                                                                                   |
   |                                 |                 |                 |                                                                                                                                                                           |
   |                                 |                 |                 | Mapping between Redis and the association table: *Name of the association table + delimiter* is a Redis key, and a row of data in the association table is a Redis value. |
   +---------------------------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | toJobConfig.keySeparator        | Yes             | String          | Key delimiter, which separates the association table and primary key                                                                                                      |
   +---------------------------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | toJobConfig.primaryKeyList      | Yes             | String          | List of primary keys. Use **&** to separate field names. For example, **id&gid**.                                                                                         |
   +---------------------------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | toJobConfig.valueStoreType      | Yes             | Enumeration     | Storage mode of rows of data in the association table on Redis. The options are **string** and **hash**.                                                                  |
   |                                 |                 |                 |                                                                                                                                                                           |
   |                                 |                 |                 | -  **STRING**: indicates that a row of data is stored as a character string, in which columns in the row are separated by **valueSeparator**.                             |
   |                                 |                 |                 | -  **Hash**: indicates that a row of data is stored in *column name:column value* format in the hash table.                                                               |
   +---------------------------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | toJobConfig.valueSeparator      | No              | String          | Value delimiter. The default value is **\\tab**. This parameter is valid when **valueStoreType** is set to **string**.                                                    |
   +---------------------------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | toJobConfig.columnList          | No              | String          | List of fields to be written. Use **&** to separate field names. For example, **id&gid&name**.                                                                            |
   +---------------------------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | toJobConfig.formats             | No              | Data structure  | Time format. For details, see :ref:`Description of the toJobConfig.formats parameter <dataartsstudio_02_0303__en-us_topic_0108272802_li27488828155343>`.                  |
   +---------------------------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

-  .. _dataartsstudio_02_0303__en-us_topic_0108272802_li27488828155343:

   Description of the **toJobConfig.formats** parameter

   ========= ========= ====== =======================================
   Parameter Mandatory Type   Description
   ========= ========= ====== =======================================
   name      Yes       String Column number. For example, **1**.
   value     Yes       String Time format. For example, *yyyy-MM-dd*.
   ========= ========= ====== =======================================
