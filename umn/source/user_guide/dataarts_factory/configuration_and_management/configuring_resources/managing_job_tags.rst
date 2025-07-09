:original_name: dataartsstudio_01_0532.html

.. _dataartsstudio_01_0532:

Managing Job Tags
=================

Job tags are used to label jobs of the same or similar purposes to facilitate job management and query. This section describes how to manage job tags, including adding, deleting, importing, and exporting tags.

Adding a Job Tag
----------------

#. Log in to the DataArts Studio console by following the instructions in :ref:`Accessing the DataArts Studio Instance Console <dataartsstudio_01_0001>`.
#. On the DataArts Studio console, locate a workspace and click **DataArts Factory**.
#. In the navigation pane, choose **Configuration** > **Configure**.
#. Choose **Job Tag**.
#. Click **Add**. In the displayed dialog box, enter a tag name and click **OK**.

   .. note::

      You can add a maximum of 100 job tags.

Deleting a Job Tag
------------------

#. In the navigation pane, choose **Configuration** > **Configure**.
#. Choose **Job Tag**.
#. Locate the tag you want to delete and click **Delete** in the **Operation** column. In the displayed dialog box, click **OK**.

   .. note::

      A locked tag cannot be deleted. For details about how to unlock a tag, see :ref:`Locking and Unlocking a Job Tag <dataartsstudio_01_0532__section7773446447>`.

Monitoring Jobs with a Specified Tag
------------------------------------

#. In the navigation pane, choose **Configuration** > **Configure**.
#. Choose **Job Tag**.
#. Locate a tag and click **Monitor** in the **Operation** column. The **Monitor Job** page is displayed, on which all the jobs with the tag are displayed.

.. _dataartsstudio_01_0532__section7773446447:

Locking and Unlocking a Job Tag
-------------------------------

To perform these operations, you must have the **DARTS** **Administrator**, **Tenant Administrator**, or workspace administrator permission.

#. In the navigation pane, choose **Configuration** > **Configure**.
#. Choose **Job Tag**.
#. Locate a tag and click **Lock** or **Unlock** in the **Operation** column.

   .. note::

      -  A locked job tag cannot be deleted.
      -  Importing a locked tag will fail.
      -  A locked tag cannot be added to or removed from a job.
      -  Importing a job with a locked tag will fail.
      -  When a job fails to be imported and a tag needs to be automatically generated, if the tag already exists and is locked, it will not be added to the job.

Importing Job Tags
------------------

To perform this operation, you must have the **DARTS** **Administrator**, **Tenant Administrator**, or workspace administrator permission.

#. In the navigation pane, choose **Configuration** > **Configure**.
#. Choose **Job Tag**.
#. Click **Import Job Tag**.
#. In the displayed dialog box, set the following parameters:

   -  **File Location**: Select **Local** or **OBS**.
   -  **Select File from Local/OBS**: Select a local path or an OBS bucket path.

      .. note::

         -  You are advised to obtain a file to import by exporting tags. The first row of the file is the tag name, and the first column is the job name. If a job has a specified tag, the value in the corresponding cell is 1. Otherwise, the value is 0. If a cell is empty, the system uses value 0 for the cell.
         -  The maximum size of the file to be imported is 10 MB.
         -  If the file to be imported contains two tags with the same name, and the ID of one tag is 0 and that of the other tag is 1, the system uses 1 as the tag ID.
         -  If the file to be imported contains two jobs with the same name, the system identifies the job in the latter row and uses the tag ID in this row.

   -  **Mode**: Select **Append** or **Overwrite**.

      -  **Append**: The new tag will not overwrite the existing one.
      -  **Overwrite**: The new tag will overwrite the existing one.

#. Click **OK**.

Exporting Job Tags
------------------

#. In the navigation pane, choose **Configuration** > **Configure**.

#. Choose **Job Tag**.

#. Export tags.

   -  To export all tags, click **Export All Tags** above the tag list.
   -  To export some tags, select them and click **Export Selected Tags** above the tag list.

   The following figure shows the exported job tags.


   .. figure:: /_static/images/en-us_image_0000002305407285.png
      :alt: **Figure 1** Exporting job tags

      **Figure 1** Exporting job tags

   .. note::

      -  In the exported file, the first row is the tag name, and the first column is the job name. If a job has a specified tag, the value in the corresponding cell is 1. Otherwise, the value is 0.
      -  The first column displays names of all the jobs in the workspace, including real-time job nodes, For Each subjobs, and Subjob subjobs.
