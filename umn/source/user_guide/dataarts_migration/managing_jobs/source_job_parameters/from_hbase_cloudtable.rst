:original_name: dataartsstudio_01_0050.html

.. _dataartsstudio_01_0050:

From HBase/CloudTable
=====================

When the source link of a job is the :ref:`Link to HBase <dataartsstudio_01_0039>` or :ref:`Link to CloudTable <dataartsstudio_01_0027>`, that is, when data is exported from MRS HBase, FusionInsight HBase, CloudTable, or Apache HBase, configure the source job parameters based on :ref:`Table 1 <dataartsstudio_01_0050__en-us_topic_0108275276_table5046103815165>`.

.. note::

   #. When you migrate data from CloudTable or HBase, CDM reads the first row of the table as an example of the field list. If the first row of data does not contain all fields of the table, you need to manually add fields.
   #. Because HBase is schema-less, CDM cannot obtain the data types. If the data is stored in binary format, CDM cannot parse the data.

   3. When data is exported from HBase or CloudTable, because HBase/CloudTable is schema-less storage systems, CDM requires that the source numeric fields be stored in regular decimal format rather than in binary format. For example, the value 100 needs to be stored as **100** rather than **01100100**.

.. _dataartsstudio_01_0050__en-us_topic_0108275276_table5046103815165:

.. table:: **Table 1** Parameter description

   +-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
   | Parameter             | Description                                                                                                                                                                                                                                             | Example Value         |
   +=======================+=========================================================================================================================================================================================================================================================+=======================+
   | Table Name            | Name of the HBase table that data will be exported from                                                                                                                                                                                                 | TBL_2                 |
   |                       |                                                                                                                                                                                                                                                         |                       |
   |                       | This parameter can be configured as a macro variable of date and time and a path name can contain multiple macro variables. When the macro variable of date and time works with a scheduled job, the incremental data can be synchronized periodically. |                       |
   +-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
   | Column Families       | (Optional) Column families to which the exported data belongs                                                                                                                                                                                           | CF1&CF2               |
   +-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
   | Split Rowkey          | (Optional) Whether to split a rowkey. The default value is **No**.                                                                                                                                                                                      | Yes                   |
   +-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
   | Rowkey Delimiter      | (Optional) Delimiter used to split a rowkey. If this parameter is left empty, the rowkey will not be split.                                                                                                                                             | \|                    |
   +-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
   | Start Time            | (Optional) Start time (including the value) for extracting data. The format is *yyyy-MM-dd HH:mm:ss*. Only the data generated at the specified time and later is extracted.                                                                             | 2019-01-01 20:00:00   |
   |                       |                                                                                                                                                                                                                                                         |                       |
   |                       | This parameter can be set to a macro variable of date and time. When the macro variable of date and time works with a scheduled job, the incremental data can be synchronized periodically.                                                             |                       |
   +-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
   | End Time              | (Optional) End time (excluding the value) for extracting data. The format is *yyyy-MM-dd HH:mm:ss*. Only the data generated before the time point is extracted.                                                                                         | 2019-02-01 20:00:00   |
   |                       |                                                                                                                                                                                                                                                         |                       |
   |                       | This parameter can be set to a macro variable of date and time.                                                                                                                                                                                         |                       |
   +-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
