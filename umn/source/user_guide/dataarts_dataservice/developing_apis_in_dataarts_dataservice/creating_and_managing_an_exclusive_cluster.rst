:original_name: dataartsstudio_01_0314.html

.. _dataartsstudio_01_0314:

Creating and Managing an Exclusive Cluster
==========================================

This topic describes how to create an exclusive DataArts DataService instance. You can create an API in Exclusive DataArts DataService and use it to provide services only after the instance is available.

.. important::

   To create or delete an exclusive cluster or change API quotas, you must have either of the following accounts:

   -  DARTS Administrator with the VPCEndpoint Administrator permission
   -  Tenant Administrator with the VPCEndpoint Administrator permission

Network Environment Preparation
-------------------------------

After a DataArts DataService exclusive cluster is created, resources are located in the resource tenant zone. ELB performs load balancing for the nodes in the cluster.

After creating an exclusive cluster, you can access APIs in the cluster in the following ways:

-  Private address: IP address of the VPC endpoint. This method is available by default.
-  Public address (optional): EIP bound to ELB The EIP is available only when you enable the Internet access when creating the DataArts DataService cluster.
-  Private domain name (optional): A private domain name takes effect in a VPC. After creating a cluster, you can bind a private domain name to the cluster. DataArts DataService invokes the DNS service to associate the private domain name with the private IP address.
-  Public domain name (optional): A public domain name is resolved on the Internet. After creating a cluster, you can bind a public domain name to the cluster by entering a registered domain name. DataArts DataService invokes the DNS service to associate the public domain name with the external IP address.


.. figure:: /_static/images/en-us_image_0000002234085892.png
   :alt: **Figure 1** Networking of the DataArts DataService exclusive cluster

   **Figure 1** Networking of the DataArts DataService exclusive cluster

To ensure that the APIs in the exclusive cluster are accessible, pay attention to the following network configurations during cluster creation:

-  Virtual Private Cloud (VPC)

   A VPC must be configured for an exclusive DataArts DataService instance. Resources (such as ECSs) in the same VPC can use the private address of the exclusive instance to call APIs.

   When you create an exclusive instance, you are advised to configure the same VPC as other associated services to ensure network security and facilitate network configuration.

-  Elastic IP (EIP)

   If you want to call an API of an exclusive instance, buy an EIP and bind it to the instance. The EIP will be used as the Internet entry of the instance.

-  Security Group

   A security group is similar to a firewall. It controls who can access the specified port of an instance and enables the communication data flow of the instance to move to the specified destination address. You are advised to enable the IP address and port in the inbound direction of the security group to protect the network security of the instance to the maximum extent.

   The security group bound to an exclusive instance must meet the following requirements:

   -  Inbound rule: To call APIs from the Internet or from resources in other security groups, enable ports 80 (HTTP) and 443 (HTTPS) in the inbound direction of the security group bound to the exclusive instance.
   -  Outbound direction: If the backend service is deployed on the Internet or in another security group, enable the backend service address and API calling listening port in the outbound direction of the security group bound to the exclusive instance.
   -  If the frontend and backend services of the API are bound to the same security group and VPC as the exclusive instance, you do not need to enable the preceding ports for the exclusive instance.

-  Route

   In the physical machine management scenario, if the physical machine and the cluster have different network segments, you need to configure a route.

   On the **Basic Details** page, click **Add** following **Route** and add the IP address of the physical server.


   .. figure:: /_static/images/en-us_image_0000002269205157.png
      :alt: **Figure 2** Basic Details page

      **Figure 2** Basic Details page

Procedure
---------

After you create a DataArts DataService incremental package, the system automatically creates a cluster based on your selected specifications.

#. Locate an enabled instance and click **Create**.

