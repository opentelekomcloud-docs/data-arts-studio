:original_name: dataartsstudio_04_0004.html

.. _dataartsstudio_04_0004:

Step 2: Prepare Data
====================

Preparations Before Using DataArts Studio
-----------------------------------------

If you are new to DataArts Studio, create a cloud platform account, create a DataArts Studio instance, create workspaces, and make other preparations. For details, see "Creating and Configuring a DataArts Studio Instance" in *User Guide*. Then you can go to the created workspace and start using DataArts Studio.

In this example, the has all the permissions required for performing all the data operations on DataArts Studio so that the entire data governance process using DataArts Studio can be demonstrated.

.. _dataartsstudio_04_0004__section167515015515:

Preparing a Data Source
-----------------------

This guide uses the collection of operations statistics from a taxi vendor in 2017 as an example.

.. note::

   The raw data of this example is from `NYC open data platform <https://data.cityofnewyork.us/Transportation/2017-Yellow-Taxi-Trip-Data/biws-g3hs/about_data>`__.

   **You do not need to obtain the raw data**. This example provides sample data that simulates the raw data. You can use the following method to prepare example data: Store example data in a .csv file, upload the .csv file to OBS, and use DataArts Migration of DataArts Studio to integrate the example data into other cloud services.

To prepare example data, perform the following steps:

#. Create a CSV file (UTF-8 without BOM) named **2017_Yellow_Taxi_Trip_Data.csv**, copy the sample data provided in the subsequent section to the CSV file, and save the file.

   To generate a CSV file in Windows, you can perform the following steps:

   a. Use a text editor (for example, Notepad) to create a .txt document and copy the sample data to the document. Then check the total number of rows and check whether the data of rows is correctly separated. (If the sample data is copied from a PDF document, the data in a single row will be wrapped if the data is too long. In this case, you must manually adjust the data to ensure that it is in a single row.)
   b. Choose **File** > **Save as**. In the displayed dialog box, set **Save as type** to **All files (*.*)**, enter the file name with the .csv suffix for **File name**, and select the UTF-8 encoding format (without BOM) to save the file in CSV format.

#. Upload the CSV file to OBS.

   a. Log in to the management console and choose **Storage** > **Object Storage Service** to access the OBS console.

   b. Click **Create Bucket** and set parameters as prompted to create an OBS bucket named **fast-demo**.

      .. note::

         To ensure network connectivity, select the same region for OBS bucket as that for the DataArts Studio instance. If an enterprise project is required, select the enterprise project that is the same as that of the DataArts Studio instance.

      For details about how to create a bucket on the OBS console, see in *Object Storage Service Console Operation Guide*\ **Console Operation Guide > Getting Started > Creating a Bucket** in *Object Storage Service 3.0* *Usage Guide*.

   c. Upload data to OBS bucket **fast-demo**.

      For details about how to upload a file on the OBS console, see in *Object Storage Service Console Operation Guide*\ **Console Operation Guide > Getting Started > Uploading a File** in *Object Storage Service 3.0* *Usage Guide*.

The example data is as follows:

