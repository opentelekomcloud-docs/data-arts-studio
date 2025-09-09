:original_name: dataartsstudio_03_0415.html

.. _dataartsstudio_03_0415:

What Should I Do If Error Message "The throttling threshold has been reached: policy user over ratelimit,limit:60,time:1 minute." Is Displayed When I Schedule an MRS Spark Job?
================================================================================================================================================================================

Symptom
-------

Error message "The throttling threshold has been reached: policy user over ratelimit,limit:60,time:1 minute" is displayed when I schedule an MRS Spark job.


.. figure:: /_static/images/en-us_image_0000002269116429.png
   :alt: **Figure 1** Error message

   **Figure 1** Error message

Solution
--------

MRS APIs can be called by a single user for a maximum of 60 times per minute. Therefore, the solution is to call the API less frequently.