#. On the displayed page, set parameters based on :ref:`Table 1 <dataartsstudio_01_0314__table10831131913425>`.

   .. _dataartsstudio_01_0314__table10831131913425:

   .. table:: **Table 1** Parameters for creating an exclusive DataArts DataService instance

      +--------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                                              | Description                                                                                                                                                                                                                                                                                                                                                   |
      +========================================================+===============================================================================================================================================================================================================================================================================================================================================================+
      | Package                                                | Select **DataArts DataService**.                                                                                                                                                                                                                                                                                                                              |
      +--------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Workspace                                              | The workspace for which you want to use the incremental package. For example, if you want to use DataArts DataService Exclusive in workspace A of the DataArts Studio instance, select workspace A. After you create an exclusive DataArts DataService cluster, you can view it in workspace A.                                                               |
      |                                                        |                                                                                                                                                                                                                                                                                                                                                               |
      |                                                        | If you want to use the cluster in other workspaces, you can share it with those workspaces by referring to :ref:`Managing Cluster Sharing <dataartsstudio_01_0314__section15513132411716>`.                                                                                                                                                                   |
      +--------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | AZ                                                     | Select the AZ where the DataArts DataService Exclusive cluster is located.                                                                                                                                                                                                                                                                                    |
      |                                                        |                                                                                                                                                                                                                                                                                                                                                               |
      |                                                        | Select **One AZ** or **Multiple AZs**. **Multiple AZs** is recommended.                                                                                                                                                                                                                                                                                       |
      |                                                        |                                                                                                                                                                                                                                                                                                                                                               |
      |                                                        | -  **One AZ**: Nodes of the DataArts DataService Exclusive cluster are deployed in the same AZ.                                                                                                                                                                                                                                                               |
      |                                                        | -  **Multiple AZs**: Nodes of the DataArts DataService Exclusive cluster are deployed in 2 to 10 AZs.                                                                                                                                                                                                                                                         |
      +--------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Name                                                   | The cluster name must start with a letter and can contain only letters, digits, hyphens (-), and underscores (_). It must contain at least five characters.                                                                                                                                                                                                   |
      +--------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Description                                            | A description of the exclusive DataArts DataService cluster.                                                                                                                                                                                                                                                                                                  |
      +--------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Version                                                | Cluster version of the exclusive DataArts DataService cluster.                                                                                                                                                                                                                                                                                                |
      +--------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Cluster Details                                        | The number of APIs supported varies depending on the instance specifications.                                                                                                                                                                                                                                                                                 |
      +--------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Public Address                                         | Enable this function. When the cluster is created, a new EIP is automatically bound to the cluster. You can use this EIP to call the APIs of the exclusive cluster.                                                                                                                                                                                           |
      |                                                        |                                                                                                                                                                                                                                                                                                                                                               |
      |                                                        | If you want to call APIs locally or across networks, you are advised to enable this function. If you do not enable this function during cluster creation, you cannot bind an EIP to the cluster later.                                                                                                                                                        |
      +--------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Bandwidth                                              | Bandwidth range on the Internet.                                                                                                                                                                                                                                                                                                                              |
      +--------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | VPC                                                    | VPC, subnet, and security group to which the DataArts DataService Exclusive cluster in the DataArts Studio instance belongs.                                                                                                                                                                                                                                  |
      |                                                        |                                                                                                                                                                                                                                                                                                                                                               |
      |                                                        | Cloud resources (such as ECSs) within the same VPC, subnet, and security group can call APIs using the private IP address of the DataArts DataService Exclusive instance. Deploy the DataArts DataService Exclusive cluster in the same VPC, subnet, and security group as your other services to facilitate network configuration and secure network access. |
      |                                                        |                                                                                                                                                                                                                                                                                                                                                               |
      |                                                        | For details about the operations on VPCs, subnets, and security groups, see *Virtual Private Cloud User Guide*.                                                                                                                                                                                                                                               |
      |                                                        |                                                                                                                                                                                                                                                                                                                                                               |
      |                                                        | .. note::                                                                                                                                                                                                                                                                                                                                                     |
      |                                                        |                                                                                                                                                                                                                                                                                                                                                               |
      |                                                        |    -  After a DataArts DataService Exclusive cluster is created, the VPC, subnet, and security group of the cluster cannot be changed. Exercise caution when setting them during the cluster creation.                                                                                                                                                        |
      |                                                        |    -  If **Enabling the public IP address** is selected, the security group must allow access from ports 80 (HTTP) and 443 (HTTPS) in the inbound direction.                                                                                                                                                                                                  |
      |                                                        |    -  You can select a VPC subnet shared by the VPC owner when you create a DataArts DataService Exclusive cluster. Through VPC subnet sharing, you can easily configure and manage multiple accounts' resources at low costs. For details about how to share a VPC subnet, see "VPC Sharing" in *Virtual Private Cloud User Guide*.                          |
      +--------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Subnet                                                 |                                                                                                                                                                                                                                                                                                                                                               |
      +--------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Security Group                                         |                                                                                                                                                                                                                                                                                                                                                               |
      +--------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Managing Cluster Resources Using an Enterprise Project | Enterprise project associated with the exclusive DataArts DataService cluster. An enterprise project facilitates management of cloud resources. For details, see *Enterprise Management User Guide*.                                                                                                                                                          |
      +--------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

#. Click **create Now**, confirm the settings, and click **Next**.

.. _dataartsstudio_01_0314__section15513132411716:

Managing Cluster Sharing
------------------------

By default, an exclusive cluster can be used only in its associated workspace by default. If you want to use the cluster in other workspaces, you can share it with them. Then you can view and use the cluster and publish APIs to the cluster in those workspaces. However, you cannot manage the cluster.

#. Log in to the DataArts Studio console by following the instructions in :ref:`Accessing the DataArts Studio Instance Console <dataartsstudio_01_0001>`.

