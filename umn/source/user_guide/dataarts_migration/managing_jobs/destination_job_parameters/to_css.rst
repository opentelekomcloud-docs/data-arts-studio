:original_name: dataartsstudio_01_0071.html

.. _dataartsstudio_01_0071:

To CSS
======

If the destination link of a job is the :ref:`Link to Elasticsearch/CSS <dataartsstudio_01_0035>`, that is, when data is imported to CSS, configure the destination job parameters based on :ref:`Table 1 <dataartsstudio_01_0071__en-us_topic_0108275347_table5046103815165>`.

.. _dataartsstudio_01_0071__en-us_topic_0108275347_table5046103815165:

.. table:: **Table 1** Parameter description

   +---------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
   | Parameter                 | Description                                                                                                                                                                                                                        | Example Value         |
   +===========================+====================================================================================================================================================================================================================================+=======================+
   | Index                     | Elasticsearch index, which is similar to the name of a relational database. CDM supports automatic creation of indexes and field types. The index and field type names can contain only lowercase letters.                         | index                 |
   +---------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
   | Type                      | Elasticsearch type, which is similar to the table name of a relational database. The type name can contain only lowercase letters.                                                                                                 | type                  |
   +---------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
   | Pipeline ID               | Pipeline used to convert the data format after data is transferred to Elasticsearch. Pipeline IDs are ready for use after being created in Kibana.                                                                                 | pipeline_id           |
   +---------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
   | Periodically Create Index | For streaming jobs that continuously write data to Elasticsearch, CDM periodically creates indexes and writes data to the indexes, which helps you delete expired data. The indexes can be created based on the following periods: | Every hour            |
   |                           |                                                                                                                                                                                                                                    |                       |
   |                           | -  **Every hour**: CDM creates indexes on the hour. The new indexes are named in the format of *Index name+Year+Month+Day+Hour*, for example, **index2018121709**.                                                                 |                       |
   |                           | -  **Every day**: CDM creates indexes at 00:00 every day. The new indexes are named in the format of *Index name+Year+Month+Day*, for example, **index20181217**.                                                                  |                       |
   |                           | -  **Every week**: CDM creates indexes at 00:00 every Monday. The new indexes are named in the format of *Index name+Year+Week*, for example, **index201842**.                                                                     |                       |
   |                           | -  **Every month**: CDM creates indexes at 00:00 on the first day of each month. The new indexes are named in the format of *Index name+Year+Month*, for example, **index201812**.                                                 |                       |
   |                           | -  **Do not create**: Do not create indexes periodically.                                                                                                                                                                          |                       |
   |                           |                                                                                                                                                                                                                                    |                       |
   |                           | When extracting data from a file, you must configure a single extractor, which means setting **Concurrent Extractors** to **1**. Otherwise, this parameter is invalid.                                                             |                       |
   +---------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
