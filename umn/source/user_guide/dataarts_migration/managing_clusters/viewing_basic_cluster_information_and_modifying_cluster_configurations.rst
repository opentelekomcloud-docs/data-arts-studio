:original_name: dataartsstudio_01_0021_0.html

.. _dataartsstudio_01_0021_0:

Viewing Basic Cluster Information and Modifying Cluster Configurations
======================================================================

Scenario
--------

After creating a CDM cluster, you can view its basic information and modify its configurations.

-  You can view the following basic cluster information:

   -  Cluster information: cluster version, creation time, project ID, instance ID, and cluster ID
   -  Instance configuration: cluster flavor, CPU, and memory
   -  Network configuration

-  You can modify the following cluster configurations:

   -  Notification: If a CDM migration job (only table/file migration) fails or the EIP is abnormal, CDM sends an SMS or email notification to the user.
   -  User isolation: determines whether other users can operate the migration jobs or links in the cluster.

      -  If this function is enabled, migration jobs and links in the cluster are isolated. Other IAM users of the a cloud platform account cannot operate the jobs and links.

      -  If this function is disabled, migration jobs and links in the cluster can be shared by users. All IAM users with the required permission in the a cloud platform account can view and perform operations on the jobs and links in the cluster.

         After disabling **User Isolation**, restart the cluster VM for the settings to take effect.

Prerequisites
-------------

You have created a CDM cluster.

Viewing Basic Cluster Information
---------------------------------

#. Log in to the DataArts Studio console by following the instructions in :ref:`Accessing the DataArts Studio Instance Console <dataartsstudio_01_0001>`. On the DataArts Studio console, locate a workspace and click **DataArts Migration** to access the CDM console.
#. Click the cluster name to view its basic information.

Modifying Cluster Configurations
--------------------------------

#. Log in to the DataArts Studio console by following the instructions in :ref:`Accessing the DataArts Studio Instance Console <dataartsstudio_01_0001>`. On the DataArts Studio console, locate a workspace and click **DataArts Migration** to access the CDM console.

2. Click the name of a cluster and click the **Cluster Configuration** tab to modify **Notification** and **User Isolation** configuration.

3. Click **Save**. The **Cluster Management** page is displayed.

4. If **User Isolation** is disabled, choose **More** > **Restart** in the **Operation** column to restart the cluster VM for the settings to take effect.


   .. figure:: /_static/images/en-us_image_0000002305441289.png
      :alt: **Figure 1** Restarting a cluster

      **Figure 1** Restarting a cluster

   -  **Restart CDM service process**: Only the CDM service process is restarted. The cluster VM will not be restarted.
   -  **VM restart**: The service process will be interrupted and VMs in the cluster will be restarted.

5. Select **VM restart** and click **Yes**.
