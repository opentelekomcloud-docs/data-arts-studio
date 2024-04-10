:original_name: dataartsstudio_02_0050.html

.. _dataartsstudio_02_0050:

Creating a Connection (to Be Taken Offline)
===========================================

.. note::

   The connection management capability is provided by Management Center. APIs of Management Center are recommended.

Function
--------

This API is used to create a connection. The supported connection types include DWS, DLI, Spark SQL, RDS, CloudTable, and Hive.

URI
---

-  URI format

   POST /v1/{project_id}/connections

-  Parameter description

   .. table:: **Table 1** URI parameter

      +------------+-----------+--------+-----------------------------------------------------------------------------------------------------------------------+
      | Parameter  | Mandatory | Type   | Description                                                                                                           |
      +============+===========+========+=======================================================================================================================+
      | project_id | Yes       | String | Project ID. For details about how to obtain a project ID, see :ref:`Project ID and Account ID <projectid_accountid>`. |
      +------------+-----------+--------+-----------------------------------------------------------------------------------------------------------------------+

Request Parameters
------------------

.. table:: **Table 2** Request header parameter

   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                               |
   +=================+=================+=================+===========================================================================================+
   | workspace       | No              | String          | Workspace ID.                                                                             |
   |                 |                 |                 |                                                                                           |
   |                 |                 |                 | -  If this parameter is not set, data in the **default** workspace is queried by default. |
   |                 |                 |                 | -  To query data in other workspaces, this header must be carried.                        |
   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------+

.. table:: **Table 3** Connection parameters

   +-----------------+-----------------+--------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type               | Description                                                                                                                                                                                                                                        |
   +=================+=================+====================+====================================================================================================================================================================================================================================================+
   | name            | Yes             | String             | Connection name. The name contains a maximum of 100 characters, including only letters, numbers, hyphens (-), and underscores (_). The connection name must be unique.                                                                             |
   +-----------------+-----------------+--------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | type            | Yes             | String             | Connection type.                                                                                                                                                                                                                                   |
   |                 |                 |                    |                                                                                                                                                                                                                                                    |
   |                 |                 |                    | -  DWS                                                                                                                                                                                                                                             |
   |                 |                 |                    | -  DLI                                                                                                                                                                                                                                             |
   |                 |                 |                    | -  SparkSQL                                                                                                                                                                                                                                        |
   |                 |                 |                    | -  HIVE                                                                                                                                                                                                                                            |
   |                 |                 |                    | -  RDS                                                                                                                                                                                                                                             |
   |                 |                 |                    | -  CloudTable                                                                                                                                                                                                                                      |
   |                 |                 |                    | -  HOST                                                                                                                                                                                                                                            |
   +-----------------+-----------------+--------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | config          | No              | Map<String,String> | Connection configuration item. The configuration item varies with the connection type. You do not need to set the **config** parameter for DLI connections. For other types of connections, see the description of connection configuration items. |
   +-----------------+-----------------+--------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | description     | No              | String             | Description of the connection. The description contains a maximum of 255 characters.                                                                                                                                                               |
   +-----------------+-----------------+--------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. table:: **Table 4** DWS connection parameters

   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                                                            |
   +=================+=================+=================+========================================================================================================================================================+
   | clusterName     | No              | String          | Name of a DWS cluster.                                                                                                                                 |
   |                 |                 |                 |                                                                                                                                                        |
   |                 |                 |                 | Perform the following operations to obtain the DWS cluster name:                                                                                       |
   |                 |                 |                 |                                                                                                                                                        |
   |                 |                 |                 | #. Log in to the management console.                                                                                                                   |
   |                 |                 |                 | #. Click **Data Warehouse Service** and select **Cluster Management** from the list on the left.                                                       |
   |                 |                 |                 |                                                                                                                                                        |
   |                 |                 |                 | You can obtain the cluster name from the cluster management list.                                                                                      |
   |                 |                 |                 |                                                                                                                                                        |
   |                 |                 |                 | By default, this parameter is left blank.                                                                                                              |
   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------------+
   | ip              | No              | String          | IP address for accessing the DWS cluster.                                                                                                              |
   |                 |                 |                 |                                                                                                                                                        |
   |                 |                 |                 | Perform the following operations to obtain the DWS access address:                                                                                     |
   |                 |                 |                 |                                                                                                                                                        |
   |                 |                 |                 | #. Log in to the management console.                                                                                                                   |
   |                 |                 |                 | #. Click **Data Warehouse Service** and select **Cluster Management** from the list on the left.                                                       |
   |                 |                 |                 | #. Click the cluster name. The basic information page of the cluster is displayed.                                                                     |
   |                 |                 |                 |                                                                                                                                                        |
   |                 |                 |                 | You can obtain the private network IP address on the **Database Attribute** tab page. If there are multiple IP addresses, select the first IP address. |
   |                 |                 |                 |                                                                                                                                                        |
   |                 |                 |                 | By default, this parameter is left blank.                                                                                                              |
   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------------+
   | port            | No              | String          | Port for accessing the DWS cluster.                                                                                                                    |
   |                 |                 |                 |                                                                                                                                                        |
   |                 |                 |                 | Perform the following operations to obtain the DWS access port:                                                                                        |
   |                 |                 |                 |                                                                                                                                                        |
   |                 |                 |                 | #. Log in to the management console.                                                                                                                   |
   |                 |                 |                 | #. Click **Data Warehouse Service** and select **Cluster Management** from the list on the left.                                                       |
   |                 |                 |                 | #. Click the cluster name. The basic information page of the cluster is displayed.                                                                     |
   |                 |                 |                 |                                                                                                                                                        |
   |                 |                 |                 | You can obtain the port information on the **Database Attribute** tab page.                                                                            |
   |                 |                 |                 |                                                                                                                                                        |
   |                 |                 |                 | For example, set **port** to **8000**. By default, this parameter is left blank.                                                                       |
   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------------+
   | userName        | Yes             | String          | Username of the database. This username is the username entered during the creation of the DWS cluster.                                                |
   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------------+
   | password        | Yes             | String          | Password for accessing the database. This password is the password entered during the creation of the DWS cluster.                                     |
   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------------+
   | sslEnable       | Yes             | boolean         | Specifies whether to enable the SSL connection.                                                                                                        |
   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------------+
   | kmsKey          | Yes             | String          | Name of a KMS key.                                                                                                                                     |
   |                 |                 |                 |                                                                                                                                                        |
   |                 |                 |                 | Perform the following operations to obtain the key:                                                                                                    |
   |                 |                 |                 |                                                                                                                                                        |
   |                 |                 |                 | #. Log in to the management console.                                                                                                                   |
   |                 |                 |                 | #. Click **Key Management Service** and select **Key Management Service** from the list on the left.                                                   |
   |                 |                 |                 |                                                                                                                                                        |
   |                 |                 |                 | You can obtain the key name from the key list.                                                                                                         |
   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------------+
   | agentName       | Yes             | String          | Name of a CDM cluster.                                                                                                                                 |
   |                 |                 |                 |                                                                                                                                                        |
   |                 |                 |                 | You can obtain the cluster name from the CDM cluster list on the **DataArts Migration** page of the DataArts Studio console.                           |
   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------------+

