:original_name: dataartsstudio_03_0055.html

.. _dataartsstudio_03_0055:

How Do I Locate Job Scheduling Nodes with a Large Number?
=========================================================

If the number of daily executed nodes exceeds the upper limit, it may be caused by frequent job scheduling. Perform the following operations:

#. In the left navigation tree of Data Development, choose **Monitoring** > **Monitor Instance**, select the current day, and view the jobs that are frequently scheduled.

#. In the left navigation tree of Data Development, choose **Monitoring** > **Monitor Job** to check whether the scheduling period of jobs that are frequently scheduled is set properly. If the scheduling period is inappropriate, adjust the scheduling period or stop the scheduling. Generally, the number of minute-level scheduling jobs executed every day exceeds the upper limit.


   .. figure:: /_static/images/en-us_image_0000001373089089.png
      :alt: **Figure 1** Viewing the scheduling period

      **Figure 1** Viewing the scheduling period
