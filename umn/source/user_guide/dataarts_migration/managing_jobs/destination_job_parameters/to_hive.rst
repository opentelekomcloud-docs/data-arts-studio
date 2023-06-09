:original_name: dataartsstudio_01_0066.html

.. _dataartsstudio_01_0066:

To Hive
=======

If the destination link of a job is the :ref:`Link to Hive <dataartsstudio_01_0026>`, configure the destination job parameters based on :ref:`Table 1 <dataartsstudio_01_0066__en-us_topic_0108275481_table31823995163953>`.

.. _dataartsstudio_01_0066__en-us_topic_0108275481_table31823995163953:

.. table:: **Table 1** Parameter description

   +--------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------------------------------------------------------------------+
   | Parameter                | Description                                                                                                                                                                                                                                                                | Example Value                                                                   |
   +==========================+============================================================================================================================================================================================================================================================================+=================================================================================+
   | Database Name            | Database name. Click the icon next to the text box. The dialog box for selecting the database is displayed.                                                                                                                                                                | default                                                                         |
   +--------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------------------------------------------------------------------+
   | Auto Table Creation      | This parameter is displayed only when the source is a relational database. The options are as follows:                                                                                                                                                                     | Non-auto creation                                                               |
   |                          |                                                                                                                                                                                                                                                                            |                                                                                 |
   |                          | -  **Non-auto creation**: CDM will not automatically create a table.                                                                                                                                                                                                       |                                                                                 |
   |                          | -  **Auto creation**: If the destination database does not contain the table specified by **Table Name**, CDM will automatically create the table. If the table specified by **Table Name** already exists, no table is created and data is written to the existing table. |                                                                                 |
   |                          | -  **Deletion before creation**: CDM deletes the table specified by **Table Name**, and then creates the table again.                                                                                                                                                      |                                                                                 |
   +--------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------------------------------------------------------------------+
   | Table Name               | Destination table name.                                                                                                                                                                                                                                                    | TBL_X                                                                           |
   |                          |                                                                                                                                                                                                                                                                            |                                                                                 |
   |                          | Click the icon next to the text box. The dialog box for selecting the table is displayed.                                                                                                                                                                                  |                                                                                 |
   |                          |                                                                                                                                                                                                                                                                            |                                                                                 |
   |                          | This parameter can be configured as a macro variable of date and time and a path name can contain multiple macro variables. When the macro variable of date and time works with a scheduled job, the incremental data can be synchronized periodically.                    |                                                                                 |
   +--------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------------------------------------------------------------------+
   | Clear Data Before Import | Whether the data in the destination table is cleared before data import. The options are as follows:                                                                                                                                                                       | Yes                                                                             |
   |                          |                                                                                                                                                                                                                                                                            |                                                                                 |
   |                          | -  **Yes**: The data is cleared.                                                                                                                                                                                                                                           |                                                                                 |
   |                          | -  **No**: The data is not cleared. Instead, it will be added to the existing table.                                                                                                                                                                                       |                                                                                 |
   +--------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------------------------------------------------------------------+
   | Partition to Clear       | This parameter is available when **Clear Data Before Import** is set to **Yes**.                                                                                                                                                                                           | Single partition: **year=2020,location=sun**                                    |
   |                          |                                                                                                                                                                                                                                                                            |                                                                                 |
   |                          | When you enter the information about the partitions to be cleared, the data in the partitions will be cleared.                                                                                                                                                             | Multiple partitions: **['year=2020,location=sun', 'year=2021,location=earth']** |
   +--------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------------------------------------------------------------------+

.. note::

   #. When Hive serves as the destination end, a table whose storage format is ORC is automatically created.

   #. When Hive serves as the migration destination, if the storage format is TEXTFILE, delimiters must be explicitly specified in the statement for creating Hive tables. The following gives an example:

      .. code-block::

         CREATE TABLE csv_tbl(
         smallint_value smallint,
         tinyint_value tinyint,
         int_value int,
         bigint_value bigint,
         float_value float,
         double_value double,
         decimal_value decimal(9, 7),
         timestmamp_value timestamp,
         date_value date,
         varchar_value varchar(100),
         string_value string,
         char_value char(20),
         boolean_value boolean,
         binary_value binary,
         varchar_null varchar(100),
         string_null string,
         char_null char(20),
         int_null int
         )
         ROW FORMAT SERDE 'org.apache.hadoop.hive.serde2.OpenCSVSerde'
         WITH SERDEPROPERTIES (
         "separatorChar" = "\t",
         "quoteChar"     = "'",
         "escapeChar"    = "\\"
         )
         STORED AS TEXTFILE;
