:original_name: dataartsstudio_02_0305.html

.. _dataartsstudio_02_0305:

To DLI
======

Sample JSON File
----------------

.. code-block::

   "to-config-values": {
                   "configs": [
                       {
                           "inputs": [
                               {
                                   "name": "toJobConfig.queue",
                                   "value": "cdm"
                               },
                               {
                                   "name": "toJobConfig.database",
                                   "value": "sqoop"
                               },
                               {
                                   "name": "toJobConfig.table",
                                   "value": "est1"
                               },
                               {
                                   "name": "toJobConfig.columnList",
                                   "value": "string_&int_&date_&double_&boolean_&short_&timestamp_&long_&smallint_&bigint_"
                               },
                               {
                                   "name": "toJobConfig.shouldClearTable",
                                   "value": "false"
                               }
                           ],
                           "name": "toJobConfig"
                       }
                   ]
               }

Parameter Description
---------------------

+------------------------------+-----------+---------+-----------------------------------------------------------------------------------------------+
| Parameter                    | Mandatory | Type    | Description                                                                                   |
+==============================+===========+=========+===============================================================================================+
| toJobConfig.queue            | Yes       | String  | Resource queue to which data is written                                                       |
+------------------------------+-----------+---------+-----------------------------------------------------------------------------------------------+
| toJobConfig.database         | Yes       | String  | DLI database to which data is written                                                         |
+------------------------------+-----------+---------+-----------------------------------------------------------------------------------------------+
| toJobConfig.table            | Yes       | String  | Name of the table to which data is written                                                    |
+------------------------------+-----------+---------+-----------------------------------------------------------------------------------------------+
| toJobConfig.columnList       | No        | String  | List of fields to be loaded. Use **&** to separate field names. For example, **id&gid&name**. |
+------------------------------+-----------+---------+-----------------------------------------------------------------------------------------------+
| toJobConfig.shouldClearTable | No        | Boolean | Whether to clear data in the resource queue before data import                                |
+------------------------------+-----------+---------+-----------------------------------------------------------------------------------------------+