.. code-block::

   VendorID,tpep_pickup_datetime,tpep_dropoff_datetime,passenger_count,trip_distance,RatecodeID,store_and_fwd_flag,PULocationID,DOLocationID,payment_type,fare_amount,extra,mta_tax,tip_amount,tolls_amount,improvement_surcharge,total_amount
   2,02/14/2017 04:08:11 PM,02/14/2017 04:21:53 PM,1,0.91,1,N,237,163,2,9.5,1,0.5,0,0,0.3,11.3
   2,02/14/2017 04:08:11 PM,02/14/2017 04:19:29 PM,2,1.03,1,N,237,229,1,8.5,1,0.5,2.06,0,0.3,12.36
   1,02/14/2017 04:08:12 PM,02/14/2017 04:19:44 PM,1,1.6,1,N,186,163,2,9,1,0.5,0,0,0.3,10.8
   1,02/14/2017 04:08:12 PM,02/14/2017 04:19:15 PM,1,1.2,1,N,48,48,2,8.5,1,0.5,0,0,0.3,10.3
   2,02/14/2017 04:08:12 PM,02/14/2017 04:13:38 PM,5,0.61,1,N,161,162,1,5.5,1,0.5,2.19,0,0.3,9.49
   2,02/14/2017 04:08:12 PM,02/14/2017 05:35:11 PM,1,19.31,2,N,152,132,1,52,4.5,0.5,12.57,5.54,0.3,75.41
   1,02/14/2017 04:08:13 PM,02/14/2017 04:20:53 PM,1,1.9,1,N,236,143,1,10.5,1,0.5,1.85,0,0.3,14.15
   2,02/14/2017 04:08:13 PM,02/14/2017 04:15:54 PM,1,0.61,1,N,48,164,1,6.5,1,0.5,1.66,0,0.3,9.96
   2,02/14/2017 04:08:13 PM,02/14/2017 04:41:40 PM,1,6.04,1,N,244,262,1,25,1,0.5,6.7,0,0.3,33.5
   2,02/14/2017 04:08:13 PM,02/14/2017 04:17:31 PM,1,1.39,1,N,170,234,1,8,1,0.5,1,0,0.3,10.8
   2,02/14/2017 04:08:14 PM,02/14/2017 04:54:11 PM,2,10.12,1,N,140,189,1,37.5,1,0.5,7,0,0.3,46.3
   2,02/14/2017 04:08:14 PM,02/14/2017 04:13:56 PM,1,0.71,1,N,179,7,2,5.5,1,0.5,0,0,0.3,7.3
   2,02/14/2017 04:08:14 PM,02/14/2017 05:04:24 PM,1,18.1,2,N,263,132,1,52,4.5,0.5,15.71,5.54,0.3,78.55
   2,02/14/2017 04:08:14 PM,02/14/2017 04:08:47 PM,1,0.02,1,N,231,231,2,2.5,1,0.5,0,0,0.3,4.3
   2,02/14/2017 04:08:15 PM,02/14/2017 04:18:13 PM,1,1.34,1,N,100,162,1,8,1,0.5,1.2,0,0.3,11
   1,02/14/2017 04:08:16 PM,02/14/2017 04:19:01 PM,1,1.8,1,N,239,151,1,9,1,0.5,2.15,0,0.3,12.95
   2,02/14/2017 04:08:16 PM,02/14/2017 04:15:57 PM,1,1.06,1,N,68,170,1,6.5,1,0.5,1,0,0.3,9.3
   2,02/14/2017 04:08:16 PM,02/14/2017 04:20:08 PM,2,1.5,1,N,161,142,1,9,1,0.5,2.16,0,0.3,12.96
   2,02/14/2017 04:08:16 PM,02/14/2017 04:11:56 PM,1,0.62,1,N,87,88,2,4.5,1,0.5,0,0,0.3,6.3
   2,02/14/2017 04:08:16 PM,02/14/2017 04:13:20 PM,1,0.88,1,N,262,236,2,5.5,1,0.5,0,0,0.3,7.3

The following table lists the taxi trip data:

.. table:: **Table 1** Taxi trip data

   +-----------------------+-----------------------+------------------------------------------------+
   | No.                   | Field Name            | Field Description                              |
   +=======================+=======================+================================================+
   | 1                     | VendorID              | Vendor ID.                                     |
   |                       |                       |                                                |
   |                       |                       | Possible values are:                           |
   |                       |                       |                                                |
   |                       |                       | 1=A Company                                    |
   |                       |                       |                                                |
   |                       |                       | 2=B Company                                    |
   +-----------------------+-----------------------+------------------------------------------------+
   | 2                     | tpep_pickup_datetime  | Time when a passenger gets on a taxi.          |
   +-----------------------+-----------------------+------------------------------------------------+
   | 3                     | tpep_dropoff_datetime | Time when a passenger gets off a taxi.         |
   +-----------------------+-----------------------+------------------------------------------------+
   | 4                     | passenger_count       | Number of passengers.                          |
   +-----------------------+-----------------------+------------------------------------------------+
   | 5                     | trip_distance         | Driving distance.                              |
   +-----------------------+-----------------------+------------------------------------------------+
   | 6                     | ratecodeid            | Charge rate code.                              |
   |                       |                       |                                                |
   |                       |                       | Possible values are:                           |
   |                       |                       |                                                |
   |                       |                       | 1=Standard rate                                |
   |                       |                       |                                                |
   |                       |                       | 2=JFK                                          |
   |                       |                       |                                                |
   |                       |                       | 3=Newark                                       |
   |                       |                       |                                                |
   |                       |                       | 4=Nassau or Westchester                        |
   |                       |                       |                                                |
   |                       |                       | 5=Negotiated fare                              |
   |                       |                       |                                                |
   |                       |                       | 6=Group ride                                   |
   +-----------------------+-----------------------+------------------------------------------------+
   | 7                     | store_fwd_flag        | Store-and-forward flag.                        |
   +-----------------------+-----------------------+------------------------------------------------+
   | 8                     | PULocationID          | Location at which a passenger gets on a taxi.  |
   +-----------------------+-----------------------+------------------------------------------------+
   | 9                     | DOLocationID          | Location at which a passenger gets off a taxi. |
   +-----------------------+-----------------------+------------------------------------------------+
   | 10                    | payment_type          | Payment type.                                  |
   |                       |                       |                                                |
   |                       |                       | Possible values are:                           |
   |                       |                       |                                                |
   |                       |                       | 1=Credit card                                  |
   |                       |                       |                                                |
   |                       |                       | 2=Cash                                         |
   |                       |                       |                                                |
   |                       |                       | 3=No charge                                    |
   |                       |                       |                                                |
   |                       |                       | 4=Dispute                                      |
   |                       |                       |                                                |
   |                       |                       | 5=Unknown                                      |
   |                       |                       |                                                |
   |                       |                       | 6=Voided trip                                  |
   +-----------------------+-----------------------+------------------------------------------------+
   | 11                    | fare_amount           | Fare amount.                                   |
   +-----------------------+-----------------------+------------------------------------------------+
   | 12                    | extra                 | Extra fee.                                     |
   +-----------------------+-----------------------+------------------------------------------------+
   | 13                    | mta_tax               | MTA tax.                                       |
   +-----------------------+-----------------------+------------------------------------------------+
   | 14                    | tip_amount            | Tip amount.                                    |
   +-----------------------+-----------------------+------------------------------------------------+
   | 15                    | tolls_amount          | Toll amount.                                   |
   +-----------------------+-----------------------+------------------------------------------------+
   | 16                    | improvement_surcharge | Improvement surcharge.                         |
   +-----------------------+-----------------------+------------------------------------------------+
   | 17                    | total_amount          | Total amount.                                  |
   +-----------------------+-----------------------+------------------------------------------------+

