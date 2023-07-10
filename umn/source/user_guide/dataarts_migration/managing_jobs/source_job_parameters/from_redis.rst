:original_name: dataartsstudio_01_0056.html

.. _dataartsstudio_01_0056:

From Redis
==========

Because DCS restricts the commands for obtaining keys, it cannot serve as the migration source but can be the migration destination. The Redis service of the third-party cloud cannot serve as the migration source. However, the Redis set up in the on-premises data center or on the ECS can be the migration source and destination.

When data is exported from an on-premises Redis, configure source job parameters as described in :ref:`Table 1 <dataartsstudio_01_0056__en-us_topic_0108275313_table31823995163953>`.

.. _dataartsstudio_01_0056__en-us_topic_0108275313_table31823995163953:

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
   | Same Field            | This parameter is displayed when **Value Storage Type** is set to **Hash**.      | Yes                   |
   |                       |                                                                                  |                       |
   |                       | The hash key contains the same field.                                            |                       |
   +-----------------------+----------------------------------------------------------------------------------+-----------------------+
