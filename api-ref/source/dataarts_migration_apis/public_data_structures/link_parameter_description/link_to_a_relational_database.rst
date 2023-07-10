:original_name: dataartsstudio_02_0262.html

.. _dataartsstudio_02_0262:

Link to a Relational Database
=============================

Description
-----------

By creating a JDBC link, you can extract data from or load data to the following relational databases:

-  Data Warehouse Service
-  RDS for MySQL
-  RDS for PostgreSQL
-  RDS for SQL Server
-  PostgreSQL
-  Microsoft SQL Server
-  IBM Db2
-  SAP HANA

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
                                   "name": "linkConfig.databaseType",
                                   "value": "MYSQL"
                               },
                               {
                                   "name": "linkConfig.host",
                                   "value": "10.120.205.30"
                               },
                               {
                                   "name": "linkConfig.port",
                                   "value": "3306"
                               },
                               {
                                   "name": "linkConfig.database",
                                   "value": "DB_name"
                               },
                               {
                                   "name": "linkConfig.username",
                                   "value": "username"
                               },
                               {
                                   "name": "linkConfig.password",
                                   "value": "Add password here"
                               },
                               {
                                   "name": "linkConfig.useAgent",
                                   "value": "false"
                               },
                               {
                                   "name": "linkConfig.fetchSize",
                                   "value": "100000"
                               },
                               {
                                   "name": "linkConfig.commitSize",
                                   "value": "10000"
                               },
                               {
                                   "name": "linkConfig.usingNative",
                                   "value": "false"
                               },
                               {
                                   "name": "linkConfig.useSSL",
                                   "value": "false"
                               }
                           ],
                           "name": "linkConfig"
                       }
                   ]
               },
               "name": "mysql_link",
               "connector-name": "generic-jdbc-connector"
           }
       ]
   }

Link Parameters
---------------

+---------------------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| Parameter                 | Mandatory       | Type            | Description                                                                                                                                                                                                            |
+===========================+=================+=================+========================================================================================================================================================================================================================+
| linkConfig.databaseType   | Yes             | Enumeration     | Database type. The options are as follows:                                                                                                                                                                             |
|                           |                 |                 |                                                                                                                                                                                                                        |
|                           |                 |                 | -  ORACLE                                                                                                                                                                                                              |
|                           |                 |                 | -  MYSQL                                                                                                                                                                                                               |
|                           |                 |                 | -  SQLSERVER                                                                                                                                                                                                           |
|                           |                 |                 | -  DB2                                                                                                                                                                                                                 |
|                           |                 |                 | -  POSTGRESQL                                                                                                                                                                                                          |
|                           |                 |                 | -  DWS                                                                                                                                                                                                                 |
|                           |                 |                 | -  DDM                                                                                                                                                                                                                 |
|                           |                 |                 | -  SAP HANA                                                                                                                                                                                                            |
+---------------------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| linkConfig.host           | Yes             | String          | IP address of the database server                                                                                                                                                                                      |
+---------------------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| linkConfig.port           | Yes             | String          | Port number of the database server                                                                                                                                                                                     |
+---------------------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| linkConfig.databaseconfig | No              | Enumeration     | Oracle database link type. This parameter is available only when an Oracle link is created. The options are as follows:                                                                                                |
|                           |                 |                 |                                                                                                                                                                                                                        |
|                           |                 |                 | -  **SERVICENAME**: Use **SERVICE_NAME** to connect to the Oracle database.                                                                                                                                            |
|                           |                 |                 | -  **SID**: Use **SID** to connect to the Oracle database.                                                                                                                                                             |
+---------------------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| linkConfig.sidname        | No              | String          | Oracle instance ID, which is used to differentiate databases by instances. This parameter is available only when an Oracle link is created and the database link type **linkConfig.databaseconfig** is set to **SID**. |
+---------------------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| linkConfig.database       | No              | String          | Database name                                                                                                                                                                                                          |
+---------------------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| linkConfig.username       | Yes             | String          | Username                                                                                                                                                                                                               |
+---------------------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| linkConfig.password       | Yes             | String          | Password                                                                                                                                                                                                               |
+---------------------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| linkConfig.useAgent       | Yes             | Boolean         | Whether to obtain data from the data source through an agent                                                                                                                                                           |
+---------------------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| linkConfig.fetchSize      | No              | String          | Number of data rows obtained each time                                                                                                                                                                                 |
+---------------------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| linkConfig.commitSize     | No              | String          | Number of data rows submitted in each request                                                                                                                                                                          |
+---------------------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| linkConfig.usingNative    | No              | Boolean         | Whether to use the local API acceleration function of the database                                                                                                                                                     |
|                           |                 |                 |                                                                                                                                                                                                                        |
|                           |                 |                 | When creating a MySQL link, you can use the LOAD DATA function of MySQL to accelerate data import and improve the performance of importing data to the MySQL database.                                                 |
+---------------------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| linkConfig.isRds          | No              | Boolean         | Whether RDS is supported. The default value **true** is used for cloud databases and **false** is used for other databases.                                                                                            |
+---------------------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| linkConfig.useSSL         | No              | Boolean         | Whether to enable SSL encrypted transmission for RDS. This parameter is available only when you create a DWS connection.                                                                                               |
+---------------------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| linkConfig.jdbcProperties | No              | Map             | Link attribute, which specifies the JDBC connector attributes of the data source. For details about how to configure the link attributes, see the JDBC connector description of the corresponding database.            |
+---------------------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| linkConfig.version        | No              | Enumeration     | Oracle database version. This parameter is available only when you create an Oracle link. The options are as follows:                                                                                                  |
|                           |                 |                 |                                                                                                                                                                                                                        |
|                           |                 |                 | -  **HIGH_VERSION**: Select this value if the Oracle database version is later than 12.1.                                                                                                                              |
|                           |                 |                 | -  **MED_VERSION**: Select this value if the Oracle database version is 12.1.                                                                                                                                          |
|                           |                 |                 | -  **LOW_VERSION**: Select this value if the Oracle database version is earlier than 12.1.                                                                                                                             |
|                           |                 |                 |                                                                                                                                                                                                                        |
|                           |                 |                 | If error message "java.sql.SQLException: Protocol violation" is displayed, select another option.                                                                                                                      |
+---------------------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| dialect.identifierEnclose | No              | String          | Reference identifier, which is the delimiter between the referenced table names or column names. For details, see the product documentation of the corresponding database.                                             |
+---------------------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