.. table:: **Table 5** Spark SQL connection parameters

   +------------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------+
   | Parameter        | Mandatory       | Type            | Description                                                                                                                  |
   +==================+=================+=================+==============================================================================================================================+
   | clusterName      | Yes             | String          | Name of an MRS cluster.                                                                                                      |
   |                  |                 |                 |                                                                                                                              |
   |                  |                 |                 | Perform the following operations to obtain the MRS cluster name:                                                             |
   |                  |                 |                 |                                                                                                                              |
   |                  |                 |                 | #. Log in to the management console.                                                                                         |
   |                  |                 |                 | #. Click **MapReduce Service** and select **Active Clusters** from the list on the left.                                     |
   |                  |                 |                 |                                                                                                                              |
   |                  |                 |                 | You can obtain the cluster name from the active clusters, such as **mrsCluster1**.                                           |
   +------------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------+
   | connectionMethod | Yes             | String          | Method to connect.                                                                                                           |
   |                  |                 |                 |                                                                                                                              |
   |                  |                 |                 | -  **agent**: connected through an agent.                                                                                    |
   |                  |                 |                 | -  **direct**: connected directly.                                                                                           |
   +------------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------+
   | userName         | No              | String          | Username of the MRS cluster. This parameter is mandatory when **connectionMethod** is set to **agent**.                      |
   +------------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------+
   | password         | No              | String          | Password for accessing the MRS cluster. This parameter is mandatory when **connectionMethod** is set to **agent**.           |
   +------------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------+
   | agentName        | No              | String          | Name of a CDM cluster. This parameter is mandatory when **connectionMethod** is set to **agent**.                            |
   |                  |                 |                 |                                                                                                                              |
   |                  |                 |                 | You can obtain the cluster name from the CDM cluster list on the **DataArts Migration** page of the DataArts Studio console. |
   +------------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------+
   | kmsKey           | No              | String          | Name of a KMS key. This parameter is mandatory when **connectionMethod** is set to **agent**.                                |
   |                  |                 |                 |                                                                                                                              |
   |                  |                 |                 | Perform the following operations to obtain the key:                                                                          |
   |                  |                 |                 |                                                                                                                              |
   |                  |                 |                 | #. Log in to the management console.                                                                                         |
   |                  |                 |                 | #. Click **Key Management Service** and select **Key Management Service** from the list on the left.                         |
   |                  |                 |                 |                                                                                                                              |
   |                  |                 |                 | You can obtain the key name from the key list.                                                                               |
   +------------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------+

