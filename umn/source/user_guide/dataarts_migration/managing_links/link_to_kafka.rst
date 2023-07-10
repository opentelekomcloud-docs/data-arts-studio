:original_name: dataartsstudio_01_0033.html

.. _dataartsstudio_01_0033:

Link to Kafka
=============

MRS Kafka
---------

When connecting CDM to Kafka of MRS, configure the parameters as described in :ref:`Table 1 <dataartsstudio_01_0033__en-us_topic_0108275385_table3104110173020>`.

.. _dataartsstudio_01_0033__en-us_topic_0108275385_table3104110173020:

.. table:: **Table 1** MRS Kafka link parameters

   +-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
   | Parameter             | Description                                                                                                                                                                                                                                                                                                                                                                   | Example Value         |
   +=======================+===============================================================================================================================================================================================================================================================================================================================================================================+=======================+
   | Name                  | Link name, which should be defined based on the data source type, so it is easier to remember what the link is for                                                                                                                                                                                                                                                            | kafka_link            |
   +-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
   | Manager IP            | Floating IP address of MRS Manager. Click **Select** next to the **Manager IP** text box to select an MRS cluster. CDM automatically fills in the authentication information.                                                                                                                                                                                                 | ``-``                 |
   +-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
   | Username              | Username used for logging in to MRS Manager                                                                                                                                                                                                                                                                                                                                   | ``-``                 |
   |                       |                                                                                                                                                                                                                                                                                                                                                                               |                       |
   |                       | To create a data connection for an MRS security cluster, do not use user **admin**. The **admin** user is the default management page user and cannot be used as the authentication user of the security cluster. You can create an MRS user and set **Username** and **Password** to the username and password of the created MRS user when creating an MRS data connection. |                       |
   |                       |                                                                                                                                                                                                                                                                                                                                                                               |                       |
   |                       | .. note::                                                                                                                                                                                                                                                                                                                                                                     |                       |
   |                       |                                                                                                                                                                                                                                                                                                                                                                               |                       |
   |                       |    -  If the CDM cluster version is 2.9.0 or later and the MRS cluster version is 3.1.0 or later, the created user must have the permissions of the **Manager_viewer** role to create links on CDM. To perform operations on databases, tables, and data of a component, you also need to add the user group permissions of the component to the user.                        |                       |
   |                       |    -  If the CDM cluster version is earlier than 2.9.0 or the MRS cluster version is earlier than 3.1.0, the created user must have the permissions of **Manager_administrator** or **System_administrator** to create links on CDM.                                                                                                                                          |                       |
   |                       |    -  A user with only the **Manager_tenant** or **Manager_auditor** permission cannot create connections.                                                                                                                                                                                                                                                                    |                       |
   +-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
   | Password              | Password used for logging in to MRS Manager                                                                                                                                                                                                                                                                                                                                   | ``-``                 |
   +-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
   | Authentication Method | Authentication method used for accessing MRS                                                                                                                                                                                                                                                                                                                                  | Yes                   |
   |                       |                                                                                                                                                                                                                                                                                                                                                                               |                       |
   |                       | -  **SIMPLE**: for non-security mode                                                                                                                                                                                                                                                                                                                                          |                       |
   |                       | -  **KERBEROS**: for security mode                                                                                                                                                                                                                                                                                                                                            |                       |
   +-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+

Click **Show Advanced Attributes**, and then click **Add** to add configuration attributes of other clients. The name and value of each attribute must be configured. You can click **Delete** to delete no longer used attributes.

Apache Kafka
------------

The Apache Kafka link is applicable to data migration of the third-party Hadoop in the local data center or ECS. You must use Direct Connect to connect to Hadoop in the local data center.

When connecting CDM to Kafka of Apache Hadoop, configure the parameters as described in :ref:`Table 2 <dataartsstudio_01_0033__en-us_topic_0108275385_table1990636915212>`.

.. _dataartsstudio_01_0033__en-us_topic_0108275385_table1990636915212:

.. table:: **Table 2** Parameter description

   +--------------+--------------------------------------------------------------------------------------------------------------------+------------------+
   | Parameter    | Description                                                                                                        | Example Value    |
   +==============+====================================================================================================================+==================+
   | Name         | Link name, which should be defined based on the data source type, so it is easier to remember what the link is for | kafka_link       |
   +--------------+--------------------------------------------------------------------------------------------------------------------+------------------+
   | Kafka broker | IP address and port number of the Kafka broker                                                                     | 192.168.1.1:9092 |
   +--------------+--------------------------------------------------------------------------------------------------------------------+------------------+

Click **Show Advanced Attributes**, and then click **Add** to add configuration attributes of other clients. The name and value of each attribute must be configured. You can click **Delete** to delete no longer used attributes.
