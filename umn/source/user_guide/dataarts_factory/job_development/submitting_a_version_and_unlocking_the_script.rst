:original_name: dataartsstudio_01_0902.html

.. _dataartsstudio_01_0902:

Submitting a Version and Unlocking the Script
=============================================

This involves the version management and lock functions.

-  Version management: traces script and job changes, and supports version comparison and rollback. The system retains 10 latest version records. In addition, version management can be used to distinguish the development state and production state.

   -  Development state: Scripts or jobs have not been submitted and are used for debugging. In the development state, you can edit, save, and run scripts or jobs without affecting those being scheduled. In addition, when a job is being associated with a script or job dependency is being configured, the associated script or job will read the configuration in the development state.
   -  Production state: Script or jobs have been submitted and are used for formal scheduling. In formal scheduling, the latest submitted versions of scripts or jobs will be used in scenarios such as script invocation, instance rerunning, and job dependency and patch data configuration.

-  Lock: prevents conflict caused by collaborative script or job development. If you create or import a script or job, it is locked by you by default. You can only edit, save, or submit a script or job you have locked. To edit, save, or submit a script or job that is locked by another user or not locked by any user, you must lock the script or job first.

   .. important::

      -  You can view the lock status of a script or job in the script or job directory tree.
      -  To view the latest version of an opened script or job locked by another user, you need to re-open the script or job because it is not updated in real time.
      -  Scripts or jobs that were created before the lock function was available are now unlocked by default. To edit, save, or submit these scripts or jobs, you need to lock them first.
      -  The locking operation depends on the soft and hard lock policies. For details about how to configure soft and hard lock policies, see :ref:`Configuring a Default Item <dataartsstudio_01_04501>`.

         -  Soft lock: You can lock or unlock jobs or scripts, regardless of whether they are locked by others.
         -  **Hard Lock**: You can lock jobs or scripts only after they have been unlocked by other users. The space administrator and the **DAYU Administrator** user can lock and unlock jobs or scripts without any limitations.

      -  Do not lock a script or job that is locked by another user because if you do so, changes to the script or job made by the user will be lost. If you want to modify the script or job, contact the user to unlock the script or job, and lock it by yourself.


   .. figure:: /_static/images/en-us_image_0000001322247932.png
      :alt: **Figure 1** Lock status

      **Figure 1** Lock status

Prerequisites
-------------

A job has been developed.


Submitting a Version and Unlocking the Script
---------------------------------------------

If you submit a version, the latest job in the development state will be saved and submitted and overwrite the previous job version. You are advised to unlock the job after submitting the version so that other developers can modify the job as needed.

#. Log in to the DataArts Studio console. Locate an instance and click **Access**. On the displayed page, locate a workspace and click **DataArts Factory**.


   .. figure:: /_static/images/en-us_image_0000001321928320.png
      :alt: **Figure 2** DataArts Factory

      **Figure 2** DataArts Factory

#. In the left navigation pane of DataArts Factory, choose **Development** > **Develop Job**.

#. In the job directory, double-click the developed job to access the job development page.

#. Above the job canvas, click **Submit** to submit a version. In the displayed dialog box, enter the change description (a maximum of 128 characters allowed) and select the check box below. If you do not select this option, you cannot click **OK**.


   .. figure:: /_static/images/en-us_image_0000001322247968.png
      :alt: **Figure 3** Submitting a version

      **Figure 3** Submitting a version

#. Above the job canvas, click **Unlock** to unlock the job.


   .. figure:: /_static/images/en-us_image_0000001373087901.png
      :alt: **Figure 4** Unlocking a job

      **Figure 4** Unlocking a job

Version Rollback
----------------

After submitting the version, you can view it in the version list. (Currently, a maximum of 10 latest versions are saved.) Click **Roll Back** to roll back to any submitted version.

The rollback involves the following contents:

-  Job definition (such as operator properties and connection lines)
-  Basic job information, job scheduling configuration, job parameters, and lineage

The procedure is as follows:

#. Log in to the DataArts Studio console. Locate an instance and click **Access**. On the displayed page, locate a workspace and click **DataArts Factory**.


   .. figure:: /_static/images/en-us_image_0000001321928320.png
      :alt: **Figure 5** DataArts Factory

      **Figure 5** DataArts Factory

#. In the left navigation pane of DataArts Factory, choose **Development** > **Develop Job**.

#. In the job directory, double-click a job to access the job development page.

#. On the right of the page, click the **Versions** tab and view the version submission records. Select the version to be rolled back and click **Roll Back**.


   .. figure:: /_static/images/en-us_image_0000001373168705.png
      :alt: **Figure 6** Rolling back the version

      **Figure 6** Rolling back the version

Viewing Version Details
-----------------------

You can view the submitted version information in the version list.

The procedure is as follows:

#. Log in to the DataArts Studio console. Locate an instance and click **Access**. On the displayed page, locate a workspace and click **DataArts Factory**.


   .. figure:: /_static/images/en-us_image_0000001321928320.png
      :alt: **Figure 7** DataArts Factory

      **Figure 7** DataArts Factory

#. In the left navigation pane of DataArts Factory, choose **Development** > **Develop Job**.

#. In the job directory, double-click a job to access the job development page.

#. On the right of the page, click the **Versions** tab and view the version submission records. Select the desired version and click **View** to view its details.

   A new page is displayed, showing the job definition of the version. You cannot modify any job attributes in this window.


   .. figure:: /_static/images/en-us_image_0000001322407956.png
      :alt: **Figure 8** Viewing version details

      **Figure 8** Viewing version details

Version Comparison
------------------

#. Log in to the DataArts Studio console. Locate an instance and click **Access**. On the displayed page, locate a workspace and click **DataArts Factory**.


   .. figure:: /_static/images/en-us_image_0000001321928320.png
      :alt: **Figure 9** DataArts Factory

      **Figure 9** DataArts Factory

#. In the left navigation pane of DataArts Factory, choose **Development** > **Develop Job**.

#. In the job directory, double-click a job to access the job development page.

#. On the right of the page, click the **Versions** tab and view the version submission records. Select the versions to be compared and click **Compare Version**.

   If you select only one version, the selected version is compared with the JSON of the development-state job. If you select two versions, the JSON of the two versions is compared.


   .. figure:: /_static/images/en-us_image_0000001373408093.png
      :alt: **Figure 10** Comparing versions

      **Figure 10** Comparing versions