.. table:: **Table 6** Hive connection parameters

   +------------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------+
   | Parameter        | Mandatory       | Type            | Description                                                                                                                  |
   +==================+=================+=================+==============================================================================================================================+
   | clusterName      | Yes             | String          | Name of an MRS cluster, for example, **mrsCluster1**.                                                                        |
   +------------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------+
   | connectionMethod | Yes             | String          | Method to connect.                                                                                                           |
   |                  |                 |                 |                                                                                                                              |
   |                  |                 |                 | -  **agent**: connected through an agent.                                                                                    |
   |                  |                 |                 | -  **direct**: connected directly.                                                                                           |
   +------------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------+
   | userName         | No              | String          | Username of the MRS cluster. This parameter is mandatory when **connectionMethod** is set to **agent**.                      |
   +------------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------+
   | password         | No              | String          | Password for accessing the MRS cluster. This parameter is mandatory when **connectionMethod** is set to **agent**.           |
   +------------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------+
   | agentName        | No              | String          | Name of a CDM cluster. This parameter is mandatory when **connectionMethod** is set to **agent**.                            |
   |                  |                 |                 |                                                                                                                              |
   |                  |                 |                 | You can obtain the cluster name from the CDM cluster list on the **DataArts Migration** page of the DataArts Studio console. |
   +------------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------+
   | kmsKey           | No              | String          | Name of a KMS key. This parameter is mandatory when **connectionMethod** is set to **agent**.                                |
   |                  |                 |                 |                                                                                                                              |
   |                  |                 |                 | Perform the following operations to obtain the key:                                                                          |
   |                  |                 |                 |                                                                                                                              |
   |                  |                 |                 | #. Log in to the management console.                                                                                         |
   |                  |                 |                 | #. Click **Key Management Service** and select **Key Management Service** from the list on the left.                         |
   |                  |                 |                 |                                                                                                                              |
   |                  |                 |                 | You can obtain the key name from the key list.                                                                               |
   +------------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------+

