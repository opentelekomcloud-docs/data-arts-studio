:original_name: dataartsstudio_01_0056.html

.. _dataartsstudio_01_0056:

From Redis
==========

The Redis service of the third-party cloud cannot serve as the migration source. However, the Redis set up in the on-premises data center or on the ECS can be the migration source and destination.

If the source link of a job is an on-premises Redis link, configure the source job parameters based on :ref:`Table 1 <dataartsstudio_01_0056__en-us_topic_0108275313_table31823995163953>`.

.. _dataartsstudio_01_0056__en-us_topic_0108275313_table31823995163953:

.. table:: **Table 1** Parameter description

   +---------------------+--------------------+----------------------------------------------------------------------------------+-----------------+
   | Category            | Parameter          | Description                                                                      | Example Value   |
   +=====================+====================+==================================================================================+=================+
   | Basic parameters    | Redis Key Prefix   | Key prefix, which is similar to the table name of a relational database          | TABLE           |
   +---------------------+--------------------+----------------------------------------------------------------------------------+-----------------+
   |                     | Value Storage Type | The options are as follows:                                                      | String          |
   |                     |                    |                                                                                  |                 |
   |                     |                    | -  **String**: without column name, such as **value1,value2**                    |                 |
   |                     |                    | -  **Hash**: with column name, such as **column1=value1,column2=value2**         |                 |
   +---------------------+--------------------+----------------------------------------------------------------------------------+-----------------+
   | Advanced attributes | Key Delimiter      | Character used to separate table names and column names of a relational database | \_              |
   +---------------------+--------------------+----------------------------------------------------------------------------------+-----------------+
   |                     | Value Delimiter    | Character used to separate columns when the storage type is string               | ;               |
   +---------------------+--------------------+----------------------------------------------------------------------------------+-----------------+
   |                     | Same Field         | This parameter is displayed when **Value Storage Type** is set to **Hash**.      | Yes             |
   |                     |                    |                                                                                  |                 |
   |                     |                    | The hash key contains the same field.                                            |                 |
   +---------------------+--------------------+----------------------------------------------------------------------------------+-----------------+
