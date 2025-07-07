:original_name: dataartsstudio_01_1280.html

.. _dataartsstudio_01_1280:

Configuring the Number of Concurrently Running Nodes
====================================================

This section describes how to configure the maximum number of job nodes that can run concurrently in a workspace.

Constraints
-----------

The number of concurrently running nodes in the workspace cannot exceed that in the instance.

Procedure
---------

#. Log in to the DataArts Studio console by following the instructions in :ref:`Accessing the DataArts Studio Instance Console <dataartsstudio_01_0001>`.

#. On the DataArts Studio console, locate a workspace and click **DataArts Factory**.

#. In the navigation pane, choose **Configuration** > **Configure**.

#. Choose **Nodes Concurrently Running**.

#. Set **Nodes Concurrently Running in the Workspace**. Ensure that the value is less than or equal to the maximum number of nodes that can run concurrently in the DataArts Studio instance.

   :ref:`Table 1 <dataartsstudio_01_1280__table13401936141317>` lists the maximum number of nodes that can run concurrently in the DataArts Studio instance. To view the quota of the job node scheduling times per day, click **More** of a DataArts Studio instance and select **Quota Usage**.

   .. _dataartsstudio_01_1280__table13401936141317:

   .. table:: **Table 1** Maximum number of nodes that can run concurrently in a DataArts Studio instance

      +-------------------------------------------------------------+---------------------------------------------------------------------------------+
      | Job Node Scheduling Times/Day of a DataArts Studio Instance | Maximum Number of Nodes That Can Run Concurrently in a DataArts Studio Instance |
      +=============================================================+=================================================================================+
      | <=500                                                       | 10                                                                              |
      +-------------------------------------------------------------+---------------------------------------------------------------------------------+
      | <=5000                                                      | 50                                                                              |
      +-------------------------------------------------------------+---------------------------------------------------------------------------------+
      | <=20000                                                     | 100                                                                             |
      +-------------------------------------------------------------+---------------------------------------------------------------------------------+
      | <=40000                                                     | 200                                                                             |
      +-------------------------------------------------------------+---------------------------------------------------------------------------------+
      | <=80000                                                     | 300                                                                             |
      +-------------------------------------------------------------+---------------------------------------------------------------------------------+
      | > 80000                                                     | 400                                                                             |
      +-------------------------------------------------------------+---------------------------------------------------------------------------------+


   .. figure:: /_static/images/en-us_image_0000002270846318.png
      :alt: **Figure 1** Configuring the number of concurrently running nodes

      **Figure 1** Configuring the number of concurrently running nodes

#. Click **Save**.

Viewing the Number of Historical Nodes Concurrently Running
-----------------------------------------------------------

#. In the navigation pane, choose **Configuration** > **Configure**.
#. Choose **Nodes Concurrently Running**.
#. In the **Historical Nodes Concurrently Running** area, set the time range.
#. Click **OK**.

   .. note::

      The maximum time range is 24 hours.
