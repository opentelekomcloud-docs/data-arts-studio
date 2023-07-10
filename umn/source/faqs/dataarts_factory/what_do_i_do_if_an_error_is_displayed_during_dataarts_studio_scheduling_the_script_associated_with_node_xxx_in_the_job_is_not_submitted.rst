:original_name: dataartsstudio_03_0115.html

.. _dataartsstudio_03_0115:

What Do I Do If an Error Is Displayed During DataArts Studio Scheduling: The Script Associated with Node XXX in the Job Is Not Submitted?
=========================================================================================================================================

Symptom
-------

An error is reported when DataArts Studio executes scheduling: The script associated with node XXX in the job is not submitted.

Cause Analysis
--------------

Job scheduling process begins before the script version is submitted. As a result, an error is reported during scheduling. Ensure that the job has a submitted script version before the job is scheduled.

Solutions
---------

#. Step 1: Switch to the script development page and find the corresponding script.
#. Step 2: Submit the script version.
#. Step 3: Schedule the job.
