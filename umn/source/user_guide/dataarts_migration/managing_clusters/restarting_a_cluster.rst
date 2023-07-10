:original_name: dataartsstudio_01_0578.html

.. _dataartsstudio_01_0578:

Restarting a Cluster
====================

Scenario
--------

After modifying some configurations (for example, disabling user isolation), you must restart the cluster to make the modification take effect.

Prerequisites
-------------

You have created a CDM cluster.


Restarting a cluster
--------------------

#. Access the CDM console and choose **Cluster Management** in the left navigation pane.


   .. figure:: /_static/images/en-us_image_0000001322088024.png
      :alt: **Figure 1** Cluster list

      **Figure 1** Cluster list

   .. note::

      The **Source** column is displayed only when you access the **DataArts Migration** page from the DataArts Studio console.

2. Locate the row that contains the target cluster, click **More** in the **Operation** column, and select **Restart** from the drop-down list.


   .. figure:: /_static/images/en-us_image_0000001322248136.png
      :alt: **Figure 2** Restarting a cluster

      **Figure 2** Restarting a cluster

3. Select **Restart CDM service process** or **VM restart** and click **OK**.

   -  **Restart CDM service process**: Only the CDM service process is restarted. The cluster VM will not be restarted.
   -  **VM restart**: The service process will be interrupted and VMs in the cluster will be restarted.
