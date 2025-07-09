:original_name: dataartsstudio_01_0088.html

.. _dataartsstudio_01_0088:

Migrating Data from OBS to CSS
==============================

Scenario
--------

CDM supports data migration between cloud services. This section describes how to use CDM to migrate data from OBS to CSS. The procedure is as follows:

#. :ref:`Creating a CDM Cluster <dataartsstudio_01_0088__en-us_topic_0123434187_section2178135115010>`
#. :ref:`Creating a Cloud Search Service Link <dataartsstudio_01_0088__en-us_topic_0123434187_section1770203514912>`
#. :ref:`Creating an OBS Link <dataartsstudio_01_0088__en-us_topic_0123434187_section4967189141012>`
#. :ref:`Creating a Migration Job <dataartsstudio_01_0088__en-us_topic_0123434187_section4397112121511>`

Prerequisites
-------------

-  You have obtained the domain name, port number, AK, and SK for accessing OBS.
-  You have subscribed to Cloud Search Service and obtained the IP address and port number of the Cloud Search Service cluster.

.. _dataartsstudio_01_0088__en-us_topic_0123434187_section2178135115010:

Creating a CDM Cluster
----------------------

Create a CDM cluster.

The key configurations are as follows:

-  The flavor of the CDM cluster is selected based on the amount of data to be migrated. Generally, cdm.medium meets the requirements for most migration scenarios.
-  The CDM and Cloud Search Service clusters must be in the same VPC. In addition, it is recommended that the CDM cluster be in the same subnet and security group as the Cloud Search Service cluster.
-  If the same subnet and security group cannot be used for security purposes, ensure that a security group rule has been configured to allow the CDM cluster to access the Cloud Search Service cluster.

.. _dataartsstudio_01_0088__en-us_topic_0123434187_section1770203514912:

Creating a Cloud Search Service Link
------------------------------------

#. Click **Job Management** in the **Operation** column of the CDM cluster. On the displayed page, click the **Links** tab and then **Create Link**. The **Select Connector** page is displayed.
#. Select **Cloud Search Service** and click **Next**. On the page that is displayed, configure the CSS link parameters.

   -  **Name**: Enter a custom link name, for example, **csslink**.
   -  **Elasticsearch Server List**: Enter the IP address and port number of the Cloud Search Service cluster (cluster later than 5.\ *x*). The format is *ip:port*. Use semicolons to separate multiple addresses. For example, **192.168.0.1:9200;192.168.0.2:9200**.
   -  **Username** and **Password**: Enter the username and password used for logging in to the Cloud Search Service cluster. The user must have the read and write permissions on the database.

#. Click **Save**. The **Link Management** page is displayed.

.. _dataartsstudio_01_0088__en-us_topic_0123434187_section4967189141012:

Creating an OBS Link
--------------------

#. Click **Job Management** in the **Operation** column of the CDM cluster. On the displayed page, click the **Links** tab and then **Create Link**. The **Select Connector** page is displayed.


   .. figure:: /_static/images/en-us_image_0000002305440037.png
      :alt: **Figure 1** Selecting a connector type

      **Figure 1** Selecting a connector type

#. Select **Object Storage Service (OBS)** and click **Next** to configure parameters for the OBS link.

   -  **Name**: Enter a custom link name, for example, **obslink**.

   -  **OBS Server** and **Port**: Enter the actual OBS address information.

   -  **AK** and **SK**: Enter the AK and SK used for logging in to OBS.

      To obtain an access key, perform the following steps:

      a. Log in to the management console, move the cursor to the username in the upper right corner, and select **My Credentials** from the drop-down list.

      b. On the **My Credentials** page, choose **Access Keys**, and click **Create Access Key**. See :ref:`Figure 2 <dataartsstudio_01_0088__en-us_topic_0123434187_en-us_topic_0108275445_en-us_topic_0000001129241845_en-us_topic_0183643042_fig1552229194615>`.

         .. _dataartsstudio_01_0088__en-us_topic_0123434187_en-us_topic_0108275445_en-us_topic_0000001129241845_en-us_topic_0183643042_fig1552229194615:

         .. figure:: /_static/images/en-us_image_0000002270789428.png
            :alt: **Figure 2** Clicking Create Access Key

            **Figure 2** Clicking Create Access Key

      c. Click **OK** and save the access key file as prompted. The access key file will be saved to your browser's configured download location. Open the **credentials.csv** file to view **Access Key Id** and **Secret Access Key**.

         .. note::

            -  Only two access keys can be added for each user.
            -  To ensure access key security, the access key is automatically downloaded only when it is generated for the first time and cannot be obtained from the management console later. Keep them properly.

