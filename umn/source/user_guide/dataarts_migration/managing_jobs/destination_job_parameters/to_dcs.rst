:original_name: dataartsstudio_01_0070.html

.. _dataartsstudio_01_0070:

To DCS
======

If the data is imported to DCS, configure the destination job parameters based on :ref:`Table 1 <dataartsstudio_01_0070__en-us_topic_0108275365_table42991210161426>`.

.. _dataartsstudio_01_0070__en-us_topic_0108275365_table42991210161426:

.. table:: **Table 1** Parameter description

   +-----------------------+----------------------------------------------------------------------------------+-----------------------+
   | Parameter             | Description                                                                      | Example Value         |
   +=======================+==================================================================================+=======================+
   | Redis Key Prefix      | Key prefix, which is similar to the table name of a relational database          | TABLE                 |
   +-----------------------+----------------------------------------------------------------------------------+-----------------------+
   | Value Storage Type    | The options are as follows:                                                      | String                |
   |                       |                                                                                  |                       |
   |                       | -  **String**: without column name, such as **value1,value2**                    |                       |
   |                       | -  **Hash**: with column name, such as **column1=value1,column2=value2**         |                       |
   +-----------------------+----------------------------------------------------------------------------------+-----------------------+
   | Key Delimiter         | Character used to separate table names and column names of a relational database | \_                    |
   +-----------------------+----------------------------------------------------------------------------------+-----------------------+
   | Value Delimiter       | Character used to separate columns when the storage type is string               | ;                     |
   +-----------------------+----------------------------------------------------------------------------------+-----------------------+
