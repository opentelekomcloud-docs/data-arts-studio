:original_name: dataartsstudio_01_0055.html

.. _dataartsstudio_01_0055:

From MongoDB/DDS
================

When you migrate MongoDB or DDS data, CDM reads the first row of the collection as an example of the field list. If the first row of data does not contain all fields of the collection, you need to manually add fields.

When the source link of a job is the :ref:`Link to MongoDB <dataartsstudio_01_0030>`, that is, when data is exported from an on-premises MongoDB or DDS, configure the source job parameters based on :ref:`Table 1 <dataartsstudio_01_0055__en-us_topic_0108275308_table31823995163953>`.

.. _dataartsstudio_01_0055__en-us_topic_0108275308_table31823995163953:

.. table:: **Table 1** Parameter description

   +-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+------------------------+
   | Parameter             | Description                                                                                                                                                                                  | Example Value          |
   +=======================+==============================================================================================================================================================================================+========================+
   | Database Name         | Name of the database from which data will be migrated                                                                                                                                        | mongodb                |
   +-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+------------------------+
   | Collection Name       | Collection name, similar to the table name of a relational database. Click the icon next to the text box to go to the page for selecting the collection or directly enter a collection name. | COLLECTION             |
   |                       |                                                                                                                                                                                              |                        |
   |                       | If the desired table is not displayed, check whether the table exists or whether the login account has the permission to query metadata.                                                     |                        |
   +-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+------------------------+
   | Filter Condition      | Conditions for filtering documents. CDM migrates only the data that meets the filter conditions. The examples are as follows:                                                                | {'last_name': 'Smith'} |
   |                       |                                                                                                                                                                                              |                        |
   |                       | #. Filter by expression: **{'last_name': 'Smith'}** indicates that all files whose **last_name** value is **Smith** are queried.                                                             |                        |
   |                       |                                                                                                                                                                                              |                        |
   |                       | #. Filter by parameter: **{ x : "john" }, { z : 1 }** indicates that all **z** fields whose **x** is **john** are queried.                                                                   |                        |
   |                       |                                                                                                                                                                                              |                        |
   |                       | #. Filter by condition: **{ "field" : { $gt: 5 } }** indicates that the **field** values greater than 5 are queried.                                                                         |                        |
   |                       |                                                                                                                                                                                              |                        |
   |                       | #. Filter by time macro:                                                                                                                                                                     |                        |
   |                       |                                                                                                                                                                                              |                        |
   |                       |    {"ts":{$gte:ISODate("${dateformat(yyyy-MM-dd'T'HH:mm:ss.SSS'Z',-1,HOUR)}")}} indicates that the values greater than those after time macro conversion in the **ts** field are queried.    |                        |
   +-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+------------------------+
