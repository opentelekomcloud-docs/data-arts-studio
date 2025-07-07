:original_name: dataartsstudio_01_0027.html

.. _dataartsstudio_01_0027:

Link to CloudTable
==================

When connecting CDM to CloudTable, configure the parameters as described in :ref:`Table 1 <dataartsstudio_01_0027__en-us_topic_0108275355_table34037531171418>`.

.. note::

   Do not change the password or user when the job is running. If you do so, the password will not take effect immediately and the job will fail.

.. _dataartsstudio_01_0027__en-us_topic_0108275355_table34037531171418:

.. table:: **Table 1** CloudTable link parameters

   +-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------+
   | Parameter             | Description                                                                                                                                    | Example Value                                                                 |
   +=======================+================================================================================================================================================+===============================================================================+
   | Name                  | Link name, which should be defined based on the data source type, so it is easier to remember what the link is for                             | cloudtable_link                                                               |
   +-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------+
   | ZK Link               | Obtain this parameter value from the cluster management page of CloudTable.                                                                    | cloudtable-cdm-zk1.cloudtable.com:2181,cloudtable-cdm-zk2.cloudtable.com:2181 |
   +-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------+
   | IAM Authentication    | If IAM authentication is enabled for the CloudTable cluster to be connected, set this parameter to **Yes**. Otherwise, set this to **No**.     | No                                                                            |
   |                       |                                                                                                                                                |                                                                               |
   |                       | If you select **Yes**, enter the username, AK, and SK.                                                                                         |                                                                               |
   +-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------+
   | Username              | Username used for accessing the CloudTable cluster                                                                                             | admin                                                                         |
   +-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------+
   | AK                    | AK for accessing the CloudTable cluster.                                                                                                       | ``-``                                                                         |
   |                       |                                                                                                                                                |                                                                               |
   |                       | You need to create an access key for the current account and obtain an AK/SK pair.                                                             |                                                                               |
   +-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------+
   | SK                    | SK for accessing the CloudTable cluster.                                                                                                       | ``-``                                                                         |
   |                       |                                                                                                                                                |                                                                               |
   |                       | You need to create an access key for the current account and obtain an AK/SK pair.                                                             |                                                                               |
   +-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------+
   | Use Cluster Config    | You can use the cluster configuration to simplify parameter settings for the Hadoop connection.                                                | No                                                                            |
   +-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------+
   | Cluster Config Name   | This parameter is valid only when **Use Cluster Config** is set to **Yes**. Select a cluster configuration that has been created.              | hadoop_01                                                                     |
   |                       |                                                                                                                                                |                                                                               |
   |                       | For details about how to configure a cluster, see "DataArts Migration" > "Managing Links" > "Managing Cluster Configurations" in *User Guide*. |                                                                               |
   +-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------+

Click **Show Advanced Attributes**, and then click **Add** to add configuration attributes of other clients. The name and value of each attribute must be configured. You can click **Delete** to delete no longer used attributes.
