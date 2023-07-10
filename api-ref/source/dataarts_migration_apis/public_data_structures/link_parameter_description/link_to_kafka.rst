:original_name: dataartsstudio_02_0274.html

.. _dataartsstudio_02_0274:

Link to Kafka
=============

Description
-----------

By creating a Kafka link, you are able to access open source Kafka and migrate data from Kafka to other data sources as required. Currently, only data export from Kafka is supported.

Sample Link
-----------

.. code-block::

     {
     "links": [
       {
         "link-config-values": {
           "configs": [
             {
               "inputs": [
                 {
                   "name": "linkConfig.hadoopType",
                   "value": "MRS"
                 },
                 {
                   "name": "linkConfig.host",
                   "value": "192.168.1.147"
                 },
                 {
                   "name": "linkConfig.user",
                   "value": "liuhuan1"
                 },
                 {
                   "name": "linkConfig.password",
                   "value": "Add password here."
                 },
                 {
                   "name": "linkConfig.authType",
                   "value": "KERBEROS"
                 }
               ],
               "name": "linkConfig"
             }
           ],
           "extended-configs": {
             "name": "linkConfig.extendedFields",
             "value": "e30="
           }
         },
         "name": "mrs_kafka_link",
         "connector-name": "kafka-connector"
       }
     ]
   }

Link Parameters
---------------

+-----------------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| Parameter             | Mandatory       | Type            | Description                                                                                                                                                                   |
+=======================+=================+=================+===============================================================================================================================================================================+
| linkConfig.hadoopType | Yes             | Enumeration     | Hadoop type. The options are as follows:                                                                                                                                      |
|                       |                 |                 |                                                                                                                                                                               |
|                       |                 |                 | -  **MRS**: link to Kafka of MRS                                                                                                                                              |
|                       |                 |                 | -  **Apache Kafka**: link to Kafka of Apache                                                                                                                                  |
+-----------------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| linkConfig.brokerList | Yes             | String          | This parameter is mandatory for Apache Kafka links. Kafka broker list in *host1:port1,host2:port2* format                                                                     |
+-----------------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| llinkConfig.host      | Yes             | String          | Floating IP address of MRS Manager. Click **Select** next to the **Manager IP** text box to select an MRS cluster. CDM automatically fills in the authentication information. |
+-----------------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| linkConfig.user       | Yes             | String          | Username used for logging in to MRS Manager.                                                                                                                                  |
+-----------------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| linkConfig.password   | Yes             | String          | Password used for logging in to MRS Manager.                                                                                                                                  |
+-----------------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| linkConfig.authType   | Yes             | Enumeration     | Authentication method. The options are as follows:                                                                                                                            |
|                       |                 |                 |                                                                                                                                                                               |
|                       |                 |                 | -  **Simple**: for non-security mode                                                                                                                                          |
|                       |                 |                 | -  **Kerberos**: for security mode                                                                                                                                            |
+-----------------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| linkConfig.properties | No              | Map             | Properties. You can add configuration properties of the client. Each property must contain a name and a value.                                                                |
+-----------------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
