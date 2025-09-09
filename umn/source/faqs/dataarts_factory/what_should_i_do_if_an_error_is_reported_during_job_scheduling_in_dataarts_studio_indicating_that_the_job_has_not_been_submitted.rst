:original_name: dataartsstudio_03_0114.html

.. _dataartsstudio_03_0114:

What Should I Do If an Error Is Reported During Job Scheduling in DataArts Studio, Indicating that the Job Has Not Been Submitted?
==================================================================================================================================

Symptom
-------

An error is reported during job scheduling in DataArts Studio, indicating that the job has not been submitted.

Cause Analysis
--------------

Job scheduling process begins before the version is submitted. As a result, an error is reported during scheduling. Ensure that the job has a submitted version before it is scheduled.

Solutions
---------

#. Step 1: Submit a job version (not a script).

#. Step 2: Schedule the job.


   .. figure:: /_static/images/en-us_image_0000002234236592.png
      :alt: **Figure 1** Submitting a version

      **Figure 1** Submitting a version
