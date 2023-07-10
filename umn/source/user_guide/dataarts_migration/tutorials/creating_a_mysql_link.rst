:original_name: dataartsstudio_01_0131.html

.. _dataartsstudio_01_0131:

Creating a MySQL Link
=====================

MySQL links are applicable to third-party cloud MySQL services and MySQL created in a local data center or ECS. This tutorial describes how to create a MySQL link.

Prerequisites
-------------

-  You have obtained the IP address, port, database name, username, and password for connecting to the MySQL database. In addition, the user must have the read and write permissions on the MySQL database.
-  The on-premises MySQL database can be accessed through the public network. If the MySQL database is deployed on an on-premises data center or a third-party cloud, ensure that an IP address that can be accessed from the public network has been configured for the MySQL database, or the VPN or Direct Connect between the on-premises data center and the cloud service platform has been established.
-  You have created a CDM cluster.


Creating a MySQL Link
---------------------

#. Access the CDM console, choose **Cluster Management** in the navigation pane, locate the target cluster, and choose **Job Management** > **Link Management** > **Driver Management**. The **Driver Management** page is displayed.


   .. figure:: /_static/images/en-us_image_0000001321929292.jpg
      :alt: **Figure 1** Uploading a driver

      **Figure 1** Uploading a driver

#. In the upper left corner of the **Driver Management** page, click **Download Driver** to download the MySQL driver. For details, see :ref:`How Do I Obtain a Driver? <dataartsstudio_01_0132__en-us_topic_0286032703_section631855342818>`.

#. On the **Driver Management** page, upload the MySQL driver using either of the following methods:

   Click **Upload** in the **Operation** column and select a local driver.

   Alternatively, click **Copy from SFTP** in the **Operation** column and configure the **SFTP Link** name and **Driver File Path**.

#. On the **Cluster Management** page, click **Job Management** of the cluster and choose **Links** > **Create Link** to enter the page for selecting the connector, as shown in :ref:`Figure 2 <dataartsstudio_01_0131__en-us_topic_0000001147041354_en-us_topic_0284710796_en-us_topic_0111325168_fig15373426133913>`.

   .. _dataartsstudio_01_0131__en-us_topic_0000001147041354_en-us_topic_0284710796_en-us_topic_0111325168_fig15373426133913:

   .. figure:: /_static/images/en-us_image_0000001322407868.png
      :alt: **Figure 2** Selecting a connector type

      **Figure 2** Selecting a connector type

#. Select **MySQL** and click **Next** to configure parameters for the MySQL link.


   .. figure:: /_static/images/en-us_image_0000001322248904.png
      :alt: **Figure 3** Creating a MySQL link

      **Figure 3** Creating a MySQL link

   .. table:: **Table 1** MySQL link parameters

      +-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------+
      | Parameter       | Description                                                                                                                                                                  | Example Value       |
      +=================+==============================================================================================================================================================================+=====================+
      | Name            | Enter a unique link name.                                                                                                                                                    | mysqllink           |
      +-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------+
      | Database Server | IP address or domain name of the MySQL database                                                                                                                              | 192.168.1.110       |
      +-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------+
      | Port            | MySQL database port                                                                                                                                                          | 3306                |
      +-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------+
      | Database Name   | Name of the MySQL database                                                                                                                                                   | sqoop               |
      +-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------+
      | Username        | User who has the read, write, and delete permissions on the MySQL database                                                                                                   | admin               |
      +-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------+
      | Password        | Password of the user                                                                                                                                                         | ``-``               |
      +-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------+
      | Use Local API   | Whether to use the local API of the database for acceleration. (The system attempts to enable the **local_infile** system variable of the MySQL database.)                   | Yes                 |
      +-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------+
      | Use Agent       | Whether to extract data from the data source through an agent                                                                                                                | Yes                 |
      +-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------+
      | Driver Version  | A driver version that adapts to MySQL                                                                                                                                        | ``-``               |
      +-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------+
      | Agent           | Click **Select** and select the agent created in :ref:`Connecting to an Agent <dataartsstudio_01_0128__en-us_topic_0207402273_en-us_topic_0191978474_section1072083564713>`. | ``-``               |
      +-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------+
      | Fetch Size      | Number of rows obtained by each request                                                                                                                                      | 1000                |
      +-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------+
      | Commit Size     | Obtaining data from the source through the agent                                                                                                                             | 1000                |
      +-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------+
      | Link Attributes | Custom attributes of the link                                                                                                                                                | useCompression=true |
      +-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------+
      | Reference Sign  | Delimiter used to separate referenced table names or column names This parameter is left blank by default.                                                                   | '                   |
      +-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------+

#. Click **Save** to return to the **Links** page.

   .. note::

      If an error occurs during the saving, the security settings of the MySQL database are incorrect. In this case, you need to enable the EIP of the CDM cluster to access the MySQL database.
