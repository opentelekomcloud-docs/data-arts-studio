:original_name: dataartsstudio_01_0913.html

.. _dataartsstudio_01_0913:

Unlocking a Job
===============

Script and job unlocking depends on the lock function of DataArts Factory.

The lock function prevents conflict caused by collaborative script or job development. If you create or import a script or job, it is locked by you by default. You can only edit, save, or submit a script or job you have locked. To edit, save, or submit a script or job that is locked by another user or not locked by any user, you must lock the script or job first.

.. important::

   -  You can view the lock status of a script or job in the script or job directory tree.
   -  To view the latest version of an opened script or job locked by another user, you need to re-open the script or job because it is not updated in real time.
   -  Scripts or jobs that were created before the lock function was available are now unlocked by default. To edit, save, or submit these scripts or jobs, you need to lock them first.
   -  The locking operation depends on the soft and hard lock policies. For details about how to configure soft and hard lock policies, see :ref:`Configuring a Default Item <dataartsstudio_01_04501>`.

      -  **Soft lock**: You can lock or unlock jobs or scripts, regardless of whether they are locked by others.
      -  **Hard Lock**: You can lock jobs or scripts only after they have been unlocked by other users. The space administrator and the DARTS Administrator can lock and unlock jobs or scripts without any limitations.

   -  Do not lock a script or job that is locked by another user because if you do so, changes to the script or job made by the user will be lost. If you want to modify the script or job, contact the user to unlock the script or job, and lock it by yourself.


.. figure:: /_static/images/en-us_image_0000002270847370.png
   :alt: **Figure 1** Lock statuses

   **Figure 1** Lock statuses

Prerequisites
-------------

A job has been developed.

Procedure
---------

If you submit a version, the latest job in the development state will be saved and submitted and overwrite the previous job version. You are advised to unlock the job after submitting the version so that other developers can modify the job as needed.

#. Log in to the DataArts Studio console by following the instructions in :ref:`Accessing the DataArts Studio Instance Console <dataartsstudio_01_0001>`.

#. On the DataArts Studio console, locate a workspace and click **DataArts Factory**.

#. In the left navigation pane of DataArts Factory, choose **Development** > **Develop Job**.

#. In the job directory, double-click the developed job to access the job development page.

#. Above the job canvas or editor, click **Unlock** to unlock the job.


   .. figure:: /_static/images/en-us_image_0000002305440313.png
      :alt: **Figure 2** Unlocking a job

      **Figure 2** Unlocking a job
