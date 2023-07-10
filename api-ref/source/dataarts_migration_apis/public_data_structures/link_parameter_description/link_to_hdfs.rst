:original_name: dataartsstudio_02_0266.html

.. _dataartsstudio_02_0266:

Link to HDFS
============

Description
-----------

By creating an HDFS link, you can extract files from or load files to MRS, FusionInsight HD, or Apache Hadoop. Files in CSV, Parquet, and binary formats are supported.

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
                                   "value": "FusionInsight HD"
                               },
                               {
                                   "name": "linkConfig.host",
                                   "value": "10.120.205.143"
                               },
                               {
                                   "name": "linkConfig.casPort",
                                   "value": "20009"
                               },
                               {
                                   "name": "linkConfig.port",
                                   "value": "28443"
                               },
                               {
                                   "name": "linkConfig.authType",
                                   "value": "KERBEROS"
                               },
                               {
                                   "name": "linkConfig.user",
                                   "value": "admin"
                               },
                               {
                                   "name": "linkConfig.password",
                                   "value": "Add password here"
                               },
                               {
                                   "name": "linkConfig.runMode",
                                   "value": "STANDALONE"
                               }
                           ],
                           "name": "linkConfig"
                       }
                   ]
               },
               "name": "hdfslink",
               "connector-name": "hdfs-connector"
           }
       ]
   }

Link Parameters
---------------

+-----------------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| Parameter             | Mandatory       | Type            | Description                                                                                                                                                                                                                                               |
+=======================+=================+=================+===========================================================================================================================================================================================================================================================+
| linkConfig.hadoopType | Yes             | Enumeration     | Hadoop type. The options are as follows:                                                                                                                                                                                                                  |
|                       |                 |                 |                                                                                                                                                                                                                                                           |
|                       |                 |                 | -  **MRS**: link to HDFS of MRS                                                                                                                                                                                                                           |
|                       |                 |                 | -  **FusionInsight HD**: link to HDFS of FusionInsight HD                                                                                                                                                                                                 |
|                       |                 |                 | -  **Apache Hadoop**: link to HDFS of Apache Hadoop                                                                                                                                                                                                       |
+-----------------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| linkConfig.uri        | No              | String          | NameNode URI required for the link to Apache Hadoop. The format is *ip:port*.                                                                                                                                                                             |
+-----------------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| linkConfig.host       | No              | String          | IP address of Manager required for the link to MRS or FusionInsight HD                                                                                                                                                                                    |
+-----------------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| linkConfig.port       | No              | String          | Port number of Manager required for the link to FusionInsight HD                                                                                                                                                                                          |
+-----------------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| linkConfig.casPort    | No              | String          | Port number of CAS Server that connects to FusionInsight HD required for the link to FusionInsight HD                                                                                                                                                     |
+-----------------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| linkConfig.user       | No              | String          | Username for logging in to Manager. This parameter is not required if the cluster configuration is used.                                                                                                                                                  |
+-----------------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| linkConfig.password   | No              | String          | Password for logging in to Manager. This parameter is not required if the cluster configuration is used.                                                                                                                                                  |
+-----------------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| linkConfig.authType   | No              | Enumeration     | Authentication method. The options are as follows:                                                                                                                                                                                                        |
|                       |                 |                 |                                                                                                                                                                                                                                                           |
|                       |                 |                 | -  **Simple**: for non-security mode                                                                                                                                                                                                                      |
|                       |                 |                 | -  **Kerberos**: for security mode                                                                                                                                                                                                                        |
+-----------------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| linkConfig.principal  | No              | String          | Account **principal** required for Kerveros authentication. You can contact the administrator to obtain the account. Before using the cluster configuration, you must set this parameter in cluster configuration management.                             |
+-----------------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| linkConfig.keytab     | No              | FileContent     | Local absolute path of the **keytab** file required for Kerveros authentication. You can also contact the administrator to obtain the file. Before using the cluster configuration, you must set this parameter in cluster configuration management.      |
+-----------------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| linkConfig.runMode    | No              | Enumeration     | Running mode of the HDFS link. The options are as follows:                                                                                                                                                                                                |
|                       |                 |                 |                                                                                                                                                                                                                                                           |
|                       |                 |                 | -  **EMBEDDED**: The link instance runs with CDM. This mode delivers better performance.                                                                                                                                                                  |
|                       |                 |                 |                                                                                                                                                                                                                                                           |
|                       |                 |                 | -  **STANDALONE**: The link instance runs in an independent process. If CDM needs to connect to multiple Hadoop data sources (MRS, Hadoop, or CloudTable) with both Kerberos and Simple authentication methods, **STANDALONE** prevails.                  |
|                       |                 |                 |                                                                                                                                                                                                                                                           |
|                       |                 |                 |    If **STANDALONE** is selected, CDM can migrate data between HDFSs of multiple MRS clusters.                                                                                                                                                            |
|                       |                 |                 |                                                                                                                                                                                                                                                           |
|                       |                 |                 | -  **Agent**: The link instance runs on an agent.                                                                                                                                                                                                         |
|                       |                 |                 |                                                                                                                                                                                                                                                           |
|                       |                 |                 |    If **Agent** is not used, and the CDM cluster connects to two or more clusters with Kerberos authentication enabled and the same realm, only one cluster can be connected in **EMBEDDED** mode, and the other clusters must be in **STANDALONE** mode. |
+-----------------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| linkConfig.properties | No              | Map             | Properties. You can add configuration properties of the client. Each property must contain a name and a value.                                                                                                                                            |
+-----------------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
