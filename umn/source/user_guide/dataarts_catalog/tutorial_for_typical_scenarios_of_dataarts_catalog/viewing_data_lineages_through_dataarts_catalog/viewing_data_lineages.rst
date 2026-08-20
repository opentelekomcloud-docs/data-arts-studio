:original_name: dataartsstudio_01_0834.html

.. _dataartsstudio_01_0834:

Viewing Data Lineages
=====================

You need to create a metadata collection task in DataArts Catalog first. When a data development job meets the :ref:`automatic lineage parsing requirements <dataartsstudio_01_0833__en-us_topic_0000001166742863_section12458162215283>` or :ref:`lineages have been manually configured <dataartsstudio_01_0833__en-us_topic_0000001166742863_section123831529241>`, and when the job is successfully scheduled, you can view the data lineages in DataArts Catalog.

Constraints
-----------

-  Data lineage updates depend on job scheduling. Data lineages are generated based on the latest job instances.

   .. note::

      After a data lineage is generated based on the latest instance of a data development job, the lineage will not be updated within the cooldown period (48 hours by default), as long as no new version is submitted for the job. If you want to update the lineage, wait until the cooldown period ends or submit another version of the job and schedule the job.

-  To delete data lineages, you need to delete jobs or job metadata. Stopping jobs alone does not delete data lineages.

Creating and Running a Metadata Collection Task
-----------------------------------------------

Create and run a metadata collection task by referring to :ref:`Configuring a Metadata Collection Task <dataartsstudio_01_0804>`. When creating the task, select the tables whose lineages you want to view.

If a task for collecting the metadata of these tables has been created and run, skip this part.

Starting Job Scheduling
-----------------------

After metadata is collected, the system generates data lineages based on the latest job instances.

#. Log in to the DataArts Studio console by following the instructions in :ref:`Accessing the DataArts Studio Instance Console <dataartsstudio_01_0001>`.

#. On the DataArts Studio console, locate a workspace and click **DataArts Factory**.

#. In the navigation pane, click |image1| and double-click the job for which lineages have been configured to open it.

#. Click **Execute**. The system starts parsing lineages of the job.

   .. note::

      If you click **Test**, the system will not parse lineages of the job.


   .. figure:: /_static/images/en-us_image_0000002269198345.png
      :alt: **Figure 1** Starting job scheduling

      **Figure 1** Starting job scheduling

#. After the job is successfully executed, wait for about 1 minute. The data lineage is generated.


Viewing Data Lineages
---------------------

#. On the DataArts Studio console, locate a workspace and click **DataArts Catalog**.

#. In the navigation pane, choose **Data Catalog**. In the right pane, click the **Technical Assets** tab. On this page, you can query jobs, nodes, and tables.

   In the **Types** area, click **Search All**, select **Job**, **Node**, and **Table**, and click **OK**.

   .. note::

      Jobs do not belong to any data connection. If you select a data connection in the search filters, no result will be returned.


   .. figure:: /_static/images/en-us_image_0000002269198329.png
      :alt: **Figure 2** Selecting types

      **Figure 2** Selecting types

#. In the search result, click the name of an asset ending with **\_job** to view its details. On the job details page, click the **Job** tab and then **Edit** to go to the job editing page.


   .. figure:: /_static/images/en-us_image_0000002269118261.png
      :alt: **Figure 3** Viewing job details

      **Figure 3** Viewing job details

#. In the data asset search result, click the name of an asset ending with **\_node** to view its details. On the node details page, you can view the node lineage information.

   -  Click the **+** or **-** icon beside the node to expand its upstream and downstream links.
   -  Click a node to view the its details.
   -  Click the **Job** tab and then **Edit** to go to the job editing page.


   .. figure:: /_static/images/en-us_image_0000002269198357.png
      :alt: **Figure 4** Viewing lineages of a node

      **Figure 4** Viewing lineages of a node

#. In the data asset search result, click the name of an asset whose icon is a table to view its details. On the table details page, you can view lineages of the table.

   -  Click the **+** or **-** icon beside the table to expand its upstream and downstream links.
   -  Click a table to view its details.


   .. figure:: /_static/images/en-us_image_0000002234238896.png
      :alt: **Figure 5** Viewing lineages of a table

      **Figure 5** Viewing lineages of a table

.. |image1| image:: /_static/images/en-us_image_0000002234079060.png
