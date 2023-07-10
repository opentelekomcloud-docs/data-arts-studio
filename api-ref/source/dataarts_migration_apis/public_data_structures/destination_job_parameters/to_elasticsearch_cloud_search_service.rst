:original_name: dataartsstudio_02_0304.html

.. _dataartsstudio_02_0304:

To Elasticsearch/Cloud Search Service
=====================================

Sample JSON File
----------------

.. code-block::

   "to-config-values": {
                   "configs": [
                       {
                           "inputs": [
                               {
                                 "name": "toJobConfig.index",
                                 "value": "cdm"
                               },
                               {
                                 "name": "toJobConfig.type",
                                 "value": "type1"
                               },
                               {
                                 "name": "toJobConfig.shouldClearType",
                                 "value": "false"
                               },
                              {
                                 "name": "toJobConfig.pipeLine",
                                 "value": "es_03"
                              }
                           ],
                           "name": "toJobConfig"
                       }
                   ]
               }

Parameter Description
---------------------

+---------------------------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| Parameter                       | Mandatory       | Type            | Description                                                                                                                                                                                                                                                          |
+=================================+=================+=================+======================================================================================================================================================================================================================================================================+
| toJobConfig.index               | Yes             | String          | Index of the written data, which is similar to the database name in the relational database                                                                                                                                                                          |
+---------------------------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| toJobConfig.type                | Yes             | String          | Type of the written data, which is similar to the table name in the relational database                                                                                                                                                                              |
+---------------------------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| toJobConfig.shouldClearType     | No              | Boolean         | Whether to clear data before import                                                                                                                                                                                                                                  |
+---------------------------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| toJobConfig.primaryKey          | No              | String          | Primary key or unique index                                                                                                                                                                                                                                          |
+---------------------------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| toJobConfig.columnList          | No              | String          | List of fields to be written. Use **&** to separate field names. For example, **id&gid&name**.                                                                                                                                                                       |
+---------------------------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| toJobConfig.pipeLine            | No              | String          | This parameter is available only after a pipeline ID is created in Kibana. It is used to convert the data format using the data transformation pipeline of Cloud Search Service or Elasticsearch after data is transferred to Cloud Search Service or Elasticsearch. |
+---------------------------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| toJobConfig.createIndexStrategy | No              | Enumeration     | For streaming jobs that continuously write data to Elasticsearch, CDM periodically creates indexes and writes data to the indexes, which helps you delete expired data. The indexes can be created based on the following periods:                                   |
|                                 |                 |                 |                                                                                                                                                                                                                                                                      |
|                                 |                 |                 | -  **EveryHour**: CDM creates indexes on the hour. The new indexes are named in the format of *Index name+Year+Month+Day+Hour*, for example, **index2018121709**.                                                                                                    |
|                                 |                 |                 | -  **EveryDay**: CDM creates indexes at 00:00 every day. The new indexes are named in the format of *Index name+Year+Month+Day*, for example, **index20181217**.                                                                                                     |
|                                 |                 |                 | -  **EveryWeek**: CDM creates indexes at 00:00 every Monday. The new indexes are named in the format of *Index name+Year+Week*, for example, **index201842**.                                                                                                        |
|                                 |                 |                 | -  **EveryMonth**: CDM creates indexes at 00:00 on the first day of each month. The new indexes are named in the format of *Index name+Year+Month*, for example, **index201812**.                                                                                    |
|                                 |                 |                 |                                                                                                                                                                                                                                                                      |
|                                 |                 |                 | When extracting data from a file, you must configure a single extractor, which means setting **Concurrent Extractors** to **1**. Otherwise, this parameter is invalid.                                                                                               |
+---------------------------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
