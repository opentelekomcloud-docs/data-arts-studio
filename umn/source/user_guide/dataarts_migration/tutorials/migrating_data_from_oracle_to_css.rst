:original_name: dataartsstudio_01_0091.html

.. _dataartsstudio_01_0091:

Migrating Data from Oracle to CSS
=================================

Scenario
--------

Cloud Search Service provides users with structured and unstructured data search, statistics, and report capabilities. This section describes how to use CDM to migrate data from the Oracle database to Cloud Search Service. The procedure is as follows:

#. :ref:`Creating a CDM Cluster and Binding an EIP to the Cluster <dataartsstudio_01_0091__en-us_topic_0108275437_section2178135115010>`
#. :ref:`Creating a Cloud Search Service Link <dataartsstudio_01_0091__en-us_topic_0108275437_section13928112795019>`
#. :ref:`Creating an Oracle Link <dataartsstudio_01_0091__en-us_topic_0108275437_section1667801135017>`
#. :ref:`Creating a Migration Job <dataartsstudio_01_0091__en-us_topic_0108275437_section5711134141215>`

Prerequisites
-------------

-  You have subscribed to Cloud Search Service and obtained the IP address and port number of the Cloud Search Service cluster.
-  You have obtained the IP address, name, username, and password of the Oracle database.
-  If the Oracle database is deployed on an on-premises data center or a third-party cloud, ensure that an IP address that can be accessed from the public network has been configured for the Oracle database, or the VPN or Direct Connect between the on-premises data center and has been established.
-  You have uploaded an Oracle database driver by following the instructions provided in :ref:`Managing Drivers <dataartsstudio_01_0132>`.

.. _dataartsstudio_01_0091__en-us_topic_0108275437_section2178135115010:

Creating a CDM Cluster and Binding an EIP to the Cluster
--------------------------------------------------------

#. Create a CDM cluster by following the instructions in :ref:`Creating a Cluster <dataartsstudio_01_0576>`.

   The key configurations are as follows:

   -  The flavor of the CDM cluster is selected based on the amount of data to be migrated. Generally, cdm.medium meets the requirements for most migration scenarios.
   -  The CDM and Cloud Search Service clusters must be in the same VPC. In addition, it is recommended that the CDM cluster be in the same subnet and security group as the Cloud Search Service cluster.
   -  If the same subnet and security group cannot be used for security purposes, ensure that a security group rule has been configured to allow the CDM cluster to access the Cloud Search Service cluster.

#. After the CDM cluster is created, on the **Cluster Management** page, click **Bind EIP** in the **Operation** column to bind an EIP to the cluster. The CDM cluster uses the EIP to access the Oracle data source.

   .. note::

      If SSL encryption is configured for the access channel of a local data source, CDM cannot connect to the data source using the EIP.

.. _dataartsstudio_01_0091__en-us_topic_0108275437_section13928112795019:

Creating a Cloud Search Service Link
------------------------------------

#. Click **Job Management** in the **Operation** column of the CDM cluster. On the displayed page, click the **Links** tab and then **Create Link**. The **Select Connector** page is displayed.
#. Select **Cloud Search Service** and click **Next**. On the page that is displayed, configure the CSS link parameters.

   -  **Name**: Enter a custom link name, for example, **csslink**.
   -  **Elasticsearch Server List**: Enter the IP address and port number of the Cloud Search Service cluster (cluster later than 5.\ *x*). The format is *ip:port*. Use semicolons to separate multiple addresses. For example, **192.168.0.1:9200;192.168.0.2:9200**.
   -  **Username** and **Password**: Enter the username and password used for logging in to the Cloud Search Service cluster. The user must have the read and write permissions on the database.

#. Click **Save**. The **Link Management** page is displayed.

.. _dataartsstudio_01_0091__en-us_topic_0108275437_section1667801135017:

Creating an Oracle Link
-----------------------