Preparing a Data Lake
---------------------

Before using DataArts Studio, you need to select cloud services or databases as the data foundation, which provides storage and compute capabilities. DataArts Studio provides one-stop data development, governance, and services based on the data foundation.

DataArts Studio can integrate cloud services such as GaussDB(DWS), DLI, and MRS Hive, as well as conventional databases such as MySQL. For details, see **Management Center > Data Sources Supported by DataArts Studio** in *DataArts Studio User Guide*.

In this example, MapReduce Service (MRS) Hive is used as the data foundation of DataArts Studio. You need to create an MRS security cluster (that is, an MRS cluster with Kerberos authentication enabled). For details, see "Creating a Custom Cluster" in *MapReduce Service (MRS) User Guide*.

To ensure that the MRS cluster can communicate with the DataArts Studio instance, the MRS cluster must meet the following requirements:

-  The MRS cluster must contain a Hive component.

-  If you want to enable automatic generation of quality jobs based on the data standards in DataArts Studio DataArts Architecture, ensure that the MRS cluster version is 2.0.3 or later and that the cluster contains Hive and Spark components and at least four nodes. In this example, this function is required.

   If the connection fails after you select a cluster, check whether the MRS cluster can communicate with the CDM instance which functions as the agent. They can communicate with each other in the following scenarios:

   -  If the CDM cluster in the DataArts Studio instance and the MRS cluster are in different regions, a public network or a dedicated connection is required. If the Internet is used for communication, ensure that an EIP has been bound to the CDM cluster, and the MRS cluster can access the Internet and the port has been enabled in the firewall rule.
   -  If the CDM cluster in the DataArts Studio instance and the MRS cluster are in the same region, VPC, subnet, and security group, they can communicate with each other by default. If they are in the same VPC but in different subnets or security groups, you must configure routing rules and security group rules. For details about how to configure routing rules, see "Adding Routes to a Route Table" in *Virtual Private Cloud (VPC) x.x.x User Guide* in *Virtual Private Cloud (VPC) x.x.x Usage Guide*. For details about how to configure security group rules, see "Security Group" > "Adding a Security Group Rule" in Virtual Private Cloud (VPC) x.x.x User Guide in Virtual Private Cloud (VPC) x.x.x Usage Guide.
   -  The MRS cluster and the DataArts Studio workspace belong to the same enterprise project. If they do not, you can modify the enterprise project of the workspace.

   .. note::

      If an agent is connected to multiple MRS clusters and one of the MRS clusters is deleted or abnormal, connections to the other MRS clusters will be affected. Therefore, you are advised to connect an agent to only one MRS cluster.

