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

#. Log in to the DataArts Studio console by following the instructions in :ref:`Accessing the DataArts Studio Instance Console <dataartsstudio_01_0001>`. On the DataArts Studio console, locate a workspace and click **DataArts Migration** to access the CDM console.

2. Locate the row that contains the target cluster, click **More** in the **Operation** column, and select **Restart** from the drop-down list.


   .. figure:: /_static/images/en-us_image_0000002270847106.png
      :alt: **Figure 1** Restarting a cluster

      **Figure 1** Restarting a cluster

3. Select **Restart CDM service process** or **VM restart** and click **OK**.

   -  **Restart CDM service process**: Only the CDM service process is restarted. The cluster VM will not be restarted.
   -  **VM restart**: The service process will be interrupted and VMs in the cluster will be restarted.
