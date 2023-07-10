:original_name: dataartsstudio_01_0021.html

.. _dataartsstudio_01_0021:

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

      -  If this function is enabled, migration jobs and links in the cluster are isolated. Other IAM users of the cloud platform account cannot operate the jobs and links.

      -  If this function is disabled, migration jobs and links in the cluster can be shared by users. All IAM users with the required permission in the cloud platform account can view and perform operations on the jobs and links in the cluster.

         After disabling **User Isolation**, restart the cluster VM for the settings to take effect.

Prerequisites
-------------

You have created a CDM cluster.

Viewing Basic Cluster Information
---------------------------------

#. Access the CDM console and choose **Cluster Management** in the left navigation pane.


   .. figure:: /_static/images/en-us_image_0000001322088024.png
      :alt: **Figure 1** Cluster list

      **Figure 1** Cluster list

   .. note::

      The **Source** column is displayed only when you access the **DataArts Migration** page from the DataArts Studio console.

#. Click the cluster name to view its basic information.


   .. figure:: /_static/images/en-us_image_0000001321929596.png
      :alt: **Figure 2** Basic cluster information

      **Figure 2** Basic cluster information

Modifying Cluster Configurations
--------------------------------

#. Access the CDM console and choose **Cluster Management** in the left navigation pane.


   .. figure:: /_static/images/en-us_image_0000001322088024.png
      :alt: **Figure 3** Cluster list

      **Figure 3** Cluster list

   .. note::

      The **Source** column is displayed only when you access the **DataArts Migration** page from the DataArts Studio console.

2. Click the name of a cluster and click the **Cluster Configuration** tab to modify **Notification** and **User Isolation** configuration.


   .. figure:: /_static/images/en-us_image_0000001373409313.png
      :alt: **Figure 4** Modifying cluster configurations

      **Figure 4** Modifying cluster configurations

3. Click **Save**. The **Cluster Management** page is displayed.

4. If **User Isolation** is disabled, choose **More** > **Restart** in the **Operation** column to restart the cluster VM for the settings to take effect.


   .. figure:: /_static/images/en-us_image_0000001373087905.png
      :alt: **Figure 5** Restarting a cluster

      **Figure 5** Restarting a cluster

   -  **Restart CDM service process**: Only the CDM service process is restarted. The cluster VM will not be restarted.
   -  **VM restart**: The service process will be interrupted and VMs in the cluster will be restarted.

5. Select **VM restart** and click **Yes**.