Creating a Data Connection on Management Center
-----------------------------------------------

After the data lake is prepared, create a data connection on Management Center to connect to the cloud service that functions as the data lake.

#. Log in to the DataArts Studio console by following the instructions in :ref:`Accessing the DataArts Studio Instance Console <dataartsstudio_01_0001>`.

#. On the DataArts Studio console, locate a workspace and click **Management Center**.

#. On the displayed **Manage Data Connections** page, click **Create Data Connection**.


   .. figure:: /_static/images/en-us_image_0000002234232344.png
      :alt: **Figure 1** Creating a data connection

      **Figure 1** Creating a data connection

#. On the displayed page, configure the following parameters and click **Save**.

   The following part describes how to create an MRS Hive connection.

   -  **Data Connection Type**: **MRS Hive** is selected by default.

   -  **Name**: Enter **mrs_hive_link**.

   -  **Tag**: Enter a new tag name or select an existing tag from the drop-down list box. This parameter is optional.

   -  **Applicable Modules**: Retain the default settings.

   -  **Connection Type**: Select **Proxy connection**.

   -  **Manual**: Select **Cluster Name Mode**. **IP** and **Port** are automatically set.

   -  **MRS Cluster Name**: Select an existing MRS cluster.

   -  **Agent**: Select a DataArts Migration cluster as the connection agent. The DataArts Migration cluster and MRS cluster must be in the same region, AZ, VPC, and subnet, and the security group rule must allow communication between the two clusters. In this example, select the DataArts Migration cluster that is automatically created during DataArts Studio instance creation.

      To connect to an MRS 2.\ *x* cluster, select the DataArts Migration cluster of the 2.\ *x* version as the agent.

   -  **Username**: Enter the Kerberos authentication user. In an MRS policy, user **admin** is the default management user and cannot be used as the authentication user of the cluster that uses Kerberos authentication. Therefore, to create a connection for an MRS cluster that uses Kerberos authentication, perform the following operations:

      a. Log in to MRS Manager as user **admin**.
      b. Choose **System** > **Permission** > **Security Policy** > **Password Policy**. Click **Add Password Policy** and add a policy under which the password never expires.

         -  Set **Password Policy Name** to **neverexp**.
         -  Set **Password Validity Period (Days)** to **0**, indicating that the password never expires.
         -  Set **Password Expiration Notification (Days)** to **0**.
         -  Retain the default values for other parameters.

      c. Choose **System** > **Permission** > **User**. On the page displayed, click **Create** to add a dedicated human-machine user as the Kerberos authentication user and set the password policy to **neverexp**. Select the user group **superGroup** for the user, and assign all roles to the user.

         .. note::

            -  For clusters of MRS 3.1.0 or later, the user must at least have permissions of the **Manager_viewer** role to create data connections in Management Center. To perform database, table, and data operations on components, the user must also have user group permissions of the components.
            -  For clusters earlier than MRS 3.1.0, the user must have permissions of the **Manager_administrator** or **System_administrator** role to create data connections in Management Center.
            -  A user with only the **Manager_tenant** or **Manager_auditor** permission cannot create connections.

      d. Log in to Manager as the new user and change the initial password. Otherwise, the connection fails to be created.
      e. Synchronize IAM users.

         #. Log in to the MRS console.
         #. Choose **Clusters** > **Active Clusters**, select a running cluster, and click its name to go to its details page.
         #. In the **Basic Information** area of the **Dashboard** page, click **Synchronize** on the right side of **IAM User Sync** to synchronize IAM users.

            .. note::

               -  When the policy of the user group to which the IAM user belongs changes from **MRS ReadOnlyAccess** to **MRS CommonOperations**, **MRS FullAccess**, or **MRS Administrator**, wait for 5 minutes until the new policy takes effect after the synchronization is complete because the **SSSD** (System Security Services Daemon) cache of cluster nodes needs time to be updated. Then, submit a job. Otherwise, the job may fail to be submitted.
               -  When the policy of the user group to which the IAM user belongs changes from **MRS CommonOperations**, **MRS FullAccess**, or **MRS Administrator** to **MRS ReadOnlyAccess**, wait for 5 minutes until the new policy takes effect after the synchronization is complete because the **SSSD** cache of cluster nodes needs time to be updated.

   -  **Password**: Enter the password of the Kerberos authentication user.


   .. figure:: /_static/images/en-us_image_0000002269111841.png
      :alt: **Figure 2** Creating an MRS Hive data connection

      **Figure 2** Creating an MRS Hive data connection

