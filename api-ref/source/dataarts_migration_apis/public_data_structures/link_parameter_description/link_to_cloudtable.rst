:original_name: dataartsstudio_02_0268.html

.. _dataartsstudio_02_0268:

Link to CloudTable
==================

Description
-----------

By creating a CloudTable link, you can extract data from or load data to CloudTable.

Sample Link
-----------

The following is the message body of a sample link. You are advised to store the AK and SK in ciphertext in the configuration file or environment variables and decrypt them when needed to ensure security.

.. code-block::

   {
     "links": [
       {
         "link-config-values": {
           "configs": [
             {
               "inputs": [
                 {
                   "name": "linkConfig.hbaseType",
                   "value": "CloudTable"
                 },
                 {
                   "name": "linkConfig.zookeeperQuorum",
                   "value": "cloudtable-pass-zk2-bae54VGN.cloudtable.com:2181,cloudtable-pass-zk1-Fu828so2.cloudtable.com:2181"
                 },
                 {
                   "name": "linkConfig.iamAuth",
                   "value": "true"
                 },
                 {
                   "name": "linkConfig.cloudtableUser",
                   "value": "zane"
                 },
                 {
                   "name": "linkConfig.accessKey",
                   "value": "<YOUR AK>"
                 },
                 {
                   "name": "linkConfig.securityKey",
                   "value": "<YOUR SK>"
                 },
                 {
                   "name": "linkConfig.runMode",
                   "value": "EMBEDDED"
                 }
               ],
               "name": "linkConfig"
             }
           ]
         },
         "name": "cloudtablelink",
         "connector-name": "hbase-connector"
       }
     ]
   }

Link Parameters
---------------

+----------------------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| Parameter                  | Mandatory       | Type            | Description                                                                                                                                                                                                                             |
+============================+=================+=================+=========================================================================================================================================================================================================================================+
| linkConfig.hbaseType       | Yes             | Enumeration     | HBase type. The options are as follows:                                                                                                                                                                                                 |
|                            |                 |                 |                                                                                                                                                                                                                                         |
|                            |                 |                 | -  **CloudTable**: link to CloudTable                                                                                                                                                                                                   |
|                            |                 |                 | -  **MRS**: link to MRS                                                                                                                                                                                                                 |
|                            |                 |                 | -  **FusionInsight HD**: link to FusionInsight HD                                                                                                                                                                                       |
|                            |                 |                 | -  **Apache Hadoop**: link to Apache Hadoop                                                                                                                                                                                             |
+----------------------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| linkConfig.zookeeperQuorum | Yes             | String          | ZooKeeper link of CloudTable. This parameter is mandatory for the **CloudTable** link.                                                                                                                                                  |
+----------------------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| linkConfig.iamAuth         | Yes             | Boolean         | If you choose IAM for identity authentication, enter the username, AK, and SK.                                                                                                                                                          |
+----------------------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| linkConfig.runMode         | Yes             | Enumeration     | Running mode of the HBase link. The options are as follows:                                                                                                                                                                             |
|                            |                 |                 |                                                                                                                                                                                                                                         |
|                            |                 |                 | -  **EMBEDDED**: The link instance runs with CDM. This mode delivers better performance.                                                                                                                                                |
|                            |                 |                 | -  **STANDALONE**: The link instance runs in an independent process. If CDM needs to connect to multiple Hadoop data sources (MRS, Hadoop, or CloudTable) with both Kerberos and Simple authentication methods, **STANDALONE** is used. |
+----------------------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| linkConfig.cloudtableUser  | Yes             | String          | Username for accessing the CloudTable cluster                                                                                                                                                                                           |
+----------------------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| linkConfig.accessKey       | Yes             | String          | AK for accessing the CloudTable cluster. You are advised to store it in ciphertext in the configuration file or an environment variable and decrypt it when needed to ensure security.                                                  |
+----------------------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| linkConfig.securityKey     | Yes             | String          | SK for accessing the CloudTable cluster. You are advised to store it in ciphertext in the configuration file or an environment variable and decrypt it when needed to ensure security.                                                  |
+----------------------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
