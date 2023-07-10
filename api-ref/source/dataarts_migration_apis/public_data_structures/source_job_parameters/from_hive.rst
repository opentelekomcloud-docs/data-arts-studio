:original_name: dataartsstudio_02_0285.html

.. _dataartsstudio_02_0285:

From Hive
=========

Sample JSON File
----------------

.. code-block::

   "from-config-values": {
           "configs": [
             {
               "inputs": [
                 {
                   "name": "fromJobConfig.hive",
                   "value": "hive"
                 },
                 {
                   "name": "fromJobConfig.database",
                   "value": "rf_database"
                 },
                 {
                   "name": "fromJobConfig.table",
                   "value": "rf_from"
                 },
                 {
                   "name": "fromJobConfig.columnList",
                   "value": "tiny&small&int&integer&bigint&float&double&timestamp&char&varchar&text"
                 }
               ],
               "name": "fromJobConfig"
             }
           ]
         }

Parameter Description
---------------------

+--------------------------+-----------+--------+----------------------------------------------------------------------------------------------------------------------+
| Parameter                | Mandatory | Type   | Description                                                                                                          |
+==========================+===========+========+======================================================================================================================+
| fromJobConfig.hive       | No        | String | Data source to be extracted. If the data source is Hive, set this parameter to **hive**.                             |
+--------------------------+-----------+--------+----------------------------------------------------------------------------------------------------------------------+
| fromJobConfig.database   | No        | String | Database from which data is extracted. For example, **default**.                                                     |
+--------------------------+-----------+--------+----------------------------------------------------------------------------------------------------------------------+
| fromJobConfig.table      | Yes       | String | Name of the table from which data is extracted. For example, **cdm**.                                                |
+--------------------------+-----------+--------+----------------------------------------------------------------------------------------------------------------------+
| fromJobConfig.columnList | No        | String | Numbers of columns to be extracted. Use **&** to separate column numbers in ascending order. For example, **1&3&5**. |
+--------------------------+-----------+--------+----------------------------------------------------------------------------------------------------------------------+
