:original_name: dataartsstudio_01_0132.html

.. _dataartsstudio_01_0132:

Managing Drivers
================

The Java Database Connectivity (JDBC) provides programmatic access to relational databases. Applications can execute SQL statements and retrieve data using the JDBC API.

Before connecting CDM to a relational database, you need to upload the JDK 8 .jar driver of the relational database.

Prerequisites
-------------

-  A cluster has been created.
-  You have downloaded one of the drivers listed in :ref:`Table 1 <dataartsstudio_01_0132__en-us_topic_0286032703_table10609618172919>`.
-  (Optional) An SFTP link has been created by referring to :ref:`Link to an FTP or SFTP Server <dataartsstudio_01_0028>` and the corresponding driver has been uploaded to the offline file server.

.. _dataartsstudio_01_0132__en-us_topic_0286032703_section631855342818:

How Do I Obtain a Driver?
-------------------------

Select a driver version that adapts to the database type. Note that the version of the uploaded driver does not need to match the version of the database to be connected. Obtain the JDK8 .jar driver of the recommended version by referring to :ref:`Table 1 <dataartsstudio_01_0132__en-us_topic_0286032703_table10609618172919>`.

.. _dataartsstudio_01_0132__en-us_topic_0286032703_table10609618172919:

.. table:: **Table 1** Drivers

   +--------------------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Relational Database Type | Driver Name     | How to Obtain                                                                                                               | Recommended Version                                                                                                                                            |
   +==========================+=================+=============================================================================================================================+================================================================================================================================================================+
   | -  RDS for MySQL         | MySQL           | https://downloads.mysql.com/archives/c-j/                                                                                   | mysql-connector-java-5.1.48.jar                                                                                                                                |
   | -  MySQL                 |                 |                                                                                                                             |                                                                                                                                                                |
   +--------------------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Oracle                   | ORACLE_6        | Driver packages: https://www.oracle.com/database/technologies/appdev/jdbc-downloads.html                                    | ojdbc8.jar for version 12.2.0.1                                                                                                                                |
   |                          |                 |                                                                                                                             |                                                                                                                                                                |
   |                          | ORACLE_7        | Driver packages of historical versions: https://repo1.maven.org/maven2/com/oracle/database/jdbc/                            | .. note::                                                                                                                                                      |
   |                          |                 |                                                                                                                             |                                                                                                                                                                |
   |                          | ORACLE_8        |                                                                                                                             |    New versions (for example, Oracle Database 21c (21.3) drivers) are not supported. If they are used, the schema name cannot be obtained during job creation. |
   +--------------------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | -  RDS for PostgreSQL    | POSTGRESQL      | https://mvnrepository.com/artifact/org.postgresql/postgresql                                                                | postgresql-42.3.4.jar for version 42.3.4                                                                                                                       |
   | -  PostgreSQL            |                 |                                                                                                                             |                                                                                                                                                                |
   +--------------------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | -  RDS for SQL Server    | SQLServer       | https://docs.microsoft.com/en-us/sql/connect/jdbc/release-notes-for-the-jdbc-driver?view=sql-server-ver15#previous-releases | sqljdbc42.jar                                                                                                                                                  |
   | -  Microsoft SQL Server  |                 |                                                                                                                             |                                                                                                                                                                |
   +--------------------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | DM                       | DM              | Obtain **DmJdbcDriver18.jar** from the DM installation directory **/dmdbms/drivers/jdbc**.                                  | DmJdbcDriver18.jar                                                                                                                                             |
   +--------------------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Doris                    | MYSQL           | https://downloads.mysql.com/archives/c-j/                                                                                   | mysql-connector-java-5.1.48.jar                                                                                                                                |
   +--------------------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | POSTGRESQL_KINGBASE      | KINGBASE        | :ref:`https://www.kingbase.com.cn/rjcxxz/index.htm <dataartsstudio_01_0132>`                                                | Driver version matching the KingBase database version                                                                                                          |
   +--------------------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------+

Procedure
---------

#. Access the CDM console, choose **Cluster Management** in the navigation pane, locate the target cluster, and choose **Job Management** > **Link Management** > **Driver Management**. On the **Driver Management** page, upload a driver.


   .. figure:: /_static/images/en-us_image_0000002305441101.png
      :alt: **Figure 1** Uploading a driver

      **Figure 1** Uploading a driver

#. Click **Upload** in the **Operation** column and select a local driver.

   Alternatively, click **Copy from SFTP** in the **Operation** column and configure the **SFTP Link** name and **Driver File Path**.

#. (Optional) If you have uploaded an updated version of a driver, you must restart the CDM cluster for the new driver to take effect.
