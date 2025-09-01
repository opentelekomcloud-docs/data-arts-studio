:original_name: dataartsstudio_01_0587.html

.. _dataartsstudio_01_0587:

Viewing and Modifying CDM Cluster Configurations
================================================

Scenario
--------

After creating a CDM cluster, you can view its basic information and modify its configurations.

-  You can view the following basic cluster information:

   -  **Cluster Information**: cluster version, creation time, project ID, instance ID, and cluster ID
   -  **Instance Configuration**: cluster flavor, CPU, and memory
   -  **Network**

-  You can modify the following cluster configurations:

   -  **Notification**: If a CDM migration job (only table/file migration) fails or the EIP is abnormal, CDM sends an SMS or email notification to the user.

   -  **User Isolation**: determines whether other users can view and operate the migration jobs and links in the cluster.

      -  If this function is enabled, migration jobs and links in the cluster are isolated. Other IAM users of the a cloud platform account cannot view or operate the migration jobs and links in the cluster.

         .. note::

            Starting jobs by group will run all jobs in the group. If user isolation is enabled, starting jobs by group will still run all jobs in the group even if otherIAM users in the a cloud platform account cannot view the jobs in the group. Therefore, you are not advised to start jobs by group in user isolation scenarios.

      -  If this function is disabled, migration jobs and links in the cluster can be shared with other users. All IAM users with the required permission in the a cloud platform account can view and operate migration jobs and links.

         After disabling **User Isolation**, restart the cluster VM for the settings to take effect.

   -  **Maximum Concurrent Extractors**: This parameter specifies the total number of concurrent extractors of a job. If the total number of concurrent extractors of all jobs exceeds the upper limit, the excess extractors will wait in a queue.

      The value of this parameter ranges from 1 to 1000. You are advised to set it based on the cluster specifications. For details about the recommended value, see :ref:`Maximum Concurrent Extractors <dataartsstudio_01_0083__en-us_topic_0173586861_section19611105617510>`. If the number of concurrent extractors is too large, memory overflow may occur. Exercise caution when changing the value.

      .. note::

         This parameter is also available on the **Settings** tab page. You can change its value either on this page or the **Settings** page.

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

2. Click the name of a cluster and click the **Cluster Configuration** tab to modify **Notification**, **User Isolation** and **Maximum Concurrent Extractors**.

3. Click **Save**. The **Cluster Management** page is displayed.

4. If **User Isolation** is disabled, choose **More** > **Restart** in the **Operation** column to restart the cluster VM for the settings to take effect.


   .. figure:: /_static/images/en-us_image_0000002269200177.png
      :alt: **Figure 1** Restarting a cluster

      **Figure 1** Restarting a cluster

   -  **Restart CDM service process**: Only the CDM service process is restarted. The cluster VM will not be restarted.
   -  **VM restart**: The service process will be interrupted and VMs in the cluster will be restarted.

5. Select **VM restart** and click **Yes**.
