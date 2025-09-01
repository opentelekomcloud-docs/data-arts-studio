:original_name: dataartsstudio_01_1821.html

.. _dataartsstudio_01_1821:

Download Center
===============

You can download or dump SQL script execution results. After downloading or dumping the SQL execution results, you can view them on the **Download Center** page.

Constraints
-----------

Records are generated on the **Download Center** page only when SQL scripts or single-task SQL jobs are executed, and results are downloaded or dumped.


Download Center
---------------

.. note::

   -  The download records age out on a regular basis. When aged out, download records and the data dumped to OBS are deleted.
   -  Operators can view only their own download records. Workspace admins can view all download records in the current workspace.

On the **Download Center** page, you can centrally manage the execution results of SQL scripts. You can view and delete the download results, and view, download, and delete the dump results.


.. figure:: /_static/images/en-us_image_0000002269117185.png
   :alt: **Figure 1** Download Center

   **Figure 1** Download Center

-  Set the default OBS path.

   .. note::

      The workspace admin can set the default OBS path for dump for the current workspace.

   #. In the left navigation pane on the DataArts Factory console, choose **Download Center**.
   #. Click **Set Default OBS Path**.
   #. Set the default OBS path.

      .. note::

         After you set the default OBS path, the test running results of scripts or single-task jobs will be dumped to this path by default. However, the paths where previous running results have been dumped will not change.

   #. Click **OK**.

-  View the script execution result.

   #. In the left navigation pane on the DataArts Factory console, choose **Download Center**.

   #. View the file name, operator, operation time, operation type, task status, and OBS path of local download tasks and asynchronous dump tasks.

      You can view the dump task download failure records.

   #. Click |image1| in the **Operation** column to download data from the OBS path.

   #. Click |image2| in the **Operation** column to delete download and dump records.

      When you click **Delete**, a message is displayed indicating that the record cannot be downloaded after being deleted. Click **OK**.

-  Filter records by search criteria.

   You can filter records by operation time, job name, OBS path, operator, operation type, and task status. You can enter a keyword for fuzzy search.

.. |image1| image:: /_static/images/en-us_image_0000002269117181.png
.. |image2| image:: /_static/images/en-us_image_0000002269197257.png