Creating a Database
-------------------

According to the implementation process of data lake governance, you are advised to create a database for each of the layers (SDI layer, DWI layer, DWR layer, and DM layer) in the data lake to implement hierarchical sharding. Data sharding is a concept involved in DataArts Architecture.

-  **Source Data Integration (SDI)** copies data from the source system.
-  **Data Warehouse Integration (DWI)** integrates and cleanses data from multiple source systems, and builds ER models based on the third normal form (3NF).
-  **Data Warehouse Report (DWR)** is based on the multi-dimensional model and its data granularity is the same as that of the DWI layer.
-  **Data Mart (DM)** is where multiple types of data are summarized and displayed.

Generally, create a database in the data lake service.

In this example, you can use either of the following methods to create a database in MRS Hive:

-  You can create a database on the DataArts Factory module of DataArts Studio. For details, see **DataArts Factory** > **Data Management** > **Creating a Database** in *DataArts Studio User Guide*.

-  You can also develop and execute a SQL script for creating a database using the DataArts Studio DataArts Factory module or on the MRS client, and then use the script to create a database. For details about how to develop a script in DataArts Factory, see "DataArts Factory" > "Script Development" > "Developing Scripts" > "Developing an SQL Script" in *DataArts Studio User Guide*. For details about how to develop a script using the MRS Client, see "Component Operation Guide" > "Using Hive" > "Using Hive from Scratch" in *MapReduce Service (MRS) User Guide*. Run the following Hive SQL commands to create a database:

   .. code-block::

      -- Create an SDI layer database.
      CREATE DATABASE demo_sdi_db;

      -- Create a DWI layer database.
      CREATE DATABASE demo_dwi_db;

      -- Create a DWR layer database.
      CREATE DATABASE demo_dwr_db;

      -- Create a DM layer database.
      CREATE DATABASE demo_dm_db;

Creating Tables
---------------

Based on sample data, create a source table to store raw data. To migrate data from a file to a database, you must create a destination table in advance. In this example, the data source is a CSV file on OBS instead of a database. When you use DataArts Studio DataArts Migration to migrate data to the cloud, the destination table cannot be automatically created. Therefore, you must create a table on the destination (MRS).

.. note::

   During data migration using DataArts Studio, a destination table can be automatically created for migration from relational databases to Hive and between relational databases. In this case, you do not need to create a table in the destination database in advance.

Run the following SQL statements to create a source table in the **demo_sdi_db** database to store raw data.

In this example, you can use either of the following methods to create a data table in MRS Hive:

-  You can create a table on the DataArts Studio DataArts Factory module. For details, see **DataArts Factory** > **Data Management** > **Creating a Table** in *DataArts Studio User Guide*.

-  You can also develop and execute a SQL script for creating a table using the DataArts Studio DataArts Factory module or on the MRS client, and then use the script to create a table. For details about how to develop a script in DataArts Factory, see "DataArts Factory" > "Script Development" > "Developing Scripts" > "Developing an SQL Script" in *DataArts Studio User Guide*. For details about how to develop a script using the MRS Client, see "Component Operation Guide" > "Using Hive" > "Using Hive from Scratch" in *MapReduce Service (MRS) User Guide*. The following is an example Hive SQL command used to create a raw table in the **demo_sdi_db** database.

   .. code-block::

      DROP TABLE IF EXISTS `sdi_taxi_trip_data`;

      CREATE TABLE demo_sdi_db.`sdi_taxi_trip_data` (
        `VendorID` BIGINT COMMENT '',
        `tpep_pickup_datetime` TIMESTAMP COMMENT '',
        `tpep_dropoff_datetime` TIMESTAMP COMMENT '',
        `passenger_count` BIGINT COMMENT '',
        `trip_distance` DECIMAL(10,2) COMMENT '',
        `ratecodeid` BIGINT COMMENT '',
        `store_fwd_flag` STRING COMMENT '',
        `PULocationID` STRING COMMENT '',
        `DOLocationID` STRING COMMENT '',
        `payment_type` BIGINT COMMENT '',
        `fare_amount` DECIMAL(10,2) COMMENT '',
        `extra` DECIMAL(10,2) COMMENT '',
        `mta_tax` DECIMAL(10,2) COMMENT '',
        `tip_amount` DECIMAL(10,2) COMMENT '',
        `tolls_amount` DECIMAL(10,2) COMMENT '',
        `improvement_surcharge` DECIMAL(10,2) COMMENT '',
        `total_amount` DECIMAL(10,2) COMMENT ''
      );
