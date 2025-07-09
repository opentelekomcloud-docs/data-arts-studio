:original_name: dataartsstudio_01_0512.html

.. _dataartsstudio_01_0512:

Monitoring PatchData
====================

In the navigation tree of the DataArts Factory console, choose **Monitoring** > **Monitor PatchData**.

On the PatchData Monitoring page, you can view the PatchData job status, date, number of parallel periods, PatchData job name, creator, creation time, and stop a running job. You can filter jobs by PatchData name, creator, date, and status.

On the PatchData Monitoring page, click PatchData name. On the displayed page, you can view the PatchData execution status. For more information, see :ref:`Batch Job Monitoring: PatchData <dataartsstudio_01_0508__en-us_topic_0159100548_section1819004120344>`.

.. note::

   -  PatchData can be sorted by plan time, start time, and end time. Note that only one of the three sorting modes takes effect at a time.
   -  Click the sorting icon once to sort PatchData in ascending order, click the sorting icon twice to sort PatchData in descending order, and click the sorting icon three times to cancel sorting.
   -  When viewing a waiting job instance, click **Remove Dependency** in the **Operation** column to remove dependency on an upstream instance.
   -  If a PatchData task fails, you can click **Operation** and select **Stop** to stop the task.
   -  On the PatchData details page, you can perform a fuzzy search of PatchData jobs by job name.
   -  If job instances need manual confirmation before they are executed, they are in waiting confirmation state on the **Monitor PatchData** page. When you click **Execute**, the job instances are in waiting execution state.
