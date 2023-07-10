:original_name: dataartsstudio_01_0901.html

.. _dataartsstudio_01_0901:

Submitting a Version and Unlocking the Script
=============================================

This involves the version management and lock functions.

-  Version management: traces script and job changes, and supports version comparison and rollback. The system retains 10 latest version records. In addition, version management can be used to distinguish the development state and production state.

   -  Development state: Scripts or jobs have not been submitted and are used for debugging. In the development state, you can edit, save, and run scripts or jobs without affecting those being scheduled. In addition, when a job is being associated with a script or job dependency is being configured, the associated script or job will read the configuration in the development state.
   -  Production state: Script or jobs have been submitted and are used for formal scheduling. In formal scheduling, the latest submitted versions of scripts or jobs will be used in scenarios such as script invocation, instance rerunning, and job dependency and patch data configuration.

-  .. _dataartsstudio_01_0901__li156131452182514:

   Lock: prevents conflict caused by collaborative script or job development. If you create or import a script or job, it is locked by you by default. You can only edit, save, or submit a script or job you have locked. To edit, save, or submit a script or job that is locked by another user or not locked by any user, you must lock the script or job first.

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

A script has been developed.


Submitting a Version and Unlocking the Script
---------------------------------------------

If you submit a version, the latest script in the development state will be saved and submitted and overwrite the previous script version. You are advised to unlock the script after submitting the version so that other developers can modify the script as needed.

#. Log in to the DataArts Studio console. Locate an instance and click **Access**. On the displayed page, locate a workspace and click **DataArts Factory**.


   .. figure:: /_static/images/en-us_image_0000001321928320.png
      :alt: **Figure 2** DataArts Factory

      **Figure 2** DataArts Factory

#. In the left navigation pane of DataArts Factory, choose **Data Development** > **Develop Script**.

#. In the script directory, double-click the developed script to access the script development page.

#. In the upper part of the script editor, click **Submit**. In the displayed dialog box, enter the change description (a maximum of 128 characters allowed) and select the check box below. If you do not select this option, you cannot click **OK**.


   .. figure:: /_static/images/en-us_image_0000001322247936.png
      :alt: **Figure 3** Submitting a version

      **Figure 3** Submitting a version

#. In the upper part of the script editor, click **Unlock** to unlock the script.


   .. figure:: /_static/images/en-us_image_0000001321928352.png
      :alt: **Figure 4** Unlocking a script

      **Figure 4** Unlocking a script

Version Rollback
----------------

After submitting the version, you can view it in the version list. (Currently, a maximum of 10 latest versions are saved.) Click **Roll Back** to roll back to any submitted version.

The rollback involves the following contents:

-  DLI: data connections, databases, resource queues, and script contents
-  DWS: data connections, databases, and script contents
-  HIVE: data connections, databases, resource queues, and script contents
-  SPARK: data connections, databases, and script contents
-  SHELL: host connections, parameters, interactive parameters, and script contents
-  RDS: data connections, databases, and script contents
-  PRESTO: data connections, modes, and script contents
-  PYTHON: host connections, parameters, interactive parameters, and script content
-  FLINK: script content

The procedure is as follows:

#. Log in to the DataArts Studio console. Locate an instance and click **Access**. On the displayed page, locate a workspace and click **DataArts Factory**.


   .. figure:: /_static/images/en-us_image_0000001321928320.png
      :alt: **Figure 5** DataArts Factory

      **Figure 5** DataArts Factory

#. In the left navigation pane of DataArts Factory, choose **Data Development** > **Develop Script**.

#. In the script directory list, double-click a script that you want to develop. The script development page is displayed.

#. On the right of the page, click the **Versions** tab and view the version submission records. Select the version to be rolled back and click **Roll Back**.

   If the content in the development state is not submitted, the content will be overwritten after the rollback. In this case, you must submit the rollback version again to make it take effect. By default, the latest submitted version is used for scheduling.


   .. figure:: /_static/images/en-us_image_0000001373087873.png
      :alt: **Figure 6** Rolling back a version

      **Figure 6** Rolling back a version

Version Comparison
------------------

You can compare the script contents of two different versions. If you select only one version, the system compares the script content of the selected version with that in the development state. If you select two versions, the system compares the script contents of two different versions.

The procedure is as follows:

#. In the left navigation pane of DataArts Factory, choose **Data Development** > **Develop Script**.

#. In the script directory list, double-click a script that you want to develop. The script development page is displayed.

#. On the right of the page, click the **Versions** tab and view the version submission records. Select the versions to be compared and click **Compare Version**.


   .. figure:: /_static/images/en-us_image_0000001322407924.png
      :alt: **Figure 7** Comparing versions

      **Figure 7** Comparing versions

#. A new page is displayed, showing the script content of different versions on the left and right separately. The differences between the two versions have been marked. You can use the |image1| and |image2| buttons in the upper right corner to go to the previous or next change.


   .. figure:: /_static/images/en-us_image_0000001373168673.png
      :alt: **Figure 8** Version comparison details

      **Figure 8** Version comparison details

.. |image1| image:: /_static/images/en-us_image_0000001373087869.png
.. |image2| image:: /_static/images/en-us_image_0000001373168677.png