#. Click **Job Management** in the **Operation** column of the CDM cluster. On the displayed page, click the **Links** tab and then **Create Link**. The **Select Connector** page is displayed.
#. Select **Oracle** and click **Next** to configure parameters for the Oracle link.

   -  **Name**: Enter a custom link name, for example, **oracle_link**.
   -  **Database Server** and **Port**: Enter the address and port number of the Oracle server.
   -  **Database Name**: Enter the name of the Oracle database whose data is to be exported.
   -  **Username** and **Password**: Enter the username and password used for logging in to the Oracle database. The user must have the permission to read the Oracle metadata.

#. Click **Save**. The **Link Management** page is displayed.

.. _dataartsstudio_01_0091__en-us_topic_0108275437_section5711134141215:

Creating a Migration Job
------------------------

#. Choose **Table/File Migration** > **Create Job** to create a job for exporting data from the Oracle database to Cloud Search Service.


   .. figure:: /_static/images/en-us_image_0000001373087853.png
      :alt: **Figure 1** Creating a job for migrating data from Oracle to Cloud Search Service

      **Figure 1** Creating a job for migrating data from Oracle to Cloud Search Service

   -  **Job Name**: Enter a unique name.
   -  **Source Job Configuration**

      -  **Source Link Name**: Select the **oracle_link** link created in :ref:`Creating an Oracle Link <dataartsstudio_01_0091__en-us_topic_0108275437_section1667801135017>`.
      -  **Schema/Tablespace**: Enter the name of the database whose data is to be migrated.
      -  **Table Name**: Enter the name of the table to be migrated.
      -  Retain the default values of the optional parameters in **Show Advanced Attributes**. For details, see :ref:`From a Common Relational Database <dataartsstudio_01_0054>`.

   -  **Destination Job Configuration**

      -  **Destination Link Name**: Select the **csslink** link created in :ref:`Creating a Cloud Search Service Link <dataartsstudio_01_0091__en-us_topic_0108275437_section13928112795019>`.
      -  **Index**: Select the Elasticsearch index of the data to be written. You can also enter a new index. CDM automatically creates the index on Cloud Search Service.
      -  **Type**: Select the Elasticsearch type of the data to be written. You can enter a new type. CDM automatically creates a type at the migration destination.
      -  Retain the default values of the optional parameters in **Show Advanced Attributes**. For details, see :ref:`To CSS <dataartsstudio_01_0071>`.

#. Click **Next**. The **Map Field** page is displayed. CDM automatically matches the source and destination fields. See :ref:`Figure 2 <dataartsstudio_01_0091__en-us_topic_0108275437_fig68696231445>`.

   -  If the field mapping is incorrect, you can drag the fields to adjust the mapping.
   -  If the type is automatically created at the migration destination, you need to configure the type and name of each field.
   -  CDM supports field conversion during the migration.

   .. _dataartsstudio_01_0091__en-us_topic_0108275437_fig68696231445:

   .. figure:: /_static/images/en-us_image_0000001373408045.png
      :alt: **Figure 2** Field mapping of Cloud Search Service

      **Figure 2** Field mapping of Cloud Search Service

#. Click **Next** and set task parameters. Generally, retain the default values of all parameters.

   In this step, you can configure the following optional functions:

   -  **Retry Upon Failure**: If the job fails to be executed, you can determine whether to automatically retry. Retain the default value **Never**.
   -  **Group**: Select the group to which the job belongs. The default group is **DEFAULT**. On the **Job Management** page, jobs can be displayed, started, or exported by group.
   -  **Schedule Execution**: To configure scheduled jobs, see :ref:`Scheduling Job Execution <dataartsstudio_01_0082>`. Retain the default value **No**.
   -  **Concurrent Extractors**: Enter the number of extractors to be concurrently executed. Retain the default value **1**.
   -  **Write Dirty Data**: Specify this parameter if data that fails to be processed or filtered out during job execution needs to be written to OBS for future viewing. Before writing dirty data, create an OBS link. Retain the default value **No** so that dirty data is not recorded.
   -  **Delete Job After Completion**: Retain the default value **Do not delete**.

#. Click **Save and Run**. The **Job Management** page is displayed, on which you can view the job execution progress and result.

#. After the job is successfully executed, in the **Operation** column of the job, click **Historical Record** to view the job's historical execution records and read/write statistics.

   On the **Historical Record** page, click **Log** to view the job logs.
