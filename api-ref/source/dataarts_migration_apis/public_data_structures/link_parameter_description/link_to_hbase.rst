:original_name: dataartsstudio_02_0267.html

.. _dataartsstudio_02_0267:

Link to HBase
=============

Description
-----------

By creating an HBase link, you can extract data from or load data to HBase of MRS, FusionInsight HD, and Apache Hadoop.

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
                   "name": "linkConfig.hbaseType",
                   "value": "MRS"
                 },
                 {
                   "name": "linkConfig.host",
                   "value": "192.168.0.34"
                 },
                 {
                   "name": "linkConfig.user",
                   "value": "zephyr"
                 },
                 {
                   "name": "linkConfig.password",
                   "value": "Add password here."
                 },
                 {
                   "name": "linkConfig.authType",
                   "value": "KERBEROS"
                 },
                 {
                   "name": "linkConfig.serviceType",
                   "value": "HDFS"
                 },
                 {
                   "name": "linkConfig.hBaseVersion",
                   "value": "HBASE_2_X"
                 },
                 {
                   "name": "linkConfig.runMode",
                   "value": "EMBEDDED"
                 }
               ],
               "name": "linkConfig"
             }
           ],
           "extended-configs": {
             "name": "linkConfig.extendedFields",
             "value": "eyL1c2VDbHVzdGVyQ29uZmlnIjoiZmFsc2UiJCLjbHVzdGVyQ29uZmlnUHLpbmNpcGFsIjoiemVwaHlyIn0="
           }
         },
         "name": "mrs_hbase_dlf",
         "connector-name": "hbase-connector"
       }
     ]
   }

Link Parameters
---------------

+-------------------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| Parameter               | Mandatory       | Type            | Description                                                                                                                                                                                                                                               |
+=========================+=================+=================+===========================================================================================================================================================================================================================================================+
| linkConfig.hbaseType    | Yes             | Enumeration     | HBase type. The options are as follows:                                                                                                                                                                                                                   |
|                         |                 |                 |                                                                                                                                                                                                                                                           |
|                         |                 |                 | -  **CloudTable**: link to CloudTable Service (CloudTable)                                                                                                                                                                                                |
|                         |                 |                 | -  **MRS**: link to HBase of MRS                                                                                                                                                                                                                          |
|                         |                 |                 | -  **FusionInsight HD**: link to HBase of FusionInsight HD                                                                                                                                                                                                |
|                         |                 |                 | -  **Apache Hadoop**: link to HBase of Apache Hadoop                                                                                                                                                                                                      |
+-------------------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| linkConfig.uri          | No              | String          | NameNode URI required for the link to Apache Hadoop. The format is *ip:port*.                                                                                                                                                                             |
+-------------------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| llinkConfig.host        | No              | String          | IP address of Manager required for the link to MRS or FusionInsight HD                                                                                                                                                                                    |
+-------------------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| linkConfig.port         | No              | String          | Port number of Manager required for the link to FusionInsight HD                                                                                                                                                                                          |
+-------------------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| linkConfig.casPort      | No              | String          | Port number of CAS Server that connects to FusionInsight HD required for the link to FusionInsight HD                                                                                                                                                     |
+-------------------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| linkConfig.hBaseVersion | Yes             | Enumeration     | HBase version                                                                                                                                                                                                                                             |
|                         |                 |                 |                                                                                                                                                                                                                                                           |
|                         |                 |                 | -  HBASE_1_X                                                                                                                                                                                                                                              |
|                         |                 |                 | -  HBASE_2_X                                                                                                                                                                                                                                              |
+-------------------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| linkConfig.user         | No              | String          | Username for logging in to Manager. This parameter is not required if the cluster configuration is used.                                                                                                                                                  |
+-------------------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| linkConfig.password     | No              | String          | Password for logging in to Manager. This parameter is not required if the cluster configuration is used.                                                                                                                                                  |
+-------------------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| linkConfig.authType     | No              | Enumeration     | Authentication method. The options are as follows:                                                                                                                                                                                                        |
|                         |                 |                 |                                                                                                                                                                                                                                                           |
|                         |                 |                 | -  **Simple**: for non-security mode                                                                                                                                                                                                                      |
|                         |                 |                 | -  **Kerberos**: for security mode                                                                                                                                                                                                                        |
+-------------------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| linkConfig.principal    | No              | String          | Account **principal** required for Kerveros authentication. You can contact the administrator to obtain the account.                                                                                                                                      |
+-------------------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| linkConfig.keytab       | No              | FileContent     | Local absolute path of the **keytab** file required for Kerveros authentication. You can also contact the administrator to obtain the file.                                                                                                               |
+-------------------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| linkConfig.serviceType  | No              | String          | Service type Currently, HDFS and HBase are supported.                                                                                                                                                                                                     |
+-------------------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| linkConfig.runMode      | No              | Enumeration     | This parameter is used only when the HBase version is **HBase_2_X**. Possible values are:                                                                                                                                                                 |
|                         |                 |                 |                                                                                                                                                                                                                                                           |
|                         |                 |                 | -  **EMBEDDED**: The link instance runs with CDM. This mode delivers better performance.                                                                                                                                                                  |
|                         |                 |                 |                                                                                                                                                                                                                                                           |
|                         |                 |                 | -  **STANDALONE**: The link instance runs in an independent process. If CDM needs to connect to multiple Hadoop data sources (MRS, Hadoop, or CloudTable) with both Kerberos and Simple authentication methods, **STANDALONE** is used.                   |
|                         |                 |                 |                                                                                                                                                                                                                                                           |
|                         |                 |                 |    If **STANDALONE** is selected, CDM can migrate data between HDFSs of multiple MRS clusters.                                                                                                                                                            |
|                         |                 |                 |                                                                                                                                                                                                                                                           |
|                         |                 |                 | -  **Agent**: The link instance runs on an agent.                                                                                                                                                                                                         |
|                         |                 |                 |                                                                                                                                                                                                                                                           |
|                         |                 |                 |    If **Agent** is not used, and the CDM cluster connects to two or more clusters with Kerberos authentication enabled and the same realm, only one cluster can be connected in **EMBEDDED** mode, and the other clusters must be in **STANDALONE** mode. |
+-------------------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| linkConfig.properties   | No              | Map             | Properties. You can add configuration properties of the client. Each property must contain a name and a value.                                                                                                                                            |
+-------------------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