#. Click **Save**. The **Link Management** page is displayed.

.. _dataartsstudio_01_0088__en-us_topic_0123434187_section4397112121511:

Creating a Migration Job
------------------------

#. Choose **Table/File Migration** > **Create Job** to create a job for exporting data from OBS to Cloud Search Service.


   .. figure:: /_static/images/en-us_image_0000002270791288.png
      :alt: **Figure 3** Creating a job for migrating data from OBS to Cloud Search Service

      **Figure 3** Creating a job for migrating data from OBS to Cloud Search Service

   -  **Job Name**: Enter a unique name.
   -  **Source Job Configuration**

      -  **Source Link Name**: Select the **obslink** link created in :ref:`Creating an OBS Link <dataartsstudio_01_0088__en-us_topic_0123434187_section4967189141012>`.
      -  **Bucket Name**: Select the bucket from which the data will be migrated.
      -  **Source Directory/File**: Set this parameter to the path of the data to be migrated. You can migrate all directories and files in the bucket.
      -  **File Format**: Select **CSV** for migrating files to a data table.
      -  Retain the default values of the optional parameters in **Show Advanced Attributes**.

   -  **Destination Job Configuration**

      -  **Destination Link Name**: Select the **csslink** link created in :ref:`Creating a Cloud Search Service Link <dataartsstudio_01_0088__en-us_topic_0123434187_section1770203514912>`.
      -  **Index**: Select the Elasticsearch index of the data to be written. You can also enter a new index. CDM automatically creates the index on Cloud Search Service.
      -  **Type**: Select the Elasticsearch type of the data to be written. You can enter a new type. CDM automatically creates a type at the migration destination.
      -  Retain the default values of the optional parameters in **Show Advanced Attributes**.

#. Click **Next**. The **Map Field** page is displayed. CDM automatically matches the source and destination fields. See :ref:`Figure 4 <dataartsstudio_01_0088__en-us_topic_0123434187_en-us_topic_0108275437_fig68696231445>`.

   -  If the field mapping is incorrect, you can drag the fields to adjust the mapping.
   -  If the type is automatically created at the migration destination, you need to configure the type and name of each field.
   -  CDM supports field conversion during the migration.

   .. _dataartsstudio_01_0088__en-us_topic_0123434187_en-us_topic_0108275437_fig68696231445:

   .. figure:: /_static/images/en-us_image_0000002305408025.png
      :alt: **Figure 4** Field mapping of Cloud Search Service

      **Figure 4** Field mapping of Cloud Search Service

#. Click **Next** and set task parameters. Generally, retain the default values of all parameters.

   In this step, you can configure the following optional functions:

   -  **Retry If Failed**: Determine whether to automatically retry the job if it fails. Retain the default value **Never**.
   -  **Group**: Select the group to which the job belongs. The default group is **DEFAULT**. On the **Job Management** page, jobs can be displayed, started, or exported by group.
   -  **Schedule Execution**: Determine whether to automatically execute the job at a scheduled time. Retain the default value **No** in this example.
   -  **Concurrent Extractors**: Enter the number of concurrent extractors. An appropriate value improves migration efficiency. Retain the default value **1**.
   -  **Write Dirty Data**: Specify this parameter if data that fails to be processed or filtered out during job execution needs to be written to OBS for future viewing. Before writing dirty data, create an OBS link on the CDM console. Retain the default value **No** so that dirty data is not recorded.


   .. figure:: /_static/images/en-us_image_0000002270846470.png
      :alt: **Figure 5** Configuring the task

      **Figure 5** Configuring the task

#. Click **Save and Run**. The **Job Management** page is displayed, on which you can view the job execution progress and result.

#. After the job is successfully executed, in the **Operation** column of the job, click **Historical Record** to view the job's historical execution records and read/write statistics.

   On the **Historical Record** page, click **Log** to view the job logs.