#. On the DataArts Studio console, locate a workspace in which you have obtained an exclusive cluster and click **DataArts DataService**.

#. In the navigation pane on the left, choose **Clusters**.

#. Click the name of a cluster to go to its details page.

#. On the cluster details page, click the **Sharing** tab.


   .. figure:: /_static/images/en-us_image_0000002269205153.png
      :alt: **Figure 3** Sharing page

      **Figure 3** Sharing page

#. Click **Share**. In the displayed dialog box, select the workspaces you want to share the cluster to and click **OK**.


   .. figure:: /_static/images/en-us_image_0000002234245724.png
      :alt: **Figure 4** Selecting workspaces

      **Figure 4** Selecting workspaces

#. You can view and use the cluster in the workspaces.

   If you want to stop sharing the cluster with a workspace, suspend the APIs you have published in the cluster in the workspace, and go to the cluster details page to stop sharing the cluster.

Setting the Allocated API Quota
-------------------------------

After an exclusive cluster is created, you need to set the API quota for the current workspace.

By default, the total quota for a DataArts DataService Exclusive cluster in a DataArts Studio instance is 5,000 by default. You can create APIs in a workspace only after allocating an API quota to the workspace. The procedure of allocating the quota is as follows:

#. Log in to the DataArts Studio console by following the instructions in :ref:`Accessing the DataArts Studio Instance Console <dataartsstudio_01_0001>`.

#. On the **Workspaces** page, locate the target workspace and click **Edit** in the **Operation** column.


   .. figure:: /_static/images/en-us_image_0000002234235668.png
      :alt: **Figure 5** Workspace Information dialog box

      **Figure 5** Workspace Information dialog box

#. Locate **API Quota of DataArts DataService Exclusive** and click **Edit** in the **Operation** column to set it. Click **OK** to save the change.

   The allocated quota indicates the quota that can be used in the current workspace. It cannot be less than the used quota or greater than the unallocated quota (total quota minus total allocated quota).


   .. figure:: /_static/images/en-us_image_0000002269195137.png
      :alt: **Figure 6** Setting the allocated quota

      **Figure 6** Setting the allocated quota

#. In the **Workspace Information** dialog box, click **OK**.

Related Operations
------------------

-  Enabling cluster log dump: When this function is enabled, all the API access logs in the current workspace of the cluster will be dumped to a specified OBS bucket or LTS log.

   On the page displaying clusters, click a cluster name to go to the **Basic Details** tab page. Enable the log dump function and select a dump mode:

   -  If you select **OBS**, all the API access logs in the current workspace will be dumped to the specified OBS bucket.
   -  If you want to select **LTS**, you need to create a log group and a log stream on the LTS console in advance. For details about how to create a log group and a log stream, see :ref:`Viewing API Access Logs <dataartsstudio_01_0900>`. When you select **LTS**, all the API access logs in the current workspace will be dumped to the created log stream.

-  Restarting a cluster: If a cluster is restarted, the APIs published in the cluster cannot be called. Exercise caution when performing this operation.

   On the **Clusters** page, locate a cluster and click **Restart** to restart it.

-  Deleting a cluster: If the current cluster does not meet your requirements, you can delete it. Note that a deleted cluster cannot be restored. Ensure that related service data has been exported for backup and exercise caution when performing this operation.

   On the **Clusters** page, locate a cluster, click **More** in the **Operation** column, and select **Delete**.

-  Binding a private domain name: A private domain name takes effect in a VPC. When a private domain name is bound, it is associated with a private IP address. Then you can call APIs using the private domain name in the same VPC in the private network.

   On the **Clusters** page, locate a cluster, click **More** in the **Operation** column, select **Bind Private Zone**, and enter a custom private domain name. DataArts DataService invokes the DNS service to associate the private domain name with the private IP address. Each tenant can add up to 50 private domain names in all projects.

   The private domain name supports various domain name levels and must comply with domain name naming rules.

   -  Domain name labels are separated by dot (.), and each label does not exceed 63 characters.
   -  A domain name label can contain letters, digits, and hyphens (-) and cannot start or end with a hyphen.
   -  The total length of the domain name cannot exceed 254 characters.

-  Binding a public domain name: A public domain name is resolved on the Internet. When a public domain name is bound, it is associated with a public IP address. Then you can call APIs using the public domain name on the Internet. On the **Clusters** page, locate a cluster, click **More** in the **Operation** column, select **Bind Public Zone**, and enter a registered domain name. DataArts DataService invokes the DNS service to associate the public domain name with the public IP address. To bind a public domain name, ensure that **Public Address** has been enabled during cluster creation and an EIP has been bound to the cluster. Otherwise, the public domain name cannot be bound to the cluster. In addition, each tenant can have up to 50 public domain names.

   The public domain name can include a primary domain name and its subdomain name, for example, abc.example.com.
