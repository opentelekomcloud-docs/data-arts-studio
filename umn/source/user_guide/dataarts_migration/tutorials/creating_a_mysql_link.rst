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

#. On the **Driver Management** page, click the document link in the **Recommended Version** column of the MySQL driver and obtain the driver file as instructed.

#. On the **Driver Management** page, upload the MySQL driver using either of the following methods:

   Click **Upload** in the **Operation** column and select a local driver.

   Alternatively, click **Copy from SFTP** in the **Operation** column and configure the **SFTP Link** name and **Driver File Path**.

#. On the **Cluster Management** page, click **Job Management** of the cluster and choose **Links** > **Create Link** to enter the page for selecting the connector.


   .. figure:: /_static/images/en-us_image_0000002305440037.png
      :alt: **Figure 1** Selecting a connector type

      **Figure 1** Selecting a connector type

#. Select **MySQL** and click **Next** to configure parameters for the MySQL link.

   .. table:: **Table 1** MySQL link parameters

      +----------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------+
      | Parameter                  | Description                                                                                                                                                                                 | Example Value       |
      +============================+=============================================================================================================================================================================================+=====================+
      | Name                       | Enter a unique link name.                                                                                                                                                                   | mysqllink           |
      +----------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------+
      | Database Server            | IP address or domain name of the MySQL database                                                                                                                                             | 192.168.1.110       |
      +----------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------+
      | Port                       | MySQL database port                                                                                                                                                                         | 3306                |
      +----------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------+
      | Database Name              | Name of the MySQL database                                                                                                                                                                  | sqoop               |
      +----------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------+
      | Username                   | User who has the read, write, and delete permissions on the MySQL database                                                                                                                  | admin               |
      +----------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------+
      | Password                   | Password of the user                                                                                                                                                                        | ``-``               |
      +----------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------+
      | Use Local API              | Whether to use the local API of the database for acceleration. (The system attempts to enable the **local_infile** system variable of the MySQL database.)                                  | Yes                 |
      +----------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------+
      | Use Agent                  | Whether to extract data from the data source through an agent                                                                                                                               | Yes                 |
      +----------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------+
      | local_infile Character Set | When using local_infile to import data to MySQL, you can configure the encoding format.                                                                                                     | utf8                |
      +----------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------+
      | Driver Version             | A driver version that adapts to MySQL                                                                                                                                                       | ``-``               |
      +----------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------+
      | Agent                      | Click **Select** and select the created agent.                                                                                                                                              | ``-``               |
      +----------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------+
      | Fetch Size                 | Number of rows obtained by each request                                                                                                                                                     | 1000                |
      +----------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------+
      | Commit Size                | Obtaining data from the source through the agent                                                                                                                                            | 1000                |
      +----------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------+
      | Link Attributes            | Custom attributes of the link                                                                                                                                                               | useCompression=true |
      +----------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------+
      | Reference Sign             | Delimiter used to separate referenced table names or column names This parameter is left blank by default.                                                                                  | '                   |
      +----------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------+
      | Batch Size                 | Number of rows written each time. It should be less than **Commit Size**. When the number of rows written reaches the value of **Commit Size**, the rows will be committed to the database. | 100                 |
      +----------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------+

#. Click **Save** to return to the **Links** page.

   .. note::

      If an error occurs during the saving, the security settings of the MySQL database are incorrect. In this case, you need to enable the EIP of the CDM cluster to access the MySQL database.
