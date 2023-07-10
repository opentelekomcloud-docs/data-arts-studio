:original_name: dataartsstudio_01_0099.html

.. _dataartsstudio_01_0099:

Migrating the Entire Elasticsearch Database to CSS
==================================================

Scenario
--------

CSS provides users with structured and unstructured data search, statistics, and report capabilities. This section describes how to use CDM to migrate the entire Elasticsearch database to Cloud Search Service. The procedure is as follows:

#. :ref:`Creating a CDM Cluster and Binding an EIP to the Cluster <dataartsstudio_01_0099__en-us_topic_0123220230_section286612269318>`
#. :ref:`Creating a Cloud Search Service Link <dataartsstudio_01_0099__en-us_topic_0123220230_section14541143415338>`
#. :ref:`Creating an Elasticsearch Link <dataartsstudio_01_0099__en-us_topic_0123220230_section46839536342>`
#. :ref:`Creating an Entire DB Migration Job <dataartsstudio_01_0099__en-us_topic_0123220230_section1508747294234>`

Prerequisites
-------------

-  You have sufficient EIP quota.

-  You have subscribed to CSS and obtained the IP address and port number of the CSS cluster.

-  You have obtained the IP address, port number, username, and password of the on-premises Elasticsearch database server.

   If the Elasticsearch server is deployed on an on-premises data center or a third-party cloud, ensure that an IP address that can be accessed from the public network has been configured for the Elasticsearch server, or the VPN or Direct Connect between the on-premises data center and has been established.

.. _dataartsstudio_01_0099__en-us_topic_0123220230_section286612269318:

Creating a CDM Cluster and Binding an EIP to the Cluster
--------------------------------------------------------

#. Create a CDM cluster by following the instructions in :ref:`Creating a Cluster <dataartsstudio_01_0576>`.

   The key configurations are as follows:

   -  The flavor of the CDM cluster is selected based on the amount of data to be migrated. Generally, cdm.medium meets the requirements for most migration scenarios.
   -  The CDM and Cloud Search Service clusters must be in the same VPC. In addition, it is recommended that the CDM cluster be in the same subnet and security group as the Cloud Search Service cluster.
   -  If the same subnet and security group cannot be used for security purposes, ensure that a security group rule has been configured to allow the CDM cluster to access the Cloud Search Service cluster.

#. After the CDM cluster is created, on the **Cluster Management** page, click **Bind EIP** in the **Operation** column to bind an EIP to the cluster. The CDM cluster uses the EIP to access the on-premises Elasticsearch.

   .. note::

      If SSL encryption is configured for the access channel of a local data source, CDM cannot connect to the data source using the EIP.

.. _dataartsstudio_01_0099__en-us_topic_0123220230_section14541143415338:

Creating a Cloud Search Service Link
------------------------------------

#. Click **Job Management** in the **Operation** column of the CDM cluster. On the displayed page, click the **Links** tab and then **Create Link**. The **Select Connector** page is displayed.
#. Select **Cloud Search Service** and click **Next**. On the page that is displayed, configure the CSS link parameters.

   -  **Name**: Enter a custom link name, for example, **csslink**.
   -  **Elasticsearch Server List**: Enter the IP address and port number of the Cloud Search Service cluster (cluster later than 5.\ *x*). The format is *ip:port*. Use semicolons to separate multiple addresses. For example, **192.168.0.1:9200;192.168.0.2:9200**.
   -  **Username** and **Password**: Enter the username and password used for logging in to the Cloud Search Service cluster. The user must have the read and write permissions on the database.

#. Click **Save**. The **Link Management** page is displayed.

.. _dataartsstudio_01_0099__en-us_topic_0123220230_section46839536342:

Creating an Elasticsearch Link
------------------------------

#. On the **Cluster Management** page, locate a cluster and click **Job Management** in the **Operation** column. On the displayed page, click the **Links** tab and then **Create Link**.
#. Select **Elasticsearch** and click **Next** to configure parameters for the Elasticsearch link. The parameters are the same as those for the CSS link.

   -  **Name**: Enter a custom link name, for example, **es_link**.
   -  **Elasticsearch Server List**: Enter the IP address and port number of the on-premises Elasticsearch database. Use semicolons to separate multiple addresses.

#. Click **Save**. The **Link Management** page is displayed.

.. _dataartsstudio_01_0099__en-us_topic_0123220230_section1508747294234:

Creating an Entire DB Migration Job
-----------------------------------

#. Choose **Entire DB Migration** > **Create Job** to create an entire DB migration job.


   .. figure:: /_static/images/en-us_image_0000001373288729.png
      :alt: **Figure 1** Creating an entire DB migration job

      **Figure 1** Creating an entire DB migration job

   -  **Job Name**: Enter a unique name.
   -  **Source Job Configuration**

      -  **Source Link Name**: Select the **es_link** link created in :ref:`Creating an Elasticsearch Link <dataartsstudio_01_0099__en-us_topic_0123220230_section46839536342>`.
      -  **Index**: Click the icon next to the text box to select an index in the on-premises Elasticsearch database or manually enter an index name. The name can contain only lowercase letters. If multiple indexes need to be migrated at a time, set this parameter to a wildcard character. CDM migrates all indexes that meet the wildcard condition. For example, if this parameter is set to **cdm\***, CDM migrates all indexes starting with **cdm**, such as **cdm01**, **cdmB3**, **cdm_45** and so on.

   -  **Destination Job Configuration**

      -  **Destination Link Name**: Select the **csslink** link created in :ref:`Creating a Cloud Search Service Link <dataartsstudio_01_0099__en-us_topic_0123220230_section14541143415338>`.
      -  **Index**: Enter the index of the data to be written. You can select an existing index in Cloud Search Service or manually enter an index name that does not exist. The name can contain only lowercase letters. CDM automatically creates the index in Cloud Search Service. If multiple indexes are migrated at a time, this parameter cannot be configured. CDM automatically creates indexes at the migration destination.
      -  **Clear Data Before Import**: If the selected index already exists in Cloud Search Service, you can choose whether to clear the data in the index before importing data. If you select **No**, the data is added to the index.

2. Click **Save and Run**. The **Job Management** page is displayed, on which you can view the job execution progress and result.

   A sub-job will be generated for each type in the on-premises Elasticsearch index for concurrent execution. You can click the job name to view the sub-job progress.

3. After the job is successfully executed, in the **Operation** column of the job, click **Historical Record** to view the job's historical execution records, read/write statistics, and job logs (only the sub-jobs have job logs).


   .. figure:: /_static/images/en-us_image_0000001373088213.png
      :alt: **Figure 2** Historical Record

      **Figure 2** Historical Record
