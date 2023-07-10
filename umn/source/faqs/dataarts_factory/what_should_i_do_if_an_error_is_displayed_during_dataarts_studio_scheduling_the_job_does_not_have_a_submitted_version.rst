:original_name: dataartsstudio_03_0114.html

.. _dataartsstudio_03_0114:

What Should I Do If an Error Is Displayed During DataArts Studio Scheduling: The Job Does Not Have a Submitted Version?
=======================================================================================================================

Symptom
-------

An error is reported when DataArts Studio executes scheduling: The job does not have a submitted version. Submit the job version first.

Cause Analysis
--------------

Job scheduling process begins before the version is submitted. As a result, an error is reported during scheduling. Ensure that the job has a submitted version before it is scheduled.

Solutions
---------

#. Step 1: Submit a job version (not a script).
#. Step 2: Schedule the job.


.. figure:: /_static/images/en-us_image_0000001321929564.png
   :alt: **Figure 1** Submitting a version

   **Figure 1** Submitting a version