.. table:: **Table 7** RDS connection parameters

   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                                  |
   +=================+=================+=================+==============================================================================================================================+
   | ip              | Yes             | String          | Address for accessing RDS.                                                                                                   |
   |                 |                 |                 |                                                                                                                              |
   |                 |                 |                 | Perform the following operations to obtain the RDS access address:                                                           |
   |                 |                 |                 |                                                                                                                              |
   |                 |                 |                 | #. Log in to the management console.                                                                                         |
   |                 |                 |                 | #. Click **Relational Database Service** and select **Instance Management** from the list on the left.                       |
   |                 |                 |                 | #. Click the name of an instance. The basic information page of the instance is displayed.                                   |
   |                 |                 |                 |                                                                                                                              |
   |                 |                 |                 | You can obtain the IP address on the **Connection Information** tab.                                                         |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------+
   | port            | Yes             | String          | Port for accessing RDS.                                                                                                      |
   |                 |                 |                 |                                                                                                                              |
   |                 |                 |                 | Perform the following operations to obtain the RDS access port:                                                              |
   |                 |                 |                 |                                                                                                                              |
   |                 |                 |                 | #. Log in to the management console.                                                                                         |
   |                 |                 |                 | #. Click **Relational Database Service** and select **Instance Management** from the list on the left.                       |
   |                 |                 |                 | #. Click the name of an instance. The basic information page of the instance is displayed.                                   |
   |                 |                 |                 |                                                                                                                              |
   |                 |                 |                 | You can obtain the database port on the **Connection Information** tab page.                                                 |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------+
   | userName        | Yes             | String          | Username of the database. This username is the username entered during the creation of the cluster.                          |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------+
   | password        | Yes             | String          | Password for accessing the database. This password is the password entered during the creation of the cluster.               |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------+
   | kmsKey          | Yes             | String          | Name of a KMS key.                                                                                                           |
   |                 |                 |                 |                                                                                                                              |
   |                 |                 |                 | Perform the following operations to obtain the key:                                                                          |
   |                 |                 |                 |                                                                                                                              |
   |                 |                 |                 | #. Log in to the management console.                                                                                         |
   |                 |                 |                 | #. Click **Key Management Service** and select **Key Management Service** from the list on the left.                         |
   |                 |                 |                 |                                                                                                                              |
   |                 |                 |                 | You can obtain the key name from the key list.                                                                               |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------+
   | agentName       | Yes             | String          | Name of a CDM cluster.                                                                                                       |
   |                 |                 |                 |                                                                                                                              |
   |                 |                 |                 | You can obtain the cluster name from the CDM cluster list on the **DataArts Migration** page of the DataArts Studio console. |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------+
   | driverName      | Yes             | String          | Name of the driver.                                                                                                          |
   |                 |                 |                 |                                                                                                                              |
   |                 |                 |                 | -  com.mysql.jdbc.Driver                                                                                                     |
   |                 |                 |                 | -  org.postgresql.Driver                                                                                                     |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------+
   | driverPath      | Yes             | String          | Path of the driver on OBS.                                                                                                   |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------+

.. table:: **Table 8** CloudTable connection parameters

   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                            |
   +=================+=================+=================+========================================================================================+
   | clusterName     | Yes             | String          | Name of a CloudTable cluster.                                                          |
   |                 |                 |                 |                                                                                        |
   |                 |                 |                 | Perform the following operations to obtain the cluster name:                           |
   |                 |                 |                 |                                                                                        |
   |                 |                 |                 | #. Log in to the management console.                                                   |
   |                 |                 |                 | #. Click **CloudTable Service** and select **Cluster Mode** from the list on the left. |
   |                 |                 |                 |                                                                                        |
   |                 |                 |                 | You can obtain the cluster name from the cluster list.                                 |
   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------+

.. table:: **Table 9** HOST connection parameters

   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                                  |
   +=================+=================+=================+==============================================================================================================================+
   | ip              | Yes             | String          | IP address of the host                                                                                                       |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------+
   | port            | Yes             | String          | SSH port number of the host                                                                                                  |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------+
   | userName        | Yes             | String          | Username for logging in to the host                                                                                          |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------+
   | password        | Yes             | String          | Password for logging in to the host                                                                                          |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------+
   | agentName       | Yes             | String          | Name of a CDM cluster.                                                                                                       |
   |                 |                 |                 |                                                                                                                              |
   |                 |                 |                 | You can obtain the cluster name from the CDM cluster list on the **DataArts Migration** page of the DataArts Studio console. |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------+
   | kmsKey          | Yes             | String          | Name of a KMS key.                                                                                                           |
   |                 |                 |                 |                                                                                                                              |
   |                 |                 |                 | Perform the following operations to obtain the key:                                                                          |
   |                 |                 |                 |                                                                                                                              |
   |                 |                 |                 | #. Log in to the management console.                                                                                         |
   |                 |                 |                 | #. Click **Key Management Service** and select **Key Management Service** from the list on the left.                         |
   |                 |                 |                 |                                                                                                                              |
   |                 |                 |                 | You can obtain the key name from the key list.                                                                               |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------+

Response Parameters
-------------------

None.

Example Request
---------------

Create a connection.

.. code-block:: text

   POST /v1/b384b9e9ab9b4ee8994c8633aabc9505/connections
   {
       "name":"connection1",
       "type":"DWS",
       "config":{
           "clusterName":"test",
           "userName":"dbadmin",
               "password":"*********",
           "kmsKey":"cdm-dlf",
           "agentName":"cdm-donotdelete",
           "sslEnable":false
       }
   }

Example Response
----------------

-  Success response

   HTTP status code 204

-  Failure response

   HTTP status code 400

   .. code-block::

      {
          "error_code":"DLF.6309",
          "error_msg":"The name already exists."
      }

Status Codes
------------

See :ref:`Status Codes <dataartsstudio_02_0310>`.
