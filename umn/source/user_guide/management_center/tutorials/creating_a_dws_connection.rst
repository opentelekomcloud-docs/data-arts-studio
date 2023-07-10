:original_name: dataartsstudio_01_0352.html

.. _dataartsstudio_01_0352:

Creating a DWS Connection
=========================

This section describes how to create a DWS connection between DataArts Studio and the data lake base.

Prerequisites
-------------

-  You have created a data lake to connect, for example, a database or cloud service supported by DataArts Studio.

   -  Before creating a DWS data connection, ensure that you have created a cluster in DWS and have the permissions required to view Key Management Service (KMS) keys.
   -  Before creating an MRS HBase, MRS Hive, MRS Kafka, MRS Presto, or MRS Spark connection, ensure that you have created an MRS cluster and selected required components.
   -  Before creating an RDS data connection, ensure that you have an RDS database instance. Currently, DataArts Studio supports only MySQL and PostgreSQL databases in RDS.

-  The data lake to connect communicates with the DataArts Studio instance properly.

   -  If the data lake is an on-premises database, a public network or a dedicated connection is required. Ensure that the host where the data source is located can access the public network and the port has been enabled in the firewall rule.
   -  If the data lake is a cloud service (such as DWS and MRS), the following requirements must be met for network interconnection:

      -  If the CDM cluster in the DataArts Studio instance and the cloud service are in different regions, a public network or a dedicated connection is required.
      -  If the CDM cluster in the DataArts Studio instance and the cloud service are in the same region, VPC, subnet, and security group, they can communicate with each other by default. If they are in the same VPC but in different subnets or security groups, you must configure routing rules and security group rules. For details about how to configure routing rules, see **Adding Routes** in *Virtual Private Cloud (VPC) Usage Guide*. For details about how to configure security group rules, see **Security Group** > **Adding a Security Group Rule** in *Virtual Private Cloud (VPC) Usage Guide*.
      -  The cloud service instance and the DataArts Studio workspace belong to the same enterprise project. If they do not, you can modify the enterprise project of the workspace.

Creating a Data Connection
--------------------------

#. On the DataArts Studio console, locate a workspace and click **Management Center**.


   .. figure:: /_static/images/en-us_image_0000001373087833.png
      :alt: **Figure 1** Management Center

      **Figure 1** Management Center

2. In the navigation pane, choose **Manage Data Connections**.


   .. figure:: /_static/images/en-us_image_0000001373168637.png
      :alt: **Figure 2** Manage Data Connections

      **Figure 2** Manage Data Connections

