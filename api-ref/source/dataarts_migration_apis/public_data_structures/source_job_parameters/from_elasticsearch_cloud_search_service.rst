:original_name: dataartsstudio_02_0293.html

.. _dataartsstudio_02_0293:

From Elasticsearch/Cloud Search Service
=======================================

Sample JSON File
----------------

.. code-block::

   "from-config-values": {
                   "configs": [
                       {
                           "inputs": [
                               {
                                   "name": "fromJobConfig.index",
                                   "value": "cdm"
                               },
                               {
                                   "name": "fromJobConfig.type",
                                   "value": "es"
                               },
                               {
                                   "name": "fromJobConfig.columnList",
                                   "value": "a1:numeric&s1:string"
                               },
                              {
                                  "name": "fromJobConfig.splitNestedField",
                                  "value": "true"
                              },
                              {
                                  "name": "fromJobConfig.queryString",
                                  "value": "last_name:Smith"
                              }
                           ],
                           "name": "fromJobConfig"
                       }
                   ]
               }

Parameter Description
---------------------

+--------------------------------+-----------+---------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| Parameter                      | Mandatory | Type    | Description                                                                                                                                                            |
+================================+===========+=========+========================================================================================================================================================================+
| fromJobConfig.index            | Yes       | String  | Index of the extracted data, which is similar to the database name in the relational database                                                                          |
+--------------------------------+-----------+---------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| fromJobConfig.type             | Yes       | String  | Type of the extracted data, which is similar to the table name in the relational database                                                                              |
+--------------------------------+-----------+---------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| fromJobConfig.columnList       | No        | String  | List of fields to be extracted. Use **&** to separate field names. For example, **id&gid&name**.                                                                       |
+--------------------------------+-----------+---------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| fromJobConfig.splitNestedField | No        | Boolean | Whether to split the JSON content of the **nested** field. For example, **a:{ b:{ c:1, d:{ e:2, f:3 } } }** can be split into **a.b.c**, **a.b.d.e**, and **a.b.d.f**. |
+--------------------------------+-----------+---------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| fromJobConfig.queryString      | No        | String  | Whether to use the Elasticsearch query string to filter the source data. CDM migrates only the data that meets the filter criteria.                                    |
+--------------------------------+-----------+---------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
