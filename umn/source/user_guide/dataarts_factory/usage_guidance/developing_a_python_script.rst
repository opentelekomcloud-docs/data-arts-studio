:original_name: dataartsstudio_01_0529.html

.. _dataartsstudio_01_0529:

Developing a Python Script
==========================

This section describes how to develop and execute a Python script using DataArts Factory.

Preparing the Environment
-------------------------

-  .. _dataartsstudio_01_0529__li6183612122320:

   An ECS named **ecs-dgc** has been created.

   .. note::

      In this example, the ECS uses the **CentOS 8.0 64bit with ARM (40 GB)** public image and the Python environment. You can log in to the ECS and run the **python** command to check the Python environment.

      |image1|

-  .. _dataartsstudio_01_0529__li948222884818:

   You have enabled the DataArts Migration incremental package and created a CDM cluster named **cdm-dlfpyhthon**. The cluster provides an agent for the DataArts Factory module to communicate with the ECS.

-  Ensure that the ECS can communicate with the CDM cluster, which depends on the following conditions:

   -  If the CDM cluster and the ECS are in the same region, VPC, subnet, and security group, they can communicate with each other by default. If they are in the same VPC but in different subnets or security groups, you must configure routing rules and security group rules. For details about how to configure routing rules, see **Adding Routes** in *Virtual Private Cloud (VPC) Usage Guide*. For details about how to configure security group rules, see **Security Group** > **Adding a Security Group Rule** in *Virtual Private Cloud (VPC) Usage Guide*.
   -  If the CDM cluster and the ECS are in different regions, a public network or a dedicated connection is required for enabling communication between the CDM cluster and the cloud service. If the Internet is used for communication, ensure that an EIP has been bound to the CDM cluster, the host where the data source is located can access the Internet, and the port has been enabled in the firewall rules.
   -  The ECS and the CDM cluster belong to the same enterprise project. If they do not, you can modify the enterprise project of the workspace.

Constraints
-----------

-  Python scripts do not support script parameters or job parameters.

.. _dataartsstudio_01_0529__section3216144795514:

Creating an ECS Data Connection
-------------------------------

Before developing a Python script, you need to create a connection to the ECS.

#. On the DataArts Studio console, locate a workspace and click **Management Center**.


   .. figure:: /_static/images/en-us_image_0000001373087833.png
      :alt: **Figure 1** Management Center

      **Figure 1** Management Center

#. In the navigation pane, choose **Manage Data Connections**.


   .. figure:: /_static/images/en-us_image_0000001373168637.png
      :alt: **Figure 2** Manage Data Connections

      **Figure 2** Manage Data Connections

#. Click **Create Data Connection**.


   .. figure:: /_static/images/en-us_image_0000001373168913.png
      :alt: **Figure 3** Create Data Connection

      **Figure 3** Create Data Connection

#. Configure parameters by referring to :ref:`Table 1 <dataartsstudio_01_0529__table11356052154616>` and create a data connection named **python_test**.

   .. _dataartsstudio_01_0529__table11356052154616:

   .. table:: **Table 1** Host Connection

      +-----------------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                   | Mandatory             | Description                                                                                                                                                                                                     |
      +=============================+=======================+=================================================================================================================================================================================================================+
      | Data Connection Name        | Yes                   | Name of the host connection. The value can contain only letters, digits, hyphens (-), and underscores (_).                                                                                                      |
      +-----------------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Host Address                | Yes                   | IP address of the host                                                                                                                                                                                          |
      |                             |                       |                                                                                                                                                                                                                 |
      |                             |                       | For details, see section "Viewing Details About an ECS" in *Elastic Cloud Server User Guide*.                                                                                                                   |
      +-----------------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Agent                       | Yes                   | Agents provided by the CDM cluster.                                                                                                                                                                             |
      +-----------------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Port                        | Yes                   | SSH port number of the host                                                                                                                                                                                     |
      +-----------------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Username                    | Yes                   | Username of the host                                                                                                                                                                                            |
      +-----------------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Login Mode                  | Yes                   | Mode for logging in to the host                                                                                                                                                                                 |
      |                             |                       |                                                                                                                                                                                                                 |
      |                             |                       | -  Key pair                                                                                                                                                                                                     |
      |                             |                       | -  Password                                                                                                                                                                                                     |
      +-----------------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Key Pair                    | Yes                   | If you select **Key pair** for **Login Mode**, you need to obtain the private key file, upload it to OBS, and select the OBS path. This parameter is available only when **Login Mode** is set to **Key pair**. |
      |                             |                       |                                                                                                                                                                                                                 |
      |                             |                       | .. note::                                                                                                                                                                                                       |
      |                             |                       |                                                                                                                                                                                                                 |
      |                             |                       |    The uploaded private key file must be in PEM format, and the uploaded private key file and the public key configured on the host must be in the same key pair.                                               |
      +-----------------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Key Pair Password           | No                    | If no password is set for the key pair, you do not need to set this parameter.                                                                                                                                  |
      +-----------------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Password                    | Yes                   | Password for logging in to the host.                                                                                                                                                                            |
      +-----------------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Host Connection Description | No                    | Description of the host connection                                                                                                                                                                              |
      +-----------------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

   .. note::

      The key parameters are as follows:

      -  **Host Address**: Enter the IP address of the :ref:`ECS <dataartsstudio_01_0529__li6183612122320>`.
      -  **Agent**: Select the :ref:`CDM cluster <dataartsstudio_01_0529__li948222884818>`.

#. Click **Test** to test connectivity of the data connection. If the test passes, the data connection is created.

#. After the test is successful, click **OK**. The system will create the data connection for you.


Developing a Python Script
--------------------------

#. Choose **DataArts Factory** > **Develop Script** and create a Python script named **python_test**.

#. Edit the Python statement in the editor, select the host connection, and click **Submit** and **Unlock**..

   .. note::

      -  This example defines a string template for saving company information and uses the template to output information about different companies.

         .. code-block::

            template='No.:{:0>9s} \t CompanyName:{:s} \t Website:https://www.{:s}.com'
            context1=template.format('1','CompanyXXX','companyxxx')
            context2=template.format('2','CompanyYYY','companyyyy')
            print(context1)
            print(context2)

      -  The script development area in :ref:`Figure 4 <dataartsstudio_01_0529__fig6853134420369>` is a temporary debugging area. After you close the script tab, the development area will be cleared.

      -  **Connection**: Select the data connection created in :ref:`Creating an ECS Data Connection <dataartsstudio_01_0529__section3216144795514>`.

   .. _dataartsstudio_01_0529__fig6853134420369:

   .. figure:: /_static/images/en-us_image_0000001373168909.png
      :alt: **Figure 4** Editing the Python statement

      **Figure 4** Editing the Python statement

#. Click **Execute** to execute the Python statement.

#. View the script execution result.

.. |image1| image:: /_static/images/en-us_image_0000001548449693.png