3. On the **Manage Data Connections** page, click **Create Data Connection**. In the displayed dialog box, select **DWS** for **Data Connection Type** and set other parameters based on the descriptions in :ref:`Table 1 <dataartsstudio_01_0352__table11826143220444>`.


   .. figure:: /_static/images/en-us_image_0000001322088112.png
      :alt: **Figure 3** Create Data Connection

      **Figure 3** Create Data Connection


   .. figure:: /_static/images/en-us_image_0000001373288457.png
      :alt: **Figure 4** DWS connection parameters

      **Figure 4** DWS connection parameters

   .. _dataartsstudio_01_0352__table11826143220444:

   .. table:: **Table 1** DWS data connection

      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter             | Mandatory             | Description                                                                                                                                                                                                                                                                                                                                                                                                  |
      +=======================+=======================+==============================================================================================================================================================================================================================================================================================================================================================================================================+
      | Data Connection Name  | Yes                   | The name of the data connection to create. Data connection names can contain 1 to 50 characters. They can include only letters, numbers, underscores (_), and hyphens (-).                                                                                                                                                                                                                                   |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Tag                   | No                    | The attribute of the data connection to create. Tags make management easier.                                                                                                                                                                                                                                                                                                                                 |
      |                       |                       |                                                                                                                                                                                                                                                                                                                                                                                                              |
      |                       |                       | .. note::                                                                                                                                                                                                                                                                                                                                                                                                    |
      |                       |                       |                                                                                                                                                                                                                                                                                                                                                                                                              |
      |                       |                       |    The name of the tag. Only letters, numbers, and underscores (_) are allowed. Tag names cannot start with underscores (_). Enter up to 100 characters.                                                                                                                                                                                                                                                     |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Manual                | Yes                   | You can turn off or turn on to disable or enable the **Manual** function.                                                                                                                                                                                                                                                                                                                                    |
      |                       |                       |                                                                                                                                                                                                                                                                                                                                                                                                              |
      |                       |                       | -  When **Manual** is disabled, you do not need to enter the IP address and port.                                                                                                                                                                                                                                                                                                                            |
      |                       |                       | -  When **Manual** is enabled, you must enter the IP address and port.                                                                                                                                                                                                                                                                                                                                       |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | IP Address            | No                    | The IP address for accessing the cluster database through the internal network. This parameter is mandatory when **Manual** is enabled. The private network address is automatically generated when you create a cluster.                                                                                                                                                                                    |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Port                  | No                    | The database port specified during DWS cluster creation. This parameter is mandatory when **Manual** is enabled. Ensure that you have enabled this port in the security group rule so that the DataArts Studio instance can connect to the database in the DWS cluster through this port.                                                                                                                    |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | SSL Connection        | Yes                   | DWS supports SSL encryption and certificate authentication for communication between the client and server. You can use **SSL Connection** to set the communication mode. If **SSL Connection** is enabled, only SSL encryption can be used. If **SSL Connection** is disabled, both modes can be used. **SSL Connection** is disabled by default.                                                           |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Cluster Name          | Yes                   | The name of the selected DWS cluster.                                                                                                                                                                                                                                                                                                                                                                        |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Username              | Yes                   | The database username, which is specified when the DWS cluster is created.                                                                                                                                                                                                                                                                                                                                   |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Password              | Yes                   | The password for accessing the database, which is specified when the DWS cluster is created.                                                                                                                                                                                                                                                                                                                 |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | KMS Key               | Yes                   | Name of the KMS key.                                                                                                                                                                                                                                                                                                                                                                                         |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Connection Type       | Yes                   | Connection type. **Proxy connection** is recommended.                                                                                                                                                                                                                                                                                                                                                        |
      |                       |                       |                                                                                                                                                                                                                                                                                                                                                                                                              |
      |                       |                       | -  **Proxy connection**: An agent (CDM cluster) is used to access DWS clusters.                                                                                                                                                                                                                                                                                                                              |
      |                       |                       | -  **Direct connection**: You can access DWS clusters directly.                                                                                                                                                                                                                                                                                                                                              |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Agent                 | No                    | This parameter is mandatory when **Connection Type** is set to **Proxy connection**.                                                                                                                                                                                                                                                                                                                         |
      |                       |                       |                                                                                                                                                                                                                                                                                                                                                                                                              |
      |                       |                       | Data Warehouse Service (DWS) is not a fully managed service and thus cannot be directly connected to DataArts Studio. A CDM cluster can provide an agent for DataArts Studio to communicate with non-fully-managed services. Therefore, you need to select a CDM cluster when creating a DWS data connection. If no CDM cluster is available, create one through the DataArts Migration incremental package. |
      |                       |                       |                                                                                                                                                                                                                                                                                                                                                                                                              |
      |                       |                       | As a network proxy, the CDM cluster must be able to communicate with the DWS cluster. To ensure network connectivity, the CDM cluster must be in the same region, AZ, VPC, and subnet as the DWS cluster. The security group rule must also allow the CDM cluster communicate with the DWS cluster.                                                                                                          |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

4. Click **Test** to test connectivity of the data connection. If the test fails, the data connection fails to be created.

5. After the test is successful, click **OK** to create the data connection.

Reference
---------

#. What should I do if the connection test fails when I enable the SSL connection during the creation of a DWS data connection?

   The failure may be caused by the rights separation function of the DWS cluster. On the DWS console, click the corresponding cluster, choose **Security Settings**, and disable **Rights Separation**.


   .. figure:: /_static/images/en-us_image_0000001373408141.png
      :alt: **Figure 5** Disabling Rights Separation for the DWS cluster

      **Figure 5** Disabling Rights Separation for the DWS cluster

#. Why does a DWS data connection fail to obtain information about databases or tables?

   The possible cause is that the CDM cluster is stopped or a concurrency conflict occurs. You can switch to another agent to temporarily avoid this issue.
