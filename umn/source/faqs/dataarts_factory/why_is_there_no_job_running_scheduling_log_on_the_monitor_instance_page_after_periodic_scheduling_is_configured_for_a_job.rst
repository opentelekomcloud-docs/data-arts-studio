:original_name: dataartsstudio_03_0058.html

.. _dataartsstudio_03_0058:

Why Is There No Job Running Scheduling Log on the Monitor Instance Page After Periodic Scheduling Is Configured for a Job?
==========================================================================================================================

#. On the Data Development page, choose **Monitoring** > **Monitor Job** to check whether the target job is being scheduled. A job can be scheduled only within the scheduling period.


   .. figure:: /_static/images/en-us_image_0000001322249144.png
      :alt: **Figure 1** Viewing the job scheduling status

      **Figure 1** Viewing the job scheduling status

#. If a job depends on other jobs, choose **Monitoring** > **Monitor Instance** to view the running status of the dependent jobs. If the job is self-dependent, expand the search time to check whether the job is waiting for running due to the failure of a historical job instance.
