:original_name: dataartsstudio_01_1097.html

.. _dataartsstudio_01_1097:

Viewing a Job Dependency Graph
==============================

You can view a job dependency graph to learn the upstream and downstream jobs associated with the job.

Prerequisites
-------------

Dependent jobs have been configured in the job scheduling configuration in :ref:`Developing a Pipeline Job <dataartsstudio_01_0435>`. Otherwise, only the current job node can be displayed in the view, and the associated upstream and downstream job nodes cannot be displayed.

Procedure
---------

#. Log in to the DataArts Studio console by following the instructions in :ref:`Accessing the DataArts Studio Instance Console <dataartsstudio_01_0001>`.

#. On the DataArts Studio console, locate a workspace and click **DataArts Factory**.

#. In the left navigation pane of DataArts Factory, choose **Development** > **Develop Job**.

#. In the job directory, right-click the job you want to view and choose **View Job Dependency Graph** from the shortcut menu.


   .. figure:: /_static/images/en-us_image_0000002270846362.png
      :alt: **Figure 1** Job Dependency page

      **Figure 1** Job Dependency page

#. On the displayed **Job Dependency** page, perform any of the following operations:

   -  In the upper right corner, select **Display complete dependency graphs**, **Display the current job and its upstream and downstream jobs**, or **Display the current job and its directly connected jobs**.

   -  In the search box in the upper right corner, you can enter the name of a node to search for the node. The node found will be highlighted.

   -  Click **Download** to download the job dependency file.

   -  Scroll your mouse wheel to zoom in or zoom out the dependency graph.

   -  Drag the blank area to view the complete relationship graph.

   -  When the cursor is hovered on a job node, the node is marked green, its upstream job is marked blue, and its downstream job is marked yellow.


      .. figure:: /_static/images/en-us_image_0000002270789500.png
         :alt: **Figure 2** Marking upstream and downstream job nodes of a node

         **Figure 2** Marking upstream and downstream job nodes of a node

   -  Right-click a job node to view the job, copy the job name, and collapse upstream or downstream jobs.


      .. figure:: /_static/images/en-us_image_0000002305406229.png
         :alt: **Figure 3** Job node operations

         **Figure 3** Job node operations


Viewing a Job Dependency Graph
------------------------------

#. In the left navigation pane of DataArts Factory, choose **Development** > **Develop Job**.

#. Right-click the job directory and select **View Job Dependency Graph**.


   .. figure:: /_static/images/en-us_image_0000002305406225.png
      :alt: **Figure 4** Viewing the job dependency graph

      **Figure 4** Viewing the job dependency graph

#. The system displays the dependencies between all the jobs in the directory. You can search for jobs by name. The matched jobs will be highlighted.

   .. note::

      -  If you click a node in the dependency graph, its upstream jobs are marked blue and its downstream jobs are marked yellow.
      -  You can drag to view the full dependency graph.
      -  Scroll the mouse wheel to zoom in or out the dependency graph.
