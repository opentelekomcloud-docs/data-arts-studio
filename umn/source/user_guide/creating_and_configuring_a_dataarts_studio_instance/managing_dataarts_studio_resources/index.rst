:original_name: dataartsstudio_01_4105.html

.. _dataartsstudio_01_4105:

Managing DataArts Studio Resources
==================================

You can centrally manage DataArts Studio resources.

Offline Resource Management
---------------------------

You can view all CDM clusters in a DataArts Studio instance and associate workspaces with CDM clusters.

.. note::

   A CDM cluster is available in a workspace only after they are associated with each other.

#. Log in to the DataArts Studio console as user **DARTS** **Administrator** or **Tenant Administrator**. For details, see :ref:`Accessing the DataArts Studio Instance Console <dataartsstudio_01_0001>`.

#. Locate an instance and click **Access**. Then click the **Resources** tab.

#. On the **Offline Resources** tab page, view all CDM clusters in the instance, such as their statuses, private IP addresses, and public IP addresses.

#. Click |image1| in the **Name** column to expand the cluster details, such as the AZ, VPC, subnet, security group, specifications, cluster ID, and associated workspaces.


   .. figure:: /_static/images/en-us_image_0000002234079328.png
      :alt: **Figure 1** Viewing cluster details

      **Figure 1** Viewing cluster details

#. Locate a CDM cluster and click **Associate with Workspace** in the **Operation** column. In the displayed dialog box, select or deselect workspaces and click **OK** to associate the CDM cluster with the selected workspaces.

   The CDM cluster is only available in the associated workspaces.


   .. figure:: /_static/images/en-us_image_0000002269118533.png
      :alt: **Figure 2** Associating a CDM cluster with workspaces

      **Figure 2** Associating a CDM cluster with workspaces

-  :ref:`Associating a Real-Time Migration Resource Group with Workspaces <dataartsstudio_01_7587>`

.. |image1| image:: /_static/images/en-us_image_0000002269118525.png

.. toctree::
   :maxdepth: 1
   :hidden: 

   associating_a_real-time_migration_resource_group_with_workspaces
