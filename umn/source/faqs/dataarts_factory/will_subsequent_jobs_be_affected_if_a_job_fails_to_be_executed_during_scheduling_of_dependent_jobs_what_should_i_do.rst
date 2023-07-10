:original_name: dataartsstudio_03_0042.html

.. _dataartsstudio_03_0042:

Will Subsequent Jobs Be Affected If a Job Fails to Be Executed During Scheduling of Dependent Jobs? What Should I Do?
=====================================================================================================================

The subsequent jobs may be suspended, continued, or terminated, depending on the configuration.


.. figure:: /_static/images/en-us_image_0000001322249176.png
   :alt: **Figure 1** Job dependencies

   **Figure 1** Job dependencies

In this case, do not stop the job. You can rerun the failed job instance or stop the abnormal instance and then run it again. After the instance failure is removed, the subsequent operations will continue. If you manually process the failure not in DataArts Factory but in other ways, you can force the job instance to succeed after the failure is removed and then subsequent jobs will continue to run properly.
